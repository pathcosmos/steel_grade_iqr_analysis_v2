# B5 강종 Adjusted IQR 적용 계획서

> **강종**: B5 (저탄소강)
> **작성일**: 2026-02-03
> **분석 기간**: 2025-04
> **목적**: Standard IQR에서 Adjusted IQR로 전환하여 과다 탐지 문제 해결

---

## 1. 현재 분석 상태 요약

### 1.1 기본 현황

| 항목 | 값 |
|------|-----|
| **총 레코드 수** | 14,391건 |
| **분석 기간** | 2025-04 (1개월) |
| **분석 태그 수** | 79개 |
| **평균 이상치율** | 4.66% |
| **최대 이상치율** | 20.36% (PR7L2_ACT_TORQUE) |

### 1.2 위험도별 태그 분포

| 위험도 | 기준 | 태그 수 | 비율 |
|--------|------|---------|------|
| 🔴 CRITICAL | ≥25% | 0개 | 0% |
| 🟠 DANGER | 15-25% | 9개 | 11.4% |
| 🟡 WARNING | 10-15% | 10개 | 12.7% |
| 🟢 CAUTION | 5-10% | 9개 | 11.4% |
| ⚪ NORMAL | <5% | 51개 | 64.5% |

### 1.3 카테고리별 이상치율 분포

| 카테고리 | 태그 수 | 평균 이상치율 | 최대 이상치율 | 주요 문제 태그 |
|----------|:-------:|:-------------:|:-------------:|----------------|
| 01_Furnace_Top_Temperature | 4 | 8.2% | 9.9% | HEATING_TOP_ZONE_NO_1 |
| 02_Furnace_Bottom_Temperature | 4 | 0.0% | 0.0% | - |
| 03_Furnace_Discharge_Temperature | 1 | 11.7% | 11.7% | FURNACE_EXIT |
| 04_Furnace_Auxiliary | 10 | 2.4% | 6.4% | MAIN_COMBUSTION_AIR_PRESSURE |
| 05_Stand_Torque | 16 | 0.2% | 0.8% | - |
| 06_Stand_Speed | 15 | 10.4% | 13.1% | STAND_1_ACTUAL_SPEED |
| 07_Stand_Load | 15 | 0.0% | 0.0% | - |
| 08_Pinchroll | 8 | 11.4% | 19.1% | PINCHROLL_2_ACTUAL_TORQUE |
| 09_PR_Detailed | 6 | 13.2% | 20.4% | PR7L2_ACT_TORQUE |

### 1.4 고이상치 태그 목록 (>10%)

| 순위 | 태그명 | 카테고리 | 이상치율 | 방향 |
|:----:|--------|----------|:--------:|:----:|
| 1 | PR7L2_ACT_TORQUE | PR_Detailed | 20.36% | upper |
| 2 | PR7L1_ACT_TORQUE | PR_Detailed | 20.00% | upper |
| 3 | PINCHROLL_2_ACTUAL_TORQUE | Pinchroll | 19.10% | lower |
| 4 | PINCHROLL_3_REFERENCE_TORQUE | Pinchroll | 19.08% | upper |
| 5 | PINCHROLL_4_REFERENCE_TORQUE | Pinchroll | 18.93% | upper |
| 6 | PR6L1_ACT_TORQUE | PR_Detailed | 17.92% | balanced |
| 7 | PINCHROLL_3_ACTUAL_TORQUE | Pinchroll | 17.26% | lower |
| 8 | PINCHROLL_4_ACTUAL_TORQUE | Pinchroll | 16.86% | lower |
| 9 | STAND_1_ACTUAL_SPEED | Stand_Speed | 13.06% | lower |
| 10 | FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | Furnace_Discharge | 11.72% | lower |

---

## 2. 데이터 분포 특성

### 2.1 왜도(Skewness) 분석

B5 강종의 `direction` 필드를 기반으로 왜도 추정:

| 방향 패턴 | 태그 수 | 의미 | Adjusted IQR 적용 효과 |
|-----------|:-------:|------|------------------------|
| **upper** | 18개 | 오른쪽 꼬리 (양의 왜도) | 상한 경계 확대, 하한 경계 축소 |
| **lower** | 32개 | 왼쪽 꼬리 (음의 왜도) | 하한 경계 확대, 상한 경계 축소 |
| **balanced** | 29개 | 대칭 분포 | 변화 미미 |

### 2.2 주요 문제 태그 분포 특성

#### 핀치롤/PR 상세 토크 (하한 미달 위주)
```
PINCHROLL_2_ACTUAL_TORQUE: lower 방향 → 음의 왜도
PINCHROLL_3_ACTUAL_TORQUE: lower 방향 → 음의 왜도
PINCHROLL_4_ACTUAL_TORQUE: lower 방향 → 음의 왜도
```
→ Adjusted IQR 적용 시 **하한 경계가 확대**되어 하한 이상치 감소 예상

#### PR 상세 토크 (상한 초과 위주)
```
PR7L1_ACT_TORQUE: upper 방향 → 양의 왜도
PR7L2_ACT_TORQUE: upper 방향 → 양의 왜도
```
→ Adjusted IQR 적용 시 **상한 경계가 확대**되어 상한 이상치 감소 예상

### 2.3 첨도(Kurtosis) 고려사항

첨도가 높은 경우(뾰족한 분포) Adjusted IQR만으로는 개선 효과가 제한적일 수 있음.
추후 MAD(Median Absolute Deviation) 기반 방법 또는 Percentile 방법 병행 검토 필요.

---

## 3. Adjusted IQR 적용 계획

### 3.1 Bowley 왜도 계산 방법

```python
def calculate_bowley_skewness(q1, median, q3):
    """Bowley 왜도 계산 (Quartile Skewness)"""
    iqr = q3 - q1
    if iqr == 0:
        return 0
    bowley_skew = (q3 + q1 - 2 * median) / iqr
    return bowley_skew
```

**Bowley 왜도 특성**:
- 범위: [-1, +1]
- 양수(+): 오른쪽 꼬리 분포 (Right-skewed)
- 음수(-): 왼쪽 꼬리 분포 (Left-skewed)
- 0 근처: 대칭 분포

### 3.2 보정 계수 적용 (c=0.8 권장)

```python
def calculate_adjusted_iqr_bounds(q1, median, q3, c=0.8):
    """Adjusted IQR 경계 계산"""
    iqr = q3 - q1
    bowley_skew = (q3 + q1 - 2 * median) / iqr if iqr > 0 else 0

    # 지수 보정 적용
    if bowley_skew >= 0:  # Right-skewed
        lower_mult = np.exp(-c * bowley_skew)
        upper_mult = np.exp(+c * bowley_skew)
    else:  # Left-skewed
        lower_mult = np.exp(+c * abs(bowley_skew))
        upper_mult = np.exp(-c * abs(bowley_skew))

    # 보정된 경계
    lower_bound = q1 - 1.5 * iqr * lower_mult
    upper_bound = q3 + 1.5 * iqr * upper_mult

    return lower_bound, upper_bound, bowley_skew
```

### 3.3 보정 계수 c 값 선정 근거

| c 값 | 보정 강도 | 적용 상황 |
|:----:|----------|----------|
| 0.6 | 약한 보정 | 약간의 왜도, 보수적 적용 |
| **0.8** | 표준 보정 | **일반적 산업 데이터 (권장)** |
| 1.0 | 강한 보정 | 강한 왜도, 적극적 보정 |

**권장값 c=0.8 선정 이유**:
1. 기존 연구 결과에서 15-20% 이상치율 감소 효과 확인
2. 과소 탐지 위험 최소화
3. 산업 공정 데이터에 일반적으로 적합

### 3.4 적용 대상 태그 우선순위

#### 1순위: 즉시 적용 (이상치율 >15%)
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| PR7L2_ACT_TORQUE | 20.36% | upper | 상한 확대로 4-5%p 감소 예상 |
| PR7L1_ACT_TORQUE | 20.00% | upper | 상한 확대로 4-5%p 감소 예상 |
| PINCHROLL_2_ACTUAL_TORQUE | 19.10% | lower | 하한 확대로 4%p 감소 예상 |
| PINCHROLL_3_REFERENCE_TORQUE | 19.08% | upper | 상한 확대로 4%p 감소 예상 |
| PINCHROLL_4_REFERENCE_TORQUE | 18.93% | upper | 상한 확대로 4%p 감소 예상 |
| PR6L1_ACT_TORQUE | 17.92% | balanced | 양방향 조정, 3%p 감소 예상 |
| PINCHROLL_3_ACTUAL_TORQUE | 17.26% | lower | 하한 확대로 3%p 감소 예상 |
| PINCHROLL_4_ACTUAL_TORQUE | 16.86% | lower | 하한 확대로 3%p 감소 예상 |

#### 2순위: 우선 적용 (이상치율 10-15%)
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| STAND_1_ACTUAL_SPEED | 13.06% | lower | 하한 확대로 2-3%p 감소 예상 |
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 11.72% | lower | 하한 확대로 2%p 감소 예상 |
| STAND 2~14 ACTUAL_SPEED | 9.9-11.0% | lower | 하한 확대로 2%p 감소 예상 |

#### 3순위: 관찰 대상 (이상치율 5-10%)
- 가열로 상부 온도 태그 4개
- 일부 가열로 보조설비 태그

---

## 4. 예상 효과

### 4.1 이상치율 감소 예측

기존 연구 결과와 outlier_methodology_analysis.py 분석 결과 기준:

| 구분 | Standard IQR | Adjusted IQR (예상) | 감소폭 |
|------|:------------:|:-------------------:|:------:|
| 평균 이상치율 | 4.66% | **3.7-4.0%** | 0.7-1.0%p |
| >15% 태그 수 | 9개 | **2-3개** | 6-7개 감소 |
| >10% 태그 수 | 19개 | **10-12개** | 7-9개 감소 |

### 4.2 카테고리별 예상 효과

| 카테고리 | 현재 평균 | 예상 평균 | 개선율 |
|----------|:---------:|:---------:|:------:|
| 08_Pinchroll | 11.4% | 8.0-9.0% | 20-30% |
| 09_PR_Detailed | 13.2% | 9.0-10.0% | 25-30% |
| 06_Stand_Speed | 10.4% | 8.0-9.0% | 15-20% |
| 01_Furnace_Top | 8.2% | 6.5-7.5% | 10-20% |

### 4.3 과다 탐지 해소 예상 태그

다음 태그들이 DANGER → WARNING 또는 WARNING → CAUTION으로 위험도 하향 예상:

1. **PR7L2_ACT_TORQUE**: DANGER(20.36%) → WARNING(15-16%)
2. **PR7L1_ACT_TORQUE**: DANGER(20.00%) → WARNING(15-16%)
3. **PINCHROLL_2_ACTUAL_TORQUE**: DANGER(19.10%) → WARNING(14-15%)
4. **PINCHROLL_3_REFERENCE_TORQUE**: DANGER(19.08%) → WARNING(14-15%)
5. **PINCHROLL_4_REFERENCE_TORQUE**: DANGER(18.93%) → WARNING(14-15%)

---

## 5. 구현 단계

### Phase 1: 시범 적용 (권장 1주)

**대상**: 1순위 고이상치 태그 8개

**작업 내용**:
1. 대상 태그별 Bowley 왜도 계산
2. Adjusted IQR 경계값 산출
3. Standard IQR vs Adjusted IQR 비교 차트 생성
4. 이상치 목록 비교 분석

**산출물**:
- `B5_adjusted_iqr_pilot_results.json`
- `B5_adjusted_iqr_comparison_chart.png`

### Phase 2: 전체 적용 (권장 2주)

**대상**: 전체 79개 태그

**작업 내용**:
1. 전체 태그 Adjusted IQR 적용
2. 카테고리별 결과 집계
3. 위험도 재분류
4. 월별 추이 재분석

**산출물**:
- `iqr_analysis_B5_adjusted_results.json`
- `IQR_ANALYSIS_REPORT_B5_ADJUSTED_KO.md`
- 개별 차트 갱신

### Phase 3: 검증 및 비교 (권장 1주)

**검증 항목**:
1. Standard IQR 결과와 병행 비교
2. 도메인 전문가 검토 (실제 공정 이상과 매칭 확인)
3. outlier_methodology_research 연구 결과와 비교
4. 위양성(False Positive) 감소율 검증

**성공 기준**:
- 평균 이상치율 15-20% 감소
- 위양성률 20% 이상 감소
- 도메인 전문가 승인

---

## 6. 기술적 고려사항

### 6.1 기존 코드 활용

`scripts/outlier_methodology_analysis.py`의 `calculate_adjusted_iqr()` 함수 활용:

```python
# 기존 구현 위치: outlier_methodology_analysis.py:114-150
def calculate_adjusted_iqr(data: np.ndarray, c: float = 0.8) -> Dict:
    """왜도 보정 Adjusted IQR 방법"""
    # ... (기존 구현 활용)
```

### 6.2 steel_grade_iqr_analysis_v2.py 수정 필요 사항

1. `--method` 옵션 추가: `standard` | `adjusted`
2. Adjusted IQR 결과에 `bowley_skewness`, `multipliers` 필드 추가
3. 비교 분석 차트 생성 로직 추가

### 6.3 데이터 검증 로직

```python
def validate_adjusted_iqr_results(standard_result, adjusted_result):
    """Adjusted IQR 적용 결과 검증"""
    # 1. 이상치율이 증가하지 않는지 확인 (balanced 제외)
    if adjusted_result['outlier_ratio'] > standard_result['outlier_ratio'] * 1.1:
        return False, "이상치율 증가 - 검토 필요"

    # 2. 경계값이 합리적 범위 내인지 확인
    if adjusted_result['lower_bound'] > adjusted_result['upper_bound']:
        return False, "경계값 역전 - 데이터 품질 확인 필요"

    return True, "검증 통과"
```

---

## 7. 위험 요소 및 대응 방안

### 7.1 위험 요소

| 위험 | 영향도 | 대응 방안 |
|------|:------:|----------|
| 과소 탐지 발생 | 높음 | c=0.8 보수적 적용, 단계적 확대 |
| 특이 분포 태그 존재 | 중간 | MAD 방법 병행 검토 |
| 월별 분포 변화 | 중간 | 월별 Bowley 왜도 재계산 |

### 7.2 롤백 기준

다음 조건 발생 시 Standard IQR로 롤백:
1. 도메인 전문가가 실제 이상을 놓치는 사례 3건 이상 보고
2. 특정 태그에서 이상치율이 오히려 30% 이상 증가
3. 전체 평균 이상치율이 2배 이상 감소 (과소 탐지 의심)

---

## 8. 참고 자료

### 8.1 관련 문서

| 문서 | 위치 | 설명 |
|------|------|------|
| 방법론 연구 결과 | `analysis_output/outlier_methodology_research/` | Standard vs Adjusted 비교 연구 |
| 현재 분석 보고서 | `B5/IQR_ANALYSIS_REPORT_B5_KO.md` | Standard IQR 적용 결과 |
| 필터 설정 | `config/tag_filter_config.yaml` | 필터 설정 파일 |

### 8.2 학술적 배경

- **Bowley 왜도**: Bowley, A.L. (1920) - 사분위수 기반 왜도 측정
- **Adjusted IQR**: Kimber, A.C. (1990) - 왜도 보정 이상치 탐지
- **지수 보정**: Hubert, M. & Vandervieren, E. (2008) - 로버스트 이상치 탐지

---

*본 계획서는 B5 강종의 Adjusted IQR 적용을 위한 가이드라인으로, 실제 적용 시 도메인 전문가 검토가 필요합니다.*

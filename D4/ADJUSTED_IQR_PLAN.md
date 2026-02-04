# D4 강종 Adjusted IQR 적용 계획서

> **강종**: D4 (중탄소강)
> **작성일**: 2026-02-03
> **분석 기간**: 2025-05 ~ 2025-08 (4개월)
> **목적**: Standard IQR에서 Adjusted IQR로 전환하여 과다 탐지 문제 해결

---

## 1. 현재 분석 상태 요약

### 1.1 기본 현황

| 항목 | 값 |
|------|-----|
| **총 레코드 수** | 20,144건 |
| **분석 기간** | 2025-05 ~ 2025-08 (4개월) |
| **분석 태그 수** | 79개 |
| **평균 이상치율** | 5.18% |
| **최대 이상치율** | 37.91% (FINISHING_BLOCK_ACTUAL_SPEED) |

### 1.2 위험도별 태그 분포

| 위험도 | 기준 | 태그 수 | 비율 |
|--------|------|---------|------|
| 🔴 CRITICAL | ≥25% | 1개 | 1.3% |
| 🟠 DANGER | 15-25% | 16개 | 20.3% |
| 🟡 WARNING | 10-15% | 3개 | 3.8% |
| 🟢 CAUTION | 5-10% | 8개 | 10.1% |
| ⚪ NORMAL | <5% | 51개 | 64.5% |

### 1.3 카테고리별 이상치율 분포

| 카테고리 | 태그 수 | 평균 이상치율 | 최대 이상치율 | 주요 문제 태그 |
|----------|:-------:|:-------------:|:-------------:|----------------|
| 01_Furnace_Top_Temperature | 4 | 2.4% | 2.8% | - |
| 02_Furnace_Bottom_Temperature | 4 | 1.6% | 2.8% | - |
| 03_Furnace_Discharge_Temperature | 1 | 8.3% | 8.3% | FURNACE_EXIT |
| 04_Furnace_Auxiliary | 10 | 9.1% | 22.1% | FURNACE_O2_ANALYZER |
| 05_Stand_Torque | 16 | 0.8% | 2.2% | - |
| **06_Stand_Speed** | **15** | **16.9%** | **37.9%** | FINISHING_BLOCK_ACTUAL_SPEED |
| 07_Stand_Load | 15 | 0.0% | 0.0% | - |
| 08_Pinchroll | 8 | 7.7% | 16.9% | PINCHROLL_2_ACTUAL_TORQUE |
| 09_PR_Detailed | 6 | 4.8% | 6.3% | PR7L1_ACT_TORQUE |

### 1.4 고이상치 태그 목록 (>10%)

| 순위 | 태그명 | 카테고리 | 이상치율 | 방향 |
|:----:|--------|----------|:--------:|:----:|
| 1 | **FINISHING_BLOCK_ACTUAL_SPEED** | Stand_Speed | **37.91%** | balanced |
| 2 | FURNACE_O2_ANALYZER | Furnace_Auxiliary | 22.12% | lower |
| 3 | PINCHROLL_2_ACTUAL_TORQUE | Pinchroll | 16.90% | lower |
| 4 | STAND_8_ACTUAL_SPEED | Stand_Speed | 16.00% | lower |
| 5 | STAND_11_ACTUAL_SPEED | Stand_Speed | 15.89% | lower |
| 6 | STAND_14_ACTUAL_SPEED | Stand_Speed | 15.81% | lower |
| 7 | STAND_12_ACTUAL_SPEED | Stand_Speed | 15.79% | lower |
| 8 | STAND_10_ACTUAL_SPEED | Stand_Speed | 15.73% | lower |
| 9 | STAND_9_ACTUAL_SPEED | Stand_Speed | 15.62% | lower |
| 10 | STAND_13_ACTUAL_SPEED | Stand_Speed | 15.58% | lower |
| 11 | STAND_2_ACTUAL_SPEED | Stand_Speed | 15.48% | lower |
| 12 | STAND_6_ACTUAL_SPEED | Stand_Speed | 15.44% | lower |
| 13 | STAND_4_ACTUAL_SPEED | Stand_Speed | 15.43% | lower |
| 14 | STAND_5_ACTUAL_SPEED | Stand_Speed | 15.37% | lower |
| 15 | STAND_7_ACTUAL_SPEED | Stand_Speed | 15.36% | lower |
| 16 | STAND_1_ACTUAL_SPEED | Stand_Speed | 15.35% | lower |
| 17 | STAND_3_ACTUAL_SPEED | Stand_Speed | 15.34% | lower |
| 18 | PINCHROLL_4_ACTUAL_TORQUE | Pinchroll | 15.34% | lower |
| 19 | PINCHROLL_2_ACTUAL_SPEED | Pinchroll | 14.57% | lower |
| 20 | PINCHROLL_4_REFERENCE_TORQUE | Pinchroll | 14.18% | upper |

---

## 2. 데이터 분포 특성

### 2.1 왜도(Skewness) 분석

D4 강종의 `direction` 필드를 기반으로 왜도 추정:

| 방향 패턴 | 태그 수 | 의미 | Adjusted IQR 적용 효과 |
|-----------|:-------:|------|------------------------|
| **lower** | 45개 | 왼쪽 꼬리 (음의 왜도) | 하한 경계 확대, 상한 경계 축소 |
| **upper** | 12개 | 오른쪽 꼬리 (양의 왜도) | 상한 경계 확대, 하한 경계 축소 |
| **balanced** | 22개 | 대칭 분포 | 변화 미미 |

### 2.2 D4 강종의 특이점: 스탠드 속도 집중 문제

**핵심 발견**: D4 강종은 **06_Stand_Speed 카테고리 전체**에서 15% 이상의 높은 이상치율을 보임.

```
분석 결과 패턴:
- FINISHING_BLOCK_ACTUAL_SPEED: 37.91% (CRITICAL)
- STAND_1~14 전체: 15.3-16.0% (DANGER)
- 방향: 모두 'lower' 또는 'balanced'
```

**원인 추정**:
1. D4 강종의 특수한 압연 조건으로 인한 저속 운전 빈도 높음
2. 다른 강종 대비 속도 분포가 왼쪽으로 편향 (음의 왜도)
3. Standard IQR이 이러한 분포 특성을 반영하지 못함

### 2.3 월별 분포 변동성

D4 강종은 4개월 데이터로 월별 변동이 관찰됨:

| 월 | 레코드 수 | 특이사항 |
|----|:---------:|----------|
| 2025-05 | 7,190 | 안정적 |
| 2025-06 | 5,758 | 안정적 |
| 2025-07 | 2,880 | 이상치율 상승 |
| 2025-08 | 4,316 | 이상치율 상승 |

→ **월별 Bowley 왜도 재계산**이 중요함

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

### 3.2 보정 계수 적용

D4 강종은 강한 음의 왜도를 보이는 태그가 많아 **c=0.8~1.0** 범위 검토 필요.

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
        lower_mult = np.exp(+c * abs(bowley_skew))  # 확대
        upper_mult = np.exp(-c * abs(bowley_skew))  # 축소

    # 보정된 경계
    lower_bound = q1 - 1.5 * iqr * lower_mult
    upper_bound = q3 + 1.5 * iqr * upper_mult

    return lower_bound, upper_bound, bowley_skew
```

### 3.3 적용 대상 태그 우선순위

#### 1순위: 즉시 적용 (이상치율 >20%)
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| **FINISHING_BLOCK_ACTUAL_SPEED** | **37.91%** | balanced | 양방향 조정, 8-10%p 감소 예상 |
| FURNACE_O2_ANALYZER | 22.12% | lower | 하한 확대로 5-6%p 감소 예상 |

#### 2순위: 우선 적용 - 스탠드 속도 전체 (이상치율 15-17%)
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| STAND_1~14_ACTUAL_SPEED | 15.3-16.0% | lower | 하한 확대로 3-4%p 감소 예상 |

→ **15개 스탠드 속도 태그 일괄 적용** 권장

#### 3순위: 핀치롤 태그 (이상치율 14-17%)
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| PINCHROLL_2_ACTUAL_TORQUE | 16.90% | lower | 하한 확대로 3-4%p 감소 예상 |
| PINCHROLL_4_ACTUAL_TORQUE | 15.34% | lower | 하한 확대로 3%p 감소 예상 |
| PINCHROLL_2_ACTUAL_SPEED | 14.57% | lower | 하한 확대로 2-3%p 감소 예상 |
| PINCHROLL_4_REFERENCE_TORQUE | 14.18% | upper | 상한 확대로 2-3%p 감소 예상 |

---

## 4. 예상 효과

### 4.1 이상치율 감소 예측

| 구분 | Standard IQR | Adjusted IQR (예상) | 감소폭 |
|------|:------------:|:-------------------:|:------:|
| 평균 이상치율 | 5.18% | **3.5-4.2%** | 1.0-1.7%p |
| **최대 이상치율** | **37.91%** | **25-28%** | 10-13%p |
| CRITICAL 태그 수 | 1개 | **0개** | 1개 감소 |
| DANGER 태그 수 | 16개 | **5-8개** | 8-11개 감소 |

### 4.2 카테고리별 예상 효과

| 카테고리 | 현재 평균 | 예상 평균 | 개선율 |
|----------|:---------:|:---------:|:------:|
| **06_Stand_Speed** | **16.9%** | **11-13%** | **35-40%** |
| 04_Furnace_Auxiliary | 9.1% | 6-7% | 25-30% |
| 08_Pinchroll | 7.7% | 5-6% | 25-30% |

### 4.3 과다 탐지 해소 예상 태그

**CRITICAL → DANGER 전환 예상**:
1. **FINISHING_BLOCK_ACTUAL_SPEED**: 37.91% → 25-28% (DANGER)

**DANGER → WARNING 전환 예상**:
1. FURNACE_O2_ANALYZER: 22.12% → 15-17%
2. STAND_1~14 전체 (15개): 15.3-16.0% → 11-13%

---

## 5. 구현 단계

### Phase 1: 시범 적용 - CRITICAL 태그 (권장 1주)

**대상**:
- FINISHING_BLOCK_ACTUAL_SPEED (최우선)
- FURNACE_O2_ANALYZER

**작업 내용**:
1. 대상 태그별 월별 Bowley 왜도 계산
2. c=0.8, 0.9, 1.0 비교 분석
3. 최적 보정 계수 결정
4. Standard vs Adjusted 비교 차트 생성

**산출물**:
- `D4_adjusted_iqr_pilot_critical.json`
- `D4_finishing_block_comparison.png`

### Phase 2: 스탠드 속도 일괄 적용 (권장 1주)

**대상**: STAND_1~14_ACTUAL_SPEED (15개)

**작업 내용**:
1. 스탠드 속도 태그 공통 Bowley 왜도 패턴 분석
2. 일괄 보정 계수 적용
3. 스탠드별 비교 분석

**산출물**:
- `D4_stand_speed_adjusted_results.json`
- `D4_stand_speed_comparison_summary.png`

### Phase 3: 전체 적용 (권장 2주)

**대상**: 전체 79개 태그

**작업 내용**:
1. 전체 태그 Adjusted IQR 적용
2. 월별 재분석 (4개월 개별)
3. 카테고리별 결과 집계

**산출물**:
- `iqr_analysis_D4_adjusted_results.json`
- `IQR_ANALYSIS_REPORT_D4_ADJUSTED_KO.md`

### Phase 4: 검증 (권장 1주)

**검증 항목**:
1. 스탠드 속도 이상치 대폭 감소 확인
2. FINISHING_BLOCK 이상치 DANGER 레벨 이하 확인
3. 실제 공정 이상 데이터와 매칭 검증

---

## 6. D4 강종 특별 고려사항

### 6.1 스탠드 속도 집중 문제 해결 전략

D4 강종의 핵심 문제는 **스탠드 속도 전체**가 높은 이상치율을 보이는 것.

**권장 접근법**:
```python
# 스탠드 속도 태그 그룹 처리
stand_speed_tags = [f"STAND_{i}_ACTUAL_SPEED" for i in range(1, 15)]
stand_speed_tags.append("FINISHING_BLOCK_ACTUAL_SPEED")

# 공통 보정 계수 계산 (그룹 평균 왜도 기준)
group_skewness = calculate_group_skewness(stand_speed_tags, data)
recommended_c = 0.8 if abs(group_skewness) < 0.5 else 1.0
```

### 6.2 FURNACE_O2_ANALYZER 특수 케이스

이 태그는 D4와 N5에서만 높은 이상치율 (B5, D5는 0%):

| 강종 | 이상치율 | 원인 추정 |
|------|:--------:|----------|
| B5 | 0.0% | 정상 |
| D4 | **22.12%** | 특수 연소 조건 |
| D5 | 0.0% | 정상 |
| N5 | **20.90%** | 특수 연소 조건 |

→ **강종별 맞춤 IQR 경계** 또는 **필터 조건 추가** 검토 필요

### 6.3 월별 변동 대응

```python
def calculate_monthly_adjusted_iqr(df, tag_name, c=0.8):
    """월별 Adjusted IQR 계산"""
    results = {}
    for month in df['month'].unique():
        month_data = df[df['month'] == month][tag_name].values
        results[month] = calculate_adjusted_iqr(month_data, c)
    return results
```

---

## 7. 위험 요소 및 대응 방안

### 7.1 위험 요소

| 위험 | 영향도 | 대응 방안 |
|------|:------:|----------|
| 스탠드 속도 과소 탐지 | 높음 | 도메인 전문가 검토, c 값 보수적 적용 |
| FINISHING_BLOCK 특이값 | 높음 | 별도 분석, 필터 조건 추가 검토 |
| 월별 왜도 변동 | 중간 | 월별 재계산, 이동 평균 적용 |

### 7.2 롤백 기준

1. FINISHING_BLOCK 실제 이상 미탐지 사례 발생
2. 스탠드 속도 이상치율이 5% 미만으로 급감 (과소 탐지 의심)
3. 도메인 전문가 피드백에 따른 조정 필요

---

## 8. 참고 자료

### 8.1 관련 문서

| 문서 | 위치 | 설명 |
|------|------|------|
| 현재 분석 보고서 | `D4/IQR_ANALYSIS_REPORT_D4_KO.md` | Standard IQR 적용 결과 |
| 방법론 연구 | `analysis_output/outlier_methodology_research/` | 비교 연구 결과 |
| 주의 태그 보고서 | `ATTENTION_TAGS_REPORT.md` | 강종별 고위험 태그 |

### 8.2 D4 강종 특성

- **용도**: 중탄소강, 일반 구조용
- **압연 특성**: 중간 압연 속도, 안정적 토크
- **데이터 특성**: 스탠드 속도 저속 운전 빈도 높음

---

*본 계획서는 D4 강종의 Adjusted IQR 적용을 위한 가이드라인으로, 특히 스탠드 속도 집중 문제 해결에 중점을 두었습니다.*

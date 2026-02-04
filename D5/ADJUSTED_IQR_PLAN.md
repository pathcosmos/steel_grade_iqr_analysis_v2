# D5 강종 Adjusted IQR 적용 계획서

> **강종**: D5 (중고탄소강)
> **작성일**: 2026-02-03
> **분석 기간**: 2025-03 ~ 2025-08 (6개월, 최장 기간)
> **목적**: Standard IQR에서 Adjusted IQR로 전환하여 과다 탐지 문제 해결

---

## 1. 현재 분석 상태 요약

### 1.1 기본 현황

| 항목 | 값 |
|------|-----|
| **총 레코드 수** | 74,855건 |
| **분석 기간** | 2025-03 ~ 2025-08 (6개월) |
| **분석 태그 수** | 79개 |
| **평균 이상치율** | **8.11%** (4개 강종 중 최고) |
| **최대 이상치율** | 34.90% (PINCHROLL_4_ACTUAL_TORQUE) |

### 1.2 위험도별 태그 분포

| 위험도 | 기준 | 태그 수 | 비율 |
|--------|------|---------|------|
| 🔴 CRITICAL | ≥25% | 2개 | 2.5% |
| 🟠 DANGER | 15-25% | 17개 | 21.5% |
| 🟡 WARNING | 10-15% | 5개 | 6.3% |
| 🟢 CAUTION | 5-10% | 19개 | 24.1% |
| ⚪ NORMAL | <5% | 36개 | 45.6% |

**주목**: D5는 4개 강종 중 **가장 높은 평균 이상치율**과 **가장 많은 고위험 태그**를 보유.

### 1.3 카테고리별 이상치율 분포

| 카테고리 | 태그 수 | 평균 이상치율 | 최대 이상치율 | 주요 문제 태그 |
|----------|:-------:|:-------------:|:-------------:|----------------|
| 01_Furnace_Top_Temperature | 4 | 9.4% | 9.6% | SOAKING_TOP_ZONE_NO_1 |
| 02_Furnace_Bottom_Temperature | 4 | 7.2% | 10.0% | SOAKING_BOTTOM_ZONE_NO_2 |
| 03_Furnace_Discharge_Temperature | 1 | 7.4% | 7.4% | FURNACE_EXIT |
| 04_Furnace_Auxiliary | 10 | 6.5% | 13.6% | MAIN_COMBUSTION_AIR_PRESSURE |
| 05_Stand_Torque | 16 | 1.2% | 3.8% | - |
| **06_Stand_Speed** | **15** | **24.3%** | **29.2%** | STAND_10_ACTUAL_SPEED |
| 07_Stand_Load | 15 | 0.0% | 0.0% | - |
| **08_Pinchroll** | **8** | **15.8%** | **34.9%** | PINCHROLL_4_ACTUAL_TORQUE |
| 09_PR_Detailed | 6 | 6.1% | 10.1% | PR6L1_ACT_TORQUE |

### 1.4 고이상치 태그 목록 (>15%)

| 순위 | 태그명 | 카테고리 | 이상치율 | 방향 |
|:----:|--------|----------|:--------:|:----:|
| 1 | **PINCHROLL_4_ACTUAL_TORQUE** | Pinchroll | **34.90%** | balanced |
| 2 | **STAND_10_ACTUAL_SPEED** | Stand_Speed | **29.18%** | lower |
| 3 | STAND_2_ACTUAL_SPEED | Stand_Speed | 26.34% | lower |
| 4 | STAND_11_ACTUAL_SPEED | Stand_Speed | 24.38% | lower |
| 5 | STAND_12_ACTUAL_SPEED | Stand_Speed | 24.38% | lower |
| 6 | STAND_7_ACTUAL_SPEED | Stand_Speed | 24.19% | lower |
| 7 | STAND_6_ACTUAL_SPEED | Stand_Speed | 24.14% | lower |
| 8 | STAND_5_ACTUAL_SPEED | Stand_Speed | 24.13% | lower |
| 9 | STAND_13_ACTUAL_SPEED | Stand_Speed | 24.12% | lower |
| 10 | FINISHING_BLOCK_ACTUAL_SPEED | Stand_Speed | 24.05% | lower |
| 11 | STAND_9_ACTUAL_SPEED | Stand_Speed | 24.02% | lower |
| 12 | STAND_14_ACTUAL_SPEED | Stand_Speed | 24.01% | lower |
| 13 | STAND_4_ACTUAL_SPEED | Stand_Speed | 24.00% | lower |
| 14 | STAND_3_ACTUAL_SPEED | Stand_Speed | 23.93% | lower |
| 15 | STAND_1_ACTUAL_SPEED | Stand_Speed | 23.79% | lower |
| 16 | STAND_8_ACTUAL_SPEED | Stand_Speed | 23.78% | lower |
| 17 | PINCHROLL_3_ACTUAL_SPEED | Pinchroll | 20.82% | lower |
| 18 | PINCHROLL_4_ACTUAL_SPEED | Pinchroll | 20.78% | lower |
| 19 | PINCHROLL_2_ACTUAL_TORQUE | Pinchroll | 20.69% | lower |
| 20 | PINCHROLL_4_REFERENCE_TORQUE | Pinchroll | 18.83% | upper |

---

## 2. 데이터 분포 특성

### 2.1 왜도(Skewness) 분석

D5 강종의 `direction` 필드를 기반으로 왜도 추정:

| 방향 패턴 | 태그 수 | 의미 | Adjusted IQR 적용 효과 |
|-----------|:-------:|------|------------------------|
| **lower** | **48개** | 왼쪽 꼬리 (음의 왜도) | 하한 경계 확대, 상한 경계 축소 |
| upper | 14개 | 오른쪽 꼬리 (양의 왜도) | 상한 경계 확대, 하한 경계 축소 |
| balanced | 17개 | 대칭 분포 | 변화 미미 |

**핵심 발견**: D5 강종은 **lower 방향 이상치가 압도적**으로 많음 (61%).

### 2.2 D5 강종의 심각한 문제점

**문제 1: 스탠드 속도 전체 24% 이상치율**
```
STAND_1~14 + FINISHING_BLOCK: 모두 23.8-29.2% 이상치율
모든 방향: lower (하한 미달)
→ 강종 특성상 저속 운전이 많아 Standard IQR이 부적절
```

**문제 2: 핀치롤 복합 문제**
```
PINCHROLL_4_ACTUAL_TORQUE: 34.90% (CRITICAL)
PINCHROLL_3/4_ACTUAL_SPEED: 20.8% (DANGER)
PINCHROLL_2_ACTUAL_TORQUE: 20.69% (DANGER)
```

### 2.3 월별 이상치율 변동

D5 강종은 6개월 데이터로 월별 변동이 심함:

| 월 | 레코드 수 | 평균 이상치율 | 특이사항 |
|----|:---------:|:-------------:|----------|
| 2025-03 | 4,320 | 낮음 | 초기 안정 |
| 2025-04 | 8,640 | 중간 | 점진적 증가 |
| 2025-05 | 21,583 | 중간 | 최다 레코드 |
| 2025-06 | 5,757 | 중간 | 안정적 |
| 2025-07 | 18,720 | 높음 | 이상치 급증 |
| **2025-08** | **15,835** | **매우 높음** | **20.85% 이상치율** |

→ **8월 데이터 특별 분석** 및 **월별 적응형 IQR** 검토 필요

---

## 3. Adjusted IQR 적용 계획

### 3.1 D5 강종 맞춤 보정 전략

D5는 강한 음의 왜도를 보이므로 **c=1.0** 적극 검토:

```python
def calculate_d5_adjusted_iqr(data, c=1.0):
    """D5 강종 맞춤 Adjusted IQR - 강한 보정"""
    q1, median, q3 = np.percentile(data, [25, 50, 75])
    iqr = q3 - q1

    # Bowley 왜도 계산
    bowley_skew = (q3 + q1 - 2 * median) / iqr if iqr > 0 else 0

    # D5 특성: 대부분 lower 방향 → 음의 왜도
    # 강한 보정(c=1.0)으로 하한 경계 대폭 확대
    if bowley_skew >= 0:
        lower_mult = np.exp(-c * bowley_skew)
        upper_mult = np.exp(+c * bowley_skew)
    else:
        lower_mult = np.exp(+c * abs(bowley_skew))  # 하한 대폭 확대
        upper_mult = np.exp(-c * abs(bowley_skew))  # 상한 축소

    lower_bound = q1 - 1.5 * iqr * lower_mult
    upper_bound = q3 + 1.5 * iqr * upper_mult

    return lower_bound, upper_bound, bowley_skew
```

### 3.2 보정 계수 비교 분석 계획

D5의 심각한 이상치율을 고려하여 다양한 c 값 비교:

| c 값 | 예상 평균 이상치율 | 적용 상황 |
|:----:|:-----------------:|----------|
| 0.8 | 6.0-7.0% | 보수적 적용 |
| **1.0** | **4.5-5.5%** | **권장 (D5 맞춤)** |
| 1.2 | 3.5-4.5% | 적극적 보정 (검증 필요) |

### 3.3 적용 대상 태그 우선순위

#### 1순위: CRITICAL 태그 즉시 적용
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| **PINCHROLL_4_ACTUAL_TORQUE** | **34.90%** | balanced | c=1.0 적용 시 10-12%p 감소 |
| **STAND_10_ACTUAL_SPEED** | **29.18%** | lower | 하한 확대로 8-10%p 감소 |

#### 2순위: 스탠드 속도 전체 일괄 적용 (DANGER)
| 태그 그룹 | 현재 범위 | 방향 | 예상 효과 |
|-----------|:---------:|:----:|----------|
| STAND_1~14 + FINISHING_BLOCK | 23.8-26.3% | 모두 lower | 하한 확대로 6-8%p 감소 |

→ **15개 태그 동일 보정 계수(c=1.0) 일괄 적용** 권장

#### 3순위: 핀치롤 속도/토크 (DANGER)
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| PINCHROLL_3_ACTUAL_SPEED | 20.82% | lower | 5-6%p 감소 |
| PINCHROLL_4_ACTUAL_SPEED | 20.78% | lower | 5-6%p 감소 |
| PINCHROLL_2_ACTUAL_TORQUE | 20.69% | lower | 5-6%p 감소 |
| PINCHROLL_4_REFERENCE_TORQUE | 18.83% | upper | 4-5%p 감소 |

#### 4순위: 가열로 관련 태그 (WARNING/CAUTION)
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| MAIN_COMBUSTION_AIR_PRESSURE | 13.59% | lower | 3-4%p 감소 |
| INDIRECT_COOLING_WATER_FLOW | 12.55% | lower | 3-4%p 감소 |
| SOAKING_BOTTOM_ZONE 2종 | 9.9-10.0% | lower | 2-3%p 감소 |

---

## 4. 예상 효과

### 4.1 이상치율 감소 예측

| 구분 | Standard IQR | Adjusted IQR (c=1.0) | 감소폭 |
|------|:------------:|:--------------------:|:------:|
| **평균 이상치율** | **8.11%** | **4.5-5.5%** | **2.6-3.6%p** |
| 최대 이상치율 | 34.90% | 22-25% | 10-13%p |
| CRITICAL 태그 수 | 2개 | **0개** | 2개 감소 |
| DANGER 태그 수 | 17개 | **5-7개** | 10-12개 감소 |
| >10% 태그 수 | 24개 | **10-12개** | 12-14개 감소 |

### 4.2 카테고리별 예상 효과

| 카테고리 | 현재 평균 | 예상 평균 (c=1.0) | 개선율 |
|----------|:---------:|:-----------------:|:------:|
| **06_Stand_Speed** | **24.3%** | **14-16%** | **35-40%** |
| **08_Pinchroll** | **15.8%** | **9-11%** | **35-40%** |
| 04_Furnace_Auxiliary | 6.5% | 4-5% | 25-35% |
| 01_Furnace_Top | 9.4% | 6-7% | 25-30% |

### 4.3 위험도 전환 예상

**CRITICAL → DANGER**:
1. PINCHROLL_4_ACTUAL_TORQUE: 34.90% → 22-25%
2. STAND_10_ACTUAL_SPEED: 29.18% → 18-21%

**DANGER → WARNING**:
1. STAND_1~14 + FINISHING_BLOCK (15개): 23-26% → 14-17%
2. PINCHROLL_3/4_ACTUAL_SPEED: 20.8% → 13-15%
3. PINCHROLL_2_ACTUAL_TORQUE: 20.69% → 13-15%

---

## 5. 구현 단계

### Phase 1: CRITICAL 태그 시범 적용 (권장 1주)

**대상**:
- PINCHROLL_4_ACTUAL_TORQUE
- STAND_10_ACTUAL_SPEED

**작업 내용**:
1. c=0.8, 1.0, 1.2 비교 분석
2. 월별 Bowley 왜도 변동 분석 (특히 8월)
3. 최적 보정 계수 결정
4. Standard vs Adjusted 비교 리포트 생성

**산출물**:
- `D5_adjusted_iqr_pilot_critical.json`
- `D5_critical_tags_comparison.png`
- `D5_monthly_skewness_analysis.md`

### Phase 2: 스탠드 속도 일괄 적용 (권장 1주)

**대상**: STAND_1~14_ACTUAL_SPEED + FINISHING_BLOCK_ACTUAL_SPEED (15개)

**작업 내용**:
1. 스탠드 속도 그룹 공통 왜도 분석
2. c=1.0 일괄 적용
3. 개별 스탠드별 효과 분석

**산출물**:
- `D5_stand_speed_adjusted_results.json`
- `D5_stand_speed_monthly_trend.png`

### Phase 3: 핀치롤 및 기타 태그 적용 (권장 1주)

**대상**:
- 핀치롤 태그 8개
- 가열로 관련 고이상치 태그

**작업 내용**:
1. 핀치롤 태그 개별 왜도 분석
2. 가열로 태그 월별 변동 분석
3. 보정 계수 최적화

### Phase 4: 전체 적용 및 검증 (권장 2주)

**작업 내용**:
1. 전체 79개 태그 Adjusted IQR 적용
2. 월별 분석 (6개월 개별)
3. 8월 특이 데이터 심층 분석
4. 도메인 전문가 검증

**산출물**:
- `iqr_analysis_D5_adjusted_results.json`
- `IQR_ANALYSIS_REPORT_D5_ADJUSTED_KO.md`
- `D5_august_special_analysis.md`

---

## 6. D5 강종 특별 고려사항

### 6.1 8월 데이터 특별 분석

8월 데이터에서 이상치율이 급증한 원인 분석 필요:

```python
def analyze_august_anomaly(df):
    """8월 데이터 특이점 분석"""
    aug_data = df[df['month'] == '2025-08']

    # 1. 일별 이상치 패턴
    daily_pattern = aug_data.groupby('date')['is_outlier'].mean()

    # 2. 특정 일자 집중 여부
    peak_dates = daily_pattern[daily_pattern > 0.3].index.tolist()

    # 3. 시간대별 패턴
    hourly_pattern = aug_data.groupby('hour')['is_outlier'].mean()

    return peak_dates, hourly_pattern
```

**추정 원인**:
1. 특정 설비 고장 또는 정비
2. 강종 배합 변경
3. 계절적 환경 변화 (고온)

### 6.2 월별 적응형 IQR 검토

D5의 월별 변동성을 고려한 적응형 접근:

```python
def calculate_adaptive_monthly_iqr(df, tag_name, c=1.0):
    """월별 적응형 Adjusted IQR"""
    monthly_bounds = {}

    for month in df['month'].unique():
        month_data = df[df['month'] == month][tag_name].values

        if len(month_data) > 100:
            bounds = calculate_adjusted_iqr(month_data, c)

            # 이전 월 대비 급격한 변화 감지
            if month in monthly_bounds:
                prev = monthly_bounds[month]
                if abs(bounds['lower'] - prev['lower']) > prev['iqr'] * 0.5:
                    # 급격한 변화 시 스무딩 적용
                    bounds['lower'] = (bounds['lower'] + prev['lower']) / 2

            monthly_bounds[month] = bounds

    return monthly_bounds
```

### 6.3 스탠드 속도 그룹 분석

15개 스탠드 속도 태그가 동일한 패턴을 보이므로:

```python
# 그룹 분석 권장
stand_speed_group = {
    'tags': [f'STAND_{i}_ACTUAL_SPEED' for i in range(1, 15)] + ['FINISHING_BLOCK_ACTUAL_SPEED'],
    'common_direction': 'lower',
    'avg_outlier_rate': 24.3,
    'recommended_c': 1.0,
    'expected_reduction': '6-8%p'
}
```

---

## 7. 위험 요소 및 대응 방안

### 7.1 위험 요소

| 위험 | 영향도 | 대응 방안 |
|------|:------:|----------|
| 과도한 보정으로 과소 탐지 | 높음 | c=1.0 초과 금지, 단계적 적용 |
| 8월 데이터 특이성 | 높음 | 8월 별도 분석, 필요시 제외 |
| 월별 왜도 불안정 | 중간 | 적응형 IQR 적용 |
| 스탠드 속도 일괄 적용 부작용 | 중간 | 개별 스탠드 모니터링 |

### 7.2 롤백 기준

1. 평균 이상치율이 3% 미만으로 급감 (과소 탐지)
2. 실제 설비 이상 미탐지 사례 발생
3. 특정 스탠드에서만 이상치율 급감 (불균형)

### 7.3 모니터링 지표

```python
monitoring_metrics = {
    'avg_outlier_rate': 'target: 4.5-5.5%',
    'max_outlier_rate': 'target: < 25%',
    'critical_tags': 'target: 0',
    'danger_tags': 'target: < 8',
    'monthly_variance': 'target: CV < 0.3'
}
```

---

## 8. 참고 자료

### 8.1 관련 문서

| 문서 | 위치 | 설명 |
|------|------|------|
| 현재 분석 보고서 | `D5/IQR_ANALYSIS_REPORT_D5_KO.md` | Standard IQR 결과 |
| 주의 태그 보고서 | `ATTENTION_TAGS_REPORT.md` | 고위험 태그 현황 |
| 방법론 연구 | `analysis_output/outlier_methodology_research/` | 비교 분석 |

### 8.2 D5 강종 특성

- **용도**: 중고탄소강, 고강도 용도
- **압연 특성**: 저속 압연 빈도 높음, 토크 변동 큼
- **데이터 특성**: 음의 왜도 강함, 월별 변동성 큼

---

*본 계획서는 D5 강종의 Adjusted IQR 적용을 위한 가이드라인으로, 4개 강종 중 가장 심각한 과다 탐지 문제 해결에 중점을 두었습니다. c=1.0 강한 보정 적용을 권장합니다.*

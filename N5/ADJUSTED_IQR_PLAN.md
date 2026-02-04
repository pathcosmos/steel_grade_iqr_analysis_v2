# N5 강종 Adjusted IQR 적용 계획서

> **강종**: N5 (저합금강)
> **작성일**: 2026-02-03
> **분석 기간**: 2025-04 ~ 2025-08 (5개월)
> **목적**: Standard IQR에서 Adjusted IQR로 전환하여 과다 탐지 문제 해결

---

## 1. 현재 분석 상태 요약

### 1.1 기본 현황

| 항목 | 값 |
|------|-----|
| **총 레코드 수** | **148,239건** (4개 강종 중 최다) |
| **분석 기간** | 2025-04 ~ 2025-08 (5개월) |
| **분석 태그 수** | 79개 |
| **평균 이상치율** | 6.43% |
| **최대 이상치율** | 27.90% (PR6L1_ACT_TORQUE) |

### 1.2 위험도별 태그 분포

| 위험도 | 기준 | 태그 수 | 비율 |
|--------|------|---------|------|
| 🔴 CRITICAL | ≥25% | 1개 | 1.3% |
| 🟠 DANGER | 15-25% | 16개 | 20.3% |
| 🟡 WARNING | 10-15% | 5개 | 6.3% |
| 🟢 CAUTION | 5-10% | 11개 | 13.9% |
| ⚪ NORMAL | <5% | 46개 | 58.2% |

### 1.3 카테고리별 이상치율 분포

| 카테고리 | 태그 수 | 평균 이상치율 | 최대 이상치율 | 주요 문제 태그 |
|----------|:-------:|:-------------:|:-------------:|----------------|
| **01_Furnace_Top_Temperature** | **4** | **13.8%** | **15.6%** | SOAKING_TOP_ZONE_NO_1 |
| 02_Furnace_Bottom_Temperature | 4 | 4.8% | 6.8% | SOAKING_BOTTOM_ZONE |
| 03_Furnace_Discharge_Temperature | 1 | 7.1% | 7.1% | FURNACE_EXIT |
| 04_Furnace_Auxiliary | 10 | 8.7% | 20.9% | FURNACE_O2_ANALYZER |
| 05_Stand_Torque | 16 | 0.8% | 3.2% | - |
| **06_Stand_Speed** | **15** | **21.6%** | **22.5%** | STAND_9_ACTUAL_SPEED |
| 07_Stand_Load | 15 | 0.0% | 0.0% | - |
| 08_Pinchroll | 8 | 0.8% | 6.5% | PINCHROLL_4_ACTUAL_TORQUE |
| **09_PR_Detailed** | **6** | **7.5%** | **27.9%** | PR6L1_ACT_TORQUE |

### 1.4 고이상치 태그 목록 (>15%)

| 순위 | 태그명 | 카테고리 | 이상치율 | 방향 |
|:----:|--------|----------|:--------:|:----:|
| 1 | **PR6L1_ACT_TORQUE** | PR_Detailed | **27.90%** | lower |
| 2 | STAND_9_ACTUAL_SPEED | Stand_Speed | 22.52% | lower |
| 3 | STAND_12_ACTUAL_SPEED | Stand_Speed | 21.98% | lower |
| 4 | STAND_11_ACTUAL_SPEED | Stand_Speed | 21.96% | lower |
| 5 | STAND_10_ACTUAL_SPEED | Stand_Speed | 21.94% | lower |
| 6 | STAND_14_ACTUAL_SPEED | Stand_Speed | 21.93% | lower |
| 7 | FINISHING_BLOCK_ACTUAL_SPEED | Stand_Speed | 21.21% | lower |
| 8 | STAND_1_ACTUAL_SPEED | Stand_Speed | 21.54% | lower |
| 9 | STAND_4_ACTUAL_SPEED | Stand_Speed | 21.52% | lower |
| 10 | STAND_8_ACTUAL_SPEED | Stand_Speed | 21.46% | lower |
| 11 | STAND_3_ACTUAL_SPEED | Stand_Speed | 21.44% | lower |
| 12 | STAND_5_ACTUAL_SPEED | Stand_Speed | 21.42% | lower |
| 13 | STAND_6_ACTUAL_SPEED | Stand_Speed | 21.41% | lower |
| 14 | STAND_2_ACTUAL_SPEED | Stand_Speed | 21.28% | lower |
| 15 | STAND_7_ACTUAL_SPEED | Stand_Speed | 21.58% | lower |
| 16 | STAND_13_ACTUAL_SPEED | Stand_Speed | 21.64% | lower |
| 17 | FURNACE_O2_ANALYZER | Furnace_Auxiliary | 20.90% | lower |
| 18 | SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | Furnace_Top | 15.61% | lower |
| 19 | SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | Furnace_Top | 15.05% | lower |

---

## 2. 데이터 분포 특성

### 2.1 왜도(Skewness) 분석

N5 강종의 `direction` 필드를 기반으로 왜도 추정:

| 방향 패턴 | 태그 수 | 의미 | Adjusted IQR 적용 효과 |
|-----------|:-------:|------|------------------------|
| **lower** | **43개** | 왼쪽 꼬리 (음의 왜도) | 하한 경계 확대, 상한 경계 축소 |
| upper | 15개 | 오른쪽 꼬리 (양의 왜도) | 상한 경계 확대, 하한 경계 축소 |
| balanced | 21개 | 대칭 분포 | 변화 미미 |

### 2.2 N5 강종의 특징적 문제

**문제 1: 가열로 상부 온도 이상치 집중**

N5만의 특이점 - 가열로 상부 온도 4개 태그 모두 높은 이상치율:

| 태그명 | B5 | D4 | D5 | N5 |
|--------|:---:|:---:|:---:|:---:|
| SOAKING_TOP_ZONE_NO_1 | 5.3% | 2.8% | 9.6% | **15.6%** |
| SOAKING_TOP_ZONE_NO_2 | 3.9% | 2.8% | 9.6% | **15.1%** |
| HEATING_TOP_ZONE_NO_1 | 9.9% | 2.0% | 9.2% | **13.2%** |
| HEATING_TOP_ZONE_NO_2 | 9.5% | 1.9% | 9.2% | **13.3%** |

→ N5 강종의 **가열 온도 조건이 다른 강종과 상이**함을 시사

**문제 2: PR6L1_ACT_TORQUE CRITICAL 수준**

| 강종 | 이상치율 | 방향 |
|------|:--------:|:----:|
| B5 | 17.92% | balanced |
| D4 | 5.27% | upper |
| D5 | 10.15% | upper |
| **N5** | **27.90%** | **lower** |

→ N5에서만 **lower 방향 이상치 집중** - 강종별 토크 특성 차이

**문제 3: 스탠드 속도 전체 21% 이상치율**
```
STAND_1~14 + FINISHING_BLOCK: 모두 21.2-22.5% 이상치율
모든 방향: lower (하한 미달)
→ D4, D5와 유사한 패턴, Adjusted IQR 적용 효과 기대
```

### 2.3 월별 이상치율 분포

| 월 | 레코드 수 | 특이사항 |
|----|:---------:|----------|
| 2025-04 | 33,118 | 14.5% 이상치율 |
| 2025-05 | 34,542 | 5.5% 이상치율 (최저) |
| **2025-06** | **64,752** | **14.5% 이상치율, 최다 레코드** |
| 2025-07 | 12,949 | 24.2% 이상치율 (최고) |
| 2025-08 | 2,878 | 13.3% 이상치율 |

→ **7월 데이터 특별 분석** 필요 (이상치율 최고)

---

## 3. Adjusted IQR 적용 계획

### 3.1 N5 맞춤 보정 전략

N5는 lower 방향 이상치가 많지만 데이터량이 가장 많아 통계적으로 안정적.
**c=0.8~0.9** 권장:

```python
def calculate_n5_adjusted_iqr(data, c=0.85):
    """N5 강종 맞춤 Adjusted IQR"""
    q1, median, q3 = np.percentile(data, [25, 50, 75])
    iqr = q3 - q1

    # Bowley 왜도 계산
    bowley_skew = (q3 + q1 - 2 * median) / iqr if iqr > 0 else 0

    # N5: lower 방향 이상치 → 음의 왜도
    # 중간 강도 보정 (c=0.85)
    if bowley_skew >= 0:
        lower_mult = np.exp(-c * bowley_skew)
        upper_mult = np.exp(+c * bowley_skew)
    else:
        lower_mult = np.exp(+c * abs(bowley_skew))  # 하한 확대
        upper_mult = np.exp(-c * abs(bowley_skew))  # 상한 축소

    lower_bound = q1 - 1.5 * iqr * lower_mult
    upper_bound = q3 + 1.5 * iqr * upper_mult

    return lower_bound, upper_bound, bowley_skew
```

### 3.2 적용 대상 태그 우선순위

#### 1순위: CRITICAL 태그 즉시 적용
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| **PR6L1_ACT_TORQUE** | **27.90%** | lower | 하한 확대로 7-9%p 감소 |

#### 2순위: 스탠드 속도 전체 (DANGER)
| 태그 그룹 | 현재 범위 | 방향 | 예상 효과 |
|-----------|:---------:|:----:|----------|
| STAND_1~14 + FINISHING_BLOCK | 21.2-22.5% | 모두 lower | 하한 확대로 5-6%p 감소 |

→ **15개 태그 동일 보정 계수(c=0.85) 일괄 적용** 권장

#### 3순위: FURNACE_O2_ANALYZER (DANGER)
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| FURNACE_O2_ANALYZER | 20.90% | lower | 하한 확대로 5-6%p 감소 |

**참고**: D4와 N5에서만 높은 이상치율 → 강종별 특성 반영 필요

#### 4순위: 가열로 상부 온도 (DANGER/WARNING)
| 태그명 | 현재 이상치율 | 방향 | 예상 효과 |
|--------|:-------------:|:----:|----------|
| SOAKING_TOP_ZONE_NO_1 | 15.61% | lower | 3-4%p 감소 |
| SOAKING_TOP_ZONE_NO_2 | 15.05% | lower | 3-4%p 감소 |
| HEATING_TOP_ZONE_NO_1 | 13.19% | lower | 2-3%p 감소 |
| HEATING_TOP_ZONE_NO_2 | 13.32% | lower | 2-3%p 감소 |

---

## 4. 예상 효과

### 4.1 이상치율 감소 예측

| 구분 | Standard IQR | Adjusted IQR (c=0.85) | 감소폭 |
|------|:------------:|:---------------------:|:------:|
| **평균 이상치율** | **6.43%** | **4.3-5.0%** | **1.4-2.1%p** |
| 최대 이상치율 | 27.90% | 18-20% | 8-10%p |
| CRITICAL 태그 수 | 1개 | **0개** | 1개 감소 |
| DANGER 태그 수 | 16개 | **6-8개** | 8-10개 감소 |
| >10% 태그 수 | 22개 | **10-12개** | 10-12개 감소 |

### 4.2 카테고리별 예상 효과

| 카테고리 | 현재 평균 | 예상 평균 (c=0.85) | 개선율 |
|----------|:---------:|:------------------:|:------:|
| **06_Stand_Speed** | **21.6%** | **14-16%** | **25-35%** |
| **01_Furnace_Top_Temperature** | **13.8%** | **9-11%** | **20-30%** |
| 04_Furnace_Auxiliary | 8.7% | 5-6% | 30-40% |
| 09_PR_Detailed | 7.5% | 4-5% | 35-45% |

### 4.3 위험도 전환 예상

**CRITICAL → DANGER**:
1. PR6L1_ACT_TORQUE: 27.90% → 18-20%

**DANGER → WARNING**:
1. STAND_1~14 + FINISHING_BLOCK (15개): 21.2-22.5% → 14-16%
2. FURNACE_O2_ANALYZER: 20.90% → 14-16%
3. SOAKING_TOP_ZONE 2개: 15.0-15.6% → 11-12%

**WARNING → CAUTION**:
1. HEATING_TOP_ZONE 2개: 13.2-13.3% → 9-10%

---

## 5. 구현 단계

### Phase 1: CRITICAL 태그 및 특이 태그 시범 적용 (권장 1주)

**대상**:
- PR6L1_ACT_TORQUE (CRITICAL)
- FURNACE_O2_ANALYZER (N5 특이)

**작업 내용**:
1. Bowley 왜도 계산 및 분포 분석
2. c=0.8, 0.85, 0.9 비교 분석
3. D4와 동일 태그 비교 (FURNACE_O2_ANALYZER)
4. Standard vs Adjusted 비교 차트 생성

**산출물**:
- `N5_adjusted_iqr_pilot_results.json`
- `N5_pr6l1_comparison.png`
- `N5_D4_furnace_o2_comparison.md`

### Phase 2: 스탠드 속도 일괄 적용 (권장 1주)

**대상**: STAND_1~14_ACTUAL_SPEED + FINISHING_BLOCK_ACTUAL_SPEED (15개)

**작업 내용**:
1. 스탠드 속도 그룹 공통 왜도 분석
2. c=0.85 일괄 적용
3. D4, D5 결과와 비교 분석

**산출물**:
- `N5_stand_speed_adjusted_results.json`
- `N5_stand_speed_all_grades_comparison.png`

### Phase 3: 가열로 온도 태그 적용 (권장 1주)

**대상**: 가열로 상부 온도 4개 태그

**작업 내용**:
1. N5 특이 패턴 분석 (다른 강종 대비)
2. 월별 온도 변동 분석
3. 7월 이상치 급증 원인 분석

**산출물**:
- `N5_furnace_top_analysis.json`
- `N5_july_anomaly_report.md`

### Phase 4: 전체 적용 및 검증 (권장 2주)

**작업 내용**:
1. 전체 79개 태그 Adjusted IQR 적용
2. 월별 분석 (5개월 개별)
3. 4개 강종 종합 비교
4. 도메인 전문가 검증

**산출물**:
- `iqr_analysis_N5_adjusted_results.json`
- `IQR_ANALYSIS_REPORT_N5_ADJUSTED_KO.md`
- `ALL_GRADES_ADJUSTED_IQR_COMPARISON.md`

---

## 6. N5 강종 특별 고려사항

### 6.1 최다 데이터량 활용

N5는 148,239건으로 가장 많은 데이터를 보유:

**장점**:
- 통계적 안정성 높음
- 월별 분석 신뢰도 우수
- Bowley 왜도 계산 정확도 높음

**활용**:
```python
# N5 결과를 다른 강종 보정 계수 참조값으로 활용
n5_optimal_c = determine_optimal_c(n5_data)

# 데이터 부족 강종(B5 등)에 참조 적용
for grade in ['B5', 'D4']:
    if data_count[grade] < 20000:
        recommended_c = n5_optimal_c * 0.95  # 보수적 적용
```

### 6.2 가열로 온도 특이 패턴 분석

N5에서만 가열로 상부 온도 이상치가 높은 이유 분석:

```python
def analyze_furnace_temp_pattern(df, grades=['B5', 'D4', 'D5', 'N5']):
    """강종별 가열로 온도 패턴 비교"""
    results = {}

    for grade in grades:
        grade_data = df[df['steel_grade'] == grade]

        # 온도 분포 비교
        temp_stats = {
            'mean': grade_data['SOAKING_TOP_ZONE_NO_1'].mean(),
            'std': grade_data['SOAKING_TOP_ZONE_NO_1'].std(),
            'q1': grade_data['SOAKING_TOP_ZONE_NO_1'].quantile(0.25),
            'median': grade_data['SOAKING_TOP_ZONE_NO_1'].median(),
            'q3': grade_data['SOAKING_TOP_ZONE_NO_1'].quantile(0.75)
        }

        results[grade] = temp_stats

    return results
```

**추정 원인**:
1. N5 강종의 목표 가열 온도가 다른 강종보다 낮음
2. 온도 제어 범위가 좁아 IQR 경계 민감
3. 특정 월(7월)에 온도 변동 큼

### 6.3 7월 이상치 급증 분석

7월 데이터에서 24.2% 이상치율의 원인:

```python
def analyze_july_anomaly(df):
    """7월 이상치 급증 분석"""
    july_data = df[df['month'] == '2025-07']

    # 1. 일별 패턴 분석
    daily_outlier_rate = july_data.groupby('date').apply(
        lambda x: x['is_outlier'].mean()
    )

    # 2. 피크 일자 식별
    peak_dates = daily_outlier_rate[daily_outlier_rate > 0.3].index

    # 3. 시간대별 패턴
    hourly_pattern = july_data.groupby('hour')['is_outlier'].mean()

    return peak_dates, hourly_pattern, daily_outlier_rate
```

### 6.4 PR6L1_ACT_TORQUE 강종별 비교

이 태그는 강종별로 매우 다른 패턴을 보임:

```python
pr6l1_comparison = {
    'B5': {'rate': 17.92, 'direction': 'balanced', 'c_rec': 0.8},
    'D4': {'rate': 5.27, 'direction': 'upper', 'c_rec': 0.8},
    'D5': {'rate': 10.15, 'direction': 'upper', 'c_rec': 0.8},
    'N5': {'rate': 27.90, 'direction': 'lower', 'c_rec': 0.9}  # 강한 보정 필요
}
```

→ N5의 PR6L1은 **개별 보정 계수(c=0.9)** 적용 권장

---

## 7. 위험 요소 및 대응 방안

### 7.1 위험 요소

| 위험 | 영향도 | 대응 방안 |
|------|:------:|----------|
| 가열로 온도 과소 탐지 | 높음 | 온도 태그는 c=0.8 보수적 적용 |
| PR6L1 개별 보정 필요 | 중간 | c=0.9 별도 적용 |
| 7월 데이터 특이성 | 중간 | 7월 별도 분석, 필요시 가중치 조정 |

### 7.2 롤백 기준

1. 가열로 온도 이상치율이 5% 미만으로 급감
2. PR6L1 실제 토크 이상 미탐지
3. 도메인 전문가 피드백에 따른 조정

### 7.3 모니터링 지표

```python
monitoring_metrics = {
    'avg_outlier_rate': 'target: 4.3-5.0%',
    'max_outlier_rate': 'target: < 20%',
    'critical_tags': 'target: 0',
    'furnace_top_avg': 'target: 9-11%',
    'stand_speed_avg': 'target: 14-16%'
}
```

---

## 8. 4개 강종 종합 비교 및 권장 사항

### 8.1 강종별 권장 보정 계수

| 강종 | 데이터량 | 현재 평균 | 권장 c 값 | 예상 결과 |
|------|:--------:|:---------:|:---------:|:---------:|
| B5 | 14,391 | 4.66% | 0.8 | 3.7-4.0% |
| D4 | 20,144 | 5.18% | 0.8-1.0 | 3.5-4.2% |
| D5 | 74,855 | **8.11%** | **1.0** | 4.5-5.5% |
| **N5** | **148,239** | 6.43% | **0.85** | 4.3-5.0% |

### 8.2 강종별 주요 문제 태그 및 해결 전략

| 강종 | 주요 문제 | 해결 전략 |
|------|----------|----------|
| B5 | 핀치롤/PR 토크 | c=0.8 표준 적용 |
| D4 | 스탠드 속도 전체 + FINISHING_BLOCK | 스탠드 일괄 c=0.8-1.0 |
| D5 | 스탠드 속도 + 핀치롤 (최심각) | c=1.0 강한 보정 |
| N5 | PR6L1 + 가열로 온도 | 태그별 차등 (0.8-0.9) |

### 8.3 공통 적용 가이드라인

```python
adjusted_iqr_guidelines = {
    # 기본 설정
    'default_c': 0.8,

    # 강종별 조정
    'grade_specific': {
        'B5': 0.8,
        'D4': 0.9,  # 스탠드 속도 문제
        'D5': 1.0,  # 가장 심각
        'N5': 0.85  # 중간
    },

    # 태그 유형별 조정
    'tag_type_adjustment': {
        'stand_speed': +0.1,  # 더 강한 보정
        'pinchroll': +0.05,
        'furnace_temp': 0,  # 보수적 유지
        'furnace_aux': +0.05
    }
}
```

---

## 9. 참고 자료

### 9.1 관련 문서

| 문서 | 위치 | 설명 |
|------|------|------|
| 현재 분석 보고서 | `N5/IQR_ANALYSIS_REPORT_N5_KO.md` | Standard IQR 결과 |
| 주의 태그 보고서 | `ATTENTION_TAGS_REPORT.md` | 강종별 고위험 태그 |
| 방법론 연구 | `analysis_output/outlier_methodology_research/` | 비교 분석 |
| 기존 Adjusted IQR 코드 | `scripts/outlier_methodology_analysis.py` | 참조 구현 |

### 9.2 N5 강종 특성

- **용도**: 저합금강, 고인성 용도
- **데이터량**: 4개 강종 중 최다 (148,239건)
- **압연 특성**: 안정적, 월별 변동 있음
- **특이점**: 가열로 온도 이상치 높음, PR6L1 CRITICAL

---

*본 계획서는 N5 강종의 Adjusted IQR 적용을 위한 가이드라인입니다. 최다 데이터량을 활용하여 다른 강종의 참조값으로도 활용할 수 있습니다.*

# 강종 [D5 / D13] Adjusted IQR 상세 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D5
**규격**: D13
**분석 방법**: Adjusted IQR (Bowley 왜도 보정)
**c 값**: 1.0
**생성일시**: 2026-02-06 17:25:14

---

## Executive Summary

### Adjusted IQR 방법론 개요

Adjusted IQR은 데이터 분포의 비대칭성(왜도)을 고려하여 이상치 경계를 동적으로 조정하는 방법입니다.

**계산 공식:**
- Bowley 왜도: `(Q3 + Q1 - 2×Median) / IQR`
- 양의 왜도 (Right-skewed):
  - Lower Mult = exp(-c × skew)
  - Upper Mult = exp(+c × skew)
- 음의 왜도 (Left-skewed):
  - Lower Mult = exp(+c × |skew|)
  - Upper Mult = exp(-c × |skew|)
- Adjusted Bounds: Q1 - 1.5×IQR×Lower_Mult, Q3 + 1.5×IQR×Upper_Mult

### 분석 개요

| 구분 | 내용 |
|------|------|
| **분석 대상 강종** | D5 / D13 |
| **c 값 (왜도 보정 강도)** | 1.0 |
| **총 분석 태그 수** | 78개 |
| **PR_Detailed L1 태그** | 4개 |
| **PR_Detailed L2 태그** | 2개 |

### 이상치율 개선 효과

| 지표 | Standard IQR | Adjusted IQR | 개선 |
|------|-------------|--------------|------|
| **총 이상치 수** | 26,781 | 23,903 | 2,878 감소 |
| **평균 개선율** | - | - | **-0.2%** |

### 위험도 분포 비교

| 등급 | Standard IQR | Adjusted IQR | 변화 |
|------|-------------|--------------|------|
| **⚫ 심각 (25% 이상)** | 0개 | 0개 | +0 |
| **🔴 위험 (15~25%)** | 6개 | 5개 | +1 |
| **🟠 경고 (10~15%)** | 0개 | 2개 | -2 |
| **🟡 주의 (5~10%)** | 6개 | 3개 | +3 |
| **🟢 양호 (0~5%)** | 66개 | 68개 | +2 |

---

## 카테고리별 상세 분석


### 01_Furnace_Top_Temperature (가열로 상부 온도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 19.58% | 19.84% | 1.3% | -0.2459 | 1.279/0.782 | 🔴 DANGER |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 19.08% | 19.67% | 3.0% | -0.2707 | 1.311/0.763 | 🔴 DANGER |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 0.51% | 7.81% | 93.5% | -0.5353 | 1.708/0.585 | 🟢 NORMAL |
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 0.50% | 7.58% | 93.4% | -0.5423 | 1.720/0.581 | 🟢 NORMAL |

### 02_Furnace_Bottom_Temperature (가열로 하부 온도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 21.40% | 19.86% | -7.8% | -0.5449 | 1.724/0.580 | 🔴 DANGER |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 20.75% | 19.70% | -5.3% | -0.5399 | 1.716/0.583 | 🔴 DANGER |
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 5.29% | 4.51% | -17.2% | -0.1054 | 1.111/0.900 | 🟡 CAUTION |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 3.30% | 3.67% | 10.2% | -0.1784 | 1.195/0.837 | 🟢 NORMAL |

### 03_Furnace_Discharge_Temperature (가열로 추출 온도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 11.65% | 9.83% | -18.6% | 0.4898 | 0.613/1.632 | 🟠 WARNING |

### 04_Furnace_Auxiliary (가열로 보조설비)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| MAIN_COMBUSTION_AIR_PRESSURE | 22.73% | 22.71% | -0.1% | -0.8320 | 2.298/0.435 | 🔴 DANGER |
| INDIRECT_COOLING_WATER_FLOW | 9.52% | 9.70% | 1.8% | 0.0563 | 0.945/1.058 | 🟡 CAUTION |
| MAIN_GAS_PRESSURE | 3.63% | 2.69% | -35.0% | -0.2309 | 1.260/0.794 | 🟢 NORMAL |
| COMBUSTION_AIR_TEMPERATURE | 0.56% | 0.20% | -175.0% | -0.4169 | 1.517/0.659 | 🟢 NORMAL |
| FURNACE_PRESSURE | 0.26% | 0.26% | 0.0% | 0.0239 | 0.976/1.024 | 🟢 NORMAL |
| MAIN_GAS_TEMPERATURE | 0.00% | 0.00% | 0.0% | -0.4994 | 1.648/0.607 | 🟢 NORMAL |
| MAIN_GAS_FLOW | 0.00% | 0.00% | 0.0% | -0.0737 | 1.076/0.929 | 🟢 NORMAL |
| FURNACE_O2_ANALYZER | 0.00% | 0.00% | 0.0% | -0.1316 | 1.141/0.877 | 🟢 NORMAL |
| INDIRECT_WATER_MAIN_TEMPERATURE | 0.00% | 0.00% | 0.0% | 0.3777 | 0.685/1.459 | 🟢 NORMAL |

### 05_Stand_Torque (스탠드 토크)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| STAND_1_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9637 | 0.381/2.621 | 🟢 NORMAL |
| STAND_2_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9536 | 0.385/2.595 | 🟢 NORMAL |
| STAND_3_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9597 | 0.383/2.611 | 🟢 NORMAL |
| STAND_4_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9409 | 0.390/2.562 | 🟢 NORMAL |
| STAND_5_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9532 | 0.386/2.594 | 🟢 NORMAL |
| STAND_6_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9132 | 0.401/2.492 | 🟢 NORMAL |
| STAND_7_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9068 | 0.404/2.476 | 🟢 NORMAL |
| STAND_8_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.8579 | 0.424/2.358 | 🟢 NORMAL |
| STAND_9_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9529 | 0.386/2.593 | 🟢 NORMAL |
| STAND_10_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9093 | 0.403/2.483 | 🟢 NORMAL |
| STAND_11_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9249 | 0.397/2.522 | 🟢 NORMAL |
| STAND_12_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.8702 | 0.419/2.387 | 🟢 NORMAL |
| STAND_13_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.9010 | 0.406/2.462 | 🟢 NORMAL |
| STAND_14_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.7939 | 0.452/2.212 | 🟢 NORMAL |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.7952 | 0.451/2.215 | 🟢 NORMAL |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | 0.7956 | 0.451/2.216 | 🟢 NORMAL |

### 06_Stand_Speed (스탠드 속도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| STAND_1_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9713 | 2.641/0.379 | 🟢 NORMAL |
| STAND_2_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9651 | 2.625/0.381 | 🟢 NORMAL |
| STAND_3_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9581 | 2.607/0.384 | 🟢 NORMAL |
| STAND_4_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9686 | 2.634/0.380 | 🟢 NORMAL |
| STAND_5_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9573 | 2.605/0.384 | 🟢 NORMAL |
| STAND_6_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9765 | 2.655/0.377 | 🟢 NORMAL |
| STAND_7_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9554 | 2.600/0.385 | 🟢 NORMAL |
| STAND_8_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.7658 | 2.151/0.465 | 🟢 NORMAL |
| STAND_9_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.8676 | 2.381/0.420 | 🟢 NORMAL |
| STAND_10_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9801 | 2.665/0.375 | 🟢 NORMAL |
| STAND_11_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9684 | 2.634/0.380 | 🟢 NORMAL |
| STAND_12_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9699 | 2.638/0.379 | 🟢 NORMAL |
| STAND_13_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9669 | 2.630/0.380 | 🟢 NORMAL |
| STAND_14_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9720 | 2.643/0.378 | 🟢 NORMAL |
| FINISHING_BLOCK_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.9767 | 2.656/0.377 | 🟢 NORMAL |

### 07_Stand_Load (스탠드 부하)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| STAND_1_LOAD | 0.00% | 0.00% | 0.0% | 0.4980 | 0.608/1.645 | 🟢 NORMAL |
| STAND_2_LOAD | 0.00% | 0.00% | 0.0% | 0.5520 | 0.576/1.737 | 🟢 NORMAL |
| STAND_3_LOAD | 0.00% | 0.00% | 0.0% | 0.5553 | 0.574/1.743 | 🟢 NORMAL |
| STAND_4_LOAD | 0.00% | 0.00% | 0.0% | 0.5237 | 0.592/1.688 | 🟢 NORMAL |
| STAND_5_LOAD | 0.00% | 0.00% | 0.0% | 0.5047 | 0.604/1.656 | 🟢 NORMAL |
| STAND_6_LOAD | 0.00% | 0.00% | 0.0% | 0.5290 | 0.589/1.697 | 🟢 NORMAL |
| STAND_7_LOAD | 0.00% | 0.00% | 0.0% | 0.5070 | 0.602/1.660 | 🟢 NORMAL |
| STAND_8_LOAD | 0.00% | 0.00% | 0.0% | 0.5237 | 0.592/1.688 | 🟢 NORMAL |
| STAND_9_LOAD | 0.00% | 0.00% | 0.0% | 0.5537 | 0.575/1.740 | 🟢 NORMAL |
| STAND_10_LOAD | 0.00% | 0.00% | 0.0% | 0.5410 | 0.582/1.718 | 🟢 NORMAL |
| STAND_11_LOAD | 0.00% | 0.00% | 0.0% | 0.5437 | 0.581/1.722 | 🟢 NORMAL |
| STAND_12_LOAD | 0.00% | 0.00% | 0.0% | 0.5403 | 0.583/1.717 | 🟢 NORMAL |
| STAND_13_LOAD | 0.00% | 0.00% | 0.0% | 0.5403 | 0.583/1.717 | 🟢 NORMAL |
| STAND_14_LOAD | 0.00% | 0.00% | 0.0% | 0.5513 | 0.576/1.736 | 🟢 NORMAL |
| FINISHING_BLOCK_LOAD | 0.00% | 0.00% | 0.0% | 0.5493 | 0.577/1.732 | 🟢 NORMAL |

### 08_Pinchroll (핀치롤)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| PINCHROLL_3_ACTUAL_SPEED | 12.33% | 4.98% | -147.4% | 0.6477 | 0.523/1.911 | 🟠 WARNING |
| PINCHROLL_2_ACTUAL_SPEED | 1.30% | 5.26% | 75.3% | -0.7432 | 2.103/0.476 | 🟢 NORMAL |
| PINCHROLL_4_ACTUAL_SPEED | 1.23% | 1.23% | 0.0% | 0.8043 | 0.447/2.235 | 🟢 NORMAL |
| PINCHROLL_2_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.9999 | 2.718/0.368 | 🟢 NORMAL |
| PINCHROLL_3_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6317 | 1.881/0.532 | 🟢 NORMAL |
| PINCHROLL_4_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6219 | 1.862/0.537 | 🟢 NORMAL |
| PINCHROLL_3_REFERENCE_TORQUE | 0.00% | 0.00% | 0.0% | 0.6737 | 0.510/1.961 | 🟢 NORMAL |
| PINCHROLL_4_REFERENCE_TORQUE | 0.00% | 0.00% | 0.0% | 0.6747 | 0.509/1.964 | 🟢 NORMAL |

### 09_PR_Detailed (PR 상세 토크)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| [L2] PR6L2_ACT_TORQUE | 5.01% | 5.59% | 10.3% | 0.4555 | 0.634/1.577 | 🟡 CAUTION |
| [L1] PR6L1_ACT_TORQUE | 0.00% | 17.35% | 100.0% | 0.8474 | 0.429/2.334 | 🟢 NORMAL |
| [L1] PR7L1_ACT_TORQUE | 0.00% | 0.00% | 0.0% | 0.9233 | 0.397/2.518 | 🟢 NORMAL |
| [L2] PR7L2_ACT_TORQUE | 0.00% | 0.00% | 0.0% | 0.9299 | 0.395/2.534 | 🟢 NORMAL |
| [L1] PR8L1_ACT_TORQUE | 0.00% | 0.00% | 0.0% | 0.9349 | 0.393/2.547 | 🟢 NORMAL |
| [L1] PR9L1_ACT_TORQUE | 0.00% | 0.00% | 0.0% | -0.8371 | 2.310/0.433 | 🟢 NORMAL |

---

## 태그별 상세 분석 (위험도 순)


### 🔴 위험 (15~25%) - 5개 태그

#### MAIN_COMBUSTION_AIR_PRESSURE 🔴

**위험도**: [DANGER] | **이상치율**: 22.73% | **개선율**: -0.1%
**Bowley 왜도**: -0.8320 | **승수 (L/U)**: 2.298/0.435

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,600 | 3,597 |
| 이상치율 | 22.73% | 22.71% |
| 하한 경계 | 1055.1877 | 1099.4865 |
| 상한 경계 | 1171.2211 | 1190.4985 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 1102.0335 |
| 표준편차 | 96.0887 |
| Q1 (25%) | 1133.6160 |
| 중앙값 | 1154.4580 |
| Q3 (75%) | 1156.3690 |
| IQR | 22.7530 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 1113.06 | 18.15% | 18.08% |
| 2025-08 | 11,520 | 1097.90 | 24.44% | 24.44% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 2,816 |
| 2 | 2025-05-09 | 482 |
| 3 | 2025-05-28 | 302 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 2,816건 (2025-08-08)
- 평균 일별 이상치: 1200.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_COMBUSTION_AIR_PRESSURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 1113.0585 |
| 중앙값 | 1154.4870 |
| IQR | 9.6420 |
| Bowley 왜도 | -0.5763 |
| Adj 이상치 수 | 794 |
| Adj 이상치율 | 18.38% |
| Std 이상치율 | 18.36% |
| 개선율 | -0.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 484건
- 2. 2025-05-28: 310건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1097.9002 |
| 중앙값 | 1154.4285 |
| IQR | 42.9302 |
| Bowley 왜도 | -0.9127 |
| Adj 이상치 수 | 2,816 |
| Adj 이상치율 | 24.44% |
| Std 이상치율 | 24.44% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 2,816건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

---

#### SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 🔴

**위험도**: [DANGER] | **이상치율**: 21.40% | **개선율**: -7.8%
**Bowley 왜도**: -0.5449 | **승수 (L/U)**: 1.724/0.580

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,390 | 3,146 |
| 이상치율 | 21.40% | 19.86% |
| 하한 경계 | 911.3563 | 971.5377 |
| 상한 경계 | 1158.1872 | 1193.0878 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 1051.6964 |
| 표준편차 | 102.4045 |
| Q1 (25%) | 1054.6190 |
| 중앙값 | 1097.4020 |
| Q3 (75%) | 1110.0065 |
| IQR | 55.3875 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 1073.07 | 29.03% | 19.68% |
| 2025-08 | 11,520 | 1043.68 | 18.54% | 19.93% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 2,136 |
| 2 | 2025-05-09 | 866 |
| 3 | 2025-05-28 | 388 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 2,136건 (2025-08-08)
- 평균 일별 이상치: 1130.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 1073.0734 |
| 중앙값 | 1114.8720 |
| IQR | 68.4735 |
| Bowley 왜도 | -0.1345 |
| Adj 이상치 수 | 834 |
| Adj 이상치율 | 19.31% |
| Std 이상치율 | 19.89% |
| 개선율 | 2.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 506건
- 2. 2025-05-28: 328건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1043.6819 |
| 중앙값 | 1088.8095 |
| IQR | 53.8322 |
| Bowley 왜도 | -0.3307 |
| Adj 이상치 수 | 2,232 |
| Adj 이상치율 | 19.38% |
| Std 이상치율 | 19.93% |
| 개선율 | 2.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 2,232건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

---

#### SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 🔴

**위험도**: [DANGER] | **이상치율**: 20.75% | **개선율**: -5.3%
**Bowley 왜도**: -0.5399 | **승수 (L/U)**: 1.716/0.583

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,286 | 3,120 |
| 이상치율 | 20.75% | 19.70% |
| 하한 경계 | 883.7259 | 944.8925 |
| 상한 경계 | 1137.0893 | 1172.7365 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 1029.3343 |
| 표준편차 | 101.3005 |
| Q1 (25%) | 1030.3340 |
| 중앙값 | 1074.1920 |
| Q3 (75%) | 1087.2950 |
| IQR | 56.9610 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 1051.20 | 28.11% | 19.26% |
| 2025-08 | 11,520 | 1021.14 | 17.99% | 19.86% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 2,072 |
| 2 | 2025-05-09 | 870 |
| 3 | 2025-05-28 | 344 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 2,072건 (2025-08-08)
- 평균 일별 이상치: 1095.3건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 1051.1995 |
| 중앙값 | 1091.0450 |
| IQR | 65.3820 |
| Bowley 왜도 | -0.1051 |
| Adj 이상치 수 | 834 |
| Adj 이상치율 | 19.31% |
| Std 이상치율 | 19.63% |
| 개선율 | 1.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 502건
- 2. 2025-05-28: 332건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1021.1368 |
| 중앙값 | 1065.5735 |
| IQR | 56.3980 |
| Bowley 왜도 | -0.3535 |
| Adj 이상치 수 | 2,176 |
| Adj 이상치율 | 18.89% |
| Std 이상치율 | 19.86% |
| 개선율 | 4.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 2,176건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

---

#### SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 🔴

**위험도**: [DANGER] | **이상치율**: 19.58% | **개선율**: 1.3%
**Bowley 왜도**: -0.2459 | **승수 (L/U)**: 1.279/0.782

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,101 | 3,142 |
| 이상치율 | 19.58% | 19.84% |
| 하한 경계 | 986.8733 | 1007.3695 |
| 상한 경계 | 1187.4172 | 1203.4455 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 1073.6264 |
| 표준편차 | 100.8191 |
| Q1 (25%) | 1080.8980 |
| 중앙값 | 1111.4340 |
| Q3 (75%) | 1129.9170 |
| IQR | 49.0190 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 1101.70 | 19.19% | 19.77% |
| 2025-08 | 11,520 | 1063.10 | 19.72% | 19.86% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 2,272 |
| 2 | 2025-05-09 | 502 |
| 3 | 2025-05-28 | 327 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 2,272건 (2025-08-08)
- 평균 일별 이상치: 1033.7건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 1101.6996 |
| 중앙값 | 1159.4760 |
| IQR | 77.4780 |
| Bowley 왜도 | -0.8053 |
| Adj 이상치 수 | 23 |
| Adj 이상치율 | 0.53% |
| Std 이상치율 | 18.68% |
| 개선율 | 97.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 12건
- 2. 2025-05-28: 11건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1063.1014 |
| 중앙값 | 1107.1335 |
| IQR | 39.5975 |
| Bowley 왜도 | -0.4218 |
| Adj 이상치 수 | 2,280 |
| Adj 이상치율 | 19.79% |
| Std 이상치율 | 19.93% |
| 개선율 | 0.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 2,280건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

---

#### SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 🔴

**위험도**: [DANGER] | **이상치율**: 19.08% | **개선율**: 3.0%
**Bowley 왜도**: -0.2707 | **승수 (L/U)**: 1.311/0.763

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,022 | 3,115 |
| 이상치율 | 19.08% | 19.67% |
| 하한 경계 | 954.1706 | 979.3590 |
| 상한 경계 | 1176.2237 | 1195.4390 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 1057.1966 |
| 표준편차 | 100.9840 |
| Q1 (25%) | 1060.3890 |
| 중앙값 | 1094.7100 |
| Q3 (75%) | 1114.4090 |
| IQR | 54.0200 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 1085.37 | 19.22% | 19.33% |
| 2025-08 | 11,520 | 1046.63 | 19.03% | 19.79% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 2,192 |
| 2 | 2025-05-09 | 512 |
| 3 | 2025-05-28 | 318 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 2,192건 (2025-08-08)
- 평균 일별 이상치: 1007.3건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 1085.3689 |
| 중앙값 | 1143.5070 |
| IQR | 75.4875 |
| Bowley 왜도 | -0.7657 |
| Adj 이상치 수 | 112 |
| Adj 이상치율 | 2.59% |
| Std 이상치율 | 18.87% |
| 개선율 | 86.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 86건
- 2. 2025-05-28: 26건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1046.6344 |
| 중앙값 | 1090.4105 |
| IQR | 43.5293 |
| Bowley 왜도 | -0.4896 |
| Adj 이상치 수 | 2,192 |
| Adj 이상치율 | 19.03% |
| Std 이상치율 | 19.86% |
| 개선율 | 4.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 2,192건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

---


### 🟠 경고 (10~15%) - 2개 태그

#### PINCHROLL_3_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 12.33% | **개선율**: -147.4%
**Bowley 왜도**: 0.6477 | **승수 (L/U)**: 0.523/1.911

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,195 | 483 |
| 이상치율 | 12.33% | 4.98% |
| 하한 경계 | 1222.0678 | 1201.3665 |
| 상한 경계 | 1356.7238 | 1317.1625 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 1247.7244 |
| 표준편차 | 94.8814 |
| Q1 (25%) | 1244.7900 |
| 중앙값 | 1249.8900 |
| Q3 (75%) | 1273.7390 |
| IQR | 28.9490 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 1273.73 | 0.18% | 0.18% |
| 2025-08 | 6,913 | 1237.26 | 17.21% | 6.91% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 1,190 |
| 2 | 2025-05-09 | 5 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 1,190건 (2025-08-08)
- 평균 일별 이상치: 597.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_3_ACTUAL_SPEED 종합 분석 차트](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 1273.7266 |
| 중앙값 | 1272.8940 |
| IQR | 5.0080 |
| Bowley 왜도 | 0.3450 |
| Adj 이상치 수 | 369 |
| Adj 이상치율 | 13.27% |
| Std 이상치율 | 14.71% |
| 개선율 | 9.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 252건
- 2. 2025-05-28: 117건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 1237.2640 |
| 중앙값 | 1246.9000 |
| IQR | 8.5060 |
| Bowley 왜도 | 0.2384 |
| Adj 이상치 수 | 2,595 |
| Adj 이상치율 | 37.54% |
| Std 이상치율 | 38.52% |
| 개선율 | 2.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 2,595건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

---

#### FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE 🟠

**위험도**: [WARNING] | **이상치율**: 11.65% | **개선율**: -18.6%
**Bowley 왜도**: 0.4898 | **승수 (L/U)**: 0.613/1.632

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,846 | 1,557 |
| 이상치율 | 11.65% | 9.83% |
| 하한 경계 | 957.7954 | 919.2605 |
| 상한 경계 | 1247.5052 | 1184.6165 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 974.5848 |
| 표준편차 | 271.8080 |
| Q1 (25%) | 1018.7690 |
| 중앙값 | 1035.6920 |
| Q3 (75%) | 1085.1080 |
| IQR | 66.3390 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 885.80 | 23.85% | 24.20% |
| 2025-08 | 11,520 | 1007.87 | 7.08% | 4.44% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-09 | 908 |
| 2 | 2025-08-08 | 816 |
| 3 | 2025-05-28 | 122 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 908건 (2025-05-09)
- 평균 일별 이상치: 615.3건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./03_Furnace_Discharge_Temperature/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE 종합 분석 차트](./03_Furnace_Discharge_Temperature/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 885.8032 |
| 중앙값 | 1022.1540 |
| IQR | 64.3080 |
| Bowley 왜도 | -0.4105 |
| Adj 이상치 수 | 1,415 |
| Adj 이상치율 | 32.76% |
| Std 이상치율 | 36.91% |
| 개선율 | 11.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-28: 911건
- 2. 2025-05-09: 504건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1007.8702 |
| 중앙값 | 1047.8770 |
| IQR | 68.3690 |
| Bowley 왜도 | 0.1485 |
| Adj 이상치 수 | 512 |
| Adj 이상치율 | 4.44% |
| Std 이상치율 | 4.44% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 512건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

---


### 🟡 주의 (5~10%) - 3개 태그

#### INDIRECT_COOLING_WATER_FLOW 🟡

**위험도**: [CAUTION] | **이상치율**: 9.52% | **개선율**: 1.8%
**Bowley 왜도**: 0.0563 | **승수 (L/U)**: 0.945/1.058

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,508 | 1,536 |
| 이상치율 | 9.52% | 9.70% |
| 하한 경계 | 154.1947 | 154.1286 |
| 상한 경계 | 157.4173 | 157.3474 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 155.4738 |
| 표준편차 | 1.5168 |
| Q1 (25%) | 155.3357 |
| 중앙값 | 155.7154 |
| Q3 (75%) | 156.1404 |
| IQR | 0.8047 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 154.76 | 34.17% | 34.82% |
| 2025-08 | 11,520 | 155.74 | 0.28% | 0.28% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-09 | 1,150 |
| 2 | 2025-05-28 | 326 |
| 3 | 2025-08-08 | 32 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 1,150건 (2025-05-09)
- 평균 일별 이상치: 502.7건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted/INDIRECT_COOLING_WATER_FLOW_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted/INDIRECT_COOLING_WATER_FLOW_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted/INDIRECT_COOLING_WATER_FLOW_07_daily_outlier_count.png)

**종합 분석 차트**

![INDIRECT_COOLING_WATER_FLOW 종합 분석 차트](./04_Furnace_Auxiliary/adjusted/INDIRECT_COOLING_WATER_FLOW_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 154.7565 |
| 중앙값 | 155.6892 |
| IQR | 5.0114 |
| Bowley 왜도 | -0.6380 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_COOLING_WATER_FLOW_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 155.7427 |
| 중앙값 | 155.7191 |
| IQR | 0.6710 |
| Bowley 왜도 | 0.0132 |
| Adj 이상치 수 | 128 |
| Adj 이상치율 | 1.11% |
| Std 이상치율 | 1.25% |
| 개선율 | 11.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 128건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_COOLING_WATER_FLOW_00_summary.png)

---

#### HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 🟡

**위험도**: [CAUTION] | **이상치율**: 5.29% | **개선율**: -17.2%
**Bowley 왜도**: -0.1054 | **승수 (L/U)**: 1.111/0.900

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 838 | 715 |
| 이상치율 | 5.29% | 4.51% |
| 하한 경계 | 804.9243 | 814.3092 |
| 상한 경계 | 1031.1052 | 1039.5516 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 925.4965 |
| 표준편차 | 55.7246 |
| Q1 (25%) | 898.7751 |
| 중앙값 | 929.8968 |
| Q3 (75%) | 955.0857 |
| IQR | 56.3106 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 938.63 | 8.84% | 8.03% |
| 2025-08 | 11,520 | 920.57 | 3.96% | 3.19% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 456 |
| 2 | 2025-05-09 | 290 |
| 3 | 2025-05-28 | 92 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 456건 (2025-08-08)
- 평균 일별 이상치: 279.3건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 938.6263 |
| 중앙값 | 940.5779 |
| IQR | 41.5341 |
| Bowley 왜도 | 0.3133 |
| Adj 이상치 수 | 917 |
| Adj 이상치율 | 21.23% |
| Std 이상치율 | 23.04% |
| 개선율 | 7.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 562건
- 2. 2025-05-28: 355건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 920.5739 |
| 중앙값 | 922.1687 |
| IQR | 58.0755 |
| Bowley 왜도 | 0.0071 |
| Adj 이상치 수 | 328 |
| Adj 이상치율 | 2.85% |
| Std 이상치율 | 2.85% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 328건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

---

#### [L2] PR6L2_ACT_TORQUE 🟡

**위험도**: [CAUTION] | **이상치율**: 5.01% | **개선율**: 10.3%
**Bowley 왜도**: 0.4555 | **승수 (L/U)**: 0.634/1.577

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 486 | 542 |
| 이상치율 | 5.01% | 5.59% |
| 하한 경계 | 3.3242 | 2.9580 |
| 상한 경계 | 6.2045 | 5.6270 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 4.9982 |
| 표준편차 | 3.5674 |
| Q1 (25%) | 3.9589 |
| 중앙값 | 4.1405 |
| Q3 (75%) | 4.6261 |
| IQR | 0.6673 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 4.60 | 0.50% | 2.70% |
| 2025-08 | 6,913 | 5.16 | 6.83% | 6.76% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 472 |
| 2 | 2025-05-28 | 8 |
| 3 | 2025-05-09 | 6 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 472건 (2025-08-08)
- 평균 일별 이상치: 162.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted/PR6L2_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted/PR6L2_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted/PR6L2_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR6L2_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted/PR6L2_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 4.6036 |
| 중앙값 | 4.4020 |
| IQR | 0.5795 |
| Bowley 왜도 | 0.6381 |
| Adj 이상치 수 | 10 |
| Adj 이상치율 | 0.36% |
| Std 이상치율 | 1.80% |
| 개선율 | 80.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 6건
- 2. 2025-05-28: 4건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L2_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 5.1569 |
| 중앙값 | 3.9846 |
| IQR | 0.4652 |
| Bowley 왜도 | 0.8490 |
| Adj 이상치 수 | 488 |
| Adj 이상치율 | 7.06% |
| Std 이상치율 | 8.39% |
| 개선율 | 15.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 488건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L2_ACT_TORQUE_00_summary.png)

---


### 🟢 양호 (0~5%) - 68개 태그

#### MAIN_GAS_PRESSURE 🟢

**위험도**: [NORMAL] | **이상치율**: 3.63% | **개선율**: -35.0%
**Bowley 왜도**: -0.2309 | **승수 (L/U)**: 1.260/0.794

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 575 | 426 |
| 이상치율 | 3.63% | 2.69% |
| 하한 경계 | 1477.0582 | 1488.3175 |
| 상한 경계 | 1594.9915 | 1603.9295 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 1547.3521 |
| 표준편차 | 24.4255 |
| Q1 (25%) | 1531.6720 |
| 중앙값 | 1549.4600 |
| Q3 (75%) | 1560.5750 |
| IQR | 28.9030 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 1551.31 | 9.61% | 5.23% |
| 2025-08 | 11,520 | 1545.87 | 1.39% | 1.74% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-09 | 216 |
| 2 | 2025-05-28 | 199 |
| 3 | 2025-08-08 | 160 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 216건 (2025-05-09)
- 평균 일별 이상치: 191.7건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_PRESSURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_PRESSURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_PRESSURE_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_GAS_PRESSURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_PRESSURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 1551.3089 |
| 중앙값 | 1554.7290 |
| IQR | 49.4035 |
| Bowley 왜도 | -0.2429 |
| Adj 이상치 수 | 6 |
| Adj 이상치율 | 0.14% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-28: 6건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1545.8686 |
| 중앙값 | 1548.5310 |
| IQR | 24.4153 |
| Bowley 왜도 | -0.2698 |
| Adj 이상치 수 | 256 |
| Adj 이상치율 | 2.22% |
| Std 이상치율 | 2.64% |
| 개선율 | 15.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 256건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_PRESSURE_00_summary.png)

---

#### HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 3.30% | **개선율**: 10.2%
**Bowley 왜도**: -0.1784 | **승수 (L/U)**: 1.195/0.837

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 522 | 581 |
| 이상치율 | 3.30% | 3.67% |
| 하한 경계 | 814.1897 | 832.0828 |
| 상한 경계 | 1061.4296 | 1076.3991 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 950.2968 |
| 표준편차 | 59.1845 |
| Q1 (25%) | 923.7014 |
| 중앙값 | 959.6891 |
| Q3 (75%) | 984.7805 |
| IQR | 61.0791 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 961.72 | 7.27% | 5.67% |
| 2025-08 | 11,520 | 946.02 | 1.81% | 2.92% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-09 | 234 |
| 2 | 2025-08-08 | 208 |
| 3 | 2025-05-28 | 80 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 234건 (2025-05-09)
- 평균 일별 이상치: 174.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 961.7175 |
| 중앙값 | 967.9849 |
| IQR | 45.9727 |
| Bowley 왜도 | 0.2718 |
| Adj 이상치 수 | 826 |
| Adj 이상치율 | 19.12% |
| Std 이상치율 | 21.02% |
| 개선율 | 9.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 488건
- 2. 2025-05-28: 338건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 946.0151 |
| 중앙값 | 954.3656 |
| IQR | 65.3982 |
| Bowley 왜도 | -0.1584 |
| Adj 이상치 수 | 112 |
| Adj 이상치율 | 0.97% |
| Std 이상치율 | 2.01% |
| 개선율 | 51.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 112건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

---

#### PINCHROLL_2_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 1.30% | **개선율**: 75.3%
**Bowley 왜도**: -0.7432 | **승수 (L/U)**: 2.103/0.476

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 126 | 510 |
| 이상치율 | 1.30% | 5.26% |
| 하한 경계 | -347.2027 | -328.2841 |
| 상한 경계 | -291.5261 | -282.5283 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | -304.8210 |
| 표준편차 | 20.0435 |
| Q1 (25%) | -311.1257 |
| 중앙값 | -301.1556 |
| Q3 (75%) | -299.6867 |
| IQR | 11.4390 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | -306.76 | 0.04% | 3.67% |
| 2025-08 | 6,913 | -304.04 | 1.81% | 5.90% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 125 |
| 2 | 2025-05-28 | 1 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 125건 (2025-08-08)
- 평균 일별 이상치: 63.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_2_ACTUAL_SPEED 종합 분석 차트](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | -306.7582 |
| 중앙값 | -301.5735 |
| IQR | 7.1977 |
| Bowley 왜도 | -0.7941 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.04% |
| Std 이상치율 | 14.20% |
| 개선율 | 99.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-28: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | -304.0417 |
| 중앙값 | -300.6901 |
| IQR | 14.4436 |
| Bowley 왜도 | -0.6625 |
| Adj 이상치 수 | 125 |
| Adj 이상치율 | 1.81% |
| Std 이상치율 | 1.55% |
| 개선율 | -16.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 125건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

---

#### PINCHROLL_4_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 1.23% | **개선율**: 0.0%
**Bowley 왜도**: 0.8043 | **승수 (L/U)**: 0.447/2.235

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 119 | 119 |
| 이상치율 | 1.23% | 1.23% |
| 하한 경계 | 1167.2836 | 1132.5680 |
| 상한 경계 | 1377.6854 | 1300.0880 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 1202.4218 |
| 표준편차 | 101.8460 |
| Q1 (25%) | 1195.3880 |
| 중앙값 | 1199.4850 |
| Q3 (75%) | 1237.2680 |
| IQR | 41.8800 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 1227.50 | 0.18% | 0.18% |
| 2025-08 | 6,913 | 1192.33 | 1.65% | 1.65% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 114 |
| 2 | 2025-05-09 | 5 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 114건 (2025-08-08)
- 평균 일별 이상치: 59.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_4_ACTUAL_SPEED 종합 분석 차트](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 1227.4970 |
| 중앙값 | 1238.5840 |
| IQR | 37.5760 |
| Bowley 왜도 | -0.8860 |
| Adj 이상치 수 | 190 |
| Adj 이상치율 | 6.83% |
| Std 이상치율 | 0.18% |
| 개선율 | -3700.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 190건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 1192.3344 |
| 중앙값 | 1198.1110 |
| IQR | 12.9010 |
| Bowley 왜도 | 0.5210 |
| Adj 이상치 수 | 114 |
| Adj 이상치율 | 1.65% |
| Std 이상치율 | 14.52% |
| 개선율 | 88.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 114건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

---

#### COMBUSTION_AIR_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.56% | **개선율**: -175.0%
**Bowley 왜도**: -0.4169 | **승수 (L/U)**: 1.517/0.659

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 88 | 32 |
| 이상치율 | 0.56% | 0.20% |
| 하한 경계 | 19.8565 | 25.7814 |
| 상한 경계 | 52.4261 | 56.3313 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 41.3156 |
| 표준편차 | 4.9691 |
| Q1 (25%) | 37.2376 |
| 중앙값 | 42.6482 |
| Q3 (75%) | 44.8751 |
| IQR | 7.6375 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 34.65 | 0.00% | 0.00% |
| 2025-08 | 11,520 | 43.81 | 0.76% | 0.28% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 88 |

- 이상치 발생 일수: 1일
- 최대 일별 이상치: 88건 (2025-08-08)
- 평균 일별 이상치: 88.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted/COMBUSTION_AIR_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted/COMBUSTION_AIR_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted/COMBUSTION_AIR_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![COMBUSTION_AIR_TEMPERATURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted/COMBUSTION_AIR_TEMPERATURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 34.6522 |
| 중앙값 | 33.9560 |
| IQR | 2.4319 |
| Bowley 왜도 | 0.0841 |
| Adj 이상치 수 | 421 |
| Adj 이상치율 | 9.75% |
| Std 이상치율 | 10.51% |
| 개선율 | 7.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-28: 421건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/COMBUSTION_AIR_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 43.8138 |
| 중앙값 | 43.3118 |
| IQR | 3.0590 |
| Bowley 왜도 | 0.4533 |
| Adj 이상치 수 | 736 |
| Adj 이상치율 | 6.39% |
| Std 이상치율 | 6.67% |
| 개선율 | 4.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 736건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/COMBUSTION_AIR_TEMPERATURE_00_summary.png)

---

#### HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 0.51% | **개선율**: 93.5%
**Bowley 왜도**: -0.5353 | **승수 (L/U)**: 1.708/0.585

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 81 | 1,237 |
| 이상치율 | 0.51% | 7.81% |
| 하한 경계 | 826.3441 | 896.1385 |
| 상한 경계 | 1118.1694 | 1159.0337 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 1020.1203 |
| 표준편차 | 64.8229 |
| Q1 (25%) | 994.7242 |
| 중앙값 | 1045.1770 |
| Q3 (75%) | 1060.4480 |
| IQR | 65.7238 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 1038.51 | 1.88% | 13.08% |
| 2025-08 | 11,520 | 1013.22 | 0.00% | 5.83% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-09 | 76 |
| 2 | 2025-05-28 | 5 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 76건 (2025-05-09)
- 평균 일별 이상치: 40.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 1038.5144 |
| 중앙값 | 1075.1860 |
| IQR | 49.2780 |
| Bowley 왜도 | -0.7505 |
| Adj 이상치 수 | 231 |
| Adj 이상치율 | 5.35% |
| Std 이상치율 | 17.99% |
| 개선율 | 70.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 188건
- 2. 2025-05-28: 43건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1013.2241 |
| 중앙값 | 1042.4230 |
| IQR | 58.8597 |
| Bowley 왜도 | -0.7132 |
| Adj 이상치 수 | 112 |
| Adj 이상치율 | 0.97% |
| Std 이상치율 | 8.33% |
| 개선율 | 88.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 112건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

---

#### HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 0.50% | **개선율**: 93.4%
**Bowley 왜도**: -0.5423 | **승수 (L/U)**: 1.720/0.581

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 79 | 1,200 |
| 이상치율 | 0.50% | 7.58% |
| 하한 경계 | 829.1848 | 899.7417 |
| 상한 경계 | 1120.0841 | 1161.1086 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 1022.8864 |
| 표준편차 | 64.1158 |
| Q1 (25%) | 997.7543 |
| 중앙값 | 1048.1410 |
| Q3 (75%) | 1063.0960 |
| IQR | 65.3417 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 1041.25 | 1.83% | 12.41% |
| 2025-08 | 11,520 | 1016.00 | 0.00% | 5.76% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-09 | 74 |
| 2 | 2025-05-28 | 5 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 74건 (2025-05-09)
- 평균 일별 이상치: 39.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 1041.2510 |
| 중앙값 | 1076.9560 |
| IQR | 46.9380 |
| Bowley 왜도 | -0.7353 |
| Adj 이상치 수 | 331 |
| Adj 이상치율 | 7.66% |
| Std 이상치율 | 18.29% |
| 개선율 | 58.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 210건
- 2. 2025-05-28: 121건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1016.0013 |
| 중앙값 | 1045.3985 |
| IQR | 59.7818 |
| Bowley 왜도 | -0.7230 |
| Adj 이상치 수 | 120 |
| Adj 이상치율 | 1.04% |
| Std 이상치율 | 6.18% |
| 개선율 | 83.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 120건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

---

#### FURNACE_PRESSURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.26% | **개선율**: 0.0%
**Bowley 왜도**: 0.0239 | **승수 (L/U)**: 0.976/1.024

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 41 | 41 |
| 이상치율 | 0.26% | 0.26% |
| 하한 경계 | 0.3831 | 0.3817 |
| 상한 경계 | 0.5415 | 0.5401 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 0.4635 |
| 표준편차 | 0.0242 |
| Q1 (25%) | 0.4411 |
| 중앙값 | 0.4604 |
| Q3 (75%) | 0.4807 |
| IQR | 0.0396 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 0.47 | 0.39% | 0.39% |
| 2025-08 | 11,520 | 0.46 | 0.21% | 0.21% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 24 |
| 2 | 2025-05-09 | 14 |
| 3 | 2025-05-28 | 3 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 24건 (2025-08-08)
- 평균 일별 이상치: 13.7건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted/FURNACE_PRESSURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted/FURNACE_PRESSURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted/FURNACE_PRESSURE_07_daily_outlier_count.png)

**종합 분석 차트**

![FURNACE_PRESSURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted/FURNACE_PRESSURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 0.4693 |
| 중앙값 | 0.4689 |
| IQR | 0.0425 |
| Bowley 왜도 | -0.0606 |
| Adj 이상치 수 | 17 |
| Adj 이상치율 | 0.39% |
| Std 이상치율 | 0.37% |
| 개선율 | -6.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 14건
- 2. 2025-05-28: 3건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 0.4613 |
| 중앙값 | 0.4583 |
| IQR | 0.0375 |
| Bowley 왜도 | -0.0303 |
| Adj 이상치 수 | 64 |
| Adj 이상치율 | 0.56% |
| Std 이상치율 | 0.42% |
| 개선율 | -33.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 64건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_PRESSURE_00_summary.png)

---

#### MAIN_GAS_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.4994 | **승수 (L/U)**: 1.648/0.607

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 6.7357 | 12.6315 |
| 상한 경계 | 33.3251 | 36.9031 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 24.6866 |
| 표준편차 | 4.5285 |
| Q1 (25%) | 21.7333 |
| 중앙값 | 26.2825 |
| Q3 (75%) | 27.8013 |
| IQR | 6.0679 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 17.85 | 0.00% | 0.00% |
| 2025-08 | 11,520 | 27.25 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_GAS_TEMPERATURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_TEMPERATURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 17.8487 |
| 중앙값 | 17.2188 |
| IQR | 2.5549 |
| Bowley 왜도 | 0.3944 |
| Adj 이상치 수 | 31 |
| Adj 이상치율 | 0.72% |
| Std 이상치율 | 2.20% |
| 개선율 | 67.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-28: 31건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 27.2502 |
| 중앙값 | 27.0439 |
| IQR | 2.3173 |
| Bowley 왜도 | 0.2206 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_TEMPERATURE_00_summary.png)

---

#### MAIN_GAS_FLOW 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.0737 | **승수 (L/U)**: 1.076/0.929

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2178.9540 | -1997.2900 |
| 상한 경계 | 4170.6885 | 4339.4508 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 1237.2548 |
| 표준편차 | 875.8384 |
| Q1 (25%) | 378.9878 |
| 중앙값 | 1229.4320 |
| Q3 (75%) | 1963.1730 |
| IQR | 1584.1852 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 1528.62 | 0.00% | 0.00% |
| 2025-08 | 11,520 | 1128.02 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_FLOW_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_FLOW_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_FLOW_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_GAS_FLOW 종합 분석 차트](./04_Furnace_Auxiliary/adjusted/MAIN_GAS_FLOW_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 1528.6164 |
| 중앙값 | 1664.5100 |
| IQR | 1944.8146 |
| Bowley 왜도 | -0.1244 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/MAIN_GAS_FLOW_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 1128.0195 |
| 중앙값 | 1124.6620 |
| IQR | 1453.6719 |
| Bowley 왜도 | -0.1145 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/MAIN_GAS_FLOW_00_summary.png)

---

#### FURNACE_O2_ANALYZER 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.1316 | **승수 (L/U)**: 1.141/0.877

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -15.0000 | -13.0905 |
| 상한 경계 | 21.4464 | 23.1204 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 5.0986 |
| 표준편차 | 4.3509 |
| Q1 (25%) | 0.4886 |
| 중앙값 | 5.6105 |
| Q3 (75%) | 9.5413 |
| IQR | 9.0527 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 7.29 | 0.00% | 0.00% |
| 2025-08 | 11,520 | 4.28 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted/FURNACE_O2_ANALYZER_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted/FURNACE_O2_ANALYZER_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted/FURNACE_O2_ANALYZER_07_daily_outlier_count.png)

**종합 분석 차트**

![FURNACE_O2_ANALYZER 종합 분석 차트](./04_Furnace_Auxiliary/adjusted/FURNACE_O2_ANALYZER_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 7.2895 |
| 중앙값 | 9.5403 |
| IQR | 5.5749 |
| Bowley 왜도 | -0.9973 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/FURNACE_O2_ANALYZER_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 4.2772 |
| 중앙값 | 0.7696 |
| IQR | 9.1357 |
| Bowley 왜도 | 0.9191 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/FURNACE_O2_ANALYZER_00_summary.png)

---

#### INDIRECT_WATER_MAIN_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.3777 | **승수 (L/U)**: 0.685/1.459

**데이터**: 원본 15,839 → 필터 후 15,839 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 24.6740 | 22.5513 |
| 상한 경계 | 43.6445 | 40.5478 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,839 |
| 평균 | 31.3681 |
| 표준편차 | 2.1188 |
| Q1 (25%) | 29.3000 |
| 중앙값 | 30.7000 |
| Q3 (75%) | 33.7991 |
| IQR | 4.4991 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,319 | 29.51 | 0.00% | 0.00% |
| 2025-08 | 11,520 | 32.06 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![INDIRECT_WATER_MAIN_TEMPERATURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,319 |
| 평균 | 29.5140 |
| 중앙값 | 29.4000 |
| IQR | 0.7000 |
| Bowley 왜도 | 0.4286 |
| Adj 이상치 수 | 343 |
| Adj 이상치율 | 7.94% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-28: 211건
- 2. 2025-05-09: 132건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,520 |
| 평균 | 32.0633 |
| 중앙값 | 32.7987 |
| IQR | 4.3992 |
| Bowley 왜도 | -0.4084 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

---

#### STAND_5_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9532 | **승수 (L/U)**: 0.386/2.594

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -29.7252 | -77.1062 |
| 상한 경계 | 251.4153 | 128.5104 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 23.8581 |
| 표준편차 | 25.1230 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.2031 |
| Q3 (75%) | 51.4041 |
| IQR | 51.4041 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 25.03 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 23.42 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_5_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_5_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_5_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_5_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_5_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 25.0317 |
| 중앙값 | 40.5585 |
| IQR | 46.5345 |
| Bowley 왜도 | -0.7432 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_5_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 23.4239 |
| 중앙값 | 0.9183 |
| IQR | 52.9260 |
| Bowley 왜도 | 0.9653 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_5_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_6_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9132 | **승수 (L/U)**: 0.401/2.492

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -28.1102 | -70.0618 |
| 상한 경계 | 221.3297 | 116.7696 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 22.0489 |
| 표준편차 | 22.9238 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 2.0261 |
| Q3 (75%) | 46.7079 |
| IQR | 46.7079 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 24.61 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 21.10 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_6_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_6_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_6_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_6_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_6_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 24.6096 |
| 중앙값 | 38.9778 |
| IQR | 45.6196 |
| Bowley 왜도 | -0.7088 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_6_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 21.1014 |
| 중앙값 | 1.6220 |
| IQR | 47.3863 |
| Bowley 왜도 | 0.9315 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_6_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_7_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9068 | **승수 (L/U)**: 0.404/2.476

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -29.0424 | -71.9203 |
| 상한 경계 | 226.0494 | 119.8671 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 21.9619 |
| 표준편차 | 22.9090 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 2.2343 |
| Q3 (75%) | 47.9468 |
| IQR | 47.9468 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 21.81 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 22.02 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_7_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_7_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_7_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_7_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_7_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 21.8129 |
| 중앙값 | 36.0918 |
| IQR | 40.2244 |
| Bowley 왜도 | -0.7945 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_7_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 22.0170 |
| 중앙값 | 1.9699 |
| IQR | 49.3542 |
| Bowley 왜도 | 0.9202 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_7_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_8_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.8579 | **승수 (L/U)**: 0.424/2.358

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -26.3750 | -62.1961 |
| 상한 경계 | 188.1316 | 103.6601 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 19.7592 |
| 표준편차 | 20.2782 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 2.9465 |
| Q3 (75%) | 41.4641 |
| IQR | 41.4641 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 21.89 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 18.97 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_8_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_8_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_8_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_8_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_8_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 21.8867 |
| 중앙값 | 34.3505 |
| IQR | 39.2998 |
| Bowley 왜도 | -0.7481 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_8_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 18.9721 |
| 중앙값 | 2.3219 |
| IQR | 42.1886 |
| Bowley 왜도 | 0.8899 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_8_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_1_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9637 | **승수 (L/U)**: 0.381/2.621

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -33.4253 | -87.6193 |
| 상한 경계 | 288.0932 | 146.0322 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 27.2842 |
| 표준편차 | 28.8381 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0606 |
| Q3 (75%) | 58.4129 |
| IQR | 58.4129 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 27.92 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 27.05 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_1_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_1_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_1_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_1_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_1_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 27.9212 |
| 중앙값 | 44.1189 |
| IQR | 51.7535 |
| Bowley 왜도 | -0.7050 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_1_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 27.0486 |
| 중앙값 | 0.8940 |
| IQR | 60.9007 |
| Bowley 왜도 | 0.9706 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_1_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_2_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9536 | **승수 (L/U)**: 0.385/2.595

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -36.8877 | -95.7251 |
| 상한 경계 | 312.2273 | 159.5418 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 30.0027 |
| 표준편차 | 31.5966 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.4805 |
| Q3 (75%) | 63.8167 |
| IQR | 63.8167 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 31.82 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 29.33 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_2_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_2_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_2_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_2_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_2_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 31.8238 |
| 중앙값 | 49.3627 |
| IQR | 59.3037 |
| Bowley 왜도 | -0.6647 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_2_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 29.3289 |
| 중앙값 | 1.2221 |
| IQR | 66.2931 |
| Bowley 왜도 | 0.9631 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_2_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_3_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9597 | **승수 (L/U)**: 0.383/2.611

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -33.3421 | -87.0521 |
| 상한 경계 | 285.3173 | 145.0869 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 27.0672 |
| 표준편차 | 28.6625 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.1698 |
| Q3 (75%) | 58.0348 |
| IQR | 58.0348 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 27.32 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 26.97 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_3_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_3_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_3_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_3_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_3_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 27.3196 |
| 중앙값 | 44.0306 |
| IQR | 50.6815 |
| Bowley 왜도 | -0.7375 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_3_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 26.9739 |
| 중앙값 | 0.9636 |
| IQR | 60.7425 |
| Bowley 왜도 | 0.9683 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_3_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_4_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9409 | **승수 (L/U)**: 0.390/2.562

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -32.4393 | -83.1189 |
| 상한 경계 | 268.3875 | 138.5315 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 25.7459 |
| 표준편차 | 27.1244 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.6374 |
| Q3 (75%) | 55.4126 |
| IQR | 55.4126 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 25.88 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 25.70 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_4_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_4_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_4_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_4_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_4_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 25.8753 |
| 중앙값 | 40.4861 |
| IQR | 48.0027 |
| Bowley 왜도 | -0.6868 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_4_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 25.6980 |
| 중앙값 | 1.3323 |
| IQR | 57.6919 |
| Bowley 왜도 | 0.9538 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_4_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_13_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9010 | **승수 (L/U)**: 0.406/2.462

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -36.6968 | -90.3483 |
| 상한 경계 | 282.6716 | 150.5805 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 28.3087 |
| 표준편차 | 29.4389 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 2.9820 |
| Q3 (75%) | 60.2322 |
| IQR | 60.2322 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 29.90 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 27.72 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_13_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_13_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_13_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_13_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_13_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 29.8996 |
| 중앙값 | 49.4737 |
| IQR | 55.5710 |
| Bowley 왜도 | -0.7806 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_13_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 27.7200 |
| 중앙값 | 2.5762 |
| IQR | 62.0029 |
| Bowley 왜도 | 0.9169 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_13_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_14_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.7939 | **승수 (L/U)**: 0.452/2.212

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -27.0602 | -59.8581 |
| 상한 경계 | 172.3138 | 99.7635 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 18.9351 |
| 표준편차 | 19.1026 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.1120 |
| Q3 (75%) | 39.9054 |
| IQR | 39.9054 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 20.74 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 18.27 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_14_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_14_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_14_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_14_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_14_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 20.7389 |
| 중앙값 | 34.5658 |
| IQR | 37.9585 |
| Bowley 왜도 | -0.8212 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_14_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 18.2678 |
| 중앙값 | 3.5292 |
| IQR | 40.6458 |
| Bowley 왜도 | 0.8263 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_14_ACTUAL_TORQUE_00_summary.png)

---

#### FINISHING_BLOCK_MASTER_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.7952 | **승수 (L/U)**: 0.451/2.215

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -30.1072 | -66.6831 |
| 상한 경계 | 192.1490 | 111.1386 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 21.3176 |
| 표준편차 | 21.3095 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.5525 |
| Q3 (75%) | 44.4554 |
| IQR | 44.4554 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 23.63 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 20.46 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_MASTER_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 23.6294 |
| 중앙값 | 39.4219 |
| IQR | 42.9204 |
| Bowley 왜도 | -0.8370 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 20.4623 |
| 중앙값 | 4.2629 |
| IQR | 45.0202 |
| Bowley 왜도 | 0.8106 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

---

#### FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.7956 | **승수 (L/U)**: 0.451/2.216

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -30.0863 | -66.6646 |
| 상한 경계 | 192.1568 | 111.1076 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 21.3077 |
| 표준편차 | 21.3026 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.5420 |
| Q3 (75%) | 44.4430 |
| IQR | 44.4430 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 23.62 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 20.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 23.6179 |
| 중앙값 | 39.4064 |
| IQR | 42.8989 |
| Bowley 왜도 | -0.8372 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 20.4530 |
| 중앙값 | 4.2508 |
| IQR | 44.9901 |
| Bowley 왜도 | 0.8110 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_1_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9713 | **승수 (L/U)**: 2.641/0.379

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2252.2290 | -852.6745 |
| 상한 경계 | 891.2650 | 1421.1242 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 361.6792 |
| 표준편차 | 278.6459 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 560.2918 |
| Q3 (75%) | 568.4497 |
| IQR | 568.4497 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 411.51 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 343.24 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_1_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_1_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_1_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_1_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_1_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 411.5139 |
| 중앙값 | 548.7492 |
| IQR | 630.5162 |
| Bowley 왜도 | -0.7406 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_1_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 343.2413 |
| 중앙값 | 560.6625 |
| IQR | 566.4557 |
| Bowley 왜도 | -0.9795 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_1_ACTUAL_SPEED_00_summary.png)

---

#### STAND_2_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9651 | **승수 (L/U)**: 2.625/0.381

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2379.9576 | -906.6336 |
| 상한 경계 | 949.8002 | 1511.0560 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 377.6934 |
| 표준편차 | 290.0548 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 593.8751 |
| Q3 (75%) | 604.4224 |
| IQR | 604.4224 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 420.37 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 361.91 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_2_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_2_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_2_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_2_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_2_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 420.3656 |
| 중앙값 | 614.2755 |
| IQR | 617.9741 |
| Bowley 왜도 | -0.9880 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_2_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 361.9055 |
| 중앙값 | 592.1953 |
| IQR | 599.4252 |
| Bowley 왜도 | -0.9759 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_2_ACTUAL_SPEED_00_summary.png)

---

#### STAND_3_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9581 | **승수 (L/U)**: 2.607/0.384

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -3160.1411 | -1212.3047 |
| 상한 경계 | 1273.2718 | 2020.5077 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 507.1390 |
| 표준편차 | 389.6964 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 791.2686 |
| Q3 (75%) | 808.2031 |
| IQR | 808.2031 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 573.12 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 482.73 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_3_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_3_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_3_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_3_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_3_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 573.1233 |
| 중앙값 | 830.3777 |
| IQR | 847.6536 |
| Bowley 왜도 | -0.9592 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_3_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 482.7261 |
| 중앙값 | 789.2386 |
| IQR | 799.0510 |
| Bowley 왜도 | -0.9754 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_3_ACTUAL_SPEED_00_summary.png)

---

#### STAND_4_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9686 | **승수 (L/U)**: 2.634/0.380

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -3271.1032 | -1241.7395 |
| 상한 경계 | 1299.2016 | 2069.5659 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 515.5693 |
| 표준편차 | 396.0179 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 814.8353 |
| Q3 (75%) | 827.8264 |
| IQR | 827.8264 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 566.61 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 496.68 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_4_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_4_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_4_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_4_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_4_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 566.6150 |
| 중앙값 | 826.3628 |
| IQR | 835.0794 |
| Bowley 왜도 | -0.9791 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_4_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 496.6834 |
| 중앙값 | 811.1440 |
| IQR | 823.6000 |
| Bowley 왜도 | -0.9698 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_4_ACTUAL_SPEED_00_summary.png)

---

#### STAND_5_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9573 | **승수 (L/U)**: 2.605/0.384

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4567.4855 | -1753.5360 |
| 상한 경계 | 1842.2365 | 2922.5600 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 731.7416 |
| 표준편차 | 562.1856 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1144.0820 |
| Q3 (75%) | 1169.0240 |
| IQR | 1169.0240 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 826.39 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 696.72 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_5_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_5_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_5_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_5_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_5_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 826.3895 |
| 중앙값 | 1206.0230 |
| IQR | 1214.5505 |
| Bowley 왜도 | -0.9860 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_5_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 696.7236 |
| 중앙값 | 1135.0590 |
| IQR | 1155.7050 |
| Bowley 왜도 | -0.9643 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_5_ACTUAL_SPEED_00_summary.png)

---

#### STAND_6_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9765 | **승수 (L/U)**: 2.655/0.377

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4617.4030 | -1739.0460 |
| 상한 경계 | 1814.3385 | 2898.4100 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 723.4043 |
| 표준편차 | 555.4995 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1145.7390 |
| Q3 (75%) | 1159.3640 |
| IQR | 1159.3640 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 790.06 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 698.74 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_6_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_6_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_6_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_6_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_6_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 790.0628 |
| 중앙값 | 1152.9200 |
| IQR | 1161.7112 |
| Bowley 왜도 | -0.9849 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_6_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 698.7419 |
| 중앙값 | 1139.9190 |
| IQR | 1157.6660 |
| Bowley 왜도 | -0.9693 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_6_ACTUAL_SPEED_00_summary.png)

---

#### STAND_7_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9554 | **승수 (L/U)**: 2.600/0.385

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4764.8335 | -1832.9040 |
| 상한 경계 | 1927.0051 | 3054.8400 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 769.7423 |
| 표준편차 | 592.1343 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1194.6630 |
| Q3 (75%) | 1221.9360 |
| IQR | 1221.9360 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 878.49 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 729.51 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_7_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_7_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_7_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_7_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_7_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 878.4873 |
| 중앙값 | 1281.1365 |
| IQR | 1293.6088 |
| Bowley 왜도 | -0.9807 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_7_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 729.5086 |
| 중앙값 | 1190.2380 |
| IQR | 1206.5220 |
| Bowley 왜도 | -0.9730 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_7_ACTUAL_SPEED_00_summary.png)

---

#### STAND_8_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7658 | **승수 (L/U)**: 2.151/0.465

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -3844.4181 | -1787.4450 |
| 상한 경계 | 2022.6946 | 2979.0750 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 720.2619 |
| 표준편차 | 555.5388 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1052.1110 |
| Q3 (75%) | 1191.6300 |
| IQR | 1191.6300 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 714.96 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 722.22 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_8_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_8_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_8_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_8_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_8_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 714.9641 |
| 중앙값 | 1042.4055 |
| IQR | 1051.8920 |
| Bowley 왜도 | -0.9820 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_8_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 722.2220 |
| 중앙값 | 1177.7970 |
| IQR | 1197.9710 |
| Bowley 왜도 | -0.9663 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_8_ACTUAL_SPEED_00_summary.png)

---

#### STAND_9_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9529 | **승수 (L/U)**: 0.386/2.593

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -30.5764 | -79.2901 |
| 상한 경계 | 258.4733 | 132.1501 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 24.9275 |
| 표준편차 | 26.2647 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.2453 |
| Q3 (75%) | 52.8601 |
| IQR | 52.8601 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 30.73 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 22.78 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_9_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_9_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_9_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_9_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_9_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 30.7336 |
| 중앙값 | 50.2548 |
| IQR | 57.4544 |
| Bowley 왜도 | -0.7494 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_9_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 22.7794 |
| 중앙값 | 0.8803 |
| IQR | 51.8027 |
| Bowley 왜도 | 0.9660 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_9_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_10_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9093 | **승수 (L/U)**: 0.403/2.483

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -37.1163 | -92.1412 |
| 상한 경계 | 290.1682 | 153.5687 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 28.7727 |
| 표준편차 | 29.8436 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 2.7867 |
| Q3 (75%) | 61.4275 |
| IQR | 61.4275 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 33.19 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 27.14 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_10_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_10_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_10_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_10_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_10_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 33.1883 |
| 중앙값 | 54.5395 |
| IQR | 61.6171 |
| Bowley 왜도 | -0.7703 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_10_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 27.1390 |
| 중앙값 | 2.3943 |
| IQR | 61.3548 |
| Bowley 왜도 | 0.9220 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_10_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_11_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9249 | **승수 (L/U)**: 0.397/2.522

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -27.1143 | -68.3751 |
| 상한 경계 | 218.0070 | 113.9584 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 21.4891 |
| 표준편차 | 22.4793 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.7106 |
| Q3 (75%) | 45.5834 |
| IQR | 45.5834 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 24.08 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 20.53 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_11_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_11_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_11_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_11_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_11_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 24.0834 |
| 중앙값 | 39.7396 |
| IQR | 44.8317 |
| Bowley 왜도 | -0.7728 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_11_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 20.5293 |
| 중앙값 | 1.3132 |
| IQR | 46.2053 |
| Bowley 왜도 | 0.9432 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_11_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_12_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.8702 | **승수 (L/U)**: 0.419/2.387

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -35.3129 | -84.3016 |
| 상한 경계 | 257.4521 | 140.5026 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 26.2223 |
| 표준편차 | 27.0014 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 3.6488 |
| Q3 (75%) | 56.2011 |
| IQR | 56.2011 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 28.38 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 25.42 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted/STAND_12_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted/STAND_12_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted/STAND_12_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_12_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted/STAND_12_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 28.3834 |
| 중앙값 | 47.2593 |
| IQR | 52.3227 |
| Bowley 왜도 | -0.8065 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted/STAND_12_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 25.4228 |
| 중앙값 | 3.0545 |
| IQR | 57.3860 |
| Bowley 왜도 | 0.8935 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted/STAND_12_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_12_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9699 | **승수 (L/U)**: 2.638/0.379

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4089.7549 | -1550.4570 |
| 상한 경계 | 1621.4280 | 2584.0950 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 642.7078 |
| 표준편차 | 498.4197 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1018.1000 |
| Q3 (75%) | 1033.6380 |
| IQR | 1033.6380 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 695.86 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 623.04 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_12_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_12_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_12_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_12_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_12_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 695.8601 |
| 중앙값 | 1019.6620 |
| IQR | 1032.5225 |
| Bowley 왜도 | -0.9751 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_12_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 623.0425 |
| 중앙값 | 1016.3510 |
| IQR | 1034.4810 |
| Bowley 왜도 | -0.9649 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_12_ACTUAL_SPEED_00_summary.png)

---

#### STAND_11_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9684 | **승수 (L/U)**: 2.634/0.380

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4149.5006 | -1575.5895 |
| 상한 경계 | 1648.6535 | 2625.9825 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 650.9443 |
| 표준편차 | 510.0879 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1033.7750 |
| Q3 (75%) | 1050.3930 |
| IQR | 1050.3930 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 704.55 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 631.11 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_11_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_11_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_11_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_11_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_11_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 704.5523 |
| 중앙값 | 1030.5510 |
| IQR | 1038.1665 |
| Bowley 왜도 | -0.9853 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_11_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 631.1104 |
| 중앙값 | 1041.3850 |
| IQR | 1053.5070 |
| Bowley 왜도 | -0.9770 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_11_ACTUAL_SPEED_00_summary.png)

---

#### STAND_10_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9801 | **승수 (L/U)**: 2.665/0.375

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4091.9677 | -1535.6318 |
| 상한 경계 | 1600.0457 | 2559.3863 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 638.7376 |
| 표준편차 | 492.6928 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1013.5600 |
| Q3 (75%) | 1023.7545 |
| IQR | 1023.7545 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 691.61 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 619.17 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_10_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_10_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_10_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_10_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_10_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 691.6131 |
| 중앙값 | 1010.7180 |
| IQR | 1019.8490 |
| Bowley 왜도 | -0.9821 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_10_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 619.1746 |
| 중앙값 | 1017.9650 |
| IQR | 1024.2880 |
| Bowley 왜도 | -0.9877 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_10_ACTUAL_SPEED_00_summary.png)

---

#### STAND_9_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8676 | **승수 (L/U)**: 2.381/0.420

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -3900.1399 | -1637.9070 |
| 상한 경계 | 1779.7952 | 2729.8450 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 668.4776 |
| 표준편차 | 516.1195 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1019.6480 |
| Q3 (75%) | 1091.9380 |
| IQR | 1091.9380 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 690.70 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 660.26 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_9_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_9_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_9_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_9_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_9_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 690.7008 |
| 중앙값 | 1011.0240 |
| IQR | 1019.5880 |
| Bowley 왜도 | -0.9832 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_9_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 660.2554 |
| 중앙값 | 1082.1940 |
| IQR | 1096.6890 |
| Bowley 왜도 | -0.9736 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_9_ACTUAL_SPEED_00_summary.png)

---

#### STAND_13_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9669 | **승수 (L/U)**: 2.630/0.380

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -3718.3501 | -1413.9333 |
| 상한 경계 | 1480.2820 | 2356.5555 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 601.7126 |
| 표준편차 | 466.0937 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 927.0240 |
| Q3 (75%) | 942.6222 |
| IQR | 942.6222 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 707.99 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 562.39 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_13_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_13_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_13_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_13_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_13_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 707.9935 |
| 중앙값 | 1034.5830 |
| IQR | 1046.8735 |
| Bowley 왜도 | -0.9765 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_13_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 562.3906 |
| 중앙값 | 926.4054 |
| IQR | 930.4845 |
| Bowley 왜도 | -0.9912 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_13_ACTUAL_SPEED_00_summary.png)

---

#### STAND_14_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9720 | **승수 (L/U)**: 2.643/0.378

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4392.7780 | -1661.9820 |
| 상한 경계 | 1736.7892 | 2769.9700 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 687.0673 |
| 표준편차 | 536.6166 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1092.4490 |
| Q3 (75%) | 1107.9880 |
| IQR | 1107.9880 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 760.49 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 659.90 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/STAND_14_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/STAND_14_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/STAND_14_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_14_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/STAND_14_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 760.4923 |
| 중앙값 | 1115.4440 |
| IQR | 1122.3150 |
| Bowley 왜도 | -0.9878 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/STAND_14_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 659.9015 |
| 중앙값 | 1091.1350 |
| IQR | 1100.5620 |
| Bowley 왜도 | -0.9829 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/STAND_14_ACTUAL_SPEED_00_summary.png)

---

#### FINISHING_BLOCK_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9767 | **승수 (L/U)**: 2.656/0.377

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -3720.6060 | -1401.0239 |
| 상한 경계 | 1461.5826 | 2335.0398 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 588.5781 |
| 표준편차 | 444.0364 |
| Q1 (25%) | -0.0000 |
| 중앙값 | 923.1268 |
| Q3 (75%) | 934.0159 |
| IQR | 934.0159 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 629.55 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 573.42 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 629.5472 |
| 중앙값 | 903.4909 |
| IQR | 923.1234 |
| Bowley 왜도 | -0.9575 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 573.4203 |
| 중앙값 | 933.8806 |
| IQR | 934.1429 |
| Bowley 왜도 | -0.9994 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

---

#### STAND_1_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.4980 | **승수 (L/U)**: 0.608/1.645

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.9116 | -1.5000 |
| 상한 경계 | 3.4681 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4791 |
| 표준편차 | 0.4856 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2510 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_1_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_1_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_1_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_1_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_1_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5605 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_1_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4490 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_1_LOAD_00_summary.png)

---

#### STAND_6_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5290 | **승수 (L/U)**: 0.589/1.697

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8838 | -1.5000 |
| 상한 경계 | 3.5459 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4782 |
| 표준편차 | 0.4856 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2355 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_6_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_6_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_6_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_6_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_6_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5597 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_6_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4481 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_6_LOAD_00_summary.png)

---

#### STAND_7_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5070 | **승수 (L/U)**: 0.602/1.660

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.9034 | -1.5000 |
| 상한 경계 | 3.4905 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4782 |
| 표준편차 | 0.4855 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2465 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_7_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_7_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_7_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_7_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_7_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5596 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_7_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4480 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_7_LOAD_00_summary.png)

---

#### STAND_8_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5237 | **승수 (L/U)**: 0.592/1.688

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8885 | -1.5000 |
| 상한 경계 | 3.5323 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4782 |
| 표준편차 | 0.4856 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2382 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_8_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_8_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_8_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_8_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_8_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5596 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_8_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4480 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_8_LOAD_00_summary.png)

---

#### STAND_9_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5537 | **승수 (L/U)**: 0.575/1.740

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8623 | -1.5000 |
| 상한 경계 | 3.6094 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4770 |
| 표준편차 | 0.4857 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2232 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_9_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_9_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_9_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_9_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_9_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5580 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_9_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4471 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_9_LOAD_00_summary.png)

---

#### STAND_2_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5520 | **승수 (L/U)**: 0.576/1.737

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8637 | -1.5000 |
| 상한 경계 | 3.6051 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4788 |
| 표준편차 | 0.4861 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2240 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_2_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_2_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_2_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_2_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_2_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5603 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_2_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4487 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_2_LOAD_00_summary.png)

---

#### STAND_3_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5553 | **승수 (L/U)**: 0.574/1.743

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8608 | -1.5000 |
| 상한 경계 | 3.6138 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4786 |
| 표준편차 | 0.4864 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2223 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_3_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_3_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_3_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_3_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_3_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5600 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_3_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4485 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_3_LOAD_00_summary.png)

---

#### STAND_4_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5237 | **승수 (L/U)**: 0.592/1.688

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8885 | -1.5000 |
| 상한 경계 | 3.5323 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4784 |
| 표준편차 | 0.4859 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2382 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_4_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_4_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_4_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_4_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_4_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5598 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_4_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4483 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_4_LOAD_00_summary.png)

---

#### STAND_5_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5047 | **승수 (L/U)**: 0.604/1.656

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.9056 | -1.5000 |
| 상한 경계 | 3.4846 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4783 |
| 표준편차 | 0.4857 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2477 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_5_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_5_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_5_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_5_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_5_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5597 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_5_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4481 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_5_LOAD_00_summary.png)

---

#### STAND_13_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5403 | **승수 (L/U)**: 0.583/1.717

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8738 | -1.5000 |
| 상한 경계 | 3.5749 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4769 |
| 표준편차 | 0.4857 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2298 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_13_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_13_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_13_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_13_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_13_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5579 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_13_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4470 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_13_LOAD_00_summary.png)

---

#### STAND_12_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5403 | **승수 (L/U)**: 0.583/1.717

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8738 | -1.5000 |
| 상한 경계 | 3.5749 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4769 |
| 표준편차 | 0.4857 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2298 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_12_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_12_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_12_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_12_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_12_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5579 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_12_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4470 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_12_LOAD_00_summary.png)

---

#### STAND_11_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5437 | **승수 (L/U)**: 0.581/1.722

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8709 | -1.5000 |
| 상한 경계 | 3.5835 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4769 |
| 표준편차 | 0.4857 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2282 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_11_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_11_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_11_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_11_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_11_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5579 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_11_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4470 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_11_LOAD_00_summary.png)

---

#### STAND_10_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5410 | **승수 (L/U)**: 0.582/1.718

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8732 | -1.5000 |
| 상한 경계 | 3.5766 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4770 |
| 표준편차 | 0.4857 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2295 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_10_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_10_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_10_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_10_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_10_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5580 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_10_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4471 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_10_LOAD_00_summary.png)

---

#### STAND_14_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5513 | **승수 (L/U)**: 0.576/1.736

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8643 | -1.5000 |
| 상한 경계 | 3.6033 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4768 |
| 표준편차 | 0.4858 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2243 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/STAND_14_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/STAND_14_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/STAND_14_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_14_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/STAND_14_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5578 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/STAND_14_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4469 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/STAND_14_LOAD_00_summary.png)

---

#### PINCHROLL_2_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.9999 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -42.3854 | -10.7211 |
| 상한 경계 | 26.7753 | 38.4246 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 15.2499 |
| 표준편차 | 7.4356 |
| Q1 (25%) | 7.7086 |
| 중앙값 | 19.9946 |
| Q3 (75%) | 19.9950 |
| IQR | 12.2864 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 16.49 | 0.00% | 0.00% |
| 2025-08 | 6,913 | 14.75 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_2_ACTUAL_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted/PINCHROLL_2_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 16.4890 |
| 중앙값 | 19.9947 |
| IQR | 2.0441 |
| Bowley 왜도 | -0.9997 |
| Adj 이상치 수 | 542 |
| Adj 이상치율 | 19.49% |
| Std 이상치율 | 23.30% |
| 개선율 | 16.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 349건
- 2. 2025-05-28: 193건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 14.7514 |
| 중앙값 | 19.9946 |
| IQR | 16.6884 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

---

#### PINCHROLL_3_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6317 | **승수 (L/U)**: 1.881/0.532

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -55.7990 | -22.6798 |
| 상한 경계 | 59.9878 | 77.5975 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 28.7933 |
| 표준편차 | 14.9030 |
| Q1 (25%) | 14.9242 |
| 중앙값 | 35.3765 |
| Q3 (75%) | 39.9935 |
| IQR | 25.0693 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 28.75 | 0.00% | 0.00% |
| 2025-08 | 6,913 | 28.81 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_3_ACTUAL_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted/PINCHROLL_3_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 28.7512 |
| 중앙값 | 34.9799 |
| IQR | 2.1951 |
| Bowley 왜도 | -0.9130 |
| Adj 이상치 수 | 622 |
| Adj 이상치율 | 22.37% |
| Std 이상치율 | 24.24% |
| 개선율 | 7.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 413건
- 2. 2025-05-28: 209건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 28.8102 |
| 중앙값 | 39.9825 |
| IQR | 35.2037 |
| Bowley 왜도 | -0.9993 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

---

#### FINISHING_BLOCK_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.5493 | **승수 (L/U)**: 0.577/1.732

**데이터**: 원본 15,839 → 필터 후 15,663 (1.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -0.8660 | -1.5000 |
| 상한 경계 | 3.5981 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 15,663 |
| 평균 | 0.4767 |
| 표준편차 | 0.4859 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 0.2253 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 4,230 | 0.56 | 0.00% | 0.00% |
| 2025-08 | 11,433 | 0.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted/FINISHING_BLOCK_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted/FINISHING_BLOCK_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted/FINISHING_BLOCK_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_LOAD 종합 분석 차트](./07_Stand_Load/adjusted/FINISHING_BLOCK_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,230 |
| 평균 | 0.5575 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted/FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted/FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted/FINISHING_BLOCK_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 11,433 |
| 평균 | 0.4468 |
| 중앙값 | 0.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted/FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted/FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted/FINISHING_BLOCK_LOAD_00_summary.png)

---

#### PINCHROLL_4_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6219 | **승수 (L/U)**: 1.862/0.537

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -52.5563 | -20.9974 |
| 상한 경계 | 59.6391 | 76.5842 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 29.1326 |
| 표준편차 | 14.3405 |
| Q1 (25%) | 15.5957 |
| 중앙값 | 35.3789 |
| Q3 (75%) | 39.9911 |
| IQR | 24.3954 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 28.96 | 0.00% | 0.00% |
| 2025-08 | 6,913 | 29.20 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_4_ACTUAL_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted/PINCHROLL_4_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 28.9631 |
| 중앙값 | 34.9866 |
| IQR | 2.2026 |
| Bowley 왜도 | -0.9131 |
| Adj 이상치 수 | 623 |
| Adj 이상치율 | 22.40% |
| Std 이상치율 | 24.24% |
| 개선율 | 7.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 413건
- 2. 2025-05-28: 210건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 29.2008 |
| 중앙값 | 39.9686 |
| IQR | 33.5236 |
| Bowley 왜도 | -0.9985 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

---

#### PINCHROLL_3_REFERENCE_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.6737 | **승수 (L/U)**: 0.510/1.961

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 14.5753 | -5.5696 |
| 상한 경계 | 143.5389 | 104.0271 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 52.7332 |
| 표준편차 | 24.7226 |
| Q1 (25%) | 35.5292 |
| 중앙값 | 40.0000 |
| Q3 (75%) | 62.9283 |
| IQR | 27.3992 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 46.07 | 0.00% | 0.00% |
| 2025-08 | 6,913 | 55.42 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted/PINCHROLL_3_REFERENCE_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted/PINCHROLL_3_REFERENCE_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted/PINCHROLL_3_REFERENCE_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_3_REFERENCE_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted/PINCHROLL_3_REFERENCE_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 46.0656 |
| 중앙값 | 35.0425 |
| IQR | 0.5550 |
| Bowley 왜도 | 0.8468 |
| Adj 이상치 수 | 631 |
| Adj 이상치율 | 22.69% |
| Std 이상치율 | 23.09% |
| 개선율 | 1.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 437건
- 2. 2025-05-28: 194건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 55.4154 |
| 중앙값 | 40.0000 |
| IQR | 40.0000 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

---

#### PINCHROLL_4_REFERENCE_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.6747 | **승수 (L/U)**: 0.509/1.964

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 14.5280 | -5.7071 |
| 상한 경계 | 143.9883 | 104.2562 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 52.8166 |
| 표준편차 | 24.8022 |
| Q1 (25%) | 35.5292 |
| 중앙값 | 40.0000 |
| Q3 (75%) | 63.0200 |
| IQR | 27.4908 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 46.13 | 0.00% | 0.00% |
| 2025-08 | 6,913 | 55.51 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted/PINCHROLL_4_REFERENCE_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted/PINCHROLL_4_REFERENCE_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted/PINCHROLL_4_REFERENCE_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_4_REFERENCE_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted/PINCHROLL_4_REFERENCE_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 46.1319 |
| 중앙값 | 35.0400 |
| IQR | 0.5550 |
| Bowley 왜도 | 0.8559 |
| Adj 이상치 수 | 639 |
| Adj 이상치율 | 22.98% |
| Std 이상치율 | 23.16% |
| 개선율 | 0.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 443건
- 2. 2025-05-28: 196건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted/PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 55.5057 |
| 중앙값 | 40.0000 |
| IQR | 40.0100 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted/PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

---

#### [L1] PR6L1_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 100.0%
**Bowley 왜도**: 0.8474 | **승수 (L/U)**: 0.429/2.334

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 1,682 |
| 이상치율 | 0.00% | 17.35% |
| 하한 경계 | -1.3189 | -7.2936 |
| 상한 경계 | 34.5287 | 20.5862 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 8.2121 |
| 표준편차 | 8.1747 |
| Q1 (25%) | 3.1613 |
| 중앙값 | 3.6931 |
| Q3 (75%) | 10.1313 |
| IQR | 6.9700 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 3.83 | 0.00% | 0.00% |
| 2025-08 | 6,913 | 9.98 | 0.00% | 24.33% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted/PR6L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted/PR6L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted/PR6L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR6L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted/PR6L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 3.8270 |
| 중앙값 | 3.6957 |
| IQR | 0.5951 |
| Bowley 왜도 | 0.4022 |
| Adj 이상치 수 | 11 |
| Adj 이상치율 | 0.40% |
| Std 이상치율 | 1.19% |
| 개선율 | 66.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-09: 7건
- 2. 2025-05-28: 4건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR6L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 9.9762 |
| 중앙값 | 3.6686 |
| IQR | 16.3851 |
| Bowley 왜도 | 0.9319 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR6L1_ACT_TORQUE_00_summary.png)

---

#### [L1] PR7L1_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9233 | **승수 (L/U)**: 0.397/2.518

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -7.5548 | -24.9313 |
| 상한 경계 | 95.6865 | 51.9392 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 11.3270 |
| 표준편차 | 9.0749 |
| Q1 (25%) | 3.8951 |
| 중앙값 | 4.6320 |
| Q3 (75%) | 23.1128 |
| IQR | 19.2176 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 11.67 | 0.00% | 0.00% |
| 2025-08 | 6,913 | 11.19 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted/PR7L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted/PR7L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted/PR7L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR7L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted/PR7L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 11.6740 |
| 중앙값 | 4.9638 |
| IQR | 21.1849 |
| Bowley 왜도 | 0.8764 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 11.1873 |
| 중앙값 | 4.6146 |
| IQR | 17.3585 |
| Bowley 왜도 | 0.9205 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L1_ACT_TORQUE_00_summary.png)

---

#### [L2] PR7L2_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9299 | **승수 (L/U)**: 0.395/2.534

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -5.6823 | -21.4011 |
| 상한 경계 | 87.6724 | 47.8383 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 11.5295 |
| 표준편차 | 8.6985 |
| Q1 (25%) | 4.5636 |
| 중앙값 | 5.1707 |
| Q3 (75%) | 21.8735 |
| IQR | 17.3099 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 12.40 | 0.00% | 0.00% |
| 2025-08 | 6,913 | 11.18 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted/PR7L2_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted/PR7L2_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted/PR7L2_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR7L2_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted/PR7L2_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 12.4029 |
| 중앙값 | 7.0622 |
| IQR | 19.6620 |
| Bowley 왜도 | 0.7566 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR7L2_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 11.1781 |
| 중앙값 | 4.9495 |
| IQR | 15.9530 |
| Bowley 왜도 | 0.9478 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR7L2_ACT_TORQUE_00_summary.png)

---

#### [L1] PR8L1_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.9349 | **승수 (L/U)**: 0.393/2.547

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -6.3702 | -22.8682 |
| 상한 경계 | 91.5858 | 49.5656 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | 10.7634 |
| 표준편차 | 9.1055 |
| Q1 (25%) | 4.2945 |
| 중앙값 | 4.8838 |
| Q3 (75%) | 22.4029 |
| IQR | 18.1085 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | 11.13 | 0.00% | 0.00% |
| 2025-08 | 6,913 | 10.62 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted/PR8L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted/PR8L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted/PR8L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR8L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted/PR8L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | 11.1280 |
| 중앙값 | 5.3103 |
| IQR | 20.0001 |
| Bowley 왜도 | 0.8893 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted/PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted/PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR8L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | 10.6168 |
| 중앙값 | 4.7956 |
| IQR | 16.2059 |
| Bowley 왜도 | 0.9424 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted/PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted/PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR8L1_ACT_TORQUE_00_summary.png)

---

#### [L1] PR9L1_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8371 | **승수 (L/U)**: 2.310/0.433

**데이터**: 원본 15,839 → 필터 후 9,694 (38.8% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -150.9645 | -83.4372 |
| 상한 경계 | 24.8200 | 54.0566 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 9,694 |
| 평균 | -11.5340 |
| 표준편차 | 16.1524 |
| Q1 (25%) | -31.8770 |
| 중앙값 | -0.3031 |
| Q3 (75%) | 2.4964 |
| IQR | 34.3735 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 2,781 | -12.37 | 0.00% | 0.00% |
| 2025-08 | 6,913 | -11.20 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted/PR9L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted/PR9L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted/PR9L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR9L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted/PR9L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,781 |
| 평균 | -12.3725 |
| 중앙값 | -4.5463 |
| IQR | 34.7243 |
| Bowley 왜도 | -0.5891 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted/PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted/PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted/PR9L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,913 |
| 평균 | -11.1966 |
| 중앙값 | 1.1571 |
| IQR | 34.1470 |
| Bowley 왜도 | -0.9231 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted/PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted/PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted/PR9L1_ACT_TORQUE_00_summary.png)

---


---

## 월별 이상치율 추이

| 월 | Adjusted IQR 평균 | Standard IQR 평균 | 개선율 |
|-----|------------------|-------------------|--------|
| 2025-03 | N/A | N/A | N/A |
| 2025-04 | N/A | N/A | N/A |
| 2025-05 | 2.60% | 2.65% | 2.1% |
| 2025-06 | N/A | N/A | N/A |
| 2025-07 | N/A | N/A | N/A |
| 2025-08 | 1.83% | 2.23% | 18.0% |

---

## 상위 개선 태그 (Top 10)

Adjusted IQR 적용으로 가장 큰 개선을 보인 태그:

| 순위 | 태그명 | Std 이상치율 | Adj 이상치율 | 개선율 | Bowley 왜도 |
|------|--------|--------------|--------------|--------|-------------|
| 1 | PR6L1_ACT_TORQUE | 17.35% | 0.00% | **100.0%** | 0.8474 |
| 2 | HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 7.81% | 0.51% | **93.5%** | -0.5353 |
| 3 | HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 7.58% | 0.50% | **93.4%** | -0.5423 |
| 4 | PINCHROLL_2_ACTUAL_SPEED | 5.26% | 1.30% | **75.3%** | -0.7432 |
| 5 | PR6L2_ACT_TORQUE | 5.59% | 5.01% | **10.3%** | 0.4555 |
| 6 | HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 3.67% | 3.30% | **10.2%** | -0.1784 |
| 7 | SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 19.67% | 19.08% | **3.0%** | -0.2707 |
| 8 | INDIRECT_COOLING_WATER_FLOW | 9.70% | 9.52% | **1.8%** | 0.0563 |
| 9 | SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 19.84% | 19.58% | **1.3%** | -0.2459 |
| 10 | FURNACE_PRESSURE | 0.26% | 0.26% | **0.0%** | 0.0239 |

---

## 높은 왜도 태그 분석

Bowley 왜도 절대값이 큰 태그 (비대칭 분포):

| 태그명 | Bowley 왜도 | 분포 방향 | 승수 (L/U) | 개선율 |
|--------|-------------|----------|------------|--------|
| PINCHROLL_2_ACTUAL_TORQUE | -0.9999 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_10_ACTUAL_SPEED | -0.9801 | ← 왼쪽 치우침 | 2.665/0.375 | 0.0% |
| FINISHING_BLOCK_ACTUAL_SPEED | -0.9767 | ← 왼쪽 치우침 | 2.656/0.377 | 0.0% |
| STAND_6_ACTUAL_SPEED | -0.9765 | ← 왼쪽 치우침 | 2.655/0.377 | 0.0% |
| STAND_14_ACTUAL_SPEED | -0.9720 | ← 왼쪽 치우침 | 2.643/0.378 | 0.0% |
| STAND_1_ACTUAL_SPEED | -0.9713 | ← 왼쪽 치우침 | 2.641/0.379 | 0.0% |
| STAND_12_ACTUAL_SPEED | -0.9699 | ← 왼쪽 치우침 | 2.638/0.379 | 0.0% |
| STAND_4_ACTUAL_SPEED | -0.9686 | ← 왼쪽 치우침 | 2.634/0.380 | 0.0% |
| STAND_11_ACTUAL_SPEED | -0.9684 | ← 왼쪽 치우침 | 2.634/0.380 | 0.0% |
| STAND_13_ACTUAL_SPEED | -0.9669 | ← 왼쪽 치우침 | 2.630/0.380 | 0.0% |


---

## 결론 및 권장사항

### 분석 결과 요약

1. **전체 개선 효과**: Adjusted IQR 적용으로 평균 **-0.2%** 이상치율 감소
2. **총 이상치 감소**: 26,781 → 23,903 (2,878개 감소)
3. **위험등급 개선**: CRITICAL/DANGER 태그 6개 → 5개

### c 값 검토

- **현재 c 값**: 1.0
- **권장 조정**:
  - 개선율이 낮은 경우 c 값 증가 (1.0~1.2)
  - 과도한 보정 시 c 값 감소 (0.6~0.8)

### 후속 조치

1. 높은 왜도 태그에 대한 데이터 품질 검토
2. 월별 추이가 불안정한 태그 모니터링 강화
3. 개선율이 낮은 태그에 대한 별도 분석 (MAD, Percentile 등 대안 방법 검토)

---

*이 보고서는 Adjusted IQR 방법론 (Bowley 왜도 보정)을 적용하여 자동 생성되었습니다.*

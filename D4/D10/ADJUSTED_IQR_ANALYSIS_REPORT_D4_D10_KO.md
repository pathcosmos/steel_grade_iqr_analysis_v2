# 강종 [D4 / D10] Adjusted IQR 상세 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D4
**규격**: D10
**분석 방법**: Adjusted IQR (Bowley 왜도 보정)
**c 값**: 1.0
**생성일시**: 2026-02-06 16:58:47

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
| **분석 대상 강종** | D4 / D10 |
| **c 값 (왜도 보정 강도)** | 1.0 |
| **총 분석 태그 수** | 78개 |
| **PR_Detailed L1 태그** | 4개 |
| **PR_Detailed L2 태그** | 2개 |

### 이상치율 개선 효과

| 지표 | Standard IQR | Adjusted IQR | 개선 |
|------|-------------|--------------|------|
| **총 이상치 수** | 46,386 | 43,911 | 2,475 감소 |
| **평균 개선율** | - | - | **0.9%** |

### 위험도 분포 비교

| 등급 | Standard IQR | Adjusted IQR | 변화 |
|------|-------------|--------------|------|
| **⚫ 심각 (25% 이상)** | 1개 | 1개 | +0 |
| **🔴 위험 (15~25%)** | 6개 | 3개 | +3 |
| **🟠 경고 (10~15%)** | 13개 | 15개 | -2 |
| **🟡 주의 (5~10%)** | 1개 | 2개 | -1 |
| **🟢 양호 (0~5%)** | 57개 | 57개 | +0 |

---

## 카테고리별 상세 분석


### 01_Furnace_Top_Temperature (가열로 상부 온도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 0.47% | 0.25% | -88.9% | -0.5685 | 1.766/0.566 | 🟢 NORMAL |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 0.41% | 0.23% | -78.8% | -0.5689 | 1.766/0.566 | 🟢 NORMAL |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 0.00% | 0.00% | 0.0% | -0.5514 | 1.736/0.576 | 🟢 NORMAL |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 0.00% | 0.00% | 0.0% | -0.5381 | 1.713/0.584 | 🟢 NORMAL |

### 02_Furnace_Bottom_Temperature (가열로 하부 온도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 0.06% | 0.26% | 76.3% | 0.1124 | 0.894/1.119 | 🟢 NORMAL |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 0.00% | 0.10% | 100.0% | 0.1270 | 0.881/1.135 | 🟢 NORMAL |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 0.00% | 0.00% | 0.0% | -0.0011 | 1.001/0.999 | 🟢 NORMAL |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 0.00% | 0.00% | 0.0% | -0.0726 | 1.075/0.930 | 🟢 NORMAL |

### 03_Furnace_Discharge_Temperature (가열로 추출 온도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 6.69% | 6.67% | -0.3% | 0.2721 | 0.762/1.313 | 🟡 CAUTION |

### 04_Furnace_Auxiliary (가열로 보조설비)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| FURNACE_O2_ANALYZER | 19.37% | 19.40% | 0.1% | -0.2414 | 1.273/0.786 | 🔴 DANGER |
| MAIN_GAS_PRESSURE | 3.87% | 4.21% | 8.1% | -0.1716 | 1.187/0.842 | 🟢 NORMAL |
| MAIN_COMBUSTION_AIR_PRESSURE | 3.57% | 3.71% | 3.9% | 0.0853 | 0.918/1.089 | 🟢 NORMAL |
| FURNACE_PRESSURE | 1.19% | 0.65% | -81.9% | -0.1422 | 1.153/0.867 | 🟢 NORMAL |
| COMBUSTION_AIR_TEMPERATURE | 0.28% | 0.31% | 11.1% | 0.0733 | 0.929/1.076 | 🟢 NORMAL |
| MAIN_GAS_TEMPERATURE | 0.00% | 0.00% | 0.0% | 0.1771 | 0.838/1.194 | 🟢 NORMAL |
| MAIN_GAS_FLOW | 0.00% | 0.00% | 0.0% | -0.3691 | 1.446/0.691 | 🟢 NORMAL |
| INDIRECT_COOLING_WATER_FLOW | 0.00% | 0.00% | 0.0% | 0.7640 | 0.466/2.147 | 🟢 NORMAL |
| INDIRECT_WATER_MAIN_TEMPERATURE | 0.00% | 0.00% | 0.0% | 0.3403 | 0.712/1.405 | 🟢 NORMAL |

### 05_Stand_Torque (스탠드 토크)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| STAND_1_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6995 | 2.013/0.497 | 🟢 NORMAL |
| STAND_2_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.8011 | 2.228/0.449 | 🟢 NORMAL |
| STAND_3_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7639 | 2.147/0.466 | 🟢 NORMAL |
| STAND_4_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6898 | 1.993/0.502 | 🟢 NORMAL |
| STAND_5_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7769 | 2.175/0.460 | 🟢 NORMAL |
| STAND_6_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7339 | 2.083/0.480 | 🟢 NORMAL |
| STAND_7_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.8273 | 2.287/0.437 | 🟢 NORMAL |
| STAND_8_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6621 | 1.939/0.516 | 🟢 NORMAL |
| STAND_9_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.8225 | 2.276/0.439 | 🟢 NORMAL |
| STAND_10_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7933 | 2.211/0.452 | 🟢 NORMAL |
| STAND_11_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7535 | 2.124/0.471 | 🟢 NORMAL |
| STAND_12_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6864 | 1.987/0.503 | 🟢 NORMAL |
| STAND_13_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.8546 | 2.350/0.425 | 🟢 NORMAL |
| STAND_14_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.8820 | 2.416/0.414 | 🟢 NORMAL |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6352 | 1.887/0.530 | 🟢 NORMAL |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6357 | 1.888/0.530 | 🟢 NORMAL |

### 06_Stand_Speed (스탠드 속도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| STAND_5_ACTUAL_SPEED | 31.43% | 13.23% | -137.6% | -0.4555 | 1.577/0.634 | ⚫ CRITICAL |
| STAND_11_ACTUAL_SPEED | 22.24% | 22.86% | 2.7% | 0.0377 | 0.963/1.038 | 🔴 DANGER |
| STAND_4_ACTUAL_SPEED | 14.13% | 13.48% | -4.9% | -0.0608 | 1.063/0.941 | 🟠 WARNING |
| STAND_6_ACTUAL_SPEED | 13.70% | 15.13% | 9.5% | 0.1531 | 0.858/1.165 | 🟠 WARNING |
| FINISHING_BLOCK_ACTUAL_SPEED | 13.64% | 33.79% | 59.6% | 0.9602 | 0.383/2.612 | 🟠 WARNING |
| STAND_14_ACTUAL_SPEED | 13.56% | 13.55% | -0.1% | 0.2917 | 0.747/1.339 | 🟠 WARNING |
| STAND_10_ACTUAL_SPEED | 13.55% | 15.37% | 11.9% | 0.2784 | 0.757/1.321 | 🟠 WARNING |
| STAND_12_ACTUAL_SPEED | 13.48% | 13.49% | 0.1% | -0.2255 | 1.253/0.798 | 🟠 WARNING |
| STAND_9_ACTUAL_SPEED | 13.35% | 13.35% | 0.0% | -0.0009 | 1.001/0.999 | 🟠 WARNING |
| STAND_13_ACTUAL_SPEED | 13.24% | 13.31% | 0.5% | -0.5241 | 1.689/0.592 | 🟠 WARNING |
| STAND_8_ACTUAL_SPEED | 13.22% | 13.15% | -0.5% | 0.6173 | 0.539/1.854 | 🟠 WARNING |
| STAND_2_ACTUAL_SPEED | 13.19% | 13.11% | -0.6% | 0.2277 | 0.796/1.256 | 🟠 WARNING |
| STAND_7_ACTUAL_SPEED | 13.18% | 13.17% | -0.1% | 0.0911 | 0.913/1.095 | 🟠 WARNING |
| STAND_1_ACTUAL_SPEED | 13.17% | 13.04% | -1.0% | 0.5209 | 0.594/1.684 | 🟠 WARNING |
| STAND_3_ACTUAL_SPEED | 13.08% | 13.17% | 0.6% | -0.2456 | 1.278/0.782 | 🟠 WARNING |

### 07_Stand_Load (스탠드 부하)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| STAND_1_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_2_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_3_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_4_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_5_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_6_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_7_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_8_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_9_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_10_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_11_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_12_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_13_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| STAND_14_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |
| FINISHING_BLOCK_LOAD | 0.00% | 0.00% | 0.0% | -1.0000 | 2.718/0.368 | 🟢 NORMAL |

### 08_Pinchroll (핀치롤)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| PINCHROLL_4_ACTUAL_TORQUE | 17.50% | 15.97% | -9.6% | 0.8138 | 0.443/2.256 | 🔴 DANGER |
| PINCHROLL_2_ACTUAL_SPEED | 13.10% | 14.18% | 7.6% | -0.1238 | 1.132/0.884 | 🟠 WARNING |
| PINCHROLL_4_REFERENCE_TORQUE | 11.16% | 13.22% | 15.6% | 0.4931 | 0.611/1.637 | 🟠 WARNING |
| PINCHROLL_2_ACTUAL_TORQUE | 2.14% | 16.06% | 86.7% | -0.9998 | 2.718/0.368 | 🟢 NORMAL |
| PINCHROLL_4_ACTUAL_SPEED | 0.00% | 0.00% | 0.0% | -0.8367 | 2.309/0.433 | 🟢 NORMAL |
| PINCHROLL_3_ACTUAL_SPEED | 0.00% | 0.02% | 100.0% | -0.9608 | 2.614/0.383 | 🟢 NORMAL |
| PINCHROLL_3_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7851 | 2.193/0.456 | 🟢 NORMAL |
| PINCHROLL_3_REFERENCE_TORQUE | 0.00% | 0.00% | 0.0% | 0.8046 | 0.447/2.236 | 🟢 NORMAL |

### 09_PR_Detailed (PR 상세 토크)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| [L1] PR6L1_ACT_TORQUE | 5.52% | 4.76% | -16.0% | -0.8761 | 2.402/0.416 | 🟡 CAUTION |
| [L2] PR7L2_ACT_TORQUE | 1.11% | 0.85% | -30.1% | -0.9597 | 2.611/0.383 | 🟢 NORMAL |
| [L1] PR7L1_ACT_TORQUE | 1.03% | 0.92% | -11.7% | -0.7992 | 2.224/0.450 | 🟢 NORMAL |
| [L1] PR8L1_ACT_TORQUE | 0.56% | 0.56% | 0.0% | 0.0202 | 0.980/1.020 | 🟢 NORMAL |
| [L2] PR6L2_ACT_TORQUE | 0.51% | 0.45% | -13.0% | -0.9118 | 2.489/0.402 | 🟢 NORMAL |
| [L1] PR9L1_ACT_TORQUE | 0.37% | 0.75% | 50.5% | -0.4626 | 1.588/0.630 | 🟢 NORMAL |

---

## 태그별 상세 분석 (위험도 순)


### ⚫ 심각 (25% 이상) - 1개 태그

#### STAND_5_ACTUAL_SPEED ⚫

**위험도**: [CRITICAL] | **이상치율**: 31.43% | **개선율**: -137.6%
**Bowley 왜도**: -0.4555 | **승수 (L/U)**: 1.577/0.634

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 4,457 | 1,876 |
| 이상치율 | 31.43% | 13.23% |
| 하한 경계 | 869.4980 | 940.8549 |
| 상한 경계 | 1225.4388 | 1270.6899 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 991.8580 |
| 표준편차 | 384.2146 |
| Q1 (25%) | 1064.5430 |
| 중앙값 | 1124.5510 |
| Q3 (75%) | 1147.0018 |
| IQR | 82.4588 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 1038.91 | 46.70% | 12.08% |
| 2025-06 | 2,831 | 966.92 | 13.99% | 14.02% |
| 2025-07 | 1,394 | 901.66 | 31.35% | 22.45% |
| 2025-08 | 2,844 | 943.24 | 10.65% | 10.79% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-18 | 2,833 |
| 2 | 2025-05-17 | 488 |
| 3 | 2025-07-05 | 437 |
| 4 | 2025-06-12 | 396 |
| 5 | 2025-08-11 | 303 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 2,833건 (2025-05-18)
- 평균 일별 이상치: 891.4건


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
| 분석 레코드 | 7,111 |
| 평균 | 1038.9128 |
| 중앙값 | 1141.1580 |
| IQR | 100.9145 |
| Bowley 왜도 | 0.7376 |
| Adj 이상치 수 | 856 |
| Adj 이상치율 | 12.04% |
| Std 이상치율 | 12.01% |
| 개선율 | -0.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 491건
- 2. 2025-05-18: 365건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 966.9181 |
| 중앙값 | 1116.9660 |
| IQR | 10.1290 |
| Bowley 왜도 | -0.0218 |
| Adj 이상치 수 | 433 |
| Adj 이상치율 | 15.29% |
| Std 이상치율 | 15.29% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 433건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_5_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 901.6568 |
| 중앙값 | 1127.4880 |
| IQR | 99.5928 |
| Bowley 왜도 | 0.7880 |
| Adj 이상치 수 | 314 |
| Adj 이상치율 | 22.53% |
| Std 이상치율 | 22.45% |
| 개선율 | -0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 314건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_5_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 943.2428 |
| 중앙값 | 1055.6640 |
| IQR | 47.4900 |
| Bowley 왜도 | -0.5078 |
| Adj 이상치 수 | 303 |
| Adj 이상치율 | 10.65% |
| Std 이상치율 | 10.79% |
| 개선율 | 1.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 303건

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


### 🔴 위험 (15~25%) - 3개 태그

#### STAND_11_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 22.24% | **개선율**: 2.7%
**Bowley 왜도**: 0.0377 | **승수 (L/U)**: 0.963/1.038

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,153 | 3,241 |
| 이상치율 | 22.24% | 22.86% |
| 하한 경계 | 967.4619 | 965.7724 |
| 상한 경계 | 1089.2119 | 1087.4574 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 901.4272 |
| 표준편차 | 349.2756 |
| Q1 (25%) | 1011.4043 |
| 중앙값 | 1026.0410 |
| Q3 (75%) | 1041.8255 |
| IQR | 30.4212 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 902.82 | 12.50% | 12.50% |
| 2025-06 | 2,831 | 937.36 | 57.75% | 60.86% |
| 2025-07 | 1,394 | 798.71 | 22.81% | 22.81% |
| 2025-08 | 2,844 | 912.53 | 10.94% | 10.94% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 1,635 |
| 2 | 2025-05-17 | 499 |
| 3 | 2025-05-18 | 390 |
| 4 | 2025-07-05 | 318 |
| 5 | 2025-08-11 | 311 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 1,635건 (2025-06-12)
- 평균 일별 이상치: 630.6건


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
| 분석 레코드 | 7,111 |
| 평균 | 902.8202 |
| 중앙값 | 1022.7810 |
| IQR | 25.7550 |
| Bowley 왜도 | 0.0511 |
| Adj 이상치 수 | 889 |
| Adj 이상치율 | 12.50% |
| Std 이상치율 | 12.50% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 499건
- 2. 2025-05-18: 390건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 937.3561 |
| 중앙값 | 1083.5080 |
| IQR | 27.7560 |
| Bowley 왜도 | -0.2564 |
| Adj 이상치 수 | 399 |
| Adj 이상치율 | 14.09% |
| Std 이상치율 | 14.09% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 399건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_11_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 798.7113 |
| 중앙값 | 1025.0890 |
| IQR | 18.8150 |
| Bowley 왜도 | 0.5537 |
| Adj 이상치 수 | 318 |
| Adj 이상치율 | 22.81% |
| Std 이상치율 | 23.17% |
| 개선율 | 1.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 318건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_11_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 912.5262 |
| 중앙값 | 1022.5975 |
| IQR | 27.7001 |
| Bowley 왜도 | -0.7223 |
| Adj 이상치 수 | 439 |
| Adj 이상치율 | 15.44% |
| Std 이상치율 | 10.90% |
| 개선율 | -41.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 439건

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

#### FURNACE_O2_ANALYZER 🔴

**위험도**: [DANGER] | **이상치율**: 19.37% | **개선율**: 0.1%
**Bowley 왜도**: -0.2414 | **승수 (L/U)**: 1.273/0.786

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 2,786 | 2,790 |
| 이상치율 | 19.37% | 19.40% |
| 하한 경계 | 9.5079 | 9.5125 |
| 상한 경계 | 9.5538 | 9.5574 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 8.0071 |
| 표준편차 | 3.3502 |
| Q1 (25%) | 9.5293 |
| 중앙값 | 9.5363 |
| Q3 (75%) | 9.5405 |
| IQR | 0.0112 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 9.45 | 2.67% | 2.70% |
| 2025-06 | 2,878 | 9.52 | 1.60% | 1.60% |
| 2025-07 | 1,440 | 8.98 | 16.25% | 16.39% |
| 2025-08 | 2,876 | 2.39 | 80.46% | 80.46% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-11 | 2,314 |
| 2 | 2025-07-05 | 234 |
| 3 | 2025-05-17 | 144 |
| 4 | 2025-05-18 | 48 |
| 5 | 2025-06-12 | 46 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 2,314건 (2025-08-11)
- 평균 일별 이상치: 557.2건


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
| 분석 레코드 | 7,190 |
| 평균 | 9.4538 |
| 중앙값 | 9.5405 |
| IQR | 0.0041 |
| Bowley 왜도 | 0.0775 |
| Adj 이상치 수 | 194 |
| Adj 이상치율 | 2.70% |
| Std 이상치율 | 2.70% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 146건
- 2. 2025-05-18: 48건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 9.5154 |
| 중앙값 | 9.5347 |
| IQR | 0.0042 |
| Bowley 왜도 | -0.2002 |
| Adj 이상치 수 | 52 |
| Adj 이상치율 | 1.81% |
| Std 이상치율 | 1.81% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 52건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_O2_ANALYZER_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 8.9790 |
| 중앙값 | 9.5292 |
| IQR | 0.0056 |
| Bowley 왜도 | -0.2404 |
| Adj 이상치 수 | 236 |
| Adj 이상치율 | 16.39% |
| Std 이상치율 | 16.39% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 236건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_O2_ANALYZER_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 2.3946 |
| 중앙값 | 0.4158 |
| IQR | 0.9721 |
| Bowley 왜도 | 0.7407 |
| Adj 이상치 수 | 636 |
| Adj 이상치율 | 22.11% |
| Std 이상치율 | 22.88% |
| 개선율 | 3.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 636건

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

#### PINCHROLL_4_ACTUAL_TORQUE 🔴

**위험도**: [DANGER] | **이상치율**: 17.50% | **개선율**: -9.6%
**Bowley 왜도**: 0.8138 | **승수 (L/U)**: 0.443/2.256

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 2,111 | 1,926 |
| 이상치율 | 17.50% | 15.97% |
| 하한 경계 | 21.4599 | 17.0243 |
| 상한 경계 | 48.2755 | 38.2671 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 24.6444 |
| 표준편차 | 8.7017 |
| Q1 (25%) | 24.9904 |
| 중앙값 | 25.4849 |
| Q3 (75%) | 30.3011 |
| IQR | 5.3107 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 25.73 | 14.79% | 13.54% |
| 2025-06 | 2,348 | 25.19 | 22.66% | 20.70% |
| 2025-07 | 1,054 | 23.06 | 25.33% | 23.24% |
| 2025-08 | 2,501 | 22.12 | 16.03% | 14.43% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 532 |
| 2 | 2025-05-18 | 459 |
| 3 | 2025-05-17 | 452 |
| 4 | 2025-08-11 | 401 |
| 5 | 2025-07-05 | 267 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 532건 (2025-06-12)
- 평균 일별 이상치: 422.2건


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
| 분석 레코드 | 6,158 |
| 평균 | 25.7343 |
| 중앙값 | 26.5752 |
| IQR | 5.7269 |
| Bowley 왜도 | 0.4474 |
| Adj 이상치 수 | 879 |
| Adj 이상치율 | 14.27% |
| Std 이상치율 | 13.32% |
| 개선율 | -7.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 441건
- 2. 2025-05-17: 438건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 25.1856 |
| 중앙값 | 29.9942 |
| IQR | 2.2646 |
| Bowley 왜도 | -0.9943 |
| Adj 이상치 수 | 846 |
| Adj 이상치율 | 36.03% |
| Std 이상치율 | 23.51% |
| 개선율 | -53.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 846건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 23.0594 |
| 중앙값 | 24.9969 |
| IQR | 8.0528 |
| Bowley 왜도 | -0.0142 |
| Adj 이상치 수 | 219 |
| Adj 이상치율 | 20.78% |
| Std 이상치율 | 20.87% |
| 개선율 | 0.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 219건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 22.1209 |
| 중앙값 | 24.9935 |
| IQR | 2.7734 |
| Bowley 왜도 | -0.9957 |
| Adj 이상치 수 | 715 |
| Adj 이상치율 | 28.59% |
| Std 이상치율 | 14.51% |
| 개선율 | -97.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 715건

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


### 🟠 경고 (10~15%) - 15개 태그

#### STAND_4_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 14.13% | **개선율**: -4.9%
**Bowley 왜도**: -0.0608 | **승수 (L/U)**: 1.063/0.941

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 2,004 | 1,911 |
| 이상치율 | 14.13% | 13.48% |
| 하한 경계 | 666.8608 | 670.9126 |
| 상한 경계 | 839.3973 | 843.2100 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 671.0287 |
| 표준편차 | 259.2320 |
| Q1 (25%) | 735.5241 |
| 중앙값 | 758.3712 |
| Q3 (75%) | 778.5984 |
| IQR | 43.0743 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 702.00 | 13.78% | 12.45% |
| 2025-06 | 2,831 | 638.15 | 14.16% | 14.24% |
| 2025-07 | 1,394 | 592.19 | 22.53% | 22.53% |
| 2025-08 | 2,844 | 664.97 | 10.86% | 10.86% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 491 |
| 2 | 2025-05-18 | 489 |
| 3 | 2025-06-12 | 401 |
| 4 | 2025-07-05 | 314 |
| 5 | 2025-08-11 | 309 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 491건 (2025-05-17)
- 평균 일별 이상치: 400.8건


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
| 분석 레코드 | 7,111 |
| 평균 | 701.9960 |
| 중앙값 | 771.5384 |
| IQR | 64.3312 |
| Bowley 왜도 | 0.7460 |
| Adj 이상치 수 | 856 |
| Adj 이상치율 | 12.04% |
| Std 이상치율 | 12.04% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 491건
- 2. 2025-05-18: 365건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 638.1534 |
| 중앙값 | 736.9729 |
| IQR | 8.1958 |
| Bowley 왜도 | -0.1003 |
| Adj 이상치 수 | 502 |
| Adj 이상치율 | 17.73% |
| Std 이상치율 | 15.58% |
| 개선율 | -13.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 502건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_4_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 592.1933 |
| 중앙값 | 738.0976 |
| IQR | 72.4702 |
| Bowley 왜도 | 0.7772 |
| Adj 이상치 수 | 314 |
| Adj 이상치율 | 22.53% |
| Std 이상치율 | 22.45% |
| 개선율 | -0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 314건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_4_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 664.9660 |
| 중앙값 | 745.1229 |
| IQR | 35.9787 |
| Bowley 왜도 | -0.5656 |
| Adj 이상치 수 | 308 |
| Adj 이상치율 | 10.83% |
| Std 이상치율 | 10.79% |
| 개선율 | -0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 308건

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

#### STAND_6_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.70% | **개선율**: 9.5%
**Bowley 왜도**: 0.1531 | **승수 (L/U)**: 0.858/1.165

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,942 | 2,146 |
| 이상치율 | 13.70% | 15.13% |
| 하한 경계 | 997.4298 | 987.2274 |
| 상한 경계 | 1190.7193 | 1178.8284 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 957.3016 |
| 표준편차 | 369.0650 |
| Q1 (25%) | 1059.0777 |
| 중앙값 | 1079.3600 |
| Q3 (75%) | 1106.9780 |
| IQR | 47.9003 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 986.77 | 12.90% | 15.10% |
| 2025-06 | 2,831 | 948.16 | 14.16% | 14.16% |
| 2025-07 | 1,394 | 859.57 | 22.53% | 26.04% |
| 2025-08 | 2,844 | 940.63 | 10.90% | 10.83% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 491 |
| 2 | 2025-05-18 | 426 |
| 3 | 2025-06-12 | 401 |
| 4 | 2025-07-05 | 314 |
| 5 | 2025-08-11 | 310 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 491건 (2025-05-17)
- 평균 일별 이상치: 388.4건


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
| 분석 레코드 | 7,111 |
| 평균 | 986.7654 |
| 중앙값 | 1081.8130 |
| IQR | 102.1135 |
| Bowley 왜도 | 0.7343 |
| Adj 이상치 수 | 856 |
| Adj 이상치율 | 12.04% |
| Std 이상치율 | 12.01% |
| 개선율 | -0.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 491건
- 2. 2025-05-18: 365건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 948.1632 |
| 중앙값 | 1095.6360 |
| IQR | 11.6650 |
| Bowley 왜도 | -0.1182 |
| Adj 이상치 수 | 427 |
| Adj 이상치율 | 15.08% |
| Std 이상치율 | 14.31% |
| 개선율 | -5.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 427건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_6_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 859.5682 |
| 중앙값 | 1077.8420 |
| IQR | 88.5332 |
| Bowley 왜도 | 0.7326 |
| Adj 이상치 수 | 313 |
| Adj 이상치율 | 22.45% |
| Std 이상치율 | 22.45% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 313건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_6_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 940.6326 |
| 중앙값 | 1052.0340 |
| IQR | 41.3783 |
| Bowley 왜도 | -0.4821 |
| Adj 이상치 수 | 311 |
| Adj 이상치율 | 10.94% |
| Std 이상치율 | 10.79% |
| 개선율 | -1.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 311건

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

#### FINISHING_BLOCK_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.64% | **개선율**: 59.6%
**Bowley 왜도**: 0.9602 | **승수 (L/U)**: 0.383/2.612

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,934 | 4,792 |
| 이상치율 | 13.64% | 33.79% |
| 하한 경계 | 917.7560 | 908.3635 |
| 상한 경계 | 973.4806 | 948.9445 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 814.5254 |
| 표준편차 | 312.4760 |
| Q1 (25%) | 923.5814 |
| 중앙값 | 923.7831 |
| Q3 (75%) | 933.7266 |
| IQR | 10.1452 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 832.17 | 12.36% | 51.47% |
| 2025-06 | 2,831 | 791.58 | 15.44% | 15.37% |
| 2025-07 | 1,394 | 731.62 | 21.81% | 27.47% |
| 2025-08 | 2,844 | 833.88 | 11.04% | 11.04% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 500 |
| 2 | 2025-06-12 | 437 |
| 3 | 2025-05-18 | 379 |
| 4 | 2025-08-11 | 314 |
| 5 | 2025-07-05 | 304 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 500건 (2025-05-17)
- 평균 일별 이상치: 386.8건


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
| 분석 레코드 | 7,111 |
| 평균 | 832.1720 |
| 중앙값 | 923.8123 |
| IQR | 41.8947 |
| Bowley 왜도 | 0.9951 |
| Adj 이상치 수 | 875 |
| Adj 이상치율 | 12.30% |
| Std 이상치율 | 12.30% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 499건
- 2. 2025-05-18: 376건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 791.5806 |
| 중앙값 | 923.5741 |
| IQR | 0.0806 |
| Bowley 왜도 | 0.1613 |
| Adj 이상치 수 | 1,019 |
| Adj 이상치율 | 35.99% |
| Std 이상치율 | 35.92% |
| 개선율 | -0.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 1,019건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 731.6209 |
| 중앙값 | 923.5665 |
| IQR | 0.7047 |
| Bowley 왜도 | -0.2735 |
| Adj 이상치 수 | 626 |
| Adj 이상치율 | 44.91% |
| Std 이상치율 | 44.76% |
| 개선율 | -0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 626건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 833.8787 |
| 중앙값 | 932.0185 |
| IQR | 0.8333 |
| Bowley 왜도 | 0.5013 |
| Adj 이상치 수 | 692 |
| Adj 이상치율 | 24.33% |
| Std 이상치율 | 24.75% |
| 개선율 | 1.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 692건

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

#### STAND_14_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.56% | **개선율**: -0.1%
**Bowley 왜도**: 0.2917 | **승수 (L/U)**: 0.747/1.339

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,923 | 1,922 |
| 이상치율 | 13.56% | 13.55% |
| 하한 경계 | 1104.4108 | 1096.7125 |
| 상한 경계 | 1188.1659 | 1177.8605 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 989.7397 |
| 표준편차 | 382.7773 |
| Q1 (25%) | 1127.1430 |
| 중앙값 | 1134.3280 |
| Q3 (75%) | 1147.4300 |
| IQR | 20.2870 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 1001.29 | 12.52% | 12.50% |
| 2025-06 | 2,831 | 1001.44 | 14.20% | 14.20% |
| 2025-07 | 1,394 | 873.09 | 22.81% | 22.81% |
| 2025-08 | 2,844 | 1006.40 | 11.01% | 11.01% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 498 |
| 2 | 2025-06-12 | 402 |
| 3 | 2025-05-18 | 392 |
| 4 | 2025-07-05 | 318 |
| 5 | 2025-08-11 | 313 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 498건 (2025-05-17)
- 평균 일별 이상치: 384.6건


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
| 분석 레코드 | 7,111 |
| 평균 | 1001.2864 |
| 중앙값 | 1134.7450 |
| IQR | 17.4830 |
| Bowley 왜도 | 0.3193 |
| Adj 이상치 수 | 890 |
| Adj 이상치율 | 12.52% |
| Std 이상치율 | 12.52% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 498건
- 2. 2025-05-18: 392건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 1001.4368 |
| 중앙값 | 1156.6240 |
| IQR | 6.2775 |
| Bowley 왜도 | 0.3599 |
| Adj 이상치 수 | 405 |
| Adj 이상치율 | 14.31% |
| Std 이상치율 | 20.59% |
| 개선율 | 30.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 405건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_14_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 873.0886 |
| 중앙값 | 1134.7295 |
| IQR | 30.7615 |
| Bowley 왜도 | -0.8317 |
| Adj 이상치 수 | 325 |
| Adj 이상치율 | 23.31% |
| Std 이상치율 | 22.81% |
| 개선율 | -2.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 325건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_14_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 1006.4027 |
| 중앙값 | 1127.2650 |
| IQR | 18.3128 |
| Bowley 왜도 | -0.7018 |
| Adj 이상치 수 | 385 |
| Adj 이상치율 | 13.54% |
| Std 이상치율 | 11.01% |
| 개선율 | -23.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 385건

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

#### STAND_10_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.55% | **개선율**: 11.9%
**Bowley 왜도**: 0.2784 | **승수 (L/U)**: 0.757/1.321

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,921 | 2,180 |
| 이상치율 | 13.55% | 15.37% |
| 하한 경계 | 897.1398 | 885.0403 |
| 상한 경계 | 1033.7956 | 1017.8120 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 834.9927 |
| 표준편차 | 325.1235 |
| Q1 (25%) | 934.8297 |
| 중앙값 | 946.8056 |
| Q3 (75%) | 968.0226 |
| IQR | 33.1929 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 856.81 | 12.50% | 15.44% |
| 2025-06 | 2,831 | 818.42 | 14.24% | 14.16% |
| 2025-07 | 1,394 | 739.58 | 22.81% | 26.61% |
| 2025-08 | 2,844 | 843.71 | 10.94% | 10.90% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 499 |
| 2 | 2025-06-12 | 403 |
| 3 | 2025-05-18 | 390 |
| 4 | 2025-07-05 | 318 |
| 5 | 2025-08-11 | 311 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 499건 (2025-05-17)
- 평균 일별 이상치: 384.2건


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
| 분석 레코드 | 7,111 |
| 평균 | 856.8113 |
| 중앙값 | 948.4268 |
| IQR | 70.7253 |
| Bowley 왜도 | 0.7522 |
| Adj 이상치 수 | 889 |
| Adj 이상치율 | 12.50% |
| Std 이상치율 | 12.40% |
| 개선율 | -0.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 499건
- 2. 2025-05-18: 390건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 818.4172 |
| 중앙값 | 945.9026 |
| IQR | 18.4484 |
| Bowley 왜도 | -0.3501 |
| Adj 이상치 수 | 403 |
| Adj 이상치율 | 14.24% |
| Std 이상치율 | 14.24% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 403건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_10_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 739.5789 |
| 중앙값 | 931.7286 |
| IQR | 69.8316 |
| Bowley 왜도 | 0.7940 |
| Adj 이상치 수 | 318 |
| Adj 이상치율 | 22.81% |
| Std 이상치율 | 22.81% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 318건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_10_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 843.7058 |
| 중앙값 | 948.0296 |
| IQR | 41.2935 |
| Bowley 왜도 | -0.7222 |
| Adj 이상치 수 | 356 |
| Adj 이상치율 | 12.52% |
| Std 이상치율 | 10.90% |
| 개선율 | -14.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 356건

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

#### STAND_12_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.48% | **개선율**: 0.1%
**Bowley 왜도**: -0.2255 | **승수 (L/U)**: 1.253/0.798

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,911 | 1,913 |
| 이상치율 | 13.48% | 13.49% |
| 하한 경계 | 973.1953 | 986.4599 |
| 상한 경계 | 1115.6787 | 1126.2649 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 922.6011 |
| 표준편차 | 356.9239 |
| Q1 (25%) | 1038.8868 |
| 중앙값 | 1060.3040 |
| Q3 (75%) | 1073.8380 |
| IQR | 34.9512 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 930.93 | 12.45% | 12.47% |
| 2025-06 | 2,831 | 927.99 | 14.06% | 14.06% |
| 2025-07 | 1,394 | 806.40 | 22.81% | 22.81% |
| 2025-08 | 2,844 | 953.38 | 10.90% | 10.90% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 497 |
| 2 | 2025-06-12 | 398 |
| 3 | 2025-05-18 | 388 |
| 4 | 2025-07-05 | 318 |
| 5 | 2025-08-11 | 310 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 497건 (2025-05-17)
- 평균 일별 이상치: 382.2건


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
| 분석 레코드 | 7,111 |
| 평균 | 930.9269 |
| 중앙값 | 1056.5960 |
| IQR | 34.6300 |
| Bowley 왜도 | -0.0810 |
| Adj 이상치 수 | 885 |
| Adj 이상치율 | 12.45% |
| Std 이상치율 | 12.47% |
| 개선율 | 0.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 497건
- 2. 2025-05-18: 388건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 927.9851 |
| 중앙값 | 1072.0630 |
| IQR | 26.4280 |
| Bowley 왜도 | -0.2746 |
| Adj 이상치 수 | 401 |
| Adj 이상치율 | 14.16% |
| Std 이상치율 | 14.16% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 401건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_12_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 806.3983 |
| 중앙값 | 1036.0025 |
| IQR | 52.7345 |
| Bowley 왜도 | -0.1459 |
| Adj 이상치 수 | 318 |
| Adj 이상치율 | 22.81% |
| Std 이상치율 | 22.81% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 318건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_12_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 953.3819 |
| 중앙값 | 1066.5420 |
| IQR | 22.7078 |
| Bowley 왜도 | -0.6971 |
| Adj 이상치 수 | 584 |
| Adj 이상치율 | 20.53% |
| Std 이상치율 | 10.94% |
| 개선율 | -87.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 584건

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

#### STAND_9_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.35% | **개선율**: 0.0%
**Bowley 왜도**: -0.0009 | **승수 (L/U)**: 1.001/0.999

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,893 | 1,893 |
| 이상치율 | 13.35% | 13.35% |
| 하한 경계 | 709.4174 | 709.5832 |
| 상한 경계 | 1185.8220 | 1185.9877 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 835.4233 |
| 표준편차 | 327.0856 |
| Q1 (25%) | 888.2349 |
| 중앙값 | 947.8407 |
| Q3 (75%) | 1007.3360 |
| IQR | 119.1011 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 865.77 | 12.33% | 12.33% |
| 2025-06 | 2,831 | 765.96 | 13.85% | 13.85% |
| 2025-07 | 1,394 | 705.39 | 22.81% | 22.81% |
| 2025-08 | 2,844 | 892.41 | 10.76% | 10.76% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 495 |
| 2 | 2025-06-12 | 392 |
| 3 | 2025-05-18 | 382 |
| 4 | 2025-07-05 | 318 |
| 5 | 2025-08-11 | 306 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 495건 (2025-05-17)
- 평균 일별 이상치: 378.6건


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
| 분석 레코드 | 7,111 |
| 평균 | 865.7746 |
| 중앙값 | 954.0474 |
| IQR | 95.3957 |
| Bowley 왜도 | 0.6399 |
| Adj 이상치 수 | 882 |
| Adj 이상치율 | 12.40% |
| Std 이상치율 | 12.36% |
| 개선율 | -0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 495건
- 2. 2025-05-18: 387건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 765.9647 |
| 중앙값 | 885.4301 |
| IQR | 17.0701 |
| Bowley 왜도 | -0.2562 |
| Adj 이상치 수 | 403 |
| Adj 이상치율 | 14.24% |
| Std 이상치율 | 14.24% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 403건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_9_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 705.3928 |
| 중앙값 | 889.8649 |
| IQR | 64.1644 |
| Bowley 왜도 | 0.7472 |
| Adj 이상치 수 | 318 |
| Adj 이상치율 | 22.81% |
| Std 이상치율 | 22.81% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 318건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_9_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 892.4106 |
| 중앙값 | 1002.4575 |
| IQR | 43.7089 |
| Bowley 왜도 | -0.6995 |
| Adj 이상치 수 | 309 |
| Adj 이상치율 | 10.86% |
| Std 이상치율 | 10.90% |
| 개선율 | 0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 309건

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

#### STAND_13_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.24% | **개선율**: 0.5%
**Bowley 왜도**: -0.5241 | **승수 (L/U)**: 1.689/0.592

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,878 | 1,887 |
| 이상치율 | 13.24% | 13.31% |
| 하한 경계 | 649.5544 | 774.3786 |
| 상한 경계 | 1183.6617 | 1257.5708 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 899.9242 |
| 표준편차 | 351.8054 |
| Q1 (25%) | 955.5757 |
| 중앙값 | 1047.6280 |
| Q3 (75%) | 1076.3737 |
| IQR | 120.7980 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 936.16 | 12.18% | 12.28% |
| 2025-06 | 2,831 | 939.21 | 13.67% | 13.74% |
| 2025-07 | 1,394 | 730.39 | 22.81% | 22.81% |
| 2025-08 | 2,844 | 853.33 | 10.79% | 10.79% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 491 |
| 2 | 2025-06-12 | 387 |
| 3 | 2025-05-18 | 375 |
| 4 | 2025-07-05 | 318 |
| 5 | 2025-08-11 | 307 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 491건 (2025-05-17)
- 평균 일별 이상치: 375.6건


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
| 분석 레코드 | 7,111 |
| 평균 | 936.1558 |
| 중앙값 | 1063.9050 |
| IQR | 29.1360 |
| Bowley 왜도 | -0.2046 |
| Adj 이상치 수 | 887 |
| Adj 이상치율 | 12.47% |
| Std 이상치율 | 12.47% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 497건
- 2. 2025-05-18: 390건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 939.2067 |
| 중앙값 | 1085.5300 |
| IQR | 11.5910 |
| Bowley 왜도 | -0.5886 |
| Adj 이상치 수 | 830 |
| Adj 이상치율 | 29.32% |
| Std 이상치율 | 17.80% |
| 개선율 | -64.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 830건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_13_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 730.3946 |
| 중앙값 | 943.8146 |
| IQR | 37.2385 |
| Bowley 왜도 | -0.4273 |
| Adj 이상치 수 | 322 |
| Adj 이상치율 | 23.10% |
| Std 이상치율 | 22.81% |
| 개선율 | -1.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 322건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_13_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 853.3250 |
| 중앙값 | 956.7410 |
| IQR | 23.7948 |
| Bowley 왜도 | -0.8244 |
| Adj 이상치 수 | 584 |
| Adj 이상치율 | 20.53% |
| Std 이상치율 | 10.94% |
| 개선율 | -87.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 584건

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

#### STAND_8_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.22% | **개선율**: -0.5%
**Bowley 왜도**: 0.6173 | **승수 (L/U)**: 0.539/1.854

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,875 | 1,865 |
| 이상치율 | 13.22% | 13.15% |
| 하한 경계 | 870.7829 | 799.5205 |
| 상한 경계 | 1344.2277 | 1212.1197 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 877.9985 |
| 표준편차 | 339.7121 |
| Q1 (25%) | 954.2452 |
| 중앙값 | 973.9854 |
| Q3 (75%) | 1057.3950 |
| IQR | 103.1498 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 891.23 | 12.04% | 11.97% |
| 2025-06 | 2,831 | 824.32 | 14.16% | 14.06% |
| 2025-07 | 1,394 | 761.94 | 22.45% | 22.45% |
| 2025-08 | 2,844 | 955.23 | 10.72% | 10.65% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 491 |
| 2 | 2025-06-12 | 401 |
| 3 | 2025-05-18 | 365 |
| 4 | 2025-07-05 | 313 |
| 5 | 2025-08-11 | 305 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 491건 (2025-05-17)
- 평균 일별 이상치: 375.0건


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
| 분석 레코드 | 7,111 |
| 평균 | 891.2300 |
| 중앙값 | 979.8107 |
| IQR | 95.5498 |
| Bowley 왜도 | 0.6164 |
| Adj 이상치 수 | 856 |
| Adj 이상치율 | 12.04% |
| Std 이상치율 | 12.01% |
| 개선율 | -0.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 491건
- 2. 2025-05-18: 365건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 824.3217 |
| 중앙값 | 952.0734 |
| IQR | 13.1649 |
| Bowley 왜도 | -0.1100 |
| Adj 이상치 수 | 405 |
| Adj 이상치율 | 14.31% |
| Std 이상치율 | 14.31% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 405건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_8_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 761.9402 |
| 중앙값 | 958.5881 |
| IQR | 66.2719 |
| Bowley 왜도 | 0.7175 |
| Adj 이상치 수 | 314 |
| Adj 이상치율 | 22.53% |
| Std 이상치율 | 22.45% |
| 개선율 | -0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 314건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_8_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 955.2329 |
| 중앙값 | 1072.4490 |
| IQR | 44.7508 |
| Bowley 왜도 | -0.7462 |
| Adj 이상치 수 | 311 |
| Adj 이상치율 | 10.94% |
| Std 이상치율 | 10.79% |
| 개선율 | -1.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 311건

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

#### STAND_2_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.19% | **개선율**: -0.6%
**Bowley 왜도**: 0.2277 | **승수 (L/U)**: 0.796/1.256

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,871 | 1,859 |
| 이상치율 | 13.19% | 13.11% |
| 하한 경계 | 451.9675 | 430.4484 |
| 상한 경계 | 739.2710 | 712.2495 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 500.8970 |
| 표준편차 | 194.6529 |
| Q1 (25%) | 536.1238 |
| 중앙값 | 563.3284 |
| Q3 (75%) | 606.5741 |
| IQR | 70.4503 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 516.66 | 11.98% | 11.94% |
| 2025-06 | 2,831 | 486.74 | 14.13% | 13.95% |
| 2025-07 | 1,394 | 500.77 | 22.45% | 22.45% |
| 2025-08 | 2,844 | 475.65 | 10.76% | 10.62% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 487 |
| 2 | 2025-06-12 | 400 |
| 3 | 2025-05-18 | 365 |
| 4 | 2025-07-05 | 313 |
| 5 | 2025-08-11 | 306 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 487건 (2025-05-17)
- 평균 일별 이상치: 374.2건


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
| 분석 레코드 | 7,111 |
| 평균 | 516.6556 |
| 중앙값 | 567.3234 |
| IQR | 45.7571 |
| Bowley 왜도 | 0.7970 |
| Adj 이상치 수 | 857 |
| Adj 이상치율 | 12.05% |
| Std 이상치율 | 12.02% |
| 개선율 | -0.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 492건
- 2. 2025-05-18: 365건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 486.7410 |
| 중앙값 | 561.7921 |
| IQR | 6.0795 |
| Bowley 왜도 | -0.0671 |
| Adj 이상치 수 | 639 |
| Adj 이상치율 | 22.57% |
| Std 이상치율 | 20.63% |
| 개선율 | -9.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 639건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_2_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 500.7739 |
| 중앙값 | 624.5782 |
| IQR | 55.8017 |
| Bowley 왜도 | 0.8394 |
| Adj 이상치 수 | 315 |
| Adj 이상치율 | 22.60% |
| Std 이상치율 | 22.45% |
| 개선율 | -0.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 315건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_2_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 475.6466 |
| 중앙값 | 534.2133 |
| IQR | 22.8528 |
| Bowley 왜도 | -0.7826 |
| Adj 이상치 수 | 407 |
| Adj 이상치율 | 14.31% |
| Std 이상치율 | 10.86% |
| 개선율 | -31.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 407건

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

#### STAND_7_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.18% | **개선율**: -0.1%
**Bowley 왜도**: 0.0911 | **승수 (L/U)**: 0.913/1.095

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,869 | 1,867 |
| 이상치율 | 13.18% | 13.17% |
| 하한 경계 | 975.1039 | 962.4845 |
| 상한 경계 | 1362.7676 | 1348.9445 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 1030.4231 |
| 표준편차 | 400.4501 |
| Q1 (25%) | 1107.4070 |
| 중앙값 | 1151.3135 |
| Q3 (75%) | 1204.0220 |
| IQR | 96.6150 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 1091.92 | 11.97% | 11.97% |
| 2025-06 | 2,831 | 983.86 | 14.06% | 13.99% |
| 2025-07 | 1,394 | 909.10 | 22.45% | 22.45% |
| 2025-08 | 2,844 | 982.48 | 10.79% | 10.79% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 489 |
| 2 | 2025-06-12 | 398 |
| 3 | 2025-05-18 | 362 |
| 4 | 2025-07-05 | 313 |
| 5 | 2025-08-11 | 307 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 489건 (2025-05-17)
- 평균 일별 이상치: 373.8건


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
| 분석 레코드 | 7,111 |
| 평균 | 1091.9194 |
| 중앙값 | 1198.0400 |
| IQR | 124.4000 |
| Bowley 왜도 | 0.6262 |
| Adj 이상치 수 | 856 |
| Adj 이상치율 | 12.04% |
| Std 이상치율 | 12.01% |
| 개선율 | -0.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 491건
- 2. 2025-05-18: 365건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 983.8638 |
| 중앙값 | 1136.4820 |
| IQR | 10.9055 |
| Bowley 왜도 | -0.0252 |
| Adj 이상치 수 | 444 |
| Adj 이상치율 | 15.68% |
| Std 이상치율 | 15.29% |
| 개선율 | -2.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 444건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_7_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 909.0962 |
| 중앙값 | 1144.5555 |
| IQR | 80.9455 |
| Bowley 왜도 | 0.6735 |
| Adj 이상치 수 | 313 |
| Adj 이상치율 | 22.45% |
| Std 이상치율 | 22.45% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 313건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_7_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 982.4761 |
| 중앙값 | 1101.9950 |
| IQR | 45.6045 |
| Bowley 왜도 | -0.6824 |
| Adj 이상치 수 | 311 |
| Adj 이상치율 | 10.94% |
| Std 이상치율 | 10.79% |
| 개선율 | -1.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 311건

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

#### STAND_1_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.17% | **개선율**: -1.0%
**Bowley 왜도**: 0.5209 | **승수 (L/U)**: 0.594/1.684

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,868 | 1,849 |
| 이상치율 | 13.17% | 13.04% |
| 하한 경계 | 425.8168 | 371.8412 |
| 상한 경계 | 817.2259 | 726.3574 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 488.6735 |
| 표준편차 | 192.7084 |
| Q1 (25%) | 504.7848 |
| 중앙값 | 526.0167 |
| Q3 (75%) | 593.4138 |
| IQR | 88.6290 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 535.43 | 11.94% | 11.81% |
| 2025-06 | 2,831 | 438.61 | 14.13% | 13.95% |
| 2025-07 | 1,394 | 417.21 | 22.45% | 22.45% |
| 2025-08 | 2,844 | 456.63 | 10.76% | 10.58% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 487 |
| 2 | 2025-06-12 | 400 |
| 3 | 2025-05-18 | 362 |
| 4 | 2025-07-05 | 313 |
| 5 | 2025-08-11 | 306 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 487건 (2025-05-17)
- 평균 일별 이상치: 373.6건


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
| 분석 레코드 | 7,111 |
| 평균 | 535.4298 |
| 중앙값 | 593.3640 |
| IQR | 38.6129 |
| Bowley 왜도 | 0.6187 |
| Adj 이상치 수 | 857 |
| Adj 이상치율 | 12.05% |
| Std 이상치율 | 12.04% |
| 개선율 | -0.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 492건
- 2. 2025-05-18: 365건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 438.6083 |
| 중앙값 | 504.9693 |
| IQR | 5.7484 |
| Bowley 왜도 | -0.0217 |
| Adj 이상치 수 | 813 |
| Adj 이상치율 | 28.72% |
| Std 이상치율 | 28.72% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 813건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_1_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 417.2099 |
| 중앙값 | 521.8297 |
| IQR | 38.3044 |
| Bowley 왜도 | 0.8340 |
| Adj 이상치 수 | 315 |
| Adj 이상치율 | 22.60% |
| Std 이상치율 | 22.53% |
| 개선율 | -0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 315건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_1_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 456.6307 |
| 중앙값 | 512.3435 |
| IQR | 23.9032 |
| Bowley 왜도 | -0.7566 |
| Adj 이상치 수 | 501 |
| Adj 이상치율 | 17.62% |
| Std 이상치율 | 10.86% |
| 개선율 | -62.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 501건

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

#### PINCHROLL_2_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.10% | **개선율**: 7.6%
**Bowley 왜도**: -0.1238 | **승수 (L/U)**: 1.132/0.884

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,580 | 1,710 |
| 이상치율 | 13.10% | 14.18% |
| 하한 경계 | -325.5835 | -324.4472 |
| 상한 경계 | -302.4608 | -301.4568 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | -314.9369 |
| 표준편차 | 11.4541 |
| Q1 (25%) | -315.8258 |
| 중앙값 | -312.5962 |
| Q3 (75%) | -310.0782 |
| IQR | 5.7476 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | -314.04 | 11.40% | 12.62% |
| 2025-06 | 2,348 | -318.83 | 16.52% | 17.21% |
| 2025-07 | 1,054 | -313.67 | 17.65% | 18.31% |
| 2025-08 | 2,501 | -314.03 | 12.16% | 13.43% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 388 |
| 2 | 2025-05-18 | 354 |
| 3 | 2025-05-17 | 348 |
| 4 | 2025-08-11 | 304 |
| 5 | 2025-07-05 | 186 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 388건 (2025-06-12)
- 평균 일별 이상치: 316.0건


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
| 분석 레코드 | 6,158 |
| 평균 | -314.0363 |
| 중앙값 | -312.3583 |
| IQR | 2.6394 |
| Bowley 왜도 | 0.2193 |
| Adj 이상치 수 | 956 |
| Adj 이상치율 | 15.52% |
| Std 이상치율 | 17.41% |
| 개선율 | 10.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 489건
- 2. 2025-05-17: 467건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | -318.8309 |
| 중앙값 | -316.1615 |
| IQR | 2.2996 |
| Bowley 왜도 | -0.3797 |
| Adj 이상치 수 | 430 |
| Adj 이상치율 | 18.31% |
| Std 이상치율 | 19.21% |
| 개선율 | 4.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 430건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | -313.6661 |
| 중앙값 | -310.0933 |
| IQR | 6.4444 |
| Bowley 왜도 | -0.9143 |
| Adj 이상치 수 | 223 |
| Adj 이상치율 | 21.16% |
| Std 이상치율 | 17.55% |
| 개선율 | -20.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 223건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | -314.0342 |
| 중앙값 | -310.2076 |
| IQR | 3.2241 |
| Bowley 왜도 | -0.5840 |
| Adj 이상치 수 | 541 |
| Adj 이상치율 | 21.63% |
| Std 이상치율 | 15.87% |
| 개선율 | -36.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 541건

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

#### STAND_3_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 13.08% | **개선율**: 0.6%
**Bowley 왜도**: -0.2456 | **승수 (L/U)**: 1.278/0.782

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,855 | 1,867 |
| 이상치율 | 13.08% | 13.17% |
| 하한 경계 | 573.5026 | 605.1584 |
| 상한 경계 | 883.5728 | 908.3341 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 674.4161 |
| 표준편차 | 260.8944 |
| Q1 (25%) | 718.8493 |
| 중앙값 | 766.0552 |
| Q3 (75%) | 794.6432 |
| IQR | 75.7939 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 697.05 | 11.94% | 12.00% |
| 2025-06 | 2,831 | 678.19 | 13.88% | 13.99% |
| 2025-07 | 1,394 | 626.37 | 22.45% | 22.45% |
| 2025-08 | 2,844 | 637.62 | 10.55% | 10.72% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 487 |
| 2 | 2025-06-12 | 393 |
| 3 | 2025-05-18 | 362 |
| 4 | 2025-07-05 | 313 |
| 5 | 2025-08-11 | 300 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 487건 (2025-05-17)
- 평균 일별 이상치: 371.0건


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
| 분석 레코드 | 7,111 |
| 평균 | 697.0506 |
| 중앙값 | 766.3763 |
| IQR | 64.1789 |
| Bowley 왜도 | 0.7212 |
| Adj 이상치 수 | 856 |
| Adj 이상치율 | 12.04% |
| Std 이상치율 | 12.04% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 491건
- 2. 2025-05-18: 365건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 678.1862 |
| 중앙값 | 782.6198 |
| IQR | 9.9984 |
| Bowley 왜도 | -0.0250 |
| Adj 이상치 수 | 434 |
| Adj 이상치율 | 15.33% |
| Std 이상치율 | 15.26% |
| 개선율 | -0.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 434건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted/STAND_3_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 626.3674 |
| 중앙값 | 779.0525 |
| IQR | 74.9403 |
| Bowley 왜도 | 0.8595 |
| Adj 이상치 수 | 315 |
| Adj 이상치율 | 22.60% |
| Std 이상치율 | 22.45% |
| 개선율 | -0.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 315건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted/STAND_3_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 637.6200 |
| 중앙값 | 714.5867 |
| IQR | 32.7050 |
| Bowley 왜도 | -0.6775 |
| Adj 이상치 수 | 350 |
| Adj 이상치율 | 12.31% |
| Std 이상치율 | 10.79% |
| 개선율 | -14.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 350건

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

#### PINCHROLL_4_REFERENCE_TORQUE 🟠

**위험도**: [WARNING] | **이상치율**: 11.16% | **개선율**: 15.6%
**Bowley 왜도**: 0.4931 | **승수 (L/U)**: 0.611/1.637

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,346 | 1,594 |
| 이상치율 | 11.16% | 13.22% |
| 하한 경계 | 6.9272 | -4.5925 |
| 상한 경계 | 93.1833 | 74.3208 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 40.7285 |
| 표준편차 | 23.6889 |
| Q1 (25%) | 25.0000 |
| 중앙값 | 30.0000 |
| Q3 (75%) | 44.7283 |
| IQR | 19.7283 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 40.98 | 9.43% | 11.35% |
| 2025-06 | 2,348 | 43.22 | 13.80% | 17.12% |
| 2025-07 | 1,054 | 43.92 | 16.51% | 18.60% |
| 2025-08 | 2,501 | 36.42 | 10.68% | 11.88% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 324 |
| 2 | 2025-05-18 | 301 |
| 3 | 2025-05-17 | 280 |
| 4 | 2025-08-11 | 267 |
| 5 | 2025-07-05 | 174 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 324건 (2025-06-12)
- 평균 일별 이상치: 269.2건


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
| 분석 레코드 | 6,158 |
| 평균 | 40.9825 |
| 중앙값 | 35.0000 |
| IQR | 20.0775 |
| Bowley 왜도 | 0.0039 |
| Adj 이상치 수 | 697 |
| Adj 이상치율 | 11.32% |
| Std 이상치율 | 11.32% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 359건
- 2. 2025-05-17: 338건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 43.2198 |
| 중앙값 | 30.0000 |
| IQR | 1.4567 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 538 |
| Adj 이상치율 | 22.91% |
| Std 이상치율 | 23.42% |
| 개선율 | 2.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 538건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 43.9186 |
| 중앙값 | 35.0000 |
| IQR | 22.2735 |
| Bowley 왜도 | 0.1021 |
| Adj 이상치 수 | 188 |
| Adj 이상치율 | 17.84% |
| Std 이상치율 | 18.22% |
| 개선율 | 2.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 188건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 36.4201 |
| 중앙값 | 25.0000 |
| IQR | 11.2075 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 281 |
| Adj 이상치율 | 11.24% |
| Std 이상치율 | 13.63% |
| 개선율 | 17.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 281건

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


### 🟡 주의 (5~10%) - 2개 태그

#### FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE 🟡

**위험도**: [CAUTION] | **이상치율**: 6.69% | **개선율**: -0.3%
**Bowley 왜도**: 0.2721 | **승수 (L/U)**: 0.762/1.313

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 963 | 960 |
| 이상치율 | 6.69% | 6.67% |
| 하한 경계 | 715.2507 | 646.8003 |
| 상한 경계 | 1502.9314 | 1413.0766 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 966.9769 |
| 표준편차 | 278.1561 |
| Q1 (25%) | 934.1539 |
| 중앙값 | 1003.8770 |
| Q3 (75%) | 1125.7230 |
| IQR | 191.5691 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 887.08 | 7.13% | 7.09% |
| 2025-06 | 2,878 | 1083.20 | 5.98% | 5.98% |
| 2025-07 | 1,440 | 1057.07 | 5.00% | 5.00% |
| 2025-08 | 2,876 | 1005.32 | 7.16% | 7.16% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-18 | 339 |
| 2 | 2025-08-11 | 206 |
| 3 | 2025-05-17 | 174 |
| 4 | 2025-06-12 | 172 |
| 5 | 2025-07-05 | 72 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 339건 (2025-05-18)
- 평균 일별 이상치: 192.6건


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
| 분석 레코드 | 7,190 |
| 평균 | 887.0756 |
| 중앙값 | 946.3384 |
| IQR | 77.1691 |
| Bowley 왜도 | 0.2105 |
| Adj 이상치 수 | 561 |
| Adj 이상치율 | 7.80% |
| Std 이상치율 | 7.55% |
| 개선율 | -3.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 387건
- 2. 2025-05-17: 174건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1083.2035 |
| 중앙값 | 1164.9850 |
| IQR | 63.6310 |
| Bowley 왜도 | -0.5319 |
| Adj 이상치 수 | 224 |
| Adj 이상치율 | 7.78% |
| Std 이상치율 | 7.85% |
| 개선율 | 0.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 224건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1057.0657 |
| 중앙값 | 1134.5230 |
| IQR | 82.0773 |
| Bowley 왜도 | -0.5670 |
| Adj 이상치 수 | 73 |
| Adj 이상치율 | 5.07% |
| Std 이상치율 | 5.90% |
| 개선율 | 14.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 73건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1005.3155 |
| 중앙값 | 1086.4620 |
| IQR | 82.5840 |
| Bowley 왜도 | -0.0656 |
| Adj 이상치 수 | 206 |
| Adj 이상치율 | 7.16% |
| Std 이상치율 | 7.16% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 206건

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

#### [L1] PR6L1_ACT_TORQUE 🟡

**위험도**: [CAUTION] | **이상치율**: 5.52% | **개선율**: -16.0%
**Bowley 왜도**: -0.8761 | **승수 (L/U)**: 2.402/0.416

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 666 | 574 |
| 이상치율 | 5.52% | 4.76% |
| 하한 경계 | -15.4997 | -6.4540 |
| 상한 경계 | 6.9901 | 10.7567 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 3.6270 |
| 표준편차 | 3.8670 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.0362 |
| Q3 (75%) | 4.3027 |
| IQR | 4.3027 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 2.42 | 0.02% | 0.00% |
| 2025-06 | 2,348 | 7.47 | 25.94% | 22.23% |
| 2025-07 | 1,054 | 3.42 | 0.00% | 0.00% |
| 2025-08 | 2,501 | 3.09 | 2.24% | 2.08% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 609 |
| 2 | 2025-08-11 | 56 |
| 3 | 2025-05-17 | 1 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 609건 (2025-06-12)
- 평균 일별 이상치: 222.0건


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
| 분석 레코드 | 6,158 |
| 평균 | 2.4154 |
| 중앙값 | 4.1995 |
| IQR | 4.3262 |
| Bowley 왜도 | -0.9414 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.02% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 1건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 7.4689 |
| 중앙값 | 4.2559 |
| IQR | 3.5487 |
| Bowley 왜도 | 0.9150 |
| Adj 이상치 수 | 2 |
| Adj 이상치율 | 0.09% |
| Std 이상치율 | 19.34% |
| 개선율 | 99.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 3.4235 |
| 중앙값 | 3.8900 |
| IQR | 0.7603 |
| Bowley 왜도 | -0.5584 |
| Adj 이상치 수 | 123 |
| Adj 이상치율 | 11.67% |
| Std 이상치율 | 11.39% |
| 개선율 | -2.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 123건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 3.0891 |
| 중앙값 | 3.8057 |
| IQR | 3.8880 |
| Bowley 왜도 | -0.9577 |
| Adj 이상치 수 | 62 |
| Adj 이상치율 | 2.48% |
| Std 이상치율 | 2.08% |
| 개선율 | -19.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 62건

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


### 🟢 양호 (0~5%) - 57개 태그

#### MAIN_GAS_PRESSURE 🟢

**위험도**: [NORMAL] | **이상치율**: 3.87% | **개선율**: 8.1%
**Bowley 왜도**: -0.1716 | **승수 (L/U)**: 1.187/0.842

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 556 | 605 |
| 이상치율 | 3.87% | 4.21% |
| 하한 경계 | 1526.5876 | 1531.7294 |
| 상한 경계 | 1600.6631 | 1604.9944 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 1568.7718 |
| 표준편차 | 18.5181 |
| Q1 (25%) | 1559.2037 |
| 중앙값 | 1569.9330 |
| Q3 (75%) | 1577.5200 |
| IQR | 18.3163 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1573.27 | 3.62% | 3.39% |
| 2025-06 | 2,878 | 1568.37 | 1.11% | 0.97% |
| 2025-07 | 1,440 | 1552.35 | 13.75% | 18.82% |
| 2025-08 | 2,876 | 1566.15 | 2.29% | 2.16% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-18 | 210 |
| 2 | 2025-07-05 | 198 |
| 3 | 2025-08-11 | 66 |
| 4 | 2025-05-17 | 50 |
| 5 | 2025-06-12 | 32 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 210건 (2025-05-18)
- 평균 일별 이상치: 111.2건


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
| 분석 레코드 | 7,190 |
| 평균 | 1573.2700 |
| 중앙값 | 1572.3810 |
| IQR | 16.7850 |
| Bowley 왜도 | 0.0253 |
| Adj 이상치 수 | 353 |
| Adj 이상치율 | 4.91% |
| Std 이상치율 | 4.81% |
| 개선율 | -2.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 213건
- 2. 2025-05-17: 140건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1568.3681 |
| 중앙값 | 1570.0330 |
| IQR | 18.3895 |
| Bowley 왜도 | -0.1589 |
| Adj 이상치 수 | 28 |
| Adj 이상치율 | 0.97% |
| Std 이상치율 | 0.83% |
| 개선율 | -16.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 28건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_PRESSURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1552.3523 |
| 중앙값 | 1552.3155 |
| IQR | 23.5798 |
| Bowley 왜도 | -0.2233 |
| Adj 이상치 수 | 84 |
| Adj 이상치율 | 5.83% |
| Std 이상치율 | 5.21% |
| 개선율 | -12.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 84건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1566.1515 |
| 중앙값 | 1568.7360 |
| IQR | 11.0370 |
| Bowley 왜도 | -0.3025 |
| Adj 이상치 수 | 200 |
| Adj 이상치율 | 6.95% |
| Std 이상치율 | 11.27% |
| 개선율 | 38.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 200건

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

#### MAIN_COMBUSTION_AIR_PRESSURE 🟢

**위험도**: [NORMAL] | **이상치율**: 3.57% | **개선율**: 3.9%
**Bowley 왜도**: 0.0853 | **승수 (L/U)**: 0.918/1.089

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 513 | 534 |
| 이상치율 | 3.57% | 3.71% |
| 하한 경계 | 1151.2270 | 1150.9261 |
| 상한 경계 | 1161.0668 | 1160.7391 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 1155.7673 |
| 표준편차 | 2.7875 |
| Q1 (25%) | 1154.6060 |
| 중앙값 | 1155.7280 |
| Q3 (75%) | 1157.0593 |
| IQR | 2.4533 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1155.94 | 2.24% | 2.24% |
| 2025-06 | 2,878 | 1155.91 | 5.42% | 5.91% |
| 2025-07 | 1,440 | 1154.59 | 8.75% | 9.10% |
| 2025-08 | 2,876 | 1155.79 | 2.43% | 2.50% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 156 |
| 2 | 2025-07-05 | 126 |
| 3 | 2025-05-17 | 86 |
| 4 | 2025-05-18 | 75 |
| 5 | 2025-08-11 | 70 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 156건 (2025-06-12)
- 평균 일별 이상치: 102.6건


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
| 분석 레코드 | 7,190 |
| 평균 | 1155.9388 |
| 중앙값 | 1155.7770 |
| IQR | 2.2480 |
| Bowley 왜도 | 0.0872 |
| Adj 이상치 수 | 211 |
| Adj 이상치율 | 2.93% |
| Std 이상치율 | 3.03% |
| 개선율 | 3.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 118건
- 2. 2025-05-18: 93건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1155.9060 |
| 중앙값 | 1155.6120 |
| IQR | 3.0757 |
| Bowley 왜도 | 0.1809 |
| Adj 이상치 수 | 100 |
| Adj 이상치율 | 3.47% |
| Std 이상치율 | 3.82% |
| 개선율 | 9.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 100건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1154.5894 |
| 중앙값 | 1155.5295 |
| IQR | 2.9108 |
| Bowley 왜도 | 0.0990 |
| Adj 이상치 수 | 117 |
| Adj 이상치율 | 8.12% |
| Std 이상치율 | 7.85% |
| 개선율 | -3.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 117건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1155.7895 |
| 중앙값 | 1155.7190 |
| IQR | 2.2610 |
| Bowley 왜도 | 0.0447 |
| Adj 이상치 수 | 104 |
| Adj 이상치율 | 3.62% |
| Std 이상치율 | 3.62% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 104건

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

#### PINCHROLL_2_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 2.14% | **개선율**: 86.7%
**Bowley 왜도**: -0.9998 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 258 | 1,937 |
| 이상치율 | 2.14% | 16.06% |
| 하한 경계 | 1.9857 | 11.1261 |
| 상한 경계 | 21.9531 | 25.3164 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 16.6351 |
| 표준편차 | 6.0841 |
| Q1 (25%) | 16.4474 |
| 중앙값 | 19.9946 |
| Q3 (75%) | 19.9950 |
| IQR | 3.5476 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 16.86 | 0.08% | 13.41% |
| 2025-06 | 2,348 | 16.22 | 0.00% | 21.55% |
| 2025-07 | 1,054 | 15.58 | 8.06% | 23.91% |
| 2025-08 | 2,501 | 16.93 | 6.72% | 14.11% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-11 | 168 |
| 2 | 2025-07-05 | 85 |
| 3 | 2025-05-17 | 5 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 168건 (2025-08-11)
- 평균 일별 이상치: 86.0건


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
| 분석 레코드 | 6,158 |
| 평균 | 16.8559 |
| 중앙값 | 19.9945 |
| IQR | 3.5308 |
| Bowley 왜도 | -0.9997 |
| Adj 이상치 수 | 10 |
| Adj 이상치율 | 0.16% |
| Std 이상치율 | 13.41% |
| 개선율 | 98.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 10건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 16.2201 |
| 중앙값 | 19.9948 |
| IQR | 2.3525 |
| Bowley 왜도 | -0.9997 |
| Adj 이상치 수 | 458 |
| Adj 이상치율 | 19.51% |
| Std 이상치율 | 23.17% |
| 개선율 | 15.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 458건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 15.5801 |
| 중앙값 | 19.9947 |
| IQR | 7.1950 |
| Bowley 왜도 | -0.9999 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 9.49% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 16.9259 |
| 중앙값 | 19.9947 |
| IQR | 3.7048 |
| Bowley 왜도 | -0.9998 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 14.11% |
| 개선율 | 100.0% |

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

#### FURNACE_PRESSURE 🟢

**위험도**: [NORMAL] | **이상치율**: 1.19% | **개선율**: -81.9%
**Bowley 왜도**: -0.1422 | **승수 (L/U)**: 1.153/0.867

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 171 | 94 |
| 이상치율 | 1.19% | 0.65% |
| 하한 경계 | 0.4160 | 0.4218 |
| 상한 경계 | 0.5167 | 0.5216 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 0.4726 |
| 표준편차 | 0.0186 |
| Q1 (25%) | 0.4592 |
| 중앙값 | 0.4735 |
| Q3 (75%) | 0.4842 |
| IQR | 0.0250 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 0.47 | 0.13% | 0.00% |
| 2025-06 | 2,878 | 0.48 | 3.61% | 2.15% |
| 2025-07 | 1,440 | 0.47 | 3.19% | 2.08% |
| 2025-08 | 2,876 | 0.47 | 0.42% | 0.07% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 104 |
| 2 | 2025-07-05 | 46 |
| 3 | 2025-08-11 | 12 |
| 4 | 2025-05-18 | 9 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 104건 (2025-06-12)
- 평균 일별 이상치: 42.8건


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
| 분석 레코드 | 7,190 |
| 평균 | 0.4694 |
| 중앙값 | 0.4714 |
| IQR | 0.0196 |
| Bowley 왜도 | -0.2270 |
| Adj 이상치 수 | 49 |
| Adj 이상치율 | 0.68% |
| Std 이상치율 | 0.53% |
| 개선율 | -28.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 45건
- 2. 2025-05-17: 4건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 0.4782 |
| 중앙값 | 0.4812 |
| IQR | 0.0367 |
| Bowley 왜도 | -0.2585 |
| Adj 이상치 수 | 20 |
| Adj 이상치율 | 0.69% |
| Std 이상치율 | 0.49% |
| 개선율 | -42.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 20건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/FURNACE_PRESSURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 0.4722 |
| 중앙값 | 0.4731 |
| IQR | 0.0389 |
| Bowley 왜도 | -0.1459 |
| Adj 이상치 수 | 8 |
| Adj 이상치율 | 0.56% |
| Std 이상치율 | 0.21% |
| 개선율 | -166.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 8건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/FURNACE_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 0.4750 |
| 중앙값 | 0.4770 |
| IQR | 0.0223 |
| Bowley 왜도 | -0.0965 |
| Adj 이상치 수 | 10 |
| Adj 이상치율 | 0.35% |
| Std 이상치율 | 0.07% |
| 개선율 | -400.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 10건

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

#### [L2] PR7L2_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 1.11% | **개선율**: -30.1%
**Bowley 왜도**: -0.9597 | **승수 (L/U)**: 2.611/0.383

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 134 | 103 |
| 이상치율 | 1.11% | 0.85% |
| 하한 경계 | -23.9608 | -9.1769 |
| 상한 경계 | 9.6326 | 15.2948 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 4.4153 |
| 표준편차 | 3.3408 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 5.9947 |
| Q3 (75%) | 6.1179 |
| IQR | 6.1179 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 3.40 | 0.02% | 0.00% |
| 2025-06 | 2,348 | 6.15 | 0.13% | 0.00% |
| 2025-07 | 1,054 | 6.90 | 12.14% | 9.77% |
| 2025-08 | 2,501 | 4.24 | 0.08% | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-05 | 128 |
| 2 | 2025-06-12 | 3 |
| 3 | 2025-08-11 | 2 |
| 4 | 2025-05-17 | 1 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 128건 (2025-07-05)
- 평균 일별 이상치: 33.5건


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
| 분석 레코드 | 6,158 |
| 평균 | 3.4011 |
| 중앙값 | 6.0109 |
| IQR | 6.1240 |
| Bowley 왜도 | -0.9631 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.02% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 1건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 6.1478 |
| 중앙값 | 6.0547 |
| IQR | 0.3048 |
| Bowley 왜도 | 0.5407 |
| Adj 이상치 수 | 21 |
| Adj 이상치율 | 0.89% |
| Std 이상치율 | 2.43% |
| 개선율 | 63.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 21건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L2_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 6.9014 |
| 중앙값 | 5.8103 |
| IQR | 0.3265 |
| Bowley 왜도 | 0.0792 |
| Adj 이상치 수 | 398 |
| Adj 이상치율 | 37.76% |
| Std 이상치율 | 38.33% |
| 개선율 | 1.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 398건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L2_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 4.2383 |
| 중앙값 | 5.8791 |
| IQR | 6.0387 |
| Bowley 왜도 | -0.9471 |
| Adj 이상치 수 | 2 |
| Adj 이상치율 | 0.08% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 2건

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

#### [L1] PR7L1_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 1.03% | **개선율**: -11.7%
**Bowley 왜도**: -0.7992 | **승수 (L/U)**: 2.224/0.450

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 124 | 111 |
| 이상치율 | 1.03% | 0.92% |
| 하한 경계 | -16.5907 | -7.4609 |
| 상한 경계 | 8.3291 | 12.4348 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 3.4839 |
| 표준편차 | 2.8880 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.4745 |
| Q3 (75%) | 4.9739 |
| IQR | 4.9739 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 2.53 | 0.00% | 0.00% |
| 2025-06 | 2,348 | 4.60 | 0.00% | 0.00% |
| 2025-07 | 1,054 | 6.24 | 11.76% | 10.53% |
| 2025-08 | 2,501 | 3.63 | 0.00% | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-05 | 124 |

- 이상치 발생 일수: 1일
- 최대 일별 이상치: 124건 (2025-07-05)
- 평균 일별 이상치: 124.0건


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
| 분석 레코드 | 6,158 |
| 평균 | 2.5261 |
| 중앙값 | 4.4123 |
| IQR | 4.5496 |
| Bowley 왜도 | -0.9396 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.02% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 1건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 4.5985 |
| 중앙값 | 4.4650 |
| IQR | 0.2700 |
| Bowley 왜도 | 0.4165 |
| Adj 이상치 수 | 147 |
| Adj 이상치율 | 6.26% |
| Std 이상치율 | 13.33% |
| 개선율 | 53.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 147건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR7L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 6.2423 |
| 중앙값 | 4.9401 |
| IQR | 0.2534 |
| Bowley 왜도 | 0.4070 |
| Adj 이상치 수 | 397 |
| Adj 이상치율 | 37.67% |
| Std 이상치율 | 40.70% |
| 개선율 | 7.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 397건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR7L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 3.6334 |
| 중앙값 | 5.0734 |
| IQR | 5.1245 |
| Bowley 왜도 | -0.9800 |
| Adj 이상치 수 | 2 |
| Adj 이상치율 | 0.08% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 2건

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

#### [L1] PR8L1_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.56% | **개선율**: 0.0%
**Bowley 왜도**: 0.0202 | **승수 (L/U)**: 0.980/1.020

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 67 | 67 |
| 이상치율 | 0.56% | 0.56% |
| 하한 경계 | -14.3737 | -14.6671 |
| 상한 경계 | 24.7445 | 24.4451 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 5.9659 |
| 표준편차 | 5.6167 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.7903 |
| Q3 (75%) | 9.7781 |
| IQR | 9.7781 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 4.62 | 0.00% | 0.00% |
| 2025-06 | 2,348 | 8.35 | 0.00% | 0.00% |
| 2025-07 | 1,054 | 8.15 | 6.36% | 6.36% |
| 2025-08 | 2,501 | 6.11 | 0.00% | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-05 | 67 |

- 이상치 발생 일수: 1일
- 최대 일별 이상치: 67건 (2025-07-05)
- 평균 일별 이상치: 67.0건


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
| 분석 레코드 | 6,158 |
| 평균 | 4.6241 |
| 중앙값 | 4.4517 |
| IQR | 6.7529 |
| Bowley 왜도 | -0.3184 |
| Adj 이상치 수 | 962 |
| Adj 이상치율 | 15.62% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 640건
- 2. 2025-05-18: 322건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 8.3528 |
| 중앙값 | 5.4876 |
| IQR | 10.1692 |
| Bowley 왜도 | 0.8683 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.04% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted/PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted/PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR8L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 8.1542 |
| 중앙값 | 5.2182 |
| IQR | 9.8094 |
| Bowley 왜도 | 0.7861 |
| Adj 이상치 수 | 4 |
| Adj 이상치율 | 0.38% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 4건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted/PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted/PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR8L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 6.1066 |
| 중앙값 | 5.2226 |
| IQR | 10.4072 |
| Bowley 왜도 | -0.0037 |
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

#### [L2] PR6L2_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.51% | **개선율**: -13.0%
**Bowley 왜도**: -0.9118 | **승수 (L/U)**: 2.489/0.402

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 61 | 54 |
| 이상치율 | 0.51% | 0.45% |
| 하한 경계 | -21.5619 | -8.6632 |
| 상한 경계 | 9.2562 | 14.4387 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 4.0091 |
| 표준편차 | 2.8036 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 5.5209 |
| Q3 (75%) | 5.7755 |
| IQR | 5.7755 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 3.22 | 0.02% | 0.00% |
| 2025-06 | 2,348 | 5.76 | 0.13% | 0.00% |
| 2025-07 | 1,054 | 4.48 | 0.09% | 0.00% |
| 2025-08 | 2,501 | 4.11 | 2.24% | 2.16% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-11 | 56 |
| 2 | 2025-06-12 | 3 |
| 3 | 2025-05-17 | 1 |
| 4 | 2025-07-05 | 1 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 56건 (2025-08-11)
- 평균 일별 이상치: 15.2건


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
| 분석 레코드 | 6,158 |
| 평균 | 3.2228 |
| 중앙값 | 5.6747 |
| IQR | 5.7988 |
| Bowley 왜도 | -0.9572 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.02% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 1건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 5.7561 |
| 중앙값 | 5.6749 |
| IQR | 0.2558 |
| Bowley 왜도 | 0.5082 |
| Adj 이상치 수 | 33 |
| Adj 이상치율 | 1.41% |
| Std 이상치율 | 7.62% |
| 개선율 | 81.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 33건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR6L2_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 4.4826 |
| 중앙값 | 5.2778 |
| IQR | 1.2726 |
| Bowley 왜도 | -0.8738 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.09% |
| Std 이상치율 | 11.57% |
| 개선율 | 99.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR6L2_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 4.1058 |
| 중앙값 | 5.2842 |
| IQR | 5.3997 |
| Bowley 왜도 | -0.9572 |
| Adj 이상치 수 | 58 |
| Adj 이상치율 | 2.32% |
| Std 이상치율 | 2.16% |
| 개선율 | -7.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 58건

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

#### HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 0.47% | **개선율**: -88.9%
**Bowley 왜도**: -0.5685 | **승수 (L/U)**: 1.766/0.566

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 68 | 36 |
| 이상치율 | 0.47% | 0.25% |
| 하한 경계 | 862.8720 | 926.5040 |
| 상한 경계 | 1112.1114 | 1148.1520 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 1042.6115 |
| 표준편차 | 31.7274 |
| Q1 (25%) | 1009.6220 |
| 중앙값 | 1053.0780 |
| Q3 (75%) | 1065.0340 |
| IQR | 55.4120 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1038.10 | 0.36% | 0.50% |
| 2025-06 | 2,878 | 1059.89 | 0.83% | 0.00% |
| 2025-07 | 1,440 | 1044.61 | 1.25% | 0.00% |
| 2025-08 | 2,876 | 1035.60 | 0.00% | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 26 |
| 2 | 2025-06-12 | 24 |
| 3 | 2025-07-05 | 18 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 26건 (2025-05-17)
- 평균 일별 이상치: 22.7건


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
| 분석 레코드 | 7,190 |
| 평균 | 1038.0964 |
| 중앙값 | 1052.9590 |
| IQR | 64.8505 |
| Bowley 왜도 | -0.5577 |
| Adj 이상치 수 | 6 |
| Adj 이상치율 | 0.08% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 6건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1059.8944 |
| 중앙값 | 1058.4040 |
| IQR | 19.0722 |
| Bowley 왜도 | 0.2289 |
| Adj 이상치 수 | 218 |
| Adj 이상치율 | 7.57% |
| Std 이상치율 | 7.57% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 218건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1044.6116 |
| 중앙값 | 1048.7420 |
| IQR | 20.6702 |
| Bowley 왜도 | -0.2073 |
| Adj 이상치 수 | 229 |
| Adj 이상치율 | 15.90% |
| Std 이상치율 | 15.69% |
| 개선율 | -1.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 229건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1035.6030 |
| 중앙값 | 1048.1810 |
| IQR | 55.8760 |
| Bowley 왜도 | -0.5891 |
| Adj 이상치 수 | 14 |
| Adj 이상치율 | 0.49% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 14건

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

#### HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 0.41% | **개선율**: -78.8%
**Bowley 왜도**: -0.5689 | **승수 (L/U)**: 1.766/0.566

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 59 | 33 |
| 이상치율 | 0.41% | 0.23% |
| 하한 경계 | 856.1527 | 921.4324 |
| 상한 경계 | 1111.6410 | 1148.5994 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 1040.3217 |
| 표준편차 | 32.3615 |
| Q1 (25%) | 1006.6200 |
| 중앙값 | 1051.1700 |
| Q3 (75%) | 1063.4118 |
| IQR | 56.7918 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1035.99 | 0.31% | 0.46% |
| 2025-06 | 2,878 | 1057.95 | 0.69% | 0.00% |
| 2025-07 | 1,440 | 1042.08 | 1.18% | 0.00% |
| 2025-08 | 2,876 | 1032.63 | 0.00% | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 22 |
| 2 | 2025-06-12 | 20 |
| 3 | 2025-07-05 | 17 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 22건 (2025-05-17)
- 평균 일별 이상치: 19.7건


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
| 분석 레코드 | 7,190 |
| 평균 | 1035.9886 |
| 중앙값 | 1051.3980 |
| IQR | 67.4598 |
| Bowley 왜도 | -0.5631 |
| Adj 이상치 수 | 2 |
| Adj 이상치율 | 0.03% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 2건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1057.9520 |
| 중앙값 | 1055.6120 |
| IQR | 19.1230 |
| Bowley 왜도 | 0.3484 |
| Adj 이상치 수 | 208 |
| Adj 이상치율 | 7.23% |
| Std 이상치율 | 7.51% |
| 개선율 | 3.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 208건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1042.0834 |
| 중앙값 | 1045.5485 |
| IQR | 19.9815 |
| Bowley 왜도 | -0.1278 |
| Adj 이상치 수 | 242 |
| Adj 이상치율 | 16.81% |
| Std 이상치율 | 16.32% |
| 개선율 | -3.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 242건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1032.6297 |
| 중앙값 | 1045.8355 |
| IQR | 58.6310 |
| Bowley 왜도 | -0.6188 |
| Adj 이상치 수 | 6 |
| Adj 이상치율 | 0.21% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 6건

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

#### [L1] PR9L1_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.37% | **개선율**: 50.5%
**Bowley 왜도**: -0.4626 | **승수 (L/U)**: 1.588/0.630

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 45 | 91 |
| 이상치율 | 0.37% | 0.75% |
| 하한 경계 | -33.9627 | -24.3387 |
| 상한 경계 | 13.2331 | 19.2927 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | -2.2148 |
| 표준편차 | 5.9660 |
| Q1 (25%) | -7.9769 |
| 중앙값 | 0.0000 |
| Q3 (75%) | 2.9309 |
| IQR | 10.9079 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | -1.67 | 0.00% | 0.00% |
| 2025-06 | 2,348 | -2.72 | 0.00% | 0.00% |
| 2025-07 | 1,054 | -4.75 | 4.27% | 8.63% |
| 2025-08 | 2,501 | -2.01 | 0.00% | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-05 | 45 |

- 이상치 발생 일수: 1일
- 최대 일별 이상치: 45건 (2025-07-05)
- 평균 일별 이상치: 45.0건


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
| 분석 레코드 | 6,158 |
| 평균 | -1.6698 |
| 중앙값 | 0.0000 |
| IQR | 5.8223 |
| Bowley 왜도 | -0.3454 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 1.19% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | -2.7224 |
| 중앙값 | 0.3351 |
| IQR | 12.9693 |
| Bowley 왜도 | -0.6024 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted/PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted/PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted/PR9L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | -4.7475 |
| 중앙값 | 0.0000 |
| IQR | 13.1426 |
| Bowley 왜도 | -0.5310 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 7.69% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted/PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted/PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted/PR9L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | -2.0130 |
| 중앙값 | 0.0000 |
| IQR | 10.8919 |
| Bowley 왜도 | -0.4279 |
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

#### COMBUSTION_AIR_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.28% | **개선율**: 11.1%
**Bowley 왜도**: 0.0733 | **승수 (L/U)**: 0.929/1.076

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 40 | 45 |
| 이상치율 | 0.28% | 0.31% |
| 하한 경계 | 24.9121 | 24.1080 |
| 상한 경계 | 55.3276 | 54.4623 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 39.3362 |
| 표준편차 | 4.7235 |
| Q1 (25%) | 35.4909 |
| 중앙값 | 39.0072 |
| Q3 (75%) | 43.0795 |
| IQR | 7.5886 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 35.72 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 41.29 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 46.28 | 2.78% | 3.12% |
| 2025-08 | 2,876 | 42.95 | 0.00% | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-05 | 40 |

- 이상치 발생 일수: 1일
- 최대 일별 이상치: 40건 (2025-07-05)
- 평균 일별 이상치: 40.0건


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
| 분석 레코드 | 7,190 |
| 평균 | 35.7201 |
| 중앙값 | 35.4886 |
| IQR | 4.2980 |
| Bowley 왜도 | 0.0673 |
| Adj 이상치 수 | 56 |
| Adj 이상치율 | 0.78% |
| Std 이상치율 | 0.83% |
| 개선율 | 6.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 56건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 41.2859 |
| 중앙값 | 40.8278 |
| IQR | 5.9229 |
| Bowley 왜도 | 0.2110 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/COMBUSTION_AIR_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 46.2791 |
| 중앙값 | 46.6372 |
| IQR | 3.8744 |
| Bowley 왜도 | -0.4972 |
| Adj 이상치 수 | 102 |
| Adj 이상치율 | 7.08% |
| Std 이상치율 | 3.82% |
| 개선율 | -85.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 102건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/COMBUSTION_AIR_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 42.9492 |
| 중앙값 | 43.0001 |
| IQR | 1.0388 |
| Bowley 왜도 | -0.2107 |
| Adj 이상치 수 | 186 |
| Adj 이상치율 | 6.47% |
| Std 이상치율 | 5.77% |
| 개선율 | -12.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 186건

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

#### HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.06% | **개선율**: 76.3%
**Bowley 왜도**: 0.1124 | **승수 (L/U)**: 0.894/1.119

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 9 | 38 |
| 이상치율 | 0.06% | 0.26% |
| 하한 경계 | 838.9280 | 829.3565 |
| 상한 경계 | 1080.1085 | 1069.3982 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 951.5855 |
| 표준편차 | 42.3227 |
| Q1 (25%) | 919.3722 |
| 중앙값 | 946.0042 |
| Q3 (75%) | 979.3826 |
| IQR | 60.0104 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 946.57 | 0.00% | 0.03% |
| 2025-06 | 2,878 | 975.58 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 961.48 | 0.62% | 2.50% |
| 2025-08 | 2,876 | 935.15 | 0.00% | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-05 | 9 |

- 이상치 발생 일수: 1일
- 최대 일별 이상치: 9건 (2025-07-05)
- 평균 일별 이상치: 9.0건


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
| 분석 레코드 | 7,190 |
| 평균 | 946.5727 |
| 중앙값 | 940.9927 |
| IQR | 77.9735 |
| Bowley 왜도 | -0.0537 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 975.5847 |
| 중앙값 | 968.7046 |
| IQR | 49.0138 |
| Bowley 왜도 | 0.1421 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 961.4786 |
| 중앙값 | 960.7482 |
| IQR | 46.9261 |
| Bowley 왜도 | -0.1687 |
| Adj 이상치 수 | 52 |
| Adj 이상치율 | 3.61% |
| Std 이상치율 | 3.06% |
| 개선율 | -18.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 52건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 935.1483 |
| 중앙값 | 926.5802 |
| IQR | 39.7504 |
| Bowley 왜도 | 0.2414 |
| Adj 이상치 수 | 56 |
| Adj 이상치율 | 1.95% |
| Std 이상치율 | 4.80% |
| 개선율 | 59.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 56건

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

#### SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.5381 | **승수 (L/U)**: 1.713/0.584

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 966.3957 | 1021.5263 |
| 상한 경계 | 1195.5963 | 1227.7842 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 1127.9231 |
| 표준편차 | 28.0442 |
| Q1 (25%) | 1098.8730 |
| 중앙값 | 1138.5290 |
| Q3 (75%) | 1150.4375 |
| IQR | 51.5645 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1126.41 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 1146.50 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 1125.90 | 0.00% | 0.00% |
| 2025-08 | 2,876 | 1114.13 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,190 |
| 평균 | 1126.4076 |
| 중앙값 | 1141.0460 |
| IQR | 56.2865 |
| Bowley 왜도 | -0.5632 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1146.5024 |
| 중앙값 | 1148.2080 |
| IQR | 11.5573 |
| Bowley 왜도 | 0.1832 |
| Adj 이상치 수 | 322 |
| Adj 이상치율 | 11.19% |
| Std 이상치율 | 10.22% |
| 개선율 | -9.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 322건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1125.8977 |
| 중앙값 | 1135.9600 |
| IQR | 30.8340 |
| Bowley 왜도 | -0.5876 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 6.18% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1114.1339 |
| 중앙값 | 1122.4685 |
| IQR | 46.3310 |
| Bowley 왜도 | -0.4213 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

#### SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.5514 | **승수 (L/U)**: 1.736/0.576

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 956.9650 | 1010.6354 |
| 상한 경계 | 1174.2733 | 1205.1964 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 1110.6579 |
| 표준편차 | 27.7134 |
| Q1 (25%) | 1083.5957 |
| 중앙값 | 1121.3250 |
| Q3 (75%) | 1132.2360 |
| IQR | 48.6403 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1108.68 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 1128.46 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 1109.15 | 0.00% | 0.00% |
| 2025-08 | 2,876 | 1098.54 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,190 |
| 평균 | 1108.6839 |
| 중앙값 | 1118.9410 |
| IQR | 51.8145 |
| Bowley 왜도 | -0.4136 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1128.4564 |
| 중앙값 | 1131.6160 |
| IQR | 11.7657 |
| Bowley 왜도 | -0.1039 |
| Adj 이상치 수 | 320 |
| Adj 이상치율 | 11.12% |
| Std 이상치율 | 11.05% |
| 개선율 | -0.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 320건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1109.1531 |
| 중앙값 | 1119.7910 |
| IQR | 33.3710 |
| Bowley 왜도 | -0.6356 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 5.00% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1098.5354 |
| 중앙값 | 1106.9330 |
| IQR | 47.8110 |
| Bowley 왜도 | -0.3853 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

#### HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 100.0%
**Bowley 왜도**: 0.1270 | **승수 (L/U)**: 0.881/1.135

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 14 |
| 이상치율 | 0.00% | 0.10% |
| 하한 경계 | 871.9047 | 861.4425 |
| 상한 경계 | 1107.2391 | 1095.3601 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 977.9039 |
| 표준편차 | 41.9671 |
| Q1 (25%) | 949.1616 |
| 중앙값 | 974.6878 |
| Q3 (75%) | 1007.6410 |
| IQR | 58.4794 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 974.02 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 999.31 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 987.47 | 0.00% | 0.97% |
| 2025-08 | 2,876 | 961.39 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,190 |
| 평균 | 974.0227 |
| 중앙값 | 971.3668 |
| IQR | 88.3119 |
| Bowley 왜도 | -0.0743 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 999.3095 |
| 중앙값 | 993.2135 |
| IQR | 46.2182 |
| Bowley 왜도 | 0.1539 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 987.4731 |
| 중앙값 | 984.5252 |
| IQR | 48.4246 |
| Bowley 왜도 | 0.0194 |
| Adj 이상치 수 | 34 |
| Adj 이상치율 | 2.36% |
| Std 이상치율 | 2.50% |
| 개선율 | 5.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 34건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 961.3950 |
| 중앙값 | 957.2423 |
| IQR | 35.5800 |
| Bowley 왜도 | 0.2483 |
| Adj 이상치 수 | 28 |
| Adj 이상치율 | 0.97% |
| Std 이상치율 | 3.62% |
| 개선율 | 73.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 28건

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

#### SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.0011 | **승수 (L/U)**: 1.001/0.999

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 985.2515 | 985.3392 |
| 상한 경계 | 1204.6015 | 1204.6893 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 1092.5471 |
| 표준편차 | 32.8785 |
| Q1 (25%) | 1067.5955 |
| 중앙값 | 1095.0435 |
| Q3 (75%) | 1122.4330 |
| IQR | 54.8375 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1086.01 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 1118.08 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 1095.24 | 0.00% | 0.00% |
| 2025-08 | 2,876 | 1081.99 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,190 |
| 평균 | 1086.0099 |
| 중앙값 | 1089.4800 |
| IQR | 73.1717 |
| Bowley 왜도 | -0.1203 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1118.0788 |
| 중앙값 | 1124.6050 |
| IQR | 25.7402 |
| Bowley 왜도 | -0.5584 |
| Adj 이상치 수 | 10 |
| Adj 이상치율 | 0.35% |
| Std 이상치율 | 1.88% |
| 개선율 | 81.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 10건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1095.2413 |
| 중앙값 | 1100.3840 |
| IQR | 39.9410 |
| Bowley 왜도 | -0.0944 |
| Adj 이상치 수 | 19 |
| Adj 이상치율 | 1.32% |
| Std 이상치율 | 3.47% |
| 개선율 | 62.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 19건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1081.9916 |
| 중앙값 | 1082.2380 |
| IQR | 29.3250 |
| Bowley 왜도 | 0.0331 |
| Adj 이상치 수 | 58 |
| Adj 이상치율 | 2.02% |
| Std 이상치율 | 1.95% |
| 개선율 | -3.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 58건

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

#### MAIN_GAS_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.1771 | **승수 (L/U)**: 0.838/1.194

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 7.5449 | 5.5000 |
| 상한 경계 | 41.5410 | 39.1000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 22.0738 |
| 표준편차 | 4.2963 |
| Q1 (25%) | 18.1000 |
| 중앙값 | 21.5562 |
| Q3 (75%) | 26.5000 |
| IQR | 8.4000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 18.48 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 23.67 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 27.61 | 0.00% | 0.00% |
| 2025-08 | 2,876 | 26.70 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,190 |
| 평균 | 18.4754 |
| 중앙값 | 18.1000 |
| IQR | 2.7039 |
| Bowley 왜도 | 0.1124 |
| Adj 이상치 수 | 84 |
| Adj 이상치율 | 1.17% |
| Std 이상치율 | 4.09% |
| 개선율 | 71.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 84건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 23.6679 |
| 중앙값 | 22.9000 |
| IQR | 4.7979 |
| Bowley 왜도 | 0.4158 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 27.6067 |
| 중앙값 | 28.0069 |
| IQR | 3.3946 |
| Bowley 왜도 | -0.2932 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 26.7043 |
| 중앙값 | 26.7916 |
| IQR | 0.5973 |
| Bowley 왜도 | -0.2996 |
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
**Bowley 왜도**: -0.3691 | **승수 (L/U)**: 1.446/0.691

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -1312.3559 | -623.2212 |
| 상한 경계 | 3017.0392 | 3493.4879 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 1433.4772 |
| 표준편차 | 623.2708 |
| Q1 (25%) | 920.5447 |
| 중앙값 | 1625.0560 |
| Q3 (75%) | 1949.7220 |
| IQR | 1029.1773 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1493.21 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 1338.86 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 1218.55 | 0.00% | 0.00% |
| 2025-08 | 2,876 | 1486.45 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,190 |
| 평균 | 1493.2073 |
| 중앙값 | 1711.1240 |
| IQR | 926.9040 |
| Bowley 왜도 | -0.4477 |
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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1338.8611 |
| 중앙값 | 1415.8010 |
| IQR | 1150.3319 |
| Bowley 왜도 | -0.1547 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/MAIN_GAS_FLOW_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1218.5453 |
| 중앙값 | 1219.7135 |
| IQR | 1292.5610 |
| Bowley 왜도 | 0.0103 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/MAIN_GAS_FLOW_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1486.4492 |
| 중앙값 | 1679.7825 |
| IQR | 824.7510 |
| Bowley 왜도 | -0.4136 |
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

#### SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.0726 | **승수 (L/U)**: 1.075/0.930

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 992.5287 | 999.0585 |
| 상한 경계 | 1224.1142 | 1230.1865 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 1112.7822 |
| 표준편차 | 33.6497 |
| Q1 (25%) | 1085.7315 |
| 중앙값 | 1116.7210 |
| Q3 (75%) | 1143.5135 |
| IQR | 57.7820 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1108.22 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 1137.37 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 1113.86 | 0.00% | 0.00% |
| 2025-08 | 2,876 | 1099.05 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,190 |
| 평균 | 1108.2186 |
| 중앙값 | 1114.8370 |
| IQR | 78.1090 |
| Bowley 왜도 | -0.2222 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 1137.3653 |
| 중앙값 | 1144.6280 |
| IQR | 23.9355 |
| Bowley 왜도 | -0.5493 |
| Adj 이상치 수 | 4 |
| Adj 이상치율 | 0.14% |
| Std 이상치율 | 2.36% |
| 개선율 | 94.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 4건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 1113.8612 |
| 중앙값 | 1118.6105 |
| IQR | 36.4557 |
| Bowley 왜도 | -0.0303 |
| Adj 이상치 수 | 39 |
| Adj 이상치율 | 2.71% |
| Std 이상치율 | 2.92% |
| 개선율 | 7.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 39건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 1099.0507 |
| 중앙값 | 1101.4330 |
| IQR | 31.0980 |
| Bowley 왜도 | -0.0739 |
| Adj 이상치 수 | 30 |
| Adj 이상치율 | 1.04% |
| Std 이상치율 | 1.67% |
| 개선율 | 37.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 30건

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

#### STAND_10_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7933 | **승수 (L/U)**: 2.211/0.452

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -187.5437 | -82.4427 |
| 상한 경계 | 101.5026 | 149.0438 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 43.3058 |
| 표준편차 | 25.7255 |
| Q1 (25%) | 4.3647 |
| 중앙값 | 56.2561 |
| Q3 (75%) | 62.2363 |
| IQR | 57.8716 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 43.56 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 43.01 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 37.52 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 45.80 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 43.5600 |
| 중앙값 | 54.2012 |
| IQR | 21.8790 |
| Bowley 왜도 | -0.4239 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.91% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 43.0115 |
| 중앙값 | 62.0051 |
| IQR | 62.1056 |
| Bowley 왜도 | -0.9185 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_10_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 37.5159 |
| 중앙값 | 60.5216 |
| IQR | 61.6460 |
| Bowley 왜도 | -0.8955 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_10_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 45.8012 |
| 중앙값 | 59.5987 |
| IQR | 14.6225 |
| Bowley 왜도 | -0.6749 |
| Adj 이상치 수 | 630 |
| Adj 이상치율 | 22.15% |
| Std 이상치율 | 23.35% |
| 개선율 | 5.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 630건

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

#### STAND_12_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6864 | **승수 (L/U)**: 1.987/0.503

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -166.7566 | -81.1986 |
| 상한 경계 | 107.0017 | 150.0707 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 42.7529 |
| 표준편차 | 25.6889 |
| Q1 (25%) | 5.5274 |
| 중앙값 | 54.2787 |
| Q3 (75%) | 63.3447 |
| IQR | 57.8173 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 41.22 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 43.95 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 36.71 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 48.36 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 41.2212 |
| 중앙값 | 48.4856 |
| IQR | 23.5342 |
| Bowley 왜도 | -0.0463 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 11.91% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 43.9458 |
| 중앙값 | 63.3748 |
| IQR | 62.6364 |
| Bowley 왜도 | -0.9229 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_12_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 36.7100 |
| 중앙값 | 53.5683 |
| IQR | 62.1549 |
| Bowley 왜도 | -0.6321 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_12_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 48.3572 |
| 중앙값 | 62.9106 |
| IQR | 17.3247 |
| Bowley 왜도 | -0.6687 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 23.00% |
| 개선율 | 100.0% |

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

#### STAND_11_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7535 | **승수 (L/U)**: 2.124/0.471

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -155.5117 | -71.4493 |
| 상한 경계 | 88.3307 | 127.8988 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 36.6073 |
| 표준편차 | 22.1658 |
| Q1 (25%) | 3.3062 |
| 중앙값 | 47.0017 |
| Q3 (75%) | 53.1433 |
| IQR | 49.8370 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 36.48 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 34.67 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 28.93 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 42.62 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 36.4821 |
| 중앙값 | 44.1840 |
| IQR | 19.0498 |
| Bowley 왜도 | -0.1597 |
| Adj 이상치 수 | 18 |
| Adj 이상치율 | 0.25% |
| Std 이상치율 | 21.83% |
| 개선율 | 98.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 10건
- 2. 2025-05-17: 8건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 34.6665 |
| 중앙값 | 50.5326 |
| IQR | 50.9936 |
| Bowley 왜도 | -0.9336 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_11_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 28.9272 |
| 중앙값 | 41.3791 |
| IQR | 50.8822 |
| Bowley 왜도 | -0.5810 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_11_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 42.6168 |
| 중앙값 | 55.4063 |
| IQR | 14.2699 |
| Bowley 왜도 | -0.7679 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 23.28% |
| 개선율 | 100.0% |

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

#### INDIRECT_COOLING_WATER_FLOW 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.7640 | **승수 (L/U)**: 0.466/2.147

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 151.2267 | 146.4286 |
| 상한 경계 | 180.6808 | 170.3796 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 158.5499 |
| 표준편차 | 4.7898 |
| Q1 (25%) | 155.4102 |
| 중앙값 | 156.1166 |
| Q3 (75%) | 161.3980 |
| IQR | 5.9878 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 155.35 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 167.37 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 161.40 | 0.00% | 0.00% |
| 2025-08 | 2,876 | 156.31 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,190 |
| 평균 | 155.3463 |
| 중앙값 | 155.4160 |
| IQR | 1.0189 |
| Bowley 왜도 | -0.1279 |
| Adj 이상치 수 | 4 |
| Adj 이상치율 | 0.06% |
| Std 이상치율 | 0.06% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 4건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 167.3675 |
| 중앙값 | 167.3781 |
| IQR | 1.3247 |
| Bowley 왜도 | 0.0060 |
| Adj 이상치 수 | 10 |
| Adj 이상치율 | 0.35% |
| Std 이상치율 | 0.35% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 10건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_COOLING_WATER_FLOW_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 161.4017 |
| 중앙값 | 161.3966 |
| IQR | 0.5879 |
| Bowley 왜도 | 0.0444 |
| Adj 이상치 수 | 10 |
| Adj 이상치율 | 0.69% |
| Std 이상치율 | 0.62% |
| 개선율 | -11.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 10건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_COOLING_WATER_FLOW_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 156.3071 |
| 중앙값 | 156.2971 |
| IQR | 0.5526 |
| Bowley 왜도 | 0.0639 |
| Adj 이상치 수 | 16 |
| Adj 이상치율 | 0.56% |
| Std 이상치율 | 0.42% |
| 개선율 | -33.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 16건

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

#### INDIRECT_WATER_MAIN_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.3403 | **승수 (L/U)**: 0.712/1.405

**데이터**: 원본 14,384 → 필터 후 14,384 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 24.2244 | 21.9694 |
| 상한 경계 | 45.9859 | 42.8169 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,384 |
| 평균 | 31.9470 |
| 표준편차 | 2.5402 |
| Q1 (25%) | 29.7872 |
| 중앙값 | 31.5064 |
| Q3 (75%) | 34.9991 |
| IQR | 5.2119 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 30.03 | 0.00% | 0.00% |
| 2025-06 | 2,878 | 31.52 | 0.00% | 0.00% |
| 2025-07 | 1,440 | 35.69 | 0.00% | 0.00% |
| 2025-08 | 2,876 | 35.31 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,190 |
| 평균 | 30.0275 |
| 중앙값 | 29.7872 |
| IQR | 2.2852 |
| Bowley 왜도 | 0.3985 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,878 |
| 평균 | 31.5160 |
| 중앙값 | 31.6000 |
| IQR | 1.0000 |
| Bowley 왜도 | -0.2000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,440 |
| 평균 | 35.6851 |
| 중앙값 | 35.6030 |
| IQR | 0.7000 |
| Bowley 왜도 | 0.4201 |
| Adj 이상치 수 | 4 |
| Adj 이상치율 | 0.28% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 4건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted/INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,876 |
| 평균 | 35.3054 |
| 중앙값 | 35.2004 |
| IQR | 0.7000 |
| Bowley 왜도 | 0.4274 |
| Adj 이상치 수 | 28 |
| Adj 이상치율 | 0.97% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 28건

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

#### FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6357 | **승수 (L/U)**: 1.888/0.530

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -142.0459 | -72.5304 |
| 상한 경계 | 99.3283 | 136.1409 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 38.2454 |
| 표준편차 | 23.1499 |
| Q1 (25%) | 5.7213 |
| 중앙값 | 48.3870 |
| Q3 (75%) | 57.8892 |
| IQR | 52.1678 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 36.45 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 39.63 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 32.52 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 44.18 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 36.4454 |
| 중앙값 | 39.2082 |
| IQR | 24.4815 |
| Bowley 왜도 | 0.3567 |
| Adj 이상치 수 | 1,552 |
| Adj 이상치율 | 21.83% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 849건
- 2. 2025-05-18: 703건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 39.6301 |
| 중앙값 | 57.3551 |
| IQR | 54.8062 |
| Bowley 왜도 | -0.9460 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 32.5182 |
| 중앙값 | 41.5213 |
| IQR | 56.9429 |
| Bowley 왜도 | -0.3303 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 44.1751 |
| 중앙값 | 56.8845 |
| IQR | 16.7510 |
| Bowley 왜도 | -0.7477 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.78% |
| 개선율 | 100.0% |

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

#### FINISHING_BLOCK_MASTER_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6352 | **승수 (L/U)**: 1.887/0.530

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -141.8954 | -72.4639 |
| 상한 경계 | 99.3861 | 136.1723 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 38.2716 |
| 표준편차 | 23.1639 |
| Q1 (25%) | 5.7747 |
| 중앙값 | 48.4204 |
| Q3 (75%) | 57.9337 |
| IQR | 52.1591 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 36.47 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 39.66 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 32.55 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 44.20 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 36.4694 |
| 중앙값 | 39.2206 |
| IQR | 24.4621 |
| Bowley 왜도 | 0.3612 |
| Adj 이상치 수 | 1,555 |
| Adj 이상치율 | 21.87% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 849건
- 2. 2025-05-18: 706건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 39.6619 |
| 중앙값 | 57.3815 |
| IQR | 54.8321 |
| Bowley 왜도 | -0.9457 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 32.5467 |
| 중앙값 | 41.5318 |
| IQR | 57.0011 |
| Bowley 왜도 | -0.3289 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 44.1996 |
| 중앙값 | 56.9196 |
| IQR | 16.7259 |
| Bowley 왜도 | -0.7476 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.78% |
| 개선율 | 100.0% |

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

#### STAND_14_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8820 | **승수 (L/U)**: 2.416/0.414

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -109.5369 | -42.6504 |
| 상한 경계 | 55.6441 | 83.3313 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 26.0437 |
| 표준편차 | 14.7741 |
| Q1 (25%) | 4.5928 |
| 중앙값 | 34.2304 |
| Q3 (75%) | 36.0882 |
| IQR | 31.4954 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 26.70 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 23.99 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 22.37 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 28.26 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 26.6960 |
| 중앙값 | 33.9876 |
| IQR | 12.2228 |
| Bowley 왜도 | -0.8006 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.67% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 23.9894 |
| 중앙값 | 34.1133 |
| IQR | 31.8262 |
| Bowley 왜도 | -0.9260 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_14_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 22.3688 |
| 중앙값 | 35.1062 |
| IQR | 33.3372 |
| Bowley 왜도 | -0.9199 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_14_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 28.2589 |
| 중앙값 | 36.4932 |
| IQR | 9.7519 |
| Bowley 왜도 | -0.8220 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.93% |
| 개선율 | 100.0% |

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

#### STAND_13_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8546 | **승수 (L/U)**: 2.350/0.425

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -165.8331 | -68.1941 |
| 상한 경계 | 83.0735 | 124.6148 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 37.4357 |
| 표준편차 | 22.0896 |
| Q1 (25%) | 4.1092 |
| 중앙값 | 48.8069 |
| Q3 (75%) | 52.3115 |
| IQR | 48.2022 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 37.71 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 33.88 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 33.50 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 42.22 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 37.7088 |
| 중앙값 | 48.2362 |
| IQR | 18.7840 |
| Bowley 왜도 | -0.8015 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.54% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 33.8805 |
| 중앙값 | 48.5033 |
| IQR | 48.3290 |
| Bowley 왜도 | -0.9077 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_13_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 33.5041 |
| 중앙값 | 51.9736 |
| IQR | 51.3609 |
| Bowley 왜도 | -0.9270 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_13_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 42.2188 |
| 중앙값 | 55.1074 |
| IQR | 14.8860 |
| Bowley 왜도 | -0.7942 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 23.07% |
| 개선율 | 100.0% |

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

#### STAND_1_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6995 | **승수 (L/U)**: 2.013/0.497

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -154.4428 | -74.5099 |
| 상한 경계 | 96.2364 | 135.9485 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 39.0593 |
| 표준편차 | 23.9482 |
| Q1 (25%) | 4.4120 |
| 중앙값 | 49.1221 |
| Q3 (75%) | 57.0266 |
| IQR | 52.6146 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 37.35 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 39.73 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 34.92 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 44.69 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 37.3516 |
| 중앙값 | 46.1438 |
| IQR | 18.7052 |
| Bowley 왜도 | -0.4028 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.78% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 39.7269 |
| 중앙값 | 56.1276 |
| IQR | 59.3612 |
| Bowley 왜도 | -0.8623 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_1_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 34.9212 |
| 중앙값 | 52.3342 |
| IQR | 59.3921 |
| Bowley 왜도 | -0.7376 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_1_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 44.6928 |
| 중앙값 | 57.0165 |
| IQR | 19.9358 |
| Bowley 왜도 | -0.4887 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.64% |
| 개선율 | 100.0% |

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
**Bowley 왜도**: -0.8011 | **승수 (L/U)**: 2.228/0.449

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -177.1727 | -75.9349 |
| 상한 경계 | 98.4707 | 143.9097 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 43.1075 |
| 표준편차 | 26.0302 |
| Q1 (25%) | 6.5068 |
| 중앙값 | 56.0021 |
| Q3 (75%) | 61.4680 |
| IQR | 54.9612 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 43.15 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 41.62 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 34.51 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 48.70 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 43.1455 |
| 중앙값 | 54.7901 |
| IQR | 23.4573 |
| Bowley 왜도 | -0.6485 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 11.63% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 41.6238 |
| 중앙값 | 58.7423 |
| IQR | 61.9341 |
| Bowley 왜도 | -0.8588 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_2_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 34.5080 |
| 중앙값 | 52.2236 |
| IQR | 58.2841 |
| Bowley 왜도 | -0.7560 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_2_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 48.7042 |
| 중앙값 | 62.2698 |
| IQR | 21.8966 |
| Bowley 왜도 | -0.5304 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.43% |
| 개선율 | 100.0% |

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
**Bowley 왜도**: -0.7639 | **승수 (L/U)**: 2.147/0.466

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -138.9249 | -59.5405 |
| 상한 경계 | 88.0859 | 125.0653 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 39.3264 |
| 표준편차 | 23.7851 |
| Q1 (25%) | 9.6867 |
| 중앙값 | 50.3909 |
| Q3 (75%) | 55.8381 |
| IQR | 46.1514 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 38.82 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 37.44 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 33.20 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 45.48 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 38.8155 |
| 중앙값 | 48.7178 |
| IQR | 20.9065 |
| Bowley 왜도 | -0.5977 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 11.73% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 37.4427 |
| 중앙값 | 52.9231 |
| IQR | 55.7828 |
| Bowley 왜도 | -0.8647 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_3_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 33.2024 |
| 중앙값 | 50.8427 |
| IQR | 55.9787 |
| Bowley 왜도 | -0.7892 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_3_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 45.4808 |
| 중앙값 | 58.0878 |
| IQR | 21.5189 |
| Bowley 왜도 | -0.5055 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.29% |
| 개선율 | 100.0% |

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
**Bowley 왜도**: -0.6898 | **승수 (L/U)**: 1.993/0.502

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -129.8229 | -60.4837 |
| 상한 경계 | 90.8893 | 125.6762 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 38.5386 |
| 표준편차 | 23.4165 |
| Q1 (25%) | 9.3263 |
| 중앙값 | 48.6472 |
| Q3 (75%) | 55.8663 |
| IQR | 46.5400 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 37.34 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 38.33 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 32.27 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 44.82 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 37.3352 |
| 중앙값 | 44.7936 |
| IQR | 20.7061 |
| Bowley 왜도 | -0.2754 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 11.71% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 38.3306 |
| 중앙값 | 54.4006 |
| IQR | 56.7776 |
| Bowley 왜도 | -0.8728 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_4_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 32.2740 |
| 중앙값 | 48.7308 |
| IQR | 54.5329 |
| Bowley 왜도 | -0.7473 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_4_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 44.8249 |
| 중앙값 | 56.7498 |
| IQR | 24.2060 |
| Bowley 왜도 | -0.5055 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.66% |
| 개선율 | 100.0% |

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

#### STAND_5_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7769 | **승수 (L/U)**: 2.175/0.460

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -129.6432 | -55.3336 |
| 상한 경계 | 79.1808 | 113.3503 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 35.0149 |
| 표준편차 | 21.0660 |
| Q1 (25%) | 7.9229 |
| 중앙값 | 45.3898 |
| Q3 (75%) | 50.0938 |
| IQR | 42.1710 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 34.67 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 33.32 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 31.52 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 39.27 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 34.6743 |
| 중앙값 | 43.4761 |
| IQR | 19.1899 |
| Bowley 왜도 | -0.5801 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.23% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 33.3196 |
| 중앙값 | 47.6768 |
| IQR | 49.4822 |
| Bowley 왜도 | -0.8908 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_5_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 31.5162 |
| 중앙값 | 48.7799 |
| IQR | 53.1872 |
| Bowley 왜도 | -0.8055 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_5_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 39.2688 |
| 중앙값 | 50.5501 |
| IQR | 17.6066 |
| Bowley 왜도 | -0.6125 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.36% |
| 개선율 | 100.0% |

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
**Bowley 왜도**: -0.7339 | **승수 (L/U)**: 2.083/0.480

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -115.3781 | -51.5399 |
| 상한 경계 | 74.9880 | 105.6338 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 32.5349 |
| 표준편차 | 19.3401 |
| Q1 (25%) | 7.4002 |
| 중앙값 | 41.4649 |
| Q3 (75%) | 46.6936 |
| IQR | 39.2934 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 32.55 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 32.30 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 28.36 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 34.79 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 32.5493 |
| 중앙값 | 40.2445 |
| IQR | 16.4987 |
| Bowley 왜도 | -0.4948 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.25% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 32.2951 |
| 중앙값 | 45.8644 |
| IQR | 47.2427 |
| Bowley 왜도 | -0.8794 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_6_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 28.3564 |
| 중앙값 | 43.7095 |
| IQR | 46.9235 |
| Bowley 왜도 | -0.8052 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_6_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 34.7857 |
| 중앙값 | 44.7206 |
| IQR | 14.0721 |
| Bowley 왜도 | -0.5513 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.93% |
| 개선율 | 100.0% |

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
**Bowley 왜도**: -0.8273 | **승수 (L/U)**: 2.287/0.437

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -116.9742 | -47.4189 |
| 상한 경계 | 66.2809 | 96.6934 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 30.5612 |
| 표준편차 | 18.0836 |
| Q1 (25%) | 6.6232 |
| 중앙값 | 39.5397 |
| Q3 (75%) | 42.6513 |
| IQR | 36.0281 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 30.28 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 28.35 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 24.99 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 36.19 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 30.2843 |
| 중앙값 | 37.9168 |
| IQR | 14.6520 |
| Bowley 왜도 | -0.5686 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.42% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 28.3500 |
| 중앙값 | 40.4799 |
| IQR | 40.4294 |
| Bowley 왜도 | -0.9042 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_7_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 24.9900 |
| 중앙값 | 38.7841 |
| IQR | 40.5364 |
| Bowley 왜도 | -0.8271 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_7_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 36.1854 |
| 중앙값 | 46.5522 |
| IQR | 15.2532 |
| Bowley 왜도 | -0.6185 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.50% |
| 개선율 | 100.0% |

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
**Bowley 왜도**: -0.6621 | **승수 (L/U)**: 1.939/0.516

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -95.1293 | -45.7047 |
| 상한 경계 | 69.1741 | 94.6646 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 29.1913 |
| 표준편차 | 17.1032 |
| Q1 (25%) | 6.9338 |
| 중앙값 | 36.0980 |
| Q3 (75%) | 42.0261 |
| IQR | 35.0923 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 29.34 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 30.15 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 26.72 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 29.09 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 29.3354 |
| 중앙값 | 34.8138 |
| IQR | 13.7837 |
| Bowley 왜도 | -0.1073 |
| Adj 이상치 수 | 1,523 |
| Adj 이상치율 | 21.42% |
| Std 이상치율 | 21.66% |
| 개선율 | 1.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 839건
- 2. 2025-05-18: 684건

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 30.1537 |
| 중앙값 | 42.6777 |
| IQR | 42.2826 |
| Bowley 왜도 | -0.8932 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_8_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 26.7154 |
| 중앙값 | 41.5614 |
| IQR | 42.5098 |
| Bowley 왜도 | -0.8455 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_8_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 29.0863 |
| 중앙값 | 36.9469 |
| IQR | 11.1171 |
| Bowley 왜도 | -0.5928 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.78% |
| 개선율 | 100.0% |

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

#### STAND_9_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8225 | **승수 (L/U)**: 2.276/0.439

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -191.5425 | -82.6809 |
| 상한 경계 | 96.9805 | 144.8089 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 41.9504 |
| 표준편차 | 25.4174 |
| Q1 (25%) | 2.6277 |
| 중앙값 | 54.4516 |
| Q3 (75%) | 59.5002 |
| IQR | 56.8724 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 42.39 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 43.42 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 38.46 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 41.09 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 42.3938 |
| 중앙값 | 54.1401 |
| IQR | 19.8121 |
| Bowley 왜도 | -0.6017 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.15% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 43.4233 |
| 중앙값 | 63.2362 |
| IQR | 64.7441 |
| Bowley 왜도 | -0.9239 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted/STAND_9_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 38.4591 |
| 중앙값 | 62.0702 |
| IQR | 64.9644 |
| Bowley 왜도 | -0.8851 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted/STAND_9_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 41.0870 |
| 중앙값 | 53.3647 |
| IQR | 15.2643 |
| Bowley 왜도 | -0.6832 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 23.07% |
| 개선율 | 100.0% |

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

#### STAND_3_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.3333 | -0.6412 |
| 상한 경계 | 1.3623 | 1.9848 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7235 |
| 표준편차 | 0.4172 |
| Q1 (25%) | 0.3435 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6565 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7441 |
| 중앙값 | 1.0000 |
| IQR | 0.3041 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.12% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6898 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_3_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6144 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_3_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7589 |
| 중앙값 | 1.0000 |
| IQR | 0.1292 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 622 |
| Adj 이상치율 | 21.87% |
| Std 이상치율 | 23.84% |
| 개선율 | 8.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 622건

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

#### STAND_2_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.3050 | -0.6273 |
| 상한 경계 | 1.3592 | 1.9764 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7239 |
| 표준편차 | 0.4180 |
| Q1 (25%) | 0.3491 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6509 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7448 |
| 중앙값 | 1.0000 |
| IQR | 0.2785 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.02% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6898 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_2_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6147 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_2_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7592 |
| 중앙값 | 1.0000 |
| IQR | 0.1447 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 610 |
| Adj 이상치율 | 21.45% |
| Std 이상치율 | 23.63% |
| 개선율 | 9.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 610건

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

#### STAND_1_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.3139 | -0.6317 |
| 상한 경계 | 1.3602 | 1.9790 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7242 |
| 표준편차 | 0.4184 |
| Q1 (25%) | 0.3473 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6527 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.75 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7454 |
| 중앙값 | 1.0000 |
| IQR | 0.2265 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.80% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6896 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_1_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6148 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_1_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7592 |
| 중앙값 | 1.0000 |
| IQR | 0.1280 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 618 |
| Adj 이상치율 | 21.73% |
| Std 이상치율 | 23.70% |
| 개선율 | 8.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 618건

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

#### STAND_13_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.4290 | -0.6883 |
| 상한 경계 | 1.3727 | 2.0130 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7209 |
| 표준편차 | 0.4187 |
| Q1 (25%) | 0.3247 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6753 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7410 |
| 중앙값 | 1.0000 |
| IQR | 0.2428 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.56% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6877 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_13_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6113 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_13_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7575 |
| 중앙값 | 1.0000 |
| IQR | 0.1408 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 614 |
| Adj 이상치율 | 21.59% |
| Std 이상치율 | 23.42% |
| 개선율 | 7.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 614건

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
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.4290 | -0.6883 |
| 상한 경계 | 1.3727 | 2.0130 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7209 |
| 표준편차 | 0.4187 |
| Q1 (25%) | 0.3247 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6753 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7410 |
| 중앙값 | 1.0000 |
| IQR | 0.2428 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.56% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6877 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_12_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6113 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_12_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7575 |
| 중앙값 | 1.0000 |
| IQR | 0.1408 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 614 |
| Adj 이상치율 | 21.59% |
| Std 이상치율 | 23.42% |
| 개선율 | 7.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 614건

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
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.3837 | -0.6660 |
| 상한 경계 | 1.3677 | 1.9996 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7208 |
| 표준편차 | 0.4186 |
| Q1 (25%) | 0.3336 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6664 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7408 |
| 중앙값 | 1.0000 |
| IQR | 0.2410 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.64% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6877 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_11_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6112 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_11_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7573 |
| 중앙값 | 1.0000 |
| IQR | 0.1418 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 610 |
| Adj 이상치율 | 21.45% |
| Std 이상치율 | 23.56% |
| 개선율 | 9.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 610건

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
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.3875 | -0.6679 |
| 상한 경계 | 1.3682 | 2.0008 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7211 |
| 표준편차 | 0.4185 |
| Q1 (25%) | 0.3328 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6672 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7413 |
| 중앙값 | 1.0000 |
| IQR | 0.2422 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.68% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6878 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_10_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6114 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_10_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7575 |
| 중앙값 | 1.0000 |
| IQR | 0.1410 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 614 |
| Adj 이상치율 | 21.59% |
| Std 이상치율 | 23.42% |
| 개선율 | 7.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 614건

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

#### STAND_9_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.3634 | -0.6560 |
| 상한 경계 | 1.3655 | 1.9936 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7208 |
| 표준편차 | 0.4184 |
| Q1 (25%) | 0.3376 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6624 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7409 |
| 중앙값 | 1.0000 |
| IQR | 0.2567 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.39% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6877 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_9_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6114 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_9_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7572 |
| 중앙값 | 1.0000 |
| IQR | 0.1413 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 614 |
| Adj 이상치율 | 21.59% |
| Std 이상치율 | 23.42% |
| 개선율 | 7.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 614건

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

#### STAND_8_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.2584 | -0.6044 |
| 상한 경계 | 1.3541 | 1.9626 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7229 |
| 표준편차 | 0.4173 |
| Q1 (25%) | 0.3582 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6418 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7430 |
| 중앙값 | 1.0000 |
| IQR | 0.2752 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.99% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6899 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_8_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6141 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_8_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7586 |
| 중앙값 | 1.0000 |
| IQR | 0.1382 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 622 |
| Adj 이상치율 | 21.87% |
| Std 이상치율 | 23.35% |
| 개선율 | 6.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 622건

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

#### STAND_7_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.3196 | -0.6345 |
| 상한 경계 | 1.3608 | 1.9807 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7227 |
| 표준편차 | 0.4172 |
| Q1 (25%) | 0.3462 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6538 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7428 |
| 중앙값 | 1.0000 |
| IQR | 0.2992 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.54% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6899 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_7_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6141 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_7_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7585 |
| 중앙값 | 1.0000 |
| IQR | 0.1378 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 622 |
| Adj 이상치율 | 21.87% |
| Std 이상치율 | 23.28% |
| 개선율 | 6.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 622건

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

#### STAND_6_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.3054 | -0.6275 |
| 상한 경계 | 1.3592 | 1.9765 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7228 |
| 표준편차 | 0.4171 |
| Q1 (25%) | 0.3490 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6510 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7429 |
| 중앙값 | 1.0000 |
| IQR | 0.2950 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.46% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6898 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_6_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6141 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_6_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7583 |
| 중앙값 | 1.0000 |
| IQR | 0.1378 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 614 |
| Adj 이상치율 | 21.59% |
| Std 이상치율 | 23.42% |
| 개선율 | 7.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 614건

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

#### STAND_5_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.2601 | -0.6052 |
| 상한 경계 | 1.3543 | 1.9631 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7227 |
| 표준편차 | 0.4170 |
| Q1 (25%) | 0.3579 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6421 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7429 |
| 중앙값 | 1.0000 |
| IQR | 0.3082 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.00% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6898 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_5_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6141 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_5_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7583 |
| 중앙값 | 1.0000 |
| IQR | 0.1365 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 626 |
| Adj 이상치율 | 22.01% |
| Std 이상치율 | 23.77% |
| 개선율 | 7.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 626건

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

#### STAND_4_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.2777 | -0.6139 |
| 상한 경계 | 1.3562 | 1.9683 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7232 |
| 표준편차 | 0.4169 |
| Q1 (25%) | 0.3545 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6455 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7436 |
| 중앙값 | 1.0000 |
| IQR | 0.3036 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 20.73% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6898 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_4_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6143 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_4_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7587 |
| 중앙값 | 1.0000 |
| IQR | 0.1320 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 622 |
| Adj 이상치율 | 21.87% |
| Std 이상치율 | 23.77% |
| 개선율 | 8.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 622건

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

#### PINCHROLL_3_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7851 | **승수 (L/U)**: 2.193/0.456

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -72.1972 | -30.6193 |
| 상한 경계 | 43.3891 | 62.3522 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 17.4736 |
| 표준편차 | 11.4112 |
| Q1 (25%) | 4.2450 |
| 중앙값 | 24.9901 |
| Q3 (75%) | 27.4879 |
| IQR | 23.2429 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 14.06 | 0.00% | 0.00% |
| 2025-06 | 2,348 | 25.19 | 0.00% | 0.00% |
| 2025-07 | 1,054 | 21.46 | 0.00% | 0.00% |
| 2025-08 | 2,501 | 16.96 | 0.00% | 0.00% |


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
| 분석 레코드 | 6,158 |
| 평균 | 14.0558 |
| 중앙값 | 5.2306 |
| IQR | 20.9793 |
| Bowley 왜도 | 0.8842 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 25.1946 |
| 중앙값 | 29.9932 |
| IQR | 0.7469 |
| Bowley 왜도 | -0.9832 |
| Adj 이상치 수 | 1,108 |
| Adj 이상치율 | 47.19% |
| Std 이상치율 | 46.85% |
| 개선율 | -0.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 1,108건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 21.4564 |
| 중앙값 | 24.9939 |
| IQR | 22.8582 |
| Bowley 왜도 | -0.7789 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 16.9619 |
| 중앙값 | 24.9900 |
| IQR | 20.8756 |
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

#### PINCHROLL_3_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 100.0%
**Bowley 왜도**: -0.9608 | **승수 (L/U)**: 2.614/0.383

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 2 |
| 이상치율 | 0.00% | 0.02% |
| 하한 경계 | -1441.0262 | 241.4005 |
| 상한 경계 | 2377.8112 | 3021.4845 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 1793.3208 |
| 표준편차 | 307.8355 |
| Q1 (25%) | 1283.9320 |
| 중앙값 | 1965.3310 |
| Q3 (75%) | 1978.9530 |
| IQR | 695.0210 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 1661.87 | 0.00% | 0.03% |
| 2025-06 | 2,348 | 1980.63 | 0.00% | 0.00% |
| 2025-07 | 1,054 | 1744.63 | 0.00% | 0.00% |
| 2025-08 | 2,501 | 1961.64 | 0.00% | 0.00% |


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
| 분석 레코드 | 6,158 |
| 평균 | 1661.8732 |
| 중앙값 | 1958.5280 |
| IQR | 684.3670 |
| Bowley 왜도 | -0.9717 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.03% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 1980.6331 |
| 중앙값 | 1976.1865 |
| IQR | 8.9780 |
| Bowley 왜도 | -0.0293 |
| Adj 이상치 수 | 421 |
| Adj 이상치율 | 17.93% |
| Std 이상치율 | 17.84% |
| 개선율 | -0.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 421건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 1744.6275 |
| 중앙값 | 2007.7370 |
| IQR | 729.2545 |
| Bowley 왜도 | -0.9709 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 1961.6406 |
| 중앙값 | 1947.3460 |
| IQR | 57.9720 |
| Bowley 왜도 | 0.7120 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

#### STAND_14_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.3695 | -0.6591 |
| 상한 경계 | 1.3662 | 1.9954 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7207 |
| 표준편차 | 0.4187 |
| Q1 (25%) | 0.3364 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6636 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7408 |
| 중앙값 | 1.0000 |
| IQR | 0.2401 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.71% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6877 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/STAND_14_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6111 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/STAND_14_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7572 |
| 중앙값 | 1.0000 |
| IQR | 0.1487 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 610 |
| Adj 이상치율 | 21.45% |
| Std 이상치율 | 23.28% |
| 개선율 | 7.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 610건

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

#### PINCHROLL_4_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8367 | **승수 (L/U)**: 2.309/0.433

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -1253.6595 | 181.8625 |
| 상한 경계 | 2485.1023 | 3106.8825 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 1779.7663 |
| 표준편차 | 334.9113 |
| Q1 (25%) | 1278.7450 |
| 중앙값 | 1950.2920 |
| Q3 (75%) | 2010.0000 |
| IQR | 731.2550 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 1628.55 | 0.00% | 0.00% |
| 2025-06 | 2,348 | 2041.36 | 0.00% | 0.00% |
| 2025-07 | 1,054 | 1692.40 | 0.00% | 0.00% |
| 2025-08 | 2,501 | 1943.31 | 0.00% | 0.00% |


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
| 분석 레코드 | 6,158 |
| 평균 | 1628.5525 |
| 중앙값 | 1943.9200 |
| IQR | 735.5240 |
| Bowley 왜도 | -0.9691 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 2041.3634 |
| 중앙값 | 2034.5955 |
| IQR | 10.8020 |
| Bowley 왜도 | -0.0286 |
| Adj 이상치 수 | 427 |
| Adj 이상치율 | 18.19% |
| Std 이상치율 | 18.14% |
| 개선율 | -0.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 427건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 1692.4020 |
| 중앙값 | 1945.4120 |
| IQR | 723.2733 |
| Bowley 왜도 | -0.9715 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 1943.3113 |
| 중앙값 | 1942.9760 |
| IQR | 33.8430 |
| Bowley 왜도 | -0.4875 |
| Adj 이상치 수 | 280 |
| Adj 이상치율 | 11.20% |
| Std 이상치율 | 9.28% |
| 개선율 | -20.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 280건

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

#### FINISHING_BLOCK_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 14,384 → 필터 후 14,180 (1.4% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -2.4163 | -0.6821 |
| 상한 경계 | 1.3713 | 2.0092 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 14,180 |
| 평균 | 0.7206 |
| 표준편차 | 0.4187 |
| Q1 (25%) | 0.3272 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.6728 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 2,831 | 0.69 | 0.00% | 0.00% |
| 2025-07 | 1,394 | 0.61 | 0.00% | 0.00% |
| 2025-08 | 2,844 | 0.76 | 0.00% | 0.00% |


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
| 분석 레코드 | 7,111 |
| 평균 | 0.7405 |
| 중앙값 | 1.0000 |
| IQR | 0.2622 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 22.40% |
| 개선율 | 100.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,831 |
| 평균 | 0.6875 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted/FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted/FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted/FINISHING_BLOCK_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,394 |
| 평균 | 0.6110 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted/FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted/FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted/FINISHING_BLOCK_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,844 |
| 평균 | 0.7573 |
| 중앙값 | 1.0000 |
| IQR | 0.1420 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 608 |
| Adj 이상치율 | 21.38% |
| Std 이상치율 | 23.35% |
| 개선율 | 8.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 608건

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

#### PINCHROLL_3_REFERENCE_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.8046 | **승수 (L/U)**: 0.447/2.236

**데이터**: 원본 14,384 → 필터 후 12,061 (16.1% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -24.5503 | -85.7812 |
| 상한 경계 | 346.5316 | 209.6354 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 12,061 |
| 평균 | 57.5793 |
| 표준편차 | 34.7326 |
| Q1 (25%) | 25.0000 |
| 중앙값 | 32.2167 |
| Q3 (75%) | 98.8542 |
| IQR | 73.8542 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 65.63 | 0.00% | 0.00% |
| 2025-06 | 2,348 | 43.50 | 0.00% | 0.00% |
| 2025-07 | 1,054 | 47.65 | 0.00% | 0.00% |
| 2025-08 | 2,501 | 55.16 | 0.00% | 0.00% |


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
| 분석 레코드 | 6,158 |
| 평균 | 65.6302 |
| 중앙값 | 98.0700 |
| IQR | 75.0000 |
| Bowley 왜도 | -0.9485 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

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

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,348 |
| 평균 | 43.4982 |
| 중앙값 | 30.0000 |
| IQR | 2.5492 |
| Bowley 왜도 | 1.0000 |
| Adj 이상치 수 | 514 |
| Adj 이상치율 | 21.89% |
| Std 이상치율 | 23.17% |
| 개선율 | 5.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 514건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted/PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 1,054 |
| 평균 | 47.6469 |
| 중앙값 | 35.0000 |
| IQR | 51.7185 |
| Bowley 왜도 | 0.6133 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted/PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,501 |
| 평균 | 55.1616 |
| 중앙값 | 27.5400 |
| IQR | 73.8817 |
| Bowley 왜도 | 0.9312 |
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


---

## 월별 이상치율 추이

| 월 | Adjusted IQR 평균 | Standard IQR 평균 | 개선율 |
|-----|------------------|-------------------|--------|
| 2025-03 | N/A | N/A | N/A |
| 2025-04 | N/A | N/A | N/A |
| 2025-05 | 3.49% | 3.79% | 7.9% |
| 2025-06 | 4.54% | 4.80% | 5.3% |
| 2025-07 | 6.44% | 6.78% | 5.0% |
| 2025-08 | 3.91% | 4.01% | 2.4% |

---

## 상위 개선 태그 (Top 10)

Adjusted IQR 적용으로 가장 큰 개선을 보인 태그:

| 순위 | 태그명 | Std 이상치율 | Adj 이상치율 | 개선율 | Bowley 왜도 |
|------|--------|--------------|--------------|--------|-------------|
| 1 | HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 0.10% | 0.00% | **100.0%** | 0.1270 |
| 2 | PINCHROLL_3_ACTUAL_SPEED | 0.02% | 0.00% | **100.0%** | -0.9608 |
| 3 | PINCHROLL_2_ACTUAL_TORQUE | 16.06% | 2.14% | **86.7%** | -0.9998 |
| 4 | HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 0.26% | 0.06% | **76.3%** | 0.1124 |
| 5 | FINISHING_BLOCK_ACTUAL_SPEED | 33.79% | 13.64% | **59.6%** | 0.9602 |
| 6 | PR9L1_ACT_TORQUE | 0.75% | 0.37% | **50.5%** | -0.4626 |
| 7 | PINCHROLL_4_REFERENCE_TORQUE | 13.22% | 11.16% | **15.6%** | 0.4931 |
| 8 | STAND_10_ACTUAL_SPEED | 15.37% | 13.55% | **11.9%** | 0.2784 |
| 9 | COMBUSTION_AIR_TEMPERATURE | 0.31% | 0.28% | **11.1%** | 0.0733 |
| 10 | STAND_6_ACTUAL_SPEED | 15.13% | 13.70% | **9.5%** | 0.1531 |

---

## 높은 왜도 태그 분석

Bowley 왜도 절대값이 큰 태그 (비대칭 분포):

| 태그명 | Bowley 왜도 | 분포 방향 | 승수 (L/U) | 개선율 |
|--------|-------------|----------|------------|--------|
| STAND_10_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_12_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_13_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_1_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_2_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_4_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_6_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_8_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_9_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_11_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |


---

## 결론 및 권장사항

### 분석 결과 요약

1. **전체 개선 효과**: Adjusted IQR 적용으로 평균 **0.9%** 이상치율 감소
2. **총 이상치 감소**: 46,386 → 43,911 (2,475개 감소)
3. **위험등급 개선**: CRITICAL/DANGER 태그 7개 → 4개

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

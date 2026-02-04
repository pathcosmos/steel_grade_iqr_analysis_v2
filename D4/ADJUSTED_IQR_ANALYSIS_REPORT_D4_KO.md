# 강종 [D4] Adjusted IQR 상세 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D4
**분석 방법**: Adjusted IQR (Bowley 왜도 보정)
**c 값**: 1.0
**생성일시**: 2026-02-03 12:06:00

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
| **분석 대상 강종** | D4 |
| **c 값 (왜도 보정 강도)** | 1.0 |
| **총 분석 태그 수** | 78개 |
| **PR_Detailed L1 태그** | 4개 |
| **PR_Detailed L2 태그** | 2개 |

### 이상치율 개선 효과

| 지표 | Standard IQR | Adjusted IQR | 개선 |
|------|-------------|--------------|------|
| **총 이상치 수** | 78,944 | 73,166 | 5,778 감소 |
| **평균 개선율** | - | - | **3.3%** |

### 위험도 분포 비교

| 등급 | Standard IQR | Adjusted IQR | 변화 |
|------|-------------|--------------|------|
| **⚫ 심각 (25% 이상)** | 1개 | 0개 | +1 |
| **🔴 위험 (15~25%)** | 17개 | 18개 | -1 |
| **🟠 경고 (10~15%)** | 2개 | 1개 | +1 |
| **🟡 주의 (5~10%)** | 6개 | 7개 | -1 |
| **🟢 양호 (0~5%)** | 52개 | 52개 | +0 |

---

## 카테고리별 상세 분석


### 01_Furnace_Top_Temperature (가열로 상부 온도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 2.60% | 2.78% | 6.4% | -0.4711 | 1.602/0.624 | 🟢 NORMAL |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 2.57% | 2.75% | 6.5% | -0.4521 | 1.572/0.636 | 🟢 NORMAL |
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 0.25% | 2.04% | 87.8% | -0.5872 | 1.799/0.556 | 🟢 NORMAL |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 0.22% | 1.89% | 88.2% | -0.5899 | 1.804/0.554 | 🟢 NORMAL |

### 02_Furnace_Bottom_Temperature (가열로 하부 온도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 2.83% | 2.80% | -1.1% | 0.1155 | 0.891/1.122 | 🟢 NORMAL |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 2.78% | 2.78% | 0.0% | 0.0026 | 0.997/1.003 | 🟢 NORMAL |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 1.40% | 0.66% | -112.0% | 0.0768 | 0.926/1.080 | 🟢 NORMAL |
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 0.58% | 0.61% | 4.9% | 0.1378 | 0.871/1.148 | 🟢 NORMAL |

### 03_Furnace_Discharge_Temperature (가열로 추출 온도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 8.33% | 8.34% | 0.1% | -0.0312 | 1.032/0.969 | 🟡 CAUTION |

### 04_Furnace_Auxiliary (가열로 보조설비)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| FURNACE_O2_ANALYZER | 22.12% | 22.12% | 0.0% | -0.1394 | 1.150/0.870 | 🔴 DANGER |
| MAIN_COMBUSTION_AIR_PRESSURE | 8.95% | 8.95% | 0.1% | 0.0641 | 0.938/1.066 | 🟡 CAUTION |
| MAIN_GAS_PRESSURE | 4.00% | 4.67% | 14.4% | -0.2891 | 1.335/0.749 | 🟢 NORMAL |
| FURNACE_PRESSURE | 2.76% | 2.23% | -23.6% | -0.1243 | 1.132/0.883 | 🟢 NORMAL |
| COMBUSTION_AIR_TEMPERATURE | 0.63% | 0.37% | -68.0% | -0.2858 | 1.331/0.751 | 🟢 NORMAL |
| MAIN_GAS_FLOW | 0.03% | 0.00% | 0.0% | -0.3592 | 1.432/0.698 | 🟢 NORMAL |
| MAIN_GAS_TEMPERATURE | 0.00% | 0.00% | 0.0% | -0.1769 | 1.194/0.838 | 🟢 NORMAL |
| INDIRECT_COOLING_WATER_FLOW | 0.00% | 0.00% | 0.0% | 0.8254 | 0.438/2.283 | 🟢 NORMAL |
| INDIRECT_WATER_MAIN_TEMPERATURE | 0.00% | 0.00% | 0.0% | 0.4151 | 0.660/1.514 | 🟢 NORMAL |

### 05_Stand_Torque (스탠드 토크)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| STAND_1_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7158 | 2.046/0.489 | 🟢 NORMAL |
| STAND_2_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7996 | 2.225/0.449 | 🟢 NORMAL |
| STAND_3_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7754 | 2.171/0.461 | 🟢 NORMAL |
| STAND_4_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6589 | 1.933/0.517 | 🟢 NORMAL |
| STAND_5_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7838 | 2.190/0.457 | 🟢 NORMAL |
| STAND_6_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7639 | 2.147/0.466 | 🟢 NORMAL |
| STAND_7_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.8091 | 2.246/0.445 | 🟢 NORMAL |
| STAND_8_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6826 | 1.979/0.505 | 🟢 NORMAL |
| STAND_9_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.8119 | 2.252/0.444 | 🟢 NORMAL |
| STAND_10_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7863 | 2.195/0.456 | 🟢 NORMAL |
| STAND_11_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.7094 | 2.033/0.492 | 🟢 NORMAL |
| STAND_12_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6264 | 1.871/0.535 | 🟢 NORMAL |
| STAND_13_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.8263 | 2.285/0.438 | 🟢 NORMAL |
| STAND_14_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.8624 | 2.369/0.422 | 🟢 NORMAL |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.3826 | 1.466/0.682 | 🟢 NORMAL |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.3829 | 1.467/0.682 | 🟢 NORMAL |

### 06_Stand_Speed (스탠드 속도)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| STAND_8_ACTUAL_SPEED | 19.18% | 16.00% | -19.9% | -0.2809 | 1.324/0.755 | 🔴 DANGER |
| STAND_11_ACTUAL_SPEED | 16.82% | 15.89% | -5.9% | -0.0824 | 1.086/0.921 | 🔴 DANGER |
| STAND_14_ACTUAL_SPEED | 15.81% | 15.81% | 0.0% | -0.0782 | 1.081/0.925 | 🔴 DANGER |
| STAND_10_ACTUAL_SPEED | 15.80% | 15.73% | -0.5% | 0.5877 | 0.556/1.800 | 🔴 DANGER |
| FINISHING_BLOCK_ACTUAL_SPEED | 15.79% | 37.91% | 58.3% | 0.9467 | 0.388/2.577 | 🔴 DANGER |
| STAND_12_ACTUAL_SPEED | 15.79% | 15.79% | 0.0% | -0.0712 | 1.074/0.931 | 🔴 DANGER |
| STAND_9_ACTUAL_SPEED | 15.62% | 15.62% | 0.0% | -0.0266 | 1.027/0.974 | 🔴 DANGER |
| STAND_4_ACTUAL_SPEED | 15.49% | 15.43% | -0.4% | 0.3098 | 0.734/1.363 | 🔴 DANGER |
| STAND_6_ACTUAL_SPEED | 15.49% | 15.44% | -0.3% | 0.4514 | 0.637/1.571 | 🔴 DANGER |
| STAND_13_ACTUAL_SPEED | 15.48% | 15.58% | 0.7% | -0.5926 | 1.809/0.553 | 🔴 DANGER |
| STAND_2_ACTUAL_SPEED | 15.45% | 15.48% | 0.2% | 0.1962 | 0.822/1.217 | 🔴 DANGER |
| STAND_7_ACTUAL_SPEED | 15.41% | 15.36% | -0.3% | 0.1984 | 0.820/1.219 | 🔴 DANGER |
| STAND_5_ACTUAL_SPEED | 15.40% | 15.37% | -0.2% | 0.1239 | 0.883/1.132 | 🔴 DANGER |
| STAND_1_ACTUAL_SPEED | 15.40% | 15.35% | -0.3% | 0.2191 | 0.803/1.245 | 🔴 DANGER |
| STAND_3_ACTUAL_SPEED | 15.32% | 15.34% | 0.1% | -0.1465 | 1.158/0.864 | 🔴 DANGER |

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
| PINCHROLL_2_ACTUAL_SPEED | 17.12% | 14.57% | -17.5% | -0.1153 | 1.122/0.891 | 🔴 DANGER |
| PINCHROLL_4_ACTUAL_TORQUE | 17.03% | 15.34% | -11.0% | 0.6003 | 0.549/1.823 | 🔴 DANGER |
| PINCHROLL_4_REFERENCE_TORQUE | 13.92% | 14.18% | 1.8% | 0.0874 | 0.916/1.091 | 🟠 WARNING |
| PINCHROLL_2_ACTUAL_TORQUE | 0.01% | 16.90% | 100.0% | -0.9998 | 2.718/0.368 | 🟢 NORMAL |
| PINCHROLL_4_ACTUAL_SPEED | 0.00% | 0.01% | 100.0% | -0.9330 | 2.542/0.393 | 🟢 NORMAL |
| PINCHROLL_3_ACTUAL_SPEED | 0.00% | 0.02% | 100.0% | -0.9071 | 2.477/0.404 | 🟢 NORMAL |
| PINCHROLL_3_ACTUAL_TORQUE | 0.00% | 0.00% | 0.0% | -0.6868 | 1.987/0.503 | 🟢 NORMAL |
| PINCHROLL_3_REFERENCE_TORQUE | 0.00% | 0.00% | 0.0% | 0.6539 | 0.520/1.923 | 🟢 NORMAL |

### 09_PR_Detailed (PR 상세 토크)

| 태그명 | Adj 이상치율 | Std 이상치율 | 개선율 | Bowley 왜도 | 승수 (L/U) | 위험등급 |
|--------|-------------|--------------|--------|-------------|------------|----------|
| [L1] PR7L1_ACT_TORQUE | 7.19% | 6.32% | -13.8% | -0.7760 | 2.173/0.460 | 🟡 CAUTION |
| [L2] PR7L2_ACT_TORQUE | 6.76% | 5.58% | -21.2% | -0.8977 | 2.454/0.408 | 🟡 CAUTION |
| [L1] PR6L1_ACT_TORQUE | 5.82% | 5.27% | -10.5% | -0.6020 | 1.826/0.548 | 🟡 CAUTION |
| [L1] PR9L1_ACT_TORQUE | 5.65% | 6.28% | 10.1% | -0.3516 | 1.421/0.704 | 🟡 CAUTION |
| [L1] PR8L1_ACT_TORQUE | 5.09% | 4.77% | -6.8% | -0.2393 | 1.270/0.787 | 🟡 CAUTION |
| [L2] PR6L2_ACT_TORQUE | 0.51% | 0.49% | -5.2% | -0.4823 | 1.620/0.617 | 🟢 NORMAL |

---

## 태그별 상세 분석 (위험도 순)


### 🔴 위험 (15~25%) - 18개 태그

#### FURNACE_O2_ANALYZER 🔴

**위험도**: [DANGER] | **이상치율**: 22.12% | **개선율**: 0.0%
**Bowley 왜도**: -0.1394 | **승수 (L/U)**: 1.150/0.870

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 4,455 | 4,456 |
| 이상치율 | 22.12% | 22.12% |
| 하한 경계 | 9.5076 | 9.5103 |
| 상한 경계 | 9.5546 | 9.5569 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 7.8815 |
| 표준편차 | 3.4013 |
| Q1 (25%) | 9.5277 |
| 중앙값 | 9.5344 |
| Q3 (75%) | 9.5394 |
| IQR | 0.0117 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 9.45 | 2.67% | 2.67% |
| 2025-06 | 5,758 | 9.26 | 7.02% | 7.02% |
| 2025-07 | 2,880 | 8.48 | 22.53% | 22.57% |
| 2025-08 | 4,316 | 3.02 | 74.37% | 74.37% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-11 | 2,314 |
| 2 | 2025-08-08 | 896 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-06 | 358 |
| 5 | 2025-07-05 | 234 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 2,314건 (2025-08-11)
- 평균 일별 이상치: 556.9건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted_FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted_FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted_FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted_FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted_FURNACE_O2_ANALYZER_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted_FURNACE_O2_ANALYZER_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted_FURNACE_O2_ANALYZER_07_daily_outlier_count.png)

**종합 분석 차트**

![FURNACE_O2_ANALYZER 종합 분석 차트](./04_Furnace_Auxiliary/adjusted_FURNACE_O2_ANALYZER_analysis.png)


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

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_O2_ANALYZER_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 9.2626 |
| 중앙값 | 9.5331 |
| IQR | 0.0057 |
| Bowley 왜도 | -0.1715 |
| Adj 이상치 수 | 410 |
| Adj 이상치율 | 7.12% |
| Std 이상치율 | 7.12% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 360건
- 2. 2025-06-12: 50건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_O2_ANALYZER_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 8.4764 |
| 중앙값 | 9.5296 |
| IQR | 0.0077 |
| Bowley 왜도 | -0.2157 |
| Adj 이상치 수 | 651 |
| Adj 이상치율 | 22.60% |
| Std 이상치율 | 22.60% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 416건
- 2. 2025-07-05: 235건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_O2_ANALYZER_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 3.0227 |
| 중앙값 | 0.4678 |
| IQR | 9.2180 |
| Bowley 왜도 | 0.9661 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_O2_ANALYZER_00_summary.png)

---

#### STAND_8_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 19.18% | **개선율**: -19.9%
**Bowley 왜도**: -0.2809 | **승수 (L/U)**: 1.324/0.755

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,791 | 3,163 |
| 이상치율 | 19.18% | 16.00% |
| 하한 경계 | 752.3738 | 802.0123 |
| 상한 경계 | 1172.6408 | 1210.1222 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 869.5171 |
| 표준편차 | 370.9368 |
| Q1 (25%) | 955.0535 |
| 중앙값 | 1020.3980 |
| Q3 (75%) | 1057.0810 |
| IQR | 102.0275 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 891.23 | 11.95% | 12.01% |
| 2025-06 | 5,678 | 893.03 | 11.18% | 11.22% |
| 2025-07 | 2,773 | 744.35 | 26.25% | 26.25% |
| 2025-08 | 4,201 | 883.60 | 37.56% | 22.47% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 1,276 |
| 2 | 2025-05-17 | 488 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 396 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 1,276건 (2025-08-08)
- 평균 일별 이상치: 473.9건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_8_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_8_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_8_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_8_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_8_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_8_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 893.0310 |
| 중앙값 | 968.5727 |
| IQR | 95.6577 |
| Bowley 왜도 | 0.6111 |
| Adj 이상치 수 | 642 |
| Adj 이상치율 | 11.31% |
| Std 이상치율 | 11.22% |
| 개선율 | -0.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 401건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_8_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 744.3504 |
| 중앙값 | 972.7760 |
| IQR | 1034.9990 |
| Bowley 왜도 | -0.8798 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_8_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 883.6030 |
| 중앙값 | 1073.6390 |
| IQR | 68.9430 |
| Bowley 왜도 | -0.2551 |
| Adj 이상치 수 | 1,514 |
| Adj 이상치율 | 36.04% |
| Std 이상치율 | 25.37% |
| 개선율 | -42.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 1,207건
- 2. 2025-08-11: 307건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_8_ACTUAL_SPEED_00_summary.png)

---

#### PINCHROLL_2_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 17.12% | **개선율**: -17.5%
**Bowley 왜도**: -0.1153 | **승수 (L/U)**: 1.122/0.891

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 2,797 | 2,380 |
| 이상치율 | 17.12% | 14.57% |
| 하한 경계 | -326.4390 | -325.2783 |
| 상한 경계 | -300.9749 | -299.9405 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | -313.5339 |
| 표준편차 | 11.6502 |
| Q1 (25%) | -315.7767 |
| 중앙값 | -312.2444 |
| Q3 (75%) | -309.4422 |
| IQR | 6.3345 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | -314.04 | 11.19% | 11.46% |
| 2025-06 | 4,896 | -315.23 | 23.47% | 14.20% |
| 2025-07 | 2,011 | -310.69 | 8.75% | 15.76% |
| 2025-08 | 3,273 | -311.80 | 23.92% | 20.23% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 779 |
| 2 | 2025-08-08 | 487 |
| 3 | 2025-06-12 | 370 |
| 4 | 2025-05-18 | 345 |
| 5 | 2025-05-17 | 344 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 779건 (2025-06-06)
- 평균 일별 이상치: 349.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_2_ACTUAL_SPEED 종합 분석 차트](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | -315.2283 |
| 중앙값 | -315.5386 |
| IQR | 6.3583 |
| Bowley 왜도 | 0.5693 |
| Adj 이상치 수 | 787 |
| Adj 이상치율 | 16.07% |
| Std 이상치율 | 24.61% |
| 개선율 | 34.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 442건
- 2. 2025-06-06: 345건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | -310.6855 |
| 중앙값 | -309.7892 |
| IQR | 7.9688 |
| Bowley 왜도 | 0.6407 |
| Adj 이상치 수 | 421 |
| Adj 이상치율 | 20.93% |
| Std 이상치율 | 16.66% |
| 개선율 | -25.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 259건
- 2. 2025-07-04: 162건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | -311.8043 |
| 중앙값 | -310.0126 |
| IQR | 5.5274 |
| Bowley 왜도 | 0.0386 |
| Adj 이상치 수 | 717 |
| Adj 이상치율 | 21.91% |
| Std 이상치율 | 22.03% |
| 개선율 | 0.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 373건
- 2. 2025-08-08: 344건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

---

#### PINCHROLL_4_ACTUAL_TORQUE 🔴

**위험도**: [DANGER] | **이상치율**: 17.03% | **개선율**: -11.0%
**Bowley 왜도**: 0.6003 | **승수 (L/U)**: 0.549/1.823

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 2,782 | 2,507 |
| 이상치율 | 17.03% | 15.34% |
| 하한 경계 | 18.3753 | 12.9331 |
| 상한 경계 | 55.0073 | 45.0883 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 26.0269 |
| 표준편차 | 10.0578 |
| Q1 (25%) | 24.9913 |
| 중앙값 | 26.5980 |
| Q3 (75%) | 33.0301 |
| IQR | 8.0388 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 25.73 | 14.05% | 12.29% |
| 2025-06 | 4,896 | 27.80 | 18.55% | 16.71% |
| 2025-07 | 2,011 | 25.50 | 23.12% | 21.63% |
| 2025-08 | 3,273 | 24.25 | 16.62% | 15.18% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 500 |
| 2 | 2025-05-17 | 436 |
| 3 | 2025-05-18 | 429 |
| 4 | 2025-06-06 | 408 |
| 5 | 2025-08-11 | 367 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 500건 (2025-06-12)
- 평균 일별 이상치: 347.8건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_4_ACTUAL_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 27.7982 |
| 중앙값 | 30.1557 |
| IQR | 5.0062 |
| Bowley 왜도 | 0.9331 |
| Adj 이상치 수 | 1,064 |
| Adj 이상치율 | 21.73% |
| Std 이상치율 | 20.14% |
| 개선율 | -7.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 580건
- 2. 2025-06-06: 484건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 25.5049 |
| 중앙값 | 26.6612 |
| IQR | 12.0942 |
| Bowley 왜도 | 0.3782 |
| Adj 이상치 수 | 424 |
| Adj 이상치율 | 21.08% |
| Std 이상치율 | 10.44% |
| 개선율 | -101.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 224건
- 2. 2025-07-04: 200건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 24.2486 |
| 중앙값 | 24.9950 |
| IQR | 4.3206 |
| Bowley 왜도 | -0.2690 |
| Adj 이상치 수 | 1,071 |
| Adj 이상치율 | 32.72% |
| Std 이상치율 | 33.12% |
| 개선율 | 1.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 734건
- 2. 2025-08-11: 337건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_11_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 16.82% | **개선율**: -5.9%
**Bowley 왜도**: -0.0824 | **승수 (L/U)**: 1.086/0.921

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,325 | 3,141 |
| 이상치율 | 16.82% | 15.89% |
| 하한 경계 | 952.9363 | 957.7300 |
| 상한 경계 | 1102.2113 | 1106.6260 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 879.7708 |
| 표준편차 | 377.3638 |
| Q1 (25%) | 1013.5660 |
| 중앙값 | 1033.7110 |
| Q3 (75%) | 1050.7900 |
| IQR | 37.2240 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 902.82 | 12.47% | 12.50% |
| 2025-06 | 5,678 | 948.19 | 14.86% | 11.64% |
| 2025-07 | 2,773 | 762.79 | 27.30% | 27.19% |
| 2025-08 | 4,201 | 825.49 | 19.92% | 19.92% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 582 |
| 2 | 2025-08-08 | 527 |
| 3 | 2025-05-17 | 499 |
| 4 | 2025-07-04 | 439 |
| 5 | 2025-05-18 | 388 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 582건 (2025-06-12)
- 평균 일별 이상치: 415.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_11_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_11_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_11_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_11_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_11_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_11_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 948.1922 |
| 중앙값 | 1064.3315 |
| IQR | 41.6923 |
| Bowley 왜도 | -0.0801 |
| Adj 이상치 수 | 661 |
| Adj 이상치율 | 11.64% |
| Std 이상치율 | 11.64% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 397건
- 2. 2025-06-06: 264건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_11_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 762.7905 |
| 중앙값 | 1037.4270 |
| IQR | 1042.9890 |
| Bowley 왜도 | -0.9893 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_11_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 825.4947 |
| 중앙값 | 1023.6830 |
| IQR | 40.2138 |
| Bowley 왜도 | -0.3333 |
| Adj 이상치 수 | 837 |
| Adj 이상치율 | 19.92% |
| Std 이상치율 | 19.92% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 310건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_11_ACTUAL_SPEED_00_summary.png)

---

#### STAND_14_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.81% | **개선율**: 0.0%
**Bowley 왜도**: -0.0782 | **승수 (L/U)**: 1.081/0.925

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,125 | 3,125 |
| 이상치율 | 15.81% | 15.81% |
| 하한 경계 | 1048.8489 | 1053.4413 |
| 상한 경계 | 1199.8361 | 1204.0832 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 958.9394 |
| 표준편차 | 411.7120 |
| Q1 (25%) | 1109.9320 |
| 중앙값 | 1130.2340 |
| Q3 (75%) | 1147.5925 |
| IQR | 37.6605 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 1001.29 | 12.50% | 12.50% |
| 2025-06 | 5,678 | 1018.59 | 11.62% | 11.62% |
| 2025-07 | 2,773 | 819.06 | 26.54% | 26.54% |
| 2025-08 | 4,201 | 898.97 | 20.00% | 20.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 527 |
| 2 | 2025-05-17 | 497 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 398 |
| 5 | 2025-05-18 | 392 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 527건 (2025-08-08)
- 평균 일별 이상치: 390.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_14_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_14_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_14_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_14_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_14_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_14_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 1018.5901 |
| 중앙값 | 1152.7335 |
| IQR | 44.5452 |
| Bowley 왜도 | -0.7827 |
| Adj 이상치 수 | 651 |
| Adj 이상치율 | 11.47% |
| Std 이상치율 | 11.62% |
| 개선율 | 1.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 392건
- 2. 2025-06-06: 259건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_14_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 819.0585 |
| 중앙값 | 1109.0380 |
| IQR | 1135.5060 |
| Bowley 왜도 | -0.9534 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_14_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 898.9688 |
| 중앙값 | 1112.1530 |
| IQR | 36.3320 |
| Bowley 왜도 | -0.1037 |
| Adj 이상치 수 | 839 |
| Adj 이상치율 | 19.97% |
| Std 이상치율 | 19.97% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 312건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_14_ACTUAL_SPEED_00_summary.png)

---

#### STAND_10_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.80% | **개선율**: -0.5%
**Bowley 왜도**: 0.5877 | **승수 (L/U)**: 0.556/1.800

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,122 | 3,108 |
| 이상치율 | 15.80% | 15.73% |
| 하한 경계 | 875.5106 | 826.8251 |
| 상한 경계 | 1206.6050 | 1118.9817 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 824.0268 |
| 표준편차 | 353.2441 |
| Q1 (25%) | 936.3838 |
| 중앙값 | 951.4421 |
| Q3 (75%) | 1009.4230 |
| IQR | 73.0392 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 856.81 | 12.50% | 12.40% |
| 2025-06 | 5,678 | 871.90 | 11.61% | 11.52% |
| 2025-07 | 2,773 | 716.53 | 26.54% | 26.54% |
| 2025-08 | 4,201 | 774.78 | 19.95% | 19.90% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 528 |
| 2 | 2025-05-17 | 499 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 399 |
| 5 | 2025-05-18 | 390 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 528건 (2025-08-08)
- 평균 일별 이상치: 390.2건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_10_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_10_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_10_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_10_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_10_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_10_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 871.9024 |
| 중앙값 | 964.1385 |
| IQR | 74.0708 |
| Bowley 왜도 | 0.3995 |
| Adj 이상치 수 | 659 |
| Adj 이상치율 | 11.61% |
| Std 이상치율 | 11.52% |
| 개선율 | -0.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 399건
- 2. 2025-06-06: 260건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_10_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 716.5279 |
| 중앙값 | 949.6066 |
| IQR | 994.6941 |
| Bowley 왜도 | -0.9093 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_10_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 774.7828 |
| 중앙값 | 949.1406 |
| IQR | 64.4250 |
| Bowley 왜도 | -0.2314 |
| Adj 이상치 수 | 845 |
| Adj 이상치율 | 20.11% |
| Std 이상치율 | 19.90% |
| 개선율 | -1.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 536건
- 2. 2025-08-11: 309건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_10_ACTUAL_SPEED_00_summary.png)

---

#### FINISHING_BLOCK_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.79% | **개선율**: 58.3%
**Bowley 왜도**: 0.9467 | **승수 (L/U)**: 0.388/2.577

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,121 | 7,492 |
| 이상치율 | 15.79% | 37.91% |
| 하한 경계 | 916.5285 | 905.5716 |
| 상한 경계 | 981.5534 | 953.3164 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 795.0645 |
| 표준편차 | 334.2869 |
| Q1 (25%) | 923.4759 |
| 중앙값 | 923.7942 |
| Q3 (75%) | 935.4121 |
| IQR | 11.9362 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 832.17 | 12.35% | 51.43% |
| 2025-06 | 5,678 | 828.32 | 12.43% | 39.08% |
| 2025-07 | 2,773 | 697.33 | 25.17% | 28.02% |
| 2025-08 | 4,201 | 751.82 | 19.97% | 19.97% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 525 |
| 2 | 2025-05-17 | 499 |
| 3 | 2025-06-12 | 437 |
| 4 | 2025-07-04 | 394 |
| 5 | 2025-05-18 | 379 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 525건 (2025-08-08)
- 평균 일별 이상치: 390.1건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 828.3170 |
| 중앙값 | 923.5914 |
| IQR | 42.3976 |
| Bowley 왜도 | 0.9770 |
| Adj 이상치 수 | 701 |
| Adj 이상치율 | 12.35% |
| Std 이상치율 | 12.21% |
| 개선율 | -1.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 434건
- 2. 2025-06-06: 267건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 697.3303 |
| 중앙값 | 923.1473 |
| IQR | 94.1436 |
| Bowley 왜도 | -0.9893 |
| Adj 이상치 수 | 687 |
| Adj 이상치율 | 24.77% |
| Std 이상치율 | 24.85% |
| 개선율 | 0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 392건
- 2. 2025-07-05: 295건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 751.8221 |
| 중앙값 | 932.0640 |
| IQR | 2.2436 |
| Bowley 왜도 | 0.6351 |
| Adj 이상치 수 | 1,125 |
| Adj 이상치율 | 26.78% |
| Std 이상치율 | 31.92% |
| 개선율 | 16.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 599건
- 2. 2025-08-08: 526건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

---

#### STAND_12_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.79% | **개선율**: 0.0%
**Bowley 왜도**: -0.0712 | **승수 (L/U)**: 1.074/0.931

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,120 | 3,120 |
| 이상치율 | 15.79% | 15.79% |
| 하한 경계 | 972.0567 | 976.1875 |
| 상한 경계 | 1121.6166 | 1125.4635 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 892.6333 |
| 표준편차 | 383.9130 |
| Q1 (25%) | 1032.1660 |
| 중앙값 | 1052.1540 |
| Q3 (75%) | 1069.4850 |
| IQR | 37.3190 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 930.93 | 12.45% | 12.45% |
| 2025-06 | 5,678 | 942.42 | 11.66% | 11.66% |
| 2025-07 | 2,773 | 756.54 | 26.54% | 26.54% |
| 2025-08 | 4,201 | 850.35 | 19.92% | 19.92% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 527 |
| 2 | 2025-05-17 | 497 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 398 |
| 5 | 2025-05-18 | 388 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 527건 (2025-08-08)
- 평균 일별 이상치: 390.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_12_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_12_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_12_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_12_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_12_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_12_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 942.4231 |
| 중앙값 | 1061.4690 |
| IQR | 35.4980 |
| Bowley 왜도 | -0.0706 |
| Adj 이상치 수 | 662 |
| Adj 이상치율 | 11.66% |
| Std 이상치율 | 11.66% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 398건
- 2. 2025-06-06: 264건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_12_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 756.5428 |
| 중앙값 | 1014.3610 |
| IQR | 1053.0490 |
| Bowley 왜도 | -0.9265 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_12_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 850.3496 |
| 중앙값 | 1048.1750 |
| IQR | 41.5860 |
| Bowley 왜도 | -0.0372 |
| Adj 이상치 수 | 837 |
| Adj 이상치율 | 19.92% |
| Std 이상치율 | 19.92% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 310건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_12_ACTUAL_SPEED_00_summary.png)

---

#### STAND_9_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.62% | **개선율**: 0.0%
**Bowley 왜도**: -0.0266 | **승수 (L/U)**: 1.027/0.974

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,087 | 3,087 |
| 이상치율 | 15.62% | 15.62% |
| 하한 경계 | 693.6833 | 698.8151 |
| 상한 경계 | 1202.2257 | 1207.2229 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 824.8073 |
| 표준편차 | 355.3895 |
| Q1 (25%) | 889.4680 |
| 중앙값 | 954.7070 |
| Q3 (75%) | 1016.5700 |
| IQR | 127.1020 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 865.77 | 12.30% | 12.30% |
| 2025-06 | 5,678 | 844.61 | 11.39% | 11.39% |
| 2025-07 | 2,773 | 684.61 | 26.54% | 26.54% |
| 2025-08 | 4,201 | 821.24 | 19.73% | 19.73% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 523 |
| 2 | 2025-05-17 | 495 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 392 |
| 5 | 2025-05-18 | 380 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 523건 (2025-08-08)
- 평균 일별 이상치: 385.9건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_9_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_9_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_9_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_9_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_9_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_9_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 844.6066 |
| 중앙값 | 899.6547 |
| IQR | 129.8719 |
| Bowley 왜도 | 0.7297 |
| Adj 이상치 수 | 656 |
| Adj 이상치율 | 11.55% |
| Std 이상치율 | 11.39% |
| 개선율 | -1.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 398건
- 2. 2025-06-06: 258건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_9_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 684.6129 |
| 중앙값 | 902.6964 |
| IQR | 951.6205 |
| Bowley 왜도 | -0.8972 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_9_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 821.2414 |
| 중앙값 | 1003.5090 |
| IQR | 65.8762 |
| Bowley 왜도 | -0.2544 |
| Adj 이상치 수 | 959 |
| Adj 이상치율 | 22.83% |
| Std 이상치율 | 20.30% |
| 개선율 | -12.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 650건
- 2. 2025-08-11: 309건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_9_ACTUAL_SPEED_00_summary.png)

---

#### STAND_4_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.49% | **개선율**: -0.4%
**Bowley 왜도**: 0.3098 | **승수 (L/U)**: 0.734/1.363

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,061 | 3,050 |
| 이상치율 | 15.49% | 15.43% |
| 하한 경계 | 644.9222 | 611.7035 |
| 상한 경계 | 989.5055 | 944.2237 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 664.1643 |
| 표준편차 | 282.2945 |
| Q1 (25%) | 736.3986 |
| 중앙값 | 765.0871 |
| Q3 (75%) | 819.5286 |
| IQR | 83.1300 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 702.00 | 12.02% | 12.00% |
| 2025-06 | 5,678 | 695.77 | 11.31% | 11.29% |
| 2025-07 | 2,773 | 579.80 | 26.29% | 26.25% |
| 2025-08 | 4,201 | 613.10 | 19.88% | 19.71% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 528 |
| 2 | 2025-05-17 | 490 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 401 |
| 5 | 2025-05-18 | 365 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 528건 (2025-08-08)
- 평균 일별 이상치: 382.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_4_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_4_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_4_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_4_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_4_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_4_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 695.7699 |
| 중앙값 | 750.0693 |
| IQR | 84.1129 |
| Bowley 왜도 | 0.6650 |
| Adj 이상치 수 | 644 |
| Adj 이상치율 | 11.34% |
| Std 이상치율 | 11.29% |
| 개선율 | -0.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 403건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_4_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 579.7980 |
| 중앙값 | 750.5014 |
| IQR | 807.5416 |
| Bowley 왜도 | -0.8587 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_4_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 613.0981 |
| 중앙값 | 746.2508 |
| IQR | 49.7644 |
| Bowley 왜도 | -0.2500 |
| Adj 이상치 수 | 1,192 |
| Adj 이상치율 | 28.37% |
| Std 이상치율 | 20.11% |
| 개선율 | -41.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 887건
- 2. 2025-08-11: 305건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_4_ACTUAL_SPEED_00_summary.png)

---

#### STAND_6_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.49% | **개선율**: -0.3%
**Bowley 왜도**: 0.4514 | **승수 (L/U)**: 0.637/1.571

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,061 | 3,051 |
| 이상치율 | 15.49% | 15.44% |
| 하한 경계 | 957.7656 | 898.6658 |
| 상한 경계 | 1425.3178 | 1332.4997 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 949.0193 |
| 표준편차 | 403.1088 |
| Q1 (25%) | 1061.3535 |
| 중앙값 | 1091.1030 |
| Q3 (75%) | 1169.8120 |
| IQR | 108.4585 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 986.77 | 12.04% | 12.01% |
| 2025-06 | 5,678 | 1015.88 | 11.31% | 11.18% |
| 2025-07 | 2,773 | 841.15 | 26.25% | 26.25% |
| 2025-08 | 4,201 | 865.97 | 19.88% | 19.85% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 528 |
| 2 | 2025-05-17 | 491 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 401 |
| 5 | 2025-05-18 | 365 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 528건 (2025-08-08)
- 평균 일별 이상치: 382.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_6_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_6_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_6_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_6_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_6_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_6_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 1015.8765 |
| 중앙값 | 1110.2590 |
| IQR | 87.2818 |
| Bowley 왜도 | 0.6273 |
| Adj 이상치 수 | 642 |
| Adj 이상치율 | 11.31% |
| Std 이상치율 | 11.31% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 401건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_6_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 841.1498 |
| 중앙값 | 1091.6000 |
| IQR | 1170.2710 |
| Bowley 왜도 | -0.8656 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_6_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 865.9663 |
| 중앙값 | 1053.7160 |
| IQR | 62.1430 |
| Bowley 왜도 | -0.1434 |
| Adj 이상치 수 | 1,107 |
| Adj 이상치율 | 26.35% |
| Std 이상치율 | 22.11% |
| 개선율 | -19.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 800건
- 2. 2025-08-11: 307건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_6_ACTUAL_SPEED_00_summary.png)

---

#### STAND_13_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.48% | **개선율**: 0.7%
**Bowley 왜도**: -0.5926 | **승수 (L/U)**: 1.809/0.553

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,059 | 3,080 |
| 이상치율 | 15.48% | 15.58% |
| 하한 경계 | 553.2630 | 723.3890 |
| 상한 경계 | 1190.2837 | 1284.3410 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 869.2221 |
| 표준편차 | 374.3231 |
| Q1 (25%) | 933.7460 |
| 중앙값 | 1045.4200 |
| Q3 (75%) | 1073.9840 |
| IQR | 140.2380 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 936.16 | 12.09% | 12.19% |
| 2025-06 | 5,678 | 952.32 | 11.27% | 11.36% |
| 2025-07 | 2,773 | 688.84 | 26.51% | 26.54% |
| 2025-08 | 4,201 | 762.68 | 19.61% | 19.80% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 523 |
| 2 | 2025-05-17 | 487 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 386 |
| 5 | 2025-05-18 | 373 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 523건 (2025-08-08)
- 평균 일별 이상치: 382.4건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_13_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_13_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_13_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_13_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_13_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_13_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 952.3218 |
| 중앙값 | 1072.6225 |
| IQR | 44.2022 |
| Bowley 왜도 | -0.3928 |
| Adj 이상치 수 | 657 |
| Adj 이상치율 | 11.57% |
| Std 이상치율 | 11.59% |
| 개선율 | 0.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 396건
- 2. 2025-06-06: 261건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_13_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 688.8379 |
| 중앙값 | 923.3658 |
| IQR | 949.5346 |
| Bowley 왜도 | -0.9449 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_13_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 762.6759 |
| 중앙값 | 936.8420 |
| IQR | 30.7067 |
| Bowley 왜도 | 0.3555 |
| Adj 이상치 수 | 838 |
| Adj 이상치율 | 19.95% |
| Std 이상치율 | 19.95% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 311건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_13_ACTUAL_SPEED_00_summary.png)

---

#### STAND_2_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.45% | **개선율**: 0.2%
**Bowley 왜도**: 0.1962 | **승수 (L/U)**: 0.822/1.217

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,053 | 3,060 |
| 이상치율 | 15.45% | 15.48% |
| 하한 경계 | 448.3222 | 429.1077 |
| 상한 경계 | 740.1276 | 716.7485 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 498.6576 |
| 표준편차 | 213.6638 |
| Q1 (25%) | 536.9730 |
| 중앙값 | 565.8745 |
| Q3 (75%) | 608.8832 |
| IQR | 71.9102 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 516.66 | 11.98% | 11.94% |
| 2025-06 | 5,678 | 523.09 | 11.27% | 11.17% |
| 2025-07 | 2,773 | 490.38 | 26.25% | 27.01% |
| 2025-08 | 4,201 | 440.64 | 19.83% | 19.71% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 527 |
| 2 | 2025-05-17 | 487 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 400 |
| 5 | 2025-05-18 | 365 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 527건 (2025-08-08)
- 평균 일별 이상치: 381.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_2_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_2_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_2_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_2_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_2_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_2_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 523.0868 |
| 중앙값 | 573.1510 |
| IQR | 47.2315 |
| Bowley 왜도 | 0.4880 |
| Adj 이상치 수 | 646 |
| Adj 이상치율 | 11.38% |
| Std 이상치율 | 11.29% |
| 개선율 | -0.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 403건
- 2. 2025-06-06: 243건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_2_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 490.3817 |
| 중앙값 | 635.5304 |
| IQR | 682.6834 |
| Bowley 왜도 | -0.8619 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_2_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 440.6372 |
| 중앙값 | 534.7484 |
| IQR | 35.5353 |
| Bowley 왜도 | -0.2234 |
| Adj 이상치 수 | 1,566 |
| Adj 이상치율 | 37.28% |
| Std 이상치율 | 24.88% |
| 개선율 | -49.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 1,260건
- 2. 2025-08-11: 306건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_2_ACTUAL_SPEED_00_summary.png)

---

#### STAND_7_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.41% | **개선율**: -0.3%
**Bowley 왜도**: 0.1984 | **승수 (L/U)**: 0.820/1.219

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,045 | 3,035 |
| 이상치율 | 15.41% | 15.36% |
| 하한 경계 | 903.9629 | 858.6675 |
| 상한 경계 | 1585.1854 | 1529.9515 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 1020.8515 |
| 표준편차 | 435.8140 |
| Q1 (25%) | 1110.3990 |
| 중앙값 | 1177.6640 |
| Q3 (75%) | 1278.2200 |
| IQR | 167.8210 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 1091.92 | 11.95% | 11.95% |
| 2025-06 | 5,678 | 1082.43 | 11.18% | 11.11% |
| 2025-07 | 2,773 | 888.97 | 26.25% | 26.25% |
| 2025-08 | 4,201 | 904.39 | 19.80% | 19.66% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 525 |
| 2 | 2025-05-17 | 488 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 396 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 525건 (2025-08-08)
- 평균 일별 이상치: 380.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_7_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_7_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_7_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_7_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_7_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_7_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 1082.4253 |
| 중앙값 | 1153.2355 |
| IQR | 150.3560 |
| Bowley 왜도 | 0.7575 |
| Adj 이상치 수 | 642 |
| Adj 이상치율 | 11.31% |
| Std 이상치율 | 11.18% |
| 개선율 | -1.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 401건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_7_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 888.9665 |
| 중앙값 | 1159.3990 |
| IQR | 1233.3430 |
| Bowley 왜도 | -0.8801 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_7_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 904.3880 |
| 중앙값 | 1103.2800 |
| IQR | 71.3620 |
| Bowley 왜도 | -0.2113 |
| Adj 이상치 수 | 1,014 |
| Adj 이상치율 | 24.14% |
| Std 이상치율 | 20.45% |
| 개선율 | -18.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 707건
- 2. 2025-08-11: 307건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_7_ACTUAL_SPEED_00_summary.png)

---

#### STAND_5_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.40% | **개선율**: -0.2%
**Bowley 왜도**: 0.1239 | **승수 (L/U)**: 0.883/1.132

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,044 | 3,037 |
| 이상치율 | 15.40% | 15.37% |
| 하한 경계 | 878.1778 | 853.0540 |
| 상한 경계 | 1456.5150 | 1428.0780 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 980.2517 |
| 표준편차 | 417.3341 |
| Q1 (25%) | 1068.6880 |
| 중앙값 | 1131.6620 |
| Q3 (75%) | 1212.4440 |
| IQR | 143.7560 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 1038.91 | 11.95% | 11.95% |
| 2025-06 | 5,678 | 1038.42 | 11.22% | 11.11% |
| 2025-07 | 2,773 | 882.25 | 26.25% | 26.25% |
| 2025-08 | 4,201 | 867.03 | 19.73% | 19.71% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 526 |
| 2 | 2025-05-17 | 488 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 396 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 526건 (2025-08-08)
- 평균 일별 이상치: 380.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_5_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_5_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_5_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_5_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_5_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_5_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 1038.4182 |
| 중앙값 | 1131.6770 |
| IQR | 92.0940 |
| Bowley 왜도 | 0.6502 |
| Adj 이상치 수 | 642 |
| Adj 이상치율 | 11.31% |
| Std 이상치율 | 11.31% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 401건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_5_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 882.2458 |
| 중앙값 | 1141.9140 |
| IQR | 1227.5910 |
| Bowley 왜도 | -0.8604 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_5_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 867.0317 |
| 중앙값 | 1057.1540 |
| IQR | 65.5220 |
| Bowley 왜도 | -0.1972 |
| Adj 이상치 수 | 1,024 |
| Adj 이상치율 | 24.38% |
| Std 이상치율 | 20.07% |
| 개선율 | -21.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 721건
- 2. 2025-08-11: 303건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_5_ACTUAL_SPEED_00_summary.png)

---

#### STAND_1_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.40% | **개선율**: -0.3%
**Bowley 왜도**: 0.2191 | **승수 (L/U)**: 0.803/1.245

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,043 | 3,033 |
| 이상치율 | 15.40% | 15.35% |
| 하한 경계 | 407.1732 | 383.0989 |
| 상한 경계 | 739.3980 | 709.4277 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 473.4445 |
| 표준편차 | 203.5734 |
| Q1 (25%) | 505.4722 |
| 중앙값 | 537.3275 |
| Q3 (75%) | 587.0544 |
| IQR | 81.5822 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 535.43 | 11.93% | 11.90% |
| 2025-06 | 5,678 | 466.54 | 11.27% | 11.17% |
| 2025-07 | 2,773 | 407.15 | 26.25% | 26.25% |
| 2025-08 | 4,201 | 421.61 | 19.69% | 19.64% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 526 |
| 2 | 2025-05-17 | 486 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 400 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 526건 (2025-08-08)
- 평균 일별 이상치: 380.4건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_1_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_1_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_1_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_1_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_1_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_1_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 466.5386 |
| 중앙값 | 521.2025 |
| IQR | 32.3747 |
| Bowley 왜도 | -0.0439 |
| Adj 이상치 수 | 646 |
| Adj 이상치율 | 11.38% |
| Std 이상치율 | 11.38% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 403건
- 2. 2025-06-06: 243건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_1_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 407.1533 |
| 중앙값 | 538.1027 |
| IQR | 563.4023 |
| Bowley 왜도 | -0.9102 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_1_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 421.6139 |
| 중앙값 | 512.9676 |
| IQR | 41.5158 |
| Bowley 왜도 | -0.1027 |
| Adj 이상치 수 | 833 |
| Adj 이상치율 | 19.83% |
| Std 이상치율 | 19.83% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 306건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_1_ACTUAL_SPEED_00_summary.png)

---

#### STAND_3_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.32% | **개선율**: 0.1%
**Bowley 왜도**: -0.1465 | **승수 (L/U)**: 1.158/0.864

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 3,027 | 3,031 |
| 이상치율 | 15.32% | 15.34% |
| 하한 경계 | 540.6883 | 565.1617 |
| 상한 경계 | 957.5979 | 978.7358 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 671.6214 |
| 표준편차 | 286.4367 |
| Q1 (25%) | 720.2520 |
| 중앙값 | 779.5235 |
| Q3 (75%) | 823.6455 |
| IQR | 103.3935 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 697.05 | 11.94% | 11.94% |
| 2025-06 | 5,678 | 728.45 | 11.06% | 11.06% |
| 2025-07 | 2,773 | 613.87 | 26.25% | 26.25% |
| 2025-08 | 4,201 | 589.90 | 19.57% | 19.66% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 523 |
| 2 | 2025-05-17 | 487 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 391 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 523건 (2025-08-08)
- 평균 일별 이상치: 378.4건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/adjusted_STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/adjusted_STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/adjusted_STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/adjusted_STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/adjusted_STAND_3_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/adjusted_STAND_3_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/adjusted_STAND_3_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_3_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/adjusted_STAND_3_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/adjusted_STAND_3_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 728.4465 |
| 중앙값 | 798.0794 |
| IQR | 66.5070 |
| Bowley 왜도 | 0.4898 |
| Adj 이상치 수 | 644 |
| Adj 이상치율 | 11.34% |
| Std 이상치율 | 11.31% |
| 개선율 | -0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 403건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/adjusted_STAND_3_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 613.8674 |
| 중앙값 | 794.4805 |
| IQR | 855.5583 |
| Bowley 왜도 | -0.8572 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/adjusted_STAND_3_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 589.8959 |
| 중앙값 | 715.4424 |
| IQR | 52.6269 |
| Bowley 왜도 | -0.1916 |
| Adj 이상치 수 | 1,041 |
| Adj 이상치율 | 24.78% |
| Std 이상치율 | 20.38% |
| 개선율 | -21.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 741건
- 2. 2025-08-11: 300건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/adjusted_STAND_3_ACTUAL_SPEED_00_summary.png)

---


### 🟠 경고 (10~15%) - 1개 태그

#### PINCHROLL_4_REFERENCE_TORQUE 🟠

**위험도**: [WARNING] | **이상치율**: 13.92% | **개선율**: 1.8%
**Bowley 왜도**: 0.0874 | **승수 (L/U)**: 0.916/1.091

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 2,274 | 2,316 |
| 이상치율 | 13.92% | 14.18% |
| 하한 경계 | 1.2307 | -1.0842 |
| 상한 경계 | 75.2221 | 72.6958 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 43.0513 |
| 표준편차 | 23.5949 |
| Q1 (25%) | 26.5833 |
| 중앙값 | 35.0000 |
| Q3 (75%) | 45.0283 |
| IQR | 18.4450 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 40.98 | 11.32% | 11.43% |
| 2025-06 | 4,896 | 46.33 | 15.20% | 15.65% |
| 2025-07 | 2,011 | 46.09 | 19.05% | 19.19% |
| 2025-08 | 3,273 | 40.17 | 13.75% | 14.05% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 400 |
| 2 | 2025-05-18 | 359 |
| 3 | 2025-06-06 | 344 |
| 4 | 2025-05-17 | 338 |
| 5 | 2025-08-11 | 295 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 400건 (2025-06-12)
- 평균 일별 이상치: 284.2건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted_PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted_PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted_PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted_PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted_PINCHROLL_4_REFERENCE_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted_PINCHROLL_4_REFERENCE_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted_PINCHROLL_4_REFERENCE_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_4_REFERENCE_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted_PINCHROLL_4_REFERENCE_TORQUE_analysis.png)


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

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 46.3329 |
| 중앙값 | 39.9700 |
| IQR | 15.5042 |
| Bowley 왜도 | -0.2861 |
| Adj 이상치 수 | 862 |
| Adj 이상치율 | 17.61% |
| Std 이상치율 | 16.42% |
| 개선율 | -7.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 452건
- 2. 2025-06-06: 410건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 46.0904 |
| 중앙값 | 35.0000 |
| IQR | 9.2458 |
| Bowley 왜도 | 0.4317 |
| Adj 이상치 수 | 423 |
| Adj 이상치율 | 21.03% |
| Std 이상치율 | 22.08% |
| 개선율 | 4.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 220건
- 2. 2025-07-04: 203건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 40.1674 |
| 중앙값 | 26.5875 |
| IQR | 15.0000 |
| Bowley 왜도 | 0.7883 |
| Adj 이상치 수 | 403 |
| Adj 이상치율 | 12.31% |
| Std 이상치율 | 15.12% |
| 개선율 | 18.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 271건
- 2. 2025-08-08: 132건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

---


### 🟡 주의 (5~10%) - 7개 태그

#### MAIN_COMBUSTION_AIR_PRESSURE 🟡

**위험도**: [CAUTION] | **이상치율**: 8.95% | **개선율**: 0.1%
**Bowley 왜도**: 0.0641 | **승수 (L/U)**: 0.938/1.066

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,802 | 1,803 |
| 이상치율 | 8.95% | 8.95% |
| 하한 경계 | 1150.5740 | 1150.3270 |
| 상한 경계 | 1161.2003 | 1160.9370 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1148.8956 |
| 표준편차 | 37.3498 |
| Q1 (25%) | 1154.3057 |
| 중앙값 | 1155.5470 |
| Q3 (75%) | 1156.9583 |
| IQR | 2.6525 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1155.94 | 1.93% | 1.82% |
| 2025-06 | 5,758 | 1155.54 | 6.46% | 6.56% |
| 2025-07 | 2,880 | 1136.65 | 25.07% | 25.17% |
| 2025-08 | 4,316 | 1136.48 | 13.18% | 13.18% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 600 |
| 2 | 2025-08-08 | 513 |
| 3 | 2025-06-06 | 240 |
| 4 | 2025-06-12 | 132 |
| 5 | 2025-07-05 | 122 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 600건 (2025-07-04)
- 평균 일별 이상치: 225.2건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_COMBUSTION_AIR_PRESSURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_analysis.png)


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

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1155.5369 |
| 중앙값 | 1155.6010 |
| IQR | 2.8895 |
| Bowley 왜도 | 0.1234 |
| Adj 이상치 수 | 336 |
| Adj 이상치율 | 5.84% |
| Std 이상치율 | 5.90% |
| 개선율 | 1.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 220건
- 2. 2025-06-12: 116건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1136.6476 |
| 중앙값 | 1154.8495 |
| IQR | 5.2365 |
| Bowley 왜도 | -0.2963 |
| Adj 이상치 수 | 523 |
| Adj 이상치율 | 18.16% |
| Std 이상치율 | 19.90% |
| 개선율 | 8.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 466건
- 2. 2025-07-05: 57건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1136.4752 |
| 중앙값 | 1155.3860 |
| IQR | 2.7033 |
| Bowley 왜도 | 0.0086 |
| Adj 이상치 수 | 562 |
| Adj 이상치율 | 13.02% |
| Std 이상치율 | 13.02% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 510건
- 2. 2025-08-11: 52건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

---

#### FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE 🟡

**위험도**: [CAUTION] | **이상치율**: 8.33% | **개선율**: 0.1%
**Bowley 왜도**: -0.0312 | **승수 (L/U)**: 1.032/0.969

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,678 | 1,680 |
| 이상치율 | 8.33% | 8.34% |
| 하한 경계 | 686.9498 | 695.1997 |
| 상한 경계 | 1380.3736 | 1388.3698 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 963.7951 |
| 표준편차 | 307.2609 |
| Q1 (25%) | 955.1385 |
| 중앙값 | 1044.4920 |
| Q3 (75%) | 1128.4310 |
| IQR | 173.2925 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 887.08 | 7.13% | 7.13% |
| 2025-06 | 5,758 | 1049.14 | 6.88% | 6.91% |
| 2025-07 | 2,880 | 921.20 | 17.53% | 17.53% |
| 2025-08 | 4,316 | 1006.17 | 6.12% | 6.12% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 433 |
| 2 | 2025-05-18 | 339 |
| 3 | 2025-06-06 | 224 |
| 4 | 2025-08-11 | 206 |
| 5 | 2025-05-17 | 174 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 433건 (2025-07-04)
- 평균 일별 이상치: 209.8건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./03_Furnace_Discharge_Temperature/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE 종합 분석 차트](./03_Furnace_Discharge_Temperature/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_analysis.png)


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

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-05/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1049.1379 |
| 중앙값 | 1130.4620 |
| IQR | 85.2920 |
| Bowley 왜도 | -0.0952 |
| Adj 이상치 수 | 492 |
| Adj 이상치율 | 8.54% |
| Std 이상치율 | 8.65% |
| 개선율 | 1.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 270건
- 2. 2025-06-12: 222건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-06/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 921.2009 |
| 중앙값 | 1132.8305 |
| IQR | 102.8920 |
| Bowley 왜도 | -0.6645 |
| Adj 이상치 수 | 506 |
| Adj 이상치율 | 17.57% |
| Std 이상치율 | 17.57% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 433건
- 2. 2025-07-05: 73건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-07/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1006.1679 |
| 중앙값 | 1070.8920 |
| IQR | 96.8000 |
| Bowley 왜도 | -0.0769 |
| Adj 이상치 수 | 269 |
| Adj 이상치율 | 6.23% |
| Std 이상치율 | 6.23% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 206건
- 2. 2025-08-08: 63건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-08/adjusted_FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

---

#### [L1] PR7L1_ACT_TORQUE 🟡

**위험도**: [CAUTION] | **이상치율**: 7.19% | **개선율**: -13.8%
**Bowley 왜도**: -0.7760 | **승수 (L/U)**: 2.173/0.460

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,421 | 1,249 |
| 이상치율 | 7.19% | 6.32% |
| 하한 경계 | -15.9524 | -7.3420 |
| 상한 경계 | 8.2738 | 12.2367 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 3.9502 |
| 표준편차 | 5.4160 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.3465 |
| Q3 (75%) | 4.8947 |
| IQR | 4.8947 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 2.30 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 4.20 | 8.31% | 7.50% |
| 2025-07 | 2,773 | 6.71 | 20.81% | 18.21% |
| 2025-08 | 4,201 | 4.58 | 8.86% | 7.57% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 472 |
| 2 | 2025-07-04 | 449 |
| 3 | 2025-08-08 | 372 |
| 4 | 2025-07-05 | 128 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 472건 (2025-06-06)
- 평균 일별 이상치: 355.2건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted_PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted_PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted_PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted_PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted_PR7L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted_PR7L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted_PR7L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR7L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted_PR7L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 2.3025 |
| 중앙값 | 4.3369 |
| IQR | 4.5345 |
| Bowley 왜도 | -0.9129 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.01% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L1_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 4.2039 |
| 중앙값 | 4.3221 |
| IQR | 4.4950 |
| Bowley 왜도 | -0.9230 |
| Adj 이상치 수 | 492 |
| Adj 이상치율 | 8.67% |
| Std 이상치율 | 7.85% |
| 개선율 | -10.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 492건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 6.7072 |
| 중앙값 | 4.6025 |
| IQR | 5.4111 |
| Bowley 왜도 | -0.7011 |
| Adj 이상치 수 | 552 |
| Adj 이상치율 | 19.91% |
| Std 이상치율 | 17.35% |
| 개선율 | -14.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 427건
- 2. 2025-07-05: 125건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 4.5762 |
| 중앙값 | 5.0547 |
| IQR | 5.1289 |
| Bowley 왜도 | -0.9711 |
| Adj 이상치 수 | 375 |
| Adj 이상치율 | 8.93% |
| Std 이상치율 | 7.40% |
| 개선율 | -20.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 373건
- 2. 2025-08-11: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L1_ACT_TORQUE_00_summary.png)

---

#### [L2] PR7L2_ACT_TORQUE 🟡

**위험도**: [CAUTION] | **이상치율**: 6.76% | **개선율**: -21.2%
**Bowley 왜도**: -0.8977 | **승수 (L/U)**: 2.454/0.408

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,336 | 1,102 |
| 이상치율 | 6.76% | 5.58% |
| 하한 경계 | -22.4585 | -9.1523 |
| 상한 경계 | 9.8313 | 15.2538 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 4.5811 |
| 표준편차 | 5.4978 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 5.7893 |
| Q3 (75%) | 6.1015 |
| IQR | 6.1015 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 3.10 | 0.04% | 0.00% |
| 2025-06 | 5,678 | 4.98 | 8.01% | 6.62% |
| 2025-07 | 2,773 | 7.00 | 19.58% | 16.26% |
| 2025-08 | 4,201 | 4.95 | 7.97% | 6.55% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 450 |
| 2 | 2025-07-04 | 414 |
| 3 | 2025-08-08 | 333 |
| 4 | 2025-07-05 | 129 |
| 5 | 2025-06-12 | 5 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 450건 (2025-06-06)
- 평균 일별 이상치: 167.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted_PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted_PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted_PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted_PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted_PR7L2_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted_PR7L2_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted_PR7L2_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR7L2_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted_PR7L2_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 3.1007 |
| 중앙값 | 5.9613 |
| IQR | 6.1157 |
| Bowley 왜도 | -0.9495 |
| Adj 이상치 수 | 4 |
| Adj 이상치율 | 0.06% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 2건
- 2. 2025-05-18: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR7L2_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 4.9798 |
| 중앙값 | 5.8703 |
| IQR | 6.0967 |
| Bowley 왜도 | -0.9258 |
| Adj 이상치 수 | 457 |
| Adj 이상치율 | 8.05% |
| Std 이상치율 | 6.62% |
| 개선율 | -21.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 452건
- 2. 2025-06-12: 5건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR7L2_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 6.9972 |
| 중앙값 | 4.9331 |
| IQR | 6.2761 |
| Bowley 왜도 | -0.5720 |
| Adj 이상치 수 | 515 |
| Adj 이상치율 | 18.57% |
| Std 이상치율 | 16.08% |
| 개선율 | -15.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 395건
- 2. 2025-07-05: 120건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR7L2_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 4.9532 |
| 중앙값 | 5.8158 |
| IQR | 6.0354 |
| Bowley 왜도 | -0.9272 |
| Adj 이상치 수 | 337 |
| Adj 이상치율 | 8.02% |
| Std 이상치율 | 6.64% |
| 개선율 | -20.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 335건
- 2. 2025-08-11: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR7L2_ACT_TORQUE_00_summary.png)

---

#### [L1] PR6L1_ACT_TORQUE 🟡

**위험도**: [CAUTION] | **이상치율**: 5.82% | **개선율**: -10.5%
**Bowley 왜도**: -0.6020 | **승수 (L/U)**: 1.826/0.548

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,151 | 1,042 |
| 이상치율 | 5.82% | 5.27% |
| 하한 경계 | -11.6343 | -6.3724 |
| 상한 경계 | 7.7386 | 10.6207 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 3.2823 |
| 표준편차 | 4.4891 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 3.4028 |
| Q3 (75%) | 4.2483 |
| IQR | 4.2483 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 2.20 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 4.42 | 13.47% | 12.15% |
| 2025-07 | 2,773 | 2.66 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 3.98 | 9.19% | 8.38% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 597 |
| 2 | 2025-08-08 | 332 |
| 3 | 2025-06-06 | 168 |
| 4 | 2025-08-11 | 54 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 597건 (2025-06-12)
- 평균 일별 이상치: 287.8건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted_PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted_PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted_PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted_PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted_PR6L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted_PR6L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted_PR6L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR6L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted_PR6L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 2.1999 |
| 중앙값 | 4.1535 |
| IQR | 4.2994 |
| Bowley 왜도 | -0.9321 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.01% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L1_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 4.4248 |
| 중앙값 | 3.8056 |
| IQR | 4.2506 |
| Bowley 왜도 | -0.7906 |
| Adj 이상치 수 | 787 |
| Adj 이상치율 | 13.86% |
| Std 이상치율 | 12.12% |
| 개선율 | -14.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 617건
- 2. 2025-06-06: 170건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 2.6646 |
| 중앙값 | 3.3438 |
| IQR | 3.9156 |
| Bowley 왜도 | -0.7079 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 3.9783 |
| 중앙값 | 3.7662 |
| IQR | 3.9064 |
| Bowley 왜도 | -0.9283 |
| Adj 이상치 수 | 405 |
| Adj 이상치율 | 9.64% |
| Std 이상치율 | 8.55% |
| 개선율 | -12.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 343건
- 2. 2025-08-11: 62건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L1_ACT_TORQUE_00_summary.png)

---

#### [L1] PR9L1_ACT_TORQUE 🟡

**위험도**: [CAUTION] | **이상치율**: 5.65% | **개선율**: 10.1%
**Bowley 왜도**: -0.3516 | **승수 (L/U)**: 1.421/0.704

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,117 | 1,242 |
| 이상치율 | 5.65% | 6.28% |
| 하한 경계 | -21.3288 | -16.5276 |
| 상한 경계 | 10.4787 | 13.8566 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | -3.0798 |
| 표준편차 | 8.7028 |
| Q1 (25%) | -5.1335 |
| 중앙값 | 0.0000 |
| Q3 (75%) | 2.4625 |
| IQR | 7.5960 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | -1.41 | 0.00% | 0.00% |
| 2025-06 | 5,678 | -3.42 | 6.76% | 7.47% |
| 2025-07 | 2,773 | -6.04 | 16.12% | 17.92% |
| 2025-08 | 4,201 | -3.49 | 6.81% | 7.64% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 384 |
| 2 | 2025-07-04 | 345 |
| 3 | 2025-08-08 | 286 |
| 4 | 2025-07-05 | 102 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 384건 (2025-06-06)
- 평균 일별 이상치: 279.2건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted_PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted_PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted_PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted_PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted_PR9L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted_PR9L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted_PR9L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR9L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted_PR9L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | -1.4081 |
| 중앙값 | 0.0000 |
| IQR | 0.5083 |
| Bowley 왜도 | -0.8156 |
| Adj 이상치 수 | 3,447 |
| Adj 이상치율 | 48.47% |
| Std 이상치율 | 48.85% |
| 개선율 | 0.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 2,334건
- 2. 2025-05-18: 1,113건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted_PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted_PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted_PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted_PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted_PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR9L1_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | -3.4228 |
| 중앙값 | 0.0000 |
| IQR | 8.5528 |
| Bowley 왜도 | -0.4348 |
| Adj 이상치 수 | 340 |
| Adj 이상치율 | 5.99% |
| Std 이상치율 | 7.04% |
| 개선율 | 15.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 340건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted_PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted_PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted_PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted_PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted_PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR9L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | -6.0444 |
| 중앙값 | 0.0000 |
| IQR | 12.6559 |
| Bowley 왜도 | -0.5900 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 13.42% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted_PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted_PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted_PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted_PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted_PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR9L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | -3.4890 |
| 중앙값 | 0.0000 |
| IQR | 9.0759 |
| Bowley 왜도 | -0.4569 |
| Adj 이상치 수 | 245 |
| Adj 이상치율 | 5.83% |
| Std 이상치율 | 7.02% |
| 개선율 | 16.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 245건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted_PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted_PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted_PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted_PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted_PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR9L1_ACT_TORQUE_00_summary.png)

---

#### [L1] PR8L1_ACT_TORQUE 🟡

**위험도**: [CAUTION] | **이상치율**: 5.09% | **개선율**: -6.8%
**Bowley 왜도**: -0.2393 | **승수 (L/U)**: 1.270/0.787

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1,006 | 942 |
| 이상치율 | 5.09% | 4.77% |
| 하한 경계 | -13.4618 | -10.5966 |
| 상한 경계 | 15.4056 | 17.6610 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 5.3644 |
| 표준편차 | 6.5472 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.3775 |
| Q3 (75%) | 7.0644 |
| IQR | 7.0644 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 4.14 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 5.62 | 5.99% | 5.60% |
| 2025-07 | 2,773 | 7.15 | 14.71% | 13.85% |
| 2025-08 | 4,201 | 5.91 | 6.14% | 5.71% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 340 |
| 2 | 2025-07-04 | 319 |
| 3 | 2025-08-08 | 258 |
| 4 | 2025-07-05 | 89 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 340건 (2025-06-06)
- 평균 일별 이상치: 251.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted_PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted_PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted_PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted_PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted_PR8L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted_PR8L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted_PR8L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR8L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted_PR8L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 4.1360 |
| 중앙값 | 1.5258 |
| IQR | 4.9021 |
| Bowley 왜도 | 0.3775 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 15.06% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted_PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted_PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted_PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted_PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted_PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR8L1_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 5.6232 |
| 중앙값 | 4.5823 |
| IQR | 7.6221 |
| Bowley 왜도 | -0.2024 |
| Adj 이상치 수 | 328 |
| Adj 이상치율 | 5.78% |
| Std 이상치율 | 5.42% |
| 개선율 | -6.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 328건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted_PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted_PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted_PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted_PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted_PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR8L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 7.1503 |
| 중앙값 | 4.2562 |
| IQR | 10.6298 |
| Bowley 왜도 | 0.1992 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted_PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted_PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted_PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted_PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted_PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR8L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 5.9150 |
| 중앙값 | 4.8364 |
| IQR | 8.4073 |
| Bowley 왜도 | -0.1505 |
| Adj 이상치 수 | 229 |
| Adj 이상치율 | 5.45% |
| Std 이상치율 | 5.12% |
| 개선율 | -6.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 229건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted_PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted_PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted_PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted_PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted_PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR8L1_ACT_TORQUE_00_summary.png)

---


### 🟢 양호 (0~5%) - 52개 태그

#### MAIN_GAS_PRESSURE 🟢

**위험도**: [NORMAL] | **이상치율**: 4.00% | **개선율**: 14.4%
**Bowley 왜도**: -0.2891 | **승수 (L/U)**: 1.335/0.749

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 805 | 940 |
| 이상치율 | 4.00% | 4.67% |
| 하한 경계 | 1509.6280 | 1520.7930 |
| 상한 경계 | 1601.2315 | 1609.5930 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1565.2726 |
| 표준편차 | 21.5173 |
| Q1 (25%) | 1554.0930 |
| 중앙값 | 1568.4025 |
| Q3 (75%) | 1576.2930 |
| IQR | 22.2000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1573.27 | 3.41% | 2.85% |
| 2025-06 | 5,758 | 1569.07 | 2.50% | 1.98% |
| 2025-07 | 2,880 | 1546.55 | 10.49% | 14.97% |
| 2025-08 | 4,316 | 1559.38 | 2.64% | 4.40% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 222 |
| 2 | 2025-05-18 | 201 |
| 3 | 2025-06-06 | 116 |
| 4 | 2025-07-05 | 80 |
| 5 | 2025-08-08 | 72 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 222건 (2025-07-04)
- 평균 일별 이상치: 100.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_PRESSURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_PRESSURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_PRESSURE_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_GAS_PRESSURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_PRESSURE_analysis.png)


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

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_PRESSURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1569.0659 |
| 중앙값 | 1571.3480 |
| IQR | 18.0515 |
| Bowley 왜도 | -0.2365 |
| Adj 이상치 수 | 214 |
| Adj 이상치율 | 3.72% |
| Std 이상치율 | 4.34% |
| 개선율 | 14.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 178건
- 2. 2025-06-12: 36건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_PRESSURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1546.5474 |
| 중앙값 | 1549.6225 |
| IQR | 25.2325 |
| Bowley 왜도 | -0.2741 |
| Adj 이상치 수 | 176 |
| Adj 이상치율 | 6.11% |
| Std 이상치율 | 7.12% |
| 개선율 | 14.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 91건
- 2. 2025-07-05: 85건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1559.3842 |
| 중앙값 | 1565.0010 |
| IQR | 22.1420 |
| Bowley 왜도 | -0.4405 |
| Adj 이상치 수 | 116 |
| Adj 이상치율 | 2.69% |
| Std 이상치율 | 3.31% |
| 개선율 | 18.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 78건
- 2. 2025-08-08: 38건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_PRESSURE_00_summary.png)

---

#### SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 2.83% | **개선율**: -1.1%
**Bowley 왜도**: 0.1155 | **승수 (L/U)**: 0.891/1.122

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 570 | 564 |
| 이상치율 | 2.83% | 2.80% |
| 하한 경계 | 988.4875 | 979.3305 |
| 상한 경계 | 1213.4746 | 1203.1965 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1082.7396 |
| 표준편차 | 51.6884 |
| Q1 (25%) | 1063.2802 |
| 중앙값 | 1088.0315 |
| Q3 (75%) | 1119.2468 |
| IQR | 55.9665 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1086.01 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 1100.64 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 1070.33 | 9.79% | 9.58% |
| 2025-08 | 4,316 | 1061.69 | 6.67% | 6.67% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 288 |
| 2 | 2025-07-04 | 282 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 288건 (2025-08-08)
- 평균 일별 이상치: 285.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_analysis.png)


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

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1100.6424 |
| 중앙값 | 1103.4770 |
| IQR | 53.1345 |
| Bowley 왜도 | -0.1097 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1070.3306 |
| 중앙값 | 1090.9475 |
| IQR | 49.6998 |
| Bowley 왜도 | 0.0606 |
| Adj 이상치 수 | 294 |
| Adj 이상치율 | 10.21% |
| Std 이상치율 | 9.97% |
| 개선율 | -2.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 294건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1061.6879 |
| 중앙값 | 1078.2915 |
| IQR | 33.7242 |
| Bowley 왜도 | -0.2512 |
| Adj 이상치 수 | 288 |
| Adj 이상치율 | 6.67% |
| Std 이상치율 | 6.86% |
| 개선율 | 2.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 288건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

---

#### SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 2.78% | **개선율**: 0.0%
**Bowley 왜도**: 0.0026 | **승수 (L/U)**: 0.997/1.003

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 561 | 561 |
| 이상치율 | 2.78% | 2.78% |
| 하한 경계 | 997.1092 | 996.8849 |
| 상한 경계 | 1225.9628 | 1225.7379 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1103.6226 |
| 표준편차 | 52.4373 |
| Q1 (25%) | 1082.7047 |
| 중앙값 | 1111.2365 |
| Q3 (75%) | 1139.9180 |
| IQR | 57.2133 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1108.22 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 1122.14 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 1089.66 | 9.48% | 9.48% |
| 2025-08 | 4,316 | 1080.58 | 6.67% | 6.67% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 288 |
| 2 | 2025-07-04 | 273 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 288건 (2025-08-08)
- 평균 일별 이상치: 280.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_analysis.png)


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

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1122.1419 |
| 중앙값 | 1127.9190 |
| IQR | 53.7720 |
| Bowley 왜도 | -0.2342 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1089.6584 |
| 중앙값 | 1109.9835 |
| IQR | 47.4560 |
| Bowley 왜도 | 0.0739 |
| Adj 이상치 수 | 286 |
| Adj 이상치율 | 9.93% |
| Std 이상치율 | 9.79% |
| 개선율 | -1.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 286건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1080.5773 |
| 중앙값 | 1097.7560 |
| IQR | 34.9610 |
| Bowley 왜도 | -0.2092 |
| Adj 이상치 수 | 289 |
| Adj 이상치율 | 6.70% |
| Std 이상치율 | 6.72% |
| 개선율 | 0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 289건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

---

#### FURNACE_PRESSURE 🟢

**위험도**: [NORMAL] | **이상치율**: 2.76% | **개선율**: -23.6%
**Bowley 왜도**: -0.1243 | **승수 (L/U)**: 1.132/0.883

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 556 | 450 |
| 이상치율 | 2.76% | 2.23% |
| 하한 경계 | 0.4100 | 0.4157 |
| 상한 경계 | 0.5240 | 0.5289 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 0.4739 |
| 표준편차 | 0.0230 |
| Q1 (25%) | 0.4581 |
| 중앙값 | 0.4741 |
| Q3 (75%) | 0.4865 |
| IQR | 0.0283 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 0.47 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 0.48 | 7.40% | 6.15% |
| 2025-07 | 2,880 | 0.47 | 3.78% | 2.92% |
| 2025-08 | 4,316 | 0.47 | 0.49% | 0.28% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 382 |
| 2 | 2025-07-04 | 88 |
| 3 | 2025-06-12 | 44 |
| 4 | 2025-07-05 | 21 |
| 5 | 2025-08-08 | 19 |

- 이상치 발생 일수: 6일
- 최대 일별 이상치: 382건 (2025-06-06)
- 평균 일별 이상치: 92.7건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted_FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted_FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted_FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted_FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted_FURNACE_PRESSURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted_FURNACE_PRESSURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted_FURNACE_PRESSURE_07_daily_outlier_count.png)

**종합 분석 차트**

![FURNACE_PRESSURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted_FURNACE_PRESSURE_analysis.png)


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

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_FURNACE_PRESSURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 0.4829 |
| 중앙값 | 0.4837 |
| IQR | 0.0321 |
| Bowley 왜도 | -0.2126 |
| Adj 이상치 수 | 284 |
| Adj 이상치율 | 4.93% |
| Std 이상치율 | 3.51% |
| 개선율 | -40.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 262건
- 2. 2025-06-12: 22건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_FURNACE_PRESSURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 0.4722 |
| 중앙값 | 0.4718 |
| IQR | 0.0414 |
| Bowley 왜도 | -0.0532 |
| Adj 이상치 수 | 14 |
| Adj 이상치율 | 0.49% |
| Std 이상치율 | 0.38% |
| 개선율 | -27.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 13건
- 2. 2025-07-05: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_FURNACE_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 0.4704 |
| 중앙값 | 0.4726 |
| IQR | 0.0307 |
| Bowley 왜도 | -0.1852 |
| Adj 이상치 수 | 21 |
| Adj 이상치율 | 0.49% |
| Std 이상치율 | 0.19% |
| 개선율 | -162.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 19건
- 2. 2025-08-11: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_FURNACE_PRESSURE_00_summary.png)

---

#### SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 2.60% | **개선율**: 6.4%
**Bowley 왜도**: -0.4711 | **승수 (L/U)**: 1.602/0.624

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 524 | 560 |
| 이상치율 | 2.60% | 2.78% |
| 하한 경계 | 963.1739 | 1007.8760 |
| 상한 경계 | 1178.0714 | 1205.9800 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1102.5063 |
| 표준편차 | 48.4907 |
| Q1 (25%) | 1082.1650 |
| 중앙값 | 1118.5935 |
| Q3 (75%) | 1131.6910 |
| IQR | 49.5260 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1108.68 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 1115.72 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 1092.57 | 8.51% | 9.48% |
| 2025-08 | 4,316 | 1081.22 | 6.46% | 6.65% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 279 |
| 2 | 2025-07-04 | 245 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 279건 (2025-08-08)
- 평균 일별 이상치: 262.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_analysis.png)


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

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1115.7202 |
| 중앙값 | 1127.5850 |
| IQR | 51.1115 |
| Bowley 왜도 | -0.6761 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1092.5664 |
| 중앙값 | 1122.0050 |
| IQR | 40.3332 |
| Bowley 왜도 | -0.5952 |
| Adj 이상치 수 | 255 |
| Adj 이상치율 | 8.85% |
| Std 이상치율 | 11.15% |
| 개선율 | 20.6% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 255건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1081.2190 |
| 중앙값 | 1095.3040 |
| IQR | 45.9810 |
| Bowley 왜도 | 0.0186 |
| Adj 이상치 수 | 287 |
| Adj 이상치율 | 6.65% |
| Std 이상치율 | 6.65% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 287건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

---

#### SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 2.57% | **개선율**: 6.5%
**Bowley 왜도**: -0.4521 | **승수 (L/U)**: 1.572/0.636

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 518 | 554 |
| 이상치율 | 2.57% | 2.75% |
| 하한 경계 | 975.3058 | 1019.6440 |
| 상한 경계 | 1198.2876 | 1226.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1119.6720 |
| 표준편차 | 48.6399 |
| Q1 (25%) | 1097.2150 |
| 중앙값 | 1134.7615 |
| Q3 (75%) | 1148.9290 |
| IQR | 51.7140 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1126.41 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 1133.59 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 1108.85 | 8.44% | 9.27% |
| 2025-08 | 4,316 | 1097.11 | 6.37% | 6.65% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 275 |
| 2 | 2025-07-04 | 243 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 275건 (2025-08-08)
- 평균 일별 이상치: 259.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_analysis.png)


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

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1133.5869 |
| 중앙값 | 1144.9550 |
| IQR | 52.2292 |
| Bowley 왜도 | -0.6461 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1108.8518 |
| 중앙값 | 1137.4735 |
| IQR | 35.5932 |
| Bowley 왜도 | -0.5558 |
| Adj 이상치 수 | 266 |
| Adj 이상치율 | 9.24% |
| Std 이상치율 | 11.84% |
| 개선율 | 22.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 266건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1097.1073 |
| 중앙값 | 1113.0200 |
| IQR | 45.1130 |
| Bowley 왜도 | -0.1184 |
| Adj 이상치 수 | 286 |
| Adj 이상치율 | 6.63% |
| Std 이상치율 | 6.65% |
| 개선율 | 0.3% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 286건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

---

#### HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 1.40% | **개선율**: -112.0%
**Bowley 왜도**: 0.0768 | **승수 (L/U)**: 0.926/1.080

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 282 | 133 |
| 이상치율 | 1.40% | 0.66% |
| 하한 경계 | 857.9989 | 851.2712 |
| 상한 경계 | 1101.2926 | 1094.0280 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 972.6013 |
| 표준편차 | 44.5651 |
| Q1 (25%) | 942.3050 |
| 중앙값 | 970.3199 |
| Q3 (75%) | 1002.9942 |
| IQR | 60.6892 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 974.02 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 985.01 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 968.72 | 6.15% | 2.57% |
| 2025-08 | 4,316 | 956.26 | 2.43% | 1.37% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 176 |
| 2 | 2025-08-08 | 105 |
| 3 | 2025-07-05 | 1 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 176건 (2025-07-04)
- 평균 일별 이상치: 94.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_analysis.png)


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

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 985.0144 |
| 중앙값 | 980.6125 |
| IQR | 51.4287 |
| Bowley 왜도 | 0.1745 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 968.7186 |
| 중앙값 | 969.5505 |
| IQR | 53.7223 |
| Bowley 왜도 | 0.1255 |
| Adj 이상치 수 | 242 |
| Adj 이상치율 | 8.40% |
| Std 이상치율 | 8.61% |
| 개선율 | 2.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 215건
- 2. 2025-07-05: 27건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 956.2636 |
| 중앙값 | 956.4466 |
| IQR | 41.5104 |
| Bowley 왜도 | 0.1490 |
| Adj 이상치 수 | 261 |
| Adj 이상치율 | 6.05% |
| Std 이상치율 | 8.39% |
| 개선율 | 27.9% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 261건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

---

#### COMBUSTION_AIR_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.63% | **개선율**: -68.0%
**Bowley 왜도**: -0.2858 | **승수 (L/U)**: 1.331/0.751

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 126 | 75 |
| 이상치율 | 0.63% | 0.37% |
| 하한 경계 | 22.8270 | 26.2836 |
| 상한 경계 | 51.5432 | 54.1404 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 40.3285 |
| 표준편차 | 4.5722 |
| Q1 (25%) | 36.7299 |
| 중앙값 | 41.2074 |
| Q3 (75%) | 43.6941 |
| IQR | 6.9642 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 35.72 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 41.37 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 45.40 | 3.96% | 2.33% |
| 2025-08 | 4,316 | 43.24 | 0.28% | 0.19% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-05 | 90 |
| 2 | 2025-07-04 | 24 |
| 3 | 2025-08-08 | 12 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 90건 (2025-07-05)
- 평균 일별 이상치: 42.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted_COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted_COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted_COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted_COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted_COMBUSTION_AIR_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted_COMBUSTION_AIR_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted_COMBUSTION_AIR_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![COMBUSTION_AIR_TEMPERATURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted_COMBUSTION_AIR_TEMPERATURE_analysis.png)


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

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_COMBUSTION_AIR_TEMPERATURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 41.3654 |
| 중앙값 | 40.8284 |
| IQR | 5.4124 |
| Bowley 왜도 | 0.2409 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_COMBUSTION_AIR_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 45.4008 |
| 중앙값 | 44.8056 |
| IQR | 3.3372 |
| Bowley 왜도 | 0.2923 |
| Adj 이상치 수 | 73 |
| Adj 이상치율 | 2.53% |
| Std 이상치율 | 3.37% |
| 개선율 | 24.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 53건
- 2. 2025-07-04: 20건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_COMBUSTION_AIR_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 43.2377 |
| 중앙값 | 43.0405 |
| IQR | 1.1802 |
| Bowley 왜도 | -0.0565 |
| Adj 이상치 수 | 714 |
| Adj 이상치율 | 16.54% |
| Std 이상치율 | 16.52% |
| 개선율 | -0.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 600건
- 2. 2025-08-11: 114건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_COMBUSTION_AIR_TEMPERATURE_00_summary.png)

---

#### HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.58% | **개선율**: 4.9%
**Bowley 왜도**: 0.1378 | **승수 (L/U)**: 0.871/1.148

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 117 | 123 |
| 이상치율 | 0.58% | 0.61% |
| 하한 경계 | 832.9538 | 821.0820 |
| 상한 경계 | 1080.5963 | 1066.9701 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 945.6271 |
| 표준편차 | 44.2717 |
| Q1 (25%) | 913.2901 |
| 중앙값 | 939.7899 |
| Q3 (75%) | 974.7621 |
| IQR | 61.4720 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 946.57 | 0.00% | 0.08% |
| 2025-06 | 5,758 | 956.49 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 944.54 | 2.15% | 2.53% |
| 2025-08 | 4,316 | 930.29 | 1.27% | 1.02% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 55 |
| 2 | 2025-07-04 | 53 |
| 3 | 2025-07-05 | 9 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 55건 (2025-08-08)
- 평균 일별 이상치: 39.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_analysis.png)


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

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 956.4873 |
| 중앙값 | 952.7126 |
| IQR | 57.1269 |
| Bowley 왜도 | 0.1089 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 944.5443 |
| 중앙값 | 943.1878 |
| IQR | 54.2767 |
| Bowley 왜도 | 0.1526 |
| Adj 이상치 수 | 240 |
| Adj 이상치율 | 8.33% |
| Std 이상치율 | 3.61% |
| 개선율 | -130.8% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 204건
- 2. 2025-07-05: 36건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 930.2857 |
| 중앙값 | 925.6385 |
| IQR | 42.2710 |
| Bowley 왜도 | 0.2178 |
| Adj 이상치 수 | 318 |
| Adj 이상치율 | 7.37% |
| Std 이상치율 | 10.19% |
| 개선율 | 27.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 272건
- 2. 2025-08-11: 46건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/adjusted_HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

---

#### [L2] PR6L2_ACT_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.51% | **개선율**: -5.2%
**Bowley 왜도**: -0.4823 | **승수 (L/U)**: 1.620/0.617

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 101 | 96 |
| 이상치율 | 0.51% | 0.49% |
| 하한 경계 | -13.8133 | -8.5278 |
| 상한 경계 | 10.9498 | 14.2129 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 3.2784 |
| 표준편차 | 2.9503 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.2136 |
| Q3 (75%) | 5.6852 |
| IQR | 5.6852 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 2.94 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 3.41 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 3.36 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 3.62 | 2.40% | 2.29% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-11 | 54 |
| 2 | 2025-08-08 | 47 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 54건 (2025-08-11)
- 평균 일별 이상치: 50.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/adjusted_PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/adjusted_PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/adjusted_PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/adjusted_PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/adjusted_PR6L2_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/adjusted_PR6L2_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/adjusted_PR6L2_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR6L2_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/adjusted_PR6L2_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 2.9371 |
| 중앙값 | 5.6222 |
| IQR | 5.7887 |
| Bowley 왜도 | -0.9425 |
| Adj 이상치 수 | 6 |
| Adj 이상치율 | 0.08% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 4건
- 2. 2025-05-18: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/adjusted_PR6L2_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 3.4126 |
| 중앙값 | 4.4052 |
| IQR | 5.6658 |
| Bowley 왜도 | -0.5550 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/adjusted_PR6L2_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 3.3597 |
| 중앙값 | 4.0761 |
| IQR | 5.2317 |
| Bowley 왜도 | -0.5582 |
| Adj 이상치 수 | 1 |
| Adj 이상치율 | 0.04% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/adjusted_PR6L2_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 3.6211 |
| 중앙값 | 4.0966 |
| IQR | 5.3362 |
| Bowley 왜도 | -0.5354 |
| Adj 이상치 수 | 104 |
| Adj 이상치율 | 2.48% |
| Std 이상치율 | 2.33% |
| 개선율 | -6.1% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 56건
- 2. 2025-08-08: 48건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/adjusted_PR6L2_ACT_TORQUE_00_summary.png)

---

#### HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 0.25% | **개선율**: 87.8%
**Bowley 왜도**: -0.5872 | **승수 (L/U)**: 1.799/0.556

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 50 | 411 |
| 이상치율 | 0.25% | 2.04% |
| 하한 경계 | 840.7388 | 913.1304 |
| 상한 경계 | 1114.5345 | 1154.7774 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1038.0606 |
| 표준편차 | 38.2874 |
| Q1 (25%) | 1003.7480 |
| 중앙값 | 1051.6895 |
| Q3 (75%) | 1064.1598 |
| IQR | 60.4117 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1038.10 | 0.22% | 0.25% |
| 2025-06 | 5,758 | 1044.14 | 0.28% | 0.00% |
| 2025-07 | 2,880 | 1039.29 | 0.56% | 7.36% |
| 2025-08 | 4,316 | 1029.06 | 0.05% | 4.19% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 16 |
| 2 | 2025-06-12 | 16 |
| 3 | 2025-07-05 | 16 |
| 4 | 2025-08-08 | 2 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 16건 (2025-05-17)
- 평균 일별 이상치: 12.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_analysis.png)


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

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1044.1443 |
| 중앙값 | 1054.0980 |
| IQR | 57.0187 |
| Bowley 왜도 | -0.6828 |
| Adj 이상치 수 | 46 |
| Adj 이상치율 | 0.80% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 40건
- 2. 2025-06-06: 6건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1039.2919 |
| 중앙값 | 1053.2725 |
| IQR | 33.2100 |
| Bowley 왜도 | -0.0633 |
| Adj 이상치 수 | 316 |
| Adj 이상치율 | 10.97% |
| Std 이상치율 | 11.98% |
| 개선율 | 8.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 252건
- 2. 2025-07-05: 64건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1029.0631 |
| 중앙값 | 1047.1695 |
| IQR | 55.4303 |
| Bowley 왜도 | -0.5832 |
| Adj 이상치 수 | 22 |
| Adj 이상치율 | 0.51% |
| Std 이상치율 | 5.12% |
| 개선율 | 90.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 14건
- 2. 2025-08-08: 8건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

---

#### HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 0.22% | **개선율**: 88.2%
**Bowley 왜도**: -0.5899 | **승수 (L/U)**: 1.804/0.554

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 45 | 380 |
| 이상치율 | 0.22% | 1.89% |
| 하한 경계 | 832.7404 | 907.4579 |
| 상한 경계 | 1113.8981 | 1155.3189 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1035.6568 |
| 표준편차 | 38.8125 |
| Q1 (25%) | 1000.4058 |
| 중앙값 | 1049.6660 |
| Q3 (75%) | 1062.3710 |
| IQR | 61.9653 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1035.99 | 0.19% | 0.13% |
| 2025-06 | 5,758 | 1042.02 | 0.24% | 0.00% |
| 2025-07 | 2,880 | 1036.34 | 0.56% | 7.36% |
| 2025-08 | 4,316 | 1026.16 | 0.02% | 3.68% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-05 | 16 |
| 2 | 2025-05-17 | 14 |
| 3 | 2025-06-12 | 14 |
| 4 | 2025-08-08 | 1 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 16건 (2025-07-05)
- 평균 일별 이상치: 11.2건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_analysis.png)


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

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1042.0210 |
| 중앙값 | 1052.3180 |
| IQR | 57.7245 |
| Bowley 왜도 | -0.6863 |
| Adj 이상치 수 | 48 |
| Adj 이상치율 | 0.83% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 42건
- 2. 2025-06-06: 6건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1036.3438 |
| 중앙값 | 1050.1550 |
| IQR | 32.2332 |
| Bowley 왜도 | -0.0408 |
| Adj 이상치 수 | 334 |
| Adj 이상치율 | 11.60% |
| Std 이상치율 | 12.43% |
| 개선율 | 6.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 257건
- 2. 2025-07-05: 77건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1026.1552 |
| 중앙값 | 1044.3540 |
| IQR | 58.1168 |
| Bowley 왜도 | -0.5987 |
| Adj 이상치 수 | 13 |
| Adj 이상치율 | 0.30% |
| Std 이상치율 | 4.29% |
| 개선율 | 93.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 8건
- 2. 2025-08-08: 5건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/adjusted_HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

---

#### MAIN_GAS_FLOW 🟢

**위험도**: [NORMAL] | **이상치율**: 0.03% | **개선율**: 0.0%
**Bowley 왜도**: -0.3592 | **승수 (L/U)**: 1.432/0.698

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 7 | 0 |
| 이상치율 | 0.03% | 0.00% |
| 하한 경계 | -1404.7508 | -713.6858 |
| 상한 경계 | 3067.2243 | 3549.7290 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1429.4984 |
| 표준편차 | 671.5521 |
| Q1 (25%) | 885.0948 |
| 중앙값 | 1609.4720 |
| Q3 (75%) | 1950.9485 |
| IQR | 1065.8537 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 1493.21 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 1432.27 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 1358.78 | 0.24% | 0.00% |
| 2025-08 | 4,316 | 1366.86 | 0.00% | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 7 |

- 이상치 발생 일수: 1일
- 최대 일별 이상치: 7건 (2025-07-04)
- 평균 일별 이상치: 7.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_FLOW_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_FLOW_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_FLOW_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_GAS_FLOW 종합 분석 차트](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_FLOW_analysis.png)


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

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_FLOW_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1432.2668 |
| 중앙값 | 1567.2160 |
| IQR | 1003.6271 |
| Bowley 왜도 | -0.3265 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_FLOW_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1358.7804 |
| 중앙값 | 1414.2270 |
| IQR | 1469.3494 |
| Bowley 왜도 | -0.1172 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_FLOW_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1366.8619 |
| 중앙값 | 1558.9245 |
| IQR | 1123.0848 |
| Bowley 왜도 | -0.4102 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_FLOW_00_summary.png)

---

#### PINCHROLL_2_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.01% | **개선율**: 100.0%
**Bowley 왜도**: -0.9998 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 1 | 2,761 |
| 이상치율 | 0.01% | 16.90% |
| 하한 경계 | 1.5610 | 10.9168 |
| 상한 경계 | 21.9993 | 25.4419 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 16.4559 |
| 표준편차 | 6.2207 |
| Q1 (25%) | 16.3637 |
| 중앙값 | 19.9946 |
| Q3 (75%) | 19.9950 |
| IQR | 3.6313 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 16.86 | 0.02% | 13.38% |
| 2025-06 | 4,896 | 16.11 | 0.00% | 19.04% |
| 2025-07 | 2,011 | 15.76 | 0.00% | 23.22% |
| 2025-08 | 3,273 | 16.64 | 0.00% | 16.44% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 1 |

- 이상치 발생 일수: 1일
- 최대 일별 이상치: 1건 (2025-05-17)
- 평균 일별 이상치: 1.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_2_ACTUAL_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted_PINCHROLL_2_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 16.1126 |
| 중앙값 | 19.9946 |
| IQR | 3.7551 |
| Bowley 왜도 | -0.9998 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 18.79% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 15.7611 |
| 중앙값 | 19.9947 |
| IQR | 5.7822 |
| Bowley 왜도 | -0.9999 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.08% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 16.6440 |
| 중앙값 | 19.9947 |
| IQR | 3.7272 |
| Bowley 왜도 | -0.9998 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 16.44% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

---

#### MAIN_GAS_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.1769 | **승수 (L/U)**: 1.194/0.838

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 6.5286 | 8.6172 |
| 상한 경계 | 35.6398 | 37.3897 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 22.8837 |
| 표준편차 | 4.1085 |
| Q1 (25%) | 19.4069 |
| 중앙값 | 23.6398 |
| Q3 (75%) | 26.6000 |
| IQR | 7.1931 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 18.48 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 23.36 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 26.94 | 0.00% | 0.00% |
| 2025-08 | 4,316 | 26.89 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_GAS_TEMPERATURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted_MAIN_GAS_TEMPERATURE_analysis.png)


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

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_MAIN_GAS_TEMPERATURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 23.3572 |
| 중앙값 | 22.6460 |
| IQR | 4.5032 |
| Bowley 왜도 | 0.3134 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_MAIN_GAS_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 26.9438 |
| 중앙값 | 26.6098 |
| IQR | 2.5141 |
| Bowley 왜도 | 0.2650 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_MAIN_GAS_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 26.8865 |
| 중앙값 | 26.8000 |
| IQR | 0.8952 |
| Bowley 왜도 | -0.1171 |
| Adj 이상치 수 | 446 |
| Adj 이상치율 | 10.33% |
| Std 이상치율 | 8.39% |
| 개선율 | -23.2% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 446건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_MAIN_GAS_TEMPERATURE_00_summary.png)

---

#### STAND_10_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7863 | **승수 (L/U)**: 2.195/0.456

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -194.3312 | -87.1974 |
| 상한 경계 | 103.0231 | 151.8258 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 41.8380 |
| 표준편차 | 26.5130 |
| Q1 (25%) | 2.4363 |
| 중앙값 | 55.8070 |
| Q3 (75%) | 62.1921 |
| IQR | 59.7558 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 43.56 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 43.55 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 36.37 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 40.21 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_10_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_10_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_10_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_10_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_10_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_10_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 43.5548 |
| 중앙값 | 57.6234 |
| IQR | 60.7889 |
| Bowley 왜도 | -0.8128 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_10_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 36.3668 |
| 중앙값 | 60.5397 |
| IQR | 63.8428 |
| Bowley 왜도 | -0.8965 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_10_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 40.2144 |
| 중앙값 | 57.8705 |
| IQR | 59.5813 |
| Bowley 왜도 | -0.8662 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_10_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_12_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6264 | **승수 (L/U)**: 1.871/0.535

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -159.5017 | -83.8097 |
| 상한 경계 | 107.5268 | 147.9868 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 40.2712 |
| 표준편차 | 25.7750 |
| Q1 (25%) | 3.1140 |
| 중앙값 | 50.2371 |
| Q3 (75%) | 61.0631 |
| IQR | 57.9491 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 41.22 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 41.28 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 34.13 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 41.36 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_12_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_12_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_12_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_12_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_12_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_12_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 41.2794 |
| 중앙값 | 49.7351 |
| IQR | 60.0443 |
| Bowley 왜도 | -0.5463 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_12_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 34.1274 |
| 중앙값 | 53.7566 |
| IQR | 57.9904 |
| Bowley 왜도 | -0.8540 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_12_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 41.3559 |
| 중앙값 | 57.6836 |
| IQR | 61.7217 |
| Bowley 왜도 | -0.7761 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_12_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_11_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7094 | **승수 (L/U)**: 2.033/0.492

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -153.1267 | -74.6464 |
| 상한 경계 | 89.3897 | 127.9976 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 34.3684 |
| 표준편차 | 22.1848 |
| Q1 (25%) | 1.3451 |
| 중앙값 | 44.6448 |
| Q3 (75%) | 52.0061 |
| IQR | 50.6610 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 36.48 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 34.45 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 26.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 35.82 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_11_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_11_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_11_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_11_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_11_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_11_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 34.4484 |
| 중앙값 | 45.6894 |
| IQR | 49.1028 |
| Bowley 왜도 | -0.8021 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_11_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 26.5866 |
| 중앙값 | 41.3680 |
| IQR | 45.1324 |
| Bowley 왜도 | -0.8332 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_11_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 35.8191 |
| 중앙값 | 50.1551 |
| IQR | 55.0921 |
| Bowley 왜도 | -0.7780 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_11_ACTUAL_TORQUE_00_summary.png)

---

#### INDIRECT_COOLING_WATER_FLOW 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.8254 | **승수 (L/U)**: 0.438/2.283

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 149.3967 | 141.4295 |
| 상한 경계 | 197.4252 | 179.2382 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 159.5778 |
| 표준편차 | 4.8624 |
| Q1 (25%) | 155.6078 |
| 중앙값 | 156.4331 |
| Q3 (75%) | 165.0600 |
| IQR | 9.4522 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 155.35 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 166.42 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 161.65 | 0.00% | 0.00% |
| 2025-08 | 4,316 | 156.12 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted_INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted_INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted_INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted_INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted_INDIRECT_COOLING_WATER_FLOW_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted_INDIRECT_COOLING_WATER_FLOW_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted_INDIRECT_COOLING_WATER_FLOW_07_daily_outlier_count.png)

**종합 분석 차트**

![INDIRECT_COOLING_WATER_FLOW 종합 분석 차트](./04_Furnace_Auxiliary/adjusted_INDIRECT_COOLING_WATER_FLOW_analysis.png)


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

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_COOLING_WATER_FLOW_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 166.4200 |
| 중앙값 | 166.2618 |
| IQR | 1.9702 |
| Bowley 왜도 | 0.1392 |
| Adj 이상치 수 | 6 |
| Adj 이상치율 | 0.10% |
| Std 이상치율 | 0.03% |
| 개선율 | -200.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 6건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_COOLING_WATER_FLOW_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 161.6460 |
| 중앙값 | 161.5820 |
| IQR | 0.8084 |
| Bowley 왜도 | 0.1002 |
| Adj 이상치 수 | 19 |
| Adj 이상치율 | 0.66% |
| Std 이상치율 | 1.08% |
| 개선율 | 38.7% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 14건
- 2. 2025-07-05: 5건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_COOLING_WATER_FLOW_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 156.1188 |
| 중앙값 | 156.1524 |
| IQR | 0.6975 |
| Bowley 왜도 | -0.0620 |
| Adj 이상치 수 | 22 |
| Adj 이상치율 | 0.51% |
| Std 이상치율 | 0.60% |
| 개선율 | 15.4% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 20건
- 2. 2025-08-11: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_COOLING_WATER_FLOW_00_summary.png)

---

#### INDIRECT_WATER_MAIN_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.4151 | **승수 (L/U)**: 0.660/1.514

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | 26.1391 | 24.0500 |
| 상한 경계 | 43.6139 | 40.4500 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 31.9078 |
| 표준편차 | 2.3866 |
| Q1 (25%) | 30.2000 |
| 중앙값 | 31.3991 |
| Q3 (75%) | 34.3000 |
| IQR | 4.1000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,190 | 30.03 | 0.00% | 0.00% |
| 2025-06 | 5,758 | 31.16 | 0.00% | 0.00% |
| 2025-07 | 2,880 | 34.63 | 0.00% | 0.00% |
| 2025-08 | 4,316 | 34.22 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![INDIRECT_WATER_MAIN_TEMPERATURE 종합 분석 차트](./04_Furnace_Auxiliary/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_analysis.png)


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

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 31.1605 |
| 중앙값 | 31.1000 |
| IQR | 1.0923 |
| Bowley 왜도 | 0.0986 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 34.6258 |
| 중앙값 | 35.5000 |
| IQR | 2.0000 |
| Bowley 왜도 | -0.6000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 11.77% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 34.2237 |
| 중앙값 | 35.0000 |
| IQR | 1.3958 |
| Bowley 왜도 | -0.2896 |
| Adj 이상치 수 | 532 |
| Adj 이상치율 | 12.33% |
| Std 이상치율 | 14.41% |
| 개선율 | 14.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 532건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/adjusted_INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

---

#### FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.3829 | **승수 (L/U)**: 1.467/0.682

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -111.5533 | -74.7524 |
| 상한 경계 | 110.4892 | 135.5824 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 35.1146 |
| 표준편차 | 22.6842 |
| Q1 (25%) | 4.1232 |
| 중앙값 | 40.4829 |
| Q3 (75%) | 56.7069 |
| IQR | 52.5837 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 36.45 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 35.46 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 28.41 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 36.82 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 35.4599 |
| 중앙값 | 40.5302 |
| IQR | 52.8796 |
| Bowley 왜도 | -0.3641 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 28.4112 |
| 중앙값 | 41.6810 |
| IQR | 40.1781 |
| Bowley 왜도 | -0.8992 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 36.8202 |
| 중앙값 | 49.2912 |
| IQR | 54.0046 |
| Bowley 왜도 | -0.6804 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

---

#### FINISHING_BLOCK_MASTER_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.3826 | **승수 (L/U)**: 1.466/0.682

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -111.5486 | -74.7749 |
| 상한 경계 | 110.5678 | 135.6519 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 35.1370 |
| 표준편차 | 22.6971 |
| Q1 (25%) | 4.1351 |
| 중앙값 | 40.5009 |
| Q3 (75%) | 56.7418 |
| IQR | 52.6067 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 36.47 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 35.48 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 28.43 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 36.84 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_MASTER_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 35.4832 |
| 중앙값 | 40.5532 |
| IQR | 52.8693 |
| Bowley 왜도 | -0.3636 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 28.4317 |
| 중앙값 | 41.7042 |
| IQR | 40.1867 |
| Bowley 왜도 | -0.8992 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 36.8399 |
| 중앙값 | 49.3062 |
| IQR | 54.0047 |
| Bowley 왜도 | -0.6803 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_14_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8624 | **승수 (L/U)**: 2.369/0.422

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -113.6022 | -45.9281 |
| 상한 경계 | 57.3341 | 85.9016 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 25.4255 |
| 표준편차 | 15.4851 |
| Q1 (25%) | 3.5080 |
| 중앙값 | 34.1986 |
| Q3 (75%) | 36.4655 |
| IQR | 32.9574 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 26.70 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 25.61 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 21.95 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 25.32 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_14_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_14_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_14_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_14_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_14_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_14_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 25.6136 |
| 중앙값 | 34.0971 |
| IQR | 32.1814 |
| Bowley 왜도 | -0.8865 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_14_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 21.9494 |
| 중앙값 | 35.2862 |
| IQR | 38.2186 |
| Bowley 왜도 | -0.8465 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_14_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 25.3153 |
| 중앙값 | 36.4039 |
| IQR | 34.4233 |
| Bowley 왜도 | -0.9276 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_14_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_13_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8263 | **승수 (L/U)**: 2.285/0.438

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -171.1465 | -73.4800 |
| 상한 경계 | 86.4896 | 129.2363 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 36.8598 |
| 표준편차 | 23.3698 |
| Q1 (25%) | 2.5386 |
| 중앙값 | 48.8154 |
| Q3 (75%) | 53.2177 |
| IQR | 50.6791 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 37.71 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 36.40 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 33.93 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 37.98 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_13_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_13_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_13_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_13_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_13_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_13_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 36.3951 |
| 중앙값 | 48.7165 |
| IQR | 49.3332 |
| Bowley 왜도 | -0.8683 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_13_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 33.9318 |
| 중앙값 | 52.1773 |
| IQR | 61.4577 |
| Bowley 왜도 | -0.6980 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_13_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 37.9834 |
| 중앙값 | 54.8209 |
| IQR | 54.7132 |
| Bowley 왜도 | -0.9149 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_13_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_1_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7158 | **승수 (L/U)**: 2.046/0.489

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -170.2218 | -82.7650 |
| 상한 경계 | 97.4730 | 140.2206 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 37.7406 |
| 표준편차 | 24.5828 |
| Q1 (25%) | 0.8546 |
| 중앙값 | 48.6804 |
| Q3 (75%) | 56.6010 |
| IQR | 55.7464 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 37.35 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 39.25 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 33.06 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 39.45 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_1_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_1_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_1_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_1_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_1_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_1_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 39.2468 |
| 중앙값 | 50.1441 |
| IQR | 56.5490 |
| Bowley 왜도 | -0.7415 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_1_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 33.0618 |
| 중앙값 | 51.5787 |
| IQR | 58.3653 |
| Bowley 왜도 | -0.7674 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_1_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 39.4515 |
| 중앙값 | 54.3318 |
| IQR | 61.0594 |
| Bowley 왜도 | -0.7537 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_1_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_2_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7996 | **승수 (L/U)**: 2.225/0.449

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -198.1900 | -88.4300 |
| 상한 경계 | 101.2146 | 150.5503 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 41.3246 |
| 표준편차 | 26.6314 |
| Q1 (25%) | 1.1876 |
| 중앙값 | 54.9477 |
| Q3 (75%) | 60.9327 |
| IQR | 59.7451 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 43.15 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 41.82 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 33.19 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 42.94 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_2_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_2_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_2_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_2_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_2_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_2_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 41.8234 |
| 중앙값 | 54.2863 |
| IQR | 59.4604 |
| Bowley 왜도 | -0.7734 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_2_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 33.1873 |
| 중앙값 | 52.0979 |
| IQR | 58.8004 |
| Bowley 왜도 | -0.7720 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_2_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 42.9394 |
| 중앙값 | 60.0680 |
| IQR | 66.0724 |
| Bowley 왜도 | -0.7851 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_2_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_3_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7754 | **승수 (L/U)**: 2.171/0.461

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -176.5326 | -80.7989 |
| 상한 경계 | 93.0366 | 137.1236 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 37.6073 |
| 표준편차 | 24.3010 |
| Q1 (25%) | 0.9221 |
| 중앙값 | 49.2846 |
| Q3 (75%) | 55.4027 |
| IQR | 54.4806 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 38.82 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 37.16 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 31.87 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 39.96 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_3_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_3_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_3_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_3_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_3_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_3_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 37.1558 |
| 중앙값 | 47.5539 |
| IQR | 52.8002 |
| Bowley 왜도 | -0.7472 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_3_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 31.8729 |
| 중앙값 | 50.3322 |
| IQR | 56.2563 |
| Bowley 왜도 | -0.7894 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_3_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 39.9578 |
| 중앙값 | 55.3871 |
| IQR | 61.8407 |
| Bowley 왜도 | -0.7628 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_3_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_4_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6589 | **승수 (L/U)**: 1.933/0.517

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -153.6996 | -78.9217 |
| 상한 경계 | 96.2050 | 134.8979 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 36.2970 |
| 표준편차 | 23.5997 |
| Q1 (25%) | 1.2607 |
| 중앙값 | 45.5979 |
| Q3 (75%) | 54.7156 |
| IQR | 53.4549 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 37.34 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 35.79 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 30.46 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 39.07 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_4_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_4_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_4_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_4_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_4_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_4_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 35.7907 |
| 중앙값 | 42.9199 |
| IQR | 52.8567 |
| Bowley 왜도 | -0.5661 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_4_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 30.4647 |
| 중앙값 | 47.6422 |
| IQR | 53.8287 |
| Bowley 왜도 | -0.7701 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_4_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 39.0738 |
| 중앙값 | 53.5141 |
| IQR | 60.2157 |
| Bowley 왜도 | -0.7372 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_4_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_5_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7838 | **승수 (L/U)**: 2.190/0.457

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -161.0797 | -73.0709 |
| 상한 경계 | 84.0014 | 124.1931 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 33.8678 |
| 표준편차 | 21.7370 |
| Q1 (25%) | 0.9031 |
| 중앙값 | 44.8874 |
| Q3 (75%) | 50.2191 |
| IQR | 49.3160 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 34.67 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 34.26 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 29.97 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 34.54 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_5_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_5_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_5_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_5_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_5_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_5_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 34.2632 |
| 중앙값 | 45.4417 |
| IQR | 48.0521 |
| Bowley 왜도 | -0.8294 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_5_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 29.9652 |
| 중앙값 | 48.1608 |
| IQR | 52.8333 |
| Bowley 왜도 | -0.8231 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_5_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 34.5444 |
| 중앙값 | 49.0769 |
| IQR | 52.8806 |
| Bowley 왜도 | -0.8252 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_5_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_6_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.7639 | **승수 (L/U)**: 2.147/0.466

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -143.3583 | -65.9532 |
| 상한 경계 | 77.9911 | 114.0483 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 31.4173 |
| 표준편차 | 19.9183 |
| Q1 (25%) | 1.5473 |
| 중앙값 | 41.2365 |
| Q3 (75%) | 46.5477 |
| IQR | 45.0004 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 32.55 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 32.72 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 26.92 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 30.71 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_6_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_6_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_6_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_6_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_6_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_6_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 32.7174 |
| 중앙값 | 42.6303 |
| IQR | 45.3810 |
| Bowley 왜도 | -0.7896 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_6_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 26.9185 |
| 중앙값 | 42.6711 |
| IQR | 47.2446 |
| Bowley 왜도 | -0.8064 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_6_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 30.7137 |
| 중앙값 | 42.7213 |
| IQR | 46.3738 |
| Bowley 왜도 | -0.7804 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_6_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_7_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8091 | **승수 (L/U)**: 2.246/0.445

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -134.1229 | -58.6287 |
| 상한 경계 | 69.3337 | 102.9469 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 29.2994 |
| 표준편차 | 18.5644 |
| Q1 (25%) | 1.9622 |
| 중앙값 | 38.5012 |
| Q3 (75%) | 42.3561 |
| IQR | 40.3939 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 30.28 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 28.72 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 23.92 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 31.97 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_7_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_7_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_7_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_7_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_7_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_7_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 28.7169 |
| 중앙값 | 37.4356 |
| IQR | 39.1326 |
| Bowley 왜도 | -0.7848 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_7_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 23.9212 |
| 중앙값 | 38.6555 |
| IQR | 41.8055 |
| Bowley 왜도 | -0.8493 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_7_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 31.9694 |
| 중앙값 | 45.0118 |
| IQR | 47.6311 |
| Bowley 왜도 | -0.8118 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_7_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_8_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6826 | **승수 (L/U)**: 1.979/0.505

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -114.2653 | -56.4333 |
| 상한 경계 | 71.8621 | 101.0841 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 28.2175 |
| 표준편차 | 17.6518 |
| Q1 (25%) | 2.6357 |
| 중앙값 | 35.7660 |
| Q3 (75%) | 42.0151 |
| IQR | 39.3793 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 29.34 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 29.67 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 25.55 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 26.12 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_8_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_8_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_8_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_8_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_8_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_8_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 29.6705 |
| 중앙값 | 36.9635 |
| IQR | 40.0922 |
| Bowley 왜도 | -0.6836 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_8_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 25.5472 |
| 중앙값 | 40.9461 |
| IQR | 44.4380 |
| Bowley 왜도 | -0.8428 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_8_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 26.1238 |
| 중앙값 | 36.1157 |
| IQR | 37.4857 |
| Bowley 왜도 | -0.8080 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_8_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_9_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.8119 | **승수 (L/U)**: 2.252/0.444

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -195.4038 | -86.2410 |
| 상한 경계 | 97.7634 | 146.2331 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 40.2076 |
| 표준편차 | 25.9683 |
| Q1 (25%) | 0.9368 |
| 중앙값 | 53.5893 |
| Q3 (75%) | 59.0553 |
| IQR | 58.1185 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 42.39 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 42.69 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 36.57 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 35.55 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/adjusted_STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/adjusted_STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/adjusted_STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/adjusted_STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/adjusted_STAND_9_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/adjusted_STAND_9_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/adjusted_STAND_9_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_9_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/adjusted_STAND_9_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/adjusted_STAND_9_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 42.6919 |
| 중앙값 | 55.8328 |
| IQR | 62.2148 |
| Bowley 왜도 | -0.7596 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/adjusted_STAND_9_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 36.5662 |
| 중앙값 | 60.3194 |
| IQR | 64.6434 |
| Bowley 왜도 | -0.8662 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/adjusted_STAND_9_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 35.5527 |
| 중앙값 | 51.4315 |
| IQR | 53.9621 |
| Bowley 왜도 | -0.8762 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/adjusted_STAND_9_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_3_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -3.9928 | -1.4583 |
| 상한 경계 | 1.5426 | 2.4750 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6974 |
| 표준편차 | 0.4299 |
| Q1 (25%) | 0.0167 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.9833 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_3_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_3_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_3_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_3_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_3_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_3_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_3_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7145 |
| 중앙값 | 1.0000 |
| IQR | 0.6997 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_3_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5897 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_3_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6664 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_3_LOAD_00_summary.png)

---

#### STAND_2_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6979 |
| 표준편차 | 0.4305 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_2_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_2_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_2_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_2_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_2_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_2_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_2_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7150 |
| 중앙값 | 1.0000 |
| IQR | 0.7062 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_2_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5899 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_2_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6666 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_2_LOAD_00_summary.png)

---

#### STAND_1_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6983 |
| 표준편차 | 0.4310 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.75 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.72 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_1_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_1_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_1_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_1_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_1_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_1_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_1_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7155 |
| 중앙값 | 1.0000 |
| IQR | 0.7117 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_1_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5901 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_1_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6667 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_1_LOAD_00_summary.png)

---

#### STAND_13_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6950 |
| 표준편차 | 0.4311 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_13_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_13_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_13_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_13_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_13_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_13_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_13_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7125 |
| 중앙값 | 1.0000 |
| IQR | 0.7263 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_13_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5873 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_13_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6647 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_13_LOAD_00_summary.png)

---

#### STAND_12_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6950 |
| 표준편차 | 0.4311 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_12_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_12_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_12_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_12_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_12_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_12_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_12_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7125 |
| 중앙값 | 1.0000 |
| IQR | 0.7263 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_12_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5873 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_12_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6647 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_12_LOAD_00_summary.png)

---

#### STAND_11_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6949 |
| 표준편차 | 0.4310 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_11_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_11_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_11_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_11_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_11_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_11_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_11_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7123 |
| 중앙값 | 1.0000 |
| IQR | 0.7263 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_11_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5873 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_11_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6646 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_11_LOAD_00_summary.png)

---

#### STAND_10_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6952 |
| 표준편차 | 0.4310 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_10_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_10_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_10_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_10_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_10_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_10_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_10_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7126 |
| 중앙값 | 1.0000 |
| IQR | 0.7374 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_10_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5875 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_10_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6648 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_10_LOAD_00_summary.png)

---

#### STAND_9_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6949 |
| 표준편차 | 0.4308 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_9_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_9_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_9_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_9_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_9_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_9_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_9_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7123 |
| 중앙값 | 1.0000 |
| IQR | 0.7336 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_9_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5875 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_9_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6646 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_9_LOAD_00_summary.png)

---

#### STAND_8_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6968 |
| 표준편차 | 0.4300 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_8_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_8_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_8_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_8_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_8_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_8_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_8_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7142 |
| 중앙값 | 1.0000 |
| IQR | 0.7104 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_8_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5894 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_8_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6659 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_8_LOAD_00_summary.png)

---

#### STAND_7_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6966 |
| 표준편차 | 0.4299 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_7_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_7_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_7_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_7_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_7_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_7_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_7_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7139 |
| 중앙값 | 1.0000 |
| IQR | 0.7045 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_7_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5894 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_7_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6659 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_7_LOAD_00_summary.png)

---

#### STAND_6_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6967 |
| 표준편차 | 0.4299 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_6_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_6_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_6_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_6_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_6_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_6_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_6_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7139 |
| 중앙값 | 1.0000 |
| IQR | 0.7051 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_6_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5894 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_6_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6658 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_6_LOAD_00_summary.png)

---

#### STAND_5_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0757 | -1.4992 |
| 상한 경계 | 1.5516 | 2.4995 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6967 |
| 표준편차 | 0.4298 |
| Q1 (25%) | 0.0003 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.9997 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_5_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_5_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_5_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_5_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_5_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_5_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_5_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7139 |
| 중앙값 | 1.0000 |
| IQR | 0.7301 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_5_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5894 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_5_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6658 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_5_LOAD_00_summary.png)

---

#### STAND_4_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6971 |
| 표준편차 | 0.4297 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_4_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_4_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_4_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_4_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_4_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_4_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_4_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7142 |
| 중앙값 | 1.0000 |
| IQR | 0.7181 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_4_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5896 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_4_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6661 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_4_LOAD_00_summary.png)

---

#### PINCHROLL_3_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -0.6868 | **승수 (L/U)**: 1.987/0.503

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -69.6181 | -32.9791 |
| 상한 경계 | 47.5334 | 65.9688 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 18.4019 |
| 표준편차 | 13.1718 |
| Q1 (25%) | 4.1264 |
| 중앙값 | 24.9901 |
| Q3 (75%) | 28.8634 |
| IQR | 24.7370 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 14.06 | 0.00% | 0.00% |
| 2025-06 | 4,896 | 20.13 | 0.00% | 0.00% |
| 2025-07 | 2,011 | 24.54 | 0.00% | 0.00% |
| 2025-08 | 3,273 | 20.23 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_3_ACTUAL_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_TORQUE_analysis.png)


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

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 20.1254 |
| 중앙값 | 29.9883 |
| IQR | 27.8925 |
| Bowley 왜도 | -0.8479 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 24.5367 |
| 중앙값 | 27.5116 |
| IQR | 21.1726 |
| Bowley 왜도 | -0.2931 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 20.2313 |
| 중앙값 | 24.9924 |
| IQR | 22.7225 |
| Bowley 왜도 | -0.7781 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

---

#### PINCHROLL_3_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 100.0%
**Bowley 왜도**: -0.9071 | **승수 (L/U)**: 2.477/0.404

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 3 |
| 이상치율 | 0.00% | 0.02% |
| 하한 경계 | -1311.0059 | 231.7575 |
| 상한 경계 | 2394.1660 | 3016.9775 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 1649.9720 |
| 표준편차 | 358.0700 |
| Q1 (25%) | 1276.2150 |
| 중앙값 | 1940.1720 |
| Q3 (75%) | 1972.5200 |
| IQR | 696.3050 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 1661.87 | 0.00% | 0.03% |
| 2025-06 | 4,896 | 1597.69 | 0.00% | 0.00% |
| 2025-07 | 2,011 | 1508.75 | 0.00% | 0.00% |
| 2025-08 | 3,273 | 1792.56 | 0.00% | 0.03% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_3_ACTUAL_SPEED 종합 분석 차트](./08_Pinchroll/adjusted_PINCHROLL_3_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 1597.6880 |
| 중앙값 | 1276.2180 |
| IQR | 701.3970 |
| Bowley 왜도 | 0.9951 |
| Adj 이상치 수 | 2 |
| Adj 이상치율 | 0.04% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 1건
- 2. 2025-06-12: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 1508.7451 |
| 중앙값 | 1255.5970 |
| IQR | 767.1730 |
| Bowley 왜도 | 0.9631 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 1792.5635 |
| 중앙값 | 1941.8240 |
| IQR | 61.5300 |
| Bowley 왜도 | 0.5810 |
| Adj 이상치 수 | 772 |
| Adj 이상치율 | 23.59% |
| Std 이상치율 | 23.59% |
| 개선율 | 0.0% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 772건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

---

#### STAND_14_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6948 |
| 표준편차 | 0.4311 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_STAND_14_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_STAND_14_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_STAND_14_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_STAND_14_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_14_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_STAND_14_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_STAND_14_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7122 |
| 중앙값 | 1.0000 |
| IQR | 0.7225 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_STAND_14_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5872 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_STAND_14_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6645 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_STAND_14_LOAD_00_summary.png)

---

#### PINCHROLL_4_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 100.0%
**Bowley 왜도**: -0.9330 | **승수 (L/U)**: 2.542/0.393

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 1 |
| 이상치율 | 0.00% | 0.01% |
| 하한 경계 | -1611.5855 | 103.5230 |
| 상한 경계 | 2394.6261 | 3069.2990 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 1630.7971 |
| 표준편차 | 381.4557 |
| Q1 (25%) | 1215.6890 |
| 중앙값 | 1932.2960 |
| Q3 (75%) | 1957.1330 |
| IQR | 741.4440 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 1628.55 | 0.00% | 0.00% |
| 2025-06 | 4,896 | 1608.57 | 0.00% | 0.00% |
| 2025-07 | 2,011 | 1467.64 | 0.00% | 0.00% |
| 2025-08 | 3,273 | 1768.52 | 0.00% | 0.03% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_4_ACTUAL_SPEED 종합 분석 차트](./08_Pinchroll/adjusted_PINCHROLL_4_ACTUAL_SPEED_analysis.png)


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

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 1608.5685 |
| 중앙값 | 1274.9500 |
| IQR | 827.8580 |
| Bowley 왜도 | 0.8342 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 1467.6444 |
| 중앙값 | 1224.2530 |
| IQR | 729.2730 |
| Bowley 왜도 | 0.9801 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 1768.5161 |
| 중앙값 | 1935.8890 |
| IQR | 42.4310 |
| Bowley 왜도 | -0.3552 |
| Adj 이상치 수 | 1,015 |
| Adj 이상치율 | 31.01% |
| Std 이상치율 | 23.59% |
| 개선율 | -31.5% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 772건
- 2. 2025-08-11: 243건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

---

#### FINISHING_BLOCK_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: -1.0000 | **승수 (L/U)**: 2.718/0.368

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -4.0774 | -1.5000 |
| 상한 경계 | 1.5518 | 2.5000 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6946 |
| 표준편차 | 0.4311 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 7,111 | 0.74 | 0.00% | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/adjusted_FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/adjusted_FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/adjusted_FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/adjusted_FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/adjusted_FINISHING_BLOCK_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/adjusted_FINISHING_BLOCK_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/adjusted_FINISHING_BLOCK_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_LOAD 종합 분석 차트](./07_Stand_Load/adjusted_FINISHING_BLOCK_LOAD_analysis.png)


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

![시계열 차트](./07_Stand_Load/monthly/2025-05/adjusted_FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/adjusted_FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/adjusted_FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/adjusted_FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/adjusted_FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/adjusted_FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/adjusted_FINISHING_BLOCK_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7120 |
| 중앙값 | 1.0000 |
| IQR | 0.7152 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/adjusted_FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/adjusted_FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/adjusted_FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/adjusted_FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/adjusted_FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/adjusted_FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/adjusted_FINISHING_BLOCK_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5869 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/adjusted_FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/adjusted_FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/adjusted_FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/adjusted_FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/adjusted_FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/adjusted_FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/adjusted_FINISHING_BLOCK_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6645 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| Bowley 왜도 | -1.0000 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/adjusted_FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/adjusted_FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/adjusted_FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/adjusted_FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/adjusted_FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/adjusted_FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/adjusted_FINISHING_BLOCK_LOAD_00_summary.png)

---

#### PINCHROLL_3_REFERENCE_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **개선율**: 0.0%
**Bowley 왜도**: 0.6539 | **승수 (L/U)**: 0.520/1.923

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | Adjusted IQR | Standard IQR |
|-----------|--------------|--------------|
| 이상치 수 | 0 | 0 |
| 이상치율 | 0.00% | 0.00% |
| 하한 경계 | -28.6275 | -80.4759 |
| 상한 경계 | 307.2764 | 207.5666 |

| 기본 통계 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 60.2180 |
| 표준편차 | 33.8219 |
| Q1 (25%) | 27.5400 |
| 중앙값 | 40.0000 |
| Q3 (75%) | 99.5506 |
| IQR | 72.0106 |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | Adj 이상치율 | Std 이상치율 |
|-----|-----------|------|--------------|---------------|
| 2025-05 | 6,158 | 65.63 | 0.00% | 0.00% |
| 2025-06 | 4,896 | 62.26 | 0.00% | 0.00% |
| 2025-07 | 2,011 | 48.03 | 0.00% | 0.00% |
| 2025-08 | 3,273 | 54.47 | 0.00% | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/adjusted_PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/adjusted_PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/adjusted_PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/adjusted_PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/adjusted_PINCHROLL_3_REFERENCE_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/adjusted_PINCHROLL_3_REFERENCE_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/adjusted_PINCHROLL_3_REFERENCE_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_3_REFERENCE_TORQUE 종합 분석 차트](./08_Pinchroll/adjusted_PINCHROLL_3_REFERENCE_TORQUE_analysis.png)


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

![시계열 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/adjusted_PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 62.2586 |
| 중앙값 | 40.0000 |
| IQR | 69.5900 |
| Bowley 왜도 | 0.7126 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/adjusted_PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 48.0265 |
| 중앙값 | 35.0000 |
| IQR | 20.8808 |
| Bowley 왜도 | 0.8150 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 21.48% |
| 개선율 | 100.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/adjusted_PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 54.4733 |
| 중앙값 | 40.0000 |
| IQR | 73.8542 |
| Bowley 왜도 | 0.5938 |
| Adj 이상치 수 | 0 |
| Adj 이상치율 | 0.00% |
| Std 이상치율 | 0.00% |
| 개선율 | 0.0% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/adjusted_PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

---


---

## 월별 이상치율 추이

| 월 | Adjusted IQR 평균 | Standard IQR 평균 | 개선율 |
|-----|------------------|-------------------|--------|
| 2025-03 | N/A | N/A | N/A |
| 2025-04 | N/A | N/A | N/A |
| 2025-05 | 3.01% | 3.65% | 17.7% |
| 2025-06 | 3.91% | 4.25% | 7.8% |
| 2025-07 | 8.29% | 8.82% | 6.0% |
| 2025-08 | 6.89% | 6.91% | 0.3% |

---

## 상위 개선 태그 (Top 10)

Adjusted IQR 적용으로 가장 큰 개선을 보인 태그:

| 순위 | 태그명 | Std 이상치율 | Adj 이상치율 | 개선율 | Bowley 왜도 |
|------|--------|--------------|--------------|--------|-------------|
| 1 | PINCHROLL_3_ACTUAL_SPEED | 0.02% | 0.00% | **100.0%** | -0.9071 |
| 2 | PINCHROLL_4_ACTUAL_SPEED | 0.01% | 0.00% | **100.0%** | -0.9330 |
| 3 | PINCHROLL_2_ACTUAL_TORQUE | 16.90% | 0.01% | **100.0%** | -0.9998 |
| 4 | HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 1.89% | 0.22% | **88.2%** | -0.5899 |
| 5 | HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 2.04% | 0.25% | **87.8%** | -0.5872 |
| 6 | FINISHING_BLOCK_ACTUAL_SPEED | 37.91% | 15.79% | **58.3%** | 0.9467 |
| 7 | MAIN_GAS_PRESSURE | 4.67% | 4.00% | **14.4%** | -0.2891 |
| 8 | PR9L1_ACT_TORQUE | 6.28% | 5.65% | **10.1%** | -0.3516 |
| 9 | SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 2.75% | 2.57% | **6.5%** | -0.4521 |
| 10 | SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 2.78% | 2.60% | **6.4%** | -0.4711 |

---

## 높은 왜도 태그 분석

Bowley 왜도 절대값이 큰 태그 (비대칭 분포):

| 태그명 | Bowley 왜도 | 분포 방향 | 승수 (L/U) | 개선율 |
|--------|-------------|----------|------------|--------|
| STAND_1_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_2_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_3_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_4_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_5_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_6_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_7_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_8_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_9_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |
| STAND_10_LOAD | -1.0000 | ← 왼쪽 치우침 | 2.718/0.368 | 0.0% |


---

## 결론 및 권장사항

### 분석 결과 요약

1. **전체 개선 효과**: Adjusted IQR 적용으로 평균 **3.3%** 이상치율 감소
2. **총 이상치 감소**: 78,944 → 73,166 (5,778개 감소)
3. **위험등급 개선**: CRITICAL/DANGER 태그 18개 → 18개

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

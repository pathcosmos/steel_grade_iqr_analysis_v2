# 강종 [D4] 사이즈 [D13] STL 계절-추세 분해 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D4 | 사이즈: D13
**생성일시**: 2026-02-09 15:10:12

---

## 분석 개요

### 분석 방법론

**STL (Seasonal-Trend Decomposition using LOESS)**

시계열 데이터를 세 가지 성분으로 분해:
- **Trend (추세)**: 장기적인 변화 패턴
- **Seasonal (계절성)**: 주기적으로 반복되는 패턴
- **Residual (잔차)**: 추세와 계절성으로 설명되지 않는 변동

| 파라미터 | 값 | 설명 |
|----------|-----|------|
| seasonal | 25h | 계절 주기 |
| robust | True | 강건 추정 |

### 분석 결과 요약

| 구분 | 태그 수 | 비율 |
|------|---------|------|
| **총 분석 태그** | 79개 | 100% |

#### 잔차 이상치율 분포

| 구분 | 태그 수 | 비율 |
|------|---------|------|
| 🔴 높음 (≥15%) | 79개 | 100.0% |
| 🟠 중간 (5~15%) | 0개 | 0.0% |
| 🟢 낮음 (<5%) | 0개 | 0.0% |

#### 계절성 강도 분포

| 구분 | 태그 수 | 비율 |
|------|---------|------|
| 🔵 강함 (≥0.7) | 0개 | 0.0% |
| 중간 (0.4~0.7) | 0개 | 0.0% |
| 약함 (<0.4) | 79개 | 100.0% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 계절성 강도 | 0.027 |
| 평균 추세 강도 | 0.875 |

---

## 상위 문제 태그 (잔차 이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 계절성 강도 | 계절성 분류 |
|------|------|----------|----------|-------------|-------------|
| 1 | STAND_8_ACTUAL_TORQUE | 스탠드 토크 | 47.79% | 0.016 | none |
| 2 | HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 가열로 상부 온도 | 45.57% | 0.016 | none |
| 3 | PR6L2_ACT_TORQUE | PR 상세 토크 | 44.27% | 0.032 | none |
| 4 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 44.21% | 0.000 | none |
| 5 | FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 스탠드 토크 | 43.75% | 0.000 | none |
| 6 | STAND_5_ACTUAL_TORQUE | 스탠드 토크 | 43.23% | 0.108 | none |
| 7 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 42.97% | 0.000 | none |
| 8 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 42.90% | 0.084 | none |
| 9 | STAND_10_ACTUAL_TORQUE | 스탠드 토크 | 42.84% | 0.042 | none |
| 10 | STAND_13_ACTUAL_TORQUE | 스탠드 토크 | 42.58% | 0.070 | none |
| 11 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 42.51% | 0.000 | none |
| 12 | HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 가열로 하부 온도 | 41.80% | 0.000 | none |
| 13 | STAND_14_LOAD | 스탠드 부하 | 41.73% | 0.024 | none |
| 14 | PR6L1_ACT_TORQUE | PR 상세 토크 | 41.60% | 0.217 | weak |
| 15 | FURNACE_PRESSURE | 가열로 보조설비 | 41.54% | 0.114 | none |

---

## 강한 계절성 태그 목록

계절성 강도가 0.7 이상인 태그입니다. 이 태그들은 STL 분석이 특히 효과적입니다.

| 태그 | 카테고리 | 계절성 강도 | 잔차 이상치율 |
|------|----------|-------------|---------------|
| - | 강한 계절성 태그 없음 | - | - |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 평균 잔차 이상치율: 40.69%
- 평균 계절성 강도: 0.005

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 40.82% | 0.000 | 0.980 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 45.57% | 0.016 | 0.942 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 35.68% | 0.003 | 0.979 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 40.69% | 0.001 | 0.858 |

#### STL 분해 차트

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (이상치율: 45.57%, 계절성: 0.016)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_stl_decomposition.png)

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (이상치율: 40.82%, 계절성: 0.000)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_stl_decomposition.png)

**SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (이상치율: 40.69%, 계절성: 0.001)

![SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_stl_decomposition.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 평균 잔차 이상치율: 36.23%
- 평균 계절성 강도: 0.002

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 41.80% | 0.000 | 0.953 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 36.39% | 0.008 | 0.967 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 30.34% | 0.001 | 0.857 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 36.39% | 0.001 | 0.828 |

#### STL 분해 차트

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (이상치율: 41.80%, 계절성: 0.000)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_stl_decomposition.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (이상치율: 36.39%, 계절성: 0.008)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_stl_decomposition.png)

**SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (이상치율: 36.39%, 계절성: 0.001)

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_stl_decomposition.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 평균 잔차 이상치율: 40.76%
- 평균 계절성 강도: 0.023

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 40.76% | 0.023 | 0.986 |

#### STL 분해 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (이상치율: 40.76%, 계절성: 0.023)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_stl_decomposition.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 평균 잔차 이상치율: 34.88%
- 평균 계절성 강도: 0.062

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| FURNACE_PRESSURE | 41.54% | 0.114 | 0.924 |
| FURNACE_O2_ANALYZER | 36.91% | 0.000 | 0.014 |
| MAIN_GAS_PRESSURE | 30.14% | 0.000 | 0.904 |
| MAIN_GAS_FLOW | 39.39% | 0.292 | 0.955 |
| MAIN_GAS_TEMPERATURE | 32.88% | 0.010 | 0.943 |
| MAIN_COMBUSTION_AIR_PRESSURE | 28.71% | 0.001 | 0.970 |
| COMBUSTION_AIR_TEMPERATURE | 35.55% | 0.134 | 0.933 |
| INDIRECT_COOLING_WATER_FLOW | 35.35% | 0.010 | 0.999 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 33.46% | 0.000 | 0.893 |

#### STL 분해 차트

**FURNACE_PRESSURE** (이상치율: 41.54%, 계절성: 0.114)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_stl_decomposition.png)

**MAIN_GAS_FLOW** (이상치율: 39.39%, 계절성: 0.292)

![MAIN_GAS_FLOW](04_Furnace_Auxiliary/MAIN_GAS_FLOW_stl_decomposition.png)

**FURNACE_O2_ANALYZER** (이상치율: 36.91%, 계절성: 0.000)

![FURNACE_O2_ANALYZER](04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_stl_decomposition.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 평균 잔차 이상치율: 39.52%
- 평균 계절성 강도: 0.044

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| STAND_1_ACTUAL_TORQUE | 41.21% | 0.001 | 0.849 |
| STAND_2_ACTUAL_TORQUE | 36.59% | 0.089 | 0.946 |
| STAND_3_ACTUAL_TORQUE | 31.97% | 0.050 | 0.866 |
| STAND_4_ACTUAL_TORQUE | 39.52% | 0.000 | 0.817 |
| STAND_5_ACTUAL_TORQUE | 43.23% | 0.108 | 0.955 |
| STAND_6_ACTUAL_TORQUE | 35.16% | 0.069 | 0.933 |
| STAND_7_ACTUAL_TORQUE | 34.77% | 0.000 | 0.817 |
| STAND_8_ACTUAL_TORQUE | 47.79% | 0.016 | 0.924 |
| STAND_9_ACTUAL_TORQUE | 36.98% | 0.003 | 0.927 |
| STAND_10_ACTUAL_TORQUE | 42.84% | 0.042 | 0.871 |
| STAND_11_ACTUAL_TORQUE | 40.17% | 0.000 | 0.847 |
| STAND_12_ACTUAL_TORQUE | 38.48% | 0.254 | 0.967 |
| STAND_13_ACTUAL_TORQUE | 42.58% | 0.070 | 0.920 |
| STAND_14_ACTUAL_TORQUE | 38.15% | 0.000 | 0.906 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 43.75% | 0.000 | 0.905 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 39.19% | 0.000 | 0.927 |

#### STL 분해 차트

**STAND_8_ACTUAL_TORQUE** (이상치율: 47.79%, 계절성: 0.016)

![STAND_8_ACTUAL_TORQUE](05_Stand_Torque/STAND_8_ACTUAL_TORQUE_stl_decomposition.png)

**FINISHING_BLOCK_MASTER_ACTUAL_TORQUE** (이상치율: 43.75%, 계절성: 0.000)

![FINISHING_BLOCK_MASTER_ACTUAL_TORQUE](05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_stl_decomposition.png)

**STAND_5_ACTUAL_TORQUE** (이상치율: 43.23%, 계절성: 0.108)

![STAND_5_ACTUAL_TORQUE](05_Stand_Torque/STAND_5_ACTUAL_TORQUE_stl_decomposition.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 평균 잔차 이상치율: 36.04%
- 평균 계절성 강도: 0.019

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| STAND_1_ACTUAL_SPEED | 33.01% | 0.000 | 0.872 |
| STAND_2_ACTUAL_SPEED | 33.92% | 0.006 | 0.915 |
| STAND_3_ACTUAL_SPEED | 37.24% | 0.041 | 0.908 |
| STAND_4_ACTUAL_SPEED | 32.29% | 0.000 | 0.831 |
| STAND_5_ACTUAL_SPEED | 35.03% | 0.002 | 0.888 |
| STAND_6_ACTUAL_SPEED | 41.15% | 0.067 | 0.899 |
| STAND_7_ACTUAL_SPEED | 36.78% | 0.000 | 0.893 |
| STAND_8_ACTUAL_SPEED | 39.97% | 0.009 | 0.866 |
| STAND_9_ACTUAL_SPEED | 34.05% | 0.005 | 0.875 |
| STAND_10_ACTUAL_SPEED | 36.39% | 0.000 | 0.870 |
| STAND_11_ACTUAL_SPEED | 38.35% | 0.123 | 0.960 |
| STAND_12_ACTUAL_SPEED | 39.52% | 0.002 | 0.857 |
| STAND_13_ACTUAL_SPEED | 27.60% | 0.020 | 0.910 |
| STAND_14_ACTUAL_SPEED | 38.15% | 0.006 | 0.898 |
| FINISHING_BLOCK_ACTUAL_SPEED | 37.11% | 0.006 | 0.880 |

#### STL 분해 차트

**STAND_6_ACTUAL_SPEED** (이상치율: 41.15%, 계절성: 0.067)

![STAND_6_ACTUAL_SPEED](06_Stand_Speed/STAND_6_ACTUAL_SPEED_stl_decomposition.png)

**STAND_8_ACTUAL_SPEED** (이상치율: 39.97%, 계절성: 0.009)

![STAND_8_ACTUAL_SPEED](06_Stand_Speed/STAND_8_ACTUAL_SPEED_stl_decomposition.png)

**STAND_12_ACTUAL_SPEED** (이상치율: 39.52%, 계절성: 0.002)

![STAND_12_ACTUAL_SPEED](06_Stand_Speed/STAND_12_ACTUAL_SPEED_stl_decomposition.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 평균 잔차 이상치율: 37.12%
- 평균 계절성 강도: 0.012

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| STAND_1_LOAD | 37.50% | 0.003 | 0.862 |
| STAND_2_LOAD | 35.81% | 0.000 | 0.842 |
| STAND_3_LOAD | 36.52% | 0.000 | 0.851 |
| STAND_4_LOAD | 39.13% | 0.000 | 0.875 |
| STAND_5_LOAD | 34.57% | 0.004 | 0.885 |
| STAND_6_LOAD | 34.96% | 0.003 | 0.862 |
| STAND_7_LOAD | 29.23% | 0.000 | 0.873 |
| STAND_8_LOAD | 37.83% | 0.000 | 0.877 |
| STAND_9_LOAD | 34.77% | 0.002 | 0.958 |
| STAND_10_LOAD | 40.62% | 0.044 | 0.960 |
| STAND_11_LOAD | 41.08% | 0.050 | 0.960 |
| STAND_12_LOAD | 36.98% | 0.000 | 0.954 |
| STAND_13_LOAD | 36.98% | 0.000 | 0.954 |
| STAND_14_LOAD | 41.73% | 0.024 | 0.925 |
| FINISHING_BLOCK_LOAD | 39.13% | 0.046 | 0.893 |

#### STL 분해 차트

**STAND_14_LOAD** (이상치율: 41.73%, 계절성: 0.024)

![STAND_14_LOAD](07_Stand_Load/STAND_14_LOAD_stl_decomposition.png)

**STAND_11_LOAD** (이상치율: 41.08%, 계절성: 0.050)

![STAND_11_LOAD](07_Stand_Load/STAND_11_LOAD_stl_decomposition.png)

**STAND_10_LOAD** (이상치율: 40.62%, 계절성: 0.044)

![STAND_10_LOAD](07_Stand_Load/STAND_10_LOAD_stl_decomposition.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 평균 잔차 이상치율: 37.40%
- 평균 계절성 강도: 0.009

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| PINCHROLL_2_ACTUAL_SPEED | 42.90% | 0.084 | 0.941 |
| PINCHROLL_3_ACTUAL_SPEED | 44.21% | 0.000 | 0.856 |
| PINCHROLL_4_ACTUAL_SPEED | 27.93% | 0.000 | 0.962 |
| PINCHROLL_2_ACTUAL_TORQUE | 32.03% | 0.000 | 0.792 |
| PINCHROLL_3_ACTUAL_TORQUE | 39.58% | 0.000 | 0.708 |
| PINCHROLL_4_ACTUAL_TORQUE | 42.97% | 0.000 | 0.742 |
| PINCHROLL_2_REFERENCE_TORQUE | 28.78% | 0.000 | 0.000 |
| PINCHROLL_3_REFERENCE_TORQUE | 35.68% | 0.000 | 0.865 |
| PINCHROLL_4_REFERENCE_TORQUE | 42.51% | 0.000 | 0.826 |

#### STL 분해 차트

**PINCHROLL_3_ACTUAL_SPEED** (이상치율: 44.21%, 계절성: 0.000)

![PINCHROLL_3_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_stl_decomposition.png)

**PINCHROLL_4_ACTUAL_TORQUE** (이상치율: 42.97%, 계절성: 0.000)

![PINCHROLL_4_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_stl_decomposition.png)

**PINCHROLL_2_ACTUAL_SPEED** (이상치율: 42.90%, 계절성: 0.084)

![PINCHROLL_2_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_stl_decomposition.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 평균 잔차 이상치율: 35.88%
- 평균 계절성 강도: 0.046

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| PR6L1_ACT_TORQUE | 41.60% | 0.217 | 0.955 |
| PR6L2_ACT_TORQUE | 44.27% | 0.032 | 0.967 |
| PR7L1_ACT_TORQUE | 21.22% | 0.000 | 0.856 |
| PR7L2_ACT_TORQUE | 36.33% | 0.000 | 0.871 |
| PR8L1_ACT_TORQUE | 40.30% | 0.027 | 0.906 |
| PR9L1_ACT_TORQUE | 31.58% | 0.000 | 0.801 |

#### STL 분해 차트

**PR6L2_ACT_TORQUE** (이상치율: 44.27%, 계절성: 0.032)

![PR6L2_ACT_TORQUE](09_PR_Detailed/PR6L2_ACT_TORQUE_stl_decomposition.png)

**PR6L1_ACT_TORQUE** (이상치율: 41.60%, 계절성: 0.217)

![PR6L1_ACT_TORQUE](09_PR_Detailed/PR6L1_ACT_TORQUE_stl_decomposition.png)

**PR8L1_ACT_TORQUE** (이상치율: 40.30%, 계절성: 0.027)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_stl_decomposition.png)



---

## 해석 가이드

### STL 분해 해석

1. **추세 (Trend)**
   - 장기적인 상승/하락 패턴
   - 설비 노화, 계절적 변화 등 반영
   - 추세 강도 높을수록 장기 변화가 뚜렷함

2. **계절성 (Seasonal)**
   - 주기적으로 반복되는 패턴 (24시간 기준)
   - 계절성 강도 ≥ 0.7: 강한 주기적 패턴
   - 계절성이 강한 태그는 STL 분석이 효과적

3. **잔차 (Residual)**
   - 추세와 계절성으로 설명되지 않는 변동
   - **순수한 이상치**를 포함
   - 잔차 기반 IQR로 "진짜" 이상치 탐지

### 계절성 강도 분류

| 분류 | 강도 범위 | 해석 |
|------|----------|------|
| Strong | ≥ 0.7 | 명확한 주기적 패턴, STL 매우 효과적 |
| Moderate | 0.4 ~ 0.7 | 적당한 주기적 패턴, STL 효과적 |
| Weak | 0.2 ~ 0.4 | 약한 주기적 패턴 |
| None | < 0.2 | 주기적 패턴 거의 없음 |

### Standard IQR vs STL Residual IQR

| 방법 | 장점 | 단점 |
|------|------|------|
| Standard IQR | 간단, 빠름 | 계절성에 영향받음 |
| STL Residual IQR | 계절성 제거, 순수 이상치 | 계산 복잡, 데이터 필요 |

**권장**: 계절성 강도 ≥ 0.4인 태그에는 STL Residual IQR 사용

---

## 메타데이터

| 항목 | 값 |
|------|-----|
| 분석 스크립트 | steel_grade_stl_analysis.py |
| 분석 기간 | 2025-03-01 ~ 2025-08-31 |
| 강종 | D4 |
| 계절 주기 | 25시간 |
| 생성일시 | 2026-02-09 15:10:12 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

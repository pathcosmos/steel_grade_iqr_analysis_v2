# 강종 [D4] 사이즈 [D10] STL 계절-추세 분해 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D4 | 사이즈: D10
**생성일시**: 2026-02-09 15:09:12

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
| 🔵 강함 (≥0.7) | 2개 | 2.5% |
| 중간 (0.4~0.7) | 1개 | 1.3% |
| 약함 (<0.4) | 76개 | 96.2% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 계절성 강도 | 0.071 |
| 평균 추세 강도 | 0.895 |

---

## 상위 문제 태그 (잔차 이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 계절성 강도 | 계절성 분류 |
|------|------|----------|----------|-------------|-------------|
| 1 | STAND_10_ACTUAL_SPEED | 스탠드 속도 | 46.70% | 0.133 | none |
| 2 | STAND_5_LOAD | 스탠드 부하 | 45.02% | 0.000 | none |
| 3 | STAND_4_ACTUAL_SPEED | 스탠드 속도 | 44.88% | 0.000 | none |
| 4 | MAIN_GAS_PRESSURE | 가열로 보조설비 | 44.73% | 0.000 | none |
| 5 | PR6L1_ACT_TORQUE | PR 상세 토크 | 44.49% | 0.119 | none |
| 6 | PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 44.16% | 0.988 | strong |
| 7 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 44.06% | 0.004 | none |
| 8 | STAND_11_LOAD | 스탠드 부하 | 44.01% | 0.000 | none |
| 9 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 43.73% | 0.007 | none |
| 10 | FINISHING_BLOCK_ACTUAL_SPEED | 스탠드 속도 | 43.34% | 0.000 | none |
| 11 | STAND_10_ACTUAL_TORQUE | 스탠드 토크 | 43.15% | 0.015 | none |
| 12 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 42.91% | 0.000 | none |
| 13 | STAND_10_LOAD | 스탠드 부하 | 42.62% | 0.000 | none |
| 14 | STAND_8_LOAD | 스탠드 부하 | 42.53% | 0.021 | none |
| 15 | STAND_12_ACTUAL_TORQUE | 스탠드 토크 | 42.39% | 0.000 | none |

---

## 강한 계절성 태그 목록

계절성 강도가 0.7 이상인 태그입니다. 이 태그들은 STL 분석이 특히 효과적입니다.

| 태그 | 카테고리 | 계절성 강도 | 잔차 이상치율 |
|------|----------|-------------|---------------|
| PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 0.988 | 44.16% |
| PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 0.727 | 34.72% |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 평균 잔차 이상치율: 38.40%
- 평균 계절성 강도: 0.038

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 36.45% | 0.000 | 0.940 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 37.26% | 0.101 | 0.953 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 41.67% | 0.053 | 0.905 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 38.22% | 0.000 | 0.896 |

#### STL 분해 차트

**SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (이상치율: 41.67%, 계절성: 0.053)

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_stl_decomposition.png)

**SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (이상치율: 38.22%, 계절성: 0.000)

![SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_stl_decomposition.png)

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (이상치율: 37.26%, 계절성: 0.101)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_stl_decomposition.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 평균 잔차 이상치율: 36.55%
- 평균 계절성 강도: 0.001

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 38.41% | 0.000 | 0.910 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 34.20% | 0.000 | 0.928 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 33.05% | 0.006 | 0.901 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 40.57% | 0.000 | 0.841 |

#### STL 분해 차트

**SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (이상치율: 40.57%, 계절성: 0.000)

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_stl_decomposition.png)

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (이상치율: 38.41%, 계절성: 0.000)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_stl_decomposition.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (이상치율: 34.20%, 계절성: 0.000)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_stl_decomposition.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 평균 잔차 이상치율: 38.89%
- 평균 계절성 강도: 0.000

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 38.89% | 0.000 | 0.954 |

#### STL 분해 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (이상치율: 38.89%, 계절성: 0.000)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_stl_decomposition.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 평균 잔차 이상치율: 37.94%
- 평균 계절성 강도: 0.092

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| FURNACE_PRESSURE | 37.74% | 0.052 | 0.875 |
| FURNACE_O2_ANALYZER | 40.61% | 0.307 | 0.989 |
| MAIN_GAS_PRESSURE | 44.73% | 0.000 | 0.107 |
| MAIN_GAS_FLOW | 32.57% | 0.108 | 0.858 |
| MAIN_GAS_TEMPERATURE | 31.51% | 0.137 | 0.979 |
| MAIN_COMBUSTION_AIR_PRESSURE | 39.66% | 0.006 | 0.420 |
| COMBUSTION_AIR_TEMPERATURE | 38.07% | 0.175 | 0.973 |
| INDIRECT_COOLING_WATER_FLOW | 40.95% | 0.000 | 0.999 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 35.58% | 0.042 | 0.998 |

#### STL 분해 차트

**MAIN_GAS_PRESSURE** (이상치율: 44.73%, 계절성: 0.000)

![MAIN_GAS_PRESSURE](04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_stl_decomposition.png)

**INDIRECT_COOLING_WATER_FLOW** (이상치율: 40.95%, 계절성: 0.000)

![INDIRECT_COOLING_WATER_FLOW](04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_stl_decomposition.png)

**FURNACE_O2_ANALYZER** (이상치율: 40.61%, 계절성: 0.307)

![FURNACE_O2_ANALYZER](04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_stl_decomposition.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 평균 잔차 이상치율: 39.85%
- 평균 계절성 강도: 0.070

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| STAND_1_ACTUAL_TORQUE | 41.62% | 0.000 | 0.899 |
| STAND_2_ACTUAL_TORQUE | 40.18% | 0.000 | 0.902 |
| STAND_3_ACTUAL_TORQUE | 36.88% | 0.063 | 0.920 |
| STAND_4_ACTUAL_TORQUE | 37.50% | 0.139 | 0.914 |
| STAND_5_ACTUAL_TORQUE | 40.76% | 0.000 | 0.928 |
| STAND_6_ACTUAL_TORQUE | 38.98% | 0.000 | 0.927 |
| STAND_7_ACTUAL_TORQUE | 42.05% | 0.267 | 0.951 |
| STAND_8_ACTUAL_TORQUE | 34.91% | 0.000 | 0.917 |
| STAND_9_ACTUAL_TORQUE | 42.00% | 0.188 | 0.931 |
| STAND_10_ACTUAL_TORQUE | 43.15% | 0.015 | 0.932 |
| STAND_11_ACTUAL_TORQUE | 36.93% | 0.000 | 0.932 |
| STAND_12_ACTUAL_TORQUE | 42.39% | 0.000 | 0.879 |
| STAND_13_ACTUAL_TORQUE | 40.52% | 0.108 | 0.926 |
| STAND_14_ACTUAL_TORQUE | 39.46% | 0.000 | 0.916 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 41.76% | 0.000 | 0.915 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 38.46% | 0.341 | 0.953 |

#### STL 분해 차트

**STAND_10_ACTUAL_TORQUE** (이상치율: 43.15%, 계절성: 0.015)

![STAND_10_ACTUAL_TORQUE](05_Stand_Torque/STAND_10_ACTUAL_TORQUE_stl_decomposition.png)

**STAND_12_ACTUAL_TORQUE** (이상치율: 42.39%, 계절성: 0.000)

![STAND_12_ACTUAL_TORQUE](05_Stand_Torque/STAND_12_ACTUAL_TORQUE_stl_decomposition.png)

**STAND_7_ACTUAL_TORQUE** (이상치율: 42.05%, 계절성: 0.267)

![STAND_7_ACTUAL_TORQUE](05_Stand_Torque/STAND_7_ACTUAL_TORQUE_stl_decomposition.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 평균 잔차 이상치율: 39.84%
- 평균 계절성 강도: 0.057

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| STAND_1_ACTUAL_SPEED | 38.03% | 0.335 | 0.963 |
| STAND_2_ACTUAL_SPEED | 41.81% | 0.000 | 0.934 |
| STAND_3_ACTUAL_SPEED | 33.76% | 0.000 | 0.912 |
| STAND_4_ACTUAL_SPEED | 44.88% | 0.000 | 0.947 |
| STAND_5_ACTUAL_SPEED | 38.36% | 0.000 | 0.849 |
| STAND_6_ACTUAL_SPEED | 37.45% | 0.000 | 0.924 |
| STAND_7_ACTUAL_SPEED | 39.51% | 0.219 | 0.968 |
| STAND_8_ACTUAL_SPEED | 40.95% | 0.000 | 0.921 |
| STAND_9_ACTUAL_SPEED | 42.05% | 0.051 | 0.937 |
| STAND_10_ACTUAL_SPEED | 46.70% | 0.133 | 0.941 |
| STAND_11_ACTUAL_SPEED | 36.78% | 0.094 | 0.957 |
| STAND_12_ACTUAL_SPEED | 38.75% | 0.014 | 0.941 |
| STAND_13_ACTUAL_SPEED | 35.11% | 0.001 | 0.931 |
| STAND_14_ACTUAL_SPEED | 40.18% | 0.008 | 0.950 |
| FINISHING_BLOCK_ACTUAL_SPEED | 43.34% | 0.000 | 0.944 |

#### STL 분해 차트

**STAND_10_ACTUAL_SPEED** (이상치율: 46.70%, 계절성: 0.133)

![STAND_10_ACTUAL_SPEED](06_Stand_Speed/STAND_10_ACTUAL_SPEED_stl_decomposition.png)

**STAND_4_ACTUAL_SPEED** (이상치율: 44.88%, 계절성: 0.000)

![STAND_4_ACTUAL_SPEED](06_Stand_Speed/STAND_4_ACTUAL_SPEED_stl_decomposition.png)

**FINISHING_BLOCK_ACTUAL_SPEED** (이상치율: 43.34%, 계절성: 0.000)

![FINISHING_BLOCK_ACTUAL_SPEED](06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_stl_decomposition.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 평균 잔차 이상치율: 39.28%
- 평균 계절성 강도: 0.018

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| STAND_1_LOAD | 40.37% | 0.000 | 0.926 |
| STAND_2_LOAD | 36.88% | 0.000 | 0.910 |
| STAND_3_LOAD | 34.96% | 0.000 | 0.898 |
| STAND_4_LOAD | 38.41% | 0.054 | 0.913 |
| STAND_5_LOAD | 45.02% | 0.000 | 0.890 |
| STAND_6_LOAD | 37.74% | 0.000 | 0.889 |
| STAND_7_LOAD | 37.26% | 0.112 | 0.927 |
| STAND_8_LOAD | 42.53% | 0.021 | 0.915 |
| STAND_9_LOAD | 38.79% | 0.012 | 0.942 |
| STAND_10_LOAD | 42.62% | 0.000 | 0.893 |
| STAND_11_LOAD | 44.01% | 0.000 | 0.919 |
| STAND_12_LOAD | 37.36% | 0.000 | 0.903 |
| STAND_13_LOAD | 37.36% | 0.000 | 0.903 |
| STAND_14_LOAD | 42.24% | 0.076 | 0.928 |
| FINISHING_BLOCK_LOAD | 33.72% | 0.000 | 0.918 |

#### STL 분해 차트

**STAND_5_LOAD** (이상치율: 45.02%, 계절성: 0.000)

![STAND_5_LOAD](07_Stand_Load/STAND_5_LOAD_stl_decomposition.png)

**STAND_11_LOAD** (이상치율: 44.01%, 계절성: 0.000)

![STAND_11_LOAD](07_Stand_Load/STAND_11_LOAD_stl_decomposition.png)

**STAND_10_LOAD** (이상치율: 42.62%, 계절성: 0.000)

![STAND_10_LOAD](07_Stand_Load/STAND_10_LOAD_stl_decomposition.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 평균 잔차 이상치율: 40.70%
- 평균 계절성 강도: 0.198

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| PINCHROLL_2_ACTUAL_SPEED | 42.19% | 0.052 | 0.680 |
| PINCHROLL_3_ACTUAL_SPEED | 34.72% | 0.727 | 0.999 |
| PINCHROLL_4_ACTUAL_SPEED | 42.91% | 0.000 | 0.982 |
| PINCHROLL_2_ACTUAL_TORQUE | 36.06% | 0.000 | 0.054 |
| PINCHROLL_3_ACTUAL_TORQUE | 39.18% | 0.000 | 0.972 |
| PINCHROLL_4_ACTUAL_TORQUE | 44.06% | 0.004 | 0.896 |
| PINCHROLL_2_REFERENCE_TORQUE | 44.16% | 0.988 | 1.000 |
| PINCHROLL_3_REFERENCE_TORQUE | 43.73% | 0.007 | 0.856 |
| PINCHROLL_4_REFERENCE_TORQUE | 39.32% | 0.000 | 0.784 |

#### STL 분해 차트

**PINCHROLL_2_REFERENCE_TORQUE** (이상치율: 44.16%, 계절성: 0.988)

![PINCHROLL_2_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_stl_decomposition.png)

**PINCHROLL_4_ACTUAL_TORQUE** (이상치율: 44.06%, 계절성: 0.004)

![PINCHROLL_4_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_stl_decomposition.png)

**PINCHROLL_3_REFERENCE_TORQUE** (이상치율: 43.73%, 계절성: 0.007)

![PINCHROLL_3_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_stl_decomposition.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 평균 잔차 이상치율: 39.24%
- 평균 계절성 강도: 0.103

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| PR6L1_ACT_TORQUE | 44.49% | 0.119 | 0.982 |
| PR6L2_ACT_TORQUE | 37.31% | 0.000 | 0.854 |
| PR7L1_ACT_TORQUE | 39.94% | 0.497 | 0.973 |
| PR7L2_ACT_TORQUE | 40.90% | 0.000 | 0.925 |
| PR8L1_ACT_TORQUE | 37.55% | 0.002 | 0.945 |
| PR9L1_ACT_TORQUE | 35.25% | 0.000 | 0.942 |

#### STL 분해 차트

**PR6L1_ACT_TORQUE** (이상치율: 44.49%, 계절성: 0.119)

![PR6L1_ACT_TORQUE](09_PR_Detailed/PR6L1_ACT_TORQUE_stl_decomposition.png)

**PR7L2_ACT_TORQUE** (이상치율: 40.90%, 계절성: 0.000)

![PR7L2_ACT_TORQUE](09_PR_Detailed/PR7L2_ACT_TORQUE_stl_decomposition.png)

**PR7L1_ACT_TORQUE** (이상치율: 39.94%, 계절성: 0.497)

![PR7L1_ACT_TORQUE](09_PR_Detailed/PR7L1_ACT_TORQUE_stl_decomposition.png)



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
| 생성일시 | 2026-02-09 15:09:12 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

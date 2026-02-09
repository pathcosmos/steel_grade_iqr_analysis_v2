# 강종 [N5] 사이즈 [D12] STL 계절-추세 분해 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5 | 사이즈: D12
**생성일시**: 2026-02-09 15:02:26

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
| 평균 계절성 강도 | 0.021 |
| 평균 추세 강도 | 0.812 |

---

## 상위 문제 태그 (잔차 이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 계절성 강도 | 계절성 분류 |
|------|------|----------|----------|-------------|-------------|
| 1 | MAIN_COMBUSTION_AIR_PRESSURE | 가열로 보조설비 | 44.94% | 0.067 | none |
| 2 | PR8L1_ACT_TORQUE | PR 상세 토크 | 44.94% | 0.000 | none |
| 3 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 43.49% | 0.000 | none |
| 4 | PR7L2_ACT_TORQUE | PR 상세 토크 | 43.42% | 0.000 | none |
| 5 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 43.39% | 0.010 | none |
| 6 | STAND_11_ACTUAL_TORQUE | 스탠드 토크 | 43.29% | 0.000 | none |
| 7 | STAND_6_ACTUAL_SPEED | 스탠드 속도 | 43.29% | 0.000 | none |
| 8 | STAND_1_LOAD | 스탠드 부하 | 43.11% | 0.042 | none |
| 9 | STAND_5_ACTUAL_SPEED | 스탠드 속도 | 42.84% | 0.000 | none |
| 10 | STAND_11_LOAD | 스탠드 부하 | 42.32% | 0.000 | none |
| 11 | STAND_4_ACTUAL_TORQUE | 스탠드 토크 | 42.29% | 0.000 | none |
| 12 | STAND_14_ACTUAL_TORQUE | 스탠드 토크 | 41.63% | 0.000 | none |
| 13 | FURNACE_PRESSURE | 가열로 보조설비 | 41.43% | 0.000 | none |
| 14 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 41.43% | 0.075 | none |
| 15 | STAND_9_ACTUAL_SPEED | 스탠드 속도 | 41.25% | 0.000 | none |

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
- 평균 잔차 이상치율: 38.55%
- 평균 계절성 강도: 0.076

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 40.46% | 0.051 | 0.933 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 39.08% | 0.000 | 0.873 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 38.60% | 0.094 | 0.944 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 36.05% | 0.161 | 0.972 |

#### STL 분해 차트

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (이상치율: 40.46%, 계절성: 0.051)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_stl_decomposition.png)

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (이상치율: 39.08%, 계절성: 0.000)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_stl_decomposition.png)

**SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (이상치율: 38.60%, 계절성: 0.094)

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_stl_decomposition.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 평균 잔차 이상치율: 38.48%
- 평균 계절성 강도: 0.009

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 37.47% | 0.013 | 0.893 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 38.02% | 0.022 | 0.940 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 37.64% | 0.000 | 0.916 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 40.81% | 0.000 | 0.974 |

#### STL 분해 차트

**SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (이상치율: 40.81%, 계절성: 0.000)

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_stl_decomposition.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (이상치율: 38.02%, 계절성: 0.022)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_stl_decomposition.png)

**SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (이상치율: 37.64%, 계절성: 0.000)

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_stl_decomposition.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 평균 잔차 이상치율: 33.44%
- 평균 계절성 강도: 0.000

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 33.44% | 0.000 | 0.639 |

#### STL 분해 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (이상치율: 33.44%, 계절성: 0.000)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_stl_decomposition.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 평균 잔차 이상치율: 38.88%
- 평균 계절성 강도: 0.025

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| FURNACE_PRESSURE | 41.43% | 0.000 | 0.488 |
| FURNACE_O2_ANALYZER | 32.89% | 0.074 | 0.943 |
| MAIN_GAS_PRESSURE | 35.47% | 0.000 | 0.378 |
| MAIN_GAS_FLOW | 40.50% | 0.000 | 0.743 |
| MAIN_GAS_TEMPERATURE | 38.60% | 0.019 | 0.951 |
| MAIN_COMBUSTION_AIR_PRESSURE | 44.94% | 0.067 | 0.854 |
| COMBUSTION_AIR_TEMPERATURE | 38.09% | 0.068 | 0.954 |
| INDIRECT_COOLING_WATER_FLOW | 38.74% | 0.000 | 0.996 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 39.29% | 0.000 | 0.995 |

#### STL 분해 차트

**MAIN_COMBUSTION_AIR_PRESSURE** (이상치율: 44.94%, 계절성: 0.067)

![MAIN_COMBUSTION_AIR_PRESSURE](04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_stl_decomposition.png)

**FURNACE_PRESSURE** (이상치율: 41.43%, 계절성: 0.000)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_stl_decomposition.png)

**MAIN_GAS_FLOW** (이상치율: 40.50%, 계절성: 0.000)

![MAIN_GAS_FLOW](04_Furnace_Auxiliary/MAIN_GAS_FLOW_stl_decomposition.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 평균 잔차 이상치율: 39.64%
- 평균 계절성 강도: 0.017

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| STAND_1_ACTUAL_TORQUE | 38.95% | 0.000 | 0.774 |
| STAND_2_ACTUAL_TORQUE | 40.94% | 0.000 | 0.816 |
| STAND_3_ACTUAL_TORQUE | 39.12% | 0.008 | 0.804 |
| STAND_4_ACTUAL_TORQUE | 42.29% | 0.000 | 0.793 |
| STAND_5_ACTUAL_TORQUE | 39.39% | 0.056 | 0.864 |
| STAND_6_ACTUAL_TORQUE | 39.12% | 0.000 | 0.828 |
| STAND_7_ACTUAL_TORQUE | 39.81% | 0.010 | 0.837 |
| STAND_8_ACTUAL_TORQUE | 40.22% | 0.023 | 0.842 |
| STAND_9_ACTUAL_TORQUE | 38.88% | 0.041 | 0.802 |
| STAND_10_ACTUAL_TORQUE | 35.92% | 0.002 | 0.827 |
| STAND_11_ACTUAL_TORQUE | 43.29% | 0.000 | 0.813 |
| STAND_12_ACTUAL_TORQUE | 38.26% | 0.052 | 0.825 |
| STAND_13_ACTUAL_TORQUE | 39.50% | 0.016 | 0.831 |
| STAND_14_ACTUAL_TORQUE | 41.63% | 0.000 | 0.871 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 40.08% | 0.056 | 0.879 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 36.91% | 0.000 | 0.829 |

#### STL 분해 차트

**STAND_11_ACTUAL_TORQUE** (이상치율: 43.29%, 계절성: 0.000)

![STAND_11_ACTUAL_TORQUE](05_Stand_Torque/STAND_11_ACTUAL_TORQUE_stl_decomposition.png)

**STAND_4_ACTUAL_TORQUE** (이상치율: 42.29%, 계절성: 0.000)

![STAND_4_ACTUAL_TORQUE](05_Stand_Torque/STAND_4_ACTUAL_TORQUE_stl_decomposition.png)

**STAND_14_ACTUAL_TORQUE** (이상치율: 41.63%, 계절성: 0.000)

![STAND_14_ACTUAL_TORQUE](05_Stand_Torque/STAND_14_ACTUAL_TORQUE_stl_decomposition.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 평균 잔차 이상치율: 39.69%
- 평균 계절성 강도: 0.036

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| STAND_1_ACTUAL_SPEED | 40.01% | 0.218 | 0.867 |
| STAND_2_ACTUAL_SPEED | 40.74% | 0.099 | 0.844 |
| STAND_3_ACTUAL_SPEED | 38.81% | 0.039 | 0.825 |
| STAND_4_ACTUAL_SPEED | 36.36% | 0.000 | 0.764 |
| STAND_5_ACTUAL_SPEED | 42.84% | 0.000 | 0.518 |
| STAND_6_ACTUAL_SPEED | 43.29% | 0.000 | 0.110 |
| STAND_7_ACTUAL_SPEED | 40.53% | 0.079 | 0.798 |
| STAND_8_ACTUAL_SPEED | 40.32% | 0.000 | 0.774 |
| STAND_9_ACTUAL_SPEED | 41.25% | 0.000 | 0.817 |
| STAND_10_ACTUAL_SPEED | 34.88% | 0.020 | 0.850 |
| STAND_11_ACTUAL_SPEED | 39.60% | 0.024 | 0.787 |
| STAND_12_ACTUAL_SPEED | 37.81% | 0.037 | 0.852 |
| STAND_13_ACTUAL_SPEED | 40.67% | 0.006 | 0.753 |
| STAND_14_ACTUAL_SPEED | 38.95% | 0.000 | 0.780 |
| FINISHING_BLOCK_ACTUAL_SPEED | 39.36% | 0.012 | 0.823 |

#### STL 분해 차트

**STAND_6_ACTUAL_SPEED** (이상치율: 43.29%, 계절성: 0.000)

![STAND_6_ACTUAL_SPEED](06_Stand_Speed/STAND_6_ACTUAL_SPEED_stl_decomposition.png)

**STAND_5_ACTUAL_SPEED** (이상치율: 42.84%, 계절성: 0.000)

![STAND_5_ACTUAL_SPEED](06_Stand_Speed/STAND_5_ACTUAL_SPEED_stl_decomposition.png)

**STAND_9_ACTUAL_SPEED** (이상치율: 41.25%, 계절성: 0.000)

![STAND_9_ACTUAL_SPEED](06_Stand_Speed/STAND_9_ACTUAL_SPEED_stl_decomposition.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 평균 잔차 이상치율: 38.06%
- 평균 계절성 강도: 0.007

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| STAND_1_LOAD | 43.11% | 0.042 | 0.847 |
| STAND_2_LOAD | 41.08% | 0.000 | 0.808 |
| STAND_3_LOAD | 37.71% | 0.005 | 0.845 |
| STAND_4_LOAD | 37.05% | 0.000 | 0.806 |
| STAND_5_LOAD | 34.16% | 0.000 | 0.727 |
| STAND_6_LOAD | 39.12% | 0.000 | 0.795 |
| STAND_7_LOAD | 38.12% | 0.000 | 0.725 |
| STAND_8_LOAD | 36.71% | 0.000 | 0.771 |
| STAND_9_LOAD | 38.09% | 0.003 | 0.832 |
| STAND_10_LOAD | 36.05% | 0.000 | 0.826 |
| STAND_11_LOAD | 42.32% | 0.000 | 0.806 |
| STAND_12_LOAD | 33.68% | 0.024 | 0.844 |
| STAND_13_LOAD | 33.68% | 0.024 | 0.844 |
| STAND_14_LOAD | 39.74% | 0.000 | 0.780 |
| FINISHING_BLOCK_LOAD | 40.25% | 0.000 | 0.788 |

#### STL 분해 차트

**STAND_1_LOAD** (이상치율: 43.11%, 계절성: 0.042)

![STAND_1_LOAD](07_Stand_Load/STAND_1_LOAD_stl_decomposition.png)

**STAND_11_LOAD** (이상치율: 42.32%, 계절성: 0.000)

![STAND_11_LOAD](07_Stand_Load/STAND_11_LOAD_stl_decomposition.png)

**STAND_2_LOAD** (이상치율: 41.08%, 계절성: 0.000)

![STAND_2_LOAD](07_Stand_Load/STAND_2_LOAD_stl_decomposition.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 평균 잔차 이상치율: 39.97%
- 평균 계절성 강도: 0.009

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| PINCHROLL_2_ACTUAL_SPEED | 38.67% | 0.000 | 0.970 |
| PINCHROLL_3_ACTUAL_SPEED | 43.39% | 0.010 | 0.941 |
| PINCHROLL_4_ACTUAL_SPEED | 43.49% | 0.000 | 0.907 |
| PINCHROLL_2_ACTUAL_TORQUE | 39.98% | 0.000 | 0.788 |
| PINCHROLL_3_ACTUAL_TORQUE | 41.43% | 0.075 | 0.884 |
| PINCHROLL_4_ACTUAL_TORQUE | 35.64% | 0.000 | 0.768 |
| PINCHROLL_2_REFERENCE_TORQUE | 38.64% | 0.000 | 0.000 |
| PINCHROLL_3_REFERENCE_TORQUE | 37.33% | 0.000 | 0.933 |
| PINCHROLL_4_REFERENCE_TORQUE | 41.18% | 0.000 | 0.861 |

#### STL 분해 차트

**PINCHROLL_4_ACTUAL_SPEED** (이상치율: 43.49%, 계절성: 0.000)

![PINCHROLL_4_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_stl_decomposition.png)

**PINCHROLL_3_ACTUAL_SPEED** (이상치율: 43.39%, 계절성: 0.010)

![PINCHROLL_3_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_stl_decomposition.png)

**PINCHROLL_3_ACTUAL_TORQUE** (이상치율: 41.43%, 계절성: 0.075)

![PINCHROLL_3_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_stl_decomposition.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 평균 잔차 이상치율: 40.43%
- 평균 계절성 강도: 0.020

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| PR6L1_ACT_TORQUE | 35.30% | 0.090 | 0.967 |
| PR6L2_ACT_TORQUE | 37.16% | 0.029 | 0.972 |
| PR7L1_ACT_TORQUE | 40.84% | 0.000 | 0.967 |
| PR7L2_ACT_TORQUE | 43.42% | 0.000 | 0.917 |
| PR8L1_ACT_TORQUE | 44.94% | 0.000 | 0.585 |
| PR9L1_ACT_TORQUE | 40.91% | 0.000 | 0.851 |

#### STL 분해 차트

**PR8L1_ACT_TORQUE** (이상치율: 44.94%, 계절성: 0.000)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_stl_decomposition.png)

**PR7L2_ACT_TORQUE** (이상치율: 43.42%, 계절성: 0.000)

![PR7L2_ACT_TORQUE](09_PR_Detailed/PR7L2_ACT_TORQUE_stl_decomposition.png)

**PR9L1_ACT_TORQUE** (이상치율: 40.91%, 계절성: 0.000)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_stl_decomposition.png)



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
| 강종 | N5 |
| 계절 주기 | 25시간 |
| 생성일시 | 2026-02-09 15:02:26 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

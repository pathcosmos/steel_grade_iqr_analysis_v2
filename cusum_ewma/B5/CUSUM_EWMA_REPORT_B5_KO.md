# 강종 [B5] CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: B5
**생성일시**: 2026-02-03 20:41:11

---

## 분석 개요

### 분석 방법론

| 방법 | 목적 | 파라미터 |
|------|------|----------|
| **CUSUM** | 점진적 드리프트 탐지 | k=0.5σ, h=5.0σ |
| **EWMA** | 급격한 변화 탐지 | λ=0.2, L=3.0 |

### 분석 결과 요약

| 구분 | 태그 수 | 비율 |
|------|---------|------|
| **총 분석 태그** | 79개 | 100% |
| 🔴 드리프트 탐지 | 79개 | 100.0% |
| 🟠 시프트 탐지 | 79개 | 100.0% |
| 🟡 경고 | 0개 | 0.0% |
| 🟢 안정 | 0개 | 0.0% |

---

## 상위 문제 태그 (드리프트 빈도 기준)

| 순위 | 태그 | 카테고리 | CUSUM 드리프트 | EWMA 시프트 | 상태 |
|------|------|----------|----------------|-------------|------|
| 1 | PR6L1_ACT_TORQUE | PR 상세 토크 | 249 | 202 | 🔴 |
| 2 | PR9L1_ACT_TORQUE | PR 상세 토크 | 242 | 68 | 🔴 |
| 3 | PR8L1_ACT_TORQUE | PR 상세 토크 | 237 | 188 | 🔴 |
| 4 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 232 | 144 | 🔴 |
| 5 | FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 가열로 추출 온도 | 219 | 202 | 🔴 |
| 6 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 171 | 142 | 🔴 |
| 7 | STAND_9_ACTUAL_TORQUE | 스탠드 토크 | 157 | 79 | 🔴 |
| 8 | FINISHING_BLOCK_LOAD | 스탠드 부하 | 153 | 107 | 🔴 |
| 9 | STAND_4_LOAD | 스탠드 부하 | 152 | 103 | 🔴 |
| 10 | STAND_8_LOAD | 스탠드 부하 | 152 | 103 | 🔴 |
| 11 | STAND_5_LOAD | 스탠드 부하 | 152 | 102 | 🔴 |
| 12 | STAND_3_LOAD | 스탠드 부하 | 150 | 105 | 🔴 |
| 13 | STAND_9_LOAD | 스탠드 부하 | 149 | 105 | 🔴 |
| 14 | STAND_10_LOAD | 스탠드 부하 | 149 | 105 | 🔴 |
| 15 | STAND_7_LOAD | 스탠드 부하 | 149 | 103 | 🔴 |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 39 | 83 | 🔴 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 36 | 74 | 🔴 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 42 | 125 | 🔴 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 33 | 119 | 🔴 |

#### 주요 태그 차트

**SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 42, Shift: 125)

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 39, Shift: 83)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 36, Shift: 74)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 12 | 38 | 🔴 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 10 | 35 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 5 | 80 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 12 | 115 | 🔴 |

#### 주요 태그 차트

**SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 12, Shift: 115)

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 12, Shift: 38)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 10, Shift: 35)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 드리프트 탐지: 1개
- 시프트 탐지: 1개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 219 | 202 | 🔴 |

#### 주요 태그 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (Drift: 219, Shift: 202)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_combined.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_PRESSURE | 28 | 267 | 🔴 |
| FURNACE_O2_ANALYZER | 13 | 118 | 🔴 |
| MAIN_GAS_PRESSURE | 17 | 128 | 🔴 |
| MAIN_GAS_FLOW | 7 | 119 | 🔴 |
| MAIN_GAS_TEMPERATURE | 3 | 11 | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | 10 | 16 | 🔴 |
| COMBUSTION_AIR_TEMPERATURE | 3 | 21 | 🔴 |
| INDIRECT_COOLING_WATER_FLOW | 11 | 169 | 🔴 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 12 | 38 | 🔴 |

#### 주요 태그 차트

**FURNACE_PRESSURE** (Drift: 28, Shift: 267)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_combined.png)

**MAIN_GAS_PRESSURE** (Drift: 17, Shift: 128)

![MAIN_GAS_PRESSURE](04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_combined.png)

**FURNACE_O2_ANALYZER** (Drift: 13, Shift: 118)

![FURNACE_O2_ANALYZER](04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_combined.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 드리프트 탐지: 16개
- 시프트 탐지: 16개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_TORQUE | 104 | 89 | 🔴 |
| STAND_2_ACTUAL_TORQUE | 119 | 81 | 🔴 |
| STAND_3_ACTUAL_TORQUE | 104 | 80 | 🔴 |
| STAND_4_ACTUAL_TORQUE | 103 | 82 | 🔴 |
| STAND_5_ACTUAL_TORQUE | 93 | 76 | 🔴 |
| STAND_6_ACTUAL_TORQUE | 103 | 80 | 🔴 |
| STAND_7_ACTUAL_TORQUE | 73 | 80 | 🔴 |
| STAND_8_ACTUAL_TORQUE | 104 | 100 | 🔴 |
| STAND_9_ACTUAL_TORQUE | 157 | 79 | 🔴 |
| STAND_10_ACTUAL_TORQUE | 139 | 78 | 🔴 |
| STAND_11_ACTUAL_TORQUE | 135 | 77 | 🔴 |
| STAND_12_ACTUAL_TORQUE | 104 | 77 | 🔴 |
| STAND_13_ACTUAL_TORQUE | 123 | 77 | 🔴 |
| STAND_14_ACTUAL_TORQUE | 125 | 76 | 🔴 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 18 | 262 | 🔴 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 18 | 262 | 🔴 |

#### 주요 태그 차트

**STAND_9_ACTUAL_TORQUE** (Drift: 157, Shift: 79)

![STAND_9_ACTUAL_TORQUE](05_Stand_Torque/STAND_9_ACTUAL_TORQUE_combined.png)

**STAND_10_ACTUAL_TORQUE** (Drift: 139, Shift: 78)

![STAND_10_ACTUAL_TORQUE](05_Stand_Torque/STAND_10_ACTUAL_TORQUE_combined.png)

**STAND_11_ACTUAL_TORQUE** (Drift: 135, Shift: 77)

![STAND_11_ACTUAL_TORQUE](05_Stand_Torque/STAND_11_ACTUAL_TORQUE_combined.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_SPEED | 22 | 33 | 🔴 |
| STAND_2_ACTUAL_SPEED | 22 | 33 | 🔴 |
| STAND_3_ACTUAL_SPEED | 22 | 33 | 🔴 |
| STAND_4_ACTUAL_SPEED | 16 | 33 | 🔴 |
| STAND_5_ACTUAL_SPEED | 24 | 33 | 🔴 |
| STAND_6_ACTUAL_SPEED | 25 | 33 | 🔴 |
| STAND_7_ACTUAL_SPEED | 22 | 33 | 🔴 |
| STAND_8_ACTUAL_SPEED | 22 | 33 | 🔴 |
| STAND_9_ACTUAL_SPEED | 21 | 35 | 🔴 |
| STAND_10_ACTUAL_SPEED | 21 | 35 | 🔴 |
| STAND_11_ACTUAL_SPEED | 21 | 35 | 🔴 |
| STAND_12_ACTUAL_SPEED | 21 | 35 | 🔴 |
| STAND_13_ACTUAL_SPEED | 21 | 35 | 🔴 |
| STAND_14_ACTUAL_SPEED | 21 | 35 | 🔴 |
| FINISHING_BLOCK_ACTUAL_SPEED | 22 | 37 | 🔴 |

#### 주요 태그 차트

**STAND_6_ACTUAL_SPEED** (Drift: 25, Shift: 33)

![STAND_6_ACTUAL_SPEED](06_Stand_Speed/STAND_6_ACTUAL_SPEED_combined.png)

**STAND_5_ACTUAL_SPEED** (Drift: 24, Shift: 33)

![STAND_5_ACTUAL_SPEED](06_Stand_Speed/STAND_5_ACTUAL_SPEED_combined.png)

**FINISHING_BLOCK_ACTUAL_SPEED** (Drift: 22, Shift: 37)

![FINISHING_BLOCK_ACTUAL_SPEED](06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_combined.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_LOAD | 148 | 105 | 🔴 |
| STAND_2_LOAD | 147 | 105 | 🔴 |
| STAND_3_LOAD | 150 | 105 | 🔴 |
| STAND_4_LOAD | 152 | 103 | 🔴 |
| STAND_5_LOAD | 152 | 102 | 🔴 |
| STAND_6_LOAD | 144 | 103 | 🔴 |
| STAND_7_LOAD | 149 | 103 | 🔴 |
| STAND_8_LOAD | 152 | 103 | 🔴 |
| STAND_9_LOAD | 149 | 105 | 🔴 |
| STAND_10_LOAD | 149 | 105 | 🔴 |
| STAND_11_LOAD | 146 | 105 | 🔴 |
| STAND_12_LOAD | 146 | 105 | 🔴 |
| STAND_13_LOAD | 146 | 105 | 🔴 |
| STAND_14_LOAD | 147 | 105 | 🔴 |
| FINISHING_BLOCK_LOAD | 153 | 107 | 🔴 |

#### 주요 태그 차트

**FINISHING_BLOCK_LOAD** (Drift: 153, Shift: 107)

![FINISHING_BLOCK_LOAD](07_Stand_Load/FINISHING_BLOCK_LOAD_combined.png)

**STAND_4_LOAD** (Drift: 152, Shift: 103)

![STAND_4_LOAD](07_Stand_Load/STAND_4_LOAD_combined.png)

**STAND_8_LOAD** (Drift: 152, Shift: 103)

![STAND_8_LOAD](07_Stand_Load/STAND_8_LOAD_combined.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 1 | 243 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 1 | 292 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 1 | 354 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 113 | 131 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 110 | 139 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 122 | 142 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 10 | 12 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 171 | 142 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 232 | 144 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_4_REFERENCE_TORQUE** (Drift: 232, Shift: 144)

![PINCHROLL_4_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_combined.png)

**PINCHROLL_3_REFERENCE_TORQUE** (Drift: 171, Shift: 142)

![PINCHROLL_3_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_combined.png)

**PINCHROLL_4_ACTUAL_TORQUE** (Drift: 122, Shift: 142)

![PINCHROLL_4_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_combined.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 드리프트 탐지: 6개
- 시프트 탐지: 6개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 249 | 202 | 🔴 |
| PR6L2_ACT_TORQUE | 97 | 274 | 🔴 |
| PR7L1_ACT_TORQUE | 28 | 451 | 🔴 |
| PR7L2_ACT_TORQUE | 18 | 472 | 🔴 |
| PR8L1_ACT_TORQUE | 237 | 188 | 🔴 |
| PR9L1_ACT_TORQUE | 242 | 68 | 🔴 |

#### 주요 태그 차트

**PR6L1_ACT_TORQUE** (Drift: 249, Shift: 202)

![PR6L1_ACT_TORQUE](09_PR_Detailed/PR6L1_ACT_TORQUE_combined.png)

**PR9L1_ACT_TORQUE** (Drift: 242, Shift: 68)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR8L1_ACT_TORQUE** (Drift: 237, Shift: 188)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_combined.png)



---

## 해석 가이드

### CUSUM (Cumulative Sum) 관리도

- **원리**: 목표값 대비 편차의 누적합을 추적
- **장점**: 작은 지속적 변화(0.5σ~2σ)에 민감
- **드리프트**: 누적합이 결정 구간(h)을 초과하면 탐지
- **활용**: 점진적인 공정 악화, 센서 드리프트 탐지

### EWMA (Exponentially Weighted Moving Average) 관리도

- **원리**: 최근 데이터에 더 큰 가중치를 부여
- **장점**: 급격한 변화에 빠른 반응
- **시프트**: EWMA 값이 제어 한계를 벗어나면 탐지
- **활용**: 급격한 공정 변화, 이상 상태 전환 탐지

### 상태 정의

| 상태 | 설명 | 권장 조치 |
|------|------|----------|
| 🔴 드리프트 탐지 | CUSUM에서 점진적 변화 감지 | 원인 분석 및 공정 조정 |
| 🟠 시프트 탐지 | EWMA에서 급격한 변화 감지 | 즉시 점검 필요 |
| 🟡 경고 | 위반율 5% 초과 | 모니터링 강화 |
| 🟢 안정 | 정상 범위 | 현 상태 유지 |

---

## 메타데이터

| 항목 | 값 |
|------|-----|
| 분석 스크립트 | steel_grade_cusum_ewma_analysis.py |
| 분석 기간 | 2025-03-01 ~ 2025-08-31 |
| 강종 | B5 |
| 생성일시 | 2026-02-03 20:41:11 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

# 강종 [N5] | 규격: D10 CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5
**규격**: D10
**생성일시**: 2026-02-09 14:49:02

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
| 1 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 225 | 143 | 🔴 |
| 2 | PR9L1_ACT_TORQUE | PR 상세 토크 | 205 | 210 | 🔴 |
| 3 | FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 가열로 추출 온도 | 180 | 241 | 🔴 |
| 4 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 127 | 169 | 🔴 |
| 5 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 127 | 144 | 🔴 |
| 6 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 96 | 247 | 🔴 |
| 7 | STAND_13_ACTUAL_TORQUE | 스탠드 토크 | 63 | 164 | 🔴 |
| 8 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 55 | 362 | 🔴 |
| 9 | PR8L1_ACT_TORQUE | PR 상세 토크 | 50 | 165 | 🔴 |
| 10 | STAND_14_ACTUAL_TORQUE | 스탠드 토크 | 41 | 268 | 🔴 |
| 11 | STAND_8_LOAD | 스탠드 부하 | 32 | 270 | 🔴 |
| 12 | STAND_5_LOAD | 스탠드 부하 | 31 | 276 | 🔴 |
| 13 | STAND_6_LOAD | 스탠드 부하 | 31 | 273 | 🔴 |
| 14 | STAND_7_LOAD | 스탠드 부하 | 31 | 273 | 🔴 |
| 15 | STAND_3_LOAD | 스탠드 부하 | 31 | 270 | 🔴 |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 8 | 43 | 🔴 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 9 | 40 | 🔴 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 3 | 51 | 🔴 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 3 | 35 | 🔴 |

#### 주요 태그 차트

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 9, Shift: 40)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 8, Shift: 43)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 3, Shift: 51)

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 8 | 46 | 🔴 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 5 | 60 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 4 | 38 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 1 | 39 | 🔴 |

#### 주요 태그 차트

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 8, Shift: 46)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 5, Shift: 60)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)

**SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 4, Shift: 38)

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 드리프트 탐지: 1개
- 시프트 탐지: 1개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 180 | 241 | 🔴 |

#### 주요 태그 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (Drift: 180, Shift: 241)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_combined.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_PRESSURE | 16 | 147 | 🔴 |
| FURNACE_O2_ANALYZER | 9 | 53 | 🔴 |
| MAIN_GAS_PRESSURE | 24 | 96 | 🔴 |
| MAIN_GAS_FLOW | 8 | 114 | 🔴 |
| MAIN_GAS_TEMPERATURE | 4 | 9 | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | 15 | 9 | 🔴 |
| COMBUSTION_AIR_TEMPERATURE | 4 | 30 | 🔴 |
| INDIRECT_COOLING_WATER_FLOW | 17 | 68 | 🔴 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 3 | 11 | 🔴 |

#### 주요 태그 차트

**MAIN_GAS_PRESSURE** (Drift: 24, Shift: 96)

![MAIN_GAS_PRESSURE](04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_combined.png)

**INDIRECT_COOLING_WATER_FLOW** (Drift: 17, Shift: 68)

![INDIRECT_COOLING_WATER_FLOW](04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_combined.png)

**FURNACE_PRESSURE** (Drift: 16, Shift: 147)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_combined.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 드리프트 탐지: 16개
- 시프트 탐지: 16개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_TORQUE | 17 | 375 | 🔴 |
| STAND_2_ACTUAL_TORQUE | 16 | 410 | 🔴 |
| STAND_3_ACTUAL_TORQUE | 16 | 278 | 🔴 |
| STAND_4_ACTUAL_TORQUE | 29 | 259 | 🔴 |
| STAND_5_ACTUAL_TORQUE | 22 | 287 | 🔴 |
| STAND_6_ACTUAL_TORQUE | 14 | 300 | 🔴 |
| STAND_7_ACTUAL_TORQUE | 15 | 304 | 🔴 |
| STAND_8_ACTUAL_TORQUE | 21 | 289 | 🔴 |
| STAND_9_ACTUAL_TORQUE | 22 | 458 | 🔴 |
| STAND_10_ACTUAL_TORQUE | 22 | 275 | 🔴 |
| STAND_11_ACTUAL_TORQUE | 8 | 349 | 🔴 |
| STAND_12_ACTUAL_TORQUE | 13 | 418 | 🔴 |
| STAND_13_ACTUAL_TORQUE | 63 | 164 | 🔴 |
| STAND_14_ACTUAL_TORQUE | 41 | 268 | 🔴 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 12 | 169 | 🔴 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 13 | 168 | 🔴 |

#### 주요 태그 차트

**STAND_13_ACTUAL_TORQUE** (Drift: 63, Shift: 164)

![STAND_13_ACTUAL_TORQUE](05_Stand_Torque/STAND_13_ACTUAL_TORQUE_combined.png)

**STAND_14_ACTUAL_TORQUE** (Drift: 41, Shift: 268)

![STAND_14_ACTUAL_TORQUE](05_Stand_Torque/STAND_14_ACTUAL_TORQUE_combined.png)

**STAND_4_ACTUAL_TORQUE** (Drift: 29, Shift: 259)

![STAND_4_ACTUAL_TORQUE](05_Stand_Torque/STAND_4_ACTUAL_TORQUE_combined.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_SPEED | 9 | 46 | 🔴 |
| STAND_2_ACTUAL_SPEED | 8 | 46 | 🔴 |
| STAND_3_ACTUAL_SPEED | 11 | 46 | 🔴 |
| STAND_4_ACTUAL_SPEED | 13 | 46 | 🔴 |
| STAND_5_ACTUAL_SPEED | 9 | 46 | 🔴 |
| STAND_6_ACTUAL_SPEED | 10 | 46 | 🔴 |
| STAND_7_ACTUAL_SPEED | 16 | 46 | 🔴 |
| STAND_8_ACTUAL_SPEED | 11 | 46 | 🔴 |
| STAND_9_ACTUAL_SPEED | 14 | 50 | 🔴 |
| STAND_10_ACTUAL_SPEED | 12 | 50 | 🔴 |
| STAND_11_ACTUAL_SPEED | 15 | 50 | 🔴 |
| STAND_12_ACTUAL_SPEED | 17 | 50 | 🔴 |
| STAND_13_ACTUAL_SPEED | 15 | 50 | 🔴 |
| STAND_14_ACTUAL_SPEED | 15 | 50 | 🔴 |
| FINISHING_BLOCK_ACTUAL_SPEED | 16 | 48 | 🔴 |

#### 주요 태그 차트

**STAND_12_ACTUAL_SPEED** (Drift: 17, Shift: 50)

![STAND_12_ACTUAL_SPEED](06_Stand_Speed/STAND_12_ACTUAL_SPEED_combined.png)

**FINISHING_BLOCK_ACTUAL_SPEED** (Drift: 16, Shift: 48)

![FINISHING_BLOCK_ACTUAL_SPEED](06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_combined.png)

**STAND_7_ACTUAL_SPEED** (Drift: 16, Shift: 46)

![STAND_7_ACTUAL_SPEED](06_Stand_Speed/STAND_7_ACTUAL_SPEED_combined.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_LOAD | 29 | 269 | 🔴 |
| STAND_2_LOAD | 30 | 269 | 🔴 |
| STAND_3_LOAD | 31 | 270 | 🔴 |
| STAND_4_LOAD | 30 | 272 | 🔴 |
| STAND_5_LOAD | 31 | 276 | 🔴 |
| STAND_6_LOAD | 31 | 273 | 🔴 |
| STAND_7_LOAD | 31 | 273 | 🔴 |
| STAND_8_LOAD | 32 | 270 | 🔴 |
| STAND_9_LOAD | 30 | 274 | 🔴 |
| STAND_10_LOAD | 29 | 273 | 🔴 |
| STAND_11_LOAD | 28 | 273 | 🔴 |
| STAND_12_LOAD | 28 | 272 | 🔴 |
| STAND_13_LOAD | 28 | 272 | 🔴 |
| STAND_14_LOAD | 29 | 272 | 🔴 |
| FINISHING_BLOCK_LOAD | 29 | 273 | 🔴 |

#### 주요 태그 차트

**STAND_8_LOAD** (Drift: 32, Shift: 270)

![STAND_8_LOAD](07_Stand_Load/STAND_8_LOAD_combined.png)

**STAND_5_LOAD** (Drift: 31, Shift: 276)

![STAND_5_LOAD](07_Stand_Load/STAND_5_LOAD_combined.png)

**STAND_6_LOAD** (Drift: 31, Shift: 273)

![STAND_6_LOAD](07_Stand_Load/STAND_6_LOAD_combined.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 18 | 181 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 1 | 14 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 1 | 140 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 225 | 143 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 55 | 362 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 96 | 247 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 13 | 18 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 127 | 144 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 127 | 169 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_2_ACTUAL_TORQUE** (Drift: 225, Shift: 143)

![PINCHROLL_2_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_combined.png)

**PINCHROLL_4_REFERENCE_TORQUE** (Drift: 127, Shift: 169)

![PINCHROLL_4_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_combined.png)

**PINCHROLL_3_REFERENCE_TORQUE** (Drift: 127, Shift: 144)

![PINCHROLL_3_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_combined.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 드리프트 탐지: 6개
- 시프트 탐지: 6개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 3 | 47 | 🔴 |
| PR6L2_ACT_TORQUE | 2 | 55 | 🔴 |
| PR7L1_ACT_TORQUE | 6 | 33 | 🔴 |
| PR7L2_ACT_TORQUE | 4 | 15 | 🔴 |
| PR8L1_ACT_TORQUE | 50 | 165 | 🔴 |
| PR9L1_ACT_TORQUE | 205 | 210 | 🔴 |

#### 주요 태그 차트

**PR9L1_ACT_TORQUE** (Drift: 205, Shift: 210)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR8L1_ACT_TORQUE** (Drift: 50, Shift: 165)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_combined.png)

**PR7L1_ACT_TORQUE** (Drift: 6, Shift: 33)

![PR7L1_ACT_TORQUE](09_PR_Detailed/PR7L1_ACT_TORQUE_combined.png)



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
| 강종 | N5 |
| 규격 | D10 |
| 생성일시 | 2026-02-09 14:49:02 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

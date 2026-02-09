# 강종 [N5] | 규격: D20 CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5
**규격**: D20
**생성일시**: 2026-02-09 14:50:29

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
| 1 | PR9L1_ACT_TORQUE | PR 상세 토크 | 334 | 222 | 🔴 |
| 2 | PR8L1_ACT_TORQUE | PR 상세 토크 | 278 | 263 | 🔴 |
| 3 | PR7L1_ACT_TORQUE | PR 상세 토크 | 260 | 230 | 🔴 |
| 4 | PR6L2_ACT_TORQUE | PR 상세 토크 | 185 | 146 | 🔴 |
| 5 | PR6L1_ACT_TORQUE | PR 상세 토크 | 183 | 186 | 🔴 |
| 6 | PR7L2_ACT_TORQUE | PR 상세 토크 | 179 | 179 | 🔴 |
| 7 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 154 | 88 | 🔴 |
| 8 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 94 | 71 | 🔴 |
| 9 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 92 | 71 | 🔴 |
| 10 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 62 | 123 | 🔴 |
| 11 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 62 | 96 | 🔴 |
| 12 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 55 | 118 | 🔴 |
| 13 | FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 가열로 추출 온도 | 52 | 112 | 🔴 |
| 14 | FURNACE_O2_ANALYZER | 가열로 보조설비 | 33 | 57 | 🔴 |
| 15 | FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 스탠드 토크 | 27 | 128 | 🔴 |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 4 | 8 | 🔴 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 4 | 8 | 🔴 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 1 | 4 | 🔴 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 1 | 4 | 🔴 |

#### 주요 태그 차트

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 4, Shift: 8)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 4, Shift: 8)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)

**SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 1, Shift: 4)

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 6 | 21 | 🔴 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 7 | 22 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 2 | 4 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 3 | 3 | 🔴 |

#### 주요 태그 차트

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 7, Shift: 22)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 6, Shift: 21)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)

**SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 3, Shift: 3)

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 드리프트 탐지: 1개
- 시프트 탐지: 1개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 52 | 112 | 🔴 |

#### 주요 태그 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (Drift: 52, Shift: 112)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_combined.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_PRESSURE | 6 | 129 | 🔴 |
| FURNACE_O2_ANALYZER | 33 | 57 | 🔴 |
| MAIN_GAS_PRESSURE | 1 | 1 | 🔴 |
| MAIN_GAS_FLOW | 2 | 33 | 🔴 |
| MAIN_GAS_TEMPERATURE | 2 | 4 | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | 2 | 2 | 🔴 |
| COMBUSTION_AIR_TEMPERATURE | 3 | 8 | 🔴 |
| INDIRECT_COOLING_WATER_FLOW | 3 | 61 | 🔴 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 3 | 4 | 🔴 |

#### 주요 태그 차트

**FURNACE_O2_ANALYZER** (Drift: 33, Shift: 57)

![FURNACE_O2_ANALYZER](04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_combined.png)

**FURNACE_PRESSURE** (Drift: 6, Shift: 129)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_combined.png)

**INDIRECT_COOLING_WATER_FLOW** (Drift: 3, Shift: 61)

![INDIRECT_COOLING_WATER_FLOW](04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_combined.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 드리프트 탐지: 16개
- 시프트 탐지: 16개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_TORQUE | 9 | 234 | 🔴 |
| STAND_2_ACTUAL_TORQUE | 11 | 262 | 🔴 |
| STAND_3_ACTUAL_TORQUE | 14 | 225 | 🔴 |
| STAND_4_ACTUAL_TORQUE | 8 | 260 | 🔴 |
| STAND_5_ACTUAL_TORQUE | 9 | 259 | 🔴 |
| STAND_6_ACTUAL_TORQUE | 8 | 277 | 🔴 |
| STAND_7_ACTUAL_TORQUE | 10 | 257 | 🔴 |
| STAND_8_ACTUAL_TORQUE | 11 | 227 | 🔴 |
| STAND_9_ACTUAL_TORQUE | 12 | 246 | 🔴 |
| STAND_10_ACTUAL_TORQUE | 8 | 273 | 🔴 |
| STAND_11_ACTUAL_TORQUE | 9 | 270 | 🔴 |
| STAND_12_ACTUAL_TORQUE | 9 | 227 | 🔴 |
| STAND_13_ACTUAL_TORQUE | 13 | 237 | 🔴 |
| STAND_14_ACTUAL_TORQUE | 7 | 282 | 🔴 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 26 | 128 | 🔴 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 27 | 128 | 🔴 |

#### 주요 태그 차트

**FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE** (Drift: 27, Shift: 128)

![FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE](05_Stand_Torque/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_combined.png)

**FINISHING_BLOCK_MASTER_ACTUAL_TORQUE** (Drift: 26, Shift: 128)

![FINISHING_BLOCK_MASTER_ACTUAL_TORQUE](05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_combined.png)

**STAND_3_ACTUAL_TORQUE** (Drift: 14, Shift: 225)

![STAND_3_ACTUAL_TORQUE](05_Stand_Torque/STAND_3_ACTUAL_TORQUE_combined.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_SPEED | 5 | 23 | 🔴 |
| STAND_2_ACTUAL_SPEED | 1 | 24 | 🔴 |
| STAND_3_ACTUAL_SPEED | 1 | 23 | 🔴 |
| STAND_4_ACTUAL_SPEED | 1 | 23 | 🔴 |
| STAND_5_ACTUAL_SPEED | 1 | 23 | 🔴 |
| STAND_6_ACTUAL_SPEED | 1 | 23 | 🔴 |
| STAND_7_ACTUAL_SPEED | 1 | 23 | 🔴 |
| STAND_8_ACTUAL_SPEED | 3 | 25 | 🔴 |
| STAND_9_ACTUAL_SPEED | 1 | 24 | 🔴 |
| STAND_10_ACTUAL_SPEED | 1 | 24 | 🔴 |
| STAND_11_ACTUAL_SPEED | 1 | 23 | 🔴 |
| STAND_12_ACTUAL_SPEED | 1 | 23 | 🔴 |
| STAND_13_ACTUAL_SPEED | 9 | 24 | 🔴 |
| STAND_14_ACTUAL_SPEED | 1 | 23 | 🔴 |
| FINISHING_BLOCK_ACTUAL_SPEED | 2 | 28 | 🔴 |

#### 주요 태그 차트

**STAND_13_ACTUAL_SPEED** (Drift: 9, Shift: 24)

![STAND_13_ACTUAL_SPEED](06_Stand_Speed/STAND_13_ACTUAL_SPEED_combined.png)

**STAND_1_ACTUAL_SPEED** (Drift: 5, Shift: 23)

![STAND_1_ACTUAL_SPEED](06_Stand_Speed/STAND_1_ACTUAL_SPEED_combined.png)

**STAND_8_ACTUAL_SPEED** (Drift: 3, Shift: 25)

![STAND_8_ACTUAL_SPEED](06_Stand_Speed/STAND_8_ACTUAL_SPEED_combined.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_LOAD | 13 | 272 | 🔴 |
| STAND_2_LOAD | 12 | 271 | 🔴 |
| STAND_3_LOAD | 12 | 280 | 🔴 |
| STAND_4_LOAD | 12 | 281 | 🔴 |
| STAND_5_LOAD | 11 | 281 | 🔴 |
| STAND_6_LOAD | 11 | 282 | 🔴 |
| STAND_7_LOAD | 10 | 279 | 🔴 |
| STAND_8_LOAD | 10 | 275 | 🔴 |
| STAND_9_LOAD | 11 | 271 | 🔴 |
| STAND_10_LOAD | 13 | 270 | 🔴 |
| STAND_11_LOAD | 13 | 269 | 🔴 |
| STAND_12_LOAD | 13 | 268 | 🔴 |
| STAND_13_LOAD | 13 | 268 | 🔴 |
| STAND_14_LOAD | 13 | 269 | 🔴 |
| FINISHING_BLOCK_LOAD | 13 | 270 | 🔴 |

#### 주요 태그 차트

**STAND_1_LOAD** (Drift: 13, Shift: 272)

![STAND_1_LOAD](07_Stand_Load/STAND_1_LOAD_combined.png)

**STAND_10_LOAD** (Drift: 13, Shift: 270)

![STAND_10_LOAD](07_Stand_Load/STAND_10_LOAD_combined.png)

**FINISHING_BLOCK_LOAD** (Drift: 13, Shift: 270)

![FINISHING_BLOCK_LOAD](07_Stand_Load/FINISHING_BLOCK_LOAD_combined.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 62 | 96 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 5 | 5 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 5 | 5 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 154 | 88 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 92 | 71 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 94 | 71 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 13 | 15 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 55 | 118 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 62 | 123 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_2_ACTUAL_TORQUE** (Drift: 154, Shift: 88)

![PINCHROLL_2_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_combined.png)

**PINCHROLL_4_ACTUAL_TORQUE** (Drift: 94, Shift: 71)

![PINCHROLL_4_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_combined.png)

**PINCHROLL_3_ACTUAL_TORQUE** (Drift: 92, Shift: 71)

![PINCHROLL_3_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_combined.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 드리프트 탐지: 6개
- 시프트 탐지: 6개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 183 | 186 | 🔴 |
| PR6L2_ACT_TORQUE | 185 | 146 | 🔴 |
| PR7L1_ACT_TORQUE | 260 | 230 | 🔴 |
| PR7L2_ACT_TORQUE | 179 | 179 | 🔴 |
| PR8L1_ACT_TORQUE | 278 | 263 | 🔴 |
| PR9L1_ACT_TORQUE | 334 | 222 | 🔴 |

#### 주요 태그 차트

**PR9L1_ACT_TORQUE** (Drift: 334, Shift: 222)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR8L1_ACT_TORQUE** (Drift: 278, Shift: 263)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_combined.png)

**PR7L1_ACT_TORQUE** (Drift: 260, Shift: 230)

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
| 규격 | D20 |
| 생성일시 | 2026-02-09 14:50:29 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

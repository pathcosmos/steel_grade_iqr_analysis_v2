# 강종 [D5] | 규격: D10 CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D5
**규격**: D10
**생성일시**: 2026-02-09 14:52:38

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
| 1 | PR9L1_ACT_TORQUE | PR 상세 토크 | 868 | 475 | 🔴 |
| 2 | PR8L1_ACT_TORQUE | PR 상세 토크 | 785 | 823 | 🔴 |
| 3 | FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 가열로 추출 온도 | 587 | 789 | 🔴 |
| 4 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 332 | 415 | 🔴 |
| 5 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 310 | 330 | 🔴 |
| 6 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 241 | 317 | 🔴 |
| 7 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 205 | 257 | 🔴 |
| 8 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 156 | 185 | 🔴 |
| 9 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 148 | 520 | 🔴 |
| 10 | STAND_2_ACTUAL_TORQUE | 스탠드 토크 | 109 | 579 | 🔴 |
| 11 | STAND_14_ACTUAL_TORQUE | 스탠드 토크 | 105 | 342 | 🔴 |
| 12 | STAND_4_LOAD | 스탠드 부하 | 104 | 291 | 🔴 |
| 13 | STAND_11_ACTUAL_TORQUE | 스탠드 토크 | 103 | 249 | 🔴 |
| 14 | STAND_3_LOAD | 스탠드 부하 | 102 | 287 | 🔴 |
| 15 | STAND_3_ACTUAL_TORQUE | 스탠드 토크 | 101 | 462 | 🔴 |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 35 | 11 | 🔴 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 34 | 10 | 🔴 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 14 | 5 | 🔴 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 13 | 5 | 🔴 |

#### 주요 태그 차트

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 35, Shift: 11)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 34, Shift: 10)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)

**SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 14, Shift: 5)

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 41 | 51 | 🔴 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 38 | 58 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 26 | 5 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 25 | 5 | 🔴 |

#### 주요 태그 차트

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 41, Shift: 51)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 38, Shift: 58)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)

**SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 26, Shift: 5)

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 드리프트 탐지: 1개
- 시프트 탐지: 1개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 587 | 789 | 🔴 |

#### 주요 태그 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (Drift: 587, Shift: 789)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_combined.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_PRESSURE | 48 | 570 | 🔴 |
| FURNACE_O2_ANALYZER | 70 | 122 | 🔴 |
| MAIN_GAS_PRESSURE | 4 | 1 | 🔴 |
| MAIN_GAS_FLOW | 15 | 272 | 🔴 |
| MAIN_GAS_TEMPERATURE | 1 | 13 | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | 3 | 3 | 🔴 |
| COMBUSTION_AIR_TEMPERATURE | 1 | 41 | 🔴 |
| INDIRECT_COOLING_WATER_FLOW | 1 | 7 | 🔴 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 2 | 27 | 🔴 |

#### 주요 태그 차트

**FURNACE_O2_ANALYZER** (Drift: 70, Shift: 122)

![FURNACE_O2_ANALYZER](04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_combined.png)

**FURNACE_PRESSURE** (Drift: 48, Shift: 570)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_combined.png)

**MAIN_GAS_FLOW** (Drift: 15, Shift: 272)

![MAIN_GAS_FLOW](04_Furnace_Auxiliary/MAIN_GAS_FLOW_combined.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 드리프트 탐지: 16개
- 시프트 탐지: 16개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_TORQUE | 80 | 595 | 🔴 |
| STAND_2_ACTUAL_TORQUE | 109 | 579 | 🔴 |
| STAND_3_ACTUAL_TORQUE | 101 | 462 | 🔴 |
| STAND_4_ACTUAL_TORQUE | 79 | 540 | 🔴 |
| STAND_5_ACTUAL_TORQUE | 89 | 523 | 🔴 |
| STAND_6_ACTUAL_TORQUE | 83 | 499 | 🔴 |
| STAND_7_ACTUAL_TORQUE | 80 | 573 | 🔴 |
| STAND_8_ACTUAL_TORQUE | 71 | 470 | 🔴 |
| STAND_9_ACTUAL_TORQUE | 92 | 474 | 🔴 |
| STAND_10_ACTUAL_TORQUE | 75 | 353 | 🔴 |
| STAND_11_ACTUAL_TORQUE | 103 | 249 | 🔴 |
| STAND_12_ACTUAL_TORQUE | 85 | 324 | 🔴 |
| STAND_13_ACTUAL_TORQUE | 78 | 252 | 🔴 |
| STAND_14_ACTUAL_TORQUE | 105 | 342 | 🔴 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 64 | 204 | 🔴 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 68 | 204 | 🔴 |

#### 주요 태그 차트

**STAND_2_ACTUAL_TORQUE** (Drift: 109, Shift: 579)

![STAND_2_ACTUAL_TORQUE](05_Stand_Torque/STAND_2_ACTUAL_TORQUE_combined.png)

**STAND_14_ACTUAL_TORQUE** (Drift: 105, Shift: 342)

![STAND_14_ACTUAL_TORQUE](05_Stand_Torque/STAND_14_ACTUAL_TORQUE_combined.png)

**STAND_11_ACTUAL_TORQUE** (Drift: 103, Shift: 249)

![STAND_11_ACTUAL_TORQUE](05_Stand_Torque/STAND_11_ACTUAL_TORQUE_combined.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_SPEED | 24 | 104 | 🔴 |
| STAND_2_ACTUAL_SPEED | 51 | 138 | 🔴 |
| STAND_3_ACTUAL_SPEED | 51 | 103 | 🔴 |
| STAND_4_ACTUAL_SPEED | 40 | 104 | 🔴 |
| STAND_5_ACTUAL_SPEED | 53 | 103 | 🔴 |
| STAND_6_ACTUAL_SPEED | 52 | 103 | 🔴 |
| STAND_7_ACTUAL_SPEED | 45 | 104 | 🔴 |
| STAND_8_ACTUAL_SPEED | 33 | 104 | 🔴 |
| STAND_9_ACTUAL_SPEED | 31 | 109 | 🔴 |
| STAND_10_ACTUAL_SPEED | 55 | 107 | 🔴 |
| STAND_11_ACTUAL_SPEED | 50 | 107 | 🔴 |
| STAND_12_ACTUAL_SPEED | 59 | 107 | 🔴 |
| STAND_13_ACTUAL_SPEED | 19 | 107 | 🔴 |
| STAND_14_ACTUAL_SPEED | 29 | 108 | 🔴 |
| FINISHING_BLOCK_ACTUAL_SPEED | 65 | 117 | 🔴 |

#### 주요 태그 차트

**FINISHING_BLOCK_ACTUAL_SPEED** (Drift: 65, Shift: 117)

![FINISHING_BLOCK_ACTUAL_SPEED](06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_combined.png)

**STAND_12_ACTUAL_SPEED** (Drift: 59, Shift: 107)

![STAND_12_ACTUAL_SPEED](06_Stand_Speed/STAND_12_ACTUAL_SPEED_combined.png)

**STAND_10_ACTUAL_SPEED** (Drift: 55, Shift: 107)

![STAND_10_ACTUAL_SPEED](06_Stand_Speed/STAND_10_ACTUAL_SPEED_combined.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_LOAD | 100 | 287 | 🔴 |
| STAND_2_LOAD | 101 | 286 | 🔴 |
| STAND_3_LOAD | 102 | 287 | 🔴 |
| STAND_4_LOAD | 104 | 291 | 🔴 |
| STAND_5_LOAD | 100 | 290 | 🔴 |
| STAND_6_LOAD | 95 | 286 | 🔴 |
| STAND_7_LOAD | 97 | 284 | 🔴 |
| STAND_8_LOAD | 98 | 284 | 🔴 |
| STAND_9_LOAD | 98 | 282 | 🔴 |
| STAND_10_LOAD | 99 | 287 | 🔴 |
| STAND_11_LOAD | 101 | 288 | 🔴 |
| STAND_12_LOAD | 97 | 289 | 🔴 |
| STAND_13_LOAD | 97 | 289 | 🔴 |
| STAND_14_LOAD | 97 | 286 | 🔴 |
| FINISHING_BLOCK_LOAD | 101 | 289 | 🔴 |

#### 주요 태그 차트

**STAND_4_LOAD** (Drift: 104, Shift: 291)

![STAND_4_LOAD](07_Stand_Load/STAND_4_LOAD_combined.png)

**STAND_3_LOAD** (Drift: 102, Shift: 287)

![STAND_3_LOAD](07_Stand_Load/STAND_3_LOAD_combined.png)

**FINISHING_BLOCK_LOAD** (Drift: 101, Shift: 289)

![FINISHING_BLOCK_LOAD](07_Stand_Load/FINISHING_BLOCK_LOAD_combined.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 156 | 185 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 28 | 32 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 27 | 28 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 310 | 330 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 241 | 317 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 148 | 520 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 43 | 52 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 205 | 257 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 332 | 415 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_4_REFERENCE_TORQUE** (Drift: 332, Shift: 415)

![PINCHROLL_4_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_combined.png)

**PINCHROLL_2_ACTUAL_TORQUE** (Drift: 310, Shift: 330)

![PINCHROLL_2_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_combined.png)

**PINCHROLL_3_ACTUAL_TORQUE** (Drift: 241, Shift: 317)

![PINCHROLL_3_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_combined.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 드리프트 탐지: 6개
- 시프트 탐지: 6개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 11 | 370 | 🔴 |
| PR6L2_ACT_TORQUE | 14 | 285 | 🔴 |
| PR7L1_ACT_TORQUE | 11 | 72 | 🔴 |
| PR7L2_ACT_TORQUE | 14 | 72 | 🔴 |
| PR8L1_ACT_TORQUE | 785 | 823 | 🔴 |
| PR9L1_ACT_TORQUE | 868 | 475 | 🔴 |

#### 주요 태그 차트

**PR9L1_ACT_TORQUE** (Drift: 868, Shift: 475)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR8L1_ACT_TORQUE** (Drift: 785, Shift: 823)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_combined.png)

**PR6L2_ACT_TORQUE** (Drift: 14, Shift: 285)

![PR6L2_ACT_TORQUE](09_PR_Detailed/PR6L2_ACT_TORQUE_combined.png)



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
| 강종 | D5 |
| 규격 | D10 |
| 생성일시 | 2026-02-09 14:52:38 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

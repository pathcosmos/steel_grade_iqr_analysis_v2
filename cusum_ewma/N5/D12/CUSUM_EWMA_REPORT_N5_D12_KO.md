# 강종 [N5] | 규격: D12 CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5
**규격**: D12
**생성일시**: 2026-02-09 14:45:31

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
| 1 | PR8L1_ACT_TORQUE | PR 상세 토크 | 1061 | 894 | 🔴 |
| 2 | PR9L1_ACT_TORQUE | PR 상세 토크 | 1023 | 779 | 🔴 |
| 3 | FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 가열로 추출 온도 | 769 | 856 | 🔴 |
| 4 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 338 | 480 | 🔴 |
| 5 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 332 | 447 | 🔴 |
| 6 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 321 | 510 | 🔴 |
| 7 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 311 | 450 | 🔴 |
| 8 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 289 | 429 | 🔴 |
| 9 | STAND_2_LOAD | 스탠드 부하 | 259 | 392 | 🔴 |
| 10 | FINISHING_BLOCK_LOAD | 스탠드 부하 | 254 | 387 | 🔴 |
| 11 | STAND_1_LOAD | 스탠드 부하 | 252 | 390 | 🔴 |
| 12 | STAND_3_LOAD | 스탠드 부하 | 249 | 394 | 🔴 |
| 13 | STAND_10_LOAD | 스탠드 부하 | 249 | 390 | 🔴 |
| 14 | STAND_12_LOAD | 스탠드 부하 | 249 | 388 | 🔴 |
| 15 | STAND_13_LOAD | 스탠드 부하 | 249 | 388 | 🔴 |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 38 | 123 | 🔴 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 41 | 120 | 🔴 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 14 | 64 | 🔴 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 20 | 94 | 🔴 |

#### 주요 태그 차트

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 41, Shift: 120)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 38, Shift: 123)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 20, Shift: 94)

![SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 47 | 195 | 🔴 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 38 | 209 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 32 | 51 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 29 | 53 | 🔴 |

#### 주요 태그 차트

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 47, Shift: 195)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 38, Shift: 209)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)

**SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 32, Shift: 51)

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 드리프트 탐지: 1개
- 시프트 탐지: 1개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 769 | 856 | 🔴 |

#### 주요 태그 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (Drift: 769, Shift: 856)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_combined.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_PRESSURE | 70 | 480 | 🔴 |
| FURNACE_O2_ANALYZER | 75 | 151 | 🔴 |
| MAIN_GAS_PRESSURE | 89 | 130 | 🔴 |
| MAIN_GAS_FLOW | 28 | 242 | 🔴 |
| MAIN_GAS_TEMPERATURE | 3 | 26 | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | 43 | 63 | 🔴 |
| COMBUSTION_AIR_TEMPERATURE | 7 | 76 | 🔴 |
| INDIRECT_COOLING_WATER_FLOW | 1 | 308 | 🔴 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 2 | 17 | 🔴 |

#### 주요 태그 차트

**MAIN_GAS_PRESSURE** (Drift: 89, Shift: 130)

![MAIN_GAS_PRESSURE](04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_combined.png)

**FURNACE_O2_ANALYZER** (Drift: 75, Shift: 151)

![FURNACE_O2_ANALYZER](04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_combined.png)

**FURNACE_PRESSURE** (Drift: 70, Shift: 480)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_combined.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 드리프트 탐지: 16개
- 시프트 탐지: 16개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_TORQUE | 193 | 786 | 🔴 |
| STAND_2_ACTUAL_TORQUE | 127 | 681 | 🔴 |
| STAND_3_ACTUAL_TORQUE | 185 | 698 | 🔴 |
| STAND_4_ACTUAL_TORQUE | 209 | 825 | 🔴 |
| STAND_5_ACTUAL_TORQUE | 168 | 694 | 🔴 |
| STAND_6_ACTUAL_TORQUE | 201 | 752 | 🔴 |
| STAND_7_ACTUAL_TORQUE | 146 | 581 | 🔴 |
| STAND_8_ACTUAL_TORQUE | 166 | 734 | 🔴 |
| STAND_9_ACTUAL_TORQUE | 207 | 759 | 🔴 |
| STAND_10_ACTUAL_TORQUE | 207 | 726 | 🔴 |
| STAND_11_ACTUAL_TORQUE | 171 | 570 | 🔴 |
| STAND_12_ACTUAL_TORQUE | 183 | 613 | 🔴 |
| STAND_13_ACTUAL_TORQUE | 237 | 444 | 🔴 |
| STAND_14_ACTUAL_TORQUE | 168 | 510 | 🔴 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 180 | 409 | 🔴 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 179 | 410 | 🔴 |

#### 주요 태그 차트

**STAND_13_ACTUAL_TORQUE** (Drift: 237, Shift: 444)

![STAND_13_ACTUAL_TORQUE](05_Stand_Torque/STAND_13_ACTUAL_TORQUE_combined.png)

**STAND_4_ACTUAL_TORQUE** (Drift: 209, Shift: 825)

![STAND_4_ACTUAL_TORQUE](05_Stand_Torque/STAND_4_ACTUAL_TORQUE_combined.png)

**STAND_9_ACTUAL_TORQUE** (Drift: 207, Shift: 759)

![STAND_9_ACTUAL_TORQUE](05_Stand_Torque/STAND_9_ACTUAL_TORQUE_combined.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_SPEED | 82 | 155 | 🔴 |
| STAND_2_ACTUAL_SPEED | 62 | 156 | 🔴 |
| STAND_3_ACTUAL_SPEED | 72 | 155 | 🔴 |
| STAND_4_ACTUAL_SPEED | 90 | 155 | 🔴 |
| STAND_5_ACTUAL_SPEED | 86 | 155 | 🔴 |
| STAND_6_ACTUAL_SPEED | 93 | 155 | 🔴 |
| STAND_7_ACTUAL_SPEED | 101 | 156 | 🔴 |
| STAND_8_ACTUAL_SPEED | 89 | 155 | 🔴 |
| STAND_9_ACTUAL_SPEED | 71 | 170 | 🔴 |
| STAND_10_ACTUAL_SPEED | 106 | 170 | 🔴 |
| STAND_11_ACTUAL_SPEED | 94 | 169 | 🔴 |
| STAND_12_ACTUAL_SPEED | 102 | 170 | 🔴 |
| STAND_13_ACTUAL_SPEED | 59 | 169 | 🔴 |
| STAND_14_ACTUAL_SPEED | 90 | 169 | 🔴 |
| FINISHING_BLOCK_ACTUAL_SPEED | 98 | 180 | 🔴 |

#### 주요 태그 차트

**STAND_10_ACTUAL_SPEED** (Drift: 106, Shift: 170)

![STAND_10_ACTUAL_SPEED](06_Stand_Speed/STAND_10_ACTUAL_SPEED_combined.png)

**STAND_12_ACTUAL_SPEED** (Drift: 102, Shift: 170)

![STAND_12_ACTUAL_SPEED](06_Stand_Speed/STAND_12_ACTUAL_SPEED_combined.png)

**STAND_7_ACTUAL_SPEED** (Drift: 101, Shift: 156)

![STAND_7_ACTUAL_SPEED](06_Stand_Speed/STAND_7_ACTUAL_SPEED_combined.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_LOAD | 252 | 390 | 🔴 |
| STAND_2_LOAD | 259 | 392 | 🔴 |
| STAND_3_LOAD | 249 | 394 | 🔴 |
| STAND_4_LOAD | 239 | 398 | 🔴 |
| STAND_5_LOAD | 233 | 399 | 🔴 |
| STAND_6_LOAD | 240 | 398 | 🔴 |
| STAND_7_LOAD | 246 | 398 | 🔴 |
| STAND_8_LOAD | 243 | 398 | 🔴 |
| STAND_9_LOAD | 247 | 393 | 🔴 |
| STAND_10_LOAD | 249 | 390 | 🔴 |
| STAND_11_LOAD | 248 | 390 | 🔴 |
| STAND_12_LOAD | 249 | 388 | 🔴 |
| STAND_13_LOAD | 249 | 388 | 🔴 |
| STAND_14_LOAD | 249 | 386 | 🔴 |
| FINISHING_BLOCK_LOAD | 254 | 387 | 🔴 |

#### 주요 태그 차트

**STAND_2_LOAD** (Drift: 259, Shift: 392)

![STAND_2_LOAD](07_Stand_Load/STAND_2_LOAD_combined.png)

**FINISHING_BLOCK_LOAD** (Drift: 254, Shift: 387)

![FINISHING_BLOCK_LOAD](07_Stand_Load/FINISHING_BLOCK_LOAD_combined.png)

**STAND_1_LOAD** (Drift: 252, Shift: 390)

![STAND_1_LOAD](07_Stand_Load/STAND_1_LOAD_combined.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 145 | 371 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 27 | 33 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 23 | 24 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 332 | 447 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 289 | 429 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 311 | 450 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 58 | 64 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 338 | 480 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 321 | 510 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_3_REFERENCE_TORQUE** (Drift: 338, Shift: 480)

![PINCHROLL_3_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_combined.png)

**PINCHROLL_2_ACTUAL_TORQUE** (Drift: 332, Shift: 447)

![PINCHROLL_2_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_combined.png)

**PINCHROLL_4_REFERENCE_TORQUE** (Drift: 321, Shift: 510)

![PINCHROLL_4_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_combined.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 드리프트 탐지: 6개
- 시프트 탐지: 6개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 11 | 648 | 🔴 |
| PR6L2_ACT_TORQUE | 11 | 492 | 🔴 |
| PR7L1_ACT_TORQUE | 15 | 64 | 🔴 |
| PR7L2_ACT_TORQUE | 14 | 58 | 🔴 |
| PR8L1_ACT_TORQUE | 1061 | 894 | 🔴 |
| PR9L1_ACT_TORQUE | 1023 | 779 | 🔴 |

#### 주요 태그 차트

**PR8L1_ACT_TORQUE** (Drift: 1061, Shift: 894)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_combined.png)

**PR9L1_ACT_TORQUE** (Drift: 1023, Shift: 779)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR7L1_ACT_TORQUE** (Drift: 15, Shift: 64)

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
| 규격 | D12 |
| 생성일시 | 2026-02-09 14:45:31 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

# 강종 [D5] | 규격: D13 CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D5
**규격**: D13
**생성일시**: 2026-02-09 14:54:00

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
| 1 | PR7L1_ACT_TORQUE | PR 상세 토크 | 205 | 119 | 🔴 |
| 2 | PR9L1_ACT_TORQUE | PR 상세 토크 | 204 | 117 | 🔴 |
| 3 | PR8L1_ACT_TORQUE | PR 상세 토크 | 166 | 123 | 🔴 |
| 4 | PR7L2_ACT_TORQUE | PR 상세 토크 | 152 | 112 | 🔴 |
| 5 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 108 | 76 | 🔴 |
| 6 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 108 | 76 | 🔴 |
| 7 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 82 | 63 | 🔴 |
| 8 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 54 | 47 | 🔴 |
| 9 | FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 가열로 추출 온도 | 53 | 131 | 🔴 |
| 10 | PR6L1_ACT_TORQUE | PR 상세 토크 | 36 | 101 | 🔴 |
| 11 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 32 | 62 | 🔴 |
| 12 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 30 | 62 | 🔴 |
| 13 | STAND_1_ACTUAL_TORQUE | 스탠드 토크 | 27 | 67 | 🔴 |
| 14 | STAND_2_ACTUAL_TORQUE | 스탠드 토크 | 22 | 115 | 🔴 |
| 15 | STAND_5_ACTUAL_TORQUE | 스탠드 토크 | 22 | 55 | 🔴 |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 10 | 30 | 🔴 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 9 | 28 | 🔴 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 5 | 15 | 🔴 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 5 | 12 | 🔴 |

#### 주요 태그 차트

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 10, Shift: 30)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 9, Shift: 28)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)

**SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 5, Shift: 15)

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 2 | 28 | 🔴 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 3 | 29 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 7 | 9 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 7 | 13 | 🔴 |

#### 주요 태그 차트

**SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 7, Shift: 13)

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)

**SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 7, Shift: 9)

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 3, Shift: 29)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 드리프트 탐지: 1개
- 시프트 탐지: 1개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 53 | 131 | 🔴 |

#### 주요 태그 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (Drift: 53, Shift: 131)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_combined.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_PRESSURE | 19 | 135 | 🔴 |
| FURNACE_O2_ANALYZER | 4 | 64 | 🔴 |
| MAIN_GAS_PRESSURE | 18 | 95 | 🔴 |
| MAIN_GAS_FLOW | 4 | 39 | 🔴 |
| MAIN_GAS_TEMPERATURE | 1 | 4 | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | 1 | 3 | 🔴 |
| COMBUSTION_AIR_TEMPERATURE | 1 | 14 | 🔴 |
| INDIRECT_COOLING_WATER_FLOW | 4 | 43 | 🔴 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 1 | 15 | 🔴 |

#### 주요 태그 차트

**FURNACE_PRESSURE** (Drift: 19, Shift: 135)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_combined.png)

**MAIN_GAS_PRESSURE** (Drift: 18, Shift: 95)

![MAIN_GAS_PRESSURE](04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_combined.png)

**FURNACE_O2_ANALYZER** (Drift: 4, Shift: 64)

![FURNACE_O2_ANALYZER](04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_combined.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 드리프트 탐지: 16개
- 시프트 탐지: 16개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_TORQUE | 27 | 67 | 🔴 |
| STAND_2_ACTUAL_TORQUE | 22 | 115 | 🔴 |
| STAND_3_ACTUAL_TORQUE | 18 | 53 | 🔴 |
| STAND_4_ACTUAL_TORQUE | 19 | 54 | 🔴 |
| STAND_5_ACTUAL_TORQUE | 22 | 55 | 🔴 |
| STAND_6_ACTUAL_TORQUE | 10 | 148 | 🔴 |
| STAND_7_ACTUAL_TORQUE | 16 | 46 | 🔴 |
| STAND_8_ACTUAL_TORQUE | 8 | 132 | 🔴 |
| STAND_9_ACTUAL_TORQUE | 5 | 206 | 🔴 |
| STAND_10_ACTUAL_TORQUE | 11 | 160 | 🔴 |
| STAND_11_ACTUAL_TORQUE | 13 | 130 | 🔴 |
| STAND_12_ACTUAL_TORQUE | 16 | 99 | 🔴 |
| STAND_13_ACTUAL_TORQUE | 19 | 51 | 🔴 |
| STAND_14_ACTUAL_TORQUE | 19 | 94 | 🔴 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 13 | 130 | 🔴 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 13 | 131 | 🔴 |

#### 주요 태그 차트

**STAND_1_ACTUAL_TORQUE** (Drift: 27, Shift: 67)

![STAND_1_ACTUAL_TORQUE](05_Stand_Torque/STAND_1_ACTUAL_TORQUE_combined.png)

**STAND_2_ACTUAL_TORQUE** (Drift: 22, Shift: 115)

![STAND_2_ACTUAL_TORQUE](05_Stand_Torque/STAND_2_ACTUAL_TORQUE_combined.png)

**STAND_5_ACTUAL_TORQUE** (Drift: 22, Shift: 55)

![STAND_5_ACTUAL_TORQUE](05_Stand_Torque/STAND_5_ACTUAL_TORQUE_combined.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_SPEED | 7 | 51 | 🔴 |
| STAND_2_ACTUAL_SPEED | 2 | 33 | 🔴 |
| STAND_3_ACTUAL_SPEED | 2 | 33 | 🔴 |
| STAND_4_ACTUAL_SPEED | 3 | 33 | 🔴 |
| STAND_5_ACTUAL_SPEED | 2 | 33 | 🔴 |
| STAND_6_ACTUAL_SPEED | 3 | 33 | 🔴 |
| STAND_7_ACTUAL_SPEED | 3 | 34 | 🔴 |
| STAND_8_ACTUAL_SPEED | 13 | 33 | 🔴 |
| STAND_9_ACTUAL_SPEED | 7 | 34 | 🔴 |
| STAND_10_ACTUAL_SPEED | 6 | 34 | 🔴 |
| STAND_11_ACTUAL_SPEED | 6 | 34 | 🔴 |
| STAND_12_ACTUAL_SPEED | 6 | 34 | 🔴 |
| STAND_13_ACTUAL_SPEED | 2 | 34 | 🔴 |
| STAND_14_ACTUAL_SPEED | 4 | 34 | 🔴 |
| FINISHING_BLOCK_ACTUAL_SPEED | 8 | 34 | 🔴 |

#### 주요 태그 차트

**STAND_8_ACTUAL_SPEED** (Drift: 13, Shift: 33)

![STAND_8_ACTUAL_SPEED](06_Stand_Speed/STAND_8_ACTUAL_SPEED_combined.png)

**FINISHING_BLOCK_ACTUAL_SPEED** (Drift: 8, Shift: 34)

![FINISHING_BLOCK_ACTUAL_SPEED](06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_combined.png)

**STAND_1_ACTUAL_SPEED** (Drift: 7, Shift: 51)

![STAND_1_ACTUAL_SPEED](06_Stand_Speed/STAND_1_ACTUAL_SPEED_combined.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_LOAD | 12 | 141 | 🔴 |
| STAND_2_LOAD | 12 | 140 | 🔴 |
| STAND_3_LOAD | 12 | 139 | 🔴 |
| STAND_4_LOAD | 13 | 139 | 🔴 |
| STAND_5_LOAD | 13 | 139 | 🔴 |
| STAND_6_LOAD | 13 | 141 | 🔴 |
| STAND_7_LOAD | 13 | 140 | 🔴 |
| STAND_8_LOAD | 13 | 139 | 🔴 |
| STAND_9_LOAD | 12 | 141 | 🔴 |
| STAND_10_LOAD | 12 | 142 | 🔴 |
| STAND_11_LOAD | 12 | 142 | 🔴 |
| STAND_12_LOAD | 12 | 142 | 🔴 |
| STAND_13_LOAD | 12 | 142 | 🔴 |
| STAND_14_LOAD | 13 | 142 | 🔴 |
| FINISHING_BLOCK_LOAD | 13 | 142 | 🔴 |

#### 주요 태그 차트

**STAND_14_LOAD** (Drift: 13, Shift: 142)

![STAND_14_LOAD](07_Stand_Load/STAND_14_LOAD_combined.png)

**FINISHING_BLOCK_LOAD** (Drift: 13, Shift: 142)

![FINISHING_BLOCK_LOAD](07_Stand_Load/FINISHING_BLOCK_LOAD_combined.png)

**STAND_6_LOAD** (Drift: 13, Shift: 141)

![STAND_6_LOAD](07_Stand_Load/STAND_6_LOAD_combined.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 54 | 47 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 15 | 17 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 9 | 12 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 82 | 63 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 30 | 62 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 32 | 62 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 18 | 18 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 108 | 76 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 108 | 76 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_3_REFERENCE_TORQUE** (Drift: 108, Shift: 76)

![PINCHROLL_3_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_combined.png)

**PINCHROLL_4_REFERENCE_TORQUE** (Drift: 108, Shift: 76)

![PINCHROLL_4_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_combined.png)

**PINCHROLL_2_ACTUAL_TORQUE** (Drift: 82, Shift: 63)

![PINCHROLL_2_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_combined.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 드리프트 탐지: 6개
- 시프트 탐지: 6개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 36 | 101 | 🔴 |
| PR6L2_ACT_TORQUE | 2 | 18 | 🔴 |
| PR7L1_ACT_TORQUE | 205 | 119 | 🔴 |
| PR7L2_ACT_TORQUE | 152 | 112 | 🔴 |
| PR8L1_ACT_TORQUE | 166 | 123 | 🔴 |
| PR9L1_ACT_TORQUE | 204 | 117 | 🔴 |

#### 주요 태그 차트

**PR7L1_ACT_TORQUE** (Drift: 205, Shift: 119)

![PR7L1_ACT_TORQUE](09_PR_Detailed/PR7L1_ACT_TORQUE_combined.png)

**PR9L1_ACT_TORQUE** (Drift: 204, Shift: 117)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR8L1_ACT_TORQUE** (Drift: 166, Shift: 123)

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
| 강종 | D5 |
| 규격 | D13 |
| 생성일시 | 2026-02-09 14:54:00 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

# 강종 [B5] | 규격: D13 CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: B5
**규격**: D13
**생성일시**: 2026-02-09 14:59:22

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
| 🟠 시프트 탐지 | 75개 | 94.9% |
| 🟡 경고 | 0개 | 0.0% |
| 🟢 안정 | 0개 | 0.0% |

---

## 상위 문제 태그 (드리프트 빈도 기준)

| 순위 | 태그 | 카테고리 | CUSUM 드리프트 | EWMA 시프트 | 상태 |
|------|------|----------|----------------|-------------|------|
| 1 | FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 가열로 추출 온도 | 123 | 108 | 🔴 |
| 2 | STAND_2_ACTUAL_TORQUE | 스탠드 토크 | 79 | 62 | 🔴 |
| 3 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 68 | 70 | 🔴 |
| 4 | STAND_7_ACTUAL_TORQUE | 스탠드 토크 | 64 | 59 | 🔴 |
| 5 | STAND_9_ACTUAL_TORQUE | 스탠드 토크 | 63 | 61 | 🔴 |
| 6 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 61 | 70 | 🔴 |
| 7 | STAND_3_ACTUAL_TORQUE | 스탠드 토크 | 60 | 61 | 🔴 |
| 8 | STAND_5_ACTUAL_TORQUE | 스탠드 토크 | 57 | 55 | 🔴 |
| 9 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 57 | 51 | 🔴 |
| 10 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 56 | 73 | 🔴 |
| 11 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 56 | 73 | 🔴 |
| 12 | STAND_1_ACTUAL_TORQUE | 스탠드 토크 | 56 | 63 | 🔴 |
| 13 | STAND_8_ACTUAL_TORQUE | 스탠드 토크 | 54 | 61 | 🔴 |
| 14 | STAND_13_ACTUAL_TORQUE | 스탠드 토크 | 54 | 57 | 🔴 |
| 15 | STAND_10_ACTUAL_TORQUE | 스탠드 토크 | 53 | 62 | 🔴 |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 32 | 57 | 🔴 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 32 | 58 | 🔴 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 29 | 58 | 🔴 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 28 | 46 | 🔴 |

#### 주요 태그 차트

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 32, Shift: 58)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 32, Shift: 57)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 29, Shift: 58)

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 16 | 17 | 🔴 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 16 | 19 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 13 | 64 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 14 | 55 | 🔴 |

#### 주요 태그 차트

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 16, Shift: 19)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 16, Shift: 17)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)

**SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 14, Shift: 55)

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 드리프트 탐지: 1개
- 시프트 탐지: 1개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 123 | 108 | 🔴 |

#### 주요 태그 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (Drift: 123, Shift: 108)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_combined.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_PRESSURE | 20 | 114 | 🔴 |
| FURNACE_O2_ANALYZER | 3 | 121 | 🔴 |
| MAIN_GAS_PRESSURE | 17 | 94 | 🔴 |
| MAIN_GAS_FLOW | 16 | 30 | 🔴 |
| MAIN_GAS_TEMPERATURE | 2 | 9 | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | 5 | 13 | 🔴 |
| COMBUSTION_AIR_TEMPERATURE | 3 | 19 | 🔴 |
| INDIRECT_COOLING_WATER_FLOW | 3 | 90 | 🔴 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 10 | 27 | 🔴 |

#### 주요 태그 차트

**FURNACE_PRESSURE** (Drift: 20, Shift: 114)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_combined.png)

**MAIN_GAS_PRESSURE** (Drift: 17, Shift: 94)

![MAIN_GAS_PRESSURE](04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_combined.png)

**MAIN_GAS_FLOW** (Drift: 16, Shift: 30)

![MAIN_GAS_FLOW](04_Furnace_Auxiliary/MAIN_GAS_FLOW_combined.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 드리프트 탐지: 16개
- 시프트 탐지: 16개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_TORQUE | 56 | 63 | 🔴 |
| STAND_2_ACTUAL_TORQUE | 79 | 62 | 🔴 |
| STAND_3_ACTUAL_TORQUE | 60 | 61 | 🔴 |
| STAND_4_ACTUAL_TORQUE | 46 | 58 | 🔴 |
| STAND_5_ACTUAL_TORQUE | 57 | 55 | 🔴 |
| STAND_6_ACTUAL_TORQUE | 44 | 58 | 🔴 |
| STAND_7_ACTUAL_TORQUE | 64 | 59 | 🔴 |
| STAND_8_ACTUAL_TORQUE | 54 | 61 | 🔴 |
| STAND_9_ACTUAL_TORQUE | 63 | 61 | 🔴 |
| STAND_10_ACTUAL_TORQUE | 53 | 62 | 🔴 |
| STAND_11_ACTUAL_TORQUE | 43 | 60 | 🔴 |
| STAND_12_ACTUAL_TORQUE | 52 | 57 | 🔴 |
| STAND_13_ACTUAL_TORQUE | 54 | 57 | 🔴 |
| STAND_14_ACTUAL_TORQUE | 39 | 55 | 🔴 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 40 | 54 | 🔴 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 40 | 54 | 🔴 |

#### 주요 태그 차트

**STAND_2_ACTUAL_TORQUE** (Drift: 79, Shift: 62)

![STAND_2_ACTUAL_TORQUE](05_Stand_Torque/STAND_2_ACTUAL_TORQUE_combined.png)

**STAND_7_ACTUAL_TORQUE** (Drift: 64, Shift: 59)

![STAND_7_ACTUAL_TORQUE](05_Stand_Torque/STAND_7_ACTUAL_TORQUE_combined.png)

**STAND_9_ACTUAL_TORQUE** (Drift: 63, Shift: 61)

![STAND_9_ACTUAL_TORQUE](05_Stand_Torque/STAND_9_ACTUAL_TORQUE_combined.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_SPEED | 18 | 23 | 🔴 |
| STAND_2_ACTUAL_SPEED | 18 | 23 | 🔴 |
| STAND_3_ACTUAL_SPEED | 18 | 23 | 🔴 |
| STAND_4_ACTUAL_SPEED | 16 | 24 | 🔴 |
| STAND_5_ACTUAL_SPEED | 17 | 24 | 🔴 |
| STAND_6_ACTUAL_SPEED | 17 | 24 | 🔴 |
| STAND_7_ACTUAL_SPEED | 18 | 23 | 🔴 |
| STAND_8_ACTUAL_SPEED | 18 | 23 | 🔴 |
| STAND_9_ACTUAL_SPEED | 19 | 22 | 🔴 |
| STAND_10_ACTUAL_SPEED | 19 | 22 | 🔴 |
| STAND_11_ACTUAL_SPEED | 19 | 23 | 🔴 |
| STAND_12_ACTUAL_SPEED | 19 | 22 | 🔴 |
| STAND_13_ACTUAL_SPEED | 19 | 22 | 🔴 |
| STAND_14_ACTUAL_SPEED | 19 | 23 | 🔴 |
| FINISHING_BLOCK_ACTUAL_SPEED | 16 | 25 | 🔴 |

#### 주요 태그 차트

**STAND_11_ACTUAL_SPEED** (Drift: 19, Shift: 23)

![STAND_11_ACTUAL_SPEED](06_Stand_Speed/STAND_11_ACTUAL_SPEED_combined.png)

**STAND_14_ACTUAL_SPEED** (Drift: 19, Shift: 23)

![STAND_14_ACTUAL_SPEED](06_Stand_Speed/STAND_14_ACTUAL_SPEED_combined.png)

**STAND_9_ACTUAL_SPEED** (Drift: 19, Shift: 22)

![STAND_9_ACTUAL_SPEED](06_Stand_Speed/STAND_9_ACTUAL_SPEED_combined.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_LOAD | 43 | 83 | 🔴 |
| STAND_2_LOAD | 42 | 82 | 🔴 |
| STAND_3_LOAD | 43 | 80 | 🔴 |
| STAND_4_LOAD | 43 | 82 | 🔴 |
| STAND_5_LOAD | 42 | 81 | 🔴 |
| STAND_6_LOAD | 43 | 81 | 🔴 |
| STAND_7_LOAD | 43 | 80 | 🔴 |
| STAND_8_LOAD | 42 | 81 | 🔴 |
| STAND_9_LOAD | 43 | 81 | 🔴 |
| STAND_10_LOAD | 43 | 82 | 🔴 |
| STAND_11_LOAD | 42 | 82 | 🔴 |
| STAND_12_LOAD | 42 | 82 | 🔴 |
| STAND_13_LOAD | 42 | 82 | 🔴 |
| STAND_14_LOAD | 41 | 82 | 🔴 |
| FINISHING_BLOCK_LOAD | 43 | 82 | 🔴 |

#### 주요 태그 차트

**STAND_1_LOAD** (Drift: 43, Shift: 83)

![STAND_1_LOAD](07_Stand_Load/STAND_1_LOAD_combined.png)

**STAND_4_LOAD** (Drift: 43, Shift: 82)

![STAND_4_LOAD](07_Stand_Load/STAND_4_LOAD_combined.png)

**STAND_10_LOAD** (Drift: 43, Shift: 82)

![STAND_10_LOAD](07_Stand_Load/STAND_10_LOAD_combined.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 57 | 51 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 61 | 70 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 68 | 70 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 45 | 60 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 46 | 59 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 47 | 59 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 5 | 5 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 56 | 73 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 56 | 73 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_4_ACTUAL_SPEED** (Drift: 68, Shift: 70)

![PINCHROLL_4_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_combined.png)

**PINCHROLL_3_ACTUAL_SPEED** (Drift: 61, Shift: 70)

![PINCHROLL_3_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_combined.png)

**PINCHROLL_2_ACTUAL_SPEED** (Drift: 57, Shift: 51)

![PINCHROLL_2_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_combined.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 드리프트 탐지: 6개
- 시프트 탐지: 2개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 18 | 55 | 🔴 |
| PR6L2_ACT_TORQUE | 40 | 58 | 🔴 |
| PR7L1_ACT_TORQUE | 18 | 0 | 🔴 |
| PR7L2_ACT_TORQUE | 19 | 0 | 🔴 |
| PR8L1_ACT_TORQUE | 9 | 0 | 🔴 |
| PR9L1_ACT_TORQUE | 28 | 0 | 🔴 |

#### 주요 태그 차트

**PR6L2_ACT_TORQUE** (Drift: 40, Shift: 58)

![PR6L2_ACT_TORQUE](09_PR_Detailed/PR6L2_ACT_TORQUE_combined.png)

**PR9L1_ACT_TORQUE** (Drift: 28, Shift: 0)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR7L2_ACT_TORQUE** (Drift: 19, Shift: 0)

![PR7L2_ACT_TORQUE](09_PR_Detailed/PR7L2_ACT_TORQUE_combined.png)



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
| 규격 | D13 |
| 생성일시 | 2026-02-09 14:59:22 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

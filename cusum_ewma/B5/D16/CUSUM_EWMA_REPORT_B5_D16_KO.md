# 강종 [B5] | 규격: D16 CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: B5
**규격**: D16
**생성일시**: 2026-02-09 14:58:02

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
| 1 | PR9L1_ACT_TORQUE | PR 상세 토크 | 281 | 109 | 🔴 |
| 2 | PR8L1_ACT_TORQUE | PR 상세 토크 | 266 | 182 | 🔴 |
| 3 | PR6L2_ACT_TORQUE | PR 상세 토크 | 183 | 181 | 🔴 |
| 4 | PR7L1_ACT_TORQUE | PR 상세 토크 | 182 | 181 | 🔴 |
| 5 | PR6L1_ACT_TORQUE | PR 상세 토크 | 181 | 180 | 🔴 |
| 6 | PR7L2_ACT_TORQUE | PR 상세 토크 | 178 | 176 | 🔴 |
| 7 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 106 | 89 | 🔴 |
| 8 | FINISHING_BLOCK_LOAD | 스탠드 부하 | 104 | 28 | 🔴 |
| 9 | MAIN_COMBUSTION_AIR_PRESSURE | 가열로 보조설비 | 103 | 171 | 🔴 |
| 10 | STAND_5_LOAD | 스탠드 부하 | 103 | 27 | 🔴 |
| 11 | STAND_2_LOAD | 스탠드 부하 | 101 | 28 | 🔴 |
| 12 | STAND_9_LOAD | 스탠드 부하 | 101 | 28 | 🔴 |
| 13 | STAND_6_LOAD | 스탠드 부하 | 100 | 28 | 🔴 |
| 14 | STAND_4_LOAD | 스탠드 부하 | 100 | 27 | 🔴 |
| 15 | STAND_7_LOAD | 스탠드 부하 | 98 | 28 | 🔴 |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 15 | 36 | 🔴 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 13 | 32 | 🔴 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 11 | 67 | 🔴 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 8 | 71 | 🔴 |

#### 주요 태그 차트

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 15, Shift: 36)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 13, Shift: 32)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)

**SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 11, Shift: 67)

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 4 | 13 | 🔴 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 3 | 25 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 1 | 39 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 1 | 28 | 🔴 |

#### 주요 태그 차트

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 4, Shift: 13)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 3, Shift: 25)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)

**SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 1, Shift: 39)

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 드리프트 탐지: 1개
- 시프트 탐지: 1개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 92 | 102 | 🔴 |

#### 주요 태그 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (Drift: 92, Shift: 102)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_combined.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_PRESSURE | 10 | 139 | 🔴 |
| FURNACE_O2_ANALYZER | 9 | 73 | 🔴 |
| MAIN_GAS_PRESSURE | 6 | 130 | 🔴 |
| MAIN_GAS_FLOW | 2 | 78 | 🔴 |
| MAIN_GAS_TEMPERATURE | 1 | 3 | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | 103 | 171 | 🔴 |
| COMBUSTION_AIR_TEMPERATURE | 1 | 10 | 🔴 |
| INDIRECT_COOLING_WATER_FLOW | 8 | 120 | 🔴 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 2 | 13 | 🔴 |

#### 주요 태그 차트

**MAIN_COMBUSTION_AIR_PRESSURE** (Drift: 103, Shift: 171)

![MAIN_COMBUSTION_AIR_PRESSURE](04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_combined.png)

**FURNACE_PRESSURE** (Drift: 10, Shift: 139)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_combined.png)

**FURNACE_O2_ANALYZER** (Drift: 9, Shift: 73)

![FURNACE_O2_ANALYZER](04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_combined.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 드리프트 탐지: 16개
- 시프트 탐지: 16개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_TORQUE | 30 | 24 | 🔴 |
| STAND_2_ACTUAL_TORQUE | 29 | 26 | 🔴 |
| STAND_3_ACTUAL_TORQUE | 30 | 26 | 🔴 |
| STAND_4_ACTUAL_TORQUE | 36 | 25 | 🔴 |
| STAND_5_ACTUAL_TORQUE | 33 | 24 | 🔴 |
| STAND_6_ACTUAL_TORQUE | 64 | 24 | 🔴 |
| STAND_7_ACTUAL_TORQUE | 32 | 25 | 🔴 |
| STAND_8_ACTUAL_TORQUE | 48 | 30 | 🔴 |
| STAND_9_ACTUAL_TORQUE | 41 | 25 | 🔴 |
| STAND_10_ACTUAL_TORQUE | 91 | 25 | 🔴 |
| STAND_11_ACTUAL_TORQUE | 82 | 25 | 🔴 |
| STAND_12_ACTUAL_TORQUE | 66 | 25 | 🔴 |
| STAND_13_ACTUAL_TORQUE | 50 | 25 | 🔴 |
| STAND_14_ACTUAL_TORQUE | 55 | 25 | 🔴 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 64 | 25 | 🔴 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 63 | 25 | 🔴 |

#### 주요 태그 차트

**STAND_10_ACTUAL_TORQUE** (Drift: 91, Shift: 25)

![STAND_10_ACTUAL_TORQUE](05_Stand_Torque/STAND_10_ACTUAL_TORQUE_combined.png)

**STAND_11_ACTUAL_TORQUE** (Drift: 82, Shift: 25)

![STAND_11_ACTUAL_TORQUE](05_Stand_Torque/STAND_11_ACTUAL_TORQUE_combined.png)

**STAND_12_ACTUAL_TORQUE** (Drift: 66, Shift: 25)

![STAND_12_ACTUAL_TORQUE](05_Stand_Torque/STAND_12_ACTUAL_TORQUE_combined.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_SPEED | 6 | 11 | 🔴 |
| STAND_2_ACTUAL_SPEED | 6 | 11 | 🔴 |
| STAND_3_ACTUAL_SPEED | 6 | 11 | 🔴 |
| STAND_4_ACTUAL_SPEED | 6 | 11 | 🔴 |
| STAND_5_ACTUAL_SPEED | 6 | 11 | 🔴 |
| STAND_6_ACTUAL_SPEED | 5 | 11 | 🔴 |
| STAND_7_ACTUAL_SPEED | 5 | 11 | 🔴 |
| STAND_8_ACTUAL_SPEED | 5 | 11 | 🔴 |
| STAND_9_ACTUAL_SPEED | 6 | 13 | 🔴 |
| STAND_10_ACTUAL_SPEED | 6 | 13 | 🔴 |
| STAND_11_ACTUAL_SPEED | 6 | 13 | 🔴 |
| STAND_12_ACTUAL_SPEED | 6 | 13 | 🔴 |
| STAND_13_ACTUAL_SPEED | 6 | 13 | 🔴 |
| STAND_14_ACTUAL_SPEED | 6 | 13 | 🔴 |
| FINISHING_BLOCK_ACTUAL_SPEED | 6 | 12 | 🔴 |

#### 주요 태그 차트

**STAND_9_ACTUAL_SPEED** (Drift: 6, Shift: 13)

![STAND_9_ACTUAL_SPEED](06_Stand_Speed/STAND_9_ACTUAL_SPEED_combined.png)

**STAND_10_ACTUAL_SPEED** (Drift: 6, Shift: 13)

![STAND_10_ACTUAL_SPEED](06_Stand_Speed/STAND_10_ACTUAL_SPEED_combined.png)

**STAND_11_ACTUAL_SPEED** (Drift: 6, Shift: 13)

![STAND_11_ACTUAL_SPEED](06_Stand_Speed/STAND_11_ACTUAL_SPEED_combined.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_LOAD | 97 | 27 | 🔴 |
| STAND_2_LOAD | 101 | 28 | 🔴 |
| STAND_3_LOAD | 98 | 27 | 🔴 |
| STAND_4_LOAD | 100 | 27 | 🔴 |
| STAND_5_LOAD | 103 | 27 | 🔴 |
| STAND_6_LOAD | 100 | 28 | 🔴 |
| STAND_7_LOAD | 98 | 28 | 🔴 |
| STAND_8_LOAD | 98 | 28 | 🔴 |
| STAND_9_LOAD | 101 | 28 | 🔴 |
| STAND_10_LOAD | 97 | 28 | 🔴 |
| STAND_11_LOAD | 96 | 28 | 🔴 |
| STAND_12_LOAD | 97 | 27 | 🔴 |
| STAND_13_LOAD | 97 | 27 | 🔴 |
| STAND_14_LOAD | 98 | 27 | 🔴 |
| FINISHING_BLOCK_LOAD | 104 | 28 | 🔴 |

#### 주요 태그 차트

**FINISHING_BLOCK_LOAD** (Drift: 104, Shift: 28)

![FINISHING_BLOCK_LOAD](07_Stand_Load/FINISHING_BLOCK_LOAD_combined.png)

**STAND_5_LOAD** (Drift: 103, Shift: 27)

![STAND_5_LOAD](07_Stand_Load/STAND_5_LOAD_combined.png)

**STAND_2_LOAD** (Drift: 101, Shift: 28)

![STAND_2_LOAD](07_Stand_Load/STAND_2_LOAD_combined.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 106 | 89 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 88 | 68 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 72 | 69 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 63 | 69 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 64 | 63 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 67 | 68 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 6 | 8 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 72 | 71 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 72 | 72 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_2_ACTUAL_SPEED** (Drift: 106, Shift: 89)

![PINCHROLL_2_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_combined.png)

**PINCHROLL_3_ACTUAL_SPEED** (Drift: 88, Shift: 68)

![PINCHROLL_3_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_combined.png)

**PINCHROLL_4_REFERENCE_TORQUE** (Drift: 72, Shift: 72)

![PINCHROLL_4_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_combined.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 드리프트 탐지: 6개
- 시프트 탐지: 6개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 181 | 180 | 🔴 |
| PR6L2_ACT_TORQUE | 183 | 181 | 🔴 |
| PR7L1_ACT_TORQUE | 182 | 181 | 🔴 |
| PR7L2_ACT_TORQUE | 178 | 176 | 🔴 |
| PR8L1_ACT_TORQUE | 266 | 182 | 🔴 |
| PR9L1_ACT_TORQUE | 281 | 109 | 🔴 |

#### 주요 태그 차트

**PR9L1_ACT_TORQUE** (Drift: 281, Shift: 109)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR8L1_ACT_TORQUE** (Drift: 266, Shift: 182)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_combined.png)

**PR6L2_ACT_TORQUE** (Drift: 183, Shift: 181)

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
| 강종 | B5 |
| 규격 | D16 |
| 생성일시 | 2026-02-09 14:58:02 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

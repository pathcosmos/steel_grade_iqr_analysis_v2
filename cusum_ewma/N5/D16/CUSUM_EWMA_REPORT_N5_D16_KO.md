# 강종 [N5] | 규격: D16 CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5
**규격**: D16
**생성일시**: 2026-02-09 14:47:29

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
| 1 | PR9L1_ACT_TORQUE | PR 상세 토크 | 921 | 474 | 🔴 |
| 2 | PR8L1_ACT_TORQUE | PR 상세 토크 | 841 | 508 | 🔴 |
| 3 | FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 가열로 추출 온도 | 498 | 497 | 🔴 |
| 4 | PR7L1_ACT_TORQUE | PR 상세 토크 | 450 | 512 | 🔴 |
| 5 | PR7L2_ACT_TORQUE | PR 상세 토크 | 370 | 405 | 🔴 |
| 6 | STAND_2_LOAD | 스탠드 부하 | 357 | 309 | 🔴 |
| 7 | STAND_12_LOAD | 스탠드 부하 | 356 | 302 | 🔴 |
| 8 | STAND_13_LOAD | 스탠드 부하 | 356 | 302 | 🔴 |
| 9 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 354 | 378 | 🔴 |
| 10 | STAND_3_LOAD | 스탠드 부하 | 354 | 312 | 🔴 |
| 11 | STAND_1_LOAD | 스탠드 부하 | 354 | 305 | 🔴 |
| 12 | FINISHING_BLOCK_LOAD | 스탠드 부하 | 353 | 304 | 🔴 |
| 13 | STAND_14_LOAD | 스탠드 부하 | 353 | 303 | 🔴 |
| 14 | STAND_11_LOAD | 스탠드 부하 | 352 | 305 | 🔴 |
| 15 | STAND_9_LOAD | 스탠드 부하 | 352 | 303 | 🔴 |

---

## 카테고리별 분석 결과

### 가열로 상부 온도 (01_Furnace_Top_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 21 | 86 | 🔴 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 20 | 79 | 🔴 |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 11 | 28 | 🔴 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 12 | 28 | 🔴 |

#### 주요 태그 차트

**HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF** (Drift: 21, Shift: 86)

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_combined.png)

**HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 20, Shift: 79)

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)

**SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF** (Drift: 12, Shift: 28)

![SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF](01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_combined.png)


### 가열로 하부 온도 (02_Furnace_Bottom_Temperature)

- 분석 태그: 4개
- 드리프트 탐지: 4개
- 시프트 탐지: 4개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 46 | 96 | 🔴 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 38 | 102 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 30 | 58 | 🔴 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 26 | 72 | 🔴 |

#### 주요 태그 차트

**HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 46, Shift: 96)

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)

**HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE** (Drift: 38, Shift: 102)

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE](02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_combined.png)

**SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE** (Drift: 30, Shift: 58)

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE](02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_combined.png)


### 가열로 추출 온도 (03_Furnace_Discharge_Temperature)

- 분석 태그: 1개
- 드리프트 탐지: 1개
- 시프트 탐지: 1개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 498 | 497 | 🔴 |

#### 주요 태그 차트

**FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE** (Drift: 498, Shift: 497)

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE](03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_combined.png)


### 가열로 보조설비 (04_Furnace_Auxiliary)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| FURNACE_PRESSURE | 30 | 276 | 🔴 |
| FURNACE_O2_ANALYZER | 88 | 160 | 🔴 |
| MAIN_GAS_PRESSURE | 35 | 233 | 🔴 |
| MAIN_GAS_FLOW | 27 | 165 | 🔴 |
| MAIN_GAS_TEMPERATURE | 3 | 14 | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | 23 | 35 | 🔴 |
| COMBUSTION_AIR_TEMPERATURE | 3 | 29 | 🔴 |
| INDIRECT_COOLING_WATER_FLOW | 3 | 182 | 🔴 |
| INDIRECT_WATER_MAIN_TEMPERATURE | 1 | 14 | 🔴 |

#### 주요 태그 차트

**FURNACE_O2_ANALYZER** (Drift: 88, Shift: 160)

![FURNACE_O2_ANALYZER](04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_combined.png)

**MAIN_GAS_PRESSURE** (Drift: 35, Shift: 233)

![MAIN_GAS_PRESSURE](04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_combined.png)

**FURNACE_PRESSURE** (Drift: 30, Shift: 276)

![FURNACE_PRESSURE](04_Furnace_Auxiliary/FURNACE_PRESSURE_combined.png)


### 스탠드 토크 (05_Stand_Torque)

- 분석 태그: 16개
- 드리프트 탐지: 16개
- 시프트 탐지: 16개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_TORQUE | 151 | 312 | 🔴 |
| STAND_2_ACTUAL_TORQUE | 245 | 303 | 🔴 |
| STAND_3_ACTUAL_TORQUE | 217 | 300 | 🔴 |
| STAND_4_ACTUAL_TORQUE | 211 | 258 | 🔴 |
| STAND_5_ACTUAL_TORQUE | 220 | 289 | 🔴 |
| STAND_6_ACTUAL_TORQUE | 169 | 259 | 🔴 |
| STAND_7_ACTUAL_TORQUE | 302 | 245 | 🔴 |
| STAND_8_ACTUAL_TORQUE | 150 | 304 | 🔴 |
| STAND_9_ACTUAL_TORQUE | 200 | 254 | 🔴 |
| STAND_10_ACTUAL_TORQUE | 238 | 239 | 🔴 |
| STAND_11_ACTUAL_TORQUE | 227 | 249 | 🔴 |
| STAND_12_ACTUAL_TORQUE | 191 | 251 | 🔴 |
| STAND_13_ACTUAL_TORQUE | 200 | 269 | 🔴 |
| STAND_14_ACTUAL_TORQUE | 294 | 229 | 🔴 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 197 | 217 | 🔴 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 196 | 217 | 🔴 |

#### 주요 태그 차트

**STAND_7_ACTUAL_TORQUE** (Drift: 302, Shift: 245)

![STAND_7_ACTUAL_TORQUE](05_Stand_Torque/STAND_7_ACTUAL_TORQUE_combined.png)

**STAND_14_ACTUAL_TORQUE** (Drift: 294, Shift: 229)

![STAND_14_ACTUAL_TORQUE](05_Stand_Torque/STAND_14_ACTUAL_TORQUE_combined.png)

**STAND_2_ACTUAL_TORQUE** (Drift: 245, Shift: 303)

![STAND_2_ACTUAL_TORQUE](05_Stand_Torque/STAND_2_ACTUAL_TORQUE_combined.png)


### 스탠드 속도 (06_Stand_Speed)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_ACTUAL_SPEED | 41 | 85 | 🔴 |
| STAND_2_ACTUAL_SPEED | 49 | 84 | 🔴 |
| STAND_3_ACTUAL_SPEED | 52 | 84 | 🔴 |
| STAND_4_ACTUAL_SPEED | 49 | 84 | 🔴 |
| STAND_5_ACTUAL_SPEED | 49 | 84 | 🔴 |
| STAND_6_ACTUAL_SPEED | 45 | 84 | 🔴 |
| STAND_7_ACTUAL_SPEED | 48 | 84 | 🔴 |
| STAND_8_ACTUAL_SPEED | 47 | 84 | 🔴 |
| STAND_9_ACTUAL_SPEED | 42 | 92 | 🔴 |
| STAND_10_ACTUAL_SPEED | 53 | 93 | 🔴 |
| STAND_11_ACTUAL_SPEED | 51 | 94 | 🔴 |
| STAND_12_ACTUAL_SPEED | 48 | 92 | 🔴 |
| STAND_13_ACTUAL_SPEED | 46 | 94 | 🔴 |
| STAND_14_ACTUAL_SPEED | 49 | 92 | 🔴 |
| FINISHING_BLOCK_ACTUAL_SPEED | 53 | 103 | 🔴 |

#### 주요 태그 차트

**FINISHING_BLOCK_ACTUAL_SPEED** (Drift: 53, Shift: 103)

![FINISHING_BLOCK_ACTUAL_SPEED](06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_combined.png)

**STAND_10_ACTUAL_SPEED** (Drift: 53, Shift: 93)

![STAND_10_ACTUAL_SPEED](06_Stand_Speed/STAND_10_ACTUAL_SPEED_combined.png)

**STAND_3_ACTUAL_SPEED** (Drift: 52, Shift: 84)

![STAND_3_ACTUAL_SPEED](06_Stand_Speed/STAND_3_ACTUAL_SPEED_combined.png)


### 스탠드 부하 (07_Stand_Load)

- 분석 태그: 15개
- 드리프트 탐지: 15개
- 시프트 탐지: 15개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| STAND_1_LOAD | 354 | 305 | 🔴 |
| STAND_2_LOAD | 357 | 309 | 🔴 |
| STAND_3_LOAD | 354 | 312 | 🔴 |
| STAND_4_LOAD | 351 | 314 | 🔴 |
| STAND_5_LOAD | 349 | 311 | 🔴 |
| STAND_6_LOAD | 347 | 310 | 🔴 |
| STAND_7_LOAD | 347 | 306 | 🔴 |
| STAND_8_LOAD | 348 | 307 | 🔴 |
| STAND_9_LOAD | 352 | 303 | 🔴 |
| STAND_10_LOAD | 350 | 305 | 🔴 |
| STAND_11_LOAD | 352 | 305 | 🔴 |
| STAND_12_LOAD | 356 | 302 | 🔴 |
| STAND_13_LOAD | 356 | 302 | 🔴 |
| STAND_14_LOAD | 353 | 303 | 🔴 |
| FINISHING_BLOCK_LOAD | 353 | 304 | 🔴 |

#### 주요 태그 차트

**STAND_2_LOAD** (Drift: 357, Shift: 309)

![STAND_2_LOAD](07_Stand_Load/STAND_2_LOAD_combined.png)

**STAND_12_LOAD** (Drift: 356, Shift: 302)

![STAND_12_LOAD](07_Stand_Load/STAND_12_LOAD_combined.png)

**STAND_13_LOAD** (Drift: 356, Shift: 302)

![STAND_13_LOAD](07_Stand_Load/STAND_13_LOAD_combined.png)


### 핀치롤 (08_Pinchroll)

- 분석 태그: 9개
- 드리프트 탐지: 9개
- 시프트 탐지: 9개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 213 | 206 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 4 | 4 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 3 | 3 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 354 | 378 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 138 | 268 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 185 | 283 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 15 | 16 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 328 | 340 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 340 | 374 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_2_ACTUAL_TORQUE** (Drift: 354, Shift: 378)

![PINCHROLL_2_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_combined.png)

**PINCHROLL_4_REFERENCE_TORQUE** (Drift: 340, Shift: 374)

![PINCHROLL_4_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_combined.png)

**PINCHROLL_3_REFERENCE_TORQUE** (Drift: 328, Shift: 340)

![PINCHROLL_3_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_combined.png)


### PR 상세 토크 (09_PR_Detailed)

- 분석 태그: 6개
- 드리프트 탐지: 6개
- 시프트 탐지: 6개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 1 | 90 | 🔴 |
| PR6L2_ACT_TORQUE | 3 | 81 | 🔴 |
| PR7L1_ACT_TORQUE | 450 | 512 | 🔴 |
| PR7L2_ACT_TORQUE | 370 | 405 | 🔴 |
| PR8L1_ACT_TORQUE | 841 | 508 | 🔴 |
| PR9L1_ACT_TORQUE | 921 | 474 | 🔴 |

#### 주요 태그 차트

**PR9L1_ACT_TORQUE** (Drift: 921, Shift: 474)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR8L1_ACT_TORQUE** (Drift: 841, Shift: 508)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_combined.png)

**PR7L1_ACT_TORQUE** (Drift: 450, Shift: 512)

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
| 규격 | D16 |
| 생성일시 | 2026-02-09 14:47:29 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

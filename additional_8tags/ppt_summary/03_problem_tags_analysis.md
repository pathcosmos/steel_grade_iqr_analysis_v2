# 문제 태그 집중 분석

---

## 1. 문제 태그 선별 기준

### 기법별 문제 판정 임계값

| 기법 | 문제 기준 | 근거 |
|------|----------|------|
| IQR | 이상치율 ≥ 10% | 통상 정상 분포에서 1.5×IQR 기준 이상치 5% 미만 |
| CUSUM-EWMA | Violation ratio ≥ 30% | 공정 관리 한계 초과 누적 30% 이상은 체계적 드리프트 |
| Rolling Z-Score | 이상치율 ≥ 3% | Z ≥ 3 기준 정상분포 이론치 0.27% 대비 10배 초과 |
| STL Residual | 잔차 이상치율 ≥ 10% | 추세·계절성 제거 후에도 10% 이상 비정상 잔차 |
| Mahalanobis | 이상치율 ≥ 5% | 다변량 Chi-square 기준 이론치 1% 대비 5배 초과 |

### 다기법 교차 확인 결과

- **3기법 이상 문제**: 47개 태그 (확실한 이상 신호)
- **4기법 문제**: 3개 태그 (최고 확신 수준)

> 차트 참조: `charts/overview/top10_problem_tags.png`

---

## 2. 카테고리별 문제 태그 상세

### 2.1 핀치롤 (08_Pinchroll) — 8개 태그, **최고 위험**

핀치롤은 분석 대상 중 가장 심각한 이상 집중 영역입니다. 속도·토크 모두에서 다기법 이상이 탐지됩니다.

#### 확정 문제 (4기법: IQR + CUSUM + Rolling-Z + STL)

| 태그 | IQR 이상치율 | CUSUM 위반율 | 비고 |
|------|-------------|-------------|------|
| **PINCHROLL_4_ACTUAL_SPEED** | B5/D16: 17.7%, N5/D12: 10.1% | 전 강종 99%+ | 4기법 전체 이상 |
| **PINCHROLL_3_ACTUAL_SPEED** | B5/D16: 17.4%, N5/D16: 22.6% | 전 강종 99%+ | 4기법 전체 이상 |

#### 높은 문제 (3기법: IQR + CUSUM + STL)

| 태그 | IQR 이상치율 (최고) | 해당 강종 |
|------|-------------------|----------|
| PINCHROLL_2_ACTUAL_SPEED | B5/D16: 18.0%, D5/D10: 15.7% | B5, D4, D5, N5 |
| PINCHROLL_3_REFERENCE_TORQUE | B5/D13: 21.2% | B5, D4, D5, N5 |
| PINCHROLL_4_REFERENCE_TORQUE | B5/D13: 21.1%, D5/D10: 19.0% | B5, D4, D5, N5 |
| PINCHROLL_4_ACTUAL_TORQUE | D5/D10: 22.7%, B5/D13: 20.9% | B5, D4, D5, N5 |
| PINCHROLL_3_ACTUAL_TORQUE | B5/D13: 21.3%, N5/D16: 19.3% | B5, D4, D5, N5 |
| PINCHROLL_2_ACTUAL_TORQUE | B5/D13: 19.7%, D5/D10: 19.7% | B5, D4, D5, N5 |

**소견**: 핀치롤 2~4번 전체(속도+토크)가 **전 강종에서** IQR 15~22%, CUSUM 65~100%의 이상치를 보입니다. 핀치롤 설비 자체의 정비 필요성을 시사합니다.

> 차트 참조: `charts/B5/IQR_PINCHROLL_4_ACTUAL_SPEED_D16_timeseries.png`, `charts/B5/CUSUM_PINCHROLL_4_ACTUAL_SPEED_combined.png`

---

### 2.2 PR 상세 토크 (09_PR_Detailed) — 6개 태그

핀치롤과 연관된 PR(Pinch Roll) 상세 토크 신호도 심각한 이상을 보입니다.

#### 확정 문제 (4기법)

| 태그 | IQR 이상치율 (최고) | CUSUM 위반율 | 비고 |
|------|-------------------|-------------|------|
| **PR6L2_ACT_TORQUE** | N5/D16: 32.3%(critical), D5/D10: 25.8%(critical) | 전 강종 99%+ | 가장 심각 |

#### 높은 문제 (3기법)

| 태그 | IQR 이상치율 (최고) | 비고 |
|------|-------------------|------|
| PR7L1_ACT_TORQUE | N5/D12: 19.2%, D5/D10: 18.5% | 전 강종 |
| PR6L1_ACT_TORQUE | D4/D13: 39.3%(critical!), D5/D10: 32.9%(critical) | **최대 IQR 이상치** |
| PR7L2_ACT_TORQUE | N5/D16: 25.1%(critical), N5/D20: 22.0% | N5에서 특히 심각 |
| PR8L1_ACT_TORQUE | N5/D10: 13.7% | D4, D5, N5 |
| PR9L1_ACT_TORQUE | - (CUSUM+Rolling-Z+STL만) | D4, D5, N5 |

**소견**: PR6~PR9 토크가 모두 문제. 특히 **PR6L1_ACT_TORQUE는 D4/D13에서 IQR 이상치율 39.3%**로 전체 태그 중 최고 수준. N5 강종에서 PR 토크 이상이 가장 심각합니다.

> 차트 참조: `charts/N5/IQR_PR6L2_ACT_TORQUE_D16_timeseries.png`

---

### 2.3 스탠드 속도 (06_Stand_Speed) — 15개 태그

전체 15개 스탠드 속도(STAND 1~14 + FINISHING BLOCK) 모두가 3기법(CUSUM + Rolling-Z + STL)에서 문제로 판정되었습니다.

| 태그 | CUSUM 위반율 | STL 잔차 이상치율 | Rolling-Z 이상치율 |
|------|-------------|-----------------|------------------|
| FINISHING_BLOCK_ACTUAL_SPEED | ~95.7% | ~42% | ~5.7% |
| STAND_12_ACTUAL_SPEED | ~95.5% | ~42% | ~5.5% |
| STAND_11_ACTUAL_SPEED | ~90.0% | ~41% | ~4.8% |
| STAND_14_ACTUAL_SPEED | ~88.4% | ~42% | ~5.1% |
| ... (STAND 1~10: 73~88%) | | | |

**소견**: 스탠드 속도 전체가 CUSUM·STL에서 높은 이상치율을 보이지만, **IQR에서는 대부분 정상 범위**입니다. 이는 스탠드 속도가 강종·사이즈에 따라 설정값이 달라지는 특성 때문일 수 있습니다. CUSUM이 공정 평균 변동에 과민하게 반응한 것으로 해석됩니다.

> 핵심: IQR에서 문제가 아닌 태그는 실제 이상보다는 **공정 조건 변경에 의한 정상 드리프트** 가능성이 높습니다.

---

### 2.4 스탠드 부하 (05_Stand_Torque) — 7개 태그

STAND 1~7 LOAD가 모두 3기법(CUSUM + Mahalanobis + STL)에서 문제입니다.

| 태그 | CUSUM 위반율 | Mahalanobis 이상치율 | STL 잔차 |
|------|-------------|-------------------|---------|
| STAND_4_LOAD | ~99.1% | ≥5% | ~40% |
| STAND_3_LOAD | ~99.0% | ≥5% | ~40% |
| STAND_5~7_LOAD | ~99.0% | ≥5% | ~40% |
| STAND_1~2_LOAD | ~99.0% | ≥5% | ~40% |

**소견**: Mahalanobis에서도 이상으로 나타나는 것은 스탠드 부하 간 **상관관계 구조가 비정상적**임을 의미합니다. 스탠드 간 부하 분배가 불균형할 가능성을 시사합니다.

---

### 2.5 가열로 보조설비 (03_Furnace_Discharge) — 5개 태그

| 태그 | 기법 | 최대 이상치율 | 비고 |
|------|------|-------------|------|
| MAIN_GAS_TEMPERATURE | CUSUM+Rolling-Z+STL | 100% | 가스 온도 불안정 |
| COMBUSTION_AIR_TEMPERATURE | CUSUM+Rolling-Z+STL | 100% | 연소 공기 온도 불안정 |
| MAIN_GAS_FLOW | CUSUM+Rolling-Z+STL | 97.8% | 가스 유량 변동 |
| FURNACE_O2_ANALYZER | CUSUM+Rolling-Z+STL | 96.6% | 산소 분석기 |
| MAIN_COMBUSTION_AIR_PRESSURE | CUSUM+Rolling-Z+STL | 45.0% | 연소 공기압 |

**소견**: 가열로 보조설비(가스, 연소공기, 산소) 관련 태그들이 높은 CUSUM 위반율을 보입니다. 이는 **가열로 연소 시스템의 제어 불안정**을 나타냅니다. 다만 IQR에서는 정상이므로 값 자체는 정상 범위 내에서의 미세 변동입니다.

---

### 2.6 가열로 상부 온도 (01_Furnace_Top_Temperature) — 4개 태그

| 태그 | 기법 | STL 잔차 이상치율 |
|------|------|-----------------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | CUSUM+Rolling-Z+STL | ~19% |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | CUSUM+Rolling-Z+STL | ~19% |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | CUSUM+Rolling-Z+STL | ~18% |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | CUSUM+Rolling-Z+STL | ~21% |

**소견**: 가열대·균열대 상부 온도 모두 STL 잔차에서 이상이 나타남. 가열로 온도 제어의 주기적 변동이 잔차로 반영됩니다.

---

## 3. 종합 비교

> 차트 참조: `charts/overview/category_outlier_boxplot.png`

### 카테고리별 위험도 순위

| 순위 | 카테고리 | 핵심 지표 | 조치 우선도 |
|------|---------|----------|-----------|
| 1 | **핀치롤 (08)** | IQR 15~23%, 4기법 교차 | 🔴 즉시 |
| 2 | **PR 토크 (09)** | IQR 최대 39.3%, 4기법 교차 | 🔴 즉시 |
| 3 | **스탠드 부하 (05)** | Mahalanobis + CUSUM 99% | 🟠 단기 |
| 4 | **가열로 보조설비 (03)** | CUSUM 100%, 연소계 불안정 | 🟠 단기 |
| 5 | **스탠드 속도 (06)** | CUSUM 높지만 IQR 정상 | 🟡 모니터링 |
| 6 | **가열로 온도 (01)** | STL 잔차 이상 | 🟡 모니터링 |

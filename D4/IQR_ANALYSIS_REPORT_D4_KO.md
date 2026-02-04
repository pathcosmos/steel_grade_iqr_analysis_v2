# 강종 [D4] IQR 상세 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D4
**생성일시**: 2026-02-02 21:20:35

---

## Executive Summary

### 분석 개요

| 구분 | 내용 |
|------|------|
| **분석 대상 강종** | D4 |
| **총 분석 태그 수** | 79개 |
| **PR_Detailed L1 태그** | 4개 |
| **PR_Detailed L2 태그** | 2개 |
| **양호 태그 (≤5%)** | 53개 |
| **주의 태그 (5~10%)** | 6개 |
| **경고 이상 태그 (≥10%)** | 20개 |

### 위험도 분포

| 등급 | 이상치율 | 태그 수 | 상태 |
|------|---------|--------|------|
| 🟢 양호 | 0~5% | 53개 | 정상 |
| 🟡 주의 | 5~10% | 6개 | 모니터링 |
| 🟠 경고 | 10~15% | 2개 | 원인 분석 |
| 🔴 위험 | 15~25% | 17개 | 점검 필요 |
| ⚫ 심각 | 25% 이상 | 1개 | 즉시 조치 |

### 상위 문제 태그 (이상치율 기준)

| 순위 | 라인 | 태그 | 이상치율 | 위험도 | 필터 제거율 |
|------|:----:|------|---------|--------|------------|
| 1 | - | FINISHING_BLOCK_ACTUAL_SPEED | 37.91% | ⚫ | 1.9% |
| 2 | - | FURNACE_O2_ANALYZER | 22.12% | 🔴 | 0.0% |
| 3 | - | PINCHROLL_2_ACTUAL_TORQUE | 16.90% | 🔴 | 18.9% |
| 4 | - | STAND_8_ACTUAL_SPEED | 16.00% | 🔴 | 1.9% |
| 5 | - | STAND_11_ACTUAL_SPEED | 15.89% | 🔴 | 1.9% |
| 6 | - | STAND_14_ACTUAL_SPEED | 15.81% | 🔴 | 1.9% |
| 7 | - | STAND_12_ACTUAL_SPEED | 15.79% | 🔴 | 1.9% |
| 8 | - | STAND_10_ACTUAL_SPEED | 15.73% | 🔴 | 1.9% |
| 9 | - | STAND_9_ACTUAL_SPEED | 15.62% | 🔴 | 1.9% |
| 10 | - | STAND_13_ACTUAL_SPEED | 15.58% | 🔴 | 1.9% |

---

## 필터 적용 범례

| 약어 | 필터명 | 설명 |
|:----:|--------|------|
| run | run_only | 가동 상태 데이터만 사용 |
| spc | special_ops | 특수 운전 제외 |
| roll | roll_change | 롤교환 구간 제외 |
| coil | coiling_transient | 권취 가감속 구간 제외 |

| 기호 | 의미 |
|:----:|------|
| ✓ | 해당 필터 적용됨 |
| ✗ | 해당 필터 미적용 |

---

## 라인별 카테고리 요약

### 01 Furnace Top Temperature

**설명**: 가열로 상부 온도

| 태그명 | L1/L2 | run | spc | roll | coil | 제거율 | 이상치 | 상태 |
|--------|:-----:|:---:|:---:|:----:|:----:|-------:|-------:|:----:|
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_R... | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 2.78% | 🟢 |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_R... | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 2.75% | 🟢 |
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_R... | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 2.04% | 🟢 |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_R... | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 1.89% | 🟢 |

**필터 적용 이유**:

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

### 02 Furnace Bottom Temperature

**설명**: 가열로 하부 온도

| 태그명 | L1/L2 | run | spc | roll | coil | 제거율 | 이상치 | 상태 |
|--------|:-----:|:---:|:---:|:----:|:----:|-------:|-------:|:----:|
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATUR... | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 2.80% | 🟢 |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATUR... | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 2.78% | 🟢 |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATUR... | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 0.66% | 🟢 |
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATUR... | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 0.61% | 🟢 |

**필터 적용 이유**:

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

### 03 Furnace Discharge Temperature

**설명**: 가열로 추출 온도

| 태그명 | L1/L2 | run | spc | roll | coil | 제거율 | 이상치 | 상태 |
|--------|:-----:|:---:|:---:|:----:|:----:|-------:|-------:|:----:|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPE... | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 8.34% | 🟡 |

**필터 적용 이유**:

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 압연 전 측정으로 롤교환 무관 |
| coiling_transient | ✗ | 권취 전 공정으로 무관 |

### 04 Furnace Auxiliary

**설명**: 가열로 보조설비

| 태그명 | L1/L2 | run | spc | roll | coil | 제거율 | 이상치 | 상태 |
|--------|:-----:|:---:|:---:|:----:|:----:|-------:|-------:|:----:|
| FURNACE_O2_ANALYZER | - | ✓ | ✓ | ✗ | ✗ | 0.0% | **22.12%** | 🔴 |
| MAIN_COMBUSTION_AIR_PRESSURE | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 8.95% | 🟡 |
| MAIN_GAS_PRESSURE | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 4.67% | 🟢 |
| FURNACE_PRESSURE | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 2.23% | 🟢 |
| COMBUSTION_AIR_TEMPERATURE | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 0.37% | 🟢 |
| MAIN_GAS_TEMPERATURE | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 0.00% | 🟢 |
| MAIN_GAS_FLOW | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 0.00% | 🟢 |
| INDIRECT_COOLING_WATER_FLOW | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 0.00% | 🟢 |
| INDIRECT_WATER_MAIN_TEMPERATURE | - | ✓ | ✓ | ✗ | ✗ | 0.0% | 0.00% | 🟢 |

**필터 적용 이유**:

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

### 05 Stand Torque

**설명**: 스탠드 토크

| 태그명 | L1/L2 | run | spc | roll | coil | 제거율 | 이상치 | 상태 |
|--------|:-----:|:---:|:---:|:----:|:----:|-------:|-------:|:----:|
| STAND_1_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_2_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_3_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_4_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_5_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_6_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_7_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_8_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_9_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_10_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_11_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_12_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_13_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_14_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQU... | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |

**필터 적용 이유**:

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

### 06 Stand Speed

**설명**: 스탠드 속도

| 태그명 | L1/L2 | run | spc | roll | coil | 제거율 | 이상치 | 상태 |
|--------|:-----:|:---:|:---:|:----:|:----:|-------:|-------:|:----:|
| FINISHING_BLOCK_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **37.91%** | ⚫ |
| STAND_8_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **16.00%** | 🔴 |
| STAND_11_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.89%** | 🔴 |
| STAND_14_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.81%** | 🔴 |
| STAND_12_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.79%** | 🔴 |
| STAND_10_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.73%** | 🔴 |
| STAND_9_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.62%** | 🔴 |
| STAND_13_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.58%** | 🔴 |
| STAND_2_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.48%** | 🔴 |
| STAND_6_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.44%** | 🔴 |
| STAND_4_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.43%** | 🔴 |
| STAND_5_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.37%** | 🔴 |
| STAND_7_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.36%** | 🔴 |
| STAND_1_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.35%** | 🔴 |
| STAND_3_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✗ | 1.9% | **15.34%** | 🔴 |

**필터 적용 이유**:

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

### 07 Stand Load

**설명**: 스탠드 부하

| 태그명 | L1/L2 | run | spc | roll | coil | 제거율 | 이상치 | 상태 |
|--------|:-----:|:---:|:---:|:----:|:----:|-------:|-------:|:----:|
| STAND_1_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_2_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_3_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_4_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_5_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_6_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_7_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_8_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_9_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_10_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_11_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_12_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_13_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| STAND_14_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |
| FINISHING_BLOCK_LOAD | - | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.00% | 🟢 |

**필터 적용 이유**:

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

### 08 Pinchroll

**설명**: 핀치롤

| 태그명 | L1/L2 | run | spc | roll | coil | 제거율 | 이상치 | 상태 |
|--------|:-----:|:---:|:---:|:----:|:----:|-------:|-------:|:----:|
| PINCHROLL_2_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✓ | 18.9% | **16.90%** | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✓ | 18.9% | **15.34%** | 🔴 |
| PINCHROLL_2_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✓ | 18.9% | **14.57%** | 🟠 |
| PINCHROLL_4_REFERENCE_TORQUE | - | ✓ | ✓ | ✓ | ✓ | 18.9% | **14.18%** | 🟠 |
| PINCHROLL_2_REFERENCE_TORQUE | - | ✓ | ✓ | ✓ | ✓ | 18.9% | 0.04% | 🟢 |
| PINCHROLL_3_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✓ | 18.9% | 0.02% | 🟢 |
| PINCHROLL_4_ACTUAL_SPEED | - | ✓ | ✓ | ✓ | ✓ | 18.9% | 0.01% | 🟢 |
| PINCHROLL_3_ACTUAL_TORQUE | - | ✓ | ✓ | ✓ | ✓ | 18.9% | 0.00% | 🟢 |
| PINCHROLL_3_REFERENCE_TORQUE | - | ✓ | ✓ | ✓ | ✓ | 18.9% | 0.00% | 🟢 |

**필터 적용 이유**:

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

### 09 PR Detailed

**설명**: PR 상세 토크

| 태그명 | L1/L2 | run | spc | roll | coil | 제거율 | 이상치 | 상태 |
|--------|:-----:|:---:|:---:|:----:|:----:|-------:|-------:|:----:|
| PR7L1_ACT_TORQUE | L1 | ✓ | ✓ | ✓ | ✗ | 1.9% | 6.32% | 🟡 |
| PR9L1_ACT_TORQUE | L1 | ✓ | ✓ | ✓ | ✗ | 1.9% | 6.28% | 🟡 |
| PR7L2_ACT_TORQUE | L2 | ✓ | ✓ | ✓ | ✗ | 1.9% | 5.58% | 🟡 |
| PR6L1_ACT_TORQUE | L1 | ✓ | ✓ | ✓ | ✗ | 1.9% | 5.27% | 🟡 |
| PR8L1_ACT_TORQUE | L1 | ✓ | ✓ | ✓ | ✗ | 1.9% | 4.77% | 🟢 |
| PR6L2_ACT_TORQUE | L2 | ✓ | ✓ | ✓ | ✗ | 1.9% | 0.49% | 🟢 |

**필터 적용 이유**:

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

---

## 태그별 상세 분석 (위험도 순)

> **정렬 기준**: 이상치율 높은 순 (⚫ 심각 → 🔴 위험 → 🟠 경고 → 🟡 주의 → 🟢 양호)

### ⚫ 심각 (25% 이상) - 1개 태그

#### FINISHING_BLOCK_ACTUAL_SPEED ⚫

**위험도**: [CRITICAL] | **이상치율**: 37.91% | **이상치 방향**: 양방향

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 795.0645 |
| 표준편차 | 334.2869 |
| Q1 (25%) | 923.4759 |
| 중앙값 | 923.7942 |
| Q3 (75%) | 935.4121 |
| IQR | 11.9362 |
| 하한 경계 | 905.5716 |
| 상한 경계 | 953.3164 |
| 이상치 수 | 7,492 (37.91%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 832.17 | 51.43% |
| 2025-06 | 5,678 | 828.32 | 39.08% |
| 2025-07 | 2,773 | 697.33 | 28.02% |
| 2025-08 | 4,201 | 751.82 | 19.97% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-18 | 3,158 |
| 2 | 2025-06-06 | 1,785 |
| 3 | 2025-08-08 | 525 |
| 4 | 2025-05-17 | 499 |
| 5 | 2025-06-12 | 434 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 3,158건 (2025-05-18)
- 평균 일별 이상치: 936.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/FINISHING_BLOCK_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 832.1720 |
| 중앙값 | 923.8123 |
| IQR | 41.8947 |
| 이상치 수 | 875 |
| 이상치율 | 12.30% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 499건
- 2. 2025-05-18: 376건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 828.3170 |
| 중앙값 | 923.5914 |
| IQR | 42.3976 |
| 이상치 수 | 693 |
| 이상치율 | 12.21% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 430건
- 2. 2025-06-06: 263건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 697.3303 |
| 중앙값 | 923.1473 |
| IQR | 94.1436 |
| 이상치 수 | 689 |
| 이상치율 | 24.85% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 392건
- 2. 2025-07-05: 297건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 751.8221 |
| 중앙값 | 932.0640 |
| IQR | 2.2436 |
| 이상치 수 | 1,341 |
| 이상치율 | 31.92% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 707건
- 2. 2025-08-11: 634건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/FINISHING_BLOCK_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/FINISHING_BLOCK_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/FINISHING_BLOCK_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/FINISHING_BLOCK_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/FINISHING_BLOCK_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/FINISHING_BLOCK_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/FINISHING_BLOCK_ACTUAL_SPEED_00_summary.png)

---

### 🔴 위험 (15~25%) - 17개 태그

#### FURNACE_O2_ANALYZER 🔴

**위험도**: [DANGER] | **이상치율**: 22.12% | **이상치 방향**: 하한 미달

**카테고리**: 04 Furnace Auxiliary

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 7.8815 |
| 표준편차 | 3.4013 |
| Q1 (25%) | 9.5277 |
| 중앙값 | 9.5344 |
| Q3 (75%) | 9.5394 |
| IQR | 0.0117 |
| 하한 경계 | 9.5103 |
| 상한 경계 | 9.5569 |
| 이상치 수 | 4,456 (22.12%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 9.45 | 2.67% |
| 2025-06 | 5,758 | 9.26 | 7.02% |
| 2025-07 | 2,880 | 8.48 | 22.57% |
| 2025-08 | 4,316 | 3.02 | 74.37% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-11 | 2,314 |
| 2 | 2025-08-08 | 896 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-06 | 358 |
| 5 | 2025-07-05 | 235 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 2,314건 (2025-08-11)
- 평균 일별 이상치: 557.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_07_daily_outlier_count.png)

**종합 분석 차트**

![FURNACE_O2_ANALYZER 종합 분석 차트](./04_Furnace_Auxiliary/FURNACE_O2_ANALYZER_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 9.4538 |
| 중앙값 | 9.5405 |
| IQR | 0.0041 |
| 이상치 수 | 194 |
| 이상치율 | 2.70% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 146건
- 2. 2025-05-18: 48건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_O2_ANALYZER_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 9.2626 |
| 중앙값 | 9.5331 |
| IQR | 0.0057 |
| 이상치 수 | 410 |
| 이상치율 | 7.12% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 360건
- 2. 2025-06-12: 50건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_O2_ANALYZER_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 8.4764 |
| 중앙값 | 9.5296 |
| IQR | 0.0077 |
| 이상치 수 | 651 |
| 이상치율 | 22.60% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 415건
- 2. 2025-07-05: 236건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_O2_ANALYZER_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 3.0227 |
| 중앙값 | 0.4678 |
| IQR | 9.2180 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_O2_ANALYZER_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_O2_ANALYZER_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_O2_ANALYZER_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_O2_ANALYZER_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_O2_ANALYZER_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_O2_ANALYZER_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_O2_ANALYZER_00_summary.png)

---

#### PINCHROLL_2_ACTUAL_TORQUE 🔴

**위험도**: [DANGER] | **이상치율**: 16.90% | **이상치 방향**: 하한 미달

**카테고리**: 08 Pinchroll

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 16.4559 |
| 표준편차 | 6.2207 |
| Q1 (25%) | 16.3637 |
| 중앙값 | 19.9946 |
| Q3 (75%) | 19.9950 |
| IQR | 3.6313 |
| 하한 경계 | 10.9168 |
| 상한 경계 | 25.4419 |
| 이상치 수 | 2,761 (16.90%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 6,158 | 16.86 | 13.38% |
| 2025-06 | 4,896 | 16.11 | 19.04% |
| 2025-07 | 2,011 | 15.76 | 23.22% |
| 2025-08 | 3,273 | 16.64 | 16.44% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 500 |
| 2 | 2025-06-06 | 432 |
| 3 | 2025-05-17 | 416 |
| 4 | 2025-05-18 | 408 |
| 5 | 2025-08-11 | 353 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 500건 (2025-06-12)
- 평균 일별 이상치: 345.1건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_2_ACTUAL_TORQUE 종합 분석 차트](./08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,158 |
| 평균 | 16.8559 |
| 중앙값 | 19.9945 |
| IQR | 3.5308 |
| 이상치 수 | 826 |
| 이상치율 | 13.41% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 418건
- 2. 2025-05-18: 408건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 16.1126 |
| 중앙값 | 19.9946 |
| IQR | 3.7551 |
| 이상치 수 | 920 |
| 이상치율 | 18.79% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 500건
- 2. 2025-06-06: 420건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 15.7611 |
| 중앙값 | 19.9947 |
| IQR | 5.7822 |
| 이상치 수 | 424 |
| 이상치율 | 21.08% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 223건
- 2. 2025-07-04: 201건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 16.6440 |
| 중앙값 | 19.9947 |
| IQR | 3.7272 |
| 이상치 수 | 538 |
| 이상치율 | 16.44% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 353건
- 2. 2025-08-08: 185건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_8_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 16.00% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 869.5171 |
| 표준편차 | 370.9368 |
| Q1 (25%) | 955.0535 |
| 중앙값 | 1020.3980 |
| Q3 (75%) | 1057.0810 |
| IQR | 102.0275 |
| 하한 경계 | 802.0123 |
| 상한 경계 | 1210.1222 |
| 이상치 수 | 3,163 (16.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 891.23 | 12.01% |
| 2025-06 | 5,678 | 893.03 | 11.22% |
| 2025-07 | 2,773 | 744.35 | 26.25% |
| 2025-08 | 4,201 | 883.60 | 22.47% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 641 |
| 2 | 2025-05-17 | 489 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 398 |
| 5 | 2025-05-18 | 365 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 641건 (2025-08-08)
- 평균 일별 이상치: 395.4건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_8_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_8_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_8_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_8_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_8_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 891.2300 |
| 중앙값 | 979.8107 |
| IQR | 95.5498 |
| 이상치 수 | 854 |
| 이상치율 | 12.01% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 489건
- 2. 2025-05-18: 365건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_8_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 893.0310 |
| 중앙값 | 968.5727 |
| IQR | 95.6577 |
| 이상치 수 | 637 |
| 이상치율 | 11.22% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 398건
- 2. 2025-06-06: 239건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_8_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 744.3504 |
| 중앙값 | 972.7760 |
| IQR | 1034.9990 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_8_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 883.6030 |
| 중앙값 | 1073.6390 |
| IQR | 68.9430 |
| 이상치 수 | 1,066 |
| 이상치율 | 25.37% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 759건
- 2. 2025-08-11: 307건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_8_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_8_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_8_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_8_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_8_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_8_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_8_ACTUAL_SPEED_00_summary.png)

---

#### STAND_11_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.89% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 879.7708 |
| 표준편차 | 377.3638 |
| Q1 (25%) | 1013.5660 |
| 중앙값 | 1033.7110 |
| Q3 (75%) | 1050.7900 |
| IQR | 37.2240 |
| 하한 경계 | 957.7300 |
| 상한 경계 | 1106.6260 |
| 이상치 수 | 3,141 (15.89%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 902.82 | 12.50% |
| 2025-06 | 5,678 | 948.19 | 11.64% |
| 2025-07 | 2,773 | 762.79 | 27.19% |
| 2025-08 | 4,201 | 825.49 | 19.92% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 527 |
| 2 | 2025-05-17 | 499 |
| 3 | 2025-07-04 | 436 |
| 4 | 2025-06-12 | 397 |
| 5 | 2025-05-18 | 390 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 527건 (2025-08-08)
- 평균 일별 이상치: 392.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_11_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_11_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_11_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_11_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_11_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 902.8202 |
| 중앙값 | 1022.7810 |
| IQR | 25.7550 |
| 이상치 수 | 889 |
| 이상치율 | 12.50% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 499건
- 2. 2025-05-18: 390건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_11_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 948.1922 |
| 중앙값 | 1064.3315 |
| IQR | 41.6923 |
| 이상치 수 | 661 |
| 이상치율 | 11.64% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 397건
- 2. 2025-06-06: 264건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_11_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 762.7905 |
| 중앙값 | 1037.4270 |
| IQR | 1042.9890 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_11_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 825.4947 |
| 중앙값 | 1023.6830 |
| IQR | 40.2138 |
| 이상치 수 | 837 |
| 이상치율 | 19.92% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 310건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_11_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_11_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_11_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_11_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_11_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_11_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_11_ACTUAL_SPEED_00_summary.png)

---

#### STAND_14_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.81% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 958.9394 |
| 표준편차 | 411.7120 |
| Q1 (25%) | 1109.9320 |
| 중앙값 | 1130.2340 |
| Q3 (75%) | 1147.5925 |
| IQR | 37.6605 |
| 하한 경계 | 1053.4413 |
| 상한 경계 | 1204.0832 |
| 이상치 수 | 3,125 (15.81%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 1001.29 | 12.50% |
| 2025-06 | 5,678 | 1018.59 | 11.62% |
| 2025-07 | 2,773 | 819.06 | 26.54% |
| 2025-08 | 4,201 | 898.97 | 20.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 527 |
| 2 | 2025-05-17 | 497 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 398 |
| 5 | 2025-05-18 | 392 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 527건 (2025-08-08)
- 평균 일별 이상치: 390.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_14_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_14_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_14_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_14_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_14_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 1001.2864 |
| 중앙값 | 1134.7450 |
| IQR | 17.4830 |
| 이상치 수 | 890 |
| 이상치율 | 12.52% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 498건
- 2. 2025-05-18: 392건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_14_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 1018.5901 |
| 중앙값 | 1152.7335 |
| IQR | 44.5452 |
| 이상치 수 | 660 |
| 이상치율 | 11.62% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 398건
- 2. 2025-06-06: 262건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_14_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 819.0585 |
| 중앙값 | 1109.0380 |
| IQR | 1135.5060 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_14_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 898.9688 |
| 중앙값 | 1112.1530 |
| IQR | 36.3320 |
| 이상치 수 | 839 |
| 이상치율 | 19.97% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 312건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_14_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_14_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_14_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_14_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_14_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_14_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_14_ACTUAL_SPEED_00_summary.png)

---

#### STAND_12_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.79% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 892.6333 |
| 표준편차 | 383.9130 |
| Q1 (25%) | 1032.1660 |
| 중앙값 | 1052.1540 |
| Q3 (75%) | 1069.4850 |
| IQR | 37.3190 |
| 하한 경계 | 976.1875 |
| 상한 경계 | 1125.4635 |
| 이상치 수 | 3,120 (15.79%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 930.93 | 12.45% |
| 2025-06 | 5,678 | 942.42 | 11.66% |
| 2025-07 | 2,773 | 756.54 | 26.54% |
| 2025-08 | 4,201 | 850.35 | 19.92% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 527 |
| 2 | 2025-05-17 | 497 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 398 |
| 5 | 2025-05-18 | 388 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 527건 (2025-08-08)
- 평균 일별 이상치: 390.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_12_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_12_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_12_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_12_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_12_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 930.9269 |
| 중앙값 | 1056.5960 |
| IQR | 34.6300 |
| 이상치 수 | 887 |
| 이상치율 | 12.47% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 497건
- 2. 2025-05-18: 390건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_12_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 942.4231 |
| 중앙값 | 1061.4690 |
| IQR | 35.4980 |
| 이상치 수 | 662 |
| 이상치율 | 11.66% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 398건
- 2. 2025-06-06: 264건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_12_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 756.5428 |
| 중앙값 | 1014.3610 |
| IQR | 1053.0490 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_12_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 850.3496 |
| 중앙값 | 1048.1750 |
| IQR | 41.5860 |
| 이상치 수 | 837 |
| 이상치율 | 19.92% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 310건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_12_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_12_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_12_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_12_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_12_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_12_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_12_ACTUAL_SPEED_00_summary.png)

---

#### STAND_10_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.73% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 824.0268 |
| 표준편차 | 353.2441 |
| Q1 (25%) | 936.3838 |
| 중앙값 | 951.4421 |
| Q3 (75%) | 1009.4230 |
| IQR | 73.0392 |
| 하한 경계 | 826.8251 |
| 상한 경계 | 1118.9817 |
| 이상치 수 | 3,108 (15.73%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 856.81 | 12.40% |
| 2025-06 | 5,678 | 871.90 | 11.52% |
| 2025-07 | 2,773 | 716.53 | 26.54% |
| 2025-08 | 4,201 | 774.78 | 19.90% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 527 |
| 2 | 2025-05-17 | 495 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 396 |
| 5 | 2025-05-18 | 387 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 527건 (2025-08-08)
- 평균 일별 이상치: 388.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_10_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_10_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_10_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_10_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_10_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 856.8113 |
| 중앙값 | 948.4268 |
| IQR | 70.7253 |
| 이상치 수 | 882 |
| 이상치율 | 12.40% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 495건
- 2. 2025-05-18: 387건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_10_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 871.9024 |
| 중앙값 | 964.1385 |
| IQR | 74.0708 |
| 이상치 수 | 654 |
| 이상치율 | 11.52% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 396건
- 2. 2025-06-06: 258건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_10_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 716.5279 |
| 중앙값 | 949.6066 |
| IQR | 994.6941 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_10_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 774.7828 |
| 중앙값 | 949.1406 |
| IQR | 64.4250 |
| 이상치 수 | 836 |
| 이상치율 | 19.90% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 309건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_10_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_10_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_10_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_10_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_10_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_10_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_10_ACTUAL_SPEED_00_summary.png)

---

#### STAND_9_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.62% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 824.8073 |
| 표준편차 | 355.3895 |
| Q1 (25%) | 889.4680 |
| 중앙값 | 954.7070 |
| Q3 (75%) | 1016.5700 |
| IQR | 127.1020 |
| 하한 경계 | 698.8151 |
| 상한 경계 | 1207.2229 |
| 이상치 수 | 3,087 (15.62%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 865.77 | 12.30% |
| 2025-06 | 5,678 | 844.61 | 11.39% |
| 2025-07 | 2,773 | 684.61 | 26.54% |
| 2025-08 | 4,201 | 821.24 | 19.73% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 523 |
| 2 | 2025-05-17 | 495 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 392 |
| 5 | 2025-05-18 | 380 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 523건 (2025-08-08)
- 평균 일별 이상치: 385.9건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_9_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_9_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_9_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_9_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_9_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 865.7746 |
| 중앙값 | 954.0474 |
| IQR | 95.3957 |
| 이상치 수 | 879 |
| 이상치율 | 12.36% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 495건
- 2. 2025-05-18: 384건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_9_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 844.6066 |
| 중앙값 | 899.6547 |
| IQR | 129.8719 |
| 이상치 수 | 647 |
| 이상치율 | 11.39% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 392건
- 2. 2025-06-06: 255건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_9_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 684.6129 |
| 중앙값 | 902.6964 |
| IQR | 951.6205 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_9_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 821.2414 |
| 중앙값 | 1003.5090 |
| IQR | 65.8762 |
| 이상치 수 | 853 |
| 이상치율 | 20.30% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 544건
- 2. 2025-08-11: 309건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_9_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_9_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_9_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_9_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_9_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_9_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_9_ACTUAL_SPEED_00_summary.png)

---

#### STAND_13_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.58% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 869.2221 |
| 표준편차 | 374.3231 |
| Q1 (25%) | 933.7460 |
| 중앙값 | 1045.4200 |
| Q3 (75%) | 1073.9840 |
| IQR | 140.2380 |
| 하한 경계 | 723.3890 |
| 상한 경계 | 1284.3410 |
| 이상치 수 | 3,080 (15.58%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 936.16 | 12.19% |
| 2025-06 | 5,678 | 952.32 | 11.36% |
| 2025-07 | 2,773 | 688.84 | 26.54% |
| 2025-08 | 4,201 | 762.68 | 19.80% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 525 |
| 2 | 2025-05-17 | 492 |
| 3 | 2025-07-04 | 418 |
| 4 | 2025-06-12 | 389 |
| 5 | 2025-05-18 | 375 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 525건 (2025-08-08)
- 평균 일별 이상치: 385.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_13_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_13_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_13_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_13_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_13_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 936.1558 |
| 중앙값 | 1063.9050 |
| IQR | 29.1360 |
| 이상치 수 | 887 |
| 이상치율 | 12.47% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 497건
- 2. 2025-05-18: 390건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_13_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 952.3218 |
| 중앙값 | 1072.6225 |
| IQR | 44.2022 |
| 이상치 수 | 658 |
| 이상치율 | 11.59% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 396건
- 2. 2025-06-06: 262건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_13_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 688.8379 |
| 중앙값 | 923.3658 |
| IQR | 949.5346 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_13_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 762.6759 |
| 중앙값 | 936.8420 |
| IQR | 30.7067 |
| 이상치 수 | 838 |
| 이상치율 | 19.95% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 311건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_13_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_13_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_13_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_13_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_13_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_13_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_13_ACTUAL_SPEED_00_summary.png)

---

#### STAND_2_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.48% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 498.6576 |
| 표준편차 | 213.6638 |
| Q1 (25%) | 536.9730 |
| 중앙값 | 565.8745 |
| Q3 (75%) | 608.8832 |
| IQR | 71.9102 |
| 하한 경계 | 429.1077 |
| 상한 경계 | 716.7485 |
| 이상치 수 | 3,060 (15.48%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 516.66 | 11.94% |
| 2025-06 | 5,678 | 523.09 | 11.17% |
| 2025-07 | 2,773 | 490.38 | 27.01% |
| 2025-08 | 4,201 | 440.64 | 19.71% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 526 |
| 2 | 2025-05-17 | 487 |
| 3 | 2025-07-04 | 436 |
| 4 | 2025-06-12 | 395 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 526건 (2025-08-08)
- 평균 일별 이상치: 382.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_2_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_2_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_2_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_2_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_2_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 516.6556 |
| 중앙값 | 567.3234 |
| IQR | 45.7571 |
| 이상치 수 | 855 |
| 이상치율 | 12.02% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 490건
- 2. 2025-05-18: 365건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_2_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 523.0868 |
| 중앙값 | 573.1510 |
| IQR | 47.2315 |
| 이상치 수 | 641 |
| 이상치율 | 11.29% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 400건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_2_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 490.3817 |
| 중앙값 | 635.5304 |
| IQR | 682.6834 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_2_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 440.6372 |
| 중앙값 | 534.7484 |
| IQR | 35.5353 |
| 이상치 수 | 1,045 |
| 이상치율 | 24.88% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 738건
- 2. 2025-08-11: 307건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_2_ACTUAL_SPEED_00_summary.png)

---

#### STAND_6_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.44% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 949.0193 |
| 표준편차 | 403.1088 |
| Q1 (25%) | 1061.3535 |
| 중앙값 | 1091.1030 |
| Q3 (75%) | 1169.8120 |
| IQR | 108.4585 |
| 하한 경계 | 898.6658 |
| 상한 경계 | 1332.4997 |
| 이상치 수 | 3,051 (15.44%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 986.77 | 12.01% |
| 2025-06 | 5,678 | 1015.88 | 11.18% |
| 2025-07 | 2,773 | 841.15 | 26.25% |
| 2025-08 | 4,201 | 865.97 | 19.85% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 527 |
| 2 | 2025-05-17 | 489 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 396 |
| 5 | 2025-05-18 | 365 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 527건 (2025-08-08)
- 평균 일별 이상치: 381.4건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_6_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_6_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_6_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_6_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_6_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 986.7654 |
| 중앙값 | 1081.8130 |
| IQR | 102.1135 |
| 이상치 수 | 854 |
| 이상치율 | 12.01% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 489건
- 2. 2025-05-18: 365건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_6_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 1015.8765 |
| 중앙값 | 1110.2590 |
| IQR | 87.2818 |
| 이상치 수 | 642 |
| 이상치율 | 11.31% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 401건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_6_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 841.1498 |
| 중앙값 | 1091.6000 |
| IQR | 1170.2710 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_6_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 865.9663 |
| 중앙값 | 1053.7160 |
| IQR | 62.1430 |
| 이상치 수 | 929 |
| 이상치율 | 22.11% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 622건
- 2. 2025-08-11: 307건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_6_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_6_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_6_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_6_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_6_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_6_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_6_ACTUAL_SPEED_00_summary.png)

---

#### STAND_4_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.43% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 664.1643 |
| 표준편차 | 282.2945 |
| Q1 (25%) | 736.3986 |
| 중앙값 | 765.0871 |
| Q3 (75%) | 819.5286 |
| IQR | 83.1300 |
| 하한 경계 | 611.7035 |
| 상한 경계 | 944.2237 |
| 이상치 수 | 3,050 (15.43%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 702.00 | 12.00% |
| 2025-06 | 5,678 | 695.77 | 11.29% |
| 2025-07 | 2,773 | 579.80 | 26.25% |
| 2025-08 | 4,201 | 613.10 | 19.71% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 526 |
| 2 | 2025-05-17 | 488 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 400 |
| 5 | 2025-05-18 | 365 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 526건 (2025-08-08)
- 평균 일별 이상치: 381.2건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_4_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_4_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_4_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_4_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_4_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 701.9960 |
| 중앙값 | 771.5384 |
| IQR | 64.3312 |
| 이상치 수 | 856 |
| 이상치율 | 12.04% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 491건
- 2. 2025-05-18: 365건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_4_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 695.7699 |
| 중앙값 | 750.0693 |
| IQR | 84.1129 |
| 이상치 수 | 641 |
| 이상치율 | 11.29% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 400건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_4_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 579.7980 |
| 중앙값 | 750.5014 |
| IQR | 807.5416 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_4_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 613.0981 |
| 중앙값 | 746.2508 |
| IQR | 49.7644 |
| 이상치 수 | 845 |
| 이상치율 | 20.11% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 538건
- 2. 2025-08-11: 307건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_4_ACTUAL_SPEED_00_summary.png)

---

#### STAND_5_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.37% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 980.2517 |
| 표준편차 | 417.3341 |
| Q1 (25%) | 1068.6880 |
| 중앙값 | 1131.6620 |
| Q3 (75%) | 1212.4440 |
| IQR | 143.7560 |
| 하한 경계 | 853.0540 |
| 상한 경계 | 1428.0780 |
| 이상치 수 | 3,037 (15.37%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 1038.91 | 11.95% |
| 2025-06 | 5,678 | 1038.42 | 11.11% |
| 2025-07 | 2,773 | 882.25 | 26.25% |
| 2025-08 | 4,201 | 867.03 | 19.71% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 525 |
| 2 | 2025-05-17 | 488 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 392 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 525건 (2025-08-08)
- 평균 일별 이상치: 379.6건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_5_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_5_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_5_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_5_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_5_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 1038.9128 |
| 중앙값 | 1141.1580 |
| IQR | 100.9145 |
| 이상치 수 | 854 |
| 이상치율 | 12.01% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 489건
- 2. 2025-05-18: 365건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_5_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 1038.4182 |
| 중앙값 | 1131.6770 |
| IQR | 92.0940 |
| 이상치 수 | 642 |
| 이상치율 | 11.31% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 401건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_5_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 882.2458 |
| 중앙값 | 1141.9140 |
| IQR | 1227.5910 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_5_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 867.0317 |
| 중앙값 | 1057.1540 |
| IQR | 65.5220 |
| 이상치 수 | 843 |
| 이상치율 | 20.07% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 536건
- 2. 2025-08-11: 307건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_5_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_5_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_5_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_5_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_5_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_5_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_5_ACTUAL_SPEED_00_summary.png)

---

#### STAND_7_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.36% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 1020.8515 |
| 표준편차 | 435.8140 |
| Q1 (25%) | 1110.3990 |
| 중앙값 | 1177.6640 |
| Q3 (75%) | 1278.2200 |
| IQR | 167.8210 |
| 하한 경계 | 858.6675 |
| 상한 경계 | 1529.9515 |
| 이상치 수 | 3,035 (15.36%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 1091.92 | 11.95% |
| 2025-06 | 5,678 | 1082.43 | 11.11% |
| 2025-07 | 2,773 | 888.97 | 26.25% |
| 2025-08 | 4,201 | 904.39 | 19.66% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 523 |
| 2 | 2025-05-17 | 488 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 392 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 523건 (2025-08-08)
- 평균 일별 이상치: 379.4건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_7_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_7_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_7_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_7_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_7_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 1091.9194 |
| 중앙값 | 1198.0400 |
| IQR | 124.4000 |
| 이상치 수 | 854 |
| 이상치율 | 12.01% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 489건
- 2. 2025-05-18: 365건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_7_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 1082.4253 |
| 중앙값 | 1153.2355 |
| IQR | 150.3560 |
| 이상치 수 | 635 |
| 이상치율 | 11.18% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 396건
- 2. 2025-06-06: 239건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_7_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 888.9665 |
| 중앙값 | 1159.3990 |
| IQR | 1233.3430 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_7_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 904.3880 |
| 중앙값 | 1103.2800 |
| IQR | 71.3620 |
| 이상치 수 | 859 |
| 이상치율 | 20.45% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 552건
- 2. 2025-08-11: 307건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_7_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_7_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_7_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_7_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_7_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_7_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_7_ACTUAL_SPEED_00_summary.png)

---

#### STAND_1_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.35% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 473.4445 |
| 표준편차 | 203.5734 |
| Q1 (25%) | 505.4722 |
| 중앙값 | 537.3275 |
| Q3 (75%) | 587.0544 |
| IQR | 81.5822 |
| 하한 경계 | 383.0989 |
| 상한 경계 | 709.4277 |
| 이상치 수 | 3,033 (15.35%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 535.43 | 11.90% |
| 2025-06 | 5,678 | 466.54 | 11.17% |
| 2025-07 | 2,773 | 407.15 | 26.25% |
| 2025-08 | 4,201 | 421.61 | 19.64% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 524 |
| 2 | 2025-05-17 | 484 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 395 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 524건 (2025-08-08)
- 평균 일별 이상치: 379.1건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_1_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_1_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_1_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_1_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_1_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 535.4298 |
| 중앙값 | 593.3640 |
| IQR | 38.6129 |
| 이상치 수 | 856 |
| 이상치율 | 12.04% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 491건
- 2. 2025-05-18: 365건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_1_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 466.5386 |
| 중앙값 | 521.2025 |
| IQR | 32.3747 |
| 이상치 수 | 646 |
| 이상치율 | 11.38% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 403건
- 2. 2025-06-06: 243건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_1_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 407.1533 |
| 중앙값 | 538.1027 |
| IQR | 563.4023 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_1_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 421.6139 |
| 중앙값 | 512.9676 |
| IQR | 41.5158 |
| 이상치 수 | 833 |
| 이상치율 | 19.83% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 527건
- 2. 2025-08-11: 306건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_1_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_1_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_1_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_1_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_1_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_1_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_1_ACTUAL_SPEED_00_summary.png)

---

#### PINCHROLL_4_ACTUAL_TORQUE 🔴

**위험도**: [DANGER] | **이상치율**: 15.34% | **이상치 방향**: 하한 미달

**카테고리**: 08 Pinchroll

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 26.0269 |
| 표준편차 | 10.0578 |
| Q1 (25%) | 24.9913 |
| 중앙값 | 26.5980 |
| Q3 (75%) | 33.0301 |
| IQR | 8.0388 |
| 하한 경계 | 12.9331 |
| 상한 경계 | 45.0883 |
| 이상치 수 | 2,507 (15.34%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 6,158 | 25.73 | 12.29% |
| 2025-06 | 4,896 | 27.80 | 16.71% |
| 2025-07 | 2,011 | 25.50 | 21.63% |
| 2025-08 | 3,273 | 24.25 | 15.18% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 442 |
| 2 | 2025-05-17 | 386 |
| 3 | 2025-06-06 | 376 |
| 4 | 2025-05-18 | 371 |
| 5 | 2025-08-11 | 335 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 442건 (2025-06-12)
- 평균 일별 이상치: 313.4건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_4_ACTUAL_TORQUE 종합 분석 차트](./08_Pinchroll/PINCHROLL_4_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,158 |
| 평균 | 25.7343 |
| 중앙값 | 26.5752 |
| IQR | 5.7269 |
| 이상치 수 | 820 |
| 이상치율 | 13.32% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 418건
- 2. 2025-05-18: 402건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 27.7982 |
| 중앙값 | 30.1557 |
| IQR | 5.0062 |
| 이상치 수 | 986 |
| 이상치율 | 20.14% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 542건
- 2. 2025-06-06: 444건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 25.5049 |
| 중앙값 | 26.6612 |
| IQR | 12.0942 |
| 이상치 수 | 210 |
| 이상치율 | 10.44% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 126건
- 2. 2025-07-05: 84건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 24.2486 |
| 중앙값 | 24.9950 |
| IQR | 4.3206 |
| 이상치 수 | 1,084 |
| 이상치율 | 33.12% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 733건
- 2. 2025-08-11: 351건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_3_ACTUAL_SPEED 🔴

**위험도**: [DANGER] | **이상치율**: 15.34% | **이상치 방향**: 하한 미달

**카테고리**: 06 Stand Speed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 속도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 671.6214 |
| 표준편차 | 286.4367 |
| Q1 (25%) | 720.2520 |
| 중앙값 | 779.5235 |
| Q3 (75%) | 823.6455 |
| IQR | 103.3935 |
| 하한 경계 | 565.1617 |
| 상한 경계 | 978.7358 |
| 이상치 수 | 3,031 (15.34%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 697.05 | 11.94% |
| 2025-06 | 5,678 | 728.45 | 11.06% |
| 2025-07 | 2,773 | 613.87 | 26.25% |
| 2025-08 | 4,201 | 589.90 | 19.66% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 526 |
| 2 | 2025-05-17 | 487 |
| 3 | 2025-07-04 | 415 |
| 4 | 2025-06-12 | 391 |
| 5 | 2025-05-18 | 362 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 526건 (2025-08-08)
- 평균 일별 이상치: 378.9건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./06_Stand_Speed/STAND_3_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/STAND_3_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/STAND_3_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_3_ACTUAL_SPEED 종합 분석 차트](./06_Stand_Speed/STAND_3_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 697.0506 |
| 중앙값 | 766.3763 |
| IQR | 64.1789 |
| 이상치 수 | 856 |
| 이상치율 | 12.04% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 491건
- 2. 2025-05-18: 365건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-05/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-05/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-05/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-05/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-05/STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-05/STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./06_Stand_Speed/monthly/2025-05/STAND_3_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 728.4465 |
| 중앙값 | 798.0794 |
| IQR | 66.5070 |
| 이상치 수 | 642 |
| 이상치율 | 11.31% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 401건
- 2. 2025-06-06: 241건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-06/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-06/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-06/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-06/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-06/STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-06/STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./06_Stand_Speed/monthly/2025-06/STAND_3_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 613.8674 |
| 중앙값 | 794.4805 |
| IQR | 855.5583 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-07/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-07/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-07/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-07/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-07/STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-07/STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./06_Stand_Speed/monthly/2025-07/STAND_3_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 589.8959 |
| 중앙값 | 715.4424 |
| IQR | 52.6269 |
| 이상치 수 | 856 |
| 이상치율 | 20.38% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 551건
- 2. 2025-08-11: 305건

**1. 시계열 (Time Series)**

![시계열 차트](./06_Stand_Speed/monthly/2025-08/STAND_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./06_Stand_Speed/monthly/2025-08/STAND_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./06_Stand_Speed/monthly/2025-08/STAND_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./06_Stand_Speed/monthly/2025-08/STAND_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./06_Stand_Speed/monthly/2025-08/STAND_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./06_Stand_Speed/monthly/2025-08/STAND_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./06_Stand_Speed/monthly/2025-08/STAND_3_ACTUAL_SPEED_00_summary.png)

---

### 🟠 경고 (10~15%) - 2개 태그

#### PINCHROLL_2_ACTUAL_SPEED 🟠

**위험도**: [WARNING] | **이상치율**: 14.57% | **이상치 방향**: 하한 미달

**카테고리**: 08 Pinchroll

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | -313.5339 |
| 표준편차 | 11.6502 |
| Q1 (25%) | -315.7767 |
| 중앙값 | -312.2444 |
| Q3 (75%) | -309.4422 |
| IQR | 6.3345 |
| 하한 경계 | -325.2783 |
| 상한 경계 | -299.9405 |
| 이상치 수 | 2,380 (14.57%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 6,158 | -314.04 | 11.46% |
| 2025-06 | 4,896 | -315.23 | 14.20% |
| 2025-07 | 2,011 | -310.69 | 15.76% |
| 2025-08 | 3,273 | -311.80 | 20.23% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 388 |
| 2 | 2025-05-18 | 354 |
| 3 | 2025-05-17 | 352 |
| 4 | 2025-08-08 | 346 |
| 5 | 2025-08-11 | 316 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 388건 (2025-06-12)
- 평균 일별 이상치: 297.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_2_ACTUAL_SPEED 종합 분석 차트](./08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,158 |
| 평균 | -314.0363 |
| 중앙값 | -312.3583 |
| IQR | 2.6394 |
| 이상치 수 | 1,072 |
| 이상치율 | 17.41% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 609건
- 2. 2025-05-17: 463건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | -315.2283 |
| 중앙값 | -315.5386 |
| IQR | 6.3583 |
| 이상치 수 | 1,205 |
| 이상치율 | 24.61% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 835건
- 2. 2025-06-12: 370건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | -310.6855 |
| 중앙값 | -309.7892 |
| IQR | 7.9688 |
| 이상치 수 | 335 |
| 이상치율 | 16.66% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 198건
- 2. 2025-07-04: 137건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | -311.8043 |
| 중앙값 | -310.0126 |
| IQR | 5.5274 |
| 이상치 수 | 721 |
| 이상치율 | 22.03% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 363건
- 2. 2025-08-08: 358건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_ACTUAL_SPEED_00_summary.png)

---

#### PINCHROLL_4_REFERENCE_TORQUE 🟠

**위험도**: [WARNING] | **이상치율**: 14.18% | **이상치 방향**: 상한 초과

**카테고리**: 08 Pinchroll

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 43.0513 |
| 표준편차 | 23.5949 |
| Q1 (25%) | 26.5833 |
| 중앙값 | 35.0000 |
| Q3 (75%) | 45.0283 |
| IQR | 18.4450 |
| 하한 경계 | -1.0842 |
| 상한 경계 | 72.6958 |
| 이상치 수 | 2,316 (14.18%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 6,158 | 40.98 | 11.43% |
| 2025-06 | 4,896 | 46.33 | 15.65% |
| 2025-07 | 2,011 | 46.09 | 19.19% |
| 2025-08 | 3,273 | 40.17 | 14.05% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 404 |
| 2 | 2025-05-18 | 362 |
| 3 | 2025-06-06 | 362 |
| 4 | 2025-05-17 | 342 |
| 5 | 2025-08-11 | 301 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 404건 (2025-06-12)
- 평균 일별 이상치: 289.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_4_REFERENCE_TORQUE 종합 분석 차트](./08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,158 |
| 평균 | 40.9825 |
| 중앙값 | 35.0000 |
| IQR | 20.0775 |
| 이상치 수 | 697 |
| 이상치율 | 11.32% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 359건
- 2. 2025-05-17: 338건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 46.3329 |
| 중앙값 | 39.9700 |
| IQR | 15.5042 |
| 이상치 수 | 804 |
| 이상치율 | 16.42% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 420건
- 2. 2025-06-06: 384건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 46.0904 |
| 중앙값 | 35.0000 |
| IQR | 9.2458 |
| 이상치 수 | 444 |
| 이상치율 | 22.08% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 233건
- 2. 2025-07-04: 211건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 40.1674 |
| 중앙값 | 26.5875 |
| IQR | 15.0000 |
| 이상치 수 | 495 |
| 이상치율 | 15.12% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 321건
- 2. 2025-08-08: 174건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_REFERENCE_TORQUE_00_summary.png)

---

### 🟡 주의 (5~10%) - 6개 태그

#### MAIN_COMBUSTION_AIR_PRESSURE 🟡

**위험도**: [CAUTION] | **이상치율**: 8.95% | **이상치 방향**: 하한 미달

**카테고리**: 04 Furnace Auxiliary

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1148.8956 |
| 표준편차 | 37.3498 |
| Q1 (25%) | 1154.3057 |
| 중앙값 | 1155.5470 |
| Q3 (75%) | 1156.9583 |
| IQR | 2.6525 |
| 하한 경계 | 1150.3270 |
| 상한 경계 | 1160.9370 |
| 이상치 수 | 1,803 (8.95%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 1155.94 | 1.82% |
| 2025-06 | 5,758 | 1155.54 | 6.56% |
| 2025-07 | 2,880 | 1136.65 | 25.17% |
| 2025-08 | 4,316 | 1136.48 | 13.18% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 597 |
| 2 | 2025-08-08 | 513 |
| 3 | 2025-06-06 | 242 |
| 4 | 2025-06-12 | 136 |
| 5 | 2025-07-05 | 128 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 597건 (2025-07-04)
- 평균 일별 이상치: 225.4건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_COMBUSTION_AIR_PRESSURE 종합 분석 차트](./04_Furnace_Auxiliary/MAIN_COMBUSTION_AIR_PRESSURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 1155.9388 |
| 중앙값 | 1155.7770 |
| IQR | 2.2480 |
| 이상치 수 | 218 |
| 이상치율 | 3.03% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 122건
- 2. 2025-05-18: 96건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1155.5369 |
| 중앙값 | 1155.6010 |
| IQR | 2.8895 |
| 이상치 수 | 340 |
| 이상치율 | 5.90% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 226건
- 2. 2025-06-12: 114건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1136.6476 |
| 중앙값 | 1154.8495 |
| IQR | 5.2365 |
| 이상치 수 | 573 |
| 이상치율 | 19.90% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 500건
- 2. 2025-07-05: 73건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1136.4752 |
| 중앙값 | 1155.3860 |
| IQR | 2.7033 |
| 이상치 수 | 562 |
| 이상치율 | 13.02% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 510건
- 2. 2025-08-11: 52건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_COMBUSTION_AIR_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_COMBUSTION_AIR_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_COMBUSTION_AIR_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_COMBUSTION_AIR_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_COMBUSTION_AIR_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_COMBUSTION_AIR_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_COMBUSTION_AIR_PRESSURE_00_summary.png)

---

#### FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE 🟡

**위험도**: [CAUTION] | **이상치율**: 8.34% | **이상치 방향**: 하한 미달

**카테고리**: 03 Furnace Discharge Temperature

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 압연 전 측정으로 롤교환 무관 |
| coiling_transient | ✗ | 권취 전 공정으로 무관 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 963.7951 |
| 표준편차 | 307.2609 |
| Q1 (25%) | 955.1385 |
| 중앙값 | 1044.4920 |
| Q3 (75%) | 1128.4310 |
| IQR | 173.2925 |
| 하한 경계 | 695.1997 |
| 상한 경계 | 1388.3698 |
| 이상치 수 | 1,680 (8.34%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 887.08 | 7.13% |
| 2025-06 | 5,758 | 1049.14 | 6.91% |
| 2025-07 | 2,880 | 921.20 | 17.53% |
| 2025-08 | 4,316 | 1006.17 | 6.12% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 433 |
| 2 | 2025-05-18 | 339 |
| 3 | 2025-06-06 | 226 |
| 4 | 2025-08-11 | 206 |
| 5 | 2025-05-17 | 174 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 433건 (2025-07-04)
- 평균 일별 이상치: 210.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE 종합 분석 차트](./03_Furnace_Discharge_Temperature/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 887.0756 |
| 중앙값 | 946.3384 |
| IQR | 77.1691 |
| 이상치 수 | 543 |
| 이상치율 | 7.55% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 369건
- 2. 2025-05-17: 174건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-05/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-05/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-05/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-05/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-05/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-05/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-05/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1049.1379 |
| 중앙값 | 1130.4620 |
| IQR | 85.2920 |
| 이상치 수 | 498 |
| 이상치율 | 8.65% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 274건
- 2. 2025-06-12: 224건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-06/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-06/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-06/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-06/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-06/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-06/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-06/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 921.2009 |
| 중앙값 | 1132.8305 |
| IQR | 102.8920 |
| 이상치 수 | 506 |
| 이상치율 | 17.57% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 433건
- 2. 2025-07-05: 73건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-07/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-07/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-07/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-07/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-07/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-07/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-07/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1006.1679 |
| 중앙값 | 1070.8920 |
| IQR | 96.8000 |
| 이상치 수 | 269 |
| 이상치율 | 6.23% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 206건
- 2. 2025-08-08: 63건

**1. 시계열 (Time Series)**

![시계열 차트](./03_Furnace_Discharge_Temperature/monthly/2025-08/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./03_Furnace_Discharge_Temperature/monthly/2025-08/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./03_Furnace_Discharge_Temperature/monthly/2025-08/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./03_Furnace_Discharge_Temperature/monthly/2025-08/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./03_Furnace_Discharge_Temperature/monthly/2025-08/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./03_Furnace_Discharge_Temperature/monthly/2025-08/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./03_Furnace_Discharge_Temperature/monthly/2025-08/FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE_00_summary.png)

---

#### PR7L1_ACT_TORQUE [L1] 🟡

**위험도**: [CAUTION] | **이상치율**: 6.32% | **이상치 방향**: 상한 초과

**카테고리**: 09 PR Detailed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 3.9502 |
| 표준편차 | 5.4160 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.3465 |
| Q3 (75%) | 4.8947 |
| IQR | 4.8947 |
| 하한 경계 | -7.3420 |
| 상한 경계 | 12.2367 |
| 이상치 수 | 1,249 (6.32%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 2.30 | 0.00% |
| 2025-06 | 5,678 | 4.20 | 7.50% |
| 2025-07 | 2,773 | 6.71 | 18.21% |
| 2025-08 | 4,201 | 4.58 | 7.57% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 426 |
| 2 | 2025-07-04 | 390 |
| 3 | 2025-08-08 | 318 |
| 4 | 2025-07-05 | 115 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 426건 (2025-06-06)
- 평균 일별 이상치: 312.2건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/PR7L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/PR7L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/PR7L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR7L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/PR7L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 2.3025 |
| 중앙값 | 4.3369 |
| IQR | 4.5345 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/PR7L1_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 4.2039 |
| 중앙값 | 4.3221 |
| IQR | 4.4950 |
| 이상치 수 | 446 |
| 이상치율 | 7.85% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 446건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/PR7L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 6.7072 |
| 중앙값 | 4.6025 |
| IQR | 5.4111 |
| 이상치 수 | 481 |
| 이상치율 | 17.35% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 370건
- 2. 2025-07-05: 111건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/PR7L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 4.5762 |
| 중앙값 | 5.0547 |
| IQR | 5.1289 |
| 이상치 수 | 311 |
| 이상치율 | 7.40% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 311건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/PR7L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/PR7L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/PR7L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/PR7L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/PR7L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/PR7L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/PR7L1_ACT_TORQUE_00_summary.png)

---

#### PR9L1_ACT_TORQUE [L1] 🟡

**위험도**: [CAUTION] | **이상치율**: 6.28% | **이상치 방향**: 하한 미달

**카테고리**: 09 PR Detailed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | -3.0798 |
| 표준편차 | 8.7028 |
| Q1 (25%) | -5.1335 |
| 중앙값 | 0.0000 |
| Q3 (75%) | 2.4625 |
| IQR | 7.5960 |
| 하한 경계 | -16.5276 |
| 상한 경계 | 13.8566 |
| 이상치 수 | 1,242 (6.28%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | -1.41 | 0.00% |
| 2025-06 | 5,678 | -3.42 | 7.47% |
| 2025-07 | 2,773 | -6.04 | 17.92% |
| 2025-08 | 4,201 | -3.49 | 7.64% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 424 |
| 2 | 2025-07-04 | 385 |
| 3 | 2025-08-08 | 321 |
| 4 | 2025-07-05 | 112 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 424건 (2025-06-06)
- 평균 일별 이상치: 310.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/PR9L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/PR9L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/PR9L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR9L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/PR9L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | -1.4081 |
| 중앙값 | 0.0000 |
| IQR | 0.5083 |
| 이상치 수 | 3,474 |
| 이상치율 | 48.85% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 2,357건
- 2. 2025-05-18: 1,117건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/PR9L1_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | -3.4228 |
| 중앙값 | 0.0000 |
| IQR | 8.5528 |
| 이상치 수 | 400 |
| 이상치율 | 7.04% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 400건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/PR9L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | -6.0444 |
| 중앙값 | 0.0000 |
| IQR | 12.6559 |
| 이상치 수 | 372 |
| 이상치율 | 13.42% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 286건
- 2. 2025-07-05: 86건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/PR9L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | -3.4890 |
| 중앙값 | 0.0000 |
| IQR | 9.0759 |
| 이상치 수 | 295 |
| 이상치율 | 7.02% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 295건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/PR9L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/PR9L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/PR9L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/PR9L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/PR9L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/PR9L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/PR9L1_ACT_TORQUE_00_summary.png)

---

#### PR7L2_ACT_TORQUE [L2] 🟡

**위험도**: [CAUTION] | **이상치율**: 5.58% | **이상치 방향**: 상한 초과

**카테고리**: 09 PR Detailed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 4.5811 |
| 표준편차 | 5.4978 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 5.7893 |
| Q3 (75%) | 6.1015 |
| IQR | 6.1015 |
| 하한 경계 | -9.1523 |
| 상한 경계 | 15.2538 |
| 이상치 수 | 1,102 (5.58%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 3.10 | 0.00% |
| 2025-06 | 5,678 | 4.98 | 6.62% |
| 2025-07 | 2,773 | 7.00 | 16.26% |
| 2025-08 | 4,201 | 4.95 | 6.55% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 376 |
| 2 | 2025-07-04 | 346 |
| 3 | 2025-08-08 | 275 |
| 4 | 2025-07-05 | 105 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 376건 (2025-06-06)
- 평균 일별 이상치: 275.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/PR7L2_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/PR7L2_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/PR7L2_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR7L2_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/PR7L2_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 3.1007 |
| 중앙값 | 5.9613 |
| IQR | 6.1157 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/PR7L2_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 4.9798 |
| 중앙값 | 5.8703 |
| IQR | 6.0967 |
| 이상치 수 | 376 |
| 이상치율 | 6.62% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 376건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/PR7L2_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 6.9972 |
| 중앙값 | 4.9331 |
| IQR | 6.2761 |
| 이상치 수 | 446 |
| 이상치율 | 16.08% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 344건
- 2. 2025-07-05: 102건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/PR7L2_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 4.9532 |
| 중앙값 | 5.8158 |
| IQR | 6.0354 |
| 이상치 수 | 279 |
| 이상치율 | 6.64% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 279건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/PR7L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/PR7L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/PR7L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/PR7L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/PR7L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/PR7L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/PR7L2_ACT_TORQUE_00_summary.png)

---

#### PR6L1_ACT_TORQUE [L1] 🟡

**위험도**: [CAUTION] | **이상치율**: 5.27% | **이상치 방향**: 상한 초과

**카테고리**: 09 PR Detailed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 3.2823 |
| 표준편차 | 4.4891 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 3.4028 |
| Q3 (75%) | 4.2483 |
| IQR | 4.2483 |
| 하한 경계 | -6.3724 |
| 상한 경계 | 10.6207 |
| 이상치 수 | 1,042 (5.27%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 2.20 | 0.00% |
| 2025-06 | 5,678 | 4.42 | 12.15% |
| 2025-07 | 2,773 | 2.66 | 0.00% |
| 2025-08 | 4,201 | 3.98 | 8.38% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-12 | 532 |
| 2 | 2025-08-08 | 300 |
| 3 | 2025-06-06 | 158 |
| 4 | 2025-08-11 | 52 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 532건 (2025-06-12)
- 평균 일별 이상치: 260.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/PR6L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/PR6L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/PR6L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR6L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/PR6L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 2.1999 |
| 중앙값 | 4.1535 |
| IQR | 4.2994 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/PR6L1_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 4.4248 |
| 중앙값 | 3.8056 |
| IQR | 4.2506 |
| 이상치 수 | 688 |
| 이상치율 | 12.12% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 532건
- 2. 2025-06-06: 156건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/PR6L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 2.6646 |
| 중앙값 | 3.3438 |
| IQR | 3.9156 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/PR6L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 3.9783 |
| 중앙값 | 3.7662 |
| IQR | 3.9064 |
| 이상치 수 | 359 |
| 이상치율 | 8.55% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 307건
- 2. 2025-08-11: 52건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/PR6L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/PR6L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/PR6L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/PR6L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/PR6L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/PR6L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/PR6L1_ACT_TORQUE_00_summary.png)

---

### 🟢 양호 (0~5%) - 53개 태그

#### PR8L1_ACT_TORQUE [L1] 🟢

**위험도**: [NORMAL] | **이상치율**: 4.77% | **이상치 방향**: 상한 초과

**카테고리**: 09 PR Detailed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 5.3644 |
| 표준편차 | 6.5472 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.3775 |
| Q3 (75%) | 7.0644 |
| IQR | 7.0644 |
| 하한 경계 | -10.5966 |
| 상한 경계 | 17.6610 |
| 이상치 수 | 942 (4.77%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 4.14 | 0.00% |
| 2025-06 | 5,678 | 5.62 | 5.60% |
| 2025-07 | 2,773 | 7.15 | 13.85% |
| 2025-08 | 4,201 | 5.91 | 5.71% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 318 |
| 2 | 2025-07-04 | 298 |
| 3 | 2025-08-08 | 240 |
| 4 | 2025-07-05 | 86 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 318건 (2025-06-06)
- 평균 일별 이상치: 235.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/PR8L1_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/PR8L1_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/PR8L1_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR8L1_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/PR8L1_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 4.1360 |
| 중앙값 | 1.5258 |
| IQR | 4.9021 |
| 이상치 수 | 1,071 |
| 이상치율 | 15.06% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 708건
- 2. 2025-05-18: 363건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/PR8L1_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 5.6232 |
| 중앙값 | 4.5823 |
| IQR | 7.6221 |
| 이상치 수 | 308 |
| 이상치율 | 5.42% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 308건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/PR8L1_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 7.1503 |
| 중앙값 | 4.2562 |
| IQR | 10.6298 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/PR8L1_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 5.9150 |
| 중앙값 | 4.8364 |
| IQR | 8.4073 |
| 이상치 수 | 215 |
| 이상치율 | 5.12% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 215건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/PR8L1_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/PR8L1_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/PR8L1_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/PR8L1_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/PR8L1_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/PR8L1_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/PR8L1_ACT_TORQUE_00_summary.png)

---

#### MAIN_GAS_PRESSURE 🟢

**위험도**: [NORMAL] | **이상치율**: 4.67% | **이상치 방향**: 양방향

**카테고리**: 04 Furnace Auxiliary

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1565.2726 |
| 표준편차 | 21.5173 |
| Q1 (25%) | 1554.0930 |
| 중앙값 | 1568.4025 |
| Q3 (75%) | 1576.2930 |
| IQR | 22.2000 |
| 하한 경계 | 1520.7930 |
| 상한 경계 | 1609.5930 |
| 이상치 수 | 940 (4.67%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 1573.27 | 2.85% |
| 2025-06 | 5,758 | 1569.07 | 1.98% |
| 2025-07 | 2,880 | 1546.55 | 14.97% |
| 2025-08 | 4,316 | 1559.38 | 4.40% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 307 |
| 2 | 2025-05-18 | 183 |
| 3 | 2025-08-08 | 168 |
| 4 | 2025-07-05 | 124 |
| 5 | 2025-06-06 | 96 |

- 이상치 발생 일수: 8일
- 최대 일별 이상치: 307건 (2025-07-04)
- 평균 일별 이상치: 117.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_GAS_PRESSURE 종합 분석 차트](./04_Furnace_Auxiliary/MAIN_GAS_PRESSURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 1573.2700 |
| 중앙값 | 1572.3810 |
| IQR | 16.7850 |
| 이상치 수 | 346 |
| 이상치율 | 4.81% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 210건
- 2. 2025-05-17: 136건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_PRESSURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1569.0659 |
| 중앙값 | 1571.3480 |
| IQR | 18.0515 |
| 이상치 수 | 250 |
| 이상치율 | 4.34% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 224건
- 2. 2025-06-12: 26건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_PRESSURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1546.5474 |
| 중앙값 | 1549.6225 |
| IQR | 25.2325 |
| 이상치 수 | 205 |
| 이상치율 | 7.12% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 136건
- 2. 2025-07-05: 69건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1559.3842 |
| 중앙값 | 1565.0010 |
| IQR | 22.1420 |
| 이상치 수 | 143 |
| 이상치율 | 3.31% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 107건
- 2. 2025-08-11: 36건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_PRESSURE_00_summary.png)

---

#### SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 2.80% | **이상치 방향**: 하한 미달

**카테고리**: 02 Furnace Bottom Temperature

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1082.7396 |
| 표준편차 | 51.6884 |
| Q1 (25%) | 1063.2802 |
| 중앙값 | 1088.0315 |
| Q3 (75%) | 1119.2468 |
| IQR | 55.9665 |
| 하한 경계 | 979.3305 |
| 상한 경계 | 1203.1965 |
| 이상치 수 | 564 (2.80%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 1086.01 | 0.00% |
| 2025-06 | 5,758 | 1100.64 | 0.00% |
| 2025-07 | 2,880 | 1070.33 | 9.58% |
| 2025-08 | 4,316 | 1061.69 | 6.67% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 288 |
| 2 | 2025-07-04 | 276 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 288건 (2025-08-08)
- 평균 일별 이상치: 282.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 1086.0099 |
| 중앙값 | 1089.4800 |
| IQR | 73.1717 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1100.6424 |
| 중앙값 | 1103.4770 |
| IQR | 53.1345 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1070.3306 |
| 중앙값 | 1090.9475 |
| IQR | 49.6998 |
| 이상치 수 | 287 |
| 이상치율 | 9.97% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 287건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1061.6879 |
| 중앙값 | 1078.2915 |
| IQR | 33.7242 |
| 이상치 수 | 296 |
| 이상치율 | 6.86% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 294건
- 2. 2025-08-11: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

---

#### SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 2.78% | **이상치 방향**: 하한 미달

**카테고리**: 02 Furnace Bottom Temperature

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1103.6226 |
| 표준편차 | 52.4373 |
| Q1 (25%) | 1082.7047 |
| 중앙값 | 1111.2365 |
| Q3 (75%) | 1139.9180 |
| IQR | 57.2133 |
| 하한 경계 | 996.8849 |
| 상한 경계 | 1225.7379 |
| 이상치 수 | 561 (2.78%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 1108.22 | 0.00% |
| 2025-06 | 5,758 | 1122.14 | 0.00% |
| 2025-07 | 2,880 | 1089.66 | 9.48% |
| 2025-08 | 4,316 | 1080.58 | 6.67% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 288 |
| 2 | 2025-07-04 | 273 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 288건 (2025-08-08)
- 평균 일별 이상치: 280.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 1108.2186 |
| 중앙값 | 1114.8370 |
| IQR | 78.1090 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1122.1419 |
| 중앙값 | 1127.9190 |
| IQR | 53.7720 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1089.6584 |
| 중앙값 | 1109.9835 |
| IQR | 47.4560 |
| 이상치 수 | 282 |
| 이상치율 | 9.79% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 282건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1080.5773 |
| 중앙값 | 1097.7560 |
| IQR | 34.9610 |
| 이상치 수 | 290 |
| 이상치율 | 6.72% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 290건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

---

#### SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 2.78% | **이상치 방향**: 하한 미달

**카테고리**: 01 Furnace Top Temperature

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1102.5063 |
| 표준편차 | 48.4907 |
| Q1 (25%) | 1082.1650 |
| 중앙값 | 1118.5935 |
| Q3 (75%) | 1131.6910 |
| IQR | 49.5260 |
| 하한 경계 | 1007.8760 |
| 상한 경계 | 1205.9800 |
| 이상치 수 | 560 (2.78%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 1108.68 | 0.00% |
| 2025-06 | 5,758 | 1115.72 | 0.00% |
| 2025-07 | 2,880 | 1092.57 | 9.48% |
| 2025-08 | 4,316 | 1081.22 | 6.65% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 287 |
| 2 | 2025-07-04 | 273 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 287건 (2025-08-08)
- 평균 일별 이상치: 280.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 1108.6839 |
| 중앙값 | 1118.9410 |
| IQR | 51.8145 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1115.7202 |
| 중앙값 | 1127.5850 |
| IQR | 51.1115 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1092.5664 |
| 중앙값 | 1122.0050 |
| IQR | 40.3332 |
| 이상치 수 | 321 |
| 이상치율 | 11.15% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 292건
- 2. 2025-07-05: 29건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1081.2190 |
| 중앙값 | 1095.3040 |
| IQR | 45.9810 |
| 이상치 수 | 287 |
| 이상치율 | 6.65% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 287건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

---

#### SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 2.75% | **이상치 방향**: 하한 미달

**카테고리**: 01 Furnace Top Temperature

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1119.6720 |
| 표준편차 | 48.6399 |
| Q1 (25%) | 1097.2150 |
| 중앙값 | 1134.7615 |
| Q3 (75%) | 1148.9290 |
| IQR | 51.7140 |
| 하한 경계 | 1019.6440 |
| 상한 경계 | 1226.5000 |
| 이상치 수 | 554 (2.75%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 1126.41 | 0.00% |
| 2025-06 | 5,758 | 1133.59 | 0.00% |
| 2025-07 | 2,880 | 1108.85 | 9.27% |
| 2025-08 | 4,316 | 1097.11 | 6.65% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 287 |
| 2 | 2025-07-04 | 267 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 287건 (2025-08-08)
- 평균 일별 이상치: 277.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 1126.4076 |
| 중앙값 | 1141.0460 |
| IQR | 56.2865 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1133.5869 |
| 중앙값 | 1144.9550 |
| IQR | 52.2292 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1108.8518 |
| 중앙값 | 1137.4735 |
| IQR | 35.5932 |
| 이상치 수 | 341 |
| 이상치율 | 11.84% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 299건
- 2. 2025-07-05: 42건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1097.1073 |
| 중앙값 | 1113.0200 |
| IQR | 45.1130 |
| 이상치 수 | 287 |
| 이상치율 | 6.65% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 287건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

---

#### FURNACE_PRESSURE 🟢

**위험도**: [NORMAL] | **이상치율**: 2.23% | **이상치 방향**: 상한 초과

**카테고리**: 04 Furnace Auxiliary

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 0.4739 |
| 표준편차 | 0.0230 |
| Q1 (25%) | 0.4581 |
| 중앙값 | 0.4741 |
| Q3 (75%) | 0.4865 |
| IQR | 0.0283 |
| 하한 경계 | 0.4157 |
| 상한 경계 | 0.5289 |
| 이상치 수 | 450 (2.23%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 0.47 | 0.00% |
| 2025-06 | 5,758 | 0.48 | 6.15% |
| 2025-07 | 2,880 | 0.47 | 2.92% |
| 2025-08 | 4,316 | 0.47 | 0.28% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-06-06 | 322 |
| 2 | 2025-07-04 | 66 |
| 3 | 2025-06-12 | 32 |
| 4 | 2025-07-05 | 18 |
| 5 | 2025-08-08 | 12 |

- 이상치 발생 일수: 5일
- 최대 일별 이상치: 322건 (2025-06-06)
- 평균 일별 이상치: 90.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/FURNACE_PRESSURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/FURNACE_PRESSURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/FURNACE_PRESSURE_07_daily_outlier_count.png)

**종합 분석 차트**

![FURNACE_PRESSURE 종합 분석 차트](./04_Furnace_Auxiliary/FURNACE_PRESSURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 0.4694 |
| 중앙값 | 0.4714 |
| IQR | 0.0196 |
| 이상치 수 | 38 |
| 이상치율 | 0.53% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 36건
- 2. 2025-05-17: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/FURNACE_PRESSURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 0.4829 |
| 중앙값 | 0.4837 |
| IQR | 0.0321 |
| 이상치 수 | 202 |
| 이상치율 | 3.51% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-06: 180건
- 2. 2025-06-12: 22건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/FURNACE_PRESSURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 0.4722 |
| 중앙값 | 0.4718 |
| IQR | 0.0414 |
| 이상치 수 | 11 |
| 이상치율 | 0.38% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 10건
- 2. 2025-07-05: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/FURNACE_PRESSURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 0.4704 |
| 중앙값 | 0.4726 |
| IQR | 0.0307 |
| 이상치 수 | 8 |
| 이상치율 | 0.19% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 8건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_PRESSURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_PRESSURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_PRESSURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_PRESSURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_PRESSURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_PRESSURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/FURNACE_PRESSURE_00_summary.png)

---

#### HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 2.04% | **이상치 방향**: 하한 미달

**카테고리**: 01 Furnace Top Temperature

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1038.0606 |
| 표준편차 | 38.2874 |
| Q1 (25%) | 1003.7480 |
| 중앙값 | 1051.6895 |
| Q3 (75%) | 1064.1598 |
| IQR | 60.4117 |
| 하한 경계 | 913.1304 |
| 상한 경계 | 1154.7774 |
| 이상치 수 | 411 (2.04%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 1038.10 | 0.25% |
| 2025-06 | 5,758 | 1044.14 | 0.00% |
| 2025-07 | 2,880 | 1039.29 | 7.36% |
| 2025-08 | 4,316 | 1029.06 | 4.19% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 212 |
| 2 | 2025-08-08 | 181 |
| 3 | 2025-05-18 | 18 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 212건 (2025-07-04)
- 평균 일별 이상치: 137.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 1038.0964 |
| 중앙값 | 1052.9590 |
| IQR | 64.8505 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1044.1443 |
| 중앙값 | 1054.0980 |
| IQR | 57.0187 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1039.2919 |
| 중앙값 | 1053.2725 |
| IQR | 33.2100 |
| 이상치 수 | 345 |
| 이상치율 | 11.98% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 255건
- 2. 2025-07-05: 90건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1029.0631 |
| 중앙값 | 1047.1695 |
| IQR | 55.4303 |
| 이상치 수 | 221 |
| 이상치율 | 5.12% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 221건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF_00_summary.png)

---

#### HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 🟢

**위험도**: [NORMAL] | **이상치율**: 1.89% | **이상치 방향**: 하한 미달

**카테고리**: 01 Furnace Top Temperature

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1035.6568 |
| 표준편차 | 38.8125 |
| Q1 (25%) | 1000.4058 |
| 중앙값 | 1049.6660 |
| Q3 (75%) | 1062.3710 |
| IQR | 61.9653 |
| 하한 경계 | 907.4579 |
| 상한 경계 | 1155.3189 |
| 이상치 수 | 380 (1.89%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 1035.99 | 0.13% |
| 2025-06 | 5,758 | 1042.02 | 0.00% |
| 2025-07 | 2,880 | 1036.34 | 7.36% |
| 2025-08 | 4,316 | 1026.16 | 3.68% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 212 |
| 2 | 2025-08-08 | 159 |
| 3 | 2025-05-18 | 9 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 212건 (2025-07-04)
- 평균 일별 이상치: 126.7건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF 종합 분석 차트](./01_Furnace_Top_Temperature/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 1035.9886 |
| 중앙값 | 1051.3980 |
| IQR | 67.4598 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-05/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1042.0210 |
| 중앙값 | 1052.3180 |
| IQR | 57.7245 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-06/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1036.3438 |
| 중앙값 | 1050.1550 |
| IQR | 32.2332 |
| 이상치 수 | 358 |
| 이상치율 | 12.43% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 259건
- 2. 2025-07-05: 99건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-07/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1026.1552 |
| 중앙값 | 1044.3540 |
| IQR | 58.1168 |
| 이상치 수 | 185 |
| 이상치율 | 4.29% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 185건

**1. 시계열 (Time Series)**

![시계열 차트](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./01_Furnace_Top_Temperature/monthly/2025-08/HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF_00_summary.png)

---

#### HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.66% | **이상치 방향**: 하한 미달

**카테고리**: 02 Furnace Bottom Temperature

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 972.6013 |
| 표준편차 | 44.5651 |
| Q1 (25%) | 942.3050 |
| 중앙값 | 970.3199 |
| Q3 (75%) | 1002.9942 |
| IQR | 60.6892 |
| 하한 경계 | 851.2712 |
| 상한 경계 | 1094.0280 |
| 이상치 수 | 133 (0.66%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 974.02 | 0.00% |
| 2025-06 | 5,758 | 985.01 | 0.00% |
| 2025-07 | 2,880 | 968.72 | 2.57% |
| 2025-08 | 4,316 | 956.26 | 1.37% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-04 | 59 |
| 2 | 2025-08-08 | 59 |
| 3 | 2025-07-05 | 15 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 59건 (2025-07-04)
- 평균 일별 이상치: 44.3건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 974.0227 |
| 중앙값 | 971.3668 |
| IQR | 88.3119 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 985.0144 |
| 중앙값 | 980.6125 |
| IQR | 51.4287 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 968.7186 |
| 중앙값 | 969.5505 |
| IQR | 53.7223 |
| 이상치 수 | 248 |
| 이상치율 | 8.61% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 212건
- 2. 2025-07-05: 36건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 956.2636 |
| 중앙값 | 956.4466 |
| IQR | 41.5104 |
| 이상치 수 | 362 |
| 이상치율 | 8.39% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 302건
- 2. 2025-08-11: 60건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE_00_summary.png)

---

#### HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.61% | **이상치 방향**: 양방향

**카테고리**: 02 Furnace Bottom Temperature

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 온도 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 열관성이 커서 롤교환 영향 없음 |
| coiling_transient | ✗ | 권취 공정과 무관 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 945.6271 |
| 표준편차 | 44.2717 |
| Q1 (25%) | 913.2901 |
| 중앙값 | 939.7899 |
| Q3 (75%) | 974.7621 |
| IQR | 61.4720 |
| 하한 경계 | 821.0820 |
| 상한 경계 | 1066.9701 |
| 이상치 수 | 123 (0.61%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 946.57 | 0.08% |
| 2025-06 | 5,758 | 956.49 | 0.00% |
| 2025-07 | 2,880 | 944.54 | 2.53% |
| 2025-08 | 4,316 | 930.29 | 1.02% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 44 |
| 2 | 2025-07-05 | 37 |
| 3 | 2025-07-04 | 36 |
| 4 | 2025-05-17 | 6 |

- 이상치 발생 일수: 4일
- 최대 일별 이상치: 44건 (2025-08-08)
- 평균 일별 이상치: 30.8건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_07_daily_outlier_count.png)

**종합 분석 차트**

![HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE 종합 분석 차트](./02_Furnace_Bottom_Temperature/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 946.5727 |
| 중앙값 | 940.9927 |
| IQR | 77.9735 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-05/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 956.4873 |
| 중앙값 | 952.7126 |
| IQR | 57.1269 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-06/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 944.5443 |
| 중앙값 | 943.1878 |
| IQR | 54.2767 |
| 이상치 수 | 104 |
| 이상치율 | 3.61% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 62건
- 2. 2025-07-05: 42건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-07/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 930.2857 |
| 중앙값 | 925.6385 |
| IQR | 42.2710 |
| 이상치 수 | 440 |
| 이상치율 | 10.19% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 312건
- 2. 2025-08-11: 128건

**1. 시계열 (Time Series)**

![시계열 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./02_Furnace_Bottom_Temperature/monthly/2025-08/HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE_00_summary.png)

---

#### PR6L2_ACT_TORQUE [L2] 🟢

**위험도**: [NORMAL] | **이상치율**: 0.49% | **이상치 방향**: 상한 초과

**카테고리**: 09 PR Detailed

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 3.2784 |
| 표준편차 | 2.9503 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 4.2136 |
| Q3 (75%) | 5.6852 |
| IQR | 5.6852 |
| 하한 경계 | -8.5278 |
| 상한 경계 | 14.2129 |
| 이상치 수 | 96 (0.49%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 2.94 | 0.00% |
| 2025-06 | 5,678 | 3.41 | 0.00% |
| 2025-07 | 2,773 | 3.36 | 0.00% |
| 2025-08 | 4,201 | 3.62 | 2.29% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-11 | 54 |
| 2 | 2025-08-08 | 42 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 54건 (2025-08-11)
- 평균 일별 이상치: 48.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./09_PR_Detailed/PR6L2_ACT_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/PR6L2_ACT_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/PR6L2_ACT_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PR6L2_ACT_TORQUE 종합 분석 차트](./09_PR_Detailed/PR6L2_ACT_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 2.9371 |
| 중앙값 | 5.6222 |
| IQR | 5.7887 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-05/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-05/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-05/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-05/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-05/PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-05/PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./09_PR_Detailed/monthly/2025-05/PR6L2_ACT_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 3.4126 |
| 중앙값 | 4.4052 |
| IQR | 5.6658 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-06/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-06/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-06/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-06/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-06/PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-06/PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./09_PR_Detailed/monthly/2025-06/PR6L2_ACT_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 3.3597 |
| 중앙값 | 4.0761 |
| IQR | 5.2317 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-07/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-07/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-07/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-07/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-07/PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-07/PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./09_PR_Detailed/monthly/2025-07/PR6L2_ACT_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 3.6211 |
| 중앙값 | 4.0966 |
| IQR | 5.3362 |
| 이상치 수 | 98 |
| 이상치율 | 2.33% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-11: 54건
- 2. 2025-08-08: 44건

**1. 시계열 (Time Series)**

![시계열 차트](./09_PR_Detailed/monthly/2025-08/PR6L2_ACT_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./09_PR_Detailed/monthly/2025-08/PR6L2_ACT_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./09_PR_Detailed/monthly/2025-08/PR6L2_ACT_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./09_PR_Detailed/monthly/2025-08/PR6L2_ACT_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./09_PR_Detailed/monthly/2025-08/PR6L2_ACT_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./09_PR_Detailed/monthly/2025-08/PR6L2_ACT_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./09_PR_Detailed/monthly/2025-08/PR6L2_ACT_TORQUE_00_summary.png)

---

#### COMBUSTION_AIR_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.37% | **이상치 방향**: 상한 초과

**카테고리**: 04 Furnace Auxiliary

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 40.3285 |
| 표준편차 | 4.5722 |
| Q1 (25%) | 36.7299 |
| 중앙값 | 41.2074 |
| Q3 (75%) | 43.6941 |
| IQR | 6.9642 |
| 하한 경계 | 26.2836 |
| 상한 경계 | 54.1404 |
| 이상치 수 | 75 (0.37%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 35.72 | 0.00% |
| 2025-06 | 5,758 | 41.37 | 0.00% |
| 2025-07 | 2,880 | 45.40 | 2.33% |
| 2025-08 | 4,316 | 43.24 | 0.19% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-07-05 | 48 |
| 2 | 2025-07-04 | 19 |
| 3 | 2025-08-08 | 8 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 48건 (2025-07-05)
- 평균 일별 이상치: 25.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/COMBUSTION_AIR_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/COMBUSTION_AIR_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/COMBUSTION_AIR_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![COMBUSTION_AIR_TEMPERATURE 종합 분석 차트](./04_Furnace_Auxiliary/COMBUSTION_AIR_TEMPERATURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 35.7201 |
| 중앙값 | 35.4886 |
| IQR | 4.2980 |
| 이상치 수 | 60 |
| 이상치율 | 0.83% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 60건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/COMBUSTION_AIR_TEMPERATURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 41.3654 |
| 중앙값 | 40.8284 |
| IQR | 5.4124 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/COMBUSTION_AIR_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 45.4008 |
| 중앙값 | 44.8056 |
| IQR | 3.3372 |
| 이상치 수 | 97 |
| 이상치율 | 3.37% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 74건
- 2. 2025-07-04: 23건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/COMBUSTION_AIR_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 43.2377 |
| 중앙값 | 43.0405 |
| IQR | 1.1802 |
| 이상치 수 | 713 |
| 이상치율 | 16.52% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 603건
- 2. 2025-08-11: 110건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/COMBUSTION_AIR_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/COMBUSTION_AIR_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/COMBUSTION_AIR_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/COMBUSTION_AIR_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/COMBUSTION_AIR_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/COMBUSTION_AIR_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/COMBUSTION_AIR_TEMPERATURE_00_summary.png)

---

#### PINCHROLL_2_REFERENCE_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.04% | **이상치 방향**: 상한 초과

**카테고리**: 08 Pinchroll

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 20.0150 |
| 표준편차 | 0.8650 |
| Q1 (25%) | 20.0000 |
| 중앙값 | 20.0000 |
| Q3 (75%) | 20.0000 |
| IQR | 0.0000 |
| 하한 경계 | 20.0000 |
| 상한 경계 | 20.0000 |
| 이상치 수 | 7 (0.04%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 6,158 | 20.02 | 0.06% |
| 2025-06 | 4,896 | 20.02 | 0.06% |
| 2025-07 | 2,011 | 20.00 | 0.00% |
| 2025-08 | 3,273 | 20.00 | 0.00% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-17 | 3 |
| 2 | 2025-06-12 | 3 |
| 3 | 2025-05-18 | 1 |

- 이상치 발생 일수: 3일
- 최대 일별 이상치: 3건 (2025-05-17)
- 평균 일별 이상치: 2.3건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_2_REFERENCE_TORQUE 종합 분석 차트](./08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,158 |
| 평균 | 20.0236 |
| 중앙값 | 20.0000 |
| IQR | 0.0000 |
| 이상치 수 | 4 |
| 이상치율 | 0.06% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 3건
- 2. 2025-05-18: 1건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_2_REFERENCE_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 20.0205 |
| 중앙값 | 20.0000 |
| IQR | 0.0000 |
| 이상치 수 | 3 |
| 이상치율 | 0.06% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 3건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_2_REFERENCE_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 20.0000 |
| 중앙값 | 20.0000 |
| IQR | 0.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_2_REFERENCE_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 20.0000 |
| 중앙값 | 20.0000 |
| IQR | 0.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_2_REFERENCE_TORQUE_00_summary.png)

---

#### PINCHROLL_3_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.02% | **이상치 방향**: 하한 미달

**카테고리**: 08 Pinchroll

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 1649.9720 |
| 표준편차 | 358.0700 |
| Q1 (25%) | 1276.2150 |
| 중앙값 | 1940.1720 |
| Q3 (75%) | 1972.5200 |
| IQR | 696.3050 |
| 하한 경계 | 231.7575 |
| 상한 경계 | 3016.9775 |
| 이상치 수 | 3 (0.02%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 6,158 | 1661.87 | 0.03% |
| 2025-06 | 4,896 | 1597.69 | 0.00% |
| 2025-07 | 2,011 | 1508.75 | 0.00% |
| 2025-08 | 3,273 | 1792.56 | 0.03% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-05-18 | 2 |
| 2 | 2025-08-08 | 1 |

- 이상치 발생 일수: 2일
- 최대 일별 이상치: 2건 (2025-05-18)
- 평균 일별 이상치: 1.5건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_3_ACTUAL_SPEED 종합 분석 차트](./08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,158 |
| 평균 | 1661.8732 |
| 중앙값 | 1958.5280 |
| IQR | 684.3670 |
| 이상치 수 | 2 |
| 이상치율 | 0.03% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-18: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 1597.6880 |
| 중앙값 | 1276.2180 |
| IQR | 701.3970 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 1508.7451 |
| 중앙값 | 1255.5970 |
| IQR | 767.1730 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 1792.5635 |
| 중앙값 | 1941.8240 |
| IQR | 61.5300 |
| 이상치 수 | 772 |
| 이상치율 | 23.59% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 772건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_SPEED_00_summary.png)

---

#### PINCHROLL_4_ACTUAL_SPEED 🟢

**위험도**: [NORMAL] | **이상치율**: 0.01% | **이상치 방향**: 하한 미달

**카테고리**: 08 Pinchroll

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 1630.7971 |
| 표준편차 | 381.4557 |
| Q1 (25%) | 1215.6890 |
| 중앙값 | 1932.2960 |
| Q3 (75%) | 1957.1330 |
| IQR | 741.4440 |
| 하한 경계 | 103.5230 |
| 상한 경계 | 3069.2990 |
| 이상치 수 | 1 (0.01%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 6,158 | 1628.55 | 0.00% |
| 2025-06 | 4,896 | 1608.57 | 0.00% |
| 2025-07 | 2,011 | 1467.64 | 0.00% |
| 2025-08 | 3,273 | 1768.52 | 0.03% |

**주요 이상치 발생 날짜** (상위 5일):

| 순위 | 날짜 | 이상치 수 |
|:----:|------|----------:|
| 1 | 2025-08-08 | 1 |

- 이상치 발생 일수: 1일
- 최대 일별 이상치: 1건 (2025-08-08)
- 평균 일별 이상치: 1.0건


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_4_ACTUAL_SPEED 종합 분석 차트](./08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,158 |
| 평균 | 1628.5525 |
| 중앙값 | 1943.9200 |
| IQR | 735.5240 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 1608.5685 |
| 중앙값 | 1274.9500 |
| IQR | 827.8580 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 1467.6444 |
| 중앙값 | 1224.2530 |
| IQR | 729.2730 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 1768.5161 |
| 중앙값 | 1935.8890 |
| IQR | 42.4310 |
| 이상치 수 | 772 |
| 이상치율 | 23.59% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 772건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_SPEED_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_SPEED_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_SPEED_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_SPEED_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_SPEED_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_SPEED_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_4_ACTUAL_SPEED_00_summary.png)

---

#### MAIN_GAS_FLOW 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 04 Furnace Auxiliary

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 1429.4984 |
| 표준편차 | 671.5521 |
| Q1 (25%) | 885.0948 |
| 중앙값 | 1609.4720 |
| Q3 (75%) | 1950.9485 |
| IQR | 1065.8537 |
| 하한 경계 | -713.6858 |
| 상한 경계 | 3549.7290 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 1493.21 | 0.00% |
| 2025-06 | 5,758 | 1432.27 | 0.00% |
| 2025-07 | 2,880 | 1358.78 | 0.00% |
| 2025-08 | 4,316 | 1366.86 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/MAIN_GAS_FLOW_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/MAIN_GAS_FLOW_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/MAIN_GAS_FLOW_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_GAS_FLOW 종합 분석 차트](./04_Furnace_Auxiliary/MAIN_GAS_FLOW_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 1493.2073 |
| 중앙값 | 1711.1240 |
| IQR | 926.9040 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_FLOW_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 1432.2668 |
| 중앙값 | 1567.2160 |
| IQR | 1003.6271 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_FLOW_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 1358.7804 |
| 중앙값 | 1414.2270 |
| IQR | 1469.3494 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_FLOW_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 1366.8619 |
| 중앙값 | 1558.9245 |
| IQR | 1123.0848 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_FLOW_00_summary.png)

---

#### MAIN_GAS_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 04 Furnace Auxiliary

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 22.8837 |
| 표준편차 | 4.1085 |
| Q1 (25%) | 19.4069 |
| 중앙값 | 23.6398 |
| Q3 (75%) | 26.6000 |
| IQR | 7.1931 |
| 하한 경계 | 8.6172 |
| 상한 경계 | 37.3897 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 18.48 | 0.00% |
| 2025-06 | 5,758 | 23.36 | 0.00% |
| 2025-07 | 2,880 | 26.94 | 0.00% |
| 2025-08 | 4,316 | 26.89 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/MAIN_GAS_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/MAIN_GAS_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/MAIN_GAS_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![MAIN_GAS_TEMPERATURE 종합 분석 차트](./04_Furnace_Auxiliary/MAIN_GAS_TEMPERATURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 18.4754 |
| 중앙값 | 18.1000 |
| IQR | 2.7039 |
| 이상치 수 | 294 |
| 이상치율 | 4.09% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 294건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/MAIN_GAS_TEMPERATURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 23.3572 |
| 중앙값 | 22.6460 |
| IQR | 4.5032 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/MAIN_GAS_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 26.9438 |
| 중앙값 | 26.6098 |
| IQR | 2.5141 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/MAIN_GAS_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 26.8865 |
| 중앙값 | 26.8000 |
| IQR | 0.8952 |
| 이상치 수 | 362 |
| 이상치율 | 8.39% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 362건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/MAIN_GAS_TEMPERATURE_00_summary.png)

---

#### INDIRECT_COOLING_WATER_FLOW 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 04 Furnace Auxiliary

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 159.5778 |
| 표준편차 | 4.8624 |
| Q1 (25%) | 155.6078 |
| 중앙값 | 156.4331 |
| Q3 (75%) | 165.0600 |
| IQR | 9.4522 |
| 하한 경계 | 141.4295 |
| 상한 경계 | 179.2382 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 155.35 | 0.00% |
| 2025-06 | 5,758 | 166.42 | 0.00% |
| 2025-07 | 2,880 | 161.65 | 0.00% |
| 2025-08 | 4,316 | 156.12 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_07_daily_outlier_count.png)

**종합 분석 차트**

![INDIRECT_COOLING_WATER_FLOW 종합 분석 차트](./04_Furnace_Auxiliary/INDIRECT_COOLING_WATER_FLOW_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 155.3463 |
| 중앙값 | 155.4160 |
| IQR | 1.0189 |
| 이상치 수 | 4 |
| 이상치율 | 0.06% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 4건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_COOLING_WATER_FLOW_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 166.4200 |
| 중앙값 | 166.2618 |
| IQR | 1.9702 |
| 이상치 수 | 2 |
| 이상치율 | 0.03% |

**주요 이상치 발생 날짜**:

- 1. 2025-06-12: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_COOLING_WATER_FLOW_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 161.6460 |
| 중앙값 | 161.5820 |
| IQR | 0.8084 |
| 이상치 수 | 31 |
| 이상치율 | 1.08% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 27건
- 2. 2025-07-05: 4건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_COOLING_WATER_FLOW_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 156.1188 |
| 중앙값 | 156.1524 |
| IQR | 0.6975 |
| 이상치 수 | 26 |
| 이상치율 | 0.60% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 24건
- 2. 2025-08-11: 2건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_COOLING_WATER_FLOW_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_COOLING_WATER_FLOW_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_COOLING_WATER_FLOW_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_COOLING_WATER_FLOW_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_COOLING_WATER_FLOW_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_COOLING_WATER_FLOW_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_COOLING_WATER_FLOW_00_summary.png)

---

#### INDIRECT_WATER_MAIN_TEMPERATURE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 04 Furnace Auxiliary

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✗ | 가열로 독립 시스템 |
| coiling_transient | ✗ | 가열로 독립 시스템 |

**데이터**: 원본 20,144 → 필터 후 20,144 (0.0% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 20,144 |
| 평균 | 31.9078 |
| 표준편차 | 2.3866 |
| Q1 (25%) | 30.2000 |
| 중앙값 | 31.3991 |
| Q3 (75%) | 34.3000 |
| IQR | 4.1000 |
| 하한 경계 | 24.0500 |
| 상한 경계 | 40.4500 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,190 | 30.03 | 0.00% |
| 2025-06 | 5,758 | 31.16 | 0.00% |
| 2025-07 | 2,880 | 34.63 | 0.00% |
| 2025-08 | 4,316 | 34.22 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./04_Furnace_Auxiliary/INDIRECT_WATER_MAIN_TEMPERATURE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/INDIRECT_WATER_MAIN_TEMPERATURE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/INDIRECT_WATER_MAIN_TEMPERATURE_07_daily_outlier_count.png)

**종합 분석 차트**

![INDIRECT_WATER_MAIN_TEMPERATURE 종합 분석 차트](./04_Furnace_Auxiliary/INDIRECT_WATER_MAIN_TEMPERATURE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,190 |
| 평균 | 30.0275 |
| 중앙값 | 29.7872 |
| IQR | 2.2852 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-05/INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,758 |
| 평균 | 31.1605 |
| 중앙값 | 31.1000 |
| IQR | 1.0923 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-06/INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,880 |
| 평균 | 34.6258 |
| 중앙값 | 35.5000 |
| IQR | 2.0000 |
| 이상치 수 | 339 |
| 이상치율 | 11.77% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-04: 339건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-07/INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,316 |
| 평균 | 34.2237 |
| 중앙값 | 35.0000 |
| IQR | 1.3958 |
| 이상치 수 | 622 |
| 이상치율 | 14.41% |

**주요 이상치 발생 날짜**:

- 1. 2025-08-08: 622건

**1. 시계열 (Time Series)**

![시계열 차트](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_WATER_MAIN_TEMPERATURE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_WATER_MAIN_TEMPERATURE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_WATER_MAIN_TEMPERATURE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_WATER_MAIN_TEMPERATURE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_WATER_MAIN_TEMPERATURE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_WATER_MAIN_TEMPERATURE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./04_Furnace_Auxiliary/monthly/2025-08/INDIRECT_WATER_MAIN_TEMPERATURE_00_summary.png)

---

#### STAND_1_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 37.7406 |
| 표준편차 | 24.5828 |
| Q1 (25%) | 0.8546 |
| 중앙값 | 48.6804 |
| Q3 (75%) | 56.6010 |
| IQR | 55.7464 |
| 하한 경계 | -82.7650 |
| 상한 경계 | 140.2206 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 37.35 | 0.00% |
| 2025-06 | 5,678 | 39.25 | 0.00% |
| 2025-07 | 2,773 | 33.06 | 0.00% |
| 2025-08 | 4,201 | 39.45 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_1_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_1_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_1_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_1_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_1_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 37.3516 |
| 중앙값 | 46.1438 |
| IQR | 18.7052 |
| 이상치 수 | 1,549 |
| 이상치율 | 21.78% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 847건
- 2. 2025-05-18: 702건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_1_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 39.2468 |
| 중앙값 | 50.1441 |
| IQR | 56.5490 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_1_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 33.0618 |
| 중앙값 | 51.5787 |
| IQR | 58.3653 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_1_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 39.4515 |
| 중앙값 | 54.3318 |
| IQR | 61.0594 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_1_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_1_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_1_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_1_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_1_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_1_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_1_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_2_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 41.3246 |
| 표준편차 | 26.6314 |
| Q1 (25%) | 1.1876 |
| 중앙값 | 54.9477 |
| Q3 (75%) | 60.9327 |
| IQR | 59.7451 |
| 하한 경계 | -88.4300 |
| 상한 경계 | 150.5503 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 43.15 | 0.00% |
| 2025-06 | 5,678 | 41.82 | 0.00% |
| 2025-07 | 2,773 | 33.19 | 0.00% |
| 2025-08 | 4,201 | 42.94 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_2_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_2_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_2_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_2_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_2_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 43.1455 |
| 중앙값 | 54.7901 |
| IQR | 23.4573 |
| 이상치 수 | 827 |
| 이상치율 | 11.63% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 476건
- 2. 2025-05-18: 351건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_2_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 41.8234 |
| 중앙값 | 54.2863 |
| IQR | 59.4604 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_2_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 33.1873 |
| 중앙값 | 52.0979 |
| IQR | 58.8004 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_2_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 42.9394 |
| 중앙값 | 60.0680 |
| IQR | 66.0724 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_2_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_2_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_2_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_2_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_2_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_2_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_2_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_3_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 37.6073 |
| 표준편차 | 24.3010 |
| Q1 (25%) | 0.9221 |
| 중앙값 | 49.2846 |
| Q3 (75%) | 55.4027 |
| IQR | 54.4806 |
| 하한 경계 | -80.7989 |
| 상한 경계 | 137.1236 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 38.82 | 0.00% |
| 2025-06 | 5,678 | 37.16 | 0.00% |
| 2025-07 | 2,773 | 31.87 | 0.00% |
| 2025-08 | 4,201 | 39.96 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_3_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_3_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_3_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_3_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_3_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 38.8155 |
| 중앙값 | 48.7178 |
| IQR | 20.9065 |
| 이상치 수 | 834 |
| 이상치율 | 11.73% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 480건
- 2. 2025-05-18: 354건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_3_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 37.1558 |
| 중앙값 | 47.5539 |
| IQR | 52.8002 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_3_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 31.8729 |
| 중앙값 | 50.3322 |
| IQR | 56.2563 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_3_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 39.9578 |
| 중앙값 | 55.3871 |
| IQR | 61.8407 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_3_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_4_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 36.2970 |
| 표준편차 | 23.5997 |
| Q1 (25%) | 1.2607 |
| 중앙값 | 45.5979 |
| Q3 (75%) | 54.7156 |
| IQR | 53.4549 |
| 하한 경계 | -78.9217 |
| 상한 경계 | 134.8979 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 37.34 | 0.00% |
| 2025-06 | 5,678 | 35.79 | 0.00% |
| 2025-07 | 2,773 | 30.46 | 0.00% |
| 2025-08 | 4,201 | 39.07 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_4_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_4_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_4_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_4_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_4_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 37.3352 |
| 중앙값 | 44.7936 |
| IQR | 20.7061 |
| 이상치 수 | 833 |
| 이상치율 | 11.71% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 479건
- 2. 2025-05-18: 354건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_4_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 35.7907 |
| 중앙값 | 42.9199 |
| IQR | 52.8567 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_4_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 30.4647 |
| 중앙값 | 47.6422 |
| IQR | 53.8287 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_4_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 39.0738 |
| 중앙값 | 53.5141 |
| IQR | 60.2157 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_4_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_4_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_4_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_4_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_4_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_4_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_4_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_5_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 33.8678 |
| 표준편차 | 21.7370 |
| Q1 (25%) | 0.9031 |
| 중앙값 | 44.8874 |
| Q3 (75%) | 50.2191 |
| IQR | 49.3160 |
| 하한 경계 | -73.0709 |
| 상한 경계 | 124.1931 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 34.67 | 0.00% |
| 2025-06 | 5,678 | 34.26 | 0.00% |
| 2025-07 | 2,773 | 29.97 | 0.00% |
| 2025-08 | 4,201 | 34.54 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_5_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_5_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_5_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_5_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_5_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 34.6743 |
| 중앙값 | 43.4761 |
| IQR | 19.1899 |
| 이상치 수 | 16 |
| 이상치율 | 0.23% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 10건
- 2. 2025-05-18: 6건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_5_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 34.2632 |
| 중앙값 | 45.4417 |
| IQR | 48.0521 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_5_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 29.9652 |
| 중앙값 | 48.1608 |
| IQR | 52.8333 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_5_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 34.5444 |
| 중앙값 | 49.0769 |
| IQR | 52.8806 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_5_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_5_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_5_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_5_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_5_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_5_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_5_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_6_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 31.4173 |
| 표준편차 | 19.9183 |
| Q1 (25%) | 1.5473 |
| 중앙값 | 41.2365 |
| Q3 (75%) | 46.5477 |
| IQR | 45.0004 |
| 하한 경계 | -65.9532 |
| 상한 경계 | 114.0483 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 32.55 | 0.00% |
| 2025-06 | 5,678 | 32.72 | 0.00% |
| 2025-07 | 2,773 | 26.92 | 0.00% |
| 2025-08 | 4,201 | 30.71 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_6_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_6_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_6_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_6_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_6_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 32.5493 |
| 중앙값 | 40.2445 |
| IQR | 16.4987 |
| 이상치 수 | 1,511 |
| 이상치율 | 21.25% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 839건
- 2. 2025-05-18: 672건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_6_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 32.7174 |
| 중앙값 | 42.6303 |
| IQR | 45.3810 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_6_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 26.9185 |
| 중앙값 | 42.6711 |
| IQR | 47.2446 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_6_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 30.7137 |
| 중앙값 | 42.7213 |
| IQR | 46.3738 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_6_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_6_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_6_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_6_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_6_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_6_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_6_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_7_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 29.2994 |
| 표준편차 | 18.5644 |
| Q1 (25%) | 1.9622 |
| 중앙값 | 38.5012 |
| Q3 (75%) | 42.3561 |
| IQR | 40.3939 |
| 하한 경계 | -58.6287 |
| 상한 경계 | 102.9469 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 30.28 | 0.00% |
| 2025-06 | 5,678 | 28.72 | 0.00% |
| 2025-07 | 2,773 | 23.92 | 0.00% |
| 2025-08 | 4,201 | 31.97 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_7_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_7_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_7_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_7_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_7_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 30.2843 |
| 중앙값 | 37.9168 |
| IQR | 14.6520 |
| 이상치 수 | 1,523 |
| 이상치율 | 21.42% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 839건
- 2. 2025-05-18: 684건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_7_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 28.7169 |
| 중앙값 | 37.4356 |
| IQR | 39.1326 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_7_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 23.9212 |
| 중앙값 | 38.6555 |
| IQR | 41.8055 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_7_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 31.9694 |
| 중앙값 | 45.0118 |
| IQR | 47.6311 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_7_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_7_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_7_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_7_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_7_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_7_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_7_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_8_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 28.2175 |
| 표준편차 | 17.6518 |
| Q1 (25%) | 2.6357 |
| 중앙값 | 35.7660 |
| Q3 (75%) | 42.0151 |
| IQR | 39.3793 |
| 하한 경계 | -56.4333 |
| 상한 경계 | 101.0841 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 29.34 | 0.00% |
| 2025-06 | 5,678 | 29.67 | 0.00% |
| 2025-07 | 2,773 | 25.55 | 0.00% |
| 2025-08 | 4,201 | 26.12 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_8_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_8_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_8_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_8_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_8_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 29.3354 |
| 중앙값 | 34.8138 |
| IQR | 13.7837 |
| 이상치 수 | 1,540 |
| 이상치율 | 21.66% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 847건
- 2. 2025-05-18: 693건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_8_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 29.6705 |
| 중앙값 | 36.9635 |
| IQR | 40.0922 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_8_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 25.5472 |
| 중앙값 | 40.9461 |
| IQR | 44.4380 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_8_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 26.1238 |
| 중앙값 | 36.1157 |
| IQR | 37.4857 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_8_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_8_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_8_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_8_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_8_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_8_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_8_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_9_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 40.2076 |
| 표준편차 | 25.9683 |
| Q1 (25%) | 0.9368 |
| 중앙값 | 53.5893 |
| Q3 (75%) | 59.0553 |
| IQR | 58.1185 |
| 하한 경계 | -86.2410 |
| 상한 경계 | 146.2331 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 42.39 | 0.00% |
| 2025-06 | 5,678 | 42.69 | 0.00% |
| 2025-07 | 2,773 | 36.57 | 0.00% |
| 2025-08 | 4,201 | 35.55 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_9_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_9_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_9_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_9_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_9_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 42.3938 |
| 중앙값 | 54.1401 |
| IQR | 19.8121 |
| 이상치 수 | 1,575 |
| 이상치율 | 22.15% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 861건
- 2. 2025-05-18: 714건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_9_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 42.6919 |
| 중앙값 | 55.8328 |
| IQR | 62.2148 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_9_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 36.5662 |
| 중앙값 | 60.3194 |
| IQR | 64.6434 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_9_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 35.5527 |
| 중앙값 | 51.4315 |
| IQR | 53.9621 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_9_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_9_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_9_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_9_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_9_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_9_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_9_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_10_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 41.8380 |
| 표준편차 | 26.5130 |
| Q1 (25%) | 2.4363 |
| 중앙값 | 55.8070 |
| Q3 (75%) | 62.1921 |
| IQR | 59.7558 |
| 하한 경계 | -87.1974 |
| 상한 경계 | 151.8258 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 43.56 | 0.00% |
| 2025-06 | 5,678 | 43.55 | 0.00% |
| 2025-07 | 2,773 | 36.37 | 0.00% |
| 2025-08 | 4,201 | 40.21 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_10_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_10_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_10_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_10_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_10_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 43.5600 |
| 중앙값 | 54.2012 |
| IQR | 21.8790 |
| 이상치 수 | 1,558 |
| 이상치율 | 21.91% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 856건
- 2. 2025-05-18: 702건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_10_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 43.5548 |
| 중앙값 | 57.6234 |
| IQR | 60.7889 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_10_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 36.3668 |
| 중앙값 | 60.5397 |
| IQR | 63.8428 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_10_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 40.2144 |
| 중앙값 | 57.8705 |
| IQR | 59.5813 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_10_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_10_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_10_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_10_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_10_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_10_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_10_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_11_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 34.3684 |
| 표준편차 | 22.1848 |
| Q1 (25%) | 1.3451 |
| 중앙값 | 44.6448 |
| Q3 (75%) | 52.0061 |
| IQR | 50.6610 |
| 하한 경계 | -74.6464 |
| 상한 경계 | 127.9976 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 36.48 | 0.00% |
| 2025-06 | 5,678 | 34.45 | 0.00% |
| 2025-07 | 2,773 | 26.59 | 0.00% |
| 2025-08 | 4,201 | 35.82 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_11_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_11_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_11_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_11_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_11_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 36.4821 |
| 중앙값 | 44.1840 |
| IQR | 19.0498 |
| 이상치 수 | 1,552 |
| 이상치율 | 21.83% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 852건
- 2. 2025-05-18: 700건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_11_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 34.4484 |
| 중앙값 | 45.6894 |
| IQR | 49.1028 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_11_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 26.5866 |
| 중앙값 | 41.3680 |
| IQR | 45.1324 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_11_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 35.8191 |
| 중앙값 | 50.1551 |
| IQR | 55.0921 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_11_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_11_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_11_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_11_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_11_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_11_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_11_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_12_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 40.2712 |
| 표준편차 | 25.7750 |
| Q1 (25%) | 3.1140 |
| 중앙값 | 50.2371 |
| Q3 (75%) | 61.0631 |
| IQR | 57.9491 |
| 하한 경계 | -83.8097 |
| 상한 경계 | 147.9868 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 41.22 | 0.00% |
| 2025-06 | 5,678 | 41.28 | 0.00% |
| 2025-07 | 2,773 | 34.13 | 0.00% |
| 2025-08 | 4,201 | 41.36 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_12_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_12_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_12_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_12_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_12_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 41.2212 |
| 중앙값 | 48.4856 |
| IQR | 23.5342 |
| 이상치 수 | 847 |
| 이상치율 | 11.91% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 480건
- 2. 2025-05-18: 367건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_12_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 41.2794 |
| 중앙값 | 49.7351 |
| IQR | 60.0443 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_12_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 34.1274 |
| 중앙값 | 53.7566 |
| IQR | 57.9904 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_12_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 41.3559 |
| 중앙값 | 57.6836 |
| IQR | 61.7217 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_12_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_12_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_12_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_12_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_12_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_12_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_12_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_13_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 36.8598 |
| 표준편차 | 23.3698 |
| Q1 (25%) | 2.5386 |
| 중앙값 | 48.8154 |
| Q3 (75%) | 53.2177 |
| IQR | 50.6791 |
| 하한 경계 | -73.4800 |
| 상한 경계 | 129.2363 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 37.71 | 0.00% |
| 2025-06 | 5,678 | 36.40 | 0.00% |
| 2025-07 | 2,773 | 33.93 | 0.00% |
| 2025-08 | 4,201 | 37.98 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_13_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_13_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_13_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_13_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_13_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 37.7088 |
| 중앙값 | 48.2362 |
| IQR | 18.7840 |
| 이상치 수 | 1,532 |
| 이상치율 | 21.54% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 841건
- 2. 2025-05-18: 691건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_13_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 36.3951 |
| 중앙값 | 48.7165 |
| IQR | 49.3332 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_13_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 33.9318 |
| 중앙값 | 52.1773 |
| IQR | 61.4577 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_13_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 37.9834 |
| 중앙값 | 54.8209 |
| IQR | 54.7132 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_13_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_13_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_13_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_13_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_13_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_13_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_13_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_14_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 25.4255 |
| 표준편차 | 15.4851 |
| Q1 (25%) | 3.5080 |
| 중앙값 | 34.1986 |
| Q3 (75%) | 36.4655 |
| IQR | 32.9574 |
| 하한 경계 | -45.9281 |
| 상한 경계 | 85.9016 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 26.70 | 0.00% |
| 2025-06 | 5,678 | 25.61 | 0.00% |
| 2025-07 | 2,773 | 21.95 | 0.00% |
| 2025-08 | 4,201 | 25.32 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/STAND_14_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/STAND_14_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/STAND_14_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_14_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/STAND_14_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 26.6960 |
| 중앙값 | 33.9876 |
| IQR | 12.2228 |
| 이상치 수 | 1,541 |
| 이상치율 | 21.67% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 841건
- 2. 2025-05-18: 700건

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/STAND_14_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 25.6136 |
| 중앙값 | 34.0971 |
| IQR | 32.1814 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/STAND_14_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 21.9494 |
| 중앙값 | 35.2862 |
| IQR | 38.2186 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/STAND_14_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 25.3153 |
| 중앙값 | 36.4039 |
| IQR | 34.4233 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/STAND_14_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/STAND_14_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/STAND_14_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/STAND_14_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/STAND_14_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/STAND_14_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/STAND_14_ACTUAL_TORQUE_00_summary.png)

---

#### FINISHING_BLOCK_MASTER_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 35.1370 |
| 표준편차 | 22.6971 |
| Q1 (25%) | 4.1351 |
| 중앙값 | 40.5009 |
| Q3 (75%) | 56.7418 |
| IQR | 52.6067 |
| 하한 경계 | -74.7749 |
| 상한 경계 | 135.6519 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 36.47 | 0.00% |
| 2025-06 | 5,678 | 35.48 | 0.00% |
| 2025-07 | 2,773 | 28.43 | 0.00% |
| 2025-08 | 4,201 | 36.84 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_MASTER_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 36.4694 |
| 중앙값 | 39.2206 |
| IQR | 24.4621 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 35.4832 |
| 중앙값 | 40.5532 |
| IQR | 52.8693 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 28.4317 |
| 중앙값 | 41.7042 |
| IQR | 40.1867 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 36.8399 |
| 중앙값 | 49.3062 |
| IQR | 54.0047 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_MASTER_ACTUAL_TORQUE_00_summary.png)

---

#### FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 05 Stand Torque

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 토크 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 토크 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 35.1146 |
| 표준편차 | 22.6842 |
| Q1 (25%) | 4.1232 |
| 중앙값 | 40.4829 |
| Q3 (75%) | 56.7069 |
| IQR | 52.5837 |
| 하한 경계 | -74.7524 |
| 상한 경계 | 135.5824 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 36.45 | 0.00% |
| 2025-06 | 5,678 | 35.46 | 0.00% |
| 2025-07 | 2,773 | 28.41 | 0.00% |
| 2025-08 | 4,201 | 36.82 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./05_Stand_Torque/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE 종합 분석 차트](./05_Stand_Torque/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 36.4454 |
| 중앙값 | 39.2082 |
| IQR | 24.4815 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./05_Stand_Torque/monthly/2025-05/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 35.4599 |
| 중앙값 | 40.5302 |
| IQR | 52.8796 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./05_Stand_Torque/monthly/2025-06/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 28.4112 |
| 중앙값 | 41.6810 |
| IQR | 40.1781 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./05_Stand_Torque/monthly/2025-07/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 36.8202 |
| 중앙값 | 49.2912 |
| IQR | 54.0046 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./05_Stand_Torque/monthly/2025-08/FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_00_summary.png)

---

#### STAND_1_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6983 |
| 표준편차 | 0.4310 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.75 | 0.00% |
| 2025-06 | 5,678 | 0.72 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_1_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_1_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_1_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_1_LOAD 종합 분석 차트](./07_Stand_Load/STAND_1_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7454 |
| 중앙값 | 1.0000 |
| IQR | 0.2265 |
| 이상치 수 | 1,621 |
| 이상치율 | 22.80% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 871건
- 2. 2025-05-18: 750건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_1_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7155 |
| 중앙값 | 1.0000 |
| IQR | 0.7117 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_1_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5901 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_1_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6667 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_1_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_1_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_1_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_1_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_1_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_1_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_1_LOAD_00_summary.png)

---

#### STAND_2_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6979 |
| 표준편차 | 0.4305 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_2_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_2_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_2_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_2_LOAD 종합 분석 차트](./07_Stand_Load/STAND_2_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7448 |
| 중앙값 | 1.0000 |
| IQR | 0.2785 |
| 이상치 수 | 1,566 |
| 이상치율 | 22.02% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 849건
- 2. 2025-05-18: 717건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_2_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7150 |
| 중앙값 | 1.0000 |
| IQR | 0.7062 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_2_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5899 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_2_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6666 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_2_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_2_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_2_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_2_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_2_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_2_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_2_LOAD_00_summary.png)

---

#### STAND_3_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6974 |
| 표준편차 | 0.4299 |
| Q1 (25%) | 0.0167 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.9833 |
| 하한 경계 | -1.4583 |
| 상한 경계 | 2.4750 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_3_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_3_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_3_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_3_LOAD 종합 분석 차트](./07_Stand_Load/STAND_3_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7441 |
| 중앙값 | 1.0000 |
| IQR | 0.3041 |
| 이상치 수 | 1,502 |
| 이상치율 | 21.12% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 821건
- 2. 2025-05-18: 681건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_3_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7145 |
| 중앙값 | 1.0000 |
| IQR | 0.6997 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_3_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5897 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_3_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6664 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_3_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_3_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_3_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_3_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_3_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_3_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_3_LOAD_00_summary.png)

---

#### STAND_4_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6971 |
| 표준편차 | 0.4297 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_4_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_4_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_4_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_4_LOAD 종합 분석 차트](./07_Stand_Load/STAND_4_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7436 |
| 중앙값 | 1.0000 |
| IQR | 0.3036 |
| 이상치 수 | 1,474 |
| 이상치율 | 20.73% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 811건
- 2. 2025-05-18: 663건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_4_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7142 |
| 중앙값 | 1.0000 |
| IQR | 0.7181 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_4_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5896 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_4_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6661 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_4_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_4_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_4_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_4_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_4_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_4_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_4_LOAD_00_summary.png)

---

#### STAND_5_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6967 |
| 표준편차 | 0.4298 |
| Q1 (25%) | 0.0003 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 0.9997 |
| 하한 경계 | -1.4992 |
| 상한 경계 | 2.4995 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_5_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_5_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_5_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_5_LOAD 종합 분석 차트](./07_Stand_Load/STAND_5_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7429 |
| 중앙값 | 1.0000 |
| IQR | 0.3082 |
| 이상치 수 | 1,493 |
| 이상치율 | 21.00% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 815건
- 2. 2025-05-18: 678건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_5_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7139 |
| 중앙값 | 1.0000 |
| IQR | 0.7301 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_5_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5894 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_5_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6658 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_5_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_5_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_5_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_5_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_5_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_5_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_5_LOAD_00_summary.png)

---

#### STAND_6_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6967 |
| 표준편차 | 0.4299 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_6_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_6_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_6_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_6_LOAD 종합 분석 차트](./07_Stand_Load/STAND_6_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7429 |
| 중앙값 | 1.0000 |
| IQR | 0.2950 |
| 이상치 수 | 1,526 |
| 이상치율 | 21.46% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 827건
- 2. 2025-05-18: 699건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_6_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7139 |
| 중앙값 | 1.0000 |
| IQR | 0.7051 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_6_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5894 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_6_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6658 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_6_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_6_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_6_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_6_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_6_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_6_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_6_LOAD_00_summary.png)

---

#### STAND_7_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6966 |
| 표준편차 | 0.4299 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_7_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_7_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_7_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_7_LOAD 종합 분석 차트](./07_Stand_Load/STAND_7_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7428 |
| 중앙값 | 1.0000 |
| IQR | 0.2992 |
| 이상치 수 | 1,532 |
| 이상치율 | 21.54% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 827건
- 2. 2025-05-18: 705건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_7_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7139 |
| 중앙값 | 1.0000 |
| IQR | 0.7045 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_7_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5894 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_7_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6659 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_7_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_7_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_7_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_7_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_7_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_7_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_7_LOAD_00_summary.png)

---

#### STAND_8_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6968 |
| 표준편차 | 0.4300 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.67 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_8_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_8_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_8_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_8_LOAD 종합 분석 차트](./07_Stand_Load/STAND_8_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7430 |
| 중앙값 | 1.0000 |
| IQR | 0.2752 |
| 이상치 수 | 1,564 |
| 이상치율 | 21.99% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 841건
- 2. 2025-05-18: 723건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_8_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7142 |
| 중앙값 | 1.0000 |
| IQR | 0.7104 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_8_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5894 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_8_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6659 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_8_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_8_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_8_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_8_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_8_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_8_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_8_LOAD_00_summary.png)

---

#### STAND_9_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6949 |
| 표준편차 | 0.4308 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_9_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_9_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_9_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_9_LOAD 종합 분석 차트](./07_Stand_Load/STAND_9_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7409 |
| 중앙값 | 1.0000 |
| IQR | 0.2567 |
| 이상치 수 | 1,592 |
| 이상치율 | 22.39% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 863건
- 2. 2025-05-18: 729건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_9_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7123 |
| 중앙값 | 1.0000 |
| IQR | 0.7336 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_9_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5875 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_9_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6646 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_9_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_9_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_9_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_9_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_9_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_9_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_9_LOAD_00_summary.png)

---

#### STAND_10_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6952 |
| 표준편차 | 0.4310 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_10_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_10_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_10_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_10_LOAD 종합 분석 차트](./07_Stand_Load/STAND_10_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7413 |
| 중앙값 | 1.0000 |
| IQR | 0.2422 |
| 이상치 수 | 1,613 |
| 이상치율 | 22.68% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 869건
- 2. 2025-05-18: 744건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_10_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7126 |
| 중앙값 | 1.0000 |
| IQR | 0.7374 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_10_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5875 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_10_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6648 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_10_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_10_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_10_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_10_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_10_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_10_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_10_LOAD_00_summary.png)

---

#### STAND_11_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6949 |
| 표준편차 | 0.4310 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_11_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_11_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_11_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_11_LOAD 종합 분석 차트](./07_Stand_Load/STAND_11_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7408 |
| 중앙값 | 1.0000 |
| IQR | 0.2410 |
| 이상치 수 | 1,610 |
| 이상치율 | 22.64% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 869건
- 2. 2025-05-18: 741건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_11_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7123 |
| 중앙값 | 1.0000 |
| IQR | 0.7263 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_11_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5873 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_11_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6646 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_11_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_11_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_11_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_11_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_11_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_11_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_11_LOAD_00_summary.png)

---

#### STAND_12_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6950 |
| 표준편차 | 0.4311 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_12_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_12_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_12_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_12_LOAD 종합 분석 차트](./07_Stand_Load/STAND_12_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7410 |
| 중앙값 | 1.0000 |
| IQR | 0.2428 |
| 이상치 수 | 1,604 |
| 이상치율 | 22.56% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 863건
- 2. 2025-05-18: 741건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_12_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7125 |
| 중앙값 | 1.0000 |
| IQR | 0.7263 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_12_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5873 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_12_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6647 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_12_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_12_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_12_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_12_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_12_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_12_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_12_LOAD_00_summary.png)

---

#### STAND_13_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6950 |
| 표준편차 | 0.4311 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_13_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_13_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_13_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_13_LOAD 종합 분석 차트](./07_Stand_Load/STAND_13_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7410 |
| 중앙값 | 1.0000 |
| IQR | 0.2428 |
| 이상치 수 | 1,604 |
| 이상치율 | 22.56% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 863건
- 2. 2025-05-18: 741건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_13_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7125 |
| 중앙값 | 1.0000 |
| IQR | 0.7263 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_13_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5873 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_13_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6647 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_13_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_13_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_13_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_13_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_13_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_13_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_13_LOAD_00_summary.png)

---

#### STAND_14_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6948 |
| 표준편차 | 0.4311 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/STAND_14_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/STAND_14_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/STAND_14_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![STAND_14_LOAD 종합 분석 차트](./07_Stand_Load/STAND_14_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7408 |
| 중앙값 | 1.0000 |
| IQR | 0.2401 |
| 이상치 수 | 1,615 |
| 이상치율 | 22.71% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 871건
- 2. 2025-05-18: 744건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/STAND_14_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7122 |
| 중앙값 | 1.0000 |
| IQR | 0.7225 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/STAND_14_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5872 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/STAND_14_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6645 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/STAND_14_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/STAND_14_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/STAND_14_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/STAND_14_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/STAND_14_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/STAND_14_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/STAND_14_LOAD_00_summary.png)

---

#### FINISHING_BLOCK_LOAD 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 07 Stand Load

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 부하 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 부하 급변 구간 제외 |
| coiling_transient | ✗ | 권취 전 공정으로 가감속 영향 없음 |

**데이터**: 원본 20,144 → 필터 후 19,763 (1.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 19,763 |
| 평균 | 0.6946 |
| 표준편차 | 0.4311 |
| Q1 (25%) | 0.0000 |
| 중앙값 | 1.0000 |
| Q3 (75%) | 1.0000 |
| IQR | 1.0000 |
| 하한 경계 | -1.5000 |
| 상한 경계 | 2.5000 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 7,111 | 0.74 | 0.00% |
| 2025-06 | 5,678 | 0.71 | 0.00% |
| 2025-07 | 2,773 | 0.59 | 0.00% |
| 2025-08 | 4,201 | 0.66 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./07_Stand_Load/FINISHING_BLOCK_LOAD_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/FINISHING_BLOCK_LOAD_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/FINISHING_BLOCK_LOAD_07_daily_outlier_count.png)

**종합 분석 차트**

![FINISHING_BLOCK_LOAD 종합 분석 차트](./07_Stand_Load/FINISHING_BLOCK_LOAD_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 7,111 |
| 평균 | 0.7405 |
| 중앙값 | 1.0000 |
| IQR | 0.2622 |
| 이상치 수 | 1,593 |
| 이상치율 | 22.40% |

**주요 이상치 발생 날짜**:

- 1. 2025-05-17: 861건
- 2. 2025-05-18: 732건

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-05/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-05/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-05/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-05/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-05/FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-05/FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./07_Stand_Load/monthly/2025-05/FINISHING_BLOCK_LOAD_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 5,678 |
| 평균 | 0.7120 |
| 중앙값 | 1.0000 |
| IQR | 0.7152 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-06/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-06/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-06/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-06/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-06/FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-06/FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./07_Stand_Load/monthly/2025-06/FINISHING_BLOCK_LOAD_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,773 |
| 평균 | 0.5869 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-07/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-07/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-07/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-07/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-07/FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-07/FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./07_Stand_Load/monthly/2025-07/FINISHING_BLOCK_LOAD_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,201 |
| 평균 | 0.6645 |
| 중앙값 | 1.0000 |
| IQR | 1.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./07_Stand_Load/monthly/2025-08/FINISHING_BLOCK_LOAD_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./07_Stand_Load/monthly/2025-08/FINISHING_BLOCK_LOAD_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./07_Stand_Load/monthly/2025-08/FINISHING_BLOCK_LOAD_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./07_Stand_Load/monthly/2025-08/FINISHING_BLOCK_LOAD_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./07_Stand_Load/monthly/2025-08/FINISHING_BLOCK_LOAD_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./07_Stand_Load/monthly/2025-08/FINISHING_BLOCK_LOAD_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./07_Stand_Load/monthly/2025-08/FINISHING_BLOCK_LOAD_00_summary.png)

---

#### PINCHROLL_3_ACTUAL_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 08 Pinchroll

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 18.4019 |
| 표준편차 | 13.1718 |
| Q1 (25%) | 4.1264 |
| 중앙값 | 24.9901 |
| Q3 (75%) | 28.8634 |
| IQR | 24.7370 |
| 하한 경계 | -32.9791 |
| 상한 경계 | 65.9688 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 6,158 | 14.06 | 0.00% |
| 2025-06 | 4,896 | 20.13 | 0.00% |
| 2025-07 | 2,011 | 24.54 | 0.00% |
| 2025-08 | 3,273 | 20.23 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_3_ACTUAL_TORQUE 종합 분석 차트](./08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,158 |
| 평균 | 14.0558 |
| 중앙값 | 5.2306 |
| IQR | 20.9793 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 20.1254 |
| 중앙값 | 29.9883 |
| IQR | 27.8925 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 24.5367 |
| 중앙값 | 27.5116 |
| IQR | 21.1726 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 20.2313 |
| 중앙값 | 24.9924 |
| IQR | 22.7225 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_ACTUAL_TORQUE_00_summary.png)

---

#### PINCHROLL_3_REFERENCE_TORQUE 🟢

**위험도**: [NORMAL] | **이상치율**: 0.00% | **이상치 방향**: 양방향

**카테고리**: 08 Pinchroll

| 필터 | 적용 | 이유 |
|------|:----:|------|
| run_only | ✓ | 가동 상태에서만 측정이 유효함 |
| special_ops | ✓ | 정상 운전 조건에서 분석 |
| roll_change | ✓ | 롤교환 시 속도/토크 급변 구간 제외 |
| coiling_transient | ✓ | 권취 시작/종료 가감속 구간 제외 |

**데이터**: 원본 20,144 → 필터 후 16,338 (18.9% 제외)

| 통계 지표 | 값 |
|-----------|-------|
| 분석 레코드 | 16,338 |
| 평균 | 60.2180 |
| 표준편차 | 33.8219 |
| Q1 (25%) | 27.5400 |
| 중앙값 | 40.0000 |
| Q3 (75%) | 99.5506 |
| IQR | 72.0106 |
| 하한 경계 | -80.4759 |
| 상한 경계 | 207.5666 |
| 이상치 수 | 0 (0.00%) |

**월별 이상치 추이**:

| 월 | 레코드 수 | 평균 | 이상치율 |
|-----|-----------|------|----------|
| 2025-05 | 6,158 | 65.63 | 0.00% |
| 2025-06 | 4,896 | 62.26 | 0.00% |
| 2025-07 | 2,011 | 48.03 | 0.00% |
| 2025-08 | 3,273 | 54.47 | 0.00% |


##### 차트 분석

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 월별 이상치율 (Monthly Outlier Rate)**

![월별 이상치율](./08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_05_monthly_outlier_rate.png)

**6. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_06_hourly_pattern.png)

**7. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_07_daily_outlier_count.png)

**종합 분석 차트**

![PINCHROLL_3_REFERENCE_TORQUE 종합 분석 차트](./08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_analysis.png)


---

##### 월별 상세 분석

**2025-05**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 6,158 |
| 평균 | 65.6302 |
| 중앙값 | 98.0700 |
| IQR | 75.0000 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-05 종합 분석 차트](./08_Pinchroll/monthly/2025-05/PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

**2025-06**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 4,896 |
| 평균 | 62.2586 |
| 중앙값 | 40.0000 |
| IQR | 69.5900 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-06 종합 분석 차트](./08_Pinchroll/monthly/2025-06/PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

**2025-07**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 2,011 |
| 평균 | 48.0265 |
| 중앙값 | 35.0000 |
| IQR | 20.8808 |
| 이상치 수 | 432 |
| 이상치율 | 21.48% |

**주요 이상치 발생 날짜**:

- 1. 2025-07-05: 256건
- 2. 2025-07-04: 176건

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-07 종합 분석 차트](./08_Pinchroll/monthly/2025-07/PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

**2025-08**

**통계 요약**:

| 지표 | 값 |
|------|-------|
| 분석 레코드 | 3,273 |
| 평균 | 54.4733 |
| 중앙값 | 40.0000 |
| IQR | 73.8542 |
| 이상치 수 | 0 |
| 이상치율 | 0.00% |

**1. 시계열 (Time Series)**

![시계열 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_REFERENCE_TORQUE_01_timeseries.png)

**2. 분포 히스토그램 (Distribution Histogram)**

![히스토그램](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_REFERENCE_TORQUE_02_histogram.png)

**3. 박스플롯 (Box Plot)**

![박스플롯](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_REFERENCE_TORQUE_03_boxplot.png)

**4. 일별 평균 추이 (Daily Average Trend)**

![일별 평균 추이](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_REFERENCE_TORQUE_04_daily_avg_trend.png)

**5. 시간별 패턴 (Hourly Pattern)**

![시간별 패턴](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_REFERENCE_TORQUE_05_hourly_pattern.png)

**6. 일별 이상치 수 (Daily Outlier Count)**

![일별 이상치 수](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_REFERENCE_TORQUE_06_daily_outlier_count.png)

**월별 종합 차트**

![2025-08 종합 분석 차트](./08_Pinchroll/monthly/2025-08/PINCHROLL_3_REFERENCE_TORQUE_00_summary.png)

---


## 분석 메타데이터

| 항목 | 값 |
|------|-----|
| 분석 스크립트 | steel_grade_iqr_analysis_v2.py |
| 분석 기간 | 2025-03-01 ~ 2025-08-31 |
| 강종 | D4 |
| 생성일시 | 2026-02-02 21:20:35 |
| 총 분석 태그 | 79개 |

---

*본 보고서는 자동 생성되었습니다.*

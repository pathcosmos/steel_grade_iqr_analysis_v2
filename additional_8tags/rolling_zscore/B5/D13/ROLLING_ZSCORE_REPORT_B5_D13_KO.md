# 강종 [B5 | Size: D13] Rolling Z-Score 동적 이상치 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: B5  
**사이즈**: D13
**생성일시**: 2026-02-23 15:59:21

---

## 분석 개요

### 분석 방법론

**Rolling Z-Score (롤링 Z-점수)**

시간 창(window) 기반 동적 이상치 탐지 방법입니다.

$$Z_{rolling}(t) = \frac{x(t) - \mu_{window}(t)}{\sigma_{window}(t)}$$

| 파라미터 | 값 | 설명 |
|----------|-----|------|
| Window | 24h | 이동 평균/표준편차 윈도우 |
| Z Threshold | ±3.0σ | 이상치 판정 임계값 |
| Severe | ±4.0σ | 심각 이상치 임계값 |

### 장점

- **비정상 시계열 적합**: 평균/분산 시변하는 데이터에 효과적
- **점진적 기준선 추적**: 장기 드리프트에 강건
- **Local Context 기반**: 해당 시점 주변 패턴 기준

### 분석 결과 요약

| 구분 | 태그 수 | 비율 |
|------|---------|------|
| **총 분석 태그** | 23개 | 100% |
| 🔴 높은 이상치율 (≥10%) | 0개 | 0.0% |
| 🟠 중간 이상치율 (3~10%) | 1개 | 4.3% |
| 🟢 낮은 이상치율 (<3%) | 20개 | 87.0% |
| 🟡 불안정 기준선 | 2개 | 8.7% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 이상치율 | 0.52% |
| 평균 기준선 안정성 | 0.811 |

---

## 상위 문제 태그 (이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 심각 이상치 | 안정성 | 상태 |
|------|------|----------|----------|-------------|--------|------|
| 1 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.11% | 2 | 0.979 | 🟠 |
| 2 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 2.92% | 145 | 0.592 | 🟢 |
| 3 | PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 2.21% | 102 | 0.157 | 🟡 |
| 4 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.02% | 0 | 0.983 | 🟢 |
| 5 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 0.27% | 0 | 0.910 | 🟢 |
| 6 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 0.24% | 0 | 0.909 | 🟢 |
| 7 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 0.24% | 0 | 0.919 | 🟢 |
| 8 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 0.22% | 0 | 0.918 | 🟢 |
| 9 | PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.14% | 1 | 0.939 | 🟢 |
| 10 | PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 0.13% | 8 | 0.612 | 🟢 |
| 11 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 0.11% | 4 | 0.603 | 🟢 |
| 12 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 0.11% | 0 | 0.929 | 🟢 |
| 13 | PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.08% | 4 | 0.000 | 🟡 |
| 14 | PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.06% | 3 | 0.685 | 🟢 |
| 15 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 0.05% | 0 | 0.915 | 🟢 |

---

## 불안정 기준선 태그

기준선 안정성(Stability Index)이 0.5 미만인 태그입니다.
이 태그들은 Rolling Z-Score 방법보다 다른 방법이 더 적합할 수 있습니다.

| 태그 | 카테고리 | 안정성 | 이상치율 |
|------|----------|--------|----------|
| PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 0.08% |
| PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 0.157 | 2.21% |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 이상치율: 0.59%
- 평균 안정성: 0.742

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PINCHROLL_2_ACTUAL_SPEED | 0.11% | 4 | 0.603 | 20.85 |
| PINCHROLL_3_ACTUAL_SPEED | 0.02% | 1 | 0.695 | 21.03 |
| PINCHROLL_4_ACTUAL_SPEED | 0.05% | 0 | 0.915 | 3.08 |
| PINCHROLL_2_ACTUAL_TORQUE | 0.11% | 0 | 0.929 | 3.16 |
| PINCHROLL_3_ACTUAL_TORQUE | 0.27% | 0 | 0.910 | 3.38 |
| PINCHROLL_4_ACTUAL_TORQUE | 0.24% | 0 | 0.909 | 3.37 |
| PINCHROLL_2_REFERENCE_TORQUE | 0.13% | 8 | 0.612 | 40.24 |
| PINCHROLL_3_REFERENCE_TORQUE | 0.24% | 0 | 0.919 | 3.37 |
| PINCHROLL_4_REFERENCE_TORQUE | 0.22% | 0 | 0.918 | 3.37 |
| PINCHROLL_3_REFERENCE_SPEED | 2.21% | 102 | 0.157 | 24.71 |
| PINCHROLL_4_REFERENCE_SPEED | 2.92% | 145 | 0.592 | 21.55 |

#### Z-Score 차트

**PINCHROLL_4_REFERENCE_SPEED** (이상치율: 2.92%, 안정성: 0.592)

![PINCHROLL_4_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_4_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_3_REFERENCE_SPEED** (이상치율: 2.21%, 안정성: 0.157)

![PINCHROLL_3_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_3_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_3_ACTUAL_TORQUE** (이상치율: 0.27%, 안정성: 0.910)

![PINCHROLL_3_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_rolling_zscore.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 이상치율: 0.45%
- 평균 안정성: 0.875

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PR6L1_ACT_TORQUE | 0.00% | 0 | 0.985 | 2.89 |
| PR6L2_ACT_TORQUE | 0.14% | 1 | 0.939 | 12.31 |
| PR7L1_ACT_TORQUE | 0.00% | 0 | 0.994 | 1.51 |
| PR7L2_ACT_TORQUE | 0.00% | 0 | 0.990 | 1.51 |
| PR8L1_ACT_TORQUE | 0.00% | 0 | 0.986 | 1.77 |
| PR9L1_ACT_TORQUE | 0.00% | 0 | 0.996 | 1.67 |
| PR6L1_ACT_SPD_MS | 0.00% | 0 | 0.980 | 2.58 |
| PR6L2_ACT_SPD_MS | 0.08% | 4 | 0.000 | 22.20 |
| PR7L1_ACT_SPD_MS | 0.00% | 0 | 0.990 | 1.73 |
| PR7L2_ACT_SPD_MS | 0.06% | 3 | 0.685 | 19.93 |
| PR8L1_ACT_SPD_MS | 2.02% | 0 | 0.983 | 3.45 |
| PR9L1_ACT_SPD_MS | 3.11% | 2 | 0.979 | 4.47 |

#### Z-Score 차트

**PR9L1_ACT_SPD_MS** (이상치율: 3.11%, 안정성: 0.979)

![PR9L1_ACT_SPD_MS](09_PR_Detailed/PR9L1_ACT_SPD_MS_rolling_zscore.png)

**PR8L1_ACT_SPD_MS** (이상치율: 2.02%, 안정성: 0.983)

![PR8L1_ACT_SPD_MS](09_PR_Detailed/PR8L1_ACT_SPD_MS_rolling_zscore.png)

**PR6L2_ACT_TORQUE** (이상치율: 0.14%, 안정성: 0.939)

![PR6L2_ACT_TORQUE](09_PR_Detailed/PR6L2_ACT_TORQUE_rolling_zscore.png)



---

## 해석 가이드

### Rolling Z-Score 해석

1. **이상치율 (Outlier Rate)**
   - |Z| > 3.0σ 비율
   - 높을수록 해당 시점 주변 패턴에서 벗어난 데이터 많음
   - 정상 분포 가정 시 약 0.3% 예상

2. **기준선 안정성 (Baseline Stability)**
   - Rolling std의 시간적 일관성
   - 1에 가까울수록 안정적
   - 0.5 미만: 비정상 시계열, 다른 방법 권장

3. **심각 이상치 (Severe Outliers)**
   - |Z| > 4.0σ
   - 극단적인 이상값
   - 즉각적인 점검 필요

### 상태 분류

| 상태 | 기준 | 해석 |
|------|------|------|
| 🔴 높음 | ≥10% | 빈번한 이상치, 점검 필요 |
| 🟠 중간 | 3~10% | 일부 이상치, 모니터링 |
| 🟢 낮음 | <3% | 정상 범위 |
| 🟡 불안정 | Stability < 0.5 | 기준선 변동 심함 |

### Standard IQR vs Rolling Z-Score

| 방법 | 장점 | 단점 |
|------|------|------|
| Standard IQR | 간단, 전체 분포 기반 | 시변 데이터에 부적합 |
| Rolling Z-Score | 시변 데이터 적합 | 윈도우 크기 설정 필요 |

**권장**: 기준선 안정성 ≥ 0.5인 태그에 효과적

---

## 메타데이터

| 항목 | 값 |
|------|-----|
| 분석 스크립트 | steel_grade_rolling_zscore_analysis.py |
| 분석 기간 | 2025-03-01 ~ 2025-08-31 |
| 강종 | B5 |
| 윈도우 크기 | 24시간 |
| Z 임계값 | ±3.0σ |
| 생성일시 | 2026-02-23 15:59:21 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

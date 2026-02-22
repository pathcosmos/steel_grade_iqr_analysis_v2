# 강종 [D4 | Size: D13] Rolling Z-Score 동적 이상치 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D4  
**사이즈**: D13
**생성일시**: 2026-02-23 01:41:25

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
| 🟠 중간 이상치율 (3~10%) | 3개 | 13.0% |
| 🟢 낮은 이상치율 (<3%) | 10개 | 43.5% |
| 🟡 불안정 기준선 | 10개 | 43.5% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 이상치율 | 1.54% |
| 평균 기준선 안정성 | 0.476 |

---

## 상위 문제 태그 (이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 심각 이상치 | 안정성 | 상태 |
|------|------|----------|----------|-------------|--------|------|
| 1 | PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 4.48% | 32 | 0.140 | 🟠 |
| 2 | PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 4.48% | 31 | 0.203 | 🟠 |
| 3 | PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 4.24% | 29 | 0.346 | 🟠 |
| 4 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.99% | 36 | 0.000 | 🟡 |
| 5 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.76% | 36 | 0.000 | 🟡 |
| 6 | PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.66% | 44 | 0.000 | 🟡 |
| 7 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 2.32% | 7 | 0.156 | 🟡 |
| 8 | PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.19% | 37 | 0.000 | 🟡 |
| 9 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 1.94% | 48 | 0.119 | 🟡 |
| 10 | PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 1.36% | 48 | 0.183 | 🟡 |
| 11 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 1.10% | 2 | 0.341 | 🟡 |
| 12 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 0.96% | 2 | 0.483 | 🟡 |
| 13 | PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 0.74% | 12 | 0.284 | 🟡 |
| 14 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 0.54% | 5 | 0.839 | 🟢 |
| 15 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 0.51% | 5 | 0.812 | 🟢 |

---

## 불안정 기준선 태그

기준선 안정성(Stability Index)이 0.5 미만인 태그입니다.
이 태그들은 Rolling Z-Score 방법보다 다른 방법이 더 적합할 수 있습니다.

| 태그 | 카테고리 | 안정성 | 이상치율 |
|------|----------|--------|----------|
| PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 2.66% |
| PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 2.19% |
| PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 2.76% |
| PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 2.99% |
| PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 0.119 | 1.94% |
| PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.140 | 4.48% |
| PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 0.156 | 2.32% |
| PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 0.183 | 1.36% |
| PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.203 | 4.48% |
| PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 0.284 | 0.74% |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 이상치율: 0.91%
- 평균 안정성: 0.589

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PINCHROLL_2_ACTUAL_SPEED | 0.96% | 2 | 0.483 | 8.64 |
| PINCHROLL_3_ACTUAL_SPEED | 1.10% | 2 | 0.341 | 26.23 |
| PINCHROLL_4_ACTUAL_SPEED | 2.32% | 7 | 0.156 | 24.86 |
| PINCHROLL_2_ACTUAL_TORQUE | 0.54% | 5 | 0.839 | 7.06 |
| PINCHROLL_3_ACTUAL_TORQUE | 0.51% | 5 | 0.812 | 7.07 |
| PINCHROLL_4_ACTUAL_TORQUE | 0.51% | 5 | 0.841 | 7.04 |
| PINCHROLL_2_REFERENCE_TORQUE | 0.00% | 0 | 1.000 | 0.00 |
| PINCHROLL_3_REFERENCE_TORQUE | 0.40% | 0 | 0.849 | 3.87 |
| PINCHROLL_4_REFERENCE_TORQUE | 0.40% | 0 | 0.856 | 3.84 |
| PINCHROLL_3_REFERENCE_SPEED | 1.36% | 48 | 0.183 | 27.01 |
| PINCHROLL_4_REFERENCE_SPEED | 1.94% | 48 | 0.119 | 26.36 |

#### Z-Score 차트

**PINCHROLL_4_ACTUAL_SPEED** (이상치율: 2.32%, 안정성: 0.156)

![PINCHROLL_4_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_rolling_zscore.png)

**PINCHROLL_4_REFERENCE_SPEED** (이상치율: 1.94%, 안정성: 0.119)

![PINCHROLL_4_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_4_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_3_REFERENCE_SPEED** (이상치율: 1.36%, 안정성: 0.183)

![PINCHROLL_3_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_3_REFERENCE_SPEED_rolling_zscore.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 이상치율: 2.12%
- 평균 안정성: 0.373

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PR6L1_ACT_TORQUE | 0.74% | 12 | 0.284 | 9.83 |
| PR6L2_ACT_TORQUE | 4.24% | 29 | 0.346 | 11.62 |
| PR7L1_ACT_TORQUE | 0.34% | 6 | 0.849 | 6.96 |
| PR7L2_ACT_TORQUE | 0.00% | 0 | 0.969 | 1.46 |
| PR8L1_ACT_TORQUE | 0.30% | 5 | 0.844 | 6.98 |
| PR9L1_ACT_TORQUE | 0.27% | 5 | 0.835 | 7.05 |
| PR6L1_ACT_SPD_MS | 2.66% | 44 | 0.000 | 21.26 |
| PR6L2_ACT_SPD_MS | 4.48% | 32 | 0.140 | 22.62 |
| PR7L1_ACT_SPD_MS | 2.19% | 37 | 0.000 | 20.10 |
| PR7L2_ACT_SPD_MS | 4.48% | 31 | 0.203 | 20.37 |
| PR8L1_ACT_SPD_MS | 2.76% | 36 | 0.000 | 17.66 |
| PR9L1_ACT_SPD_MS | 2.99% | 36 | 0.000 | 17.26 |

#### Z-Score 차트

**PR6L2_ACT_SPD_MS** (이상치율: 4.48%, 안정성: 0.140)

![PR6L2_ACT_SPD_MS](09_PR_Detailed/PR6L2_ACT_SPD_MS_rolling_zscore.png)

**PR7L2_ACT_SPD_MS** (이상치율: 4.48%, 안정성: 0.203)

![PR7L2_ACT_SPD_MS](09_PR_Detailed/PR7L2_ACT_SPD_MS_rolling_zscore.png)

**PR6L2_ACT_TORQUE** (이상치율: 4.24%, 안정성: 0.346)

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
| 강종 | D4 |
| 윈도우 크기 | 24시간 |
| Z 임계값 | ±3.0σ |
| 생성일시 | 2026-02-23 01:41:25 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

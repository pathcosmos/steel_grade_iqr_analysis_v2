# 강종 [D4 | Size: D10] Rolling Z-Score 동적 이상치 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D4  
**사이즈**: D10
**생성일시**: 2026-02-23 15:59:37

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
| 🟠 중간 이상치율 (3~10%) | 12개 | 52.2% |
| 🟢 낮은 이상치율 (<3%) | 6개 | 26.1% |
| 🟡 불안정 기준선 | 5개 | 21.7% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 이상치율 | 2.87% |
| 평균 기준선 안정성 | 0.483 |

---

## 상위 문제 태그 (이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 심각 이상치 | 안정성 | 상태 |
|------|------|----------|----------|-------------|--------|------|
| 1 | PR9L1_ACT_TORQUE | PR 상세 (토크+속도) | 6.32% | 89 | 0.678 | 🟠 |
| 2 | PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 5.28% | 93 | 0.838 | 🟠 |
| 3 | PR8L1_ACT_TORQUE | PR 상세 (토크+속도) | 5.12% | 74 | 0.754 | 🟠 |
| 4 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 4.63% | 349 | 0.000 | 🟠 |
| 5 | PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 4.15% | 360 | 0.000 | 🟠 |
| 6 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 3.52% | 232 | 0.000 | 🟠 |
| 7 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.48% | 50 | 0.821 | 🟠 |
| 8 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.44% | 50 | 0.822 | 🟠 |
| 9 | PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.24% | 44 | 0.845 | 🟠 |
| 10 | PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.24% | 44 | 0.845 | 🟠 |
| 11 | PR7L1_ACT_TORQUE | PR 상세 (토크+속도) | 3.20% | 41 | 0.855 | 🟠 |
| 12 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 3.16% | 221 | 0.000 | 🟠 |
| 13 | PR7L2_ACT_TORQUE | PR 상세 (토크+속도) | 2.91% | 157 | 0.000 | 🟡 |
| 14 | PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 2.85% | 157 | 0.000 | 🟡 |
| 15 | PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 2.85% | 159 | 0.000 | 🟡 |

---

## 불안정 기준선 태그

기준선 안정성(Stability Index)이 0.5 미만인 태그입니다.
이 태그들은 Rolling Z-Score 방법보다 다른 방법이 더 적합할 수 있습니다.

| 태그 | 카테고리 | 안정성 | 이상치율 |
|------|----------|--------|----------|
| PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 0.000 | 3.16% |
| PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 0.000 | 3.52% |
| PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 0.000 | 4.15% |
| PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 0.000 | 4.63% |
| PR7L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.000 | 2.91% |
| PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 2.85% |
| PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 2.85% |
| PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.036 | 2.82% |
| PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 0.401 | 0.06% |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 이상치율: 1.93%
- 평균 안정성: 0.419

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PINCHROLL_2_ACTUAL_SPEED | 1.00% | 58 | 0.526 | 23.96 |
| PINCHROLL_3_ACTUAL_SPEED | 3.16% | 221 | 0.000 | 45.49 |
| PINCHROLL_4_ACTUAL_SPEED | 3.52% | 232 | 0.000 | 27.46 |
| PINCHROLL_2_ACTUAL_TORQUE | 0.85% | 42 | 0.800 | 8.24 |
| PINCHROLL_3_ACTUAL_TORQUE | 1.13% | 61 | 0.675 | 18.02 |
| PINCHROLL_4_ACTUAL_TORQUE | 0.87% | 44 | 0.716 | 10.36 |
| PINCHROLL_2_REFERENCE_TORQUE | 0.06% | 6 | 0.401 | 34.34 |
| PINCHROLL_3_REFERENCE_TORQUE | 0.99% | 57 | 0.689 | 25.79 |
| PINCHROLL_4_REFERENCE_TORQUE | 0.88% | 44 | 0.806 | 10.33 |
| PINCHROLL_3_REFERENCE_SPEED | 4.15% | 360 | 0.000 | 49.07 |
| PINCHROLL_4_REFERENCE_SPEED | 4.63% | 349 | 0.000 | 39.84 |

#### Z-Score 차트

**PINCHROLL_4_REFERENCE_SPEED** (이상치율: 4.63%, 안정성: 0.000)

![PINCHROLL_4_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_4_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_3_REFERENCE_SPEED** (이상치율: 4.15%, 안정성: 0.000)

![PINCHROLL_3_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_3_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_4_ACTUAL_SPEED** (이상치율: 3.52%, 안정성: 0.000)

![PINCHROLL_4_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_rolling_zscore.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 이상치율: 3.73%
- 평균 안정성: 0.541

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PR6L1_ACT_TORQUE | 5.28% | 93 | 0.838 | 26.78 |
| PR6L2_ACT_TORQUE | 2.82% | 156 | 0.036 | 22.73 |
| PR7L1_ACT_TORQUE | 3.20% | 41 | 0.855 | 26.78 |
| PR7L2_ACT_TORQUE | 2.91% | 157 | 0.000 | 24.31 |
| PR8L1_ACT_TORQUE | 5.12% | 74 | 0.754 | 26.78 |
| PR9L1_ACT_TORQUE | 6.32% | 89 | 0.678 | 26.78 |
| PR6L1_ACT_SPD_MS | 3.24% | 44 | 0.845 | 26.78 |
| PR6L2_ACT_SPD_MS | 2.85% | 157 | 0.000 | 49.99 |
| PR7L1_ACT_SPD_MS | 3.24% | 44 | 0.845 | 26.78 |
| PR7L2_ACT_SPD_MS | 2.85% | 159 | 0.000 | 49.94 |
| PR8L1_ACT_SPD_MS | 3.44% | 50 | 0.822 | 26.78 |
| PR9L1_ACT_SPD_MS | 3.48% | 50 | 0.821 | 26.78 |

#### Z-Score 차트

**PR9L1_ACT_TORQUE** (이상치율: 6.32%, 안정성: 0.678)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_rolling_zscore.png)

**PR6L1_ACT_TORQUE** (이상치율: 5.28%, 안정성: 0.838)

![PR6L1_ACT_TORQUE](09_PR_Detailed/PR6L1_ACT_TORQUE_rolling_zscore.png)

**PR8L1_ACT_TORQUE** (이상치율: 5.12%, 안정성: 0.754)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_rolling_zscore.png)



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
| 생성일시 | 2026-02-23 15:59:37 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

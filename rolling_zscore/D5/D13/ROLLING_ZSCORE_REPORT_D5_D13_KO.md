# 강종 [D5 | Size: D13] Rolling Z-Score 동적 이상치 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: D5  
**사이즈**: D13
**생성일시**: 2026-02-23 01:41:50

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
| 🟠 중간 이상치율 (3~10%) | 0개 | 0.0% |
| 🟢 낮은 이상치율 (<3%) | 15개 | 65.2% |
| 🟡 불안정 기준선 | 8개 | 34.8% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 이상치율 | 0.77% |
| 평균 기준선 안정성 | 0.564 |

---

## 상위 문제 태그 (이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 심각 이상치 | 안정성 | 상태 |
|------|------|----------|----------|-------------|--------|------|
| 1 | PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 2.00% | 64 | 0.397 | 🟡 |
| 2 | PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 1.82% | 27 | 0.000 | 🟡 |
| 3 | PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 1.23% | 18 | 0.000 | 🟡 |
| 4 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 1.11% | 8 | 0.065 | 🟡 |
| 5 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 0.91% | 67 | 0.521 | 🟢 |
| 6 | PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 0.91% | 70 | 0.529 | 🟢 |
| 7 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.85% | 11 | 0.134 | 🟡 |
| 8 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 0.84% | 59 | 0.552 | 🟢 |
| 9 | PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 0.80% | 70 | 0.708 | 🟢 |
| 10 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 0.72% | 44 | 0.781 | 🟢 |
| 11 | PR7L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.71% | 23 | 0.790 | 🟢 |
| 12 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 0.68% | 40 | 0.770 | 🟢 |
| 13 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 0.63% | 54 | 0.420 | 🟡 |
| 14 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 0.62% | 34 | 0.787 | 🟢 |
| 15 | PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.62% | 10 | 0.794 | 🟢 |

---

## 불안정 기준선 태그

기준선 안정성(Stability Index)이 0.5 미만인 태그입니다.
이 태그들은 Rolling Z-Score 방법보다 다른 방법이 더 적합할 수 있습니다.

| 태그 | 카테고리 | 안정성 | 이상치율 |
|------|----------|--------|----------|
| PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 0.000 | 1.23% |
| PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 1.82% |
| PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.065 | 1.11% |
| PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.134 | 0.85% |
| PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.397 | 2.00% |
| PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 0.411 | 0.60% |
| PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 0.420 | 0.63% |
| PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.485 | 0.46% |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 이상치율: 0.63%
- 평균 안정성: 0.661

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PINCHROLL_2_ACTUAL_SPEED | 0.84% | 59 | 0.552 | 10.65 |
| PINCHROLL_3_ACTUAL_SPEED | 0.91% | 67 | 0.521 | 12.79 |
| PINCHROLL_4_ACTUAL_SPEED | 0.60% | 51 | 0.411 | 11.35 |
| PINCHROLL_2_ACTUAL_TORQUE | 0.72% | 44 | 0.781 | 12.87 |
| PINCHROLL_3_ACTUAL_TORQUE | 0.68% | 40 | 0.770 | 13.03 |
| PINCHROLL_4_ACTUAL_TORQUE | 0.62% | 34 | 0.787 | 11.31 |
| PINCHROLL_2_REFERENCE_TORQUE | 0.80% | 70 | 0.708 | 23.49 |
| PINCHROLL_3_REFERENCE_TORQUE | 0.10% | 5 | 0.893 | 8.18 |
| PINCHROLL_4_REFERENCE_TORQUE | 0.10% | 5 | 0.903 | 6.73 |
| PINCHROLL_3_REFERENCE_SPEED | 0.91% | 70 | 0.529 | 12.97 |
| PINCHROLL_4_REFERENCE_SPEED | 0.63% | 54 | 0.420 | 11.35 |

#### Z-Score 차트

**PINCHROLL_3_ACTUAL_SPEED** (이상치율: 0.91%, 안정성: 0.521)

![PINCHROLL_3_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_rolling_zscore.png)

**PINCHROLL_3_REFERENCE_SPEED** (이상치율: 0.91%, 안정성: 0.529)

![PINCHROLL_3_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_3_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_2_ACTUAL_SPEED** (이상치율: 0.84%, 안정성: 0.552)

![PINCHROLL_2_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_2_ACTUAL_SPEED_rolling_zscore.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 이상치율: 0.91%
- 평균 안정성: 0.474

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PR6L1_ACT_TORQUE | 1.23% | 18 | 0.000 | 13.55 |
| PR6L2_ACT_TORQUE | 2.00% | 64 | 0.397 | 21.82 |
| PR7L1_ACT_TORQUE | 0.59% | 10 | 0.800 | 7.28 |
| PR7L2_ACT_TORQUE | 0.71% | 23 | 0.790 | 11.23 |
| PR8L1_ACT_TORQUE | 0.53% | 10 | 0.810 | 7.34 |
| PR9L1_ACT_TORQUE | 0.59% | 11 | 0.803 | 7.45 |
| PR6L1_ACT_SPD_MS | 1.82% | 27 | 0.000 | 19.86 |
| PR6L2_ACT_SPD_MS | 0.46% | 23 | 0.485 | 18.79 |
| PR7L1_ACT_SPD_MS | 0.62% | 10 | 0.794 | 18.57 |
| PR7L2_ACT_SPD_MS | 0.38% | 22 | 0.611 | 17.83 |
| PR8L1_ACT_SPD_MS | 1.11% | 8 | 0.065 | 19.85 |
| PR9L1_ACT_SPD_MS | 0.85% | 11 | 0.134 | 19.30 |

#### Z-Score 차트

**PR6L2_ACT_TORQUE** (이상치율: 2.00%, 안정성: 0.397)

![PR6L2_ACT_TORQUE](09_PR_Detailed/PR6L2_ACT_TORQUE_rolling_zscore.png)

**PR6L1_ACT_SPD_MS** (이상치율: 1.82%, 안정성: 0.000)

![PR6L1_ACT_SPD_MS](09_PR_Detailed/PR6L1_ACT_SPD_MS_rolling_zscore.png)

**PR6L1_ACT_TORQUE** (이상치율: 1.23%, 안정성: 0.000)

![PR6L1_ACT_TORQUE](09_PR_Detailed/PR6L1_ACT_TORQUE_rolling_zscore.png)



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
| 강종 | D5 |
| 윈도우 크기 | 24시간 |
| Z 임계값 | ±3.0σ |
| 생성일시 | 2026-02-23 01:41:50 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

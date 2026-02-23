# 강종 [N5 | Size: D10] Rolling Z-Score 동적 이상치 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5  
**사이즈**: D10
**생성일시**: 2026-02-23 16:00:56

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
| 🟢 낮은 이상치율 (<3%) | 9개 | 39.1% |
| 🟡 불안정 기준선 | 2개 | 8.7% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 이상치율 | 2.86% |
| 평균 기준선 안정성 | 0.382 |

---

## 상위 문제 태그 (이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 심각 이상치 | 안정성 | 상태 |
|------|------|----------|----------|-------------|--------|------|
| 1 | PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 7.46% | 460 | 0.080 | 🟠 |
| 2 | PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 7.44% | 459 | 0.081 | 🟠 |
| 3 | PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 5.91% | 341 | 0.000 | 🟠 |
| 4 | PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 4.88% | 162 | 0.000 | 🟠 |
| 5 | PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 4.83% | 163 | 0.000 | 🟠 |
| 6 | PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 4.76% | 474 | 0.107 | 🟠 |
| 7 | PR7L2_ACT_TORQUE | PR 상세 (토크+속도) | 4.62% | 316 | 0.165 | 🟠 |
| 8 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 4.53% | 424 | 0.135 | 🟠 |
| 9 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 4.47% | 444 | 0.060 | 🟠 |
| 10 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 4.11% | 394 | 0.086 | 🟠 |
| 11 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.67% | 137 | 0.229 | 🟠 |
| 12 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.65% | 137 | 0.248 | 🟠 |
| 13 | PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 1.44% | 48 | 0.000 | 🟡 |
| 14 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 1.40% | 153 | 0.661 | 🟢 |
| 15 | PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 1.20% | 179 | 0.505 | 🟢 |

---

## 불안정 기준선 태그

기준선 안정성(Stability Index)이 0.5 미만인 태그입니다.
이 태그들은 Rolling Z-Score 방법보다 다른 방법이 더 적합할 수 있습니다.

| 태그 | 카테고리 | 안정성 | 이상치율 |
|------|----------|--------|----------|
| PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 0.000 | 1.44% |
| PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.000 | 5.91% |
| PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 4.83% |
| PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 4.88% |
| PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 0.060 | 4.47% |
| PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.080 | 7.46% |
| PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.081 | 7.44% |
| PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 0.086 | 4.11% |
| PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 0.107 | 4.76% |
| PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 0.135 | 4.53% |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 이상치율: 1.87%
- 평균 안정성: 0.537

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PINCHROLL_2_ACTUAL_SPEED | 1.40% | 153 | 0.661 | 18.22 |
| PINCHROLL_3_ACTUAL_SPEED | 4.53% | 424 | 0.135 | 26.47 |
| PINCHROLL_4_ACTUAL_SPEED | 4.11% | 394 | 0.086 | 35.04 |
| PINCHROLL_2_ACTUAL_TORQUE | 0.02% | 0 | 0.882 | 3.74 |
| PINCHROLL_3_ACTUAL_TORQUE | 0.02% | 0 | 0.885 | 3.78 |
| PINCHROLL_4_ACTUAL_TORQUE | 0.03% | 0 | 0.889 | 3.76 |
| PINCHROLL_2_REFERENCE_TORQUE | 1.20% | 179 | 0.505 | 33.15 |
| PINCHROLL_3_REFERENCE_TORQUE | 0.03% | 0 | 0.839 | 3.78 |
| PINCHROLL_4_REFERENCE_TORQUE | 0.03% | 0 | 0.860 | 3.76 |
| PINCHROLL_3_REFERENCE_SPEED | 4.76% | 474 | 0.107 | 33.32 |
| PINCHROLL_4_REFERENCE_SPEED | 4.47% | 444 | 0.060 | 39.83 |

#### Z-Score 차트

**PINCHROLL_3_REFERENCE_SPEED** (이상치율: 4.76%, 안정성: 0.107)

![PINCHROLL_3_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_3_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_3_ACTUAL_SPEED** (이상치율: 4.53%, 안정성: 0.135)

![PINCHROLL_3_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_rolling_zscore.png)

**PINCHROLL_4_REFERENCE_SPEED** (이상치율: 4.47%, 안정성: 0.060)

![PINCHROLL_4_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_4_REFERENCE_SPEED_rolling_zscore.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 이상치율: 3.76%
- 평균 안정성: 0.239

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PR6L1_ACT_TORQUE | 1.44% | 48 | 0.000 | 15.43 |
| PR6L2_ACT_TORQUE | 5.91% | 341 | 0.000 | 14.93 |
| PR7L1_ACT_TORQUE | 1.13% | 24 | 0.287 | 9.58 |
| PR7L2_ACT_TORQUE | 4.62% | 316 | 0.165 | 11.11 |
| PR8L1_ACT_TORQUE | 0.00% | 0 | 0.866 | 2.86 |
| PR9L1_ACT_TORQUE | 0.07% | 0 | 0.917 | 3.23 |
| PR6L1_ACT_SPD_MS | 4.83% | 163 | 0.000 | 44.80 |
| PR6L2_ACT_SPD_MS | 7.46% | 460 | 0.080 | 26.53 |
| PR7L1_ACT_SPD_MS | 4.88% | 162 | 0.000 | 39.68 |
| PR7L2_ACT_SPD_MS | 7.44% | 459 | 0.081 | 26.52 |
| PR8L1_ACT_SPD_MS | 3.67% | 137 | 0.229 | 20.90 |
| PR9L1_ACT_SPD_MS | 3.65% | 137 | 0.248 | 18.54 |

#### Z-Score 차트

**PR6L2_ACT_SPD_MS** (이상치율: 7.46%, 안정성: 0.080)

![PR6L2_ACT_SPD_MS](09_PR_Detailed/PR6L2_ACT_SPD_MS_rolling_zscore.png)

**PR7L2_ACT_SPD_MS** (이상치율: 7.44%, 안정성: 0.081)

![PR7L2_ACT_SPD_MS](09_PR_Detailed/PR7L2_ACT_SPD_MS_rolling_zscore.png)

**PR6L2_ACT_TORQUE** (이상치율: 5.91%, 안정성: 0.000)

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
| 강종 | N5 |
| 윈도우 크기 | 24시간 |
| Z 임계값 | ±3.0σ |
| 생성일시 | 2026-02-23 16:00:56 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

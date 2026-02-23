# 강종 [N5 | Size: D16] Rolling Z-Score 동적 이상치 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5  
**사이즈**: D16
**생성일시**: 2026-02-23 16:00:45

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
| 🟢 낮은 이상치율 (<3%) | 12개 | 52.2% |
| 🟡 불안정 기준선 | 11개 | 47.8% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 이상치율 | 0.91% |
| 평균 기준선 안정성 | 0.415 |

---

## 상위 문제 태그 (이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 심각 이상치 | 안정성 | 상태 |
|------|------|----------|----------|-------------|--------|------|
| 1 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.14% | 191 | 0.606 | 🟢 |
| 2 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.12% | 209 | 0.558 | 🟢 |
| 3 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 1.93% | 335 | 0.000 | 🟡 |
| 4 | PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 1.89% | 108 | 0.000 | 🟡 |
| 5 | PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 1.75% | 109 | 0.000 | 🟡 |
| 6 | PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 1.69% | 316 | 0.000 | 🟡 |
| 7 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 1.20% | 160 | 0.000 | 🟡 |
| 8 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 1.17% | 162 | 0.000 | 🟡 |
| 9 | PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 1.03% | 48 | 0.000 | 🟡 |
| 10 | PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.87% | 129 | 0.046 | 🟡 |
| 11 | PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.86% | 129 | 0.037 | 🟡 |
| 12 | PR7L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.79% | 13 | 0.663 | 🟢 |
| 13 | PR7L1_ACT_TORQUE | PR 상세 (토크+속도) | 0.57% | 27 | 0.822 | 🟢 |
| 14 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 0.47% | 5 | 0.836 | 🟢 |
| 15 | PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 0.45% | 49 | 0.718 | 🟢 |

---

## 불안정 기준선 태그

기준선 안정성(Stability Index)이 0.5 미만인 태그입니다.
이 태그들은 Rolling Z-Score 방법보다 다른 방법이 더 적합할 수 있습니다.

| 태그 | 카테고리 | 안정성 | 이상치율 |
|------|----------|--------|----------|
| PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 0.000 | 1.17% |
| PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 0.000 | 1.20% |
| PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 0.000 | 1.69% |
| PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 0.000 | 1.93% |
| PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.000 | 1.03% |
| PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 1.75% |
| PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 1.89% |
| PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.037 | 0.86% |
| PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.046 | 0.87% |
| PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 0.224 | 0.11% |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 이상치율: 0.74%
- 평균 안정성: 0.394

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PINCHROLL_2_ACTUAL_SPEED | 0.40% | 23 | 0.575 | 25.85 |
| PINCHROLL_3_ACTUAL_SPEED | 1.17% | 162 | 0.000 | 34.00 |
| PINCHROLL_4_ACTUAL_SPEED | 1.20% | 160 | 0.000 | 36.47 |
| PINCHROLL_2_ACTUAL_TORQUE | 0.24% | 13 | 0.860 | 11.74 |
| PINCHROLL_3_ACTUAL_TORQUE | 0.31% | 12 | 0.503 | 11.81 |
| PINCHROLL_4_ACTUAL_TORQUE | 0.19% | 11 | 0.499 | 11.81 |
| PINCHROLL_2_REFERENCE_TORQUE | 0.11% | 34 | 0.224 | 61.43 |
| PINCHROLL_3_REFERENCE_TORQUE | 0.47% | 5 | 0.836 | 4.59 |
| PINCHROLL_4_REFERENCE_TORQUE | 0.42% | 5 | 0.842 | 4.59 |
| PINCHROLL_3_REFERENCE_SPEED | 1.69% | 316 | 0.000 | 65.11 |
| PINCHROLL_4_REFERENCE_SPEED | 1.93% | 335 | 0.000 | 65.06 |

#### Z-Score 차트

**PINCHROLL_4_REFERENCE_SPEED** (이상치율: 1.93%, 안정성: 0.000)

![PINCHROLL_4_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_4_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_3_REFERENCE_SPEED** (이상치율: 1.69%, 안정성: 0.000)

![PINCHROLL_3_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_3_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_4_ACTUAL_SPEED** (이상치율: 1.20%, 안정성: 0.000)

![PINCHROLL_4_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_rolling_zscore.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 이상치율: 1.06%
- 평균 안정성: 0.433

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PR6L1_ACT_TORQUE | 0.45% | 49 | 0.718 | 8.14 |
| PR6L2_ACT_TORQUE | 1.03% | 48 | 0.000 | 16.94 |
| PR7L1_ACT_TORQUE | 0.57% | 27 | 0.822 | 10.58 |
| PR7L2_ACT_TORQUE | 0.79% | 13 | 0.663 | 7.84 |
| PR8L1_ACT_TORQUE | 0.16% | 18 | 0.879 | 12.03 |
| PR9L1_ACT_TORQUE | 0.14% | 11 | 0.870 | 11.65 |
| PR6L1_ACT_SPD_MS | 0.86% | 129 | 0.037 | 61.45 |
| PR6L2_ACT_SPD_MS | 1.75% | 109 | 0.000 | 43.58 |
| PR7L1_ACT_SPD_MS | 0.87% | 129 | 0.046 | 61.09 |
| PR7L2_ACT_SPD_MS | 1.89% | 108 | 0.000 | 43.46 |
| PR8L1_ACT_SPD_MS | 2.12% | 209 | 0.558 | 15.92 |
| PR9L1_ACT_SPD_MS | 2.14% | 191 | 0.606 | 14.50 |

#### Z-Score 차트

**PR9L1_ACT_SPD_MS** (이상치율: 2.14%, 안정성: 0.606)

![PR9L1_ACT_SPD_MS](09_PR_Detailed/PR9L1_ACT_SPD_MS_rolling_zscore.png)

**PR8L1_ACT_SPD_MS** (이상치율: 2.12%, 안정성: 0.558)

![PR8L1_ACT_SPD_MS](09_PR_Detailed/PR8L1_ACT_SPD_MS_rolling_zscore.png)

**PR7L2_ACT_SPD_MS** (이상치율: 1.89%, 안정성: 0.000)

![PR7L2_ACT_SPD_MS](09_PR_Detailed/PR7L2_ACT_SPD_MS_rolling_zscore.png)



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
| 생성일시 | 2026-02-23 16:00:45 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

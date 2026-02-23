# 강종 [N5 | Size: D20] Rolling Z-Score 동적 이상치 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5  
**사이즈**: D20
**생성일시**: 2026-02-23 16:01:07

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
| 🟠 중간 이상치율 (3~10%) | 14개 | 60.9% |
| 🟢 낮은 이상치율 (<3%) | 8개 | 34.8% |
| 🟡 불안정 기준선 | 1개 | 4.3% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 이상치율 | 3.12% |
| 평균 기준선 안정성 | 0.509 |

---

## 상위 문제 태그 (이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 심각 이상치 | 안정성 | 상태 |
|------|------|----------|----------|-------------|--------|------|
| 1 | PR7L1_ACT_TORQUE | PR 상세 (토크+속도) | 5.94% | 50 | 0.727 | 🟠 |
| 2 | PR7L2_ACT_TORQUE | PR 상세 (토크+속도) | 5.38% | 74 | 0.696 | 🟠 |
| 3 | PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 5.18% | 243 | 0.169 | 🟠 |
| 4 | PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 5.07% | 73 | 0.634 | 🟠 |
| 5 | PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 5.00% | 241 | 0.164 | 🟠 |
| 6 | PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 4.54% | 37 | 0.749 | 🟠 |
| 7 | PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 4.16% | 151 | 0.401 | 🟠 |
| 8 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 3.70% | 272 | 0.331 | 🟠 |
| 9 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.69% | 141 | 0.578 | 🟠 |
| 10 | PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.65% | 146 | 0.390 | 🟠 |
| 11 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 3.47% | 244 | 0.337 | 🟠 |
| 12 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.34% | 131 | 0.628 | 🟠 |
| 13 | PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 3.33% | 252 | 0.000 | 🟠 |
| 14 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 3.18% | 226 | 0.000 | 🟠 |
| 15 | PR8L1_ACT_TORQUE | PR 상세 (토크+속도) | 1.89% | 60 | 0.677 | 🟢 |

---

## 불안정 기준선 태그

기준선 안정성(Stability Index)이 0.5 미만인 태그입니다.
이 태그들은 Rolling Z-Score 방법보다 다른 방법이 더 적합할 수 있습니다.

| 태그 | 카테고리 | 안정성 | 이상치율 |
|------|----------|--------|----------|
| PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 0.000 | 3.18% |
| PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 0.000 | 3.33% |
| PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.164 | 5.00% |
| PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.169 | 5.18% |
| PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 0.331 | 3.70% |
| PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 0.337 | 3.47% |
| PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.390 | 3.65% |
| PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.401 | 4.16% |
| PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 0.414 | 0.48% |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 이상치율: 2.00%
- 평균 안정성: 0.474

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PINCHROLL_2_ACTUAL_SPEED | 0.94% | 51 | 0.724 | 13.67 |
| PINCHROLL_3_ACTUAL_SPEED | 3.18% | 226 | 0.000 | 29.53 |
| PINCHROLL_4_ACTUAL_SPEED | 3.47% | 244 | 0.337 | 31.55 |
| PINCHROLL_2_ACTUAL_TORQUE | 1.29% | 90 | 0.700 | 21.38 |
| PINCHROLL_3_ACTUAL_TORQUE | 1.36% | 94 | 0.664 | 26.52 |
| PINCHROLL_4_ACTUAL_TORQUE | 1.82% | 119 | 0.666 | 22.45 |
| PINCHROLL_2_REFERENCE_TORQUE | 0.48% | 49 | 0.414 | 22.53 |
| PINCHROLL_3_REFERENCE_TORQUE | 1.23% | 25 | 0.685 | 6.56 |
| PINCHROLL_4_REFERENCE_TORQUE | 1.23% | 19 | 0.687 | 6.56 |
| PINCHROLL_3_REFERENCE_SPEED | 3.33% | 252 | 0.000 | 29.10 |
| PINCHROLL_4_REFERENCE_SPEED | 3.70% | 272 | 0.331 | 33.45 |

#### Z-Score 차트

**PINCHROLL_4_REFERENCE_SPEED** (이상치율: 3.70%, 안정성: 0.331)

![PINCHROLL_4_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_4_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_4_ACTUAL_SPEED** (이상치율: 3.47%, 안정성: 0.337)

![PINCHROLL_4_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_rolling_zscore.png)

**PINCHROLL_3_REFERENCE_SPEED** (이상치율: 3.33%, 안정성: 0.000)

![PINCHROLL_3_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_3_REFERENCE_SPEED_rolling_zscore.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 이상치율: 4.14%
- 평균 안정성: 0.541

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PR6L1_ACT_TORQUE | 4.54% | 37 | 0.749 | 9.76 |
| PR6L2_ACT_TORQUE | 5.07% | 73 | 0.634 | 12.69 |
| PR7L1_ACT_TORQUE | 5.94% | 50 | 0.727 | 13.49 |
| PR7L2_ACT_TORQUE | 5.38% | 74 | 0.696 | 14.11 |
| PR8L1_ACT_TORQUE | 1.89% | 60 | 0.677 | 13.96 |
| PR9L1_ACT_TORQUE | 1.87% | 64 | 0.681 | 14.40 |
| PR6L1_ACT_SPD_MS | 4.16% | 151 | 0.401 | 27.23 |
| PR6L2_ACT_SPD_MS | 5.18% | 243 | 0.169 | 48.05 |
| PR7L1_ACT_SPD_MS | 3.65% | 146 | 0.390 | 27.17 |
| PR7L2_ACT_SPD_MS | 5.00% | 241 | 0.164 | 47.98 |
| PR8L1_ACT_SPD_MS | 3.69% | 141 | 0.578 | 15.57 |
| PR9L1_ACT_SPD_MS | 3.34% | 131 | 0.628 | 13.24 |

#### Z-Score 차트

**PR7L1_ACT_TORQUE** (이상치율: 5.94%, 안정성: 0.727)

![PR7L1_ACT_TORQUE](09_PR_Detailed/PR7L1_ACT_TORQUE_rolling_zscore.png)

**PR7L2_ACT_TORQUE** (이상치율: 5.38%, 안정성: 0.696)

![PR7L2_ACT_TORQUE](09_PR_Detailed/PR7L2_ACT_TORQUE_rolling_zscore.png)

**PR6L2_ACT_SPD_MS** (이상치율: 5.18%, 안정성: 0.169)

![PR6L2_ACT_SPD_MS](09_PR_Detailed/PR6L2_ACT_SPD_MS_rolling_zscore.png)



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
| 생성일시 | 2026-02-23 16:01:07 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

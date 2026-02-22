# 강종 [N5 | Size: D12] Rolling Z-Score 동적 이상치 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5  
**사이즈**: D12
**생성일시**: 2026-02-23 01:42:05

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
| 🟢 낮은 이상치율 (<3%) | 8개 | 34.8% |
| 🟡 불안정 기준선 | 14개 | 60.9% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 이상치율 | 1.70% |
| 평균 기준선 안정성 | 0.348 |

---

## 상위 문제 태그 (이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 심각 이상치 | 안정성 | 상태 |
|------|------|----------|----------|-------------|--------|------|
| 1 | PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 3.03% | 952 | 0.079 | 🟠 |
| 2 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.99% | 337 | 0.270 | 🟡 |
| 3 | PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.86% | 332 | 0.000 | 🟡 |
| 4 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 2.85% | 919 | 0.165 | 🟡 |
| 5 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.83% | 335 | 0.264 | 🟡 |
| 6 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 2.58% | 832 | 0.208 | 🟡 |
| 7 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 2.51% | 755 | 0.125 | 🟡 |
| 8 | PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 2.43% | 301 | 0.000 | 🟡 |
| 9 | PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 2.24% | 243 | 0.000 | 🟡 |
| 10 | PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 2.22% | 578 | 0.000 | 🟡 |
| 11 | PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 2.16% | 431 | 0.000 | 🟡 |
| 12 | PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 1.97% | 355 | 0.000 | 🟡 |
| 13 | PR7L1_ACT_TORQUE | PR 상세 (토크+속도) | 1.92% | 214 | 0.000 | 🟡 |
| 14 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 1.30% | 397 | 0.658 | 🟢 |
| 15 | PR7L2_ACT_TORQUE | PR 상세 (토크+속도) | 1.24% | 297 | 0.000 | 🟡 |

---

## 불안정 기준선 태그

기준선 안정성(Stability Index)이 0.5 미만인 태그입니다.
이 태그들은 Rolling Z-Score 방법보다 다른 방법이 더 적합할 수 있습니다.

| 태그 | 카테고리 | 안정성 | 이상치율 |
|------|----------|--------|----------|
| PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 0.000 | 2.43% |
| PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.000 | 2.22% |
| PR7L1_ACT_TORQUE | PR 상세 (토크+속도) | 0.000 | 1.92% |
| PR7L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.000 | 1.24% |
| PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 2.86% |
| PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 2.16% |
| PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 2.24% |
| PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.000 | 1.97% |
| PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 0.079 | 3.03% |
| PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 0.125 | 2.51% |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 이상치율: 1.36%
- 평균 안정성: 0.530

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PINCHROLL_2_ACTUAL_SPEED | 1.30% | 397 | 0.658 | 23.72 |
| PINCHROLL_3_ACTUAL_SPEED | 2.51% | 755 | 0.125 | 38.23 |
| PINCHROLL_4_ACTUAL_SPEED | 2.58% | 832 | 0.208 | 40.50 |
| PINCHROLL_2_ACTUAL_TORQUE | 0.36% | 65 | 0.851 | 14.19 |
| PINCHROLL_3_ACTUAL_TORQUE | 0.49% | 107 | 0.805 | 25.68 |
| PINCHROLL_4_ACTUAL_TORQUE | 0.37% | 74 | 0.824 | 14.41 |
| PINCHROLL_2_REFERENCE_TORQUE | 0.69% | 330 | 0.414 | 39.79 |
| PINCHROLL_3_REFERENCE_TORQUE | 0.38% | 71 | 0.827 | 26.86 |
| PINCHROLL_4_REFERENCE_TORQUE | 0.39% | 53 | 0.877 | 6.59 |
| PINCHROLL_3_REFERENCE_SPEED | 3.03% | 952 | 0.079 | 44.18 |
| PINCHROLL_4_REFERENCE_SPEED | 2.85% | 919 | 0.165 | 43.45 |

#### Z-Score 차트

**PINCHROLL_3_REFERENCE_SPEED** (이상치율: 3.03%, 안정성: 0.079)

![PINCHROLL_3_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_3_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_4_REFERENCE_SPEED** (이상치율: 2.85%, 안정성: 0.165)

![PINCHROLL_4_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_4_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_4_ACTUAL_SPEED** (이상치율: 2.58%, 안정성: 0.208)

![PINCHROLL_4_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_rolling_zscore.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 이상치율: 2.02%
- 평균 안정성: 0.181

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PR6L1_ACT_TORQUE | 2.43% | 301 | 0.000 | 40.92 |
| PR6L2_ACT_TORQUE | 2.22% | 578 | 0.000 | 46.58 |
| PR7L1_ACT_TORQUE | 1.92% | 214 | 0.000 | 23.00 |
| PR7L2_ACT_TORQUE | 1.24% | 297 | 0.000 | 23.00 |
| PR8L1_ACT_TORQUE | 0.57% | 59 | 0.878 | 23.00 |
| PR9L1_ACT_TORQUE | 0.81% | 54 | 0.761 | 23.00 |
| PR6L1_ACT_SPD_MS | 2.86% | 332 | 0.000 | 55.43 |
| PR6L2_ACT_SPD_MS | 2.16% | 431 | 0.000 | 47.18 |
| PR7L1_ACT_SPD_MS | 2.24% | 243 | 0.000 | 55.96 |
| PR7L2_ACT_SPD_MS | 1.97% | 355 | 0.000 | 62.01 |
| PR8L1_ACT_SPD_MS | 2.99% | 337 | 0.270 | 24.12 |
| PR9L1_ACT_SPD_MS | 2.83% | 335 | 0.264 | 23.00 |

#### Z-Score 차트

**PR8L1_ACT_SPD_MS** (이상치율: 2.99%, 안정성: 0.270)

![PR8L1_ACT_SPD_MS](09_PR_Detailed/PR8L1_ACT_SPD_MS_rolling_zscore.png)

**PR6L1_ACT_SPD_MS** (이상치율: 2.86%, 안정성: 0.000)

![PR6L1_ACT_SPD_MS](09_PR_Detailed/PR6L1_ACT_SPD_MS_rolling_zscore.png)

**PR9L1_ACT_SPD_MS** (이상치율: 2.83%, 안정성: 0.264)

![PR9L1_ACT_SPD_MS](09_PR_Detailed/PR9L1_ACT_SPD_MS_rolling_zscore.png)



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
| 생성일시 | 2026-02-23 01:42:05 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

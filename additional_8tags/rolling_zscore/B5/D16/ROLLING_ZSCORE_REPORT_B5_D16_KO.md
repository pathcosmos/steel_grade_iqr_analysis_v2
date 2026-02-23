# 강종 [B5 | Size: D16] Rolling Z-Score 동적 이상치 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: B5  
**사이즈**: D16
**생성일시**: 2026-02-23 15:59:11

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
| 🟠 중간 이상치율 (3~10%) | 2개 | 8.7% |
| 🟢 낮은 이상치율 (<3%) | 21개 | 91.3% |
| 🟡 불안정 기준선 | 0개 | 0.0% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 이상치율 | 0.50% |
| 평균 기준선 안정성 | 0.911 |

---

## 상위 문제 태그 (이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 심각 이상치 | 안정성 | 상태 |
|------|------|----------|----------|-------------|--------|------|
| 1 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.66% | 8 | 0.969 | 🟠 |
| 2 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 3.45% | 0 | 0.968 | 🟠 |
| 3 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 1.74% | 42 | 0.633 | 🟢 |
| 4 | PINCHROLL_3_REFERENCE_SPEED | 핀치롤 | 1.23% | 25 | 0.698 | 🟢 |
| 5 | PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 0.29% | 18 | 0.804 | 🟢 |
| 6 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 0.19% | 5 | 0.864 | 🟢 |
| 7 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 0.13% | 2 | 0.911 | 🟢 |
| 8 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 0.13% | 2 | 0.893 | 🟢 |
| 9 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 0.13% | 2 | 0.895 | 🟢 |
| 10 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 0.11% | 3 | 0.910 | 🟢 |
| 11 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 0.11% | 2 | 0.923 | 🟢 |
| 12 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 0.11% | 2 | 0.924 | 🟢 |
| 13 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 0.10% | 2 | 0.897 | 🟢 |
| 14 | PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 0.05% | 0 | 0.950 | 🟢 |
| 15 | PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 0.03% | 0 | 0.953 | 🟢 |

---

## 불안정 기준선 태그

기준선 안정성(Stability Index)이 0.5 미만인 태그입니다.
이 태그들은 Rolling Z-Score 방법보다 다른 방법이 더 적합할 수 있습니다.

| 태그 | 카테고리 | 안정성 | 이상치율 |
|------|----------|--------|----------|
| - | 불안정 태그 없음 | - | - |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 이상치율: 0.39%
- 평균 안정성: 0.850

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PINCHROLL_2_ACTUAL_SPEED | 0.19% | 5 | 0.864 | 7.68 |
| PINCHROLL_3_ACTUAL_SPEED | 0.13% | 2 | 0.911 | 5.68 |
| PINCHROLL_4_ACTUAL_SPEED | 0.11% | 3 | 0.910 | 5.63 |
| PINCHROLL_2_ACTUAL_TORQUE | 0.10% | 2 | 0.897 | 5.83 |
| PINCHROLL_3_ACTUAL_TORQUE | 0.13% | 2 | 0.893 | 5.83 |
| PINCHROLL_4_ACTUAL_TORQUE | 0.13% | 2 | 0.895 | 5.83 |
| PINCHROLL_2_REFERENCE_TORQUE | 0.29% | 18 | 0.804 | 20.01 |
| PINCHROLL_3_REFERENCE_TORQUE | 0.11% | 2 | 0.923 | 5.83 |
| PINCHROLL_4_REFERENCE_TORQUE | 0.11% | 2 | 0.924 | 5.83 |
| PINCHROLL_3_REFERENCE_SPEED | 1.23% | 25 | 0.698 | 8.89 |
| PINCHROLL_4_REFERENCE_SPEED | 1.74% | 42 | 0.633 | 16.01 |

#### Z-Score 차트

**PINCHROLL_4_REFERENCE_SPEED** (이상치율: 1.74%, 안정성: 0.633)

![PINCHROLL_4_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_4_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_3_REFERENCE_SPEED** (이상치율: 1.23%, 안정성: 0.698)

![PINCHROLL_3_REFERENCE_SPEED](08_Pinchroll/PINCHROLL_3_REFERENCE_SPEED_rolling_zscore.png)

**PINCHROLL_2_REFERENCE_TORQUE** (이상치율: 0.29%, 안정성: 0.804)

![PINCHROLL_2_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_2_REFERENCE_TORQUE_rolling_zscore.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 이상치율: 0.60%
- 평균 안정성: 0.966

| 태그 | 이상치율 | 심각 이상치 | 안정성 | Max \|Z\| |
|------|----------|-------------|--------|--------|
| PR6L1_ACT_TORQUE | 0.03% | 0 | 0.953 | 3.33 |
| PR6L2_ACT_TORQUE | 0.00% | 0 | 0.969 | 2.79 |
| PR7L1_ACT_TORQUE | 0.03% | 0 | 0.962 | 3.33 |
| PR7L2_ACT_TORQUE | 0.00% | 0 | 0.966 | 2.83 |
| PR8L1_ACT_TORQUE | 0.00% | 0 | 0.983 | 2.11 |
| PR9L1_ACT_TORQUE | 0.00% | 0 | 0.986 | 2.03 |
| PR6L1_ACT_SPD_MS | 0.05% | 0 | 0.950 | 3.33 |
| PR6L2_ACT_SPD_MS | 0.00% | 0 | 0.968 | 2.70 |
| PR7L1_ACT_SPD_MS | 0.03% | 0 | 0.958 | 3.33 |
| PR7L2_ACT_SPD_MS | 0.00% | 0 | 0.960 | 2.86 |
| PR8L1_ACT_SPD_MS | 3.66% | 8 | 0.969 | 4.13 |
| PR9L1_ACT_SPD_MS | 3.45% | 0 | 0.968 | 3.99 |

#### Z-Score 차트

**PR8L1_ACT_SPD_MS** (이상치율: 3.66%, 안정성: 0.969)

![PR8L1_ACT_SPD_MS](09_PR_Detailed/PR8L1_ACT_SPD_MS_rolling_zscore.png)

**PR9L1_ACT_SPD_MS** (이상치율: 3.45%, 안정성: 0.968)

![PR9L1_ACT_SPD_MS](09_PR_Detailed/PR9L1_ACT_SPD_MS_rolling_zscore.png)

**PR6L1_ACT_SPD_MS** (이상치율: 0.05%, 안정성: 0.950)

![PR6L1_ACT_SPD_MS](09_PR_Detailed/PR6L1_ACT_SPD_MS_rolling_zscore.png)



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
| 생성일시 | 2026-02-23 15:59:11 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

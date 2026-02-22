# 강종 [N5] | 규격: D16 CUSUM-EWMA 공정 관리도 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5
**규격**: D16
**생성일시**: 2026-02-23 01:39:45

---

## 분석 개요

### 분석 방법론

| 방법 | 목적 | 파라미터 |
|------|------|----------|
| **CUSUM** | 점진적 드리프트 탐지 | k=0.5σ, h=5.0σ |
| **EWMA** | 급격한 변화 탐지 | λ=0.2, L=3.0 |

### 분석 결과 요약

| 구분 | 태그 수 | 비율 |
|------|---------|------|
| **총 분석 태그** | 23개 | 100% |
| 🔴 드리프트 탐지 | 23개 | 100.0% |
| 🟠 시프트 탐지 | 23개 | 100.0% |
| 🟡 경고 | 0개 | 0.0% |
| 🟢 안정 | 0개 | 0.0% |

---

## 상위 문제 태그 (드리프트 빈도 기준)

| 순위 | 태그 | 카테고리 | CUSUM 드리프트 | EWMA 시프트 | 상태 |
|------|------|----------|----------------|-------------|------|
| 1 | PR9L1_ACT_TORQUE | PR 상세 (토크+속도) | 687 | 359 | 🔴 |
| 2 | PR8L1_ACT_TORQUE | PR 상세 (토크+속도) | 620 | 363 | 🔴 |
| 3 | PR6L1_ACT_TORQUE | PR 상세 (토크+속도) | 365 | 412 | 🔴 |
| 4 | PINCHROLL_2_ACTUAL_TORQUE | 핀치롤 | 354 | 378 | 🔴 |
| 5 | PR7L1_ACT_TORQUE | PR 상세 (토크+속도) | 347 | 449 | 🔴 |
| 6 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 340 | 374 | 🔴 |
| 7 | PINCHROLL_3_REFERENCE_TORQUE | 핀치롤 | 328 | 340 | 🔴 |
| 8 | PINCHROLL_2_ACTUAL_SPEED | 핀치롤 | 213 | 206 | 🔴 |
| 9 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 185 | 283 | 🔴 |
| 10 | PR9L1_ACT_SPD_MS | PR 상세 (토크+속도) | 168 | 150 | 🔴 |
| 11 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 138 | 268 | 🔴 |
| 12 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 136 | 144 | 🔴 |
| 13 | PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 15 | 16 | 🔴 |
| 14 | PR6L1_ACT_SPD_MS | PR 상세 (토크+속도) | 7 | 8 | 🔴 |
| 15 | PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 7 | 8 | 🔴 |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 드리프트 탐지: 11개
- 시프트 탐지: 11개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PINCHROLL_2_ACTUAL_SPEED | 213 | 206 | 🔴 |
| PINCHROLL_3_ACTUAL_SPEED | 4 | 4 | 🔴 |
| PINCHROLL_4_ACTUAL_SPEED | 3 | 3 | 🔴 |
| PINCHROLL_2_ACTUAL_TORQUE | 354 | 378 | 🔴 |
| PINCHROLL_3_ACTUAL_TORQUE | 138 | 268 | 🔴 |
| PINCHROLL_4_ACTUAL_TORQUE | 185 | 283 | 🔴 |
| PINCHROLL_2_REFERENCE_TORQUE | 15 | 16 | 🔴 |
| PINCHROLL_3_REFERENCE_TORQUE | 328 | 340 | 🔴 |
| PINCHROLL_4_REFERENCE_TORQUE | 340 | 374 | 🔴 |
| PINCHROLL_3_REFERENCE_SPEED | 4 | 4 | 🔴 |
| PINCHROLL_4_REFERENCE_SPEED | 3 | 3 | 🔴 |

#### 주요 태그 차트

**PINCHROLL_2_ACTUAL_TORQUE** (Drift: 354, Shift: 378)

![PINCHROLL_2_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_2_ACTUAL_TORQUE_combined.png)

**PINCHROLL_4_REFERENCE_TORQUE** (Drift: 340, Shift: 374)

![PINCHROLL_4_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_4_REFERENCE_TORQUE_combined.png)

**PINCHROLL_3_REFERENCE_TORQUE** (Drift: 328, Shift: 340)

![PINCHROLL_3_REFERENCE_TORQUE](08_Pinchroll/PINCHROLL_3_REFERENCE_TORQUE_combined.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 드리프트 탐지: 12개
- 시프트 탐지: 12개
- 안정: 0개

| 태그 | CUSUM Drift | EWMA Shift | 상태 |
|------|-------------|------------|------|
| PR6L1_ACT_TORQUE | 365 | 412 | 🔴 |
| PR6L2_ACT_TORQUE | 1 | 241 | 🔴 |
| PR7L1_ACT_TORQUE | 347 | 449 | 🔴 |
| PR7L2_ACT_TORQUE | 3 | 6 | 🔴 |
| PR8L1_ACT_TORQUE | 620 | 363 | 🔴 |
| PR9L1_ACT_TORQUE | 687 | 359 | 🔴 |
| PR6L1_ACT_SPD_MS | 7 | 8 | 🔴 |
| PR6L2_ACT_SPD_MS | 3 | 6 | 🔴 |
| PR7L1_ACT_SPD_MS | 7 | 8 | 🔴 |
| PR7L2_ACT_SPD_MS | 4 | 6 | 🔴 |
| PR8L1_ACT_SPD_MS | 136 | 144 | 🔴 |
| PR9L1_ACT_SPD_MS | 168 | 150 | 🔴 |

#### 주요 태그 차트

**PR9L1_ACT_TORQUE** (Drift: 687, Shift: 359)

![PR9L1_ACT_TORQUE](09_PR_Detailed/PR9L1_ACT_TORQUE_combined.png)

**PR8L1_ACT_TORQUE** (Drift: 620, Shift: 363)

![PR8L1_ACT_TORQUE](09_PR_Detailed/PR8L1_ACT_TORQUE_combined.png)

**PR6L1_ACT_TORQUE** (Drift: 365, Shift: 412)

![PR6L1_ACT_TORQUE](09_PR_Detailed/PR6L1_ACT_TORQUE_combined.png)



---

## 해석 가이드

### CUSUM (Cumulative Sum) 관리도

- **원리**: 목표값 대비 편차의 누적합을 추적
- **장점**: 작은 지속적 변화(0.5σ~2σ)에 민감
- **드리프트**: 누적합이 결정 구간(h)을 초과하면 탐지
- **활용**: 점진적인 공정 악화, 센서 드리프트 탐지

### EWMA (Exponentially Weighted Moving Average) 관리도

- **원리**: 최근 데이터에 더 큰 가중치를 부여
- **장점**: 급격한 변화에 빠른 반응
- **시프트**: EWMA 값이 제어 한계를 벗어나면 탐지
- **활용**: 급격한 공정 변화, 이상 상태 전환 탐지

### 상태 정의

| 상태 | 설명 | 권장 조치 |
|------|------|----------|
| 🔴 드리프트 탐지 | CUSUM에서 점진적 변화 감지 | 원인 분석 및 공정 조정 |
| 🟠 시프트 탐지 | EWMA에서 급격한 변화 감지 | 즉시 점검 필요 |
| 🟡 경고 | 위반율 5% 초과 | 모니터링 강화 |
| 🟢 안정 | 정상 범위 | 현 상태 유지 |

---

## 메타데이터

| 항목 | 값 |
|------|-----|
| 분석 스크립트 | steel_grade_cusum_ewma_analysis.py |
| 분석 기간 | 2025-03-01 ~ 2025-08-31 |
| 강종 | N5 |
| 규격 | D16 |
| 생성일시 | 2026-02-23 01:39:45 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

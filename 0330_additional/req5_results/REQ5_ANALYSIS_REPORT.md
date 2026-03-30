# REQ #5 분석 결과: ML vs 통계 Feature 순위 불일치 해소

분석일: 2026-03-30 21:39

데이터: tag_defect_matrix (127일, 2025-05-15 ~ 2025-08-30)


## 1. 기본 태그 단위 순위 비교

- 통계(Spearman) base 태그: 46개
- ML(Ensemble FI) base 태그: 47개
- 합집합 비교: 38개


### 통계 Top-5

| Rank | Tag | |Spearman| |
|:----:|-----|:--------:|
| 1 | PINCHROLL_3_REFERENCE_TORQUE | 0.5912 |
| 2 | PR6L2_ACT_TORQUE | 0.5811 |
| 3 | PR6L1_ACT_TORQUE | 0.5719 |
| 4 | STAND_12_ACTUAL_TORQUE | 0.5679 |
| 5 | STAND_11_ACTUAL_TORQUE | 0.5542 |

### ML Top-5

| Rank | Tag | Max FI |
|:----:|-----|:------:|
| 1 | FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 0.0082 |
| 2 | PINCHROLL_3_REFERENCE_TORQUE | 0.0074 |
| 3 | MAIN_WASTE_GAS_PRESSURE | 0.0068 |
| 4 | PR6L2_ACT_TORQUE | 0.0066 |
| 5 | PR9L1_ACT_TORQUE | 0.0053 |

### Reconciled Ranking Top-10

| Rank | Tag | Stat Rank | ML Rank | Diff | Score |
|:----:|-----|:---------:|:-------:|:----:|:-----:|
| 1 | PINCHROLL_3_REFERENCE_TORQUE | 1 | 2 | +1 | 0.941 |
| 2 | FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 10 | 1 | -9 | 0.933 |
| 3 | PR6L2_ACT_TORQUE | 2 | 4 | +2 | 0.876 |
| 4 | MAIN_WASTE_GAS_PRESSURE | 15 | 3 | -12 | 0.825 |
| 5 | PR9L1_ACT_TORQUE | 9 | 5 | -4 | 0.745 |
| 6 | PR6L1_ACT_TORQUE | 3 | 7 | +4 | 0.709 |
| 7 | STAND_1_ACTUAL_TORQUE | 12 | 8 | -4 | 0.618 |
| 8 | STAND_6_ACTUAL_TORQUE | 13 | 9 | -4 | 0.617 |
| 9 | PINCHROLL_4_REFERENCE_TORQUE | 6 | 14 | +8 | 0.604 |
| 10 | STAND_10_ACTUAL_TORQUE | 14 | 12 | -2 | 0.594 |

## 2. 반증 사례 요약

- 통계 Top-1: PINCHROLL_3_REFERENCE_TORQUE (PINCHROLL_3_REFERENCE_TORQUE_std)
- ML Top-1: FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE (FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE_std)

| Type | Count | Meaning |
|------|:-----:|---------|
| A_consensus | 26 | Both methods agree, actually defective |
| B_stat_false_alarm | 18 | Stat says risk, ML says normal, actually normal |
| C_ml_superior | 1 | ML says risk, Stat says normal, actually defective |
| D_undetected | 0 | Both say normal, actually defective |

## 3. 현장 설득 핵심 메시지

1. **통계와 ML은 다른 질문에 답한다** — 통계: 개별 변수의 독립 효과, ML: 다변량 순수 효과
2. **통계 내부에서도 순위가 다름** — Spearman(단조 상관) vs Cohen's d(그룹 분리도)는 측정 대상이 다름
3. **반증 사례가 증거** — Type B(통계 과대경보)와 Type C(ML 우위) 사례가 핵심 설득 자료
4. **Reconciled Ranking** — 두 방법을 가중 통합한 순위를 '현장 권고 순위'로 사용


## 4. 생성된 파일

- `reconciled_ranking.csv` — 통합 순위표
- `counter_examples.csv` — 반증 사례 카탈로그
- `chart1_bump_ranking.png` — 순위 비교 Bump Chart
- `chart2_normalized_importance.png` — 정규화 중요도 비교
- `chart3_reconciled_ranking.png` — 통합 순위 Top-15
- `chart4_counter_examples.png` — 반증 사례 산점도
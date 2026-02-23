# 추가 8개 태그 다기법 이상치 분석 결과

## 분석 배경

`TAG_CROSS_VERIFICATION_ACTIONS.md` 교차 검증 결과, ClickHouse DB의 `iba_timeseries_unified_alter` 테이블에 데이터가 존재하지만 기존 분석 스크립트(`steel_grade_iqr_analysis_v2.py`)에 포함되지 않은 **8개 태그**가 발견되었습니다.

이 폴더는 해당 8개 태그에 대한 **전 강종(B5/D4/D5/N5) × 전 규격(all-sizes)** 분석 결과를 담고 있습니다.
초기 IQR 분석 이후 **CUSUM-EWMA, Rolling Z-Score, STL Residual, Mahalanobis** 4개 기법을 추가 적용하여 다기법 교차 검증을 완료하였으며, 경영진 보고용 **PPT 발표자료**도 생성하였습니다.

## 추가 태그 목록 (8개)

### Group A — `08_Pinchroll` 카테고리 추가 (2개)

| 태그명 | 설명 | 비고 |
|--------|------|------|
| `PINCHROLL_3_REFERENCE_SPEED` | 핀치롤 3 기준속도 | 기존 ACTUAL_SPEED의 설정값 |
| `PINCHROLL_4_REFERENCE_SPEED` | 핀치롤 4 기준속도 | 기존 ACTUAL_SPEED의 설정값 |

### Group B — `09_PR_Detailed` 카테고리 추가 (6개)

| 태그명 | 설명 | 비고 |
|--------|------|------|
| `PR6L1_ACT_SPD_MS` | PR6 L1(A라인) 실제 속도 (m/s) | 기존 토크 태그의 속도 대응값 |
| `PR6L2_ACT_SPD_MS` | PR6 L2(B라인) 실제 속도 (m/s) | 기존 토크 태그의 속도 대응값 |
| `PR7L1_ACT_SPD_MS` | PR7 L1(A라인) 실제 속도 (m/s) | 기존 토크 태그의 속도 대응값 |
| `PR7L2_ACT_SPD_MS` | PR7 L2(B라인) 실제 속도 (m/s) | 기존 토크 태그의 속도 대응값 |
| `PR8L1_ACT_SPD_MS` | PR8 L1(A라인) 실제 속도 (m/s) | L1 전용 |
| `PR9L1_ACT_SPD_MS` | PR9 L1(A라인) 실제 속도 (m/s) | L1 전용 |

## 분석 범위

- **분석 기간**: 2025-03-01 ~ 2025-08-31
- **강종**: B5, D4, D5, N5
- **규격**: 전 규격 (all-sizes), 10개 규격 (D10, D12, D13, D16, D20)
- **필터**: run_only + special_ops + roll_change + coiling_transient

### 분석 기법 (5가지)

| 기법 | 약어 | 설명 | 탐지 대상 |
|------|------|------|----------|
| **IQR** | Interquartile Range | 사분위 범위 기반 이상치 탐지 | 정적 분포 이상치 (극단값) |
| **CUSUM-EWMA** | Cumulative Sum + Exponentially Weighted Moving Average | 누적합·지수가중이동평균 관리도 | 공정 드리프트, 평균 이동 |
| **Rolling Z-Score** | 이동 Z-점수 | 이동 윈도우 기반 표준편차 이탈 | 국소적 급변, 스파이크 |
| **STL Residual** | Seasonal-Trend Decomposition (Loess) 잔차 | 시계열 분해 후 잔차 분석 | 추세·계절성 제거 후 비정상 잔차 |
| **Mahalanobis** | 마할라노비스 거리 | 다변량 상관 구조를 반영한 거리 기반 탐지 | 다변량 이상 조합 |

## 분석 결과 요약

### 핵심 발견 3줄 요약

1. **핀치롤 3/4번 속도, PR6 토크**는 전 강종에서 4기법 모두 이상을 탐지한 **확정 문제** 설비 신호
2. 문제의 **64%가 밀 후반부**(스탠드 속도 + 핀치롤 + PR 토크)에 집중 → 설비 정비 우선 대상
3. D5 강종이 CUSUM·STL 최고 위험(98%), B5는 IQR 기준 65%로 가장 높은 정적 이상치율

### 전체 현황

| 구분 | 수치 |
|------|------|
| 전체 태그×기법 조합 | 1,386건 |
| 문제 판정 태그 (1기법 이상) | **87개** |
| 3기법 이상 교차 확인 문제 태그 | **47개** |
| 4기법 교차 확인 (확정 문제) | **3개** |

### 4기법 교차 확인 확정 문제 태그

| 태그 | 카테고리 | 최대 이상치율 | 해당 강종 |
|------|---------|-------------|----------|
| PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 100.0% | B5, D4, D5, N5 (전체) |
| PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 100.0% | B5, D4, D5, N5 (전체) |
| PR6L2_ACT_TORQUE | PR 상세 토크 | 99.8% | B5, D4, D5, N5 (전체) |

### 강종별 건전성 요약

| 강종 | IQR 문제 태그 | CUSUM 드리프트 | 종합 판정 |
|------|-------------|---------------|----------|
| **B5** | 30/46 (65%) | 70/79 (89%) | 🔴 위험 — 핀치롤·스탠드 속도 전반 이상 |
| **D4** | 13/46 (28%) | 75/79 (95%) | 🟠 경고 — CUSUM 드리프트 가장 높음, IQR은 상대적 안정 |
| **D5** | 19/46 (41%) | 77/79 (98%) | 🔴 위험 — CUSUM·STL 최고 위험, 스탠드 속도 심각 |
| **N5** | 42/92 (46%) | 74/79 (94%) | 🟠 경고 — 사이즈별 편차 큼 (D20 특이) |

### IQR 강종별 차트 수

| 강종 | 규격 | PNG 차트 수 |
|------|------|-------------|
| B5 | D13, D16 | 832 |
| D4 | D10, D13 | 1,464 |
| D5 | D10, D13 | 1,936 |
| N5 | D10, D12, D16, D20 | 3,560 |
| **합계** | **10 규격** | **7,792** |

### 기법별 차트 수

| 기법 | PNG 차트 수 | 리포트 수 |
|------|-------------|----------|
| IQR | 7,792 | 10개 (강종×규격별) |
| CUSUM-EWMA | 687 | 10개 (강종×규격별) |
| Rolling Z-Score | 230 | 10개 (강종×규격별) |
| STL Residual | 374 | 9개 (B5/D16 데이터 부족 제외) |
| Mahalanobis | 90 | 10개 (강종×규격별) |
| PPT 발표 차트 | 348 | 6개 (종합) |
| **합계** | **9,521** | **55개** |

## 폴더 구조

```
additional_8tags/
├── README.md                          ← 본 문서
├── B5/                                ← IQR 분석 (D13, D16)
│   ├── D13/
│   │   ├── 08_Pinchroll/             (PINCHROLL 기준속도 2개 태그 차트)
│   │   ├── 09_PR_Detailed/           (PR 속도 6개 태그 차트)
│   │   ├── IQR_ANALYSIS_REPORT_B5_D13_KO.md
│   │   └── iqr_analysis_B5_D13_results.json
│   └── D16/
│       └── (동일 구조)
├── D4/                                ← IQR 분석 (D10, D13)
│   ├── D10/
│   └── D13/
├── D5/                                ← IQR 분석 (D10, D13)
│   ├── D10/
│   └── D13/
├── N5/                                ← IQR 분석 (D10, D12, D16, D20)
│   ├── D10/
│   ├── D12/
│   ├── D16/
│   └── D20/
├── cusum_ewma/                        ← CUSUM-EWMA 관리도 분석
│   ├── B5/
│   ├── D4/
│   ├── D5/
│   └── N5/
├── rolling_zscore/                    ← Rolling Z-Score 분석
│   ├── B5/
│   ├── D4/
│   ├── D5/
│   └── N5/
├── stl_residual/                      ← STL 시계열 분해 잔차 분석
│   ├── B5/
│   ├── D4/
│   ├── D5/
│   └── N5/
├── mahalanobis/                       ← Mahalanobis 다변량 분석
│   ├── B5/
│   ├── D4/
│   ├── D5/
│   └── N5/
└── ppt_summary/                       ← PPT 발표자료 및 종합 차트
    ├── 00_PPT_GUIDE.md
    ├── 01_executive_summary.md
    ├── 02_methodology.md
    ├── 03_problem_tags_analysis.md
    ├── 04_grade_comparison.md
    ├── 05_findings_and_actions.md
    ├── additional_8tags_분석결과_발표자료.pptx
    ├── appendix/
    │   ├── all_results_summary.csv
    │   ├── grade_method_summary.csv
    │   └── problem_tags.json
    └── charts/
        ├── overview/                  (종합 차트 6개)
        ├── B5/                        (B5 대표 차트 83개)
        ├── D4/                        (D4 대표 차트 84개)
        ├── D5/                        (D5 대표 차트 87개)
        └── N5/                        (N5 대표 차트 88개)
```

## 하위 문서 링크

### IQR 분석 리포트 (10개)

| 강종 | 규격 | 리포트 | 데이터 |
|------|------|--------|--------|
| B5 | D13 | [IQR_ANALYSIS_REPORT_B5_D13_KO.md](B5/D13/IQR_ANALYSIS_REPORT_B5_D13_KO.md) | [JSON](B5/D13/iqr_analysis_B5_D13_results.json) |
| B5 | D16 | [IQR_ANALYSIS_REPORT_B5_D16_KO.md](B5/D16/IQR_ANALYSIS_REPORT_B5_D16_KO.md) | [JSON](B5/D16/iqr_analysis_B5_D16_results.json) |
| D4 | D10 | [IQR_ANALYSIS_REPORT_D4_D10_KO.md](D4/D10/IQR_ANALYSIS_REPORT_D4_D10_KO.md) | [JSON](D4/D10/iqr_analysis_D4_D10_results.json) |
| D4 | D13 | [IQR_ANALYSIS_REPORT_D4_D13_KO.md](D4/D13/IQR_ANALYSIS_REPORT_D4_D13_KO.md) | [JSON](D4/D13/iqr_analysis_D4_D13_results.json) |
| D5 | D10 | [IQR_ANALYSIS_REPORT_D5_D10_KO.md](D5/D10/IQR_ANALYSIS_REPORT_D5_D10_KO.md) | [JSON](D5/D10/iqr_analysis_D5_D10_results.json) |
| D5 | D13 | [IQR_ANALYSIS_REPORT_D5_D13_KO.md](D5/D13/IQR_ANALYSIS_REPORT_D5_D13_KO.md) | [JSON](D5/D13/iqr_analysis_D5_D13_results.json) |
| N5 | D10 | [IQR_ANALYSIS_REPORT_N5_D10_KO.md](N5/D10/IQR_ANALYSIS_REPORT_N5_D10_KO.md) | [JSON](N5/D10/iqr_analysis_N5_D10_results.json) |
| N5 | D12 | [IQR_ANALYSIS_REPORT_N5_D12_KO.md](N5/D12/IQR_ANALYSIS_REPORT_N5_D12_KO.md) | [JSON](N5/D12/iqr_analysis_N5_D12_results.json) |
| N5 | D16 | [IQR_ANALYSIS_REPORT_N5_D16_KO.md](N5/D16/IQR_ANALYSIS_REPORT_N5_D16_KO.md) | [JSON](N5/D16/iqr_analysis_N5_D16_results.json) |
| N5 | D20 | [IQR_ANALYSIS_REPORT_N5_D20_KO.md](N5/D20/IQR_ANALYSIS_REPORT_N5_D20_KO.md) | [JSON](N5/D20/iqr_analysis_N5_D20_results.json) |

### CUSUM-EWMA 리포트 (10개, 사이즈별)

| 강종 | 규격 | 리포트 | 데이터 |
|------|------|--------|--------|
| B5 | D13 | [CUSUM_EWMA_REPORT_B5_D13_KO.md](cusum_ewma/B5/D13/CUSUM_EWMA_REPORT_B5_D13_KO.md) | [JSON](cusum_ewma/B5/D13/cusum_ewma_B5_D13_results.json) |
| B5 | D16 | [CUSUM_EWMA_REPORT_B5_D16_KO.md](cusum_ewma/B5/D16/CUSUM_EWMA_REPORT_B5_D16_KO.md) | [JSON](cusum_ewma/B5/D16/cusum_ewma_B5_D16_results.json) |
| D4 | D10 | [CUSUM_EWMA_REPORT_D4_D10_KO.md](cusum_ewma/D4/D10/CUSUM_EWMA_REPORT_D4_D10_KO.md) | [JSON](cusum_ewma/D4/D10/cusum_ewma_D4_D10_results.json) |
| D4 | D13 | [CUSUM_EWMA_REPORT_D4_D13_KO.md](cusum_ewma/D4/D13/CUSUM_EWMA_REPORT_D4_D13_KO.md) | [JSON](cusum_ewma/D4/D13/cusum_ewma_D4_D13_results.json) |
| D5 | D10 | [CUSUM_EWMA_REPORT_D5_D10_KO.md](cusum_ewma/D5/D10/CUSUM_EWMA_REPORT_D5_D10_KO.md) | [JSON](cusum_ewma/D5/D10/cusum_ewma_D5_D10_results.json) |
| D5 | D13 | [CUSUM_EWMA_REPORT_D5_D13_KO.md](cusum_ewma/D5/D13/CUSUM_EWMA_REPORT_D5_D13_KO.md) | [JSON](cusum_ewma/D5/D13/cusum_ewma_D5_D13_results.json) |
| N5 | D10 | [CUSUM_EWMA_REPORT_N5_D10_KO.md](cusum_ewma/N5/D10/CUSUM_EWMA_REPORT_N5_D10_KO.md) | [JSON](cusum_ewma/N5/D10/cusum_ewma_N5_D10_results.json) |
| N5 | D12 | [CUSUM_EWMA_REPORT_N5_D12_KO.md](cusum_ewma/N5/D12/CUSUM_EWMA_REPORT_N5_D12_KO.md) | [JSON](cusum_ewma/N5/D12/cusum_ewma_N5_D12_results.json) |
| N5 | D16 | [CUSUM_EWMA_REPORT_N5_D16_KO.md](cusum_ewma/N5/D16/CUSUM_EWMA_REPORT_N5_D16_KO.md) | [JSON](cusum_ewma/N5/D16/cusum_ewma_N5_D16_results.json) |
| N5 | D20 | [CUSUM_EWMA_REPORT_N5_D20_KO.md](cusum_ewma/N5/D20/CUSUM_EWMA_REPORT_N5_D20_KO.md) | [JSON](cusum_ewma/N5/D20/cusum_ewma_N5_D20_results.json) |

### Rolling Z-Score 리포트 (10개, 사이즈별)

| 강종 | 규격 | 리포트 | 데이터 |
|------|------|--------|--------|
| B5 | D13 | [ROLLING_ZSCORE_REPORT_B5_D13_KO.md](rolling_zscore/B5/D13/ROLLING_ZSCORE_REPORT_B5_D13_KO.md) | [JSON](rolling_zscore/B5/D13/rolling_zscore_B5_D13_results.json) |
| B5 | D16 | [ROLLING_ZSCORE_REPORT_B5_D16_KO.md](rolling_zscore/B5/D16/ROLLING_ZSCORE_REPORT_B5_D16_KO.md) | [JSON](rolling_zscore/B5/D16/rolling_zscore_B5_D16_results.json) |
| D4 | D10 | [ROLLING_ZSCORE_REPORT_D4_D10_KO.md](rolling_zscore/D4/D10/ROLLING_ZSCORE_REPORT_D4_D10_KO.md) | [JSON](rolling_zscore/D4/D10/rolling_zscore_D4_D10_results.json) |
| D4 | D13 | [ROLLING_ZSCORE_REPORT_D4_D13_KO.md](rolling_zscore/D4/D13/ROLLING_ZSCORE_REPORT_D4_D13_KO.md) | [JSON](rolling_zscore/D4/D13/rolling_zscore_D4_D13_results.json) |
| D5 | D10 | [ROLLING_ZSCORE_REPORT_D5_D10_KO.md](rolling_zscore/D5/D10/ROLLING_ZSCORE_REPORT_D5_D10_KO.md) | [JSON](rolling_zscore/D5/D10/rolling_zscore_D5_D10_results.json) |
| D5 | D13 | [ROLLING_ZSCORE_REPORT_D5_D13_KO.md](rolling_zscore/D5/D13/ROLLING_ZSCORE_REPORT_D5_D13_KO.md) | [JSON](rolling_zscore/D5/D13/rolling_zscore_D5_D13_results.json) |
| N5 | D10 | [ROLLING_ZSCORE_REPORT_N5_D10_KO.md](rolling_zscore/N5/D10/ROLLING_ZSCORE_REPORT_N5_D10_KO.md) | [JSON](rolling_zscore/N5/D10/rolling_zscore_N5_D10_results.json) |
| N5 | D12 | [ROLLING_ZSCORE_REPORT_N5_D12_KO.md](rolling_zscore/N5/D12/ROLLING_ZSCORE_REPORT_N5_D12_KO.md) | [JSON](rolling_zscore/N5/D12/rolling_zscore_N5_D12_results.json) |
| N5 | D16 | [ROLLING_ZSCORE_REPORT_N5_D16_KO.md](rolling_zscore/N5/D16/ROLLING_ZSCORE_REPORT_N5_D16_KO.md) | [JSON](rolling_zscore/N5/D16/rolling_zscore_N5_D16_results.json) |
| N5 | D20 | [ROLLING_ZSCORE_REPORT_N5_D20_KO.md](rolling_zscore/N5/D20/ROLLING_ZSCORE_REPORT_N5_D20_KO.md) | [JSON](rolling_zscore/N5/D20/rolling_zscore_N5_D20_results.json) |

### STL Residual 리포트 (9개, 사이즈별)

| 강종 | 규격 | 리포트 | 데이터 |
|------|------|--------|--------|
| B5 | D13 | [STL_ANALYSIS_REPORT_B5_D13_KO.md](stl_residual/B5/D13/STL_ANALYSIS_REPORT_B5_D13_KO.md) | [JSON](stl_residual/B5/D13/stl_analysis_B5_D13_results.json) |
| D4 | D10 | [STL_ANALYSIS_REPORT_D4_D10_KO.md](stl_residual/D4/D10/STL_ANALYSIS_REPORT_D4_D10_KO.md) | [JSON](stl_residual/D4/D10/stl_analysis_D4_D10_results.json) |
| D4 | D13 | [STL_ANALYSIS_REPORT_D4_D13_KO.md](stl_residual/D4/D13/STL_ANALYSIS_REPORT_D4_D13_KO.md) | [JSON](stl_residual/D4/D13/stl_analysis_D4_D13_results.json) |
| D5 | D10 | [STL_ANALYSIS_REPORT_D5_D10_KO.md](stl_residual/D5/D10/STL_ANALYSIS_REPORT_D5_D10_KO.md) | [JSON](stl_residual/D5/D10/stl_analysis_D5_D10_results.json) |
| D5 | D13 | [STL_ANALYSIS_REPORT_D5_D13_KO.md](stl_residual/D5/D13/STL_ANALYSIS_REPORT_D5_D13_KO.md) | [JSON](stl_residual/D5/D13/stl_analysis_D5_D13_results.json) |
| N5 | D10 | [STL_ANALYSIS_REPORT_N5_D10_KO.md](stl_residual/N5/D10/STL_ANALYSIS_REPORT_N5_D10_KO.md) | [JSON](stl_residual/N5/D10/stl_analysis_N5_D10_results.json) |
| N5 | D12 | [STL_ANALYSIS_REPORT_N5_D12_KO.md](stl_residual/N5/D12/STL_ANALYSIS_REPORT_N5_D12_KO.md) | [JSON](stl_residual/N5/D12/stl_analysis_N5_D12_results.json) |
| N5 | D16 | [STL_ANALYSIS_REPORT_N5_D16_KO.md](stl_residual/N5/D16/STL_ANALYSIS_REPORT_N5_D16_KO.md) | [JSON](stl_residual/N5/D16/stl_analysis_N5_D16_results.json) |
| N5 | D20 | [STL_ANALYSIS_REPORT_N5_D20_KO.md](stl_residual/N5/D20/STL_ANALYSIS_REPORT_N5_D20_KO.md) | [JSON](stl_residual/N5/D20/stl_analysis_N5_D20_results.json) |

> **참고**: B5/D16은 STL 분석에 필요한 최소 데이터(51 포인트) 미달로 리포트 미생성

### Mahalanobis 리포트 (10개, 사이즈별)

| 강종 | 규격 | 리포트 | 데이터 |
|------|------|--------|--------|
| B5 | D13 | [MAHALANOBIS_REPORT_B5_D13_KO.md](mahalanobis/B5/D13/MAHALANOBIS_REPORT_B5_D13_KO.md) | [JSON](mahalanobis/B5/D13/mahalanobis_B5_D13_results.json) |
| B5 | D16 | [MAHALANOBIS_REPORT_B5_D16_KO.md](mahalanobis/B5/D16/MAHALANOBIS_REPORT_B5_D16_KO.md) | [JSON](mahalanobis/B5/D16/mahalanobis_B5_D16_results.json) |
| D4 | D10 | [MAHALANOBIS_REPORT_D4_D10_KO.md](mahalanobis/D4/D10/MAHALANOBIS_REPORT_D4_D10_KO.md) | [JSON](mahalanobis/D4/D10/mahalanobis_D4_D10_results.json) |
| D4 | D13 | [MAHALANOBIS_REPORT_D4_D13_KO.md](mahalanobis/D4/D13/MAHALANOBIS_REPORT_D4_D13_KO.md) | [JSON](mahalanobis/D4/D13/mahalanobis_D4_D13_results.json) |
| D5 | D10 | [MAHALANOBIS_REPORT_D5_D10_KO.md](mahalanobis/D5/D10/MAHALANOBIS_REPORT_D5_D10_KO.md) | [JSON](mahalanobis/D5/D10/mahalanobis_D5_D10_results.json) |
| D5 | D13 | [MAHALANOBIS_REPORT_D5_D13_KO.md](mahalanobis/D5/D13/MAHALANOBIS_REPORT_D5_D13_KO.md) | [JSON](mahalanobis/D5/D13/mahalanobis_D5_D13_results.json) |
| N5 | D10 | [MAHALANOBIS_REPORT_N5_D10_KO.md](mahalanobis/N5/D10/MAHALANOBIS_REPORT_N5_D10_KO.md) | [JSON](mahalanobis/N5/D10/mahalanobis_N5_D10_results.json) |
| N5 | D12 | [MAHALANOBIS_REPORT_N5_D12_KO.md](mahalanobis/N5/D12/MAHALANOBIS_REPORT_N5_D12_KO.md) | [JSON](mahalanobis/N5/D12/mahalanobis_N5_D12_results.json) |
| N5 | D16 | [MAHALANOBIS_REPORT_N5_D16_KO.md](mahalanobis/N5/D16/MAHALANOBIS_REPORT_N5_D16_KO.md) | [JSON](mahalanobis/N5/D16/mahalanobis_N5_D16_results.json) |
| N5 | D20 | [MAHALANOBIS_REPORT_N5_D20_KO.md](mahalanobis/N5/D20/MAHALANOBIS_REPORT_N5_D20_KO.md) | [JSON](mahalanobis/N5/D20/mahalanobis_N5_D20_results.json) |

### PPT 발표자료 (6개 MD + 1 PPTX)

| 파일 | 내용 | PPT 분량 |
|------|------|---------|
| [00_PPT_GUIDE.md](ppt_summary/00_PPT_GUIDE.md) | 슬라이드 구성 가이드 | - |
| [01_executive_summary.md](ppt_summary/01_executive_summary.md) | 핵심 요약 (배경, 판정, 강종별 건전성) | 2-3장 |
| [02_methodology.md](ppt_summary/02_methodology.md) | 5가지 분석 기법 소개 및 판정 기준 | 2장 |
| [03_problem_tags_analysis.md](ppt_summary/03_problem_tags_analysis.md) | 문제 태그 집중 분석 (카테고리별) | 6-8장 |
| [04_grade_comparison.md](ppt_summary/04_grade_comparison.md) | 강종별 비교 및 히트맵 | 4-5장 |
| [05_findings_and_actions.md](ppt_summary/05_findings_and_actions.md) | 핵심 발견 5가지 및 조치 권고 | 3-4장 |
| [additional_8tags_분석결과_발표자료.pptx](ppt_summary/additional_8tags_분석결과_발표자료.pptx) | **PowerPoint 발표 파일** (25장) | 25장 |

### PPT 부록 데이터

| 파일 | 내용 |
|------|------|
| [all_results_summary.csv](ppt_summary/appendix/all_results_summary.csv) | 전체 기법×강종×태그 결과 요약 테이블 |
| [grade_method_summary.csv](ppt_summary/appendix/grade_method_summary.csv) | 강종×기법별 문제 태그 비율 요약 |
| [problem_tags.json](ppt_summary/appendix/problem_tags.json) | 다기법 교차 문제 태그 목록 (구조화 데이터) |

## 총 파일 현황

| 구분 | 파일 수 |
|------|--------|
| PNG 차트 | 9,521 |
| MD 리포트 | 56 (README 포함) |
| JSON 데이터 | 50 |
| CSV 요약 | 4 |
| PPTX 발표자료 | 1 |
| **총 파일** | **9,632** |

## 수정된 파일

| 파일 | 수정 내용 |
|------|----------|
| `scripts/steel_grade_iqr_analysis_v2.py` | TAG_CATEGORIES에 8개 태그 추가, `--output-dir`/`--categories` CLI 옵션 추가 |
| `scripts/steel_grade_cusum_ewma_analysis.py` | `--output-dir` CLI 옵션 추가 (절대/상대 경로 지원) |
| `scripts/steel_grade_rolling_zscore_analysis.py` | `--output-dir` CLI 옵션 추가 (절대/상대 경로 지원) |
| `scripts/steel_grade_stl_analysis.py` | `--output-dir` CLI 옵션 추가 (절대/상대 경로 지원) |
| `scripts/steel_grade_mahalanobis_analysis.py` | TAG_CATEGORIES에 8개 태그 추가, `--categories`/`--output-dir` CLI 옵션 추가 |
| `config/tag_filter_config.py` | `10_PR_Detailed` → `09_PR_Detailed` 통일, 6개 속도 태그 추가 |
| `config/tag_filter_config.yaml` | 08/09 카테고리 notes 업데이트 (태그 수, 속도 태그 명시) |
| ClickHouse VIEW | `v_iba_by_steel_grade` 뷰에 8개 컬럼 추가 (`CREATE OR REPLACE VIEW`) |

## 실행 명령어

```bash
# IQR 분석 — 특정 강종 + 특정 카테고리만 (추가 태그용)
./venv/bin/python scripts/steel_grade_iqr_analysis_v2.py \
    --grade B5 --all-sizes \
    --output-dir steel_grade_iqr_analysis_v2/additional_8tags \
    --categories 08_Pinchroll 09_PR_Detailed

# CUSUM-EWMA 분석
./venv/bin/python scripts/steel_grade_cusum_ewma_analysis.py \
    --grade B5 --all-sizes \
    --categories 08_Pinchroll 09_PR_Detailed \
    --output-dir steel_grade_iqr_analysis_v2/additional_8tags/cusum_ewma

# Rolling Z-Score 분석
./venv/bin/python scripts/steel_grade_rolling_zscore_analysis.py \
    --grade B5 --all-sizes \
    --categories 08_Pinchroll 09_PR_Detailed \
    --output-dir steel_grade_iqr_analysis_v2/additional_8tags/rolling_zscore

# STL Residual 분석
./venv/bin/python scripts/steel_grade_stl_analysis.py \
    --grade B5 --all-sizes \
    --categories 08_Pinchroll 09_PR_Detailed \
    --output-dir steel_grade_iqr_analysis_v2/additional_8tags/stl_residual

# Mahalanobis 분석
./venv/bin/python scripts/steel_grade_mahalanobis_analysis.py \
    --grade B5 --all-sizes \
    --categories 08_Pinchroll 09_PR_Detailed \
    --output-dir steel_grade_iqr_analysis_v2/additional_8tags/mahalanobis
```

## 생성일

- **IQR 분석**: 2026-02-20
- **CUSUM-EWMA / Rolling Z-Score / STL / Mahalanobis (초기, 전체 태그)**: 2026-02-22
- **PPT 발표자료**: 2026-02-23
- **4기법 재분석 (8개 추가 태그 한정, 사이즈별)**: 2026-02-23
- **README 업데이트**: 2026-02-23

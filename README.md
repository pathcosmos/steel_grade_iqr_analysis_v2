# 강종별 다각적 이상치 분석 (Steel Grade Multi-Method Anomaly Analysis) v2 - 종합 보고서

> **문서 버전**: 3.0
> **작성일**: 2026-02-06
> **목적**: 강종별/규격별 IQR 분석 및 다각적 이상치 탐지(CUSUM-EWMA, Rolling Z-Score, Mahalanobis, STL) 방법론, 필터 시스템, 태그 상세 설명 종합 정리

---

## 목차

1. [분석 시스템 개요](#1-분석-시스템-개요)
2. [필터 시스템 상세](#2-필터-시스템-상세)
3. [A/B 라인(L1/L2) 분류](#3-ab-라인l1l2-분류)
4. [IQR 분석 방법론](#4-iqr-분석-방법론)
5. [규격별 IQR 분석](#5-규격별-iqr-분석)
6. [Adjusted IQR (왜도 보정 IQR)](#6-adjusted-iqr-왜도-보정-iqr)
7. [CUSUM-EWMA 공정 관리도](#7-cusum-ewma-공정-관리도)
8. [Rolling Z-Score 동적 이상치 분석](#8-rolling-z-score-동적-이상치-분석)
9. [Mahalanobis 다변량 이상치 분석](#9-mahalanobis-다변량-이상치-분석)
10. [STL 계절-추세 분해 분석](#10-stl-계절-추세-분해-분석)
11. [분석 방법 비교](#11-분석-방법-비교)
12. [태그 카테고리별 상세 설명](#12-태그-카테고리별-상세-설명)
13. [위험도 분류 기준](#13-위험도-분류-기준)
14. [추가 수집 필요 태그](#14-추가-수집-필요-태그)
15. [분석 실행 가이드](#15-분석-실행-가이드)
16. [부록](#16-부록)

---

## 1. 분석 시스템 개요

### 1.1 시스템 아키텍처

```
┌──────────────────────────────────────────────────────────────────────┐
│                     IBA 다각적 이상치 분석 시스템                       │
├──────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─────────────┐   ┌─────────────┐   ┌─────────────────────────┐    │
│  │ ClickHouse  │ → │  필터링     │ → │  분석 엔진 (6종)        │    │
│  │   (원본)    │   │  엔진       │   │                         │    │
│  └─────────────┘   └─────────────┘   │  ① Standard IQR        │    │
│        ↓                 ↓           │  ② Adjusted IQR        │    │
│  v_iba_by_steel    tag_filter_       │  ③ CUSUM-EWMA          │    │
│  _grade 뷰         config.yaml      │  ④ Rolling Z-Score     │    │
│                                      │  ⑤ Mahalanobis         │    │
│                                      │  ⑥ STL Residual        │    │
│                                      └─────────────────────────┘    │
│                                                ↓                     │
│                                      차트(PNG) + 보고서(MD) + JSON  │
└──────────────────────────────────────────────────────────────────────┘
```

### 1.2 강종별 데이터 현황

| 강종 | 레코드 수 | 기간 | 월 수 | 비고 |
|------|-----------|------|-------|------|
| **N5** | 148,239건 | 2025-04 ~ 2025-08 | 5개월 | 최다 데이터 |
| **D5** | 74,855건 | 2025-03 ~ 2025-08 | 6개월 | 최장 기간 |
| **D4** | 20,144건 | 2025-05 ~ 2025-08 | 4개월 | - |
| **B5** | 14,391건 | 2025-04 ~ 2025-08 | 5개월 | 최초 분석 대상 |

### 1.3 태그 현황 요약

| 항목 | 값 |
|------|-----|
| 총 태그 수 | 85개 (분석 대상) |
| 카테고리 수 | 10개 |
| 제외 태그 수 | 9개 (데이터 품질 이슈) |

### 1.4 분석 출력 구조

```
analysis_output/steel_grade_iqr_analysis_v2/
│
├── ATTENTION_TAGS_REPORT.md                  # 전 강종 주의 태그 종합 보고서
├── README.md                                 # 본 문서
│
├── {강종}/                                   # B5, D4, D5, N5
│   ├── 01_Furnace_Top_Temperature/           # 카테고리별 IQR 차트
│   │   ├── {tag}_analysis.png                #   종합 6패널
│   │   ├── {tag}_01_timeseries.png           #   개별 차트 (01~07)
│   │   └── monthly/{yyyy-mm}/*.png           #   월별 차트
│   ├── 02~09_*/                              # 나머지 카테고리 (동일 구조)
│   ├── {규격}/                               # D10, D13, D16, D20 등
│   │   ├── 01~09_*/                          #   규격별 카테고리 차트
│   │   ├── iqr_analysis_{강종}_{규격}_results.json
│   │   └── IQR_ANALYSIS_REPORT_{강종}_{규격}_KO.md
│   ├── iqr_analysis_{강종}_results.json      # 강종 통합 IQR 결과
│   ├── adjusted_iqr_results_{강종}.json      # Adjusted IQR 결과
│   ├── IQR_ANALYSIS_REPORT_{강종}_KO.md
│   ├── ADJUSTED_IQR_ANALYSIS_REPORT_{강종}_KO.md
│   └── ADJUSTED_IQR_PLAN.md
│
├── cusum_ewma/
│   ├── {강종}/
│   │   ├── {카테고리}/{tag}_cusum.png        # CUSUM 누적합 차트
│   │   ├── {카테고리}/{tag}_ewma.png         # EWMA 지수가중 차트
│   │   ├── {카테고리}/{tag}_combined.png     # 통합 차트
│   │   ├── cusum_ewma_{강종}_results.json
│   │   └── CUSUM_EWMA_REPORT_{강종}_KO.md
│   └── summary/drift_detection_summary.csv
│
├── rolling_zscore/
│   ├── {강종}/
│   │   ├── {카테고리}/{tag}_rolling_zscore.png
│   │   ├── rolling_zscore_{강종}_results.json
│   │   └── ROLLING_ZSCORE_REPORT_{강종}_KO.md
│
├── mahalanobis/
│   ├── {강종}/
│   │   ├── {카테고리}_correlation_heatmap.png  # 상관계수 히트맵
│   │   ├── {카테고리}_distance.png             # 거리 분포
│   │   ├── {카테고리}_pca_scatter.png          # PCA 산점도
│   │   ├── mahalanobis_{강종}_results.json
│   │   └── MAHALANOBIS_REPORT_{강종}_KO.md
│
└── stl_residual/
    ├── {강종}/
    │   ├── {카테고리}/{tag}_stl_decomposition.png  # Trend/Seasonal/Residual 분해
    │   ├── {카테고리}/{tag}_residual_outliers.png   # 잔차 이상치
    │   ├── stl_analysis_{강종}_results.json
    │   └── STL_ANALYSIS_REPORT_{강종}_KO.md
```

### 1.5 강종별 분석 가용성

| 분석 유형 | B5 | D4 | D5 | N5 | 규격별 분석 |
|-----------|:--:|:--:|:--:|:--:|:-----------:|
| Standard IQR | ✅ | ✅ | ✅ | ✅ | ✅ |
| Adjusted IQR | ✅ | ✅ | ✅ | ✅ | - |
| CUSUM-EWMA | ✅ | ✅ | ✅ | ✅ | - |
| Rolling Z-Score | ✅ | ✅ | ✅ | ✅ | - |
| Mahalanobis | ✅ | ✅ | ✅ | ✅ | - |
| STL Residual | ✅ | ✅ | ✅ | ✅ | - |

### 1.6 규격별 분석 현황

| 강종 | 사이즈 규격 |
|------|------------|
| **B5** | D13, D16 |
| **D4** | D10, D13 |
| **D5** | D10, D13 |
| **N5** | D10, D12, D16, D20 |

---

## 2. 필터 시스템 상세

### 2.1 3단계 필터 상속 구조

```
┌─────────────────────────────────────────────────────────────────────┐
│                     3단계 필터 상속 구조                              │
├─────────────────────────────────────────────────────────────────────┤
│  Level 1: 기본값 (defaults)                                         │
│     ↓ 오버라이드                                                     │
│  Level 2: 카테고리별 설정 (categories)                               │
│     ↓ 오버라이드                                                     │
│  Level 3: 태그별 개별 설정 (tag_overrides)                           │
└─────────────────────────────────────────────────────────────────────┘
```

### 2.2 필터 종류 및 정의

#### 2.2.1 RUN 필터 (`run_only`)

| 항목 | 내용 |
|------|------|
| **목적** | 정상 압연 가동 중 데이터만 분석 |
| **조건** | `OPERATION_STATUS = 'RUN'` |
| **제외 대상** | IDLE (정지), TRANS (전환) 상태 |
| **데이터 영향** | 전체의 약 44.6%만 선택 |
| **적용 태그** | **전체 85개 (100%)** |

**적용 근거**: IDLE 상태의 데이터는 설비 미가동 상태로 분석 의미 없음. RUN 상태에서만 실제 공정 데이터가 유효함.

#### 2.2.2 Special-Ops 필터 (`special_ops`)

| 항목 | 내용 |
|------|------|
| **목적** | 특수 작업 구간 제외 |
| **조건** | `MILL_STATUS = 'RUN'` AND `FURNACE_STATUS = 'HOT'` |
| **제외 대상** | 압연기 비가동, 가열로 저온 상태 |
| **데이터 영향** | 가동 중 데이터의 약 90% 선택 |
| **적용 태그** | **전체 85개 (100%)** |

**적용 근거**: 가열로가 HOT 상태가 아니면 정상 공정이 아님. 압연기가 RUN 상태가 아니면 스탠드 데이터 무의미.

#### 2.2.3 Roll-Change 필터 (`roll_change`)

| 항목 | 내용 |
|------|------|
| **목적** | 롤 교환/롤 직경 변경 시 비정상 데이터 제외 |
| **조건 1** | `OPERATION_STATUS != 'TRANS'` |
| **조건 2** | 속도 변화율 < 50% (`speed_spike_threshold`) |
| **제외 대상** | TRANS 상태, 급격한 속도 변화 구간 |
| **데이터 영향** | 약 11% 추가 제외 |
| **적용 태그** | **64개 (75.3%)** - 스탠드 및 핀치롤 태그만 |

**적용 근거**: 롤 교환 시 스탠드 속도/토크/부하가 급변. 가열로 태그는 열관성으로 롤 교환 영향 없음.

#### 2.2.4 Coiling 필터 (`coiling_transient`)

| 항목 | 내용 |
|------|------|
| **목적** | 권취 가속/감속 구간의 비정상 패턴 제외 |
| **조건** | 속도 변화율 ≤ 5% (`coiling_steady_threshold`) |
| **기준 태그** | `PINCHROLL_2_ACTUAL_SPEED` |
| **제외 대상** | 가속 구간 (COIL_START), 감속 구간 (COIL_END) |
| **데이터 영향** | 권취 중 약 15-25% 제외 |
| **적용 태그** | **18개 (21.2%)** - 핀치롤 태그만 |

**적용 근거**: 권취 시작/종료 시 핀치롤 속도/토크가 급변. 정속 구간만 IQR 분석에 포함해야 정상 패턴 파악 가능.

### 2.3 기본 임계값 설정

```yaml
thresholds:
  speed_spike: 0.5         # 롤 교환 감지: 50% 이상 속도 변화
  coiling_steady: 0.05     # 정속 구간 판정: 5% 이하 변화율
  coiling_window: 5        # 이동평균 윈도우 크기 (초)
```

### 2.4 카테고리별 필터 적용 현황

| 카테고리 | 태그 수 | RUN | Special-Ops | Roll-Change | Coiling | 비고 |
|----------|:------:|:---:|:-----------:|:-----------:|:-------:|------|
| 01_Furnace_Top_Temperature | 4 | ✅ | ✅ | ❌ | ❌ | 열관성으로 롤교환 무관 |
| 02_Furnace_Bottom_Temperature | 4 | ✅ | ✅ | ❌ | ❌ | 열관성으로 롤교환 무관 |
| 03_Furnace_Discharge_Temperature | 1 | ✅ | ✅ | ❌ | ❌ | 압연 전 측정 |
| 04_Furnace_Auxiliary | 10 | ✅ | ✅ | ❌ | ❌ | 독립 시스템 |
| 05_Stand_Torque | 16 | ✅ | ✅ | ✅ | ❌ | 롤교환 시 토크 급변 |
| 06_Stand_Speed | 15 | ✅ | ✅ | ✅ | ❌ | 롤교환 감지 기준 |
| 07_Stand_Load | 15 | ✅ | ✅ | ✅ | ❌ | 토크/속도 함수 |
| 08_Pinchroll | 12 | ✅ | ✅ | ✅ | ✅ | 권취 영향 큼 |
| 09_Cooling_Water | 2 | ✅ | ✅ | ❌ | ❌ | 독립 냉각 시스템 |
| 10_PR_Detailed | 6 | ✅ | ✅ | ✅ | ✅ | 권취 직접 연동 |

### 2.5 필터별 적용 태그 분포

```
RUN 필터:        ████████████████████████████████████████ 85/85 (100%)
Special-Ops:     ████████████████████████████████████████ 85/85 (100%)
Roll-Change:     ██████████████████████████████░░░░░░░░░░ 64/85 (75.3%)
Coiling:         ████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ 18/85 (21.2%)
```

### 2.6 필터 프리셋

| 프리셋 | 설명 | run_only | special_ops | roll_change | coiling_transient |
|--------|------|:--------:|:-----------:|:-----------:|:-----------------:|
| **P0_RAW** | 전체 데이터 (필터 없음) | ❌ | ❌ | ❌ | ❌ |
| **P1_BASIC** | 기본 IQR 분석 (RUN만) | ✅ | ❌ | ❌ | ❌ |
| **P2_OPTIMAL** | 정상 가동 분석 | ✅ | ✅ | ❌ | ❌ |
| **P3_STRICT** | 최고 품질 분석 | ✅ | ✅ | ✅ | ✅ |
| **P4_PER_TAG** | 태그별 최적화 **(권장)** | 태그별 | 태그별 | 태그별 | 태그별 |

---

## 3. A/B 라인(L1/L2) 분류

### 3.1 VCC 권취 영역 이중 라인 구조

VCC(Vertical Coil Collector) 권취 영역은 **이중 라인 구조**로 설계되어 있습니다:

- **Line 1 (L1)**: VCC 권취 라인 1 - 첫 번째 권취 스테이션
- **Line 2 (L2)**: VCC 권취 라인 2 - 두 번째 권취 스테이션

```
┌─────────────────────────────────────────────────────────────────┐
│                    VCC (Variable Cooling Control)               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│    압연 완료 → ┌─────┐ → ┌─────┐ → ┌─────┐ → ┌─────┐          │
│               │ PR6 │   │ PR7 │   │ PR8 │   │ PR9 │          │
│               └──┬──┘   └──┬──┘   └──┬──┘   └──┬──┘          │
│                  │         │         │         │              │
│         ┌───────┴───────┬─┴─────────┴─────────┘              │
│         │               │                                     │
│     ┌───┴───┐       ┌───┴───┐                                │
│     │  L1   │       │  L2   │                                │
│     │ 라인  │       │ 라인  │                                │
│     └───┬───┘       └───┬───┘                                │
│         │               │                                     │
│         ▼               ▼                                     │
│     [코일러1]       [코일러2]                                 │
│                                                               │
└─────────────────────────────────────────────────────────────────┘
```

### 3.2 라인별 태그 분류

#### 3.2.1 L1/L2 모두 수집되는 설비 (완전 구분 가능)

| 설비 | L1 태그 | L2 태그 | 분석 방식 |
|------|---------|---------|-----------|
| **PR6** | PR6L1_ACT_TORQUE | PR6L2_ACT_TORQUE | 독립 IQR |
| **PR7** | PR7L1_ACT_TORQUE | PR7L2_ACT_TORQUE | 독립 IQR |

#### 3.2.2 L1만 수집되는 설비 (부분 구분)

| 설비 | L1 태그 | L2 태그 | 비고 |
|------|---------|---------|------|
| **PR8** | PR8L1_ACT_TORQUE | ❌ 미수집 | L2 데이터 없음 |
| **PR9** | PR9L1_ACT_TORQUE | ❌ 미수집 | L2 데이터 없음 |

### 3.3 L1/L2 분석 시 고려사항

| 항목 | 내용 |
|------|------|
| **독립 분석 필요성** | L1과 L2는 별도의 모터와 제어 시스템을 사용하므로 독립 분석 필수 |
| **시간대별 활성 라인** | L1 가동 시 L2 정지 가능 (교대 운전) |
| **통계 분석 왜곡 방지** | 혼합 분석 시 IQR 범위가 비정상적으로 넓어짐 |
| **0값 필터링** | 비가동 라인의 0값은 분석에서 제외 필요 |

### 3.4 혼합 분석의 문제점 예시

```
[잘못된 혼합 분석]
L1 토크 분포: [10, 15, 20, 25]  → IQR_L1 = 10
L2 토크 분포: [50, 55, 60, 65]  → IQR_L2 = 10
혼합 분포: [10, 15, 20, 25, 50, 55, 60, 65]
→ 혼합 IQR = 40 (실제 각 라인 IQR의 4배!)
→ 정상범위가 비정상적으로 넓어져 이상치 미탐지

[올바른 분리 분석]
L1: 별도 IQR 계산 → 이상치율 정확
L2: 별도 IQR 계산 → 이상치율 정확
```

---

## 4. IQR 분석 방법론

### 4.1 IQR 기반 이상치 탐지 공식

```
Q1 = 25번째 백분위수
Q3 = 75번째 백분위수
IQR = Q3 - Q1

하한 경계 = Q1 - 1.5 × IQR
상한 경계 = Q3 + 1.5 × IQR

이상치: 값 < 하한 경계 OR 값 > 상한 경계
```

### 4.2 시각화 개념도

```
     하한 경계                          상한 경계
         │          정상 범위              │
    ─────┼──────────────────────────────────┼─────
         │    [Q1]────[IQR]────[Q3]        │
    ─────┼──────────────────────────────────┼─────
  이상치 │                                  │ 이상치
```

### 4.3 전역 IQR vs 강종별 IQR

| 방법 | 테이블 | 장점 | 단점 | 적용 상황 |
|------|--------|------|------|----------|
| **전역 IQR** | `iba_tag_iqr_bounds` | 단순, 빠름 | 강종 특성 무시 | 설비 모니터링 |
| **강종별 IQR** | `iba_steel_grade_iqr_bounds` | 정밀, 강종 특성 반영 | 소량 강종 신뢰도↓ | 품질 분석 **(권장)** |

### 4.4 분석 차트 구성

#### 개별 차트 (7개)

| # | 차트 | 파일 접미사 | 설명 |
|---|------|-------------|------|
| 01 | 시계열 | `_01_timeseries.png` | 전체 기간 시계열 |
| 02 | 히스토그램 | `_02_histogram.png` | 값 분포 |
| 03 | 박스플롯 | `_03_boxplot.png` | IQR 시각화 |
| 04 | 일별 평균 추이 | `_04_daily_avg_trend.png` | 일별 평균 변화 |
| 05 | 월별 이상치율 | `_05_monthly_outlier_rate.png` | 월별 이상치율 |
| 06 | 시간대별 히트맵 | `_06_hourly_heatmap.png` | 시간대별 패턴 |
| 07 | 일별 이상치 건수 | `_07_daily_outlier_count.png` | 일별 이상치 수 |

#### 종합 차트 (6패널)

```
┌─────────────────┬─────────────────┐
│ 1. 시계열       │ 2. 히스토그램   │
├─────────────────┼─────────────────┤
│ 3. 박스플롯     │ 4. 일별 추이    │
├─────────────────┼─────────────────┤
│ 5. 월별 이상치  │ 6. 시간대 히트맵│
└─────────────────┴─────────────────┘
```

### 4.5 컨텍스트 인식 분석

운영 상태를 고려한 이상치 판정:

| 상태 | 설명 | 분석 활용 |
|:----:|------|----------|
| `RUN` | 정상 압연 운전 중 | 품질 분석의 핵심 데이터 |
| `TRANS` | 전환 상태 (시작/종료) | 과도 상태 분석 |
| `IDLE` | 대기 상태 | 이상치 분석에서 제외 권장 |

---

## 5. 규격별 IQR 분석

강종 내 사이즈 규격(D10, D13, D16, D20 등)별로 데이터를 분리하여 IQR 분석을 수행합니다. 동일 강종이라도 사이즈에 따라 공정 조건이 달라지므로, 규격별 분리 분석이 더 정밀한 이상치 탐지를 가능하게 합니다.

### 5.1 분석 원리

- 강종 통합 분석에서는 여러 사이즈의 데이터가 혼합되어 IQR 범위가 과대/과소 추정될 수 있음
- 규격별로 분리하면 각 사이즈 고유의 정상 범위를 정확히 파악 가능
- 분석 방법론은 Standard IQR과 동일 (Q1 ± 1.5 × IQR)

### 5.2 출력 구조

각 규격 폴더에 강종 통합 분석과 동일한 구조가 생성됩니다:
- 9개 카테고리 폴더 (01~09)
- 각 카테고리 내 7종 개별 차트 + 종합 6패널 차트
- 월별 차트 (`monthly/{yyyy-mm}/`)
- JSON 결과: `iqr_analysis_{강종}_{규격}_results.json`
- MD 보고서: `IQR_ANALYSIS_REPORT_{강종}_{규격}_KO.md`

### 5.3 실행 방법

```bash
# 특정 강종의 특정 규격만 분석
./venv/bin/python scripts/steel_grade_iqr_analysis_v2.py --grade B5 --size D13

# 특정 강종의 전체 규격 분석
./venv/bin/python scripts/steel_grade_iqr_analysis_v2.py --grade B5 --all-sizes
```

---

## 6. Adjusted IQR (왜도 보정 IQR)

Standard IQR의 **과다 탐지(Over-detection)** 문제를 해결하기 위해, 데이터 분포의 왜도(Skewness)를 반영하여 상한/하한 경계를 비대칭적으로 조정합니다.

### 6.1 분석 원리

Standard IQR은 대칭 분포를 가정하지만, 실제 공정 데이터는 편향된 분포를 가질 수 있습니다.

**Bowley Skewness Correction**:
```
Bowley Skewness = (Q3 + Q1 - 2×Median) / (Q3 - Q1)

양의 왜도 (upper 방향): 상한 경계 확대, 하한 경계 축소
음의 왜도 (lower 방향): 하한 경계 확대, 상한 경계 축소
```

| 파라미터 | 설명 |
|----------|------|
| `c_value` | 왜도 보정 강도 (기본: 강종별 권장값, 일반적으로 0.8) |
| `lower_multiplier` | Skewness 기반 하한 경계 배수 |
| `upper_multiplier` | Skewness 기반 상한 경계 배수 |

### 6.2 출력 파일

- **결과 JSON**: `{강종}/adjusted_iqr_results_{강종}.json`
- **분석 보고서**: `{강종}/ADJUSTED_IQR_ANALYSIS_REPORT_{강종}_KO.md`
- **분석 설계**: `{강종}/ADJUSTED_IQR_PLAN.md`

### 6.3 실행 방법

```bash
# 단일 강종
./venv/bin/python scripts/steel_grade_adjusted_iqr_analysis.py --grade B5

# 왜도 보정 강도 지정
./venv/bin/python scripts/steel_grade_adjusted_iqr_analysis.py --grade B5 --c-value 0.8
```

---

## 7. CUSUM-EWMA 공정 관리도

점진적 **드리프트(drift)** 와 급격한 **시프트(shift)** 를 동시에 탐지하는 통계적 공정 관리(SPC) 방법입니다.

### 7.1 분석 원리

| 방법 | 목적 | 파라미터 | 탐지 대상 |
|------|------|----------|----------|
| **CUSUM** (누적합 관리도) | 중장기 점진적 편차 탐지 | k=0.5σ, h=5.0σ | 서서히 변하는 드리프트 |
| **EWMA** (지수가중이동평균) | 단기 급격한 변화 탐지 | λ=0.2, L=3.0 | 급변하는 시프트 |

**CUSUM 공식**:
```
S⁺(t) = max(0, S⁺(t-1) + (x(t) - μ₀ - k))   # 상향 누적합
S⁻(t) = max(0, S⁻(t-1) - (x(t) - μ₀ + k))   # 하향 누적합
드리프트 판정: S⁺(t) > h 또는 S⁻(t) > h
```

**EWMA 공식**:
```
Z(t) = λ·x(t) + (1-λ)·Z(t-1)
관리 한계 = μ₀ ± L·σ·√(λ/(2-λ))
시프트 판정: Z(t)가 관리 한계 이탈
```

### 7.2 차트 유형

| 차트 | 파일 패턴 | 설명 |
|------|-----------|------|
| CUSUM | `{tag}_cusum.png` | 누적합 그래프 + 드리프트 이벤트 표시 |
| EWMA | `{tag}_ewma.png` | 지수가중 그래프 + 시프트 이벤트 표시 |
| Combined | `{tag}_combined.png` | CUSUM + EWMA 통합 비교 차트 |

### 7.3 실행 방법

```bash
./venv/bin/python scripts/steel_grade_cusum_ewma_analysis.py --grade B5
```

---

## 8. Rolling Z-Score 동적 이상치 분석

시간 윈도우 기반으로 **지역적(local) 기준선**을 추적하며 이상치를 탐지합니다. 평균/분산이 시간에 따라 변하는 비정상(non-stationary) 시계열에 적합합니다.

### 8.1 분석 원리

```
Z_rolling(t) = (x(t) - μ_window(t)) / σ_window(t)
```

| 파라미터 | 기본값 | 설명 |
|----------|--------|------|
| Window | 24시간 | 이동 평균/표준편차 계산 윈도우 |
| Z Threshold | ±3.0σ | 일반 이상치 판정 임계값 |
| Severe Threshold | ±4.0σ | 심각 이상치 판정 임계값 |

Standard IQR이 **전체 기간의 고정 기준**으로 판정하는 반면, Rolling Z-Score는 **직전 24시간의 동적 기준**으로 판정하여 점진적 변화에도 적응합니다.

### 8.2 주요 지표

| 지표 | 설명 |
|------|------|
| `outlier_ratio` | 이상치율 (|Z| > 3σ) |
| `severe_outlier_ratio` | 심각 이상치율 (|Z| > 4σ) |
| `baseline_stability` | 기준선 안정성 (0~1, 높을수록 안정) |
| `max_z` | 최대 Z-스코어 |

### 8.3 차트 유형

- `{tag}_rolling_zscore.png`: 시계열 + 롤링 Z-스코어 + 3σ/4σ 경계선

### 8.4 실행 방법

```bash
# 기본 윈도우 (24시간)
./venv/bin/python scripts/steel_grade_rolling_zscore_analysis.py --grade B5

# 윈도우 크기 지정
./venv/bin/python scripts/steel_grade_rolling_zscore_analysis.py --grade B5 --window 48
```

---

## 9. Mahalanobis 다변량 이상치 분석

**변수 간 상관관계**를 고려하여 **복합 이상치(Multivariate Anomaly)** 를 탐지합니다. 개별 태그로는 정상이지만 태그 조합으로 보면 이상인 경우를 잡아냅니다.

### 9.1 분석 원리

```
D_M(x) = √((x - μ)ᵀ · Σ⁻¹ · (x - μ))
```

| 파라미터 | 값 | 설명 |
|----------|-----|------|
| α (유의수준) | 0.001 | χ² 분포 기반 임계값 |
| Percentile | 99.5% | 대체 백분위수 임계값 |

**분석 단위**: 개별 태그가 아닌 **카테고리 단위** (동일 카테고리 내 태그들의 상관관계 분석)

### 9.2 차트 유형

| 차트 | 파일 패턴 | 설명 |
|------|-----------|------|
| 상관 히트맵 | `{카테고리}_correlation_heatmap.png` | 태그 간 상관계수 시각화 |
| 거리 분포 | `{카테고리}_distance.png` | Mahalanobis 거리 분포 + 이상치 |
| PCA 산점도 | `{카테고리}_pca_scatter.png` | 주성분 2D 공간에서의 이상치 시각화 |

### 9.3 실행 방법

```bash
./venv/bin/python scripts/steel_grade_mahalanobis_analysis.py --grade B5
```

---

## 10. STL 계절-추세 분해 분석

시계열을 **Trend(추세) + Seasonal(계절성) + Residual(잔차)** 로 분해한 뒤, 잔차의 이상치를 탐지합니다. 주기적 패턴이 있는 데이터에서 패턴 외의 이상을 걸러냅니다.

### 10.1 분석 원리

```
X(t) = Trend(t) + Seasonal(t) + Residual(t)

잔차 이상치 = |Residual(t)| > Threshold
```

| 파라미터 | 기본값 | 설명 |
|----------|--------|------|
| seasonal | 25 (시간) | 계절 주기 (일 단위 반복 패턴 가정) |
| robust | True | 강건 추정 (이상치에 덜 민감한 LOESS) |

### 10.2 주요 지표

| 지표 | 설명 |
|------|------|
| `residual_outlier_rate` | 잔차 이상치율 |
| `seasonality_strength` | 계절성 강도 (0~1) |
| `trend_strength` | 추세 강도 (0~1) |
| `seasonality_classification` | 계절성 판정 (strong/moderate/weak/none) |

### 10.3 차트 유형

| 차트 | 파일 패턴 | 설명 |
|------|-----------|------|
| STL 분해 | `{tag}_stl_decomposition.png` | Trend/Seasonal/Residual 3단 분해 |
| 잔차 이상치 | `{tag}_residual_outliers.png` | 잔차 시계열 + 이상치 표시 |

### 10.4 실행 방법

```bash
# 기본 계절 주기 (25시간)
./venv/bin/python scripts/steel_grade_stl_analysis.py --grade B5

# 계절 주기 지정
./venv/bin/python scripts/steel_grade_stl_analysis.py --grade B5 --seasonal 49
```

---

## 11. 분석 방법 비교

### 11.1 방법별 특성 비교

| 방법 | 탐지 대상 | 분석 단위 | 기준선 | 민감도 |
|------|-----------|----------|--------|--------|
| **Standard IQR** | 정적 이상치 | 태그별 | 전체 기간 고정 | 보통 |
| **Adjusted IQR** | 정적 이상치 (왜도 보정) | 태그별 | 전체 기간 고정 (비대칭) | 보통 |
| **CUSUM-EWMA** | 드리프트 + 시프트 | 태그별 | 초기 기준선 | 높음 |
| **Rolling Z-Score** | 동적 이상치 | 태그별 | 24시간 이동 윈도우 | 보수적 |
| **Mahalanobis** | 다변량 복합 이상치 | 카테고리별 | 공분산 행렬 | 보통 |
| **STL Residual** | 계절성 제거 후 이상치 | 태그별 | Trend+Seasonal 분해 | 민감 |

### 11.2 방법별 평균 이상치율 (B5 기준)

```
Standard IQR:    ██████████░░░░░░░░░░  ~10%     (고정 기준)
Adjusted IQR:    ████████░░░░░░░░░░░░  ~8%      (왜도 보정 효과)
Rolling Z-Score: ██░░░░░░░░░░░░░░░░░░  ~1.2%    (매우 보수적)
Mahalanobis:     ████░░░░░░░░░░░░░░░░  ~2.4%    (상관관계 고려)
STL Residual:    ████████████████████  ~20%+    (매우 민감)
CUSUM-EWMA:      ████████████████████  100% drift (공정 불안정 탐지)
```

### 11.3 권장 활용 시나리오

| 시나리오 | 권장 방법 | 이유 |
|----------|-----------|------|
| 일상 모니터링 | Standard IQR | 직관적이고 해석 용이 |
| 편향 분포 태그 | Adjusted IQR | 과다 탐지 방지 |
| 공정 안정성 평가 | CUSUM-EWMA | 점진적/급격한 변화 구분 |
| 실시간 이상 감지 | Rolling Z-Score | 동적 기준선 추적 |
| 설비 간 상관 분석 | Mahalanobis | 복합 이상 탐지 |
| 주기 패턴 분석 | STL Residual | 계절성 제거 후 분석 |

---

## 12. 태그 카테고리별 상세 설명

### 12.1 전체 카테고리 개요

| # | 카테고리 | 태그 수 | 설명 | 설비 위치 |
|---|----------|:-------:|------|----------|
| 01 | Furnace_Top_Temperature | 4 | 가열로 상부 온도 | 상류 (가열로) |
| 02 | Furnace_Bottom_Temperature | 4 | 가열로 하부 온도 | 상류 (가열로) |
| 03 | Furnace_Discharge_Temperature | 1 | 가열로 추출 온도 | 상류 (가열로 출구) |
| 04 | Furnace_Auxiliary | 10 | 가열로 부대설비 | 상류 (가열로) |
| 05 | Stand_Torque | 16 | 스탠드 토크 | 중류 (압연기) |
| 06 | Stand_Speed | 15 | 스탠드 속도 | 중류 (압연기) |
| 07 | Stand_Load | 15 | 스탠드 부하 | 중류 (압연기) |
| 08 | Pinchroll | 12 | 핀치롤 | 하류 (냉각 후) |
| 09 | Cooling_Water | 2 | 냉각수 | 중류 (냉각대) |
| 10 | PR_Detailed | 6 | 핀치롤 상세 (L1/L2) | 하류 (권취 전) |

### 12.2 카테고리별 태그 상세

#### 01_Furnace_Top_Temperature (4개)

| 태그명 | 한글명 | 단위 |
|--------|--------|------|
| HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 가열대 1존 상부 온도 | °C |
| HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 가열대 2존 상부 온도 | °C |
| SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF | 균열대 1존 상부 온도 | °C |
| SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF | 균열대 2존 상부 온도 | °C |

**특성**: 가열로 내부 상부(천정) 영역의 온도. 열관성이 커서 롤 교환/권취 영향 없음.

#### 02_Furnace_Bottom_Temperature (4개)

| 태그명 | 한글명 | 단위 |
|--------|--------|------|
| HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 가열대 1존 하부 온도 (반대측) | °C |
| HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 가열대 2존 하부 온도 (밀측) | °C |
| SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE | 균열대 1존 하부 온도 (반대측) | °C |
| SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE | 균열대 2존 하부 온도 (밀측) | °C |

**특성**: OPP_SIDE는 반대측, MILL_SIDE는 압연기측을 의미.

#### 03_Furnace_Discharge_Temperature (1개)

| 태그명 | 한글명 | 단위 |
|--------|--------|------|
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 가열로 추출 빌렛 온도 | °C |

**특성**: 가열로에서 빌렛이 추출될 때 측정되는 온도. 압연 품질에 직접적 영향.

#### 04_Furnace_Auxiliary (10개)

| 태그명 | 한글명 | 단위 |
|--------|--------|------|
| COMBUSTION_AIR_TEMPERATURE | 연소 공기 온도 | °C |
| FURNACE_O2_ANALYZER | 가열로 산소 분석 | % |
| FURNACE_PRESSURE | 가열로 내부 압력 | Pa |
| INDIRECT_COOLING_WATER_FLOW | 간접 냉각수 유량 | m³/h |
| INDIRECT_WATER_MAIN_TEMPERATURE | 간접 냉각수 주 온도 | °C |
| MAIN_COMBUSTION_AIR_PRESSURE | 주 연소 공기 압력 | kPa |
| MAIN_GAS_FLOW | 주 가스 유량 | Nm³/h |
| MAIN_GAS_PRESSURE | 주 가스 압력 | kPa |
| MAIN_GAS_TEMPERATURE | 주 가스 온도 | °C |
| FURNACE_HYDRAULIC_TANK_OIL_TEMPERATURE | 유압 탱크 오일 온도 | °C |

**특성**: 연소 시스템, 유압 시스템, 배기 시스템 관련. 독립 제어 시스템으로 운영.

#### 05_Stand_Torque (16개)

| 태그명 | 한글명 |
|--------|--------|
| STAND_1_ACTUAL_TORQUE ~ STAND_14_ACTUAL_TORQUE | 스탠드 1~14 실제 토크 |
| FINISHING_BLOCK_MASTER_ACTUAL_TORQUE | 피니싱 블록 마스터 토크 |
| FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE | 피니싱 블록 슬레이브 토크 |

**특성**: 압연 부하의 직접 지표. 롤 교환 시 토크가 급변하므로 Roll-Change 필터 적용.

#### 06_Stand_Speed (15개)

| 태그명 | 한글명 |
|--------|--------|
| STAND_1_ACTUAL_SPEED ~ STAND_14_ACTUAL_SPEED | 스탠드 1~14 실제 속도 |
| FINISHING_BLOCK_ACTUAL_SPEED | 피니싱 블록 속도 |

**특성**: `STAND_1_ACTUAL_SPEED`는 **롤 교환 감지의 기준 태그**로 사용됨.

#### 07_Stand_Load (15개)

| 태그명 | 한글명 |
|--------|--------|
| STAND_1_LOAD ~ STAND_14_LOAD | 스탠드 1~14 부하 |
| FINISHING_BLOCK_LOAD | 피니싱 블록 부하 |

**특성**: 부하(Load) = f(토크, 속도) 관계로 계산됨.

#### 08_Pinchroll (12개)

| 태그명 | 한글명 |
|--------|--------|
| PINCHROLL_2/3/4_ACTUAL_SPEED | 핀치롤 2/3/4 실제 속도 |
| PINCHROLL_2/3/4_ACTUAL_TORQUE | 핀치롤 2/3/4 실제 토크 |
| PINCHROLL_2/3/4_REFERENCE_SPEED | 핀치롤 2/3/4 기준 속도 |
| PINCHROLL_2/3/4_REFERENCE_TORQUE | 핀치롤 2/3/4 기준 토크 |

**특성**: **모든 필터 적용**. 권취기 직전에 위치하여 권취 작업과 직접 연동.

#### 10_PR_Detailed (6개) - L1/L2 라인

| 태그명 | 라인 | 설명 |
|--------|:----:|------|
| PR6L1_ACT_TORQUE | L1 | 핀치롤 6 L1 토크 |
| PR6L2_ACT_TORQUE | L2 | 핀치롤 6 L2 토크 |
| PR7L1_ACT_TORQUE | L1 | 핀치롤 7 L1 토크 |
| PR7L2_ACT_TORQUE | L2 | 핀치롤 7 L2 토크 |
| PR8L1_ACT_TORQUE | L1 | 핀치롤 8 L1 토크 |
| PR9L1_ACT_TORQUE | L1 | 핀치롤 9 L1 토크 |

**특성**: **모든 필터 적용**. PR6~PR9는 하류 핀치롤로 권취기에 가까움.

---

## 13. 위험도 분류 기준

### 13.1 이상치율 기반 위험도

| 등급 | 이상치율 | 의미 | 권장 조치 |
|:----:|:--------:|------|-----------|
| 🔴 **CRITICAL** | ≥25% | 심각한 이상 | 즉시 점검 필요 |
| 🟠 **DANGER** | ≥15% | 높은 위험 | 조속한 점검 권고 |
| 🟡 **WARNING** | ≥10% | 주의 필요 | 모니터링 강화 |
| 🔵 **CAUTION** | ≥5% | 경미한 이상 | 정기 점검 시 확인 |
| 🟢 **NORMAL** | <5% | 정상 범위 | 일반 관리 |

### 13.2 위험도 시각화

```
이상치율 0%      5%       10%      15%      25%      50%
         │       │        │        │        │        │
         ├───────┼────────┼────────┼────────┼────────┤
         │🟢     │🔵      │🟡      │🟠      │🔴      │
         │NORMAL │CAUTION │WARNING │DANGER  │CRITICAL│
         └───────┴────────┴────────┴────────┴────────┘
```

---

## 14. 추가 수집 필요 태그

### 14.1 현재 태그 구조의 취약점

현재 217개 IBA 태그 중 **권취 품질 개선**에 필수적인 다음 영역의 데이터가 **전무**:

| 영역 | 현재 태그 | 커버리지 | 평가 |
|------|:---------:|:--------:|:----:|
| 레잉헤드 (Laying Head) | **0개** | 0% | ❌ 심각 |
| 스텔모어/냉각대 (Stelmor) | **0개** | 0% | ❌ 심각 |
| VCC (권취기) | **0개** | 0% | ❌ 심각 |
| 코일 품질 실적 | **0개** | 0% | ❌ 심각 |

### 14.2 추가 수집 필요 태그 목록

#### 14.2.1 레잉헤드 (Laying Head) - **최우선**

| 우선순위 | 태그명 (권장) | 측정 유형 | 품질 영향도 |
|:--------:|---------------|-----------|-------------|
| ⭐⭐⭐ | `LAYING_HEAD_ACTUAL_SPEED` | 속도(실적) rpm | 루프 직경 결정 |
| ⭐⭐⭐ | `LAYING_HEAD_PIPE_ANGLE` | 각도 ° | 루프 형상 |
| ⭐⭐⭐ | `LAYING_HEAD_EXIT_TEMPERATURE` | 온도 °C | 냉각 시작점 |
| ⭐⭐ | `LAYING_HEAD_MOTOR_TORQUE` | 토크 % | 이상 감지 |

#### 14.2.2 스텔모어/냉각대 (Stelmor) - **최우선**

| 우선순위 | 태그명 (권장) | 측정 유형 | 품질 영향도 |
|:--------:|---------------|-----------|-------------|
| ⭐⭐⭐ | `STELMOR_FAN_1~10_SPEED` | 속도 rpm/% | 냉각속도 제어 |
| ⭐⭐⭐ | `STELMOR_COVER_1~10_POSITION` | 개폐 | 공냉 제어 |
| ⭐⭐⭐ | `STELMOR_ROLLER_SPEED_ZONE_1~10` | 속도 m/min | 루프 간격 |
| ⭐⭐⭐ | `STELMOR_ZONE_TEMPERATURE_1~10` | 온도 °C | 냉각 프로파일 |

#### 14.2.3 VCC (Vertical Coil Collector) - **최우선**

| 우선순위 | 태그명 (권장) | 측정 유형 | 품질 영향도 |
|:--------:|---------------|-----------|-------------|
| ⭐⭐⭐ | `VCC1/2_VERTICAL_POSITION` | 위치 mm | 코일 형상 |
| ⭐⭐⭐ | `VCC1/2_ROTATION_SPEED` | 속도 rpm | 분배 균일성 |
| ⭐⭐⭐ | `VCC1/2_DISTRIBUTOR_POSITION` | 위치 ° | 코일 충전 |
| ⭐⭐ | `VCC_CONTAINMENT_ROLL_POSITION` | 위치 mm | 코일 외경 |

#### 14.2.4 코일 품질 실적 - **필수**

| 우선순위 | 태그명 (권장) | 측정 유형 | 품질 영향도 |
|:--------:|---------------|-----------|-------------|
| ⭐⭐⭐ | `COIL_WEIGHT_ACTUAL` | 무게 kg | 생산 실적 |
| ⭐⭐⭐ | `COIL_OUTER_DIAMETER` | 외경 mm | 형상 품질 |
| ⭐⭐⭐ | `COIL_INNER_DIAMETER` | 내경 mm | 형상 품질 |
| ⭐⭐⭐ | `COIL_HEIGHT` | 높이 mm | 형상 품질 |
| ⭐⭐⭐ | `COIL_LENGTH` | 길이 m | 생산 실적 |

### 14.3 태그 수집 우선순위 Phase

| Phase | 영역 | 추가 태그 수 | 예상 효과 |
|:-----:|------|:------------:|-----------|
| **1** | 레잉헤드, 스텔모어, VCC, 코일품질 | ~40개 | 권취 품질 분석 기반 확보 |
| **2** | 수냉대, 장력제어, 온도측정 | ~20개 | 정밀 분석 역량 강화 |
| **3** | 결속/이송, 품질검사, 에너지 | ~15개 | 스마트 팩토리 고도화 |

### 14.4 추가 태그 수집 시 예상 분석 가능 항목

| 분석 항목 | 현재 | 추가 후 |
|-----------|:----:|:-------:|
| 코일 형상 불량 원인 분석 | ❌ | ✅ |
| 냉각 속도와 재질 특성 상관관계 | ❌ | ✅ |
| 레잉헤드 속도-루프 직경 관계 | ❌ | ✅ |
| VCC 설정-코일 충전 균일성 | ❌ | ✅ |
| 품질 개선 효과 정량 측정 | ❌ | ✅ |

---

## 15. 분석 실행 가이드

### 15.1 스크립트 일람

| # | 스크립트 | 분석 유형 | 주요 옵션 |
|---|---------|----------|-----------|
| 1 | `steel_grade_iqr_analysis_v2.py` | Standard IQR + 규격별 | `--grade`, `--size`, `--all-sizes`, `--filter-preset` |
| 2 | `steel_grade_adjusted_iqr_analysis.py` | Adjusted IQR | `--grade`, `--c-value` |
| 3 | `steel_grade_cusum_ewma_analysis.py` | CUSUM-EWMA | `--grade` |
| 4 | `steel_grade_rolling_zscore_analysis.py` | Rolling Z-Score | `--grade`, `--window` |
| 5 | `steel_grade_mahalanobis_analysis.py` | Mahalanobis | `--grade` |
| 6 | `steel_grade_stl_analysis.py` | STL Residual | `--grade`, `--seasonal` |

모든 스크립트는 `--test` 옵션으로 첫 번째 태그/카테고리만 빠르게 테스트 가능합니다.

### 15.2 전체 분석 일괄 실행

```bash
# 전체 강종에 대해 모든 분석 실행
for grade in B5 D4 D5 N5; do
    echo "=== ${grade} 강종 분석 시작 ==="

    # ① Standard IQR (강종 통합 + 규격별)
    ./venv/bin/python scripts/steel_grade_iqr_analysis_v2.py --grade $grade --all-sizes

    # ② Adjusted IQR
    ./venv/bin/python scripts/steel_grade_adjusted_iqr_analysis.py --grade $grade

    # ③ CUSUM-EWMA
    ./venv/bin/python scripts/steel_grade_cusum_ewma_analysis.py --grade $grade

    # ④ Rolling Z-Score
    ./venv/bin/python scripts/steel_grade_rolling_zscore_analysis.py --grade $grade

    # ⑤ Mahalanobis
    ./venv/bin/python scripts/steel_grade_mahalanobis_analysis.py --grade $grade

    # ⑥ STL Residual
    ./venv/bin/python scripts/steel_grade_stl_analysis.py --grade $grade

    echo "=== ${grade} 완료 ==="
done
```

### 15.3 단일 강종 분석

```bash
# Standard IQR
./venv/bin/python scripts/steel_grade_iqr_analysis_v2.py --grade B5

# 규격별 IQR (특정 규격)
./venv/bin/python scripts/steel_grade_iqr_analysis_v2.py --grade B5 --size D13

# 필터 프리셋 사용
./venv/bin/python scripts/steel_grade_iqr_analysis_v2.py --grade B5 --filter-preset P4_PER_TAG
```

### 15.4 출력 확인

| 출력 유형 | 파일 패턴 | 설명 |
|-----------|-----------|------|
| 종합 차트 | `*_analysis.png` | 6패널 종합 분석 |
| 개별 차트 | `*_01~07.png` | 상세 분석별 차트 |
| JSON 결과 | `*_results.json` | 분석 수치 데이터 |
| MD 보고서 | `*_REPORT_*_KO.md` | 한국어 분석 보고서 |

---

## 16. 부록

### 16.1 제외 태그 목록 (데이터 품질 이슈)

| 태그명 | 제외 사유 |
|--------|-----------|
| ENTRY_MILL_PINCHROLL_ACTUAL_SPEED | ALL_ZEROS - 항상 0값 |
| ENTRY_MILL_PINCHROLL_REFERENCE_SPEED | ALL_ZEROS - 항상 0값 |
| EXIT_FURNACE_RT_SEC_1_ACTUAL_SPEED | LOW_VARIANCE - 변동성 부족 |
| EXIT_FURNACE_RT_SEC_1_REFERENCE_SPEED | LOW_VARIANCE - 변동성 부족 |
| EXIT_FURNACE_RT_SEC_2_ACTUAL_SPEED | LOW_VARIANCE - 변동성 부족 |
| EXIT_FURNACE_RT_SEC_2_REFERENCE_SPEED | LOW_VARIANCE - 변동성 부족 |
| DR01BFZI1_PRESENCE_AT_FURNACE_EXIT_SIDE | ALL_ZEROS - 항상 0값 |
| DR01BFZI2_PRESENCE_AT_DISCHARGING_POSITION_ROLLS_8_9_SEC_1 | ALL_ZEROS - 항상 0값 |
| Y165 | CONSTANT - 상수값 |

### 16.2 용어집

| 용어 | 정의 |
|------|------|
| IQR | 사분위수 범위 (Interquartile Range) = Q3 - Q1 |
| 이상치 | IQR 기준 1.5배 범위를 벗어난 값 |
| 강종 | 강철의 종류/등급 (Steel Grade) |
| VCC | Vertical Coil Collector - 수직형 코일 집적기 |
| 핀치롤 | 철강재를 밀어주는 롤러 |
| 가열대 | 빌렛을 가열하는 구역 (Heating Zone) |
| 균열대 | 온도를 균일하게 하는 구역 (Soaking Zone) |
| 레잉헤드 | 선재를 나선형 루프로 성형하는 설비 |
| 스텔모어 | 선재 공냉 냉각 컨베이어 시스템 |
| CUSUM | Cumulative Sum - 누적합 관리도 |
| EWMA | Exponentially Weighted Moving Average - 지수가중이동평균 |
| STL | Seasonal-Trend decomposition using LOESS |
| Mahalanobis | 공분산을 고려한 다변량 거리 측도 |
| 왜도 | Skewness - 분포의 비대칭 정도 |
| 드리프트 | 공정 평균이 점진적으로 이동하는 현상 |
| 시프트 | 공정 평균이 급격히 변화하는 현상 |

### 16.3 관련 문서

| 문서 | 위치 | 설명 |
|------|------|------|
| 필터 설정 보고서 | `docs/TAG_FILTER_CONFIGURATION_REPORT_KO.md` | 상세 필터 설정 |
| 분석 방법론 | `docs/IBA_DATA_ANALYSIS_METHODOLOGY_KO.md` | 분석 방법론 상세 |
| 태그 상세 목록 | `docs/IBA_태그_상세_목록.md` | 전체 태그 목록 및 추가 수집 필요 태그 |
| 분석 설정 종합 | `docs/IBA_분석설정_종합문서.md` | 종합 설정 문서 |

### 16.4 설정 파일 위치

| 파일 | 경로 | 용도 |
|------|------|------|
| tag_filter_config.yaml | `config/` | 필터 설정 |
| steel_grade_iqr_analysis_v2.py | `scripts/` | Standard IQR 분석 |
| steel_grade_adjusted_iqr_analysis.py | `scripts/` | Adjusted IQR 분석 |
| steel_grade_cusum_ewma_analysis.py | `scripts/` | CUSUM-EWMA 분석 |
| steel_grade_rolling_zscore_analysis.py | `scripts/` | Rolling Z-Score 분석 |
| steel_grade_mahalanobis_analysis.py | `scripts/` | Mahalanobis 분석 |
| steel_grade_stl_analysis.py | `scripts/` | STL Residual 분석 |
| convert_abs_to_rel_paths.py | `scripts/` | JSON 내 절대경로→상대경로 변환 |

---

**문서 이력**
| 버전 | 날짜 | 변경 내용 |
|------|------|-----------|
| 3.0 | 2026-02-06 | 다각적 분석 방법론 6종 추가, 규격별 분석/출력 구조 반영, 실행 가이드 확장 |
| 2.0 | 2026-02-03 | 종합 보고서 작성 - 4개 참조 문서 통합 |

---

*이 문서는 DH Steel IBA 데이터 프로파일링 프로젝트의 공식 참조 문서입니다.*

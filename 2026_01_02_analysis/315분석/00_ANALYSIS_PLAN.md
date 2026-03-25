# 태그-불량 상관관계 분석 프로젝트 계획서

> **프로젝트명**: 3분류 태그 그룹별 품질/불량 상관관계 분석 및 Top-20 핵심 태그 선정
> **작성일**: 2026-03-15
> **데이터 기간**: 2025-03-01 ~ 2025-08-31 (6개월)
> **최종 산출물**: PPTX 보고서용 MD + 차트 세트

---

## 목차

1. [프로젝트 목적 및 범위](#1-프로젝트-목적-및-범위)
2. [데이터 현황 및 제약](#2-데이터-현황-및-제약)
   - [2.5 필터 시스템 통합 설계](#25-필터-시스템-통합-설계)
   - [2.6 강종별/규격별 계층 분석 설계](#26-강종별규격별-계층-분석-설계)
3. [분석 방법론 설계](#3-분석-방법론-설계)
4. [단계별 실행 계획](#4-단계별-실행-계획)
5. [산출물 명세](#5-산출물-명세)
6. [팀플레이 구성](#6-팀플레이-구성)
7. [리스크 및 대응](#7-리스크-및-대응)
8. [결과 해석 기준](#8-결과-해석-기준)
   - [8.4 강종별 해석 원칙](#84-강종별-해석-원칙)
   - [8.5 규격별 해석 원칙](#85-규격별-해석-원칙)
   - [8.6 미채택 기법 향후 로드맵](#86-미채택-기법-향후-로드맵)

---

## 1. 프로젝트 목적 및 범위

### 1.1 핵심 질문 (Research Questions)

| # | 질문 | 측정 방법 |
|---|------|----------|
| Q1 | 3분류 그룹(PLC/현업/AI) 중 어느 태그 그룹이 불량과 가장 깊이 연관되는가? | 그룹별 평균 상관계수 비교 |
| Q2 | 10개 AI 카테고리(Cat01~Cat09b) 중 어느 카테고리가 불량 예측력이 높은가? | 카테고리별 앙상블 점수 |
| Q3 | 불량(권취/중량)과 가장 강한 상관을 보이는 태그 Top-20은 무엇인가? | 6가지 기법 앙상블 순위 |
| Q4 | 고불량일 vs 정상일에 태그 분포가 유의미하게 다른가? | Mann-Whitney U, Cohen's d |
| Q5 | 어떤 태그의 이상치 빈도가 불량 발생일과 시간적으로 선행하는가? | 변점 빈도 × 불량률 Spearman ρ |

### 1.2 분석 범위

| 구분 | 대상 |
|------|------|
| **분석 태그** | Column 3 AI 실행 91개 (DB 적재 기준) + Column 1 PLC 27개 (겹치는 태그 포함) |
| **불량 대상** | 권취불량(`winding_defect_rate`), 중량불량(`weight_defect_rate`), 종합불량(`total_defect_rate` — 파생값: `total_defect_quantity / production_quantity`, DB 컬럼 아님) |
| **강종 구분** | Layer 0 전체 합산 (기본) + Layer 1 강종별 서브분석 (N5: ~41일 ✅, D5: ~21일 ⚠️) + Layer 2 규격별 서브분석 (N5/D5 상위 3규격) |
| **기간** | 2025-03-01 ~ 2025-08-31 (최대 184일 영업일 기준) |
| **제외 태그** | DB 미적재 20개(Column1) + 4개(Column3 PR8/9 L2) + 저분산/상수 제외 9개 → 유효 분석 태그 약 82개 |
| **필터 프리셋** | P4_PER_TAG (카테고리별 최적 자동 적용): Cat01~04 run_only+special_ops / Cat05~07 +roll_change / Cat08~09b +coiling_transient |

---

## 2. 데이터 현황 및 제약

### 2.1 데이터 소스 정리

```
┌────────────────────────────────────────────────────────────────┐
│ ClickHouse: iba_timeseries_unified_alter                      │
│  - 레코드: ~939K건 (초 단위)                                   │
│  - 기간 중 약 15.9M건 추정 (184일 × 86,400초 × 운전율 약 75%) │
│  - 분석 대상 태그: 91개 (RUN 상태 필터링)                       │
│  - ⚠️ steel_grade, size 컬럼 없음 → VIEW 또는 JOIN 필요       │
├────────────────────────────────────────────────────────────────┤
│ ClickHouse VIEW: v_iba_by_steel_grade                         │
│  - iba_timeseries_unified_alter + memo_prod_result JOIN       │
│  - toDate(BASE_TIME) = toDate(production_datetime) 기준       │
│  - 강종(steel_grade), 규격(size) 필터링 가능                    │
│  - ⚠️ 일별 집계 시 중복 없음, 번들 단위 확장 시 주의 (L8)       │
├────────────────────────────────────────────────────────────────┤
│ MariaDB: defect_selection_status                              │
│  - 413건 전체 → 기간 내 약 184건 추정                           │
│  - 키: production_date, steel_grade (SD400/SD500/500N/B500B)  │
│  - 불량률: winding_defect_rate, weight_defect_rate             │
│  - ⚠️ total_defect_rate는 저장값 아님 → 계산 필요              │
├────────────────────────────────────────────────────────────────┤
│ MariaDB: memo_prod_result (ClickHouse MySQL 엔진 경유 접속)    │
│  (필수 — VIEW의 강종/규격 매핑 핵심)                            │
│  - 1,086건 전체 → 기간 내 약 530건 추정                         │
│  - 키: bundle_no, production_datetime, steel_grade, size       │
│  - 역할 1: v_iba_by_steel_grade VIEW의 강종/규격 JOIN 소스     │
│  - 역할 2: weight_error 연속값 프록시 (A3 방안)                 │
└────────────────────────────────────────────────────────────────┘
```

### 2.2 알려진 제약 및 대응 전략

| 한계 | 심각도 | 적용 대응 방안 |
|------|:------:|--------------|
| L1: 일별 집계 vs 초 단위 불일치 | ★★★★★ | IBA → 일별 avg/std/IQR 집계 후 JOIN |
| L2: 강종 코드 불일치 | ★★★★ | A4 매핑 (SD400→D4, SD500→D5, 500N→N5, B500B→B5) |
| L5: 소량 데이터 (~184일) | ★★★★ | Spearman(비모수), LOO-CV, Quantile Regression |
| L7: 클래스 불균형 (불량일 < 20%) | ★★★ | 불량률 연속값 회귀 + 상위 20% 고불량일 분리 |
| L8: VIEW toDate() JOIN 중복 위험 | ★★ | v_iba_by_steel_grade VIEW의 toDate() JOIN → 하루 복수 번들 시 IBA 레코드 중복. 일별 집계에는 무영향, 번들 단위 확장 시 주의 |
| L9: 불량률 저장값 vs 계산값 불일치 | ★ | `winding_defect_rate`, `weight_defect_rate`는 DB에 DECIMAL(5,4) 저장값이 존재하나, `common.py`는 quantity/count로 재계산. 반올림 미세 차이 가능 → **계산값(quantity/count) 일관 사용** |

### 2.3 JOIN 성공률 예측

- 기존 전체 기간 JOIN 성공률: 85.5% (353/413건)
- 2025-03~08 기간은 최신 데이터 → JOIN 성공률 90%+ 예상
- 미조인 날은 분석에서 제외 (NaN 처리)

---

### 2.5 필터 시스템 통합 설계

필터는 `config/tag_filter_config.yaml` 정의 기반이며, `scripts/additional_methods/common.py`에 구현된 함수를 재사용한다.

#### 카테고리별 필터 적용 매트릭스 (P4_PER_TAG 기준)

| 카테고리 | 적용 필터 | 설명 |
|---------|---------|------|
| Cat01~04 (가열로) | `run_only` + `special_ops` | OPERATION_STATUS='RUN' AND MILL_STATUS='RUN' AND FURNACE_STATUS='HOT' |
| Cat05~07 (스탠드) | + `roll_change` | 롤교환 시 속도 급변(>50%) 전후 10초 추가 제외 |
| Cat08~09b (핀치롤·PR상세) | + `roll_change` + `coiling_transient` | 권취 가감속 구간(변화율 >5%) 추가 제외 |

#### 필터별 예상 데이터 감소율

| 필터 | 예상 감소율 | 비고 |
|------|:----------:|------|
| `run_only` | -15~25% | 비가동 시간 (야간·휴무 등) |
| `special_ops` | -추가 5% | 냉간 시동, 로 예열 구간 |
| `roll_change` | -5~10% | 롤교환 전후 과도 구간 |
| `coiling_transient` | -10~20% | 권취 가감속 구간 (Cat08 기준) |
| **P4_PER_TAG 총 누적** | **최대 -45%** | Cat08~09b 적용 시 최대치 |

#### 필터 적용 흐름 (Phase 1 구현)

```
1단계 (SQL): WHERE OPERATION_STATUS = 'RUN'
             AND MILL_STATUS = 'RUN' AND FURNACE_STATUS = 'HOT'
              → ClickHouse 쿼리 레벨에서 적용 (전체 카테고리 공통)

2단계 (DataFrame): Cat05~07 태그에 대해
  → detect_roll_change(df, speed_columns, spike_threshold=0.5) 적용
  → 해당 타임스탬프 행 제거 후 일별 재집계

3단계 (DataFrame): Cat08~09b 태그에 대해
  → detect_roll_change() (2단계와 동일)
  → detect_coiling_transient(df, speed_column, steady_threshold=0.05, window_size=5) 추가 적용
  → 제거 후 일별 재집계
```

#### 제외 태그 9개 (ALL_ZEROS / LOW_VARIANCE / CONSTANT)

분석 쿼리 및 집계에서 **사전 제외**:

| # | 태그명 | 사유 |
|---|--------|------|
| 1 | `ENTRY_MILL_PINCHROLL_ACTUAL_SPEED` | ALL_ZEROS |
| 2 | `ENTRY_MILL_PINCHROLL_REFERENCE_SPEED` | ALL_ZEROS |
| 3 | `EXIT_FURNACE_RT_SEC_1_ACTUAL_SPEED` | LOW_VARIANCE |
| 4 | `EXIT_FURNACE_RT_SEC_1_REFERENCE_SPEED` | LOW_VARIANCE |
| 5 | `EXIT_FURNACE_RT_SEC_2_ACTUAL_SPEED` | LOW_VARIANCE |
| 6 | `EXIT_FURNACE_RT_SEC_2_REFERENCE_SPEED` | LOW_VARIANCE |
| 7 | `DR01BFZI1_*` | CONSTANT |
| 8 | `DR01BFZI2_*` | CONSTANT |
| 9 | `Y165` | ALL_ZEROS |

**저장 추가 파일**: `data/filter_application_stats.json`
```json
{
  "Cat01_Cat04": {"original": 9876, "after_run_only": 7431, "after_special_ops": 7085},
  "Cat05_Cat07": {"after_roll_change": 6743, "removal_rate": 0.317},
  "Cat08_Cat09b": {"after_coiling_transient": 5612, "removal_rate": 0.432}
}
```

---

### 2.6 강종별/규격별 계층 분석 설계

#### 분석 계층 정의

```
Layer 0 (전체 합산)
  → 전 강종 합산 일별 데이터
  → 기본 Top-20 도출 (기준선)
  → ALL 기준 M1~M6 전체 기법 적용

Layer 1 (강종별 독립 분석)
  → N5 (~41일): M1·M2·M3·M4 통계적으로 유효 → Full analysis (M3 LOO-CV 가능)
  → D5 (~21일): M1·M2만 (ML 모델 학습 데이터 부족) → Partial analysis
  → D4 (~6일): 참고용 시각화만 (통계 검정 제외)
  → B5 (~4일): 참고용 시각화만 (통계 검정 제외)

Layer 2 (규격별 서브분석)
  → N5 내 상위 3개 규격 (데이터 건수 기준)
  → D5 내 상위 3개 규격
  → Layer 2는 M1·M2만 적용 (최소 요건 충족 시)
```

#### 데이터 충분성 기준

| 강종 | IBA 건수 | 환산 일수 | Full 분석 | ML 기법 | 통계 검정 |
|------|:-------:|:--------:|:---------:|:-------:|:--------:|
| N5 | 148,239 | ~41일 | ✅ | ✅ | ✅ |
| D5 | 74,855 | ~21일 | 제한적 ⚠️ | ❌ | ✅ |
| D4 | 20,144 | ~6일 | ❌ | ❌ | ❌ |
| B5 | 14,391 | ~4일 | ❌ | ❌ | ❌ |

> 상관 분석 최소 기준: 30일 이상 (권고 50일)

#### 불량 데이터 강종 JOIN 전략

| Layer | IBA 강종 | MariaDB 매핑 조건 |
|-------|---------|-----------------|
| Layer 0 (ALL) | 전체 | WHERE 없음 (전 강종 합산) |
| Layer 1 N5 | N5 | `WHERE steel_grade = '500N'` |
| Layer 1 D5 | D5 | `WHERE steel_grade IN ('SD500', 'SD500S')` |
| Layer 1 D4 | D4 | `WHERE steel_grade = 'SD400'` (참고용) |
| Layer 1 B5 | B5 | `WHERE steel_grade = 'B500B'` (참고용) |
| Layer 2 (규격별) | N5/D5 | + `AND size = '{size}'` (IBA + MariaDB 동시) |

#### 강종별 데이터셋 설정 코드

```python
GRADE_ANALYSIS_CONFIG = {
    'ALL':  {'defect_filter': None,              'min_days': 30, 'full_analysis': True},
    'N5':   {'defect_filter': ['500N'],           'min_days': 30, 'full_analysis': True},
    'D5':   {'defect_filter': ['SD500','SD500S'], 'min_days': 20, 'full_analysis': False},
    'D4':   {'defect_filter': ['SD400'],          'min_days': 0,  'full_analysis': False, 'viz_only': True},
    'B5':   {'defect_filter': ['B500B'],          'min_days': 0,  'full_analysis': False, 'viz_only': True},
}

SIZE_ANALYSIS_GRADES = ['N5', 'D5']
TOP_N_SIZES = 3  # 강종당 데이터 많은 상위 3개 규격
```

---

## 3. 분석 방법론 설계

### 3.1 6가지 상관 측정 기법

각 기법은 독립적으로 순위를 산출하고, 최종 앙상블 순위를 통해 Top-20을 선정한다.

#### 6가지 기법 종합 비교표

| 기법 | 분류 | 핵심 질문 | 측정 지표 | 강점 | 한계 | 가중치 |
|------|------|----------|----------|------|------|:------:|
| **M1** Spearman ρ | 단변량 상관 | "이 태그의 일별 통계가 불량률과 함께 움직이는가?" | \|ρ\| + Bonferroni p-value | 비모수, 이상치 강건, 해석 용이 | 비선형·상호작용 미포착 | 0.25 |
| **M2** Mann-Whitney + Cohen's d | 그룹 비교 | "고불량일에 이 태그의 분포가 정상일과 다른가?" | Cohen's d (효과 크기) | 분포 형태 비교, 소량 데이터 적합 | 임계값(상위20%) 의존 | 0.20 |
| **M3** LightGBM FI | ML 회귀 | "다수 태그를 동시 고려할 때 불량률 예측에 가장 기여하는 태그는?" | gain 기반 Feature Importance | 비선형·상호작용 포착, 예측력 기반 | 과적합 위험, 해석 난이도 | 0.25 |
| **M4** Quantile Reg Q90 | 극단값 회귀 | "고불량 극단 이벤트(상위 10%)를 설명하는 태그는?" | \|회귀 계수\| (표준화) | 극단 꼬리 민감, 평균 왜곡 무관 | 선형 가정, 소량 데이터 | 0.15 |
| **M5** IQR 이상치 교차 | 이상치-불량 연관 | "이 태그에 이상치가 발생한 날이 고불량일과 겹치는가?" | Fisher's Exact OR + Spearman ρ | 기존 6기법 분석 재활용, 직관적 | IQR 경계 의존, 단일 태그 | 0.10 |
| **M6** PELT 변점 빈도 | 시계열 구조 변화 | "이 태그의 공정 상태 전환 빈도가 불량 증가와 관련되는가?" | Spearman ρ (변점수 vs 불량률) | 시계열 구조 포착, 공정 불안정 감지 | 파라미터 민감, 보조 지표 | 0.05 |

> **설계 철학**: M1~M2는 **통계적 관점** (개별 태그의 직접 상관), M3~M4는 **모델링 관점** (다수 태그 동시 고려), M5~M6는 **패턴 관점** (이상치·변점 기반 교차 검증). 세 관점을 앙상블하여 단일 기법의 편향을 보정한다.

#### M1. Spearman 순위 상관계수 (기본 기법)

```
대상: 일별 태그 통계 × 일별 불량률 (전체 기간)
지표: ρ (rho) + p-value (Bonferroni 보정)
변수: avg, std, max 각각 계산 → 가장 큰 |ρ| 채택
해석: |ρ| ≥ 0.30 = 의미 있는 상관
참조: DEFECT_DATA_UTILIZATION_STRATEGY.md C4
```

**왜 Spearman인가 (Pearson이 아닌 이유)**:
- **비모수적**: 불량률 분포가 정규분포를 따르지 않음 (0에 밀집, 우측 꼬리 긴 분포). Pearson은 정규성 가정 위반 시 왜곡됨.
- **이상치 강건성**: 순위 변환으로 극단 불량일의 영향을 완화. 철강 공정에서 설비 사고일 같은 이상치가 상관계수를 왜곡하는 것을 방지.
- **단조 비선형 포착**: Pearson은 선형 관계만 측정하지만, Spearman은 "온도 올라가면 불량도 올라간다" 같은 단조적 비선형 관계도 감지.
- **소량 데이터 적합**: ~166일 데이터에서 모수적 가정을 피하는 것이 통계적으로 안전.

**공정적 해석 가이드**:
- ρ > 0 (양의 상관): 태그 값 증가 → 불량률 증가 (예: 가열로 온도 과다 → 표면 불량)
- ρ < 0 (음의 상관): 태그 값 감소 → 불량률 증가 (예: 핀치롤 속도 저하 → 권취 불량)
- `_avg`와 높은 ρ: **수준(level) 자체**가 불량과 관련 (공정 설정값 문제)
- `_std`와 높은 ρ: **변동성(variability)**이 불량과 관련 (공정 불안정 문제)
- `_max`와 높은 ρ: **극단 이벤트(spike)**가 불량과 관련 (순간 이상 문제)

**기존 분석 기반 기대값** (analyze_defect_correlation.py, comprehensive_defect_analysis.py 결과 참조):
- 기존 Pearson 상관에서 |r| 최대 ~0.18 (STAND_1_ACTUAL_SPEED). Spearman 비모수 전환 시 **|ρ| 0.20~0.35 범위로 상승** 기대 (분포 왜곡 보정 효과).
- 기존 Lag 상관 분석에서 1~3일 시차 효과 확인됨. 본 분석은 **동일일(Lag 0) 상관**에 집중하되, 유의미한 결과 부족 시 Lag 1~3 확장 옵션 보유.
- 기존 분석은 전체 강종 합산만 수행 → **강종별 분리(Layer 1) 시 |ρ| 상승** 기대 (강종 간 잡음 제거).

**한계 및 보완**: 비선형 상호작용(예: "온도 × 속도 조합")은 포착 불가 → M3(LightGBM)이 보완.

- **불량 라벨 3종**: `winding_defect_rate`, `weight_defect_rate`, `total_defect_rate`
- **통계량 3종**: `_avg`, `_std`, `_max` (태그당 9가지 조합 → 최대 |ρ| 채택)
- **보정**: Bonferroni 보정 (82 유효 태그 × 3 불량 → α = 0.05/246 = 0.000203)

#### M2. Mann-Whitney U + Cohen's d (고불량일 vs 정상일 프로파일)

```
대상: 불량률 상위 20%일(고불량) vs 하위 80%(정상)
지표: U 통계량, p-value, Cohen's d (효과 크기)
해석: |d| ≥ 0.50 = 중간 효과, |d| ≥ 0.80 = 큰 효과
참조: DEFECT_DATA_UTILIZATION_STRATEGY.md C4
```

**M1과의 차별점 — 왜 별도 기법이 필요한가**:
- M1(Spearman)은 **연속적 추세**를 봄: "불량률이 1%→2%→3%로 올라갈 때 태그도 같이 변하나?"
- M2는 **이진 프로파일 차이**를 봄: "고불량일의 태그 분포가 정상일과 통째로 다른가?"
- M1에서 ρ=0이지만 M2에서 d≥0.8인 경우: **임계값 효과** (특정 수준 이상에서만 불량 급증)를 의미하며, 이는 알람 임계값 설정에 직결됨.

**왜 Mann-Whitney U (t-test가 아닌 이유)**:
- 고불량일(~33건)과 정상일(~133건) 간 **표본 크기 불균형**이 크므로 등분산 가정이 위험.
- 태그 값 분포가 **비정규**인 경우가 많음 (온도는 정규에 가깝지만, 전류·토크는 0 근처 밀집+급등 분포).
- Mann-Whitney U는 **순위 기반**이므로 분포 가정 불요, 이상치에 강건.

**왜 Cohen's d (p-value만으로 부족한 이유)**:
- p-value는 **"차이가 존재하는가"** (유/무)만 답변.
- Cohen's d는 **"차이가 얼마나 큰가"** (크기)를 답변 → 166건 소량 데이터에서 p-value는 유의하지 않아도 d≥0.5면 실질적 차이 존재.
- 공정 관리에서는 **통계적 유의성**보다 **실무적 효과 크기**가 중요.

**공정적 해석 가이드**:
- |d| ≥ 0.80 + p < 0.05: **확정 알람 태그** — 고불량일에 명확히 다른 수준/변동
- |d| ≥ 0.50 + p ≥ 0.05: **주의 태그** — 실질 차이 있으나 데이터 부족으로 유의성 미달 → 데이터 축적 시 재확인
- |d| < 0.20: **무관 태그** — 고불량일과 정상일에 동일 분포

- 고불량일: `winding_defect_rate` 상위 20% (권취 불량 집중)
- 별도: `weight_defect_rate` 상위 20% (중량 불량 집중)
- 순위 기준: Cohen's d 절댓값

#### M3. Gradient Boosting Regressor + Feature Importance (불량률 회귀)

```
대상: 유효 태그 × 일별 통계 → total_defect_rate 예측
      ⚠️ [F4] 분석 대상 태그 수는 get_available_columns() 결과에서 제외 태그 9개와
      비센서 컬럼(BASE_TIME, OPERATION_STATUS 등)을 뺀 동적 값 사용 (약 82개)
지표: gain 기반 feature importance (정규화)
검증: LeaveOneOut CV (소량 데이터 대응)
참조: DEFECT_DATA_UTILIZATION_STRATEGY.md B2
```

**M1/M2와의 핵심 차별점 — 왜 ML이 필요한가**:
- M1/M2는 **단변량 분석**: 태그 하나씩 독립적으로 불량과의 관계를 봄.
- M3는 **다변량 분석**: 82개 태그를 동시에 고려하여, **태그 간 상호작용 효과**를 포착.
- 예: "가열로 온도(Cat03)가 높고 + 스탠드 속도(Cat06)가 낮을 때" 불량 급증 — M1은 이런 조합 효과를 감지 못하지만 M3는 트리 분기로 자연스럽게 포착.

**왜 LightGBM (sklearn GBR이 아닌 이유)**:
- **속도**: 82 feature × 166 샘플에서도 LOO-CV(166회 학습)를 합리적 시간 내 완료.
- **범주형 처리**: 향후 강종/규격 변수 추가 시 원-핫 인코딩 불요.
- **과적합 제어**: `max_depth=4, num_leaves=16, min_child_samples=8`로 166건 데이터에 맞춰 트리 복잡도를 강하게 제한.

**왜 LOO-CV (K-Fold가 아닌 이유)**:
- 166건 데이터에서 5-Fold = Fold당 33건 → 학습 데이터 133건으로 충분하지만, **검증 데이터가 33건뿐**이라 분산이 큼.
- LOO-CV: 매번 165건 학습 + 1건 검증 → **최대 학습 데이터 활용** + **편향 최소** (소량 데이터에 최적).
- 단점: 분산이 다소 높지만, 166회 평균이므로 안정적.

**Feature Importance 해석 주의점**:
- **gain 기반**: 해당 feature로 분기할 때 얻는 손실 감소량 합계 → 예측력에 대한 직접 기여도.
- **주의**: 상관된 태그(예: Cat06 스탠드 속도 ACTUAL vs REFERENCE)가 있으면 importance가 분산됨 → 카테고리별 합산 보완 필요.
- **split 기반과의 차이**: split 기반은 "얼마나 자주 사용됐는지"이므로 연속값 태그에 편향 → gain이 더 신뢰성 높음.

**공정적 해석 가이드**:
- FI 상위 태그가 M1에서도 상위 → **강건한 핵심 태그** (단변량+다변량 모두 중요)
- FI 상위이나 M1에서 하위 → **상호작용 효과 태그** (단독으로는 약하지만 조합 시 강력) → 공정 간 연계 모니터링 필요
- M3a(종합)와 M3b(권취) 순위 비교 → 불량 유형별 핵심 태그 차이 파악

- 모델: `LightGBM` (n_estimators=200, max_depth=4, num_leaves=16)
- 두 번 실행:
  - M3a: `total_defect_rate` (종합)
  - M3b: `winding_defect_rate` (권취 집중)

#### M4. Quantile Regression (Q90 — 고불량 구간 예측)

```
대상: 일별 태그 통계 → total_defect_rate Q90 예측
지표: |회귀 계수| (표준화 후)
해석: Q90 회귀 계수 큰 태그 = 고불량 이벤트 기여 태그
참조: DEFECT_DATA_UTILIZATION_STRATEGY.md E3 (확장 기법)
```

**M3(LightGBM)와의 핵심 차별점 — 왜 별도 회귀가 필요한가**:
- M3(LightGBM)는 **평균(mean) 예측**: "태그 값이 이러면 불량률이 평균적으로 몇 %인가?"
- M4(Quantile Q90)는 **상위 꼬리(tail) 예측**: "태그 값이 이러면 불량률이 상위 10%까지 얼마나 올라갈 수 있는가?"
- **핵심 통찰**: 불량은 **극단 이벤트**. 평균적으로 불량률 1%인 날에도 상위 10%에서는 5% 이상 발생 가능. M4는 이 극단 구간의 기여 태그를 식별.

**왜 Q90 (Q50이나 Q75가 아닌 이유)**:
- Q50 ≈ 중앙값 회귀 → M3(평균 회귀)와 유사한 결과
- Q75: 약한 극단 → 일반적인 "나쁜 날" 수준
- **Q90**: "10일에 1일 발생하는 고불량 이벤트" 수준 → 공정 관리 알람 임계값에 직접 대응
- Q95 이상: 166건 중 상위 8건 → 추정 불안정

**왜 선형 Quantile Regression (LightGBM Quantile이 아닌 이유)**:
- 166건 데이터에서 **선형 모델의 회귀 계수**가 직접 해석 가능 (태그당 기여도 = 계수 크기).
- LightGBM Quantile은 비선형이지만 해석이 FI에 의존 → M3와 중복.
- 선형 + 표준화 → 계수 크기가 곧 **태그 간 상대적 기여도** → 공정 엔지니어에게 설명 용이.

**공정적 해석 가이드**:
- Q90 계수 > 0 큰 태그: 해당 태그 값이 **상승하면 극단 불량일 확률 증가** → 상한 알람 설정 대상
- Q90 계수 < 0 큰 태그: 해당 태그 값이 **하강하면 극단 불량일 확률 증가** → 하한 알람 설정 대상
- M3 FI 상위이나 M4 계수 낮음 → 평균적으로 중요하나 극단 이벤트와 무관 (일상 관리용)
- M4 계수 높으나 M3 FI 하위 → 평소에는 조용하나 극단 사건 시 핵심 원인 (비상 감시 대상)

- `QuantileRegressor(quantile=0.90)` from sklearn
- 태그 표준화 후 계수 비교

#### M5. IQR 이상치 빈도 × 고불량일 교차 (이상치-우선)

```
대상: 일별 IQR 이상치 발생 여부 × 고불량일 여부
지표: Fisher's Exact OR + Spearman(이상치 수 vs 불량률)
해석: OR > 2.0 & p < 0.05 = 불량과 연관된 이상치 태그
참조: DEFECT_DATA_UTILIZATION_STRATEGY.md B1
```

**M1~M4와의 핵심 차별점 — 왜 이상치 관점이 필요한가**:
- M1~M4는 **일별 집계 통계**(avg, std, max)를 입력으로 사용 — 즉, 하루의 "평균적 상태"를 봄.
- M5는 **초 단위 원본 데이터의 이상치 발생 빈도**를 사용 — "하루 중 몇 %의 시점에서 비정상적인 값이 나왔는가"를 봄.
- **핵심 통찰**: 일평균은 정상 범위이지만 **짧은 시간 동안 극단값이 빈발**한 경우가 불량 원인일 수 있음 (예: 핀치롤 순간 과부하 → 권취 불량). M5만이 이 패턴을 포착.

**기존 분석 자산 활용 (부분적)**:
- 본 프로젝트 이전에 6가지 이상치 탐지 기법(IQR, Adjusted IQR, CUSUM/EWMA, Rolling Z, Mahalanobis, Context-Aware)이 이미 수행됨.
- ⚠️ [F5] 그러나 기존 출력(`detailed_iqr_analysis_v2_results.json` 등)은 **전체 기간 합산** 이상치 통계만 제공.
  **"태그별 × 날짜별 이상치 발생 여부"** 데이터는 기존 출력에서 바로 사용 불가.
- **해결**: Phase 1 Step 1-1에서 일별 집계 시 산출하는 `outlier_ratio` 컬럼이 M5 입력 데이터 역할을 수행.
  (IQR Fence 기준 초과 비율을 날짜별로 신규 집계)
- M5는 이 일별 이상치 빈도를 불량 데이터와 교차하여, **"어떤 태그의 이상치가 불량과 연관되는가"**를 검증.

**Fisher's Exact Test와 Odds Ratio 해석**:
- 2×2 분할표: (이상치 유/무) × (고불량일 유/무)
- **OR = 1.0**: 이상치와 불량 무관 (우연 수준)
- **OR = 2.0**: 이상치 발생일에 고불량일 확률이 **2배** → 의미 있는 연관
- **OR ≥ 5.0**: 매우 강한 연관 → 최우선 알람 태그 후보
- Fisher's Exact: 소량 데이터(기대빈도 < 5)에서도 정확한 p-value 제공 (χ² 검정보다 적합)

**공정적 해석 가이드**:
- OR 높고 + Spearman(이상치 수 vs 불량률)도 높음 → **이상치 빈도 자체가 불량 강도와 비례** → 이상치 건수 기반 알람 유효
- OR 높지만 + Spearman 낮음 → 이상치 **유무**는 중요하나 건수는 무관 → 이진 알람(있다/없다)만 의미

- IQR 경계: 학습 기간 전체 Q1-1.5IQR, Q3+1.5IQR 로 계산
- 일별 이상치 횟수 (초 단위 데이터 중 이상치 비율)

#### M6. PELT 변점 빈도 × 불량률 상관 (변점 탐지)

```
대상: 일별 태그 시계열에서 변점 탐지 → 빈도 × 불량률
지표: Spearman ρ (변점 빈도 vs 불량률)
해석: 변점 빈발 = 공정 불안정 = 불량 증가 가설 검증
참조: DEFECT_DATA_UTILIZATION_STRATEGY.md C3, E2
```

**M1~M5와의 핵심 차별점 — 왜 변점 관점이 필요한가**:
- M1~M5는 **태그 값의 크기(수준, 분포, 이상치)**를 봄 — "얼마나 높은가/낮은가"
- M6는 **시계열의 구조적 변화(regime shift)**를 봄 — "언제 공정 상태가 전환됐는가"
- **핵심 가설**: 불량은 공정이 **안정 상태에서 벗어나는 과도 구간**(전환기)에 집중 발생.
  예: 롤교환 후 재설정, 강종 변경 시 온도 전환, 설비 간헐적 이상 → 이런 "전환"의 빈도가 높은 날일수록 불량 증가.

**PELT 알고리즘 설명 (Pruned Exact Linear Time)**:
- **원리**: 시계열을 복수의 구간(segment)으로 분할하여, 각 구간 내 통계 특성이 최대한 균일하도록 최적 분할점(changepoint)을 찾음.
- **장점**: 변점 개수를 사전에 지정할 필요 없음 (penalty 파라미터로 자동 결정).
- **시간복잡도**: O(n) — 일별 통계 166일 데이터에 수 밀리초 이내 완료.

**왜 RBF 커널 (linear이 아닌 이유)**:
- `model="rbf"` (Radial Basis Function): 평균 변화 + 분산 변화 + 비선형 변화를 모두 감지.
- `model="l2"` (linear): 평균 변화만 감지 → 분산 변화를 놓침 (공정에서 "수준은 같지만 변동이 커진" 불안정 구간을 놓침).
- 철강 공정에서 "온도 수준은 유지되나 변동폭이 커지는" 패턴이 불량과 관련 → RBF가 적합.

**슬라이딩 7일 윈도우 근거**:
- 주간 단위 공정 패턴(주말 감속/월요일 재시동) 고려.
- 7일 미만: 일간 노이즈에 민감 / 14일 이상: 단기 불안정 구간 희석.
- 각 날짜의 "7일 윈도우 내 변점 수"를 집계 → 불량률과 Spearman ρ 계산.

**⚠️ [F6] PELT 최소 데이터 요건 및 대안 경로**:
- PELT RBF 커널은 최소 ~50점 이상 권장. Layer 0 ALL(~166일) ✅, N5(~41일) ⚠️ 경계, D5(~21일) ❌ 부족.
- **대안**: 기존 CUSUM/EWMA 변점 결과(`analysis_output/steel_grade_iqr_analysis_v2/cusum_ewma/`)를
  일별 변점 빈도로 집계하여 활용 가능. PELT 신규 적용 대비 **초 단위 데이터 기반이므로 정보량 우위**.
- Layer 1(N5/D5)에서는 PELT 대신 기존 CUSUM/EWMA 일별 빈도 집계를 우선 사용 권장.

**공정적 해석 가이드**:
- ρ > 0.3: "변점이 잦은 주간에 불량이 많다" → **공정 안정성 관리가 품질 핵심**
- 특정 카테고리(예: Cat05~07 스탠드)에서만 높은 ρ → 해당 공정의 전환 관리 강화 필요
- 전체적으로 ρ ≈ 0: 변점과 불량이 무관 → 불량 원인이 수준(level) 문제이지 불안정(instability) 문제가 아님

**한계 및 보조 지표 역할**:
- penalty 파라미터 선택에 민감 (과소검출 ↔ 과다검출 트레이드오프).
- 일별 집계 시계열(166점)에서 변점 탐지는 해상도 한계 → **보조 지표(가중치 0.05)**로 활용.

- `ruptures.Pelt(model="rbf")` 적용 (일별 통계 시계열 대상)
- 슬라이딩 7일 윈도우 내 변점 수

### 3.2 앙상블 순위 통합

**왜 앙상블인가 (단일 기법 순위로 부족한 이유)**:
- **기법별 편향 보정**: M1(Spearman)은 단조 관계에 강하지만 상호작용을 놓치고, M3(LightGBM)은 상호작용에 강하지만 과적합 위험. 여러 관점을 결합하면 각 기법의 약점이 상쇄됨.
- **강건성(robustness)**: 6개 기법 중 4개 이상에서 Top-30에 드는 태그는 **관점에 무관하게 중요** → 우연이 아닌 실질적 상관.
- **가중치 설계 근거**: 직접 상관(M1) 0.25 + 예측력(M3) 0.25 = 50% (핵심), 프로파일(M2) 0.20 + 극단값(M4) 0.15 = 35% (보완), 이상치(M5) 0.10 + 변점(M6) 0.05 = 15% (검증).

```
최종 점수 계산:
  rank_i (M1) = Spearman |ρ| 기준 순위
  rank_i (M2) = Cohen's d 기준 순위
  rank_i (M3) = Feature Importance 기준 순위
  rank_i (M4) = Quantile 계수 기준 순위
  rank_i (M5) = OR + Spearman ρ 평균 기준 순위
  rank_i (M6) = Spearman ρ 기준 순위

  ensemble_score_i = Σ (w_k × rank_i(Mk)) / Σ w_k
  가중치: w = [0.25, 0.20, 0.25, 0.15, 0.10, 0.05]
          (M1=Spearman이 가장 신뢰, M6=변점이 보조)

  최종 순위 = ensemble_score 오름차순 (낮을수록 높은 순위)
```

### 3.3 그룹별 집계

```
그룹 단위 점수:
  group_score(G) = mean(ensemble_score of tags in G)
  group_top_tag(G) = min(ensemble_score of tags in G)

대상 그룹:
  [3분류] Column1(PLC) / Column2-매핑가능(현업) / Column3(AI)
  [카테고리] Cat01~Cat04(가열로) / Cat05~Cat07(스탠드) /
             Cat08(핀치롤) / Cat09(냉각수) / Cat09b(PR상세)
```

---

## 4. 단계별 실행 계획

### Phase 0: 환경 준비 (사전 확인)

```
목표: ClickHouse/MariaDB 접속 확인 + 기간 내 데이터 존재 여부 검증
소요: 0.5일
```

**체크리스트**:
- [ ] ClickHouse: `iba_timeseries_unified_alter` 기간 내 레코드 수 확인
- [ ] MariaDB: `defect_selection_status` 2025-03~08 레코드 수 확인
- [ ] 기간 내 결측 날짜 파악 (공장 휴무일 등)
- [ ] 91개 분석 대상 태그 컬럼명 최종 확인 (Null 비율 체크)
- [ ] Python 패키지 설치 확인: `lightgbm`, `ruptures`, `scikit-learn` (≥1.1, QuantileRegressor), `scipy`

**검증 쿼리**:
```sql
-- ClickHouse: 기간 내 일별 레코드 수
SELECT
    toDate(BASE_TIME) as dt,
    count() as n_records,
    countIf(OPERATION_STATUS = 'RUN') as n_run
FROM iba_timeseries_unified_alter
WHERE BASE_TIME >= '2025-03-01' AND BASE_TIME < '2025-09-01'
GROUP BY dt
ORDER BY dt;

-- MariaDB: 기간 내 불량 데이터
SELECT
    production_date,
    steel_grade,
    winding_defect_rate,
    weight_defect_rate,
    -- total_defect_rate는 저장 컬럼이 아님 → 계산 필요
    (winding_defect_quantity + weight_defect_quantity)
        / NULLIF(production_quantity, 0) AS total_defect_rate
FROM defect_selection_status
WHERE production_date >= '2025-03-01'
  AND production_date < '2025-09-01'
ORDER BY production_date;
```

> **⚠️ [A2] MariaDB 접속 경로**: `common.py`에서 MariaDB 테이블(`defect_selection_status`, `memo_prod_result`)을
> **ClickHouse MySQL 엔진 경유**로 접근합니다 (`client: Client`가 ClickHouse 클라이언트).
> Phase 0 검증 쿼리도 ClickHouse 클라이언트로 실행하면 됩니다 (`common.py`의 `get_client()` 패턴 따르기).

---

### Phase 1: 데이터 추출 및 전처리 (Script 01)

```
파일: scripts/01_data_extraction.py
목표: 일별 태그 통계 + 불량 데이터 JOIN → 분석용 parquet 생성
소요: 1일
```

**Step 1-1: IBA 일별 집계 (ClickHouse) — 카테고리별 필터 적용**
```
집계 단위: 1일
필터 전략 (P4_PER_TAG 프리셋):
  ① SQL WHERE: OPERATION_STATUS='RUN' AND MILL_STATUS='RUN' AND FURNACE_STATUS='HOT'
     → 전체 카테고리 공통 적용 (ClickHouse 쿼리 레벨)
  ② DataFrame 후처리: Cat05~07 → detect_roll_change() 적용 후 재집계
  ③ DataFrame 후처리: Cat08~09b → detect_roll_change() + detect_coiling_transient() 적용 후 재집계
  ④ 사전 제외: 제외 태그 9개는 쿼리에서 컬럼 제외

태그별 산출 통계:
  - avg, std, min, max, median (approx_percentile 0.50)
  - IQR (approx_percentile 0.75 - 0.25)
  - 이상치 비율: IQR Fence 기준 초과 비율  ← ⚠️ [F5] M5 입력 데이터로 직접 사용됨
    (기존 IQR 분석 출력은 전체 기간 합산이므로, 일별 이상치 비율은 여기서 신규 집계 필요)
  - CV (coefficient of variation = std/avg)
집계 결과: 184일 × ~82태그(유효) × 8통계 = ~120K 값
필터 통계 저장: filter_application_stats.json (카테고리별 제거 건수 기록)

common.py 재사용 함수 (scripts/additional_methods/common.py):
  - get_client()                  : ClickHouse/MariaDB 클라이언트 생성
  - get_available_columns()       : 테이블 내 존재하는 태그 컬럼명 조회
  - fetch_timeseries_data()       : IBA 시계열 데이터 추출 (필터 적용)
  - fetch_daily_defect_rates()    : MariaDB 일별 불량률 조회
    ⚠️ [F1] grade 파라미터가 SQL WHERE에 미반영 → 전체 합산만 반환. 강종별 분석 시 수정 필요.
  - fetch_iba_daily_stats()       : ⚠️ [F3] 미구현 — 신규 작성 필요. 구현 가이드:
    (방안1) v_iba_by_steel_grade VIEW에서 일별 avg/std/max 직접 집계 (권장):
      SELECT toDate(BASE_TIME) AS dt, avg({tag}) AS {tag}_avg, stddevPop({tag}) AS {tag}_std, ...
      FROM v_iba_by_steel_grade
      WHERE BASE_TIME >= ... AND steel_grade = '{grade}' [AND size = '{size}']
      GROUP BY dt ORDER BY dt
    (방안2) 기존 fetch_tag_group_data() 호출 → pandas df.groupby(df['BASE_TIME'].dt.date).agg() 변환
      (초 단위 → 일별 집계. 간단하지만 대량 데이터 전송으로 느림)
  - detect_roll_change()          : 롤교환 구간 감지 (Cat05~07)
  - detect_coiling_transient()    : 권취 과도 구간 감지 (Cat08~09b)
  - save_results()                : 분석 결과 CSV/JSON 저장
  - save_figure()                 : 차트 PNG 저장 (DPI/크기 표준화)
```

```sql
-- ClickHouse: 일별 태그 통계 집계 (예시: 단일 태그)
SELECT
    toDate(BASE_TIME) as dt,
    -- 태그별 통계 (91개 반복)
    avg(FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE) as furnace_temp_avg,
    stddevPop(FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE) as furnace_temp_std,
    min(FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE) as furnace_temp_min,
    max(FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE) as furnace_temp_max,
    quantile(0.25)(FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE) as furnace_temp_q25,
    quantile(0.75)(FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE) as furnace_temp_q75,
    -- ... (91개 태그 동일하게)
FROM iba_timeseries_unified_alter
WHERE BASE_TIME >= '2025-03-01'
  AND BASE_TIME < '2025-09-01'
  AND OPERATION_STATUS = 'RUN'
GROUP BY dt
ORDER BY dt;
```

> **⚠️ 강종별 조회 시**: `iba_timeseries_unified_alter` 테이블에는 `steel_grade`, `size` 컬럼이 없음.
> 강종/규격 필터링이 필요한 경우 `v_iba_by_steel_grade` VIEW를 사용하거나,
> `memo_prod_result` 테이블과 `toDate(BASE_TIME)` 기준 JOIN을 수행해야 함.

**Step 1-2: 불량 데이터 추출 + 강종 매핑 (MariaDB)**
```python
# A4: 강종 코드 매핑
STEEL_GRADE_MAPPING = {
    'SD400': 'D4', 'SD500': 'D5', '500N': 'N5',
    'B500B': 'B5', '500B': 'B5', 'SD500S': 'D5',
}

# 일별 불량률 (전 강종 합산 + 강종별 분리)
query = """
SELECT
    production_date,
    SUM(winding_defect_quantity) / NULLIF(SUM(production_quantity), 0) as winding_defect_rate,
    SUM(weight_defect_quantity)  / NULLIF(SUM(production_quantity), 0) as weight_defect_rate,
    SUM(total_defect_quantity)   / NULLIF(SUM(production_quantity), 0) as total_defect_rate
FROM defect_selection_status
WHERE production_date >= '2025-03-01'
  AND production_date < '2025-09-01'
GROUP BY production_date
ORDER BY production_date
"""
```

**Step 1-3: 데이터 병합 (날짜 기준 INNER JOIN)**
```python
# 최종 분석 데이터셋
tag_defect_matrix = iba_daily.merge(defect_daily, on='date', how='inner')

# 기대 레코드 수: 184일 × 90% JOIN 성공률 ≈ 166건
# 저장
tag_defect_matrix.to_parquet('data/tag_defect_matrix_ALL.parquet')
```

**Step 1-4: 파생 변수 추가 (C2 방안)**
```python
# 이진 불량 라벨 (C4 프로파일 비교용)
q80_winding = tag_defect_matrix['winding_defect_rate'].quantile(0.80)
q80_weight  = tag_defect_matrix['weight_defect_rate'].quantile(0.80)
tag_defect_matrix['high_winding_defect'] = (tag_defect_matrix['winding_defect_rate'] >= q80_winding)
tag_defect_matrix['high_weight_defect']  = (tag_defect_matrix['weight_defect_rate']  >= q80_weight)

# 고불량일 정의: 두 불량 중 하나라도 상위 20%
tag_defect_matrix['any_high_defect'] = (
    tag_defect_matrix['high_winding_defect'] | tag_defect_matrix['high_weight_defect']
)
```

**Step 1-5: 강종별 태그-불량 매트릭스 분기 생성**
```python
# Layer 0: 전체 합산 (기존 Step 1-3 결과 이름 변경)
tag_defect_matrix_ALL = tag_defect_matrix
tag_defect_matrix_ALL.to_parquet('data/tag_defect_matrix_ALL.parquet')

# Layer 1: 강종별 분기
for grade, cfg in GRADE_ANALYSIS_CONFIG.items():
    if grade == 'ALL':
        continue
    defect_filter = cfg['defect_filter']
    # ⚠️ [F1] fetch_daily_defect_rates()는 현재 grade 파라미터를 SQL WHERE에 미반영 (common.py:443)
    #     → 전체 강종 합산 불량률만 반환됨. 강종별 분석을 위해 아래 중 택 1:
    #     (a) common.py 함수 수정: WHERE ... AND steel_grade IN ({grades_str}) 추가
    #     (b) 직접 SQL 작성: Step 1-2의 쿼리에 steel_grade 필터 추가 후 별도 호출
    grade_defect = fetch_daily_defect_rates(grade_filter=defect_filter)
    # ⚠️ [F3] fetch_iba_daily_stats()는 현재 common.py에 미구현 — 신규 작성 필요 (아래 가이드 참조)
    grade_iba    = fetch_iba_daily_stats(steel_grade=grade)   # ClickHouse: v_iba_by_steel_grade VIEW 사용 (steel_grade는 memo_prod_result JOIN으로 제공)
    grade_matrix = grade_iba.merge(grade_defect, on='date', how='inner')
    grade_matrix.to_parquet(f'data/tag_defect_matrix_{grade}.parquet')
    # D4, B5: viz_only → 통계 분석 미실행
```

**Step 1-6: 규격별 태그-불량 매트릭스 생성 (N5, D5 한정)**
```python
for grade in SIZE_ANALYSIS_GRADES:      # ['N5', 'D5']
    top_sizes = get_top_sizes_by_count(grade, top_n=TOP_N_SIZES)
    for size in top_sizes:
        size_iba    = fetch_iba_daily_stats(steel_grade=grade, size=size)
        size_defect = fetch_daily_defect_rates(grade_filter=..., size=size)
        size_matrix = size_iba.merge(size_defect, on='date', how='inner')
        size_matrix.to_parquet(f'data/tag_defect_matrix_{grade}_SZ{size}.parquet')
```

**산출물 (Step 1 전체)**:
- `data/tag_defect_matrix_ALL.parquet` (166행 × ~600열, ALL 합산)
- `data/tag_defect_matrix_N5.parquet` (N5 강종별)
- `data/tag_defect_matrix_D5.parquet` (D5 강종별)
- `data/tag_defect_matrix_N5_SZ{size}.parquet` (N5 규격별, 상위 3개)
- `data/tag_defect_matrix_D5_SZ{size}.parquet` (D5 규격별, 상위 3개)
- `data/daily_coverage_report.json` (날짜별 데이터 커버리지)
- `data/filter_application_stats.json` (카테고리별 필터 제거 통계)
- `data/grade_size_coverage.json` (강종×규격별 데이터 건수)

**진단 차트 (Phase 1 완료 후 인라인 생성)**:

#### D15. 레이어별 데이터 충분성 요약
- **파일**: `diagnostics/diag_data_coverage_summary.png`
- **유형**: GridSpec 2패널: 좌=stacked bar, 우=표
- **좌 패널**: X=레이어(ALL,N5,D5,D4,B5), Y=유효 일수
- **색상**: 초록(>30일), 노랑(20~30), 빨강(<20)
- **크기**: (14, 6)
- **설계**: 30일(최소), 50일(권장) 수평선. 우 패널: 레이어별 M1~M6 활성화 표
- **목적**: 결과 해석의 즉각 컨텍스트 제공

#### D16. 필터 적용 후 데이터 잔존율
- **파일**: `diagnostics/diag_filter_retention_rates.png`
- **유형**: Grouped bar
- **소스**: `filter_application_stats.json`
- **X축**: 9개 카테고리 (Cat01~Cat09b)
- **Y축**: 데이터 잔존율 (%)
- **색상**: 필터 단계별 (run_only=초록, special_ops=노랑, roll_change=주황, coiling_transient=빨강)
- **크기**: (14, 6)
- **설계**: 55% 기준선 (이하 시 분석 품질 저하 경고)
- **목적**: 카테고리별 과도 필터링 여부 검증

---

### Phase 2: 상관 분석 실행 (Script 02 + 03)

```
파일: scripts/02_correlation_analysis.py
       scripts/03_ml_regression.py
목표: M1~M6 각 기법 순위표 생성 (Layer 0 ALL + Layer 1 N5/D5 강종별)
소요: 1~2일
```

#### 데이터 충분성에 따른 기법 선택

| Layer | 데이터 | M1 Spearman | M2 MW+d | M3 LightGBM | M4 Quantile | M5 이상치 | M6 변점 |
|-------|:------:|:-----------:|:-------:|:-----------:|:-----------:|:--------:|:------:|
| ALL (~166일) | 충분 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| N5 (~41일) | 충분 | ✅ | ✅ | ✅ | ✅ | ❌ 제한 | ❌ 제한 |
| D5 (~21일) | 경계 | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ |
| D4/B5 (<10일) | 부족 | viz_only | viz_only | ❌ | ❌ | ❌ | ❌ |

#### 결과 파일 명명 규칙

```
results_m1_spearman_ALL.csv       ← 전체 합산 Spearman
results_m1_spearman_N5.csv        ← N5 강종별
results_m1_spearman_D5.csv        ← D5 강종별
results_m2_mannwhitney_ALL.csv
results_m2_mannwhitney_N5.csv
results_m3_lgbm_importance_ALL.csv
results_m3_lgbm_importance_N5.csv  (N5만: D5는 데이터 부족)
... (동일 패턴)
```

#### 기존 분석 스크립트 재사용 참조

| 기존 스크립트 | 구현된 기법 | 재사용 패턴 | 적용 기법 |
|-------------|-----------|-----------|----------|
| `scripts/analyze_defect_correlation.py` | Pearson, Lag(0~7일) | Spearman으로 전환 + Bonferroni 보정 추가 | M1 Spearman |
| `scripts/comprehensive_defect_analysis.py` | Pearson/Spearman, Lag(0~14일), RF, Ridge/Lasso | 5-Fold CV → LOO-CV 전환, Feature Importance 추출 | M1, M3 참조 |
| `scripts/advanced_defect_analysis.py` | GBR, ExtraTrees, MLP, 강종별 분할 | LightGBM 교체 + 강종별 분기 패턴 재사용 | M3 LightGBM |
| `scripts/advanced_defect_analysis.py` | Z-Score Outlier, Trend 분석 | QuantileRegressor Q90 추가 구현 | M4 Quantile |
| `scripts/deep_analysis/eda_correlation.py` | Pearson/Spearman/Kendall, CCF, PCA | 3중 상관 비교 패턴, PCA loadings 참조 | M1 검증, 향후 C2 확장 |
| `scripts/cross_validate_defect_outlier_tags.py` | 불량 태그-이상치 교차, 변동성(CV) | Fisher's Exact OR 추가 + 교차 검증 확장 | M5 이상치 교차 |
| `scripts/phase1_outlier_detection.py` | IQR, Modified Z-Score, Context-Aware 필터 | IQR 경계값 + 카테고리별 필터 설정 재사용 | M5 IQR 경계 |

> **기존 분석에서 발견된 도메인 인사이트** (M1~M6 결과 해석 시 참조):
> - 가스 압력/유량이 권취 불량과 **음의 상관** (ρ ≈ -0.15) — 가스 공급 부족 시 불량 증가
> - 스탠드 속도(STAND_1~14)가 불량과 **음의 상관** (ρ ≈ -0.18) — 속도 저하 시 불량 증가
> - 불량은 파라미터 이상 후 **1~3일 시차**로 발현 (가스 24시간, 온도 2~3일 지연)
> - D5 강종은 온도 변동에, N5는 속도 동기화에 더 민감

**Script 02: M1(Spearman), M2(Mann-Whitney), M5(이상치 교차), M6(변점)**

```python
TAG_STAT_COMBINATIONS = {
    # 태그명: [(stat_suffix, defect_col), ...]
    # 예: 'FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE':
    #     [('_avg', 'winding_defect_rate'), ('_std', 'winding_defect_rate'), ...]
}

results_m1 = []  # Spearman ρ
results_m2 = []  # Mann-Whitney + Cohen's d

for tag in ALL_ANALYSIS_TAGS:  # 91개
    for stat in ['avg', 'std', 'max', 'cv', 'iqr']:
        col = f'{tag}_{stat}'
        if col not in tag_defect_matrix.columns:
            continue
        for defect_col in ['winding_defect_rate', 'weight_defect_rate', 'total_defect_rate']:
            # M1: Spearman
            rho, pval = spearmanr(tag_defect_matrix[col].dropna(),
                                   tag_defect_matrix[defect_col].dropna())
            results_m1.append({'tag': tag, 'stat': stat, 'defect': defect_col,
                                'rho': rho, 'pval': pval})

            # M2: Mann-Whitney U
            high = tag_defect_matrix.loc[tag_defect_matrix['any_high_defect'], col].dropna()
            normal = tag_defect_matrix.loc[~tag_defect_matrix['any_high_defect'], col].dropna()
            if len(high) >= 3 and len(normal) >= 3:
                u_stat, u_pval = mannwhitneyu(high, normal, alternative='two-sided')
                pooled_std = np.sqrt((high.std()**2 + normal.std()**2) / 2)
                cohens_d = (high.mean() - normal.mean()) / pooled_std if pooled_std > 0 else 0
                results_m2.append({'tag': tag, 'stat': stat, 'u_pval': u_pval,
                                    'cohens_d': cohens_d})
```

**진단 차트 (Script 02 내 인라인 생성)**:

#### D01. Volcano Plot — M1 상관 강도 vs 통계적 유의성
- **파일**: `diagnostics/D01_volcano_spearman.png`
- **유형**: Scatter (volcano)
- **소스**: `results_m1_spearman_ALL.csv`
- **X축**: Spearman ρ (부호 포함, -0.5~+0.5)
- **Y축**: -log10(Bonferroni 보정 p-value)
- **색상**: 카테고리 색상 (`CATEGORY_COLORS`). 유의선 위=채움, 아래=투명
- **크기**: (12, 8)
- **설계**: 수평선 -log10(0.05), 수직선 ρ = ±0.30. Top-5 태그 라벨. 태그별 최적 통계량/불량 조합 표시
- **목적**: Bonferroni 보정 과도 여부 검증 + 실용적 유의미 태그 식별

#### D02. M1 통계량 유형별 Heatmap (avg vs std vs max)
- **파일**: `diagnostics/D02_heatmap_spearman.png`
- **유형**: Heatmap (3행 × N열)
- **소스**: `results_m1_spearman_ALL.csv`
- **X축**: Top 30 태그 (|ρ| 순)
- **Y축**: 3 통계량: `_avg`, `_std`, `_max` (defect 3종별 패널 가능)
- **색상**: `RdBu_r` diverging (0 중심). p < 0.05(Bonferroni) 셀에 * 표시
- **크기**: (16, 6)
- **목적**: "평균 수준(avg)이 문제인가, 변동성(std)이 문제인가, 극단값(max)이 문제인가?" → 알람 유형(정적 임계/변동폭 알람) 결정 근거

#### D03. M2 효과 크기 분포 + 유의성 바
- **파일**: `diagnostics/D03_cohens_d_bar.png`
- **유형**: Horizontal bar (이중 인코딩)
- **소스**: `results_m2_mannwhitney_ALL.csv`
- **X축**: |Cohen's d|
- **Y축**: Top 30 태그
- **색상**: 초록(p<0.05), 노랑(0.05~0.10), 회색(p≥0.10). 오른쪽 d 부호/수치 주석
- **크기**: (12, 10)
- **설계**: d=0.20(소), 0.50(중), 0.80(대) 수직 기준선 + 배경 밴드
- **목적**: p-value와 독립적으로 실용적 효과 크기 시각화

#### D04. M2 Top-5 태그 분포 비교 (Split Violin)
- **파일**: `diagnostics/D04_violin_split.png`
- **유형**: Split violin 또는 raincloud plot
- **소스**: `tag_defect_matrix_ALL.parquet`, M2 Top-5 태그 필터
- **X축**: 5 태그 (패널)
- **Y축**: 표준화 태그 값
- **색상**: 주황=고불량일(상위 20%), 파랑=정상일
- **크기**: (14, 8) 또는 GridSpec 1×5
- **목적**: C05/C06 boxplot 대비 전체 분포 형태(bimodality, skewness) 확인

#### D05. M5 2×2 분할표 Mosaic (Top-6 태그)
- **파일**: `diagnostics/D05_contingency_mosaic.png`
- **유형**: GridSpec 2×3 mosaic 패널
- **소스**: `results_m5_outlier_cross.csv` + 원시 분할표
- **패널**: 각 태그별 (이상치 유/무) × (고불량일 유/무) 2×2
- **색상**: 빨강=(이상치+고불량) 일치 셀, 파랑=(정상+정상) 일치 셀, 회색=불일치
- **크기**: (14, 10)
- **설계**: 패널 제목: 태그명 + OR값 + p-value. OR>2.0 패널 빨간 테두리
- **목적**: Fisher's Exact 분할표 시각적 검증

#### D06. M5 Odds Ratio vs Spearman ρ Scatter
- **파일**: `diagnostics/D06_scatter_or_vs_rho.png`
- **유형**: Scatter
- **소스**: `results_m5_outlier_cross.csv`
- **X축**: log2(Odds Ratio)
- **Y축**: Spearman ρ (이상치 수 vs 불량률)
- **색상**: 카테고리. 점 크기 ∝ 이상치 발생 일수
- **크기**: (10, 8)
- **설계**: 4사분면: Q1(OR 높+ρ 높)="이진+등급 알람", Q2(OR 높+ρ 낮)="이진 알람만", Q3(OR 낮+ρ 높)="등급 알람만", Q4="무관"
- **목적**: 이상치 유무(이진) vs 이상치 빈도(건수) 중 어느 것이 불량과 연관인지 판단 → 알람 설계

#### D07. M6 변점 빈도 시계열 (Dual-axis)
- **파일**: `diagnostics/D07_changepoint_timeseries.png`
- **유형**: Dual-axis line chart
- **소스**: `results_m6_changepoint.csv` + 일별 불량률
- **X축**: 날짜 (2025-03~08)
- **Y축 좌**: 7일 롤링 변점 수 (Top-3 태그, 선 스타일 구분)
- **Y축 우**: 종합 불량률 (빨간 점선)
- **색상**: 태그별 카테고리 색상. 고불량 주간 회색 밴드
- **크기**: (14, 6)
- **목적**: M6 가설("변점 빈발 ↔ 불량 증가") 시각적 검증

#### D08. M6 변점-불량 ρ 순위 바
- **파일**: `diagnostics/D08_changepoint_bar.png`
- **유형**: Horizontal bar
- **소스**: `results_m6_changepoint.csv`
- **X축**: Spearman ρ (변점 빈도 vs 불량률)
- **Y축**: Top 20 태그
- **색상**: 카테고리. ρ>0.3 초과 바 진한 채움
- **크기**: (10, 8)
- **설계**: ρ=0.3 수직선. p-value 주석
- **목적**: 공정 불안정-불량 상관 태그 빠른 순위 확인

---

**Script 03: M3(LightGBM), M4(Quantile Regression)**

```python
# M3: LightGBM Feature Importance
import lightgbm as lgb
from sklearn.model_selection import LeaveOneOut

# 특성: 태그별 avg 통계 82 유효 태그 (결측 0으로 채움)
feature_cols = [f'{t}_avg' for t in ALL_ANALYSIS_TAGS]
X = tag_defect_matrix[feature_cols].fillna(0)
y = tag_defect_matrix['winding_defect_rate'].fillna(0)

model = lgb.LGBMRegressor(n_estimators=200, max_depth=4, num_leaves=16,
                            learning_rate=0.05, min_child_samples=8,
                            verbose=-1, random_state=42)
model.fit(X, y)

importance_m3 = pd.Series(model.feature_importances_, index=feature_cols)

# M4: Quantile Regression Q90
from sklearn.linear_model import QuantileRegressor
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

qr = QuantileRegressor(quantile=0.90, alpha=0.05, solver='highs')
qr.fit(X_scaled, y)

coef_m4 = pd.Series(np.abs(qr.coef_), index=feature_cols)
```

**진단 차트 (Script 03 내 인라인 생성)**:

#### D09. M3 Feature Importance: Gain vs Split 비교
- **파일**: `diagnostics/D09_lgbm_gain_split_importance.png`
- **유형**: GridSpec 1×2 paired horizontal bar
- **소스**: `results_m3_lgbm_importance_ALL.csv` (gain + split 모두)
- **좌 패널**: Gain FI (정규화). **우 패널**: Split FI (정규화)
- **Y축**: Top 20 features (gain FI 순)
- **색상**: 파랑(gain), 주황(split). 순위 차 >10 빨간 화살표
- **크기**: (14, 8)
- **목적**: Gain 기반 FI의 신뢰성 검증. 높은 split + 낮은 gain = 상관 프록시 태그

#### D10. M3 LOO-CV 예측 vs 실측 Scatter
- **파일**: `diagnostics/D10_loocv_scatter.png`
- **유형**: Scatter + 45° 대각선
- **소스**: LOO-CV predictions 배열
- **X축**: 실제 불량률. **Y축**: LOO-CV 예측 불량률
- **색상**: 월별 그라디언트. 잔차 > 2×RMSE 빨간 표시
- **크기**: (8, 8) 정사각형
- **설계**: R², RMSE, MAE 주석
- **목적**: M3 가중치(0.25)의 정당성 검증. R²<0.1이면 FI 해석 주의

#### D11. M3 Partial Dependence Plot (Top-4 Feature)
- **파일**: `diagnostics/D11_partial_dependence_top4.png`
- **유형**: GridSpec 2×2 line plots
- **소스**: sklearn `PartialDependenceDisplay`
- **X축**: feature 값. **Y축**: partial dependence (불량률 한계 효과)
- **색상**: 파랑선 + 회색 신뢰구간 + 빨강 rug plot
- **크기**: (12, 10)
- **목적**: FI는 **크기**만, PDP는 **방향과 형태** 제공. "온도 올라가면 불량 증가 후 plateau" 같은 비선형 관계 → 알람 임계값 설정 근거

#### D12. M4 회귀 계수 방향 차트 (Diverging Bar)
- **파일**: `diagnostics/D12_quantile_q90_diverging.png`
- **유형**: Diverging horizontal bar
- **소스**: `results_m4_quantile_ALL.csv`
- **X축**: 표준화 계수 (음수~양수)
- **Y축**: Top 20 features (|계수| 순)
- **색상**: 빨강=양(태그↑→불량↑), 파랑=음(태그↓→불량↑)
- **크기**: (12, 8)
- **설계**: 0선 명확. 화살표 주석: "상한 알람 설정" / "하한 알람 설정"
- **목적**: M3 FI는 크기만, M4는 **방향** 제공 — 상한 vs 하한 알람 결정에 핵심

#### D13. M4 Quantile 비교 (Q50 vs Q75 vs Q90)
- **파일**: `diagnostics/D13_quantile_q50_q75_q90_comparison.png`
- **유형**: Grouped horizontal bar
- **소스**: Q50, Q75, Q90 각각 회귀 실행 결과
- **X축**: |표준화 계수|. **Y축**: Top 15 features
- **색상**: Q50=연회색, Q75=주황, Q90=빨강
- **크기**: (12, 8)
- **목적**: Q90>>Q50인 feature = "극단 이벤트 전용 태그" (비상 감시). Q50≥Q90인 feature = "기본 태그" (일상 관리)

#### D14. M3 FI vs M4 Q90 계수 교차 비교 Scatter
- **파일**: `diagnostics/D14_m3_vs_m4_rank_scatter.png`
- **유형**: Scatter
- **소스**: M3 FI + M4 Q90 결과
- **X축**: M3 LightGBM FI (정규화 순위 백분위)
- **Y축**: M4 Q90 |계수| (정규화 순위 백분위)
- **색상**: 카테고리. 점 크기 ∝ M1 |ρ|
- **크기**: (10, 10)
- **설계**: 4사분면: "핵심 태그"(우상), "극단 전용"(좌상), "평균 전용"(우하), "저우선"(좌하). Top-10 라벨
- **목적**: 평균 예측(M3) vs 극단 예측(M4) 교차 검증 → 모니터링 우선순위 설정

---

### Phase 3: 앙상블 순위 통합 및 Top-20 선정 (Script 04)

```
파일: scripts/04_ensemble_ranking.py
목표: M1~M6 순위 통합 → Top-20 태그 + 그룹별 집계
소요: 0.5일
```

**앙상블 가중치 설정 근거**:

| 기법 | 가중치 | 근거 |
|------|:------:|------|
| M1 Spearman ρ | 0.25 | 직접적 상관 측정, 비모수적 강건성 |
| M2 Cohen's d | 0.20 | 실용적 효과 크기, 불균형 대응 |
| M3 LightGBM FI | 0.25 | 비선형 상호작용 포착, 예측력 기반 |
| M4 Quantile Q90 | 0.15 | 고불량 극단 이벤트 민감도 |
| M5 이상치 교차 | 0.10 | 이상치 기반 검증 (기존 분석 연계) |
| M6 변점 빈도 | 0.05 | 보조 지표 |

```python
def compute_ensemble_rank(m1_df, m2_df, m3_series, m4_series, m5_df, m6_df):
    """
    각 기법 결과 → 태그별 정규화 순위 → 가중 평균
    반환: tag × ensemble_score DataFrame
    """
    weights = {'m1': 0.25, 'm2': 0.20, 'm3': 0.25, 'm4': 0.15, 'm5': 0.10, 'm6': 0.05}

    # 각 기법 최고 점수 채택 (태그별)
    # 통계량별(avg/std/max)과 불량별(winding/weight/total) 조합 중 최대값
    m1_best = m1_df.groupby('tag')['abs_rho'].max()  # |ρ| 최대
    m2_best = m2_df.groupby('tag')['abs_cohens_d'].max()
    # ...

    # 순위 계산 (내림차순: 점수 높을수록 상위)
    rank_m1 = m1_best.rank(ascending=False)
    rank_m2 = m2_best.rank(ascending=False)
    rank_m3 = m3_series.rank(ascending=False)
    rank_m4 = m4_series.rank(ascending=False)
    rank_m5 = m5_df['m5_score'].rank(ascending=False)
    rank_m6 = m6_df['rho'].rank(ascending=False)

    # 가중 앙상블 (낮을수록 상위)
    ensemble = (
        weights['m1'] * rank_m1 +
        weights['m2'] * rank_m2 +
        weights['m3'] * rank_m3 +
        weights['m4'] * rank_m4 +
        weights['m5'] * rank_m5 +
        weights['m6'] * rank_m6
    )
    return ensemble.sort_values()
```

**강종별 앙상블 실행**:
```python
# Layer 0 (ALL): M1~M6 전체
ensemble_ALL = compute_ensemble_rank(m1_ALL, m2_ALL, m3_ALL, m4_ALL, m5_ALL, m6_ALL)
ensemble_ALL.to_csv('data/top20_ensemble_ranking_ALL.csv')

# Layer 1 N5: M1, M2, M3, M4 (M5/M6 제외)
ensemble_N5 = compute_ensemble_rank_partial(m1_N5, m2_N5, m3_N5, m4_N5,
    weights={'m1': 0.35, 'm2': 0.30, 'm3': 0.25, 'm4': 0.10})
ensemble_N5.to_csv('data/top20_ensemble_ranking_N5.csv')

# Layer 1 D5: M1, M2만
ensemble_D5 = compute_ensemble_rank_partial(m1_D5, m2_D5,
    weights={'m1': 0.55, 'm2': 0.45})
ensemble_D5.to_csv('data/top20_ensemble_ranking_D5.csv')

# 강종 비교표 생성
grade_compare = pd.DataFrame({
    'rank_ALL': ensemble_ALL.rank(),
    'rank_N5':  ensemble_N5.rank(),
    'rank_D5':  ensemble_D5.rank(),
}).sort_values('rank_ALL')
grade_compare['common_count'] = (grade_compare <= 20).sum(axis=1)
grade_compare.to_csv('data/top20_ensemble_ranking_grade_compare.csv')

# ⚠️ 기존 deep_tag_defect_analysis 결과와 교차 비교 (결과 신뢰도 검증)
# final_tag_ranking.csv에 3,688개 태그×통계 조합의 기존 앙상블 순위 존재
# → 본 분석 Top-20과 Kendall's τ 비교로 결과 일관성 검증
existing_ranking = pd.read_csv('analysis_output/deep_tag_defect_analysis/final_tag_ranking.csv')
tau_vs_existing, p_val = kendalltau(ensemble_ALL.rank(), existing_ranking_mapped)

# 규격별 순위 변동성 (Kendall's τ)
for grade in SIZE_ANALYSIS_GRADES:
    size_rankings = [ensemble_by_size[grade][sz] for sz in top_sizes[grade]]
    tau_matrix = compute_kendall_tau_matrix(size_rankings)
    # tau < 0.5 → 규격별 독립 임계값 설정 권고
```

**Step 3-2: 강종별 Top-20 비교표 생성**:
```python
# ALL ∩ N5 ∩ D5 공통 Top-20 → 최우선 모니터링 대상
top20_ALL = set(ensemble_ALL.head(20).index)
top20_N5  = set(ensemble_N5.head(20).index)
top20_D5  = set(ensemble_D5.head(20).index)
core_tags = top20_ALL & top20_N5 & top20_D5
shared_tags = top20_ALL | top20_N5 | top20_D5
```

**Step 3-3: 규격별 순위 변동성 (N5, D5 각각)**:
```python
# Kendall's τ (규격 간 순위 일치도)
# τ ≥ 0.7: 규격 관계없이 동일 태그 → 공통 임계값 설정 가능
# τ < 0.5: 규격별로 다른 태그가 중요 → 규격별 독립 모니터링 권고
grade_size_variation.to_csv('data/grade_size_top10_variation.csv')
```

**그룹별 분석**:
```python
CATEGORY_TAG_MAP = {
    'Cat01_가열로상부온도': [...],
    'Cat02_가열로하부온도': [...],
    'Cat03_가열로추출온도': [...],
    'Cat04_가열로보조설비': [...],
    'Cat05_스탠드토크': [...],
    'Cat06_스탠드속도': [...],
    'Cat07_스탠드부하': [...],
    'Cat08_핀치롤': [...],
    'Cat09_냉각수': [...],
    'Cat09b_PR상세': [...],
}

# 그룹별 집계
for cat, tags in CATEGORY_TAG_MAP.items():
    cat_tags = [t for t in tags if t in ensemble_scores.index]
    group_scores[cat] = {
        'mean_ensemble_score': ensemble_scores[cat_tags].mean(),
        'best_tag': ensemble_scores[cat_tags].idxmin(),
        'best_score': ensemble_scores[cat_tags].min(),
        'n_top20': sum(ensemble_scores[cat_tags].rank() <= 20),
    }
```

---

### Phase 4: 차트 생성 (Script 05)

```
파일: scripts/05_chart_generation.py
목표: 20종 차트 생성 (C01~C20, PPTX 삽입용 PNG)
소요: 1일
```

#### 차트 목록

| # | 파일명 | 차트 유형 | 내용 |
|---|--------|----------|------|
| C01 | `chart_01_spearman_heatmap.png` | 히트맵 | 91태그 × 3불량 Spearman ρ 매트릭스 (상위 30개) |
| C02 | `chart_02_group_comparison_bar.png` | 수평 바 차트 | 10개 카테고리별 평균 앙상블 점수 (내림차순) |
| C03 | `chart_03_top20_ranking.png` | 수평 바 차트 | Top-20 태그 앙상블 점수 + 기법별 색상 구분 |
| C04 | `chart_04_method_comparison_scatter.png` | 산점도 | M1 Spearman vs M3 LightGBM FI (태그별 점) |
| C05 | `chart_05_top5_boxplot_winding.png` | 박스플롯 | 권취불량 상위 5태그 — 고불량일 vs 정상일 분포 |
| C06 | `chart_06_top5_boxplot_weight.png` | 박스플롯 | 중량불량 상위 5태그 — 고불량일 vs 정상일 분포 |
| C07 | `chart_07_monthly_trend.png` | 라인 차트 | 2025-03~08 월별 고불량일 빈도 + Top-3 태그 이상치 빈도 |
| C08 | `chart_08_category_radar.png` | 레이더 차트 | 10개 카테고리 × 6기법 점수 다각형 |
| C09 | `chart_09_venn_diagram.png` | 벤 다이어그램 | Top-20 태그의 3분류 소속 분포 |
| C10 | `chart_10_defect_rate_timeseries.png` | 라인 차트 | 2025-03~08 기간 일별 불량률 + Top-1 태그 이상치 |
| C11 | `chart_11_cohens_d_ranking.png` | 수평 바 차트 | Cohen's d 기준 상위 20태그 (효과 크기) |
| C12 | `chart_12_correlation_change_by_grade.png` | 그룹 바 차트 | Top-10 태그의 강종별(B5/D4/D5/N5) 상관계수 비교 |
| C13 | `chart_13_filter_impact.png` | 폭포수 차트 | 필터 단계별 데이터 감소량 (카테고리별 원본→run_only→special_ops→roll_change→coiling_transient) |
| C14 | `chart_14_grade_top20_heatmap.png` | 히트맵 | 강종별(ALL/N5/D5) × Top-20 태그 앙상블 순위 매트릭스 |
| C15 | `chart_15_size_variation.png` | 선+점 차트 | 규격별 Top-10 태그 상관계수 변동 (N5/D5 각각, 규격 x축) |
| C16 | `chart_16_filter_preset_compare.png` | 산점도 | P2_OPTIMAL vs P4_PER_TAG 결과 비교 (태그별 순위 변동 산점도) |
| C17 | `chart_17_method_agreement_heatmap.png` | 히트맵 | 6기법(M1~M6) × Top-20 태그 순위 합의도 매트릭스 |
| C18 | `chart_18_ensemble_decomposition.png` | Stacked H-Bar | Top-20 태그 앙상블 점수의 기법별 가중 기여도 분해 |
| C19 | `chart_19_defect_tag_overlay.png` | Multi-line + dual Y | 일별 불량률(area) + Top-3 앙상블 태그(line) 시계열 오버레이 |
| C20 | `chart_20_actionable_summary.png` | GridSpec 2×2 대시보드 | 실행 가능 요약: Top-10 바 + 알람 방향 + 카테고리 파이 + 데이터 신뢰도 |

#### C17~C20 신규 PPTX 차트 상세

**C17. 기법 합의도 Heatmap**
- **소스**: M1~M6 전체 결과 + 앙상블 순위
- **X축**: 6 기법 (M1~M6). **Y축**: Top 20 태그 (앙상블 순위)
- **색상**: `YlOrRd` (낮은 순위=진함=중요). Top-30 밖이면 회색
- **크기**: (12, 10)
- **설계**: 행 주석: 앙상블 순위 번호. 열 헤더: 기법명+가중치. 4+기법 합의 행 bold
- **PPTX 슬라이드**: 23번
- **목적**: 앙상블 결과가 단일 기법에 의존하지 않음을 검증. 4+기법 합의 태그 = 강건한 핵심 태그

**C18. 앙상블 점수 분해 (Stacked Bar)**
- **소스**: `top20_ensemble_ranking_ALL.csv` (기법별 가중 점수)
- **X축**: 가중 순위 기여도. **Y축**: Top 20 태그
- **색상**: `METHOD_COLORS` (M1=남색, M2=청록, M3=초록, M4=주황, M5=보라, M6=분홍)
- **크기**: (14, 10)
- **설계**: 범례에 기법명+가중치. 단일 기법 >60% 점유 시 경고 아이콘
- **PPTX 슬라이드**: 18번 뒤 신규 삽입
- **목적**: "왜 이 태그가 N위인가?" 설명. 기법별 기여 시각적 분해

**C19. 불량률-태그 시계열 오버레이 (Enhanced C10)**
- **소스**: `tag_defect_matrix_ALL.parquet`
- **X축**: 날짜 (2025-03~08)
- **Y축 좌**: 불량률 (권취+중량 stacked area). **Y축 우**: Top-3 앙상블 태그 값 (표준화, line)
- **색상**: 불량 area: 연빨강(권취)+연파랑(중량). 태그 선: 카테고리 색상
- **크기**: (16, 6)
- **설계**: 고불량일(상위 20%) 주황 수직 밴드. 태그별 ρ 주석
- **PPTX 슬라이드**: Chapter 4 내 C10 대체/보강
- **목적**: 현장 엔지니어에게 가장 직관적. Top-3 태그가 불량률과 실제로 연동하는지 날짜별 시각 확인

**C20. 실행 가능 요약 대시보드**
- **유형**: GridSpec 2×2 다목적 대시보드
- **패널 1(좌상)**: Top-10 앙상블 바 (카테고리 색상)
- **패널 2(우상)**: 알람 방향 요약 (M4 계수 양→상한, 음→하한, 화살표)
- **패널 3(좌하)**: 카테고리별 Top-20 태그 수 파이
- **패널 4(우하)**: 데이터 신뢰도 게이지 (레이어별 충분성)
- **색상**: 카테고리 색상 + 초록/빨강(알람 방향)
- **크기**: (16, 12)
- **PPTX 슬라이드**: 28번 (개선 우선순위 권고)
- **목적**: 경영진/공장장 요약용. 이 차트 하나로 핵심 파악: (1) 중요 태그, (2) 알람 방향, (3) 공정 영역, (4) 데이터 신뢰도

**차트 공통 스타일**:
```python
# 공통 설정
plt.rcParams['font.family'] = 'DejaVu Sans'
plt.rcParams['figure.dpi'] = 150
plt.rcParams['savefig.dpi'] = 150
fig_size_full = (14, 8)        # 전페이지 차트
fig_size_half = (10, 6)        # 반페이지 차트
fig_size_wide = (16, 6)        # 와이드 차트 (C19, D07 등)
fig_size_dashboard = (16, 12)  # 대시보드 차트 (C20)

# 카테고리 색상 팔레트
CATEGORY_COLORS = {
    'Cat01~04 가열로': '#E74C3C',   # 빨강
    'Cat05~07 스탠드': '#3498DB',   # 파랑
    'Cat08 핀치롤':    '#2ECC71',   # 초록
    'Cat09 냉각수':    '#9B59B6',   # 보라
    'Cat09b PR상세':   '#F39C12',   # 주황
}

# 기법별 색상 (C17, C18 전용)
METHOD_COLORS = {
    'M1': '#2C3E50',  # 남색 (Spearman)
    'M2': '#1ABC9C',  # 청록 (Mann-Whitney)
    'M3': '#27AE60',  # 초록 (LightGBM)
    'M4': '#F39C12',  # 주황 (Quantile)
    'M5': '#8E44AD',  # 보라 (이상치 교차)
    'M6': '#E91E63',  # 분홍 (변점 빈도)
}
```

---

### Phase 5: 보고서 MD 작성 (PPTX용)

```
파일: analysis_output/tag_defect_correlation/REPORT_tag_defect_pptx.md
목표: PPTX 변환용 구조화된 보고서 MD
소요: 1일
```

#### 슬라이드 구성 계획 (41 슬라이드 예상 — 필터/강종 분석 5개 + C17~C20 차트 4개 추가)

| 슬라이드 # | 섹션 | 내용 | 차트 |
|:----------:|------|------|:----:|
| 1 | 표지 | 제목, 날짜, 버전 | - |
| 2 | 목차 | 5개 챕터 개요 | - |
| 3 | **[Chapter 1] 배경** | 분석 목적 및 질문 | - |
| 4 | 데이터 현황 | 3개 DB 테이블 요약 | - |
| 5 | 분석 기간 | 2025-03~08, 데이터 커버리지 | C10 일부 |
| 6 | 분석 범위 | 91태그 × 3분류 × 6기법 | - |
| 7 | **[Chapter 2] 방법론** | 6가지 기법 소개 | - |
| 8 | M1~M2 설명 | Spearman, Mann-Whitney | - |
| 9 | M3~M4 설명 | LightGBM, Quantile Reg | - |
| 10 | M5~M6 설명 | 이상치 교차, 변점 빈도 | - |
| 11 | 앙상블 통합 방식 | 가중 순위 집계 수식 | - |
| 11a | 필터 시스템 설명 | 4가지 필터 종류 및 카테고리별 적용 매트릭스 | - |
| 11b | 필터 적용 전후 비교 | 데이터 품질 및 감소량 폭포수 | C13 |
| 12 | **[Chapter 3] 그룹별 결과** | 10개 카테고리 비교 요약 | C02 |
| 13 | 가열로 그룹 (Cat01~04) | 4개 카테고리 상관 분석 | C08 |
| 14 | 스탠드 그룹 (Cat05~07) | 스탠드 토크/속도/부하 | C08 |
| 15 | 핀치롤/PR 그룹 (Cat08~09b) | 핀치롤 + 냉각수 | C08 |
| 16 | 3분류 비교 | PLC vs 현업 vs AI 그룹 | C09 |
| 17 | 카테고리별 Top 태그 | 각 Cat 최고 상관 태그 | - |
| 18 | **[Chapter 4] Top-20 결과** | 최종 순위 표 | C03 |
| 18a | 앙상블 점수 분해 | Top-20 기법별 기여도 시각화 | C18 |
| 19 | #1~5 태그 상세 | 태그명, 설명, 상관 계수, 공정 의미 | C05 |
| 20 | #6~10 태그 상세 | 동일 | C06 |
| 21 | #11~15 태그 상세 | 동일 | - |
| 22 | #16~20 태그 상세 | 동일 | - |
| 23 | 기법 간 일치도 분석 | M1~M6 순위 Kendall's τ + 합의도 히트맵 | C04, C17 |
| 24 | 권취 vs 중량 불량 비교 | 불량 유형별 Top-10 차이 | C11 |
| 24a | 불량률-태그 시계열 오버레이 | Top-3 태그 × 불량률 일별 연동 | C19 |
| 25 | 월별 추세 분석 | 3~8월 이상치 패턴 | C07 |
| 26 | 강종별 차이 | B5/D4/D5/N5 상관계수 비교 | C12 |
| 26c | 강종별 분석 전략 | 데이터 충분성 기준 및 Layer 0~2 정의 | - |
| 26d | 강종별 Top-20 비교 | ALL/N5/D5 기준 Top-20 히트맵 + 공통 핵심 태그 | C14 |
| 26e | 규격별 Top-10 변동 | N5/D5 규격별 순위 변동 및 Kendall's τ | C15 |
| 27 | **[Chapter 5] 시사점** | Top-20 태그의 공정 의미 | - |
| 28 | 개선 우선순위 제안 | 태그별 모니터링 강화 권고 + 실행 요약 대시보드 | C20 |
| 29 | 데이터 보강 요청 | 미수집 태그 수집 필요성 | - |
| 30 | 향후 분석 방향 | 코일 단위 분석, FDA, Conformal | - |
| 31 | 결론 | 핵심 3가지 요약 | - |
| 32 | 부록: 분석 환경 | Python 버전, 라이브러리 목록 | - |
| 33 | 부록: 전체 태그 순위표 | 91태그 앙상블 순위 전체 | - |

---

## 5. 산출물 명세

### 5.1 파일 구조

```
analysis_output/tag_defect_correlation/
│
├── 00_ANALYSIS_PLAN.md                   ← 본 문서 (계획서)
│
├── scripts/
│   ├── 01_data_extraction.py             ← Phase 1: 데이터 추출
│   ├── 02_correlation_analysis.py        ← Phase 2: M1/M2/M5/M6
│   ├── 03_ml_regression.py               ← Phase 2: M3/M4
│   ├── 04_ensemble_ranking.py            ← Phase 3: 앙상블 순위
│   └── 05_chart_generation.py           ← Phase 4: 차트 생성
│
├── data/
│   ├── tag_defect_matrix_ALL.parquet        ← Phase 1: 전체 합산 (기존 이름 변경)
│   ├── tag_defect_matrix_N5.parquet         ← Phase 1: N5 강종별 (신규)
│   ├── tag_defect_matrix_D5.parquet         ← Phase 1: D5 강종별 (신규)
│   ├── tag_defect_matrix_N5_SZ{sz}.parquet  ← Phase 1: N5 규격별 (신규, 3개)
│   ├── tag_defect_matrix_D5_SZ{sz}.parquet  ← Phase 1: D5 규격별 (신규, 3개)
│   ├── daily_coverage_report.json
│   ├── filter_application_stats.json        ← Phase 1: 필터 효과 통계 (신규)
│   ├── grade_size_coverage.json             ← Phase 1: 강종×규격 데이터 건수 (신규)
│   ├── results_m1_spearman_ALL.csv          ← Phase 2: 전체 합산 (이름 변경)
│   ├── results_m1_spearman_N5.csv           ← Phase 2: N5 강종별 (신규)
│   ├── results_m1_spearman_D5.csv           ← Phase 2: D5 강종별 (신규)
│   ├── results_m2_mannwhitney_ALL.csv
│   ├── results_m2_mannwhitney_N5.csv        ← 신규
│   ├── results_m2_mannwhitney_D5.csv        ← 신규
│   ├── results_m3_lgbm_importance_ALL.csv
│   ├── results_m3_lgbm_importance_N5.csv    ← 신규 (N5만, D5 부족)
│   ├── results_m4_quantile_ALL.csv
│   ├── results_m4_quantile_N5.csv           ← 신규
│   ├── results_m5_outlier_cross.csv
│   ├── results_m6_changepoint.csv
│   ├── top20_ensemble_ranking_ALL.csv       ← Phase 3 최종 산출 (이름 변경)
│   ├── top20_ensemble_ranking_N5.csv        ← Phase 3: N5 강종별 순위 (신규)
│   ├── top20_ensemble_ranking_D5.csv        ← Phase 3: D5 강종별 순위 (신규)
│   ├── top20_ensemble_ranking_grade_compare.csv  ← Phase 3: 강종 비교표 (신규)
│   └── grade_size_top10_variation.csv       ← Phase 3: 규격별 순위 변동 (신규)
│
├── charts/                                    ← Phase 4: PPTX 삽입용 차트 (20건)
│   ├── chart_01_spearman_heatmap.png
│   ├── chart_02_group_comparison_bar.png
│   ├── chart_03_top20_ranking.png
│   ├── chart_04_method_comparison_scatter.png
│   ├── chart_05_top5_boxplot_winding.png
│   ├── chart_06_top5_boxplot_weight.png
│   ├── chart_07_monthly_trend.png
│   ├── chart_08_category_radar.png
│   ├── chart_09_venn_diagram.png
│   ├── chart_10_defect_rate_timeseries.png
│   ├── chart_11_cohens_d_ranking.png
│   ├── chart_12_correlation_change_by_grade.png
│   ├── chart_13_filter_impact.png           ← 신규: 필터 데이터 감소 폭포수
│   ├── chart_14_grade_top20_heatmap.png     ← 신규: 강종별 Top-20 히트맵
│   ├── chart_15_size_variation.png          ← 신규: 규격별 Top-10 변동
│   ├── chart_16_filter_preset_compare.png   ← 신규: P2 vs P4 비교 산점도
│   ├── chart_17_method_agreement_heatmap.png  ← 신규: 기법 합의도 히트맵
│   ├── chart_18_ensemble_decomposition.png    ← 신규: 앙상블 점수 분해
│   ├── chart_19_defect_tag_overlay.png        ← 신규: 불량률-태그 시계열 오버레이
│   └── chart_20_actionable_summary.png        ← 신규: 실행 가능 요약 대시보드
│
├── diagnostics/                               ← Phase 1~2: 기법별 진단 차트 (16건)
│   ├── diag_data_coverage_summary.png         ← D15: 레이어별 데이터 충분성
│   ├── diag_filter_retention_rates.png        ← D16: 필터 잔존율
│   ├── D01_volcano_spearman.png               ← D01: M1 Volcano Plot
│   ├── D02_heatmap_spearman.png               ← D02: M1 통계량 유형 Heatmap
│   ├── D03_cohens_d_bar.png                   ← D03: M2 효과 크기 분포
│   ├── D04_violin_split.png                   ← D04: M2 Top-5 Violin
│   ├── D05_contingency_mosaic.png             ← D05: M5 2×2 분할표
│   ├── D06_scatter_or_vs_rho.png              ← D06: M5 OR vs ρ Scatter
│   ├── D07_changepoint_timeseries.png         ← D07: M6 변점 시계열
│   ├── D08_changepoint_bar.png                ← D08: M6 ρ 순위 바
│   ├── D09_lgbm_gain_split_importance.png     ← D09: M3 Gain vs Split
│   ├── D10_loocv_scatter.png                  ← D10: M3 LOO-CV Scatter
│   ├── D11_partial_dependence_top4.png        ← D11: M3 PDP
│   ├── D12_quantile_q90_diverging.png         ← D12: M4 계수 방향
│   ├── D13_quantile_q50_q75_q90_comparison.png ← D13: M4 Quantile 비교
│   └── D14_m3_vs_m4_rank_scatter.png          ← D14: M3 vs M4 교차
│
└── REPORT_tag_defect_pptx.md             ← Phase 5 최종 보고서 MD
```

### 5.2 주요 결과물 형식

**top20_ensemble_ranking.csv**:
```csv
rank,tag,category,column,description,
ensemble_score,m1_rho_winding,m1_rho_weight,m2_cohens_d,
m3_lgbm_importance,m4_quantile_coef,m5_odds_ratio,m6_changepoint_rho
1,PR6L1_ACT_TORQUE,Cat09b,Col1&Col3,"PR6 L1 실제 토크",...
2,...
```

**top20_ensemble_ranking_grade_compare.csv**:
```csv
tag,rank_ALL,rank_N5,rank_D5,common_count,category,column,description
PR6L1_ACT_TORQUE,1,3,2,3,Cat09b,Col1&Col3,"PR6 L1 실제 토크"
FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE,2,1,5,3,Cat03,Col3,"추출 빌렛 온도"
...
```

**REPORT_tag_defect_pptx.md**:
- GitHub Flavored Markdown
- 각 슬라이드 = `## Slide N: 제목` 섹션
- 차트: `![설명](charts/chart_NN_name.png)`
- 표: Markdown table 형식

---

## 6. 팀플레이 구성

복잡한 분석 단계는 병렬 에이전트로 분담하여 시간을 절약한다.

### 6.1 병렬 실행 가능 구간

```
Phase 1 완료 후 (4-way 병렬):
  ┌─ Agent-A: ALL 기준 M1/M2/M5/M6 (Script 02, tag_defect_matrix_ALL)
  ├─ Agent-B: ALL 기준 M3/M4 LightGBM (Script 03, tag_defect_matrix_ALL)
  ├─ Agent-C: N5 기준 M1/M2/M4 + N5 규격별 M1/M2 (Script 02/04, tag_defect_matrix_N5*)
  └─ Agent-D: D5 기준 M1/M2 + D5 규격별 M1/M2 (Script 02/04, tag_defect_matrix_D5*)

Phase 3 완료 후 (3-way 병렬):
  ┌─ Agent-E: 차트 세트 A (C01~C10, C17, C18 — 12건: 핵심 순위/앙상블)
  ├─ Agent-F: 차트 세트 B (C11~C16, C19, C20 — 8건: 강종/필터/실행용)
  └─ Agent-G: REPORT MD 슬라이드 1~25 초안 (강종 비교 슬라이드 포함)
```

### 6.2 에이전트 역할 분담

| 에이전트 | 역할 | 데이터 | 의존성 |
|---------|------|--------|--------|
| Main | Phase 0 환경 확인 + Phase 1 (Step 1-1 ~ 1-6) 전체 | - | 없음 |
| Agent-A | ALL: M1/M2/M5/M6 상관 분석 | tag_defect_matrix_ALL | Phase 1 완료 |
| Agent-B | ALL: M3/M4 ML 회귀 분석 | tag_defect_matrix_ALL | Phase 1 완료 |
| Agent-C | N5: M1/M2/M4 + N5 규격별 M1/M2 | tag_defect_matrix_N5* | Phase 1 완료 |
| Agent-D | D5: M1/M2 + D5 규격별 M1/M2 | tag_defect_matrix_D5* | Phase 1 완료 |
| Agent-E | 차트 세트 A (C01~C10, C17, C18: 핵심 순위/앙상블 12건) | Phase 3 결과 | Phase 3 완료 |
| Agent-F | 차트 세트 B (C11~C16, C19, C20: 강종/필터/실행용 8건) | Phase 3 결과 | Phase 3 완료 |
| Agent-G | 보고서 MD 슬라이드 1~25 초안 + 26a~26e | Phase 3 결과 | Phase 3 완료 |

---

## 7. 리스크 및 대응

| 리스크 | 확률 | 영향 | 대응 방안 |
|--------|:----:|:----:|----------|
| ClickHouse 쿼리 타임아웃 (91태그 × 184일) | 중 | 높음 | 태그 배치별 쿼리 (20태그씩 분할) |
| 불량 데이터 기간 내 레코드 부족 (<50건) | 저 | 높음 | 기간 확장 (2024-09~2025-08) 또는 전체 기간 사용 |
| LightGBM 과적합 (소량 데이터) | 중 | 중 | max_depth=3 제한 + LOO-CV 검증 |
| Top-20 태그가 동일 카테고리에 집중 | 중 | 중 | 카테고리별 최소 1개 강제 할당 (그룹 대표성 보장) |
| 일부 태그 Null 비율 > 50% | 중 | 중 | 해당 기간 Null 비율 확인 후 임계값 설정 (>30% Null 제외) |
| 불량률이 항상 0인 날 다수 | 높음 | 중 | 불량률 > 0인 날만 상관 분석에 포함 옵션 추가 |
| **필터 적용 시 강종별 데이터 부족** | 중 | 높음 | P2_OPTIMAL 프리셋으로 fallback (run_only+special_ops만 적용) |
| **N5/D5 강종별 일수 30일 미만** | 중 | 중 | ML 기법(M3/M4) 제외, M1(Spearman)/M2(Mann-Whitney)만 사용 |
| **규격별 불량 데이터 없음** | 높음 | 중 | 불량 데이터 강종별 JOIN 후 규격 필터 적용 확인, 없으면 Layer 2 스킵 |
| **강종별 필터 효과 편차** | 저 | 저 | 동일 P4_PER_TAG 프리셋 일관 적용 (공정 카테고리 기준 동일 필터) |

---

## 8. 결과 해석 기준

### 8.1 상관 강도 기준

| |ρ| 구간 | 해석 | 권고 조치 |
|:----------:|------|---------|
| 0.50 이상 | 강한 상관 | 즉시 모니터링 강화 대상 |
| 0.30~0.49 | 중간 상관 | 우선 모니터링 대상 |
| 0.10~0.29 | 약한 상관 | 참고 지표 |
| 0.10 미만 | 상관 없음 | 분석 제외 |

### 8.2 Cohen's d 효과 크기 기준

| |d| 구간 | 해석 |
|:----------:|------|
| 0.80 이상 | 큰 효과 — 고불량일과 정상일이 명확히 다름 |
| 0.50~0.79 | 중간 효과 — 통계적으로 의미 있는 차이 |
| 0.20~0.49 | 작은 효과 — 미미한 차이 |
| 0.20 미만 | 효과 없음 |

### 8.3 최종 해석 원칙

1. **앙상블 일치**: 6가지 기법 중 4개 이상에서 Top-30 포함 시 → **확정 핵심 태그**
2. **단일 기법 우수**: 특정 기법에서만 두드러질 경우 → **조건부 핵심 태그** (원인 분석 필요)
3. **도메인 합치**: Top-20 태그가 Column2(현업 수요)와 겹치면 → **골든 확인 태그**
4. **공정 논리**: 가열로 → 스탠드 → 핀치롤 순서의 인과 흐름과 Top-20 순서가 일치하는지 검토

### 8.4 강종별 해석 원칙

| 분류 | 정의 | 모니터링 전략 |
|------|------|-------------|
| **전공장 공통 핵심 태그** | ALL ∩ N5 ∩ D5 공통 Top-20 | 최우선 모니터링 (강종 무관) |
| **N5 특화 태그** | N5 Top-20 ∩ ALL Top-20, D5 미포함 | N5 생산 시 추가 모니터링 |
| **D5 특화 태그** | D5 Top-20 ∩ ALL Top-20, N5 미포함 | D5 생산 시 추가 모니터링 |
| **강종 전용 태그** | 특정 강종 Top-20에만 존재 | 해당 강종별 임계값 별도 설정 |

- **ALL ∩ N5 ∩ D5 공통 Top-20** → 최우선 모니터링 대상 (3개 Layer 모두 일치)
- **ALL에 있지만 N5·D5에 없는 태그** → 약한 강종 특이성 → 추가 조사 필요
- **N5 또는 D5에만 있는 태그** → 강종 의존적 → 강종별 독립 알람 권고

### 8.5 규격별 해석 원칙

| Kendall's τ (규격 간 순위 일치도) | 해석 | 권고 조치 |
|:--------------------------------:|------|---------|
| τ ≥ 0.70 | 규격 관계없이 동일 태그 중요 | 공통 임계값 설정 가능 |
| 0.50 ≤ τ < 0.70 | 부분 일치 — 일부 규격에서 차이 | 주요 규격 분리 모니터링 |
| τ < 0.50 | 규격별로 다른 태그가 중요 | **규격별 독립 임계값 설정 강력 권고** |

- **규격별 Top-10 순위가 크게 다른 태그**: 규격 의존성 높음 → 규격별 임계값 설정 필수
- **Kendall's τ < 0.5**: 규격별 독립 모니터링 설정 권고 → `/iba-tag` 분석 심화 실시

### 8.6 미채택 기법 향후 로드맵

전략문서(DEFECT_DATA_UTILIZATION_STRATEGY.md) 25+ 기법 중 현재 미채택이나, 데이터/인프라 조건 충족 시 도입 가능한 핵심 4건:

| 기법 | 전략문서 코드 | 미채택 이유 | 향후 적용 조건 |
|------|:----------:|-----------|-------------|
| A1 번들 시간 윈도우 | A1 | 코일(번들) 단위 추적 미구현 | D1 코일 추적 시스템 구축 시 |
| C1 불량 전조 패턴 | C1 | Lag 데이터 일별 집계만 가능 | 시간 단위 불량 데이터 확보 시 |
| C2 PCA 특성 추출 | C2 | 현재 단변량 분석 우선 | 단변량 결과 불충분 시 다변량 확장 |
| E1 Conformal Prediction | E1 | sklearn 최신 버전 + 모델 배포 필요 | 모델 운영 배포 단계에서 적용 |

> 상기 기법은 본 프로젝트 M1~M6 결과를 기반으로, 후속 프로젝트에서 단계적으로 도입한다.

---

## 다음 단계 확인 요청 사항

아래를 확인 후 실행 단계를 진행한다:

- [x] **Phase 0 우선 실행 여부**: ClickHouse/MariaDB 기간 데이터 확인 먼저 진행 → **결정: Phase 0 우선 실행**
- [x] **강종별 서브분석 범위**: 전체 합산만 vs 강종별 분리 병행 → **결정: Layer 0/1/2 계층 분석 병행**
- [ ] **배치 쿼리 전략**: 91태그를 몇 개씩 나눠서 쿼리할지 (20개 배치 기본)?
- [x] **차트 우선순위**: C01~C20 전체 20종 PPTX 차트 + D01~D16 진단 차트 16건 확정 → **결정: 전체 36건 생성**
- [ ] **팀플레이 병렬 에이전트 사용 여부**: Phase 2 이후 병렬 에이전트 활성화?

---

*작성: IBA 데이터 분석팀 | 기준: THREE_COLUMN_TAG_REGISTRY.md + DEFECT_DATA_UTILIZATION_STRATEGY.md*
*참조 방법론: A4(강종매핑) + B1(이상치 교차) + B2(LightGBM 회귀) + C3(변점) + C4(프로파일) + E2(BOCPD) + E3(분위회귀)*

# 품질/불량 DB 데이터 활용 극대화 전략

> **문서 성격**: 조사·분석 보고서 + 구현 가이드
> **작성일**: 2026-02-25
> **대상**: DH Steel IBA 데이터 프로파일링 프로젝트

---

## 목차

1. [개요 및 배경](#1-개요-및-배경)
2. [데이터 한계 상세 분석 (7가지)](#2-데이터-한계-상세-분석)
3. [데이터 보정/보완 방안 (Section A)](#3-데이터-보정보완-방안-section-a-data-level-fixes)
4. [모델링/분석 전략 (Section B)](#4-모델링분석-전략-section-b-modeling-approaches)
5. [대안적 분석 전략 (Section C)](#5-대안적-분석-전략-section-c-alternative-strategies)
6. [데이터 보강 요청 사항 (Section D)](#6-데이터-보강-요청-사항-section-d-customer-data-enrichment)
7. [**확장 탐색 기법 (Section E)**](#7-확장-탐색-기법-section-e-extended-techniques) ← 신규 추가
8. [우선순위 및 실행 로드맵](#8-우선순위-및-실행-로드맵)
9. [기법 간 비교 매트릭스](#9-기법-간-비교-매트릭스)

---

## 1. 개요 및 배경

### 1.1 IT 담당자 의견 정리

고객사 IT 담당자로부터 다음과 같은 의견을 받음:

> "품질관리/불량 데이터(`defect_selection_status`, `memo_prod_result`)는 **보고 목적으로 작성된 자료**이므로 모델 세팅이나 데이터 분석에 직접 활용하기에는 한계가 있다."

**핵심 의미**: 이 데이터는 경영 보고·집계 목적으로 설계되었으며, 개별 코일/압연 단위의 원인 추적이나 실시간 품질 예측 모델의 학습 라벨로 사용하기에는 해상도·정밀도·정규화 수준이 부족하다.

**그럼에도 불구하고**, 현재 보유한 데이터에서 최대한의 분석적 가치를 추출하는 것이 본 문서의 목표이다.

### 1.2 보유 데이터 테이블 요약

| 테이블 | 레코드 수 | 시간 해상도 | 핵심 컬럼 | 용도 |
|--------|-----------|------------|-----------|------|
| `defect_selection_status` | ~413건 | **일별** 집계 | production_date, steel_grade(SD400/SD500/500N/B500B), size, production_quantity/weight, winding_defect_quantity/weight/rate, weight_defect_quantity/weight/rate | 일별 불량 현황 보고 |
| `memo_prod_result` | ~1,086건 | **번들 단위** | bundle_no, production_datetime, product_steel_grade, size, weight_error, remarks(자유 텍스트) | 번들별 생산 결과 기록 |
| `iba_timeseries_unified_alter` | ~939,050건 | **초 단위** | BASE_TIME, OPERATION_STATUS, 85개 센서 태그 (온도, 속도, 전류, 압력 등) | 설비 공정 시계열 |

### 1.3 기존 분석 뷰 (Views)

| 뷰 | 설명 | 위치 |
|----|------|------|
| `v_production_defect_analysis` | 일별 집계 기반 (memo_prod_result + defect_selection_status JOIN) | `schema/production_defect_views.sql:12` |
| `v_timeseries_production_quality` | 번들 단위 시계열 (remarks, weight_error, 이상 플래그 포함) | `schema/production_defect_views.sql:101` |
| `v_monthly_defect_stats` | 월별 불량 통계 | `schema/defect_selection_status_schema.sql:65` |
| `v_steel_grade_defect_stats` | 강종별 불량 통계 | `schema/defect_selection_status_schema.sql:93` |

### 1.4 분석 활용 목표

1. **공정 파라미터 ↔ 불량 상관관계 규명**: 어떤 센서 값 패턴이 불량과 연관되는가?
2. **불량 전조 탐지**: 불량 발생 전 D-1~D-3에 나타나는 설비 이상 신호 포착
3. **설비 건강 지수 구축**: 다수 이상치 탐지 기법의 결과를 통합한 종합 점수
4. **강종별 차별화 분석**: 강종마다 다른 불량 패턴 및 임계값 식별

---

## 2. 데이터 한계 상세 분석

### 한계 L1: 시간 해상도 불일치

| 항목 | 내용 |
|------|------|
| **원인** | 불량 데이터는 일별 집계, IBA 센서는 초 단위 기록 |
| **영향** | 하루에 수백~수천 개 코일을 생산하므로, 일별 불량률로는 어떤 코일(시점)에서 불량이 발생했는지 특정 불가 |
| **심각도** | ★★★★★ (최고) — 가장 근본적인 한계 |
| **기존 대응** | `data_preparation.py`: IBA를 일별 avg/min/max/std로 집계 → defect 일별 데이터와 merge하여 `tag_defect_matrix.parquet` 생성 |
| **참조** | `scripts/deep_analysis/data_preparation.py:40-95` (load_tag_data, 일별 집계) |

### 한계 L2: 강종 코드 불일치

| 항목 | 내용 |
|------|------|
| **원인** | defect 테이블은 한국 규격 코드(SD400, SD500, 500N, B500B), IBA는 내부 코드(D4, D5, N5, B5) 사용 |
| **영향** | 강종별 필터링 시 JOIN 불가, 현재 전체 강종 합산 사용으로 강종 고유 패턴 손실 |
| **심각도** | ★★★★ (높음) — 쉽게 해결 가능하나 현재 미적용 |
| **기존 대응** | `common.py:389-399` — `fetch_coil_aggregated_data()`에서 `steel_grade` 필터 없이 전체 합산 |
| **매핑 관계** | SD400→D4, SD500→D5, 500N→N5, B500B→B5, SD500S→(확인 필요), 500B→B5 |

### 한계 L3: 번들-코일 연결 부재

| 항목 | 내용 |
|------|------|
| **원인** | `memo_prod_result.production_datetime`은 번들 완료 시점이며, IBA 시계열의 개별 코일 압연 시작/종료 시점과 직접 매핑 불가 |
| **영향** | 번들 단위 불량 정보(remarks, weight_error)를 해당 코일의 IBA 시계열 구간에 매핑할 수 없음 |
| **심각도** | ★★★★ (높음) — 코일 단위 분석의 핵심 걸림돌 |
| **기존 대응** | `v_timeseries_production_quality` VIEW가 번들 정보에 일별 불량률을 JOIN하지만, 개별 코일 IBA 구간 연결은 미구현 |
| **참조** | `schema/production_defect_views.sql:101-200` |

### 한계 L4: remarks 비정규화

| 항목 | 내용 |
|------|------|
| **원인** | `memo_prod_result.remarks`가 자유 텍스트 필드로, 불량 유형을 비표준적으로 기록 |
| **영향** | 동일 불량 유형이 10+ 변형으로 기록됨 (예: '선별(권취불량)', '권취x', '선별)권취', '선별_권취x', '선별(권취x)', '선별_권취X') |
| **심각도** | ★★★ (중간) — 매핑 확장으로 해결 가능 |
| **기존 대응** | `scripts/deep_analysis/config.py:159-181` — `DEFECT_TYPE_MAPPING`에 12개 항목 매핑 |
| **현재 매핑 현황** | 권취불량 7개, 중량불량 3개(중/상/하), 기타 4개(선별, 토션, 용접끊김, 딱지, 돼지꼬리) |

**현재 DEFECT_TYPE_MAPPING (12개):**

```python
DEFECT_TYPE_MAPPING = {
    '선별(권취불량)': '권취불량', '권취x': '권취불량', '선별)권취': '권취불량',
    '선별_권취x': '권취불량', '선별(권취x)': '권취불량', '선별_권취X': '권취불량',
    '별도(권취불량)': '권취불량',
    '중': '중량-M', '상': '중량-H', '하': '중량-L',
    '선별': '선별', '선별(토션)': '토션', '별도(토션)': '토션',
    '비정량_용접끊김': '용접끊김', '별도(딱지)': '딱지', '선별(돼지꼬리)': '돼지꼬리',
}
```

### 한계 L5: 소량 데이터

| 항목 | 내용 |
|------|------|
| **원인** | 2023년~현재 약 2년간의 데이터, 일별 413건, 번들 1,086건 |
| **영향** | 통계적 검정력 부족, 일반적 ML 분류/회귀 모델 학습 데이터 부족, 과적합 위험 |
| **심각도** | ★★★★ (높음) — 구조적 한계, 데이터 자체의 증가만이 근본 해결 |
| **기존 대응** | 전체 강종 합산(common.py), 비지도 이상치 탐지 위주 분석 |
| **강종별 생산일수** | B5:5일, D4:8일, D5:14일, N5:30일 (매우 적음) |

### 한계 L6: 강종별 필터 미적용

| 항목 | 내용 |
|------|------|
| **원인** | 소량 데이터 문제를 회피하기 위해 의도적으로 전체 합산 사용 |
| **영향** | 강종 고유의 불량 패턴 희석, 각 강종의 최적 공정 파라미터 범위 차이 무시 |
| **심각도** | ★★★ (중간) — L5와 연동된 파생 문제 |
| **기존 대응** | `common.py:366` — 주석에 "개별 강종 생산일수가 5~30일로 매우 적어 공장 전체 가동일 기준 집계" 명시 |
| **참조** | `scripts/additional_methods/common.py:357-427` |

### 한계 L7: 불량률 = 0인 날 다수

| 항목 | 내용 |
|------|------|
| **원인** | 실제로 불량이 적거나, 불량 집계가 일부 날에만 기록됨 |
| **영향** | 이진 분류(불량 유/무) 시 극도의 클래스 불균형 (예: 불량일 < 20%), 분류 모델 편향 |
| **심각도** | ★★★ (중간) — 모델링 전략으로 대응 가능 |
| **기존 대응** | `data_preparation.py:134-137` — `has_defect`, `has_winding_defect`, `has_weight_defect` 이진 변수 생성 |

---

## 3. 데이터 보정/보완 방안 (Section A: Data-Level Fixes)

### A1. 번들 시간 윈도우 재구성

| 항목 | 내용 |
|------|------|
| **대응 한계** | L1(시간 해상도), L3(번들-코일 연결) |
| **난이도** | ★★★ (중) |
| **기대효과** | ★★★★★ (높음) |

**개요**: `memo_prod_result.production_datetime` 기반으로 IBA 시계열과 시간 매칭하여, 번들 단위 품질 라벨을 IBA 시간 구간에 연결한다.

**구현 방향**:

```python
# 의사 코드: 번들-IBA 시간 윈도우 매칭
def match_bundle_to_iba(bundle_df, iba_df, window_minutes=30):
    """
    memo_prod_result.production_datetime를 기준으로
    해당 번들의 IBA 시계열 구간을 추정

    가정: production_datetime ≈ 번들 완료 시점
    → 그 이전 window_minutes 구간이 해당 번들의 압연 구간
    """
    results = []
    for _, bundle in bundle_df.iterrows():
        end_time = bundle['production_datetime']
        start_time = end_time - timedelta(minutes=window_minutes)

        # IBA 시계열에서 해당 구간 추출
        mask = (iba_df['BASE_TIME'] >= start_time) & \
               (iba_df['BASE_TIME'] <= end_time) & \
               (iba_df['OPERATION_STATUS'] == 'RUN')

        iba_segment = iba_df[mask]

        if len(iba_segment) > 0:
            # 구간 통계 산출 (avg, std, min, max, range, skew)
            stats = iba_segment[tag_cols].agg(['mean', 'std', 'min', 'max'])
            stats['bundle_no'] = bundle['bundle_no']
            stats['weight_error'] = bundle['weight_error']
            stats['remarks'] = bundle['remarks']
            results.append(stats)

    return pd.DataFrame(results)
```

**윈도우 크기 추정 방법**:
1. IBA에서 `OPERATION_STATUS`가 `RUN`→`TRANS` 전환하는 이벤트 간격 분포 분석
2. `memo_prod_result`의 동일 날짜 번들 간 `production_datetime` 간격 분포 분석
3. 두 분포의 중앙값을 교차 검증하여 적정 윈도우 크기 결정

**참고**: `v_timeseries_production_quality` VIEW가 이미 번들-일별불량 JOIN을 제공하지만, IBA 초 단위 시계열과의 직접 연결은 미구현 상태.

**SQL 예시 (윈도우 매칭)**:
```sql
-- 번들별 IBA 시계열 구간 통계 (ClickHouse)
SELECT
    m.bundle_no,
    m.production_datetime,
    m.weight_error,
    m.remarks,
    avg(t.HEATING_TEMPERATURE_01) as avg_heating_temp,
    stddevPop(t.HEATING_TEMPERATURE_01) as std_heating_temp,
    avg(t.PR6_SPEED) as avg_pr6_speed,
    stddevPop(t.PR6_SPEED) as std_pr6_speed
FROM memo_prod_result m
JOIN iba_timeseries_unified_alter t
    ON t.BASE_TIME BETWEEN
        subtractMinutes(m.production_datetime, 30)
        AND m.production_datetime
    AND t.OPERATION_STATUS = 'RUN'
GROUP BY m.bundle_no, m.production_datetime, m.weight_error, m.remarks
```

---

### A2. remarks 정규화 완성

| 항목 | 내용 |
|------|------|
| **대응 한계** | L4(remarks 비정규화) |
| **난이도** | ★ (낮음) |
| **기대효과** | ★★★ (중) |

**개요**: `DEFECT_TYPE_MAPPING`을 전수 조사 후 확장하고, regex 기반 fuzzy matching을 추가한다.

**구현 방향**:

```python
import re

# Step 1: 전수 조사 — remarks 고유값 전체 목록 추출
# SQL: SELECT DISTINCT remarks FROM memo_prod_result WHERE remarks IS NOT NULL

# Step 2: 확장된 매핑 (regex 기반)
DEFECT_TYPE_PATTERNS = [
    # 권취불량 (모든 변형 포괄)
    (re.compile(r'권취|coil.*(defect|bad|불량)', re.IGNORECASE), '권취불량'),

    # 중량불량
    (re.compile(r'^중$|중량.*불량|weight.*(error|defect)', re.IGNORECASE), '중량불량'),
    (re.compile(r'^상$'), '중량-H'),
    (re.compile(r'^하$'), '중량-L'),

    # 토션
    (re.compile(r'토션|torsion', re.IGNORECASE), '토션'),

    # 용접
    (re.compile(r'용접|끊김|welding', re.IGNORECASE), '용접끊김'),

    # 딱지
    (re.compile(r'딱지|scale|scab', re.IGNORECASE), '딱지'),

    # 돼지꼬리
    (re.compile(r'돼지|꼬리|pigtail', re.IGNORECASE), '돼지꼬리'),

    # 선별 (가장 마지막, 가장 넓은 매칭)
    (re.compile(r'선별|select', re.IGNORECASE), '선별'),
]

def normalize_remarks(raw_remarks: str) -> str:
    """remarks 텍스트를 정규화된 불량 유형으로 변환"""
    if not raw_remarks or pd.isna(raw_remarks):
        return '정상'

    raw = raw_remarks.strip()

    # 1차: 기존 exact match
    if raw in DEFECT_TYPE_MAPPING:
        return DEFECT_TYPE_MAPPING[raw]

    # 2차: regex pattern match (순서 중요 — 구체적 패턴 먼저)
    for pattern, defect_type in DEFECT_TYPE_PATTERNS:
        if pattern.search(raw):
            return defect_type

    # 미매핑 → 로그 + '기타불량' 반환
    logging.warning(f"미매핑 remarks: '{raw}'")
    return '기타불량'
```

**적용 위치**: `scripts/deep_analysis/config.py:159-181` (기존 `DEFECT_TYPE_MAPPING` 옆에 추가)

**검증 방법**:
```sql
-- 현재 remarks 고유값 및 빈도 확인
SELECT remarks, COUNT(*) as cnt
FROM memo_prod_result
WHERE remarks IS NOT NULL AND remarks != ''
GROUP BY remarks
ORDER BY cnt DESC
```

---

### A3. weight_error를 중량불량 프록시로 활용

| 항목 | 내용 |
|------|------|
| **대응 한계** | L1(시간 해상도), L5(소량 데이터) |
| **난이도** | ★ (낮음) |
| **기대효과** | ★★★ (중) |

**개요**: `memo_prod_result.weight_error`의 절대값/비율을 **연속값 품질 지표**로 활용한다. 이진 분류(불량 유/무) 대신 연속 변수 회귀를 통해 소량 데이터 문제를 완화.

**이미 구현된 기반**:
- `v_timeseries_production_quality` VIEW에 `weight_error_pct` (= |weight_error| / theoretical_weight × 100) 및 `weight_anomaly_flag` (5% 초과 시 1) 계산됨
- 참조: `schema/production_defect_views.sql:132-135`

**추가 활용 방향**:

```python
# weight_error를 다단계 품질 지표로 변환
def create_weight_quality_features(bundle_df):
    """
    weight_error → 다양한 품질 파생 변수 생성
    """
    df = bundle_df.copy()

    # 1. 절대 오차
    df['abs_weight_error'] = df['weight_error'].abs()

    # 2. 비율 오차 (theoretical_weight 대비)
    df['weight_error_pct'] = np.where(
        df['theoretical_weight'] > 0,
        df['abs_weight_error'] / df['theoretical_weight'] * 100,
        np.nan
    )

    # 3. 오차 방향 (양: 과중, 음: 미달)
    df['weight_direction'] = np.sign(df['weight_error'])

    # 4. 심각도 등급 (연속→범주)
    df['weight_severity'] = pd.cut(
        df['weight_error_pct'],
        bins=[0, 1, 3, 5, 10, float('inf')],
        labels=['정상', '경미', '주의', '불량', '심각']
    )

    # 5. 일별 집계 시 활용할 수 있는 통계
    daily_stats = df.groupby(df['production_datetime'].dt.date).agg({
        'weight_error_pct': ['mean', 'std', 'max'],
        'abs_weight_error': ['mean', 'sum'],
        'weight_direction': 'mean',  # 편향 방향 (양이면 과중 경향)
    })

    return df, daily_stats
```

**핵심 장점**: 413건의 이진 라벨 대신 1,086건의 연속값 라벨 확보 → 회귀 모델에 더 적합.

---

### A4. 강종 코드 매핑 테이블

| 항목 | 내용 |
|------|------|
| **대응 한계** | L2(강종 코드 불일치), L6(강종별 필터 미적용) |
| **난이도** | ★ (낮음) |
| **기대효과** | ★★★★★ (높음) |

**개요**: defect 테이블의 한국 규격 코드와 IBA의 내부 코드를 통합 매핑하여 강종별 분석을 활성화한다.

**매핑 테이블**:

```python
STEEL_GRADE_MAPPING = {
    # defect_selection_status.steel_grade → IBA 내부 코드
    'SD400':  'D4',
    'SD500':  'D5',
    '500N':   'N5',
    'B500B':  'B5',
    '500B':   'B5',   # 변형
    'SD500S': 'D5',   # SD500 계열 (확인 필요)
}

# 역매핑
IBA_TO_DEFECT_GRADE = {v: k for k, v in STEEL_GRADE_MAPPING.items()}
```

**적용 예시 (common.py 수정 방향)**:

```python
def fetch_coil_aggregated_data(client, grade, available_cols):
    """기존: 전체 합산 → 개선: 강종 필터 적용 (fallback: 전체)"""

    defect_grades = [k for k, v in STEEL_GRADE_MAPPING.items() if v == grade]

    if defect_grades:
        grade_filter = "AND steel_grade IN ({})".format(
            ", ".join(f"'{g}'" for g in defect_grades)
        )
    else:
        grade_filter = ""  # fallback: 전체 합산

    query_defects = f"""
    SELECT
        production_date as prod_date,
        COALESCE(sum(total_defect_quantity), 0) as defect_count,
        COALESCE(sum(production_quantity), 0) as total_count
    FROM defect_selection_status
    WHERE production_date >= '{DEFAULT_START_DATE}'
      AND production_date < '{DEFAULT_END_DATE}'
      {grade_filter}
    GROUP BY prod_date
    ORDER BY prod_date
    """
    # ... 이하 동일
```

**주의**: 강종별 필터 적용 시 레코드 수가 급감하므로(B5:5일, D4:8일 등), 분석 방법을 소량 데이터에 적합한 기법(B6 베이지안, C4 프로파일 비교 등)으로 전환해야 한다.

---

### A5. IBA 공정 단계 시간 정렬

| 항목 | 내용 |
|------|------|
| **대응 한계** | L1(시간 해상도), L3(번들-코일 연결) |
| **난이도** | ★★★ (중) |
| **기대효과** | ★★★★★ (높음) |

**개요**: IBA 시계열의 `OPERATION_STATUS` 전환 이벤트를 기반으로 개별 코일의 압연 구간을 식별한다.

**구현 방향**:

```python
def identify_coil_segments(iba_df):
    """
    OPERATION_STATUS 변화 이벤트 기반 코일 압연 구간 식별
    RUN 시작 → RUN 종료(TRANS 전환) = 하나의 코일 압연 구간
    """
    # OPERATION_STATUS 변화점 탐지
    status_changes = iba_df['OPERATION_STATUS'] != iba_df['OPERATION_STATUS'].shift(1)
    change_points = iba_df[status_changes].copy()

    segments = []
    run_start = None

    for idx, row in change_points.iterrows():
        if row['OPERATION_STATUS'] == 'RUN' and run_start is None:
            run_start = row['BASE_TIME']
        elif row['OPERATION_STATUS'] != 'RUN' and run_start is not None:
            run_end = row['BASE_TIME']
            duration = (run_end - run_start).total_seconds()

            # 의미 있는 구간만 (최소 10초 이상)
            if duration >= 10:
                segments.append({
                    'start_time': run_start,
                    'end_time': run_end,
                    'duration_sec': duration,
                })
            run_start = None

    return pd.DataFrame(segments)
```

```sql
-- ClickHouse: OPERATION_STATUS 전환점 조회
SELECT
    BASE_TIME,
    OPERATION_STATUS,
    neighbor(OPERATION_STATUS, -1) as prev_status,
    neighbor(BASE_TIME, -1) as prev_time,
    dateDiff('second', neighbor(BASE_TIME, -1), BASE_TIME) as gap_sec
FROM iba_timeseries_unified_alter
WHERE OPERATION_STATUS != neighbor(OPERATION_STATUS, -1)
ORDER BY BASE_TIME
```

**번들 매칭**: 식별된 코일 구간을 `memo_prod_result.production_datetime`과 시간순으로 매칭 (가장 가까운 구간 할당).

---

## 4. 모델링/분석 전략 (Section B: Modeling Approaches)

### B1. 이상치-우선 접근법 (Anomaly-First)

| 항목 | 내용 |
|------|------|
| **적합도** | ★★★★★ |
| **대응 한계** | L1, L5, L7 |
| **핵심 아이디어** | 비지도 이상치 탐지 결과와 고불량일을 교차 검증 |

**개요**: 이미 보유한 6가지 이상치 탐지 기법의 결과를 활용하여, 이상치 탐지 결과와 불량 데이터를 교차 검증한다. **라벨이 부족해도 비지도 학습은 가능**하다는 점이 핵심.

**기존 보유 이상치 탐지 기법**:
1. IQR (`steel_grade_iqr_analysis_v2/`)
2. Adjusted IQR (`steel_grade_iqr_analysis_v2/`)
3. CUSUM/EWMA (`steel_grade_iqr_analysis_v2/cusum_ewma/`)
4. Rolling Z-Score (`steel_grade_iqr_analysis_v2/`)
5. Mahalanobis (`mahalanobis_realdata/`)
6. Context-Aware (`context_aware_outlier/`)

**구현 방향**:

```python
def anomaly_defect_cross_validation(outlier_dates, defect_df):
    """
    이상치 탐지 결과와 고불량일 교차 검증

    지표:
    - 이상치일 중 고불량일 비율 (Precision-like)
    - 고불량일 중 이상치일 비율 (Recall-like)
    - 교차율 vs 우연 기대치 비교 (Fisher's exact test)
    """
    # 고불량일 정의: total_defect_rate 상위 20%
    high_defect_threshold = defect_df['total_defect_rate'].quantile(0.80)
    high_defect_dates = set(
        defect_df[defect_df['total_defect_rate'] >= high_defect_threshold]['date']
    )

    outlier_set = set(outlier_dates)

    # 교차 분석
    overlap = outlier_set & high_defect_dates

    # Fisher's exact test (이상치-불량 연관 유의성)
    from scipy.stats import fisher_exact
    all_dates = set(defect_df['date'])
    table = [[len(overlap), len(outlier_set - high_defect_dates)],
             [len(high_defect_dates - outlier_set),
              len(all_dates - outlier_set - high_defect_dates)]]
    odds_ratio, p_value = fisher_exact(table)

    return {
        'precision': len(overlap) / len(outlier_set) if outlier_set else 0,
        'recall': len(overlap) / len(high_defect_dates) if high_defect_dates else 0,
        'odds_ratio': odds_ratio,
        'p_value': p_value,
    }
```

**장점**: 라벨 불요, 기존 분석 결과 100% 재활용, 해석 용이.

---

### B2. 불량률 회귀 (Rate Regression)

| 항목 | 내용 |
|------|------|
| **적합도** | ★★★★★ |
| **대응 한계** | L5(소량), L7(클래스 불균형) |
| **핵심 아이디어** | 이진 분류 대신 연속값(불량률) 회귀 → 소량 데이터에 더 적합 |

**구현 방향**:

```python
from sklearn.ensemble import GradientBoostingRegressor
from sklearn.model_selection import LeaveOneOut, cross_val_score

def defect_rate_regression(tag_defect_matrix):
    """
    일별 IBA 통계량 → 불량률 연속값 예측 (회귀)

    이진 분류(불량 유/무)는 413건으로 부족하지만,
    연속 회귀는 모든 데이터 포인트를 활용 가능
    """
    X = tag_defect_matrix[feature_cols]
    y = tag_defect_matrix['total_defect_rate']  # 연속값

    # Leave-One-Out CV (소량 데이터 최적)
    model = GradientBoostingRegressor(
        n_estimators=100,
        max_depth=3,      # 과적합 방지
        min_samples_leaf=5,  # 소량 데이터 보호
        learning_rate=0.05,
    )

    loo = LeaveOneOut()
    scores = cross_val_score(model, X, y, cv=loo, scoring='r2')

    # 전체 학습 후 feature importance
    model.fit(X, y)
    importance = pd.Series(model.feature_importances_, index=feature_cols)
    top_features = importance.nlargest(20)

    return model, top_features, scores.mean()
```

**장점**: 클래스 불균형 문제 자체가 소멸, LOO-CV로 소량 데이터 검증 가능.

---

### B3. Multi-Instance Learning (MIL)

| 항목 | 내용 |
|------|------|
| **적합도** | ★★★ |
| **대응 한계** | L1(시간 해상도), L3(번들-코일 연결) |
| **핵심 아이디어** | 번들 = bag, IBA 시점 = instance → bag 레벨 라벨 활용 |

**개요**: "이 번들은 불량이다"라는 bag-level 라벨만 있고, 어떤 시점(instance)이 원인인지 모르는 상황에 적합한 약지도학습(Weakly Supervised Learning) 프레임워크.

**구현 개요**:

```python
# 개념적 구현 (MIL 프레임워크)
# 의존: mil-python 또는 직접 구현

class BundleMIL:
    """
    Bag: 번들 (A1 방안으로 매칭된 IBA 구간)
    Instance: 해당 구간 내 각 시점(초 단위)의 센서 벡터
    Label: 번들 단위 불량 유/무 (remarks 정규화 결과)

    Bag이 '불량'이면 최소 1개 Instance가 불량 원인
    → MIL이 해당 Instance를 자동 식별
    """
    def __init__(self):
        # Attention-based MIL pooling
        self.attention_net = ...
        self.classifier = ...

    def forward(self, bag_instances):
        # Instance별 attention weight 산출
        # → 불량 기여도 높은 시점 자동 식별
        attention_weights = self.attention_net(bag_instances)
        bag_representation = (attention_weights * bag_instances).sum(dim=0)
        return self.classifier(bag_representation)
```

**전제 조건**: A1(번들 시간 윈도우) 완료 필요. A1 + A2(remarks 정규화) → B3 순차 적용.

**적합 시나리오**: 충분한 번들 수(현재 1,086건) 확보 후, 불량 번들이 100건+ 있을 때 효과적.

---

### B4. 준지도학습 (Semi-Supervised Learning)

| 항목 | 내용 |
|------|------|
| **적합도** | ★★★ |
| **대응 한계** | L5(소량 라벨 데이터), L7(클래스 불균형) |
| **핵심 아이디어** | 라벨 없는 IBA 데이터(939K건) + 소량 라벨(413~1,086건) 결합 |

**구현 방향**:

```python
from sklearn.semi_supervised import LabelPropagation, LabelSpreading

def semi_supervised_analysis(iba_daily_stats, defect_labels):
    """
    라벨 있는 데이터: 불량 기록이 있는 413일
    라벨 없는 데이터: IBA만 있고 불량 기록 없는 날

    Label Propagation: 라벨 있는 데이터의 패턴을
    유사한 라벨 없는 데이터로 전파
    """
    X = iba_daily_stats[feature_cols].values

    # 라벨: 불량일 = 1, 정상일 = 0, 라벨 없음 = -1
    y = np.full(len(X), -1)  # 기본: unlabeled
    for idx in labeled_indices:
        y[idx] = defect_labels[idx]

    model = LabelSpreading(kernel='knn', n_neighbors=7, alpha=0.8)
    model.fit(X, y)

    # 전파된 라벨 확인
    predicted_labels = model.transduction_
    label_distributions = model.label_distributions_

    return predicted_labels, label_distributions
```

**Self-Training 변형**:

```python
from sklearn.semi_supervised import SelfTrainingClassifier
from sklearn.ensemble import RandomForestClassifier

def self_training_defect(X_all, y_partial):
    """
    단계적 자기학습:
    1. 라벨 있는 데이터로 초기 모델 학습
    2. 높은 확신도의 예측을 pseudo-label로 추가
    3. 반복
    """
    base_model = RandomForestClassifier(n_estimators=100, max_depth=5)
    self_trainer = SelfTrainingClassifier(
        base_model,
        threshold=0.9,  # 높은 확신도만 채택
        max_iter=10,
    )
    self_trainer.fit(X_all, y_partial)
    return self_trainer
```

---

### B5. 전이학습 (Transfer Learning)

| 항목 | 내용 |
|------|------|
| **적합도** | ★★ |
| **대응 한계** | L5(소량 데이터) |
| **핵심 아이디어** | 유사 공정(타 철강사, 타 라인) 사전학습 모델 활용 |

**현재 적용 어려운 이유**:
- 유사 공정 데이터 미보유
- 공개된 철강 압연 품질 사전학습 모델 부재

**향후 적용 가능 시나리오**:
- 동일 공장 다른 라인의 데이터 확보 시
- 산업별 사전학습 모델(예: 공정 이상 탐지 foundation model) 등장 시
- 동일 설비 이전 기간 데이터 축적 후 도메인 적응(Domain Adaptation)

---

### B6. 베이지안 접근법 (Bayesian Methods)

| 항목 | 내용 |
|------|------|
| **적합도** | ★★★★ |
| **대응 한계** | L5(소량 데이터), L7(클래스 불균형) |
| **핵심 아이디어** | 사전분포에 도메인 지식 반영, 소량 데이터에서도 강건한 추정 |

**구현 방향**:

```python
from sklearn.linear_model import BayesianRidge
from sklearn.gaussian_process import GaussianProcessRegressor
from sklearn.gaussian_process.kernels import RBF, ConstantKernel

def bayesian_defect_regression(X, y):
    """
    베이지안 릿지 회귀: 소량 데이터에서 과적합 방지 + 불확실성 정량화

    장점:
    - 사전분포가 정규화 역할 → 소량 데이터 과적합 방지
    - 예측값 + 불확실성 구간 동시 제공
    """
    model = BayesianRidge(
        alpha_1=1e-6, alpha_2=1e-6,  # 사전분포 하이퍼파라미터
        lambda_1=1e-6, lambda_2=1e-6,
        compute_score=True,
    )
    model.fit(X, y)

    y_pred, y_std = model.predict(X, return_std=True)

    return model, y_pred, y_std

def gaussian_process_defect(X, y):
    """
    가우시안 프로세스 회귀: 비선형 관계 + 불확실성

    장점: 소량 데이터에서 특히 강력, 비모수적 접근
    주의: 데이터 수 > 1000 시 계산 비용 증가
    """
    kernel = ConstantKernel(1.0) * RBF(length_scale=1.0)
    gp = GaussianProcessRegressor(
        kernel=kernel,
        n_restarts_optimizer=10,
        alpha=0.1,  # 노이즈 수준
    )
    gp.fit(X, y)

    y_pred, y_std = gp.predict(X, return_std=True)

    return gp, y_pred, y_std
```

**도메인 지식 반영 예시**:
- 가열로 온도 편차 > X°C → 불량 사전확률 증가 (도메인 전문가 인터뷰 기반)
- 핀치롤 속도 변동 > Y% → 권취불량 사전확률 증가

---

### B7. 데이터 증강 (Data Augmentation)

| 항목 | 내용 |
|------|------|
| **적합도** | ★★★ |
| **대응 한계** | L5(소량), L7(클래스 불균형) |
| **핵심 아이디어** | 합성 데이터 생성으로 학습 데이터 보충 |

**구현 방향**:

```python
from imblearn.over_sampling import SMOTE, ADASYN

def augment_defect_data(X, y_binary):
    """
    클래스 불균형 해소를 위한 합성 데이터 생성

    SMOTE: k-NN 기반 합성 (소수 클래스 오버샘플링)
    ADASYN: 적응형 합성 (경계 영역 집중)
    """
    # SMOTE (불량일이 충분히 적을 때)
    if y_binary.sum() >= 6:  # k_neighbors 기본값 5 → 최소 6개 필요
        smote = SMOTE(
            sampling_strategy='auto',
            k_neighbors=min(5, y_binary.sum() - 1),
            random_state=42,
        )
        X_resampled, y_resampled = smote.fit_resample(X, y_binary)
        return X_resampled, y_resampled
    else:
        # 극소량: 노이즈 추가 방식
        return noise_augmentation(X, y_binary)

def sliding_window_augmentation(iba_daily, window_size=5, stride=1):
    """
    시간 윈도우 슬라이딩으로 학습 샘플 증가

    일별 데이터 413건 → 윈도우 크기 5, 스트라이드 1 → ~409 윈도우
    각 윈도우: 5일간의 패턴 벡터 (flatten 또는 통계 요약)
    """
    windows = []
    for i in range(0, len(iba_daily) - window_size + 1, stride):
        window = iba_daily.iloc[i:i+window_size]
        # 윈도우 내 통계 요약
        summary = {
            f'{col}_win_mean': window[col].mean(),
            f'{col}_win_std': window[col].std(),
            f'{col}_win_trend': np.polyfit(range(window_size), window[col].values, 1)[0],
        }
        # 윈도우 마지막 날의 불량 라벨
        summary['defect_label'] = window['has_defect'].iloc[-1]
        windows.append(summary)

    return pd.DataFrame(windows)
```

---

## 5. 대안적 분석 전략 (Section C: Alternative Strategies)

### C1. 불량 전조 구간 분석

| 항목 | 내용 |
|------|------|
| **대응 한계** | L1, L5 |
| **핵심 아이디어** | 고불량일 D-1~D-3 IBA 패턴 vs 정상일 비교 |

**기존 기반**: `data_preparation.py:193-241` — 이미 D-1~D-14 시차 변수(`_lag{N}`, `_ma{N}`, `_delta{N}`) 생성 중.

**추가 분석 방향**:

```python
def precursor_analysis(tag_defect_matrix, lead_days=[1, 2, 3]):
    """
    고불량일 전조 패턴 분석

    방법:
    1. 고불량일(상위 20%) 식별
    2. 고불량일 D-1, D-2, D-3의 IBA 통계와 전체 평균 비교
    3. 유의미한 차이가 있는 태그 식별
    """
    high_defect_threshold = tag_defect_matrix['total_defect_rate'].quantile(0.80)
    high_defect_days = tag_defect_matrix[
        tag_defect_matrix['total_defect_rate'] >= high_defect_threshold
    ].index

    results = {}
    for lead in lead_days:
        # 고불량일 D-{lead}의 태그 값
        precursor_indices = [i - lead for i in high_defect_days if i - lead >= 0]
        precursor_data = tag_defect_matrix.iloc[precursor_indices]

        # 정상일의 태그 값
        normal_data = tag_defect_matrix[
            tag_defect_matrix['total_defect_rate'] < high_defect_threshold
        ]

        # 태그별 t-test
        for col in feature_cols:
            t_stat, p_val = stats.ttest_ind(
                precursor_data[col].dropna(),
                normal_data[col].dropna(),
                equal_var=False,  # Welch's t-test
            )
            if p_val < 0.05:
                results.setdefault(f'D-{lead}', []).append({
                    'tag': col, 't_stat': t_stat, 'p_value': p_val
                })

    return results
```

---

### C2. 파생 특성 엔지니어링

| 항목 | 내용 |
|------|------|
| **대응 한계** | L5(소량 → 변수 다양화로 보완) |
| **핵심 아이디어** | 일별 IBA 통계에서 고차 파생 변수 생성 후 차원축소 |

**파생 변수 종류**:

```python
def create_derived_features(iba_daily):
    """
    413일 × N개 태그 → 413일 × 수백개 파생변수 → PCA 축소
    """
    df = iba_daily.copy()

    for tag in base_tags:
        avg_col = f'{tag}_avg'
        std_col = f'{tag}_std'
        min_col = f'{tag}_min'
        max_col = f'{tag}_max'

        # 1. Range (max - min)
        df[f'{tag}_range'] = df[max_col] - df[min_col]

        # 2. Coefficient of Variation (CV = std/avg)
        df[f'{tag}_cv'] = df[std_col] / df[avg_col].replace(0, np.nan)

        # 3. 이동평균 (3일, 7일)
        df[f'{tag}_ma3'] = df[avg_col].rolling(3, min_periods=1).mean()
        df[f'{tag}_ma7'] = df[avg_col].rolling(7, min_periods=1).mean()

        # 4. 변화율 (전일 대비)
        df[f'{tag}_pct_change'] = df[avg_col].pct_change()

        # 5. 가속도 (변화율의 변화율)
        df[f'{tag}_accel'] = df[f'{tag}_pct_change'].diff()

        # 6. 왜도 (skewness proxy: (mean - median) / std)
        # 일별 집계에서 median 미보유 → (avg - (min+max)/2) / std로 근사
        df[f'{tag}_skew_proxy'] = (
            df[avg_col] - (df[min_col] + df[max_col]) / 2
        ) / df[std_col].replace(0, np.nan)

    # PCA 차원축소
    from sklearn.decomposition import PCA
    feature_cols = [c for c in df.columns if c != 'date' and not c.startswith('defect')]
    X = df[feature_cols].fillna(0)

    pca = PCA(n_components=0.95)  # 95% 분산 유지
    X_pca = pca.fit_transform(X)

    return X_pca, pca
```

---

### C3. 변점 탐지 기반 접근

| 항목 | 내용 |
|------|------|
| **대응 한계** | L1(시간 해상도 — 변점은 일별보다 정밀) |
| **핵심 아이디어** | CUSUM/EWMA 변점 발생 빈도 ↔ 불량률 상관 |

**기존 보유 자산**: `analysis_output/steel_grade_iqr_analysis_v2/cusum_ewma/` — CUSUM/EWMA 분석 결과 이미 존재.

**구현 방향**:

```python
def changepoint_defect_correlation(cusum_results, defect_daily):
    """
    기존 CUSUM/EWMA 변점 결과에서 일별 변점 카운트를 생성하고
    불량률과의 상관관계 분석

    가설: 변점 빈발일 = 공정 불안정 = 불량 발생 가능성 ↑
    """
    # 1. CUSUM/EWMA 변점을 일별로 집계
    changepoint_daily = cusum_results.groupby(
        cusum_results['timestamp'].dt.date
    ).agg({
        'cusum_signal': 'sum',        # 일별 CUSUM 신호 횟수
        'ewma_signal': 'sum',         # 일별 EWMA 신호 횟수
        'cusum_value': ['mean', 'max'],  # 일별 CUSUM 값 통계
    })

    # 2. 불량률과 합치기
    merged = changepoint_daily.merge(defect_daily, left_index=True, right_on='date')

    # 3. 상관 분석
    correlations = {
        'cusum_count_vs_defect': stats.spearmanr(
            merged['cusum_signal_sum'], merged['total_defect_rate']
        ),
        'ewma_count_vs_defect': stats.spearmanr(
            merged['ewma_signal_sum'], merged['total_defect_rate']
        ),
    }

    return correlations
```

---

### C4. 불량일 vs 정상일 프로파일 비교

| 항목 | 내용 |
|------|------|
| **대응 한계** | L5(소량 — 비모수 검정 적합), L7(불균형) |
| **핵심 아이디어** | 고불량일(상위 10-20%) IBA 프로파일 vs 정상일 통계 검정 |

**구현 방향**:

```python
from scipy.stats import mannwhitneyu, ks_2samp

def profile_comparison(tag_defect_matrix, threshold_pct=0.80):
    """
    고불량일 vs 정상일의 태그별 통계 검정

    검정 방법:
    - Welch's t-test: 평균 차이
    - Mann-Whitney U: 분포 중앙값 차이 (비모수)
    - KS test: 전체 분포 차이

    결과: 어떤 태그가 불량일에 유의미하게 다른 패턴을 보이는가?
    """
    threshold = tag_defect_matrix['total_defect_rate'].quantile(threshold_pct)

    high_defect = tag_defect_matrix[tag_defect_matrix['total_defect_rate'] >= threshold]
    normal = tag_defect_matrix[tag_defect_matrix['total_defect_rate'] < threshold]

    results = []
    for col in feature_cols:
        h_vals = high_defect[col].dropna()
        n_vals = normal[col].dropna()

        if len(h_vals) < 3 or len(n_vals) < 3:
            continue

        # Welch's t-test
        t_stat, t_pval = stats.ttest_ind(h_vals, n_vals, equal_var=False)

        # Mann-Whitney U
        u_stat, u_pval = mannwhitneyu(h_vals, n_vals, alternative='two-sided')

        # Kolmogorov-Smirnov
        ks_stat, ks_pval = ks_2samp(h_vals, n_vals)

        # 효과 크기 (Cohen's d)
        pooled_std = np.sqrt((h_vals.std()**2 + n_vals.std()**2) / 2)
        cohens_d = (h_vals.mean() - n_vals.mean()) / pooled_std if pooled_std > 0 else 0

        results.append({
            'tag': col,
            'high_defect_mean': h_vals.mean(),
            'normal_mean': n_vals.mean(),
            'mean_diff_pct': (h_vals.mean() - n_vals.mean()) / n_vals.mean() * 100 if n_vals.mean() != 0 else np.nan,
            't_pval': t_pval,
            'u_pval': u_pval,
            'ks_pval': ks_pval,
            'cohens_d': cohens_d,
            'significant': min(t_pval, u_pval, ks_pval) < 0.05 / len(feature_cols),  # Bonferroni
        })

    return pd.DataFrame(results).sort_values('cohens_d', key=abs, ascending=False)
```

**Bonferroni 보정**: 다중 검정(85개 태그 × 4개 통계) 시 유의수준 조정. 이미 `config.py:187`에 `BONFERRONI_CORRECTION = True` 설정됨.

---

### C5. 앙상블 설비 건강 지수

| 항목 | 내용 |
|------|------|
| **대응 한계** | L1, L5, L7 전체 대응 |
| **핵심 아이디어** | 다수 기법의 이상치 점수를 통합한 단일 설비 건강 지수 구축 |

**구현 방향**:

```python
def ensemble_health_index(outlier_results_dict):
    """
    6가지 이상치 탐지 기법의 결과를 통합하여
    일별 설비 건강 지수(Equipment Health Index) 산출

    outlier_results_dict = {
        'iqr': daily_outlier_scores,      # 이상치 수/비율
        'adj_iqr': daily_outlier_scores,
        'cusum': daily_signal_counts,
        'ewma': daily_signal_counts,
        'rolling_z': daily_outlier_scores,
        'mahalanobis': daily_distances,
    }
    """
    # 1. 각 기법별 일별 점수를 [0, 1]로 정규화
    from sklearn.preprocessing import MinMaxScaler
    scaler = MinMaxScaler()

    normalized_scores = {}
    for method, scores in outlier_results_dict.items():
        normalized_scores[method] = scaler.fit_transform(
            scores.values.reshape(-1, 1)
        ).flatten()

    # 2. 가중 평균 (기법별 가중치 — 전문가 조정 가능)
    weights = {
        'iqr': 0.15, 'adj_iqr': 0.15, 'cusum': 0.20,
        'ewma': 0.20, 'rolling_z': 0.15, 'mahalanobis': 0.15,
    }

    health_index = sum(
        weights[method] * normalized_scores[method]
        for method in weights
    )

    # 3. 건강 지수 = 1 - 이상 점수 (높을수록 건강)
    health_index = 1.0 - health_index

    # 4. 불량률과의 상관 검증
    correlation, p_value = stats.spearmanr(health_index, daily_defect_rate)

    return health_index, correlation, p_value
```

**기대 효과**: 개별 기법의 false positive를 앙상블로 억제하면서, 불량과의 상관을 극대화한 단일 지표 제공.

---

## 6. 데이터 보강 요청 사항 (Section D: Customer Data Enrichment)

현재 데이터의 근본적 한계를 해소하기 위해 고객사에 추가 요청할 수 있는 항목:

| ID | 요청 항목 | 대응 한계 | 우선순위 | 구현 난이도 |
|----|----------|-----------|---------|------------|
| D1 | **코일 단위 추적 시스템** | L1, L3 | ★★★★★ | 높음 (MES 연동 필요) |
| | 코일ID ↔ IBA 시간 구간(시작/종료) 매핑 테이블 제공 | | | |
| | 최소: 코일 번호 + 압연 시작 시각 + 종료 시각 | | | |
| D2 | **불량 상세 분류 코드화** | L4 | ★★★★ | 낮음 (운영 변경) |
| | 자유 텍스트(remarks) → 표준 코드 체계 전환 | | | |
| | 예: W01=권취불량, W02=중량과다, W03=중량미달, T01=토션, S01=딱지 등 | | | |
| D3 | **실시간 불량 판정 시점 기록** | L1 | ★★★★★ | 중 (시스템 개선) |
| | 불량 발생 시점(초 단위)을 IBA 타임스탬프와 동기화 | | | |
| D4 | **롤 교환 이력** | 보조 | ★★★ | 낮음 (이력 제공) |
| | 롤 교환 시각, 롤 사용량(톤), 롤 마모도 → 롤 상태와 불량 상관 분석 | | | |
| D5 | **설비 정비 이력** | 보조 | ★★★ | 낮음 (이력 제공) |
| | 정기/비정기 정비 일시, 정비 내용 → 정비 전후 불량 패턴 비교 | | | |
| D6 | **빌렛/원자재 성분 데이터** | 보조 | ★★ | 중 (데이터 연동) |
| | heat_no별 화학 성분(C, Si, Mn, P, S 등) → 원자재 기인 불량 식별 | | | |

---

## 7. 확장 탐색 기법 (Section E: Extended Techniques)

> **추가 조사일**: 2026-03-15
> **목적**: 기존 17가지 방안(A1~A5, B1~B7, C1~C5)에서 다루지 않은 공백 영역 보완
> **공백 식별**: 불확실성 정량화 / 함수형 시계열 / 구조적 인과 / 극단값 모델링 / 도메인 규칙 결합

---

### E1. Conformal Prediction (교정 예측 — 통계적 커버리지 보장)

| 항목 | 내용 |
|------|------|
| **대응 한계** | L5(소량 데이터), L7(클래스 불균형) |
| **난이도** | ★★ (낮음) |
| **기대효과** | ★★★★ (높음) |
| **핵심 아이디어** | 기존 회귀·분류 모델에 **통계적 커버리지 보장**을 추가 — "예측값이 아닌 예측 집합"으로 소량 데이터의 불확실성을 정직하게 표현 |

**개요**: B2(불량률 회귀)나 B6(베이지안) 모델은 점 예측(point estimate)을 제공하지만, 소량 데이터(413건)에서는 예측 구간의 신뢰성이 의심스럽다. **Conformal Prediction(CP)**은 분포 가정 없이 임의의 모델에 적용 가능한 커버리지 보장 기법으로, "실제 값이 예측 구간 안에 있을 확률 ≥ 1-α"를 수학적으로 보장한다.

**B2(불량률 회귀)와의 결합**:

```python
from mapie.regression import MapieRegressor
from sklearn.ensemble import GradientBoostingRegressor

def conformal_defect_regression(X_train, y_train, X_test, alpha=0.10):
    """
    Conformal Prediction으로 불량률 예측 구간 생성
    alpha=0.10 → 90% coverage 보장 (소량 데이터 대응)

    MAPIE(Model Agnostic Prediction Interval Estimator) 활용:
    - Split Conformal: calibration set으로 잔차 분포 추정
    - Jackknife+: LOO 잔차로 더 작은 구간 (소량 데이터 우선)
    """
    base_model = GradientBoostingRegressor(n_estimators=100, max_depth=3)

    mapie = MapieRegressor(
        estimator=base_model,
        method="plus",      # Jackknife+: 소량 데이터에 유리
        cv=-1,              # LOO cross-val (=LeaveOneOut)
        random_state=42,
    )
    mapie.fit(X_train, y_train)

    y_pred, y_pis = mapie.predict(X_test, alpha=alpha)
    # y_pis[:, 0, 0] = 하한, y_pis[:, 0, 1] = 상한

    # 커버리지 검증 (empirical coverage ≈ 1 - alpha 검증)
    coverage = np.mean(
        (y_test >= y_pis[:, 0, 0]) & (y_test <= y_pis[:, 0, 1])
    )

    return y_pred, y_pis, coverage
```

**이진 분류(불량 유/무)에 CP 적용**:

```python
from mapie.classification import MapieClassifier
from sklearn.ensemble import RandomForestClassifier

def conformal_defect_classification(X_cal, y_cal, X_test, alpha=0.05):
    """
    Adaptive Prediction Set (APS) — 불균형 클래스에서 더 정확한 coverage
    결과: 각 샘플에 대해 {정상}, {불량}, {정상, 불량} 중 하나의 예측 집합 반환
    → "모른다"를 명시적으로 표현
    """
    base = RandomForestClassifier(n_estimators=200, class_weight='balanced')
    mapie_clf = MapieClassifier(
        estimator=base,
        method="aps",    # Adaptive Prediction Set (불균형 대응)
        cv="prefit",
        random_state=42,
    )
    base.fit(X_cal, y_cal)
    mapie_clf.fit(X_cal, y_cal)

    _, sets = mapie_clf.predict(X_test, alpha=alpha, include_last_label="randomized")
    # sets: shape (n_test, n_classes) — True면 해당 클래스가 예측 집합에 포함

    return sets
```

**실용적 의의**:
- 기존 B2/B6 결과를 "90% 신뢰 구간 [하한, 상한]"으로 변환 → 현장 담당자에게 신뢰성 있는 정보 제공
- 구간이 넓은 날 = 모델 불확실성 높음 → 집중 모니터링 대상
- **설치**: `pip install mapie` (scikit-learn 호환, 의존성 최소)

**기존 방안과의 차별점**:
| 방안 | 불확실성 표현 | 커버리지 보장 | 소량 데이터 적합 |
|------|------------|------------|----------------|
| B2 불량률 회귀 | 없음 (점 예측) | 없음 | 보통 |
| B6 베이지안 | 사후분포 (분포 가정 필요) | 근사적 | 우수 |
| **E1 Conformal** | **예측 구간** | **수학적 보장** | **최우수** |

---

### E2. Bayesian Online Change Point Detection (BOCPD — 온라인 베이지안 변점 탐지)

| 항목 | 내용 |
|------|------|
| **대응 한계** | L1(시간 해상도 — 초 단위 변점 정밀 탐지), L3(번들-코일 연결) |
| **난이도** | ★★ (낮음~중) |
| **기대효과** | ★★★★ (높음) |
| **핵심 아이디어** | 기존 C3(CUSUM/EWMA 변점) 대비: **베이지안 확률**로 변점 존재 여부와 위치를 동시에 추정 — "언제부터 공정이 바뀌었는가?"를 확률 분포로 표현 |

**기존 C3 한계 vs E2 개선**:
- C3: CUSUM 신호가 0/1로만 표현 → 경계 판단의 임계값 민감
- E2: 변점 확률 P(change at t) → 연속 점수로 불량 상관 분석 가능

```python
# 구현 옵션 1: ruptures 라이브러리 (오프라인, 고속)
import ruptures as rpt

def detect_changepoints_ruptures(signal, penalty=10):
    """
    PELT (Pruned Exact Linear Time) 변점 탐지
    penalty: 변점 수 조절 (작을수록 많은 변점)

    신호: 단일 태그의 일별 평균값 시계열
    반환: 변점 위치 리스트 (인덱스)
    """
    model = rpt.Pelt(model="rbf", min_size=3, jump=1)
    result = model.fit_predict(signal.values.reshape(-1, 1), pen=penalty)
    # pen=np.log(len(signal)) * signal.std()**2  # BIC 기반 자동 설정
    return result[:-1]  # 마지막 요소는 시계열 끝 → 제외

def changepoint_defect_regression(daily_stats, defect_daily, tag_cols):
    """
    각 태그별 변점 특성 → 불량률 회귀 특성으로 변환

    파생 변수:
    - n_changepoints_7d: 최근 7일 내 변점 수
    - days_since_last_cp: 마지막 변점으로부터 경과일
    - mean_before_cp, mean_after_cp: 변점 전후 평균 차이
    """
    features = []
    for tag in tag_cols:
        cps = detect_changepoints_ruptures(daily_stats[tag])
        features.append({
            'tag': tag,
            'n_changepoints': len(cps),
            'cp_positions': cps,
        })
    return features
```

```python
# 구현 옵션 2: BOCPD (Adams & MacKay 2007) — 온라인 추론
# 의존: bayeschangept 또는 직접 구현

def bocpd_run_length(data, hazard_rate=1/100, obs_likelihood='gaussian'):
    """
    Run Length Distribution: 각 시점에서 "마지막 변점 이후 경과 시간"의 분포
    높은 확률 질량이 짧은 run length → 최근 변점 발생
    """
    T = len(data)
    R = np.zeros((T + 1, T + 1))  # run-length distribution
    R[0, 0] = 1

    # Gaussian 관측 모델
    from scipy.stats import norm
    mu_0, kappa_0, alpha_0, beta_0 = 0, 1, 1, 1  # NIW prior

    for t in range(1, T + 1):
        # 성장 확률 (변점 없음)
        # ... (Adams & MacKay 2007 알고리즘)
        pass

    # 변점 확률 = R[:, 0] (run length가 0으로 리셋되는 확률)
    changepoint_probs = R[:, 0]
    return changepoint_probs
```

**실용적 활용**:
```python
# 태그별 일별 변점 확률 → 불량률 회귀 특성
def create_changepoint_features(daily_stats, tag_cols, window=7):
    features = {}
    for tag in tag_cols:
        cps = detect_changepoints_ruptures(daily_stats[tag])
        cp_binary = np.zeros(len(daily_stats))
        for cp in cps:
            cp_binary[cp] = 1

        features[f'{tag}_cp_count_7d'] = pd.Series(cp_binary).rolling(window).sum()
        features[f'{tag}_days_since_cp'] = pd.Series(cp_binary).apply(
            lambda x: 0 if x else np.nan
        ).ffill().cumsum()

    return pd.DataFrame(features)
```

**기존 C3과의 시너지**: BOCPD/PELT 결과 → C3의 Spearman 상관 분석에 투입 가능.

---

### E3. Extreme Value Theory + Quantile Regression (극단값 이론 + 분위 회귀)

| 항목 | 내용 |
|------|------|
| **대응 한계** | L5(소량 데이터), L7(클래스 불균형 — 극단 불량에 집중) |
| **난이도** | ★★ (낮음~중) |
| **기대효과** | ★★★★ (높음) |
| **핵심 아이디어** | 불량률의 **극단값(상위 10~20%)** 모델링에 특화 — 일반 회귀는 평균에 집중하지만, 고불량 이벤트는 꼬리 분포에서 발생 |

**EVT (Generalized Pareto Distribution) 기반 극단 불량 모델링**:

```python
from scipy.stats import genpareto

def fit_defect_extremes(defect_rates, threshold_quantile=0.80):
    """
    Peaks-Over-Threshold (POT) 방법:
    threshold 초과 불량률을 GPD로 피팅 → 극단 사건 확률 추정

    이점: 소량 극단값(~80건)도 GPD로 안정적 추정 가능
    """
    threshold = np.quantile(defect_rates, threshold_quantile)
    exceedances = defect_rates[defect_rates > threshold] - threshold

    # GPD 피팅
    c, loc, scale = genpareto.fit(exceedances, floc=0)

    # 반환 수준 (Return Level): 특정 기간 동안 초과할 확률
    # T일에 1번 발생하는 불량률 수준
    T_days = [30, 90, 180]
    return_levels = {}
    for T in T_days:
        p = 1 / (T * (1 - threshold_quantile))
        rl = threshold + scale / c * ((1 / p) ** c - 1) if c != 0 else threshold - scale * np.log(p)
        return_levels[f'RL_{T}d'] = rl

    return {'c': c, 'scale': scale, 'threshold': threshold, 'return_levels': return_levels}
```

**Quantile Regression (분위 회귀) — 고불량 구간 예측**:

```python
from sklearn.linear_model import QuantileRegressor

def quantile_defect_model(X, y, quantiles=[0.50, 0.75, 0.90, 0.95]):
    """
    B2(불량률 회귀)는 평균 예측
    E3(분위 회귀)는 상위 분위 예측 → 고불량 이벤트에 더 민감

    quantile=0.90: "90%의 날은 이 예측값 이하의 불량률"
    → 고불량 예측 경보에 직접 활용
    """
    models = {}
    for q in quantiles:
        qr = QuantileRegressor(quantile=q, alpha=0.01, solver='highs')
        qr.fit(X, y)
        models[f'q{int(q*100)}'] = qr

    # 예측: 상위 10% 초과 확률 제공
    predictions = {q_name: m.predict(X) for q_name, m in models.items()}

    # 특성 중요도 (절대 회귀 계수)
    coef_df = pd.DataFrame(
        {q: m.coef_ for q, m in models.items()},
        index=X.columns if hasattr(X, 'columns') else range(X.shape[1])
    )

    return predictions, coef_df
```

**LightGBM 분위 회귀 (비선형 버전)**:

```python
import lightgbm as lgb

def lgbm_quantile_defect(X_train, y_train, X_test, alpha=0.90):
    """
    비선형 분위 회귀: 태그 간 상호작용 포착
    소량 데이터(413건)에서 early stopping으로 과적합 방지
    """
    params = {
        'objective': 'quantile',
        'alpha': alpha,
        'n_estimators': 300,
        'learning_rate': 0.05,
        'num_leaves': 8,        # 소량 데이터: 단순 트리
        'min_child_samples': 10,
        'reg_alpha': 0.1,
        'reg_lambda': 0.1,
        'verbose': -1,
    }
    model = lgb.LGBMRegressor(**params)
    model.fit(
        X_train, y_train,
        eval_set=[(X_test, y_test)],
        callbacks=[lgb.early_stopping(30), lgb.log_evaluation(0)],
    )

    y_q = model.predict(X_test)
    importance = pd.Series(model.feature_importances_, index=X_train.columns)
    return y_q, importance.nlargest(20)
```

**기존 B2와의 차이**: B2는 E[y|X] 예측 → 평균적 불량일 탐지 강점. E3는 Q90[y|X] 예측 → **고불량 이벤트 사전 경보** 강점.

---

### E4. 도메인 규칙 앙상블 (Rule Mining + ML Hybrid)

| 항목 | 내용 |
|------|------|
| **대응 한계** | L4(remarks 비정규화), L5(소량), L7(불균형) |
| **난이도** | ★★ (낮음~중) |
| **기대효과** | ★★★★ (높음) |
| **핵심 아이디어** | ML 이상치 탐지 결과에 **도메인 규칙**을 추가 레이어로 결합 → 모델 해석성 + 탐지율 동시 개선 |

**접근법 1: 연관규칙 마이닝 (Apriori/FP-Growth)**

```python
from mlxtend.frequent_patterns import fpgrowth, association_rules
from mlxtend.preprocessing import TransactionEncoder

def defect_association_rules(tag_defect_matrix, feature_cols, min_support=0.05):
    """
    "특정 태그 이상 AND 고불량일" 규칙 마이닝

    예시 출력:
    {PR6_SPEED_high, HEATING_TEMP_low} → {winding_defect} (confidence=0.82, lift=3.1)
    → "PR6 속도 과대 AND 가열 온도 저하 시 권취불량 발생 확률 82%"

    소량 데이터 대응: min_support를 낮게 설정 (0.05 = 5% = ~20일)
    """
    # 이진화: 각 태그의 일별 값이 IQR 이상치 범위 초과 여부
    binary_df = pd.DataFrame()
    for col in feature_cols:
        q1, q3 = tag_defect_matrix[col].quantile([0.25, 0.75])
        iqr = q3 - q1
        binary_df[f'{col}_high'] = tag_defect_matrix[col] > q3 + 1.5 * iqr
        binary_df[f'{col}_low'] = tag_defect_matrix[col] < q1 - 1.5 * iqr

    # 불량 이진 변수 추가
    binary_df['winding_defect'] = tag_defect_matrix['winding_defect_rate'] > \
        tag_defect_matrix['winding_defect_rate'].quantile(0.80)
    binary_df['weight_defect'] = tag_defect_matrix['weight_defect_rate'] > \
        tag_defect_matrix['weight_defect_rate'].quantile(0.80)

    # FP-Growth (Apriori보다 빠름)
    frequent_itemsets = fpgrowth(binary_df.astype(int), min_support=min_support, use_colnames=True)
    rules = association_rules(frequent_itemsets, metric="confidence", min_threshold=0.60)

    # 불량이 결과절(consequent)인 규칙만 필터
    defect_rules = rules[rules['consequents'].apply(
        lambda x: any('defect' in item for item in x)
    )].sort_values('lift', ascending=False)

    return defect_rules
```

**접근법 2: RIPPER/CN2 규칙 학습**

```python
# 의존: wittgenstein 라이브러리 (pip install wittgenstein)
import wittgenstein as lw

def learn_defect_rules(X_binary, y_binary):
    """
    RIPPER 알고리즘: 불량 예측 IF-THEN 규칙 자동 학습
    소량 데이터에서 단순 규칙 생성 → 해석 용이

    출력 예시:
    IF PR6_SPEED_avg > 12.5 AND HEATING_TEMP_avg < 1050 THEN 권취불량=True
    """
    ripper = lw.RIPPER(k=2, prune_size=0.33, max_rules=15)
    ripper.fit(X_binary, y_binary, pos_class=1)

    print(ripper.ruleset_)  # 학습된 규칙 출력
    return ripper
```

**접근법 3: 도메인 지식 규칙 → 점수 가산**

```python
def domain_rule_scoring(daily_stats):
    """
    철강 압연 도메인 지식 기반 규칙:
    (고객사 담당자/공정 전문가 인터뷰 기반 — 추후 파라미터 조정 필요)

    각 규칙 위반 시 이상 점수 가산 → 앙상블 건강 지수(C5)에 결합
    """
    score = pd.Series(0.0, index=daily_stats.index)

    # 규칙 R1: 가열로 온도 급변 (일 내 표준편차 > X)
    if 'HEATING_TEMPERATURE_01_std' in daily_stats.columns:
        threshold_r1 = daily_stats['HEATING_TEMPERATURE_01_std'].quantile(0.85)
        score += (daily_stats['HEATING_TEMPERATURE_01_std'] > threshold_r1).astype(float) * 0.25

    # 규칙 R2: PR6 속도 이상 (평균 ± 2σ 이탈)
    if 'PR6_SPEED_avg' in daily_stats.columns:
        mu = daily_stats['PR6_SPEED_avg'].mean()
        sigma = daily_stats['PR6_SPEED_avg'].std()
        score += (np.abs(daily_stats['PR6_SPEED_avg'] - mu) > 2 * sigma).astype(float) * 0.20

    # 규칙 R3: 핀치롤 전류 이상
    # ... 공정 담당자와 협의하여 추가

    return score  # C5 건강 지수에 가산하거나 별도 경보로 활용
```

**기존 방안과의 통합**: E4 규칙 점수 → C5(앙상블 건강 지수)의 추가 입력 → 도메인 설명력 향상.

---

### E5. Functional Data Analysis (FDA — 함수적 데이터 분석)

| 항목 | 내용 |
|------|------|
| **대응 한계** | L1(시간 해상도 — 초 단위 시계열 직접 활용), L3(번들-코일 연결) |
| **난이도** | ★★★ (중) |
| **기대효과** | ★★★★ (높음) |
| **핵심 아이디어** | 일별 avg/std 집계 대신 **압연 구간의 시계열 곡선 자체**를 분석 단위로 사용 — 형태(Shape) 정보 보존 |

**기존 접근의 한계**: 일별 통계(avg, std, min, max)는 **시계열의 형태 정보**를 소실. FDA는 각 압연 구간을 하나의 "함수"로 모델링하여 형태 패턴을 직접 비교.

```python
# 의존: scikit-fda (pip install scikit-fda)
import skfda
from skfda import FDataGrid
from skfda.preprocessing.dim_reduction import FPCA

def functional_coil_analysis(coil_segments, tag_name, n_basis=10):
    """
    각 코일 압연 구간(A1/A5로 식별)을 FDataGrid로 변환 후
    Functional PCA로 주요 변동 패턴 추출

    coil_segments: list of (time_points, tag_values) for each coil
    tag_name: 분석 태그 (예: 'PR6_SPEED')
    n_basis: B-spline 기저 함수 수
    """
    # 불규칙 시계열 → 공통 격자로 보간
    # (압연 구간 길이가 코일마다 다를 수 있음)
    max_len = max(len(seg[0]) for seg in coil_segments)
    common_grid = np.linspace(0, 1, max_len)

    fd_data = []
    for time_points, values in coil_segments:
        # 정규화된 시간 격자로 보간
        normalized_time = (time_points - time_points[0]) / (time_points[-1] - time_points[0])
        interp_values = np.interp(common_grid, normalized_time, values)
        fd_data.append(interp_values)

    fd = FDataGrid(
        data_matrix=np.array(fd_data),
        sample_points=common_grid,
    )

    # B-spline 평활화
    smoother = skfda.preprocessing.smoothing.BasisSmoother(
        skfda.representation.basis.BSpline(n_basis=n_basis)
    )
    fd_smooth = smoother.fit_transform(fd)

    # FPCA (Functional PCA)
    fpca = FPCA(n_components=5)
    fd_scores = fpca.fit_transform(fd_smooth)

    # FPCA 점수 → 불량 분류기 입력
    return fd_scores, fpca
```

**불량 구분에 활용**:

```python
def functional_defect_separation(fd_scores, defect_labels):
    """
    FPCA 점수 공간에서 불량/정상 코일 분리 시각화 + 분류

    기대 효과:
    - PC1: 온도/속도 전반적 수준 (Level component)
    - PC2: 압연 시작-종료 패턴 (Shape component)
    - PC3: 이상 급변 패턴 (Spike component)
    → 불량과 특정 PC가 상관 → 공정 이해 심화
    """
    from sklearn.discriminant_analysis import LinearDiscriminantAnalysis

    lda = LinearDiscriminantAnalysis()
    lda.fit(fd_scores, defect_labels)

    # 불량 구분 능력 검증
    from sklearn.model_selection import StratifiedKFold, cross_val_score
    skf = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)
    accuracy = cross_val_score(lda, fd_scores, defect_labels, cv=skf, scoring='f1')

    return lda, accuracy.mean()
```

**전제 조건**: A1(번들 시간 윈도우) 또는 A5(공정 단계 정렬) 완료 → 코일 단위 IBA 구간 추출 필요.

**기존 C2(파생 특성)와의 차이**: C2는 통계 기반 → 형태 손실. FDA는 함수 자체를 분석 단위로 → 형태 정보 완전 보존.

---

### E6. Causal Discovery / DAG 학습 (구조적 인과 탐색)

| 항목 | 내용 |
|------|------|
| **대응 한계** | L1(시간 해상도 — 시차 인과 탐색), L5(소량 — 단순 그래프 학습) |
| **난이도** | ★★★ (중) |
| **기대효과** | ★★★★ (높음) |
| **핵심 아이디어** | 기존 C3(Granger 인과)·`03_causality_analysis.py`(PCMCI/Transfer Entropy)는 **쌍방향 인과**. E6은 **시스템 전체의 인과 구조(DAG)**를 학습 → "어떤 태그가 불량의 직접 원인인가?" 식별 |

**기존 코드와의 차이**:
- `03_causality_analysis.py`: Granger(선형 시차 인과), PCMCI(다변량 시차 인과) → 쌍별 관계
- E6: NOTEARS/PC Algorithm → **방향성 비순환 그래프(DAG)** 학습 → 공정 인과 구조 시각화

```python
# 옵션 1: NOTEARS (Gradient-based DAG learning) — pip install notears
# 옵션 2: causal-learn 라이브러리 — pip install causal-learn

from causallearn.search.ConstraintBased.PC import pc
from causallearn.utils.cit import fisherz

def discover_process_dag(daily_stats, tag_subset, alpha=0.05):
    """
    PC Algorithm으로 IBA 태그 간 인과 DAG 학습

    입력: 일별 태그 통계 (n_days × n_tags)
    출력: 인과 그래프 (방향성 있는 엣지)

    선택 전략: 소량 데이터(413건) → 태그 수 제한 (20개 이하 권장)
    우선 태그: TAG_CATEGORIES의 핵심 태그 (예: 가열로 온도, PR 속도, 핀치롤 전류)
    """
    X = daily_stats[tag_subset].dropna().values

    cg = pc(
        data=X,
        alpha=alpha,         # 유의수준 (소량 데이터: 0.05~0.10 권장)
        indep_test=fisherz,  # Fisher-z (정규성 가정)
        stable=True,
        uc_rule=0,
    )

    return cg
```

```python
# 옵션 2: LiNGAM (비가우시안 → 방향 결정 가능)
# pip install lingam
import lingam

def lingam_dag(daily_stats, tag_subset):
    """
    LiNGAM: 비정규 분포를 활용해 인과 방향 결정
    철강 공정 데이터는 종종 비정규 → LiNGAM 적합

    장점: 비가우시안 분포 → PC Algorithm보다 더 정확한 방향 결정
    단점: 선형성 가정
    """
    X = daily_stats[tag_subset].dropna().values

    model = lingam.DirectLiNGAM()
    model.fit(X)

    # 인과 순서 (위상 정렬)
    causal_order = model.causal_order_

    # 인과 효과 매트릭스 (B[i,j]: j가 i에 미치는 직접 효과)
    B = model.adjacency_matrix_

    # 불량 관련 직접 원인 태그 식별
    defect_idx = list(tag_subset).index('winding_defect_rate')
    direct_causes = [(tag_subset[i], abs(B[defect_idx, i]))
                     for i in range(len(tag_subset))
                     if abs(B[defect_idx, i]) > 0.1]

    return model, causal_order, sorted(direct_causes, key=lambda x: -x[1])
```

**시각화**:

```python
import networkx as nx
import matplotlib.pyplot as plt

def plot_causal_dag(adjacency_matrix, tag_names, defect_tags):
    """
    인과 DAG를 NetworkX 그래프로 시각화
    불량 관련 태그를 빨간색으로 강조
    """
    G = nx.DiGraph()
    G.add_nodes_from(tag_names)

    n = len(tag_names)
    for i in range(n):
        for j in range(n):
            if abs(adjacency_matrix[i, j]) > 0.1:
                G.add_edge(tag_names[j], tag_names[i],
                           weight=abs(adjacency_matrix[i, j]))

    node_colors = ['red' if t in defect_tags else 'lightblue' for t in G.nodes()]
    pos = nx.kamada_kawai_layout(G)

    nx.draw(G, pos, with_labels=True, node_color=node_colors,
            arrows=True, edge_color='gray', node_size=1000)
    plt.title("공정 인과 DAG (빨간색=불량 연관 태그)")
    plt.tight_layout()
    plt.savefig('analysis_output/causal_dag.png', dpi=150)
```

**기존 분석과의 통합**: PCMCI 결과(03_causality_analysis.py)와 E6 DAG 결과를 비교 → 일관된 인과 관계를 "확정 인과"로 분류.

---

### E7. Contrastive / Self-Supervised Representation Learning (대조·자기지도 표현 학습)

| 항목 | 내용 |
|------|------|
| **대응 한계** | L5(소량 라벨), L7(클래스 불균형) |
| **난이도** | ★★★ (중) |
| **기대효과** | ★★★ (중~높음) |
| **핵심 아이디어** | 939K건의 **라벨 없는 IBA 데이터**로 먼저 표현을 학습한 뒤, 소량 불량 라벨로 미세 조정 — B4(준지도)의 딥러닝 버전 |

**SimCLR 기반 시계열 대조 학습**:

```python
import torch
import torch.nn as nn

class TimeSeriesEncoder(nn.Module):
    """
    1D-CNN 기반 시계열 인코더
    입력: (batch, n_tags, seq_len) — 압연 구간 다변량 시계열
    출력: (batch, hidden_dim) — 표현 벡터
    """
    def __init__(self, n_tags=85, hidden_dim=64):
        super().__init__()
        self.conv1 = nn.Conv1d(n_tags, 128, kernel_size=7, padding=3)
        self.conv2 = nn.Conv1d(128, hidden_dim, kernel_size=5, padding=2)
        self.pool = nn.AdaptiveAvgPool1d(1)
        self.bn1 = nn.BatchNorm1d(128)

    def forward(self, x):
        x = torch.relu(self.bn1(self.conv1(x)))
        x = torch.relu(self.conv2(x))
        x = self.pool(x).squeeze(-1)  # Global Average Pooling
        return x


def contrastive_augmentations(segment):
    """
    시계열 대조 학습용 증강 쌍 생성

    같은 코일의 다른 부분 → Positive pair
    다른 코일 → Negative pair

    증강 방법:
    - 시간 스케일링 (압연 속도 ±10%)
    - 서브샘플링 (다른 시간 해상도)
    - 가우시안 노이즈 추가 (센서 노이즈 모방)
    - 마스킹 (일부 태그 0으로 치환)
    """
    aug1 = segment + np.random.normal(0, 0.01, segment.shape)  # 노이즈
    aug2 = segment[::2]  # 절반 서브샘플링 → 동일 길이로 보간

    aug2_interp = np.interp(
        np.linspace(0, 1, len(segment)),
        np.linspace(0, 1, len(aug2)),
        aug2
    )
    return aug1, aug2_interp
```

**소량 라벨 미세 조정 (Fine-tuning)**:

```python
def finetune_with_defect_labels(pretrained_encoder, X_labeled, y_labeled):
    """
    대조 학습으로 사전학습된 인코더 + 선형 분류기
    소량 라벨(불량 번들)로 미세 조정

    배경: B5(전이학습)는 외부 데이터 필요 → 현재 불가
    E7은 자사 IBA 데이터(939K건)로 자체 사전학습 → 현실적
    """
    classifier = nn.Sequential(
        pretrained_encoder,
        nn.Linear(64, 32),
        nn.ReLU(),
        nn.Linear(32, 2),  # 불량/정상
    )

    # 인코더는 freeze, 분류기만 학습 (소량 데이터 과적합 방지)
    for param in pretrained_encoder.parameters():
        param.requires_grad = False

    optimizer = torch.optim.Adam(classifier[-3:].parameters(), lr=1e-3)
    criterion = nn.CrossEntropyLoss(
        weight=torch.tensor([1.0, 5.0])  # 불량 클래스 가중치 상향
    )

    return classifier
```

**현실적 요건**: A1(번들 시간 윈도우) 또는 A5(공정 단계 정렬) 완료 시 의미 있는 학습 가능. 구현 복잡도 대비 B4(준지도) 먼저 시도 권장.

---

### E8. Time-Series Foundation Models 활용 (시계열 파운데이션 모델)

| 항목 | 내용 |
|------|------|
| **대응 한계** | L5(소량 데이터), B5(전이학습 — 현재 적용 불가)의 현실적 대안 |
| **난이도** | ★★★ (중) |
| **기대효과** | ★★★ (중~높음) |
| **핵심 아이디어** | 대규모 시계열 데이터로 사전학습된 모델을 **Zero-shot / Few-shot**으로 이상 탐지에 적용 — 유사 공정 데이터 없이도 전이 가능 |

**옵션 1: Amazon Chronos (Few-shot 예측 → 잔차 이상 탐지)**

```python
# pip install chronos-forecasting
from chronos import ChronosPipeline
import torch

def chronos_anomaly_detection(tag_series, context_length=100, prediction_length=10):
    """
    Chronos: AWS가 공개한 시계열 파운데이션 모델 (zero-shot)
    사용법: 과거 데이터 → 미래 예측 → 실제값과 괴리 = 이상 점수

    장점:
    - 별도 학습 불필요 (zero-shot)
    - 불확실성 구간 제공 (E1 Conformal과 유사 효과)
    - 70M 파라미터 이하 버전 → CPU 실행 가능
    """
    pipeline = ChronosPipeline.from_pretrained(
        "amazon/chronos-t5-small",   # tiny/small/base/large 중 선택
        device_map="cpu",
        torch_dtype=torch.bfloat16,
    )

    context = torch.tensor(tag_series[-context_length:].values).unsqueeze(0)

    forecast = pipeline.predict(
        context=context,
        prediction_length=prediction_length,
        num_samples=20,
    )
    # forecast: (n_samples, prediction_length)

    median_forecast = forecast.median(dim=0).values
    q10 = forecast.quantile(0.10, dim=0).values
    q90 = forecast.quantile(0.90, dim=0).values

    return median_forecast, q10, q90
```

**옵션 2: Moment (이상 탐지 전용 파운데이션 모델)**

```python
# pip install momentfm
from momentfm import MOMENTPipeline

def moment_anomaly_detection(multivariate_segment):
    """
    MOMENT: CMU가 공개한 시계열 파운데이션 모델
    이상 탐지 Task에 직접 사전학습됨 → 추가 fine-tuning 없이 사용 가능

    입력: (batch, n_channels, seq_len) — 다변량 압연 구간
    출력: 이상 점수 시계열
    """
    model = MOMENTPipeline.from_pretrained(
        "AutonLab/MOMENT-1-large",
        model_kwargs={'task_name': 'anomaly_detection'},
    )
    model.init()

    # 512-토큰 단위 슬라이딩 윈도우 처리
    from momentfm.utils.utils import control_randomness
    control_randomness(seed=42)

    trunc_timeseries = torch.tensor(multivariate_segment).float().unsqueeze(0)
    output = model(trunc_timeseries)

    return output.anomaly_scores  # (batch, seq_len)
```

**통합 활용 전략**:

```python
def foundation_model_ensemble_score(tag_series_dict, defect_daily):
    """
    Chronos + MOMENT 이상 점수를 C5(앙상블 건강 지수)에 추가 입력

    1. Chronos: 단변량 태그별 예측 잔차 → 이상 점수
    2. MOMENT: 다변량 압연 구간 이상 점수
    3. 두 점수를 C5에 결합 → 7가지 기법 앙상블
    """
    chronos_scores = {}
    for tag, series in tag_series_dict.items():
        _, q10, q90 = chronos_anomaly_detection(series)
        actual_next = series.iloc[-10:].values  # 실제 다음 구간
        # 실제값이 90% 예측 구간 밖 → 이상
        chronos_scores[tag] = np.mean(
            (actual_next < q10) | (actual_next > q90)
        )

    combined_score = (
        0.5 * np.mean(list(chronos_scores.values())) +
        # MOMENT 점수 결합
    )
    return combined_score
```

**현실적 고려사항**:
- Chronos-small: 파라미터 46M, CPU 추론 가능 (단변량, 수 초 내)
- MOMENT-Large: GPU 권장, CPU도 가능하나 느림
- Zero-shot 성능은 도메인 특화 모델 대비 제한적 → 경보 보조 지표로 활용 권장
- B5(전이학습)의 현실적 대안: 유사 공정 데이터 없이도 대규모 시계열로 사전학습된 특징 활용 가능

---

### E1~E8 통합 요약

| ID | 기법 | 대응 한계 | 난이도 | 기대효과 | 기존 방안 대비 차별점 |
|----|------|----------|--------|---------|---------------------|
| E1 | Conformal Prediction | L5, L7 | ★★ | ★★★★ | 예측 불확실성의 수학적 보장 (B2/B6 보완) |
| E2 | BOCPD / PELT 변점 탐지 | L1, L3 | ★★ | ★★★★ | 변점 확률 연속화 (C3 대비 임계값 불민감) |
| E3 | EVT + Quantile Regression | L5, L7 | ★★ | ★★★★ | 극단 불량 이벤트 꼬리 분포 모델링 (B2 보완) |
| E4 | Rule Mining + ML Hybrid | L4, L5, L7 | ★★ | ★★★★ | 도메인 규칙 + 데이터 기반 해석 규칙 발굴 |
| E5 | Functional Data Analysis | L1, L3 | ★★★ | ★★★★ | 시계열 형태(Shape) 정보 보존 (C2 대비) |
| E6 | Causal Discovery / DAG | L1, L5 | ★★★ | ★★★★ | 단방향 인과 구조 학습 (C3 Granger 확장) |
| E7 | Contrastive Learning | L5, L7 | ★★★ | ★★★ | 939K 비라벨 데이터 자체 표현 학습 (B4/B5 통합) |
| E8 | Time-series Foundation Models | L5 | ★★★ | ★★★ | Zero-shot 이상 탐지 (B5 현실적 대안) |

---

## 8. 우선순위 및 실행 로드맵

### Phase 1: 즉시 실행 (1-2일)

> **목표**: 코드 변경 최소화, 기존 인프라 활용

| ID | 방안 | 변경 범위 | 기대 효과 |
|----|------|----------|-----------|
| A2 | remarks 정규화 완성 | `config.py` 매핑 확장 + regex 추가 | 번들 불량 유형 분류 정확도 향상 |
| A4 | 강종 코드 매핑 | `config.py`에 매핑 딕셔너리 추가, `common.py` 쿼리 수정 | 강종별 불량 분석 활성화 |
| A3 | weight_error 프록시 활용 | 파생 변수 함수 추가 | 1,086건 연속값 라벨 확보 |

**구체적 작업**:
1. `memo_prod_result` remarks 전수 조사 (SQL 쿼리)
2. `DEFECT_TYPE_MAPPING` 확장 + `DEFECT_TYPE_PATTERNS` (regex) 추가
3. `STEEL_GRADE_MAPPING` 딕셔너리 추가
4. `fetch_coil_aggregated_data()`, `fetch_daily_defect_rates()` 강종 필터 옵션 추가
5. weight_error 파생 변수 생성 유틸리티 함수 작성

### Phase 2: 단기 (3-5일)

> **목표**: 기존 분석 결과 재활용, 새로운 인사이트 도출

| ID | 방안 | 전제 조건 | 기대 효과 |
|----|------|----------|-----------|
| C4 | 불량일 vs 정상일 프로파일 비교 | Phase 1 완료 | 불량 연관 태그 Top-N 식별 |
| C3 | 변점 ↔ 불량 상관 | CUSUM/EWMA 결과 존재 | 공정 불안정 ↔ 불량 연관성 검증 |
| B1 | 이상치-우선 접근 | 6가지 이상치 결과 존재 | 이상치 ∩ 고불량일 교차 검증 |

**구체적 작업**:
1. `tag_defect_matrix.parquet` 기반 불량일/정상일 분리 + 태그별 검정
2. CUSUM/EWMA 결과 파일 로드 → 일별 변점 카운트 → 불량률 Spearman 상관
3. 6가지 이상치 탐지 결과 → 고불량일 교차율 + Fisher's exact test

### Phase 3: 중기 (1-2주)

> **목표**: 새로운 데이터 연결 및 예측 모델 구축

| ID | 방안 | 전제 조건 | 기대 효과 |
|----|------|----------|-----------|
| A1 | 번들 시간 윈도우 재구성 | A5 또는 윈도우 크기 추정 | 번들-IBA 연결 → 코일 단위 분석 가능 |
| B2 | 불량률 회귀 | Phase 1 + 2 피처 엔지니어링 | 불량률 예측 모델 + feature importance |
| C2 | 파생 특성 엔지니어링 | Phase 1 완료 | PCA 기반 잠재 변수 발견 |
| C5 | 앙상블 건강 지수 | Phase 2 완료 (이상치 결과) | 단일 설비 상태 지표 |
| C1 | 불량 전조 구간 분석 | 이미 시차변수 생성 중 | D-1~D-3 전조 패턴 태그 식별 |

### Phase 4: 장기 (필요 시)

> **목표**: 고급 ML 기법 적용

| ID | 방안 | 전제 조건 | 기대 효과 |
|----|------|----------|-----------|
| B3 | Multi-Instance Learning | A1 완료 (번들-IBA 연결) | 불량 원인 시점 자동 식별 |
| B4 | 준지도학습 | Phase 3 완료 | 라벨 전파로 학습 데이터 확대 |
| B6 | 베이지안 접근법 | Phase 2-3 완료 | 불확실성 정량화 |
| A5 | 공정 단계 시간 정렬 | IBA 원시 시계열 접근 | 정밀 코일 구간 식별 |
| B7 | 데이터 증강 | Phase 1 완료 | SMOTE/ADASYN 불균형 해소 |

---

### Phase E1~E2: 확장 기법 — 빠른 적용 가능 (Phase 1~2 병행 권장)

> **목표**: 기존 방안과 독립적으로 병행 적용 가능한 확장 기법 (의존성 낮음)

| ID | 방안 | 전제 조건 | 기대 효과 | 우선도 |
|----|------|----------|-----------|--------|
| E1 | Conformal Prediction | B2 또는 B6 완료 | 불확실성 정량화, 현장 신뢰도 향상 | ★★★★ |
| E2 | BOCPD / PELT 변점 탐지 | IBA 일별 통계 | 변점 특성 추출 → B2 입력 보강 | ★★★★ |
| E3 | EVT + Quantile Regression | Phase 1 완료 | 고불량 이벤트 꼬리 모델링 | ★★★★ |
| E4 | Rule Mining + ML Hybrid | Phase 2 완료 (이상치 결과) | 도메인 규칙 자동 발굴 | ★★★★ |

### Phase E3: 확장 기법 — 중기 (Phase 3 병행)

> **목표**: 초 단위 시계열 직접 활용 및 인과 구조 학습

| ID | 방안 | 전제 조건 | 기대 효과 |
|----|------|----------|-----------|
| E5 | Functional Data Analysis | A1 / A5 완료 (코일 구간 식별) | 시계열 형태 기반 불량 구분 |
| E6 | Causal Discovery / DAG | Phase 2 완료 | 공정 인과 구조 → 직접 원인 태그 식별 |
| E7 | Contrastive Learning | A1 / A5 완료 | 비라벨 IBA 활용 표현 학습 |
| E8 | Foundation Models | IBA 시계열 접근 | Zero-shot 이상 탐지 보조 지표 |

---

## 9. 기법 간 비교 매트릭스

### 9.1 데이터 요구량 vs 기대효과 2×2 매트릭스

```
                    기대효과 높음
                         │
    B6(베이지안)          │  B1(이상치-우선) ★★★★★
    C4(프로파일 비교)     │  B2(불량률 회귀) ★★★★★
    C3(변점↔불량)        │  A1(번들 윈도우)
    A2(remarks 정규화)   │  A4(강종 매핑)
    A3(weight_error)     │  C5(앙상블 건강지수)
                         │
   ─────────────────────┼──────────────────────
                         │
    B5(전이학습)          │  B3(MIL)
    B7(데이터 증강)       │  B4(준지도학습)
    E8(Foundation)        │  C2(파생 특성 + PCA)
    E7(Contrastive)       │  E5(FDA) ← 형태 보존
    E6(Causal DAG)        │  E2(BOCPD 변점)
                         │
                    기대효과 낮음

  데이터 요구량 낮음 ◀────────────▶ 데이터 요구량 높음
```

### 9.2 기존 인프라 활용도 점수

| 방안 | 기존 코드 활용 | 기존 결과 활용 | 추가 개발량 | 종합 활용도 |
|------|--------------|--------------|------------|------------|
| B1 이상치-우선 | ★★★★★ | ★★★★★ | ★ (최소) | **95%** |
| C3 변점↔불량 | ★★★★ | ★★★★★ | ★★ | **90%** |
| A4 강종 매핑 | ★★★★ | ★★★ | ★ (최소) | **85%** |
| A2 remarks 정규화 | ★★★★ | ★★★ | ★ (최소) | **85%** |
| C4 프로파일 비교 | ★★★★ | ★★★ | ★★ | **80%** |
| A3 weight_error | ★★★ | ★★ | ★★ | **75%** |
| C1 전조 분석 | ★★★★ | ★★★ | ★★ | **75%** |
| **E1 Conformal** | ★★★ | ★★★ | ★★ | **70%** |
| **E2 BOCPD/PELT** | ★★★ | ★★★ | ★★ | **65%** |
| **E3 EVT+Quantile** | ★★★ | ★★ | ★★ | **65%** |
| **E4 Rule Mining** | ★★★ | ★★★★ | ★★ | **65%** |
| B2 불량률 회귀 | ★★★ | ★★ | ★★★ | **60%** |
| C2 파생 특성 | ★★★ | ★★ | ★★★ | **55%** |
| C5 건강 지수 | ★★★ | ★★★★ | ★★★ | **55%** |
| **E6 Causal DAG** | ★★ | ★★ | ★★★ | **45%** |
| A1 번들 윈도우 | ★★ | ★ | ★★★★ | **35%** |
| B6 베이지안 | ★★ | ★ | ★★★ | **30%** |
| **E8 Foundation** | ★★ | ★ | ★★★ | **30%** |
| B4 준지도학습 | ★★ | ★ | ★★★★ | **20%** |
| **E5 FDA** | ★★ | ★ | ★★★★ | **20%** |
| **E7 Contrastive** | ★ | ★ | ★★★★ | **15%** |
| A5 공정단계 정렬 | ★★ | ★ | ★★★★ | **25%** |
| B7 데이터 증강 | ★★ | ★ | ★★★ | **30%** |
| B3 MIL | ★ | ★ | ★★★★★ | **15%** |
| B5 전이학습 | ★ | ★ | ★★★★★ | **10%** |

### 9.3 한계별 방안 매핑 (Coverage Matrix) — 확장판

| 한계 | A1 | A2 | A3 | A4 | A5 | B1 | B2 | B3 | B4 | B5 | B6 | B7 | C1 | C2 | C3 | C4 | C5 | **E1** | **E2** | **E3** | **E4** | **E5** | **E6** | **E7** | **E8** |
|------|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|---|---|---|---|---|---|---|---|
| L1 시간해상도 | ●● | | | | ●● | ● | | ●● | | | | | ● | | ● | | ● | | ●● | | | ●● | ● | | ● |
| L2 강종코드 | | | | ●● | | | | | | | | | | | | | | | | | | | | | |
| L3 번들-코일 | ●● | | | | ●● | | | ●● | | | | | | | | | | | ● | | | ●● | | ● | |
| L4 remarks | | ●● | | | | | | | | | | | | | | | | | | | ●● | | | | |
| L5 소량 | | | ● | | | ● | ●● | | ●● | ● | ●● | ●● | ● | ● | | ● | | ●● | | ●● | ● | | ● | ●● | ●● |
| L6 강종필터 | | | | ●● | | | | | | | | | | | | | | | | | | | | | |
| L7 불균형 | | | | | | ● | ●● | | ● | | ● | ●● | | | | ● | | ● | | ●● | ●● | | | ● | |

> ●● = 직접 해결, ● = 부분 완화

### 9.4 기존 방안 vs 확장 기법 공백 보완 분석

```
[ 기존 17가지 방안이 커버하지 못한 영역 ]

1. 예측 불확실성 정량화 (Uncertainty Quantification)
   → E1 Conformal Prediction이 보완
   → "예측값을 얼마나 신뢰할 수 있나?" 의 수학적 답변

2. 극단 불량 이벤트 꼬리 모델링
   → E3 EVT + Quantile Regression이 보완
   → 평균 기반 B2 회귀가 놓치는 상위 5~10% 고불량 구간 포착

3. 변점 탐지의 확률화 (임계값 민감성 해소)
   → E2 BOCPD/PELT가 보완
   → C3의 CUSUM 이진 신호 → 연속 확률 점수로 전환

4. 도메인 규칙의 데이터 기반 발굴
   → E4 Rule Mining이 보완
   → 전문가 인터뷰 없이 데이터에서 IF-THEN 규칙 자동 학습

5. 시계열 형태(Shape) 정보 보존
   → E5 FDA가 보완
   → C2 파생 특성(통계 요약)이 손실하는 곡선 형태 패턴 보존

6. 구조적 인과(방향성 DAG)
   → E6 Causal Discovery가 보완
   → C3 Granger(쌍방향 인과) → 시스템 전체 인과 구조 학습

7. 939K 비라벨 IBA 데이터 활용
   → E7 Contrastive Learning이 보완
   → B4 준지도학습(라벨 전파)과 달리 표현 공간 자체를 먼저 학습

8. B5(전이학습) 현실적 대안
   → E8 Foundation Models이 보완
   → 외부 유사 공정 데이터 없이 Zero-shot 이상 탐지 가능
```

---

## 부록: 핵심 참조 파일 경로

| 파일 | 참조 내용 |
|------|----------|
| `schema/defect_selection_status_schema.sql` | 일별 불량 집계 스키마 (강종, 사이즈, 불량수량/중량/률) |
| `schema/memo_prod_result_schema.sql` | 번들 단위 생산결과 (production_datetime, weight_error, remarks) |
| `schema/production_defect_views.sql` | 2개 분석 뷰 + 인덱스 권장 |
| `scripts/deep_analysis/config.py:159-181` | DEFECT_TYPE_MAPPING (현재 12개 항목) |
| `scripts/deep_analysis/data_preparation.py` | DataPreparator: 일별 집계 → tag_defect_matrix 생성 |
| `scripts/additional_methods/common.py:357-470` | fetch_coil_aggregated_data (강종 미필터), fetch_daily_defect_rates |
| `scripts/comprehensive_analysis/02_correlation_analysis.py` | CorrelationAnalyzer (Pearson/Spearman × 불량률) |
| `scripts/comprehensive_analysis/03_causality_analysis.py` | CausalityAnalyzer (Granger/PCMCI/Transfer Entropy) |
| `config/tag_filter_config.yaml` | 태그별 필터 설정 (3단계 상속) |
| `analysis_output/steel_grade_iqr_analysis_v2/` | IQR, Adj-IQR, Rolling Z, CUSUM/EWMA 결과 |
| `analysis_output/mahalanobis_realdata/` | Mahalanobis 다변량 이상치 결과 |
| `analysis_output/context_aware_outlier/` | Context-Aware 이상치 결과 |

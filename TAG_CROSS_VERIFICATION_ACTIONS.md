# IBA_TAG_BY_DH.md 기준 추가 분석 필요 태그

> **기준 문서**: [`references/IBA_TAG_BY_DH.md`](references/IBA_TAG_BY_DH.md) — 현업 확인 47개 태그
> **검증일**: 2026-02-10
> **검증 대상**: DB `iba_timeseries_unified_alter` (224컬럼) + `steel_grade_iqr_analysis_v2.py` (79태그, 9카테고리)

---

## 1. 현황

```
현업 확인 47개 태그 → 분석 스크립트 포함 여부:

✅ DB 존재 + 분석 포함        ████████░░░░░░░░░░░░░░░░  15개 (32%)
⚠️ DB 존재 + 분석 미포함      ████░░░░░░░░░░░░░░░░░░░░   8개 (17%)  ← 즉시 추가 가능
❌ DB 미존재 + 수집 필요       ████████████░░░░░░░░░░░░  24개 (51%)  ← 수집 선행 필요
```

---

## 2. 즉시 분석 추가 가능 — 8개 (DB 데이터 존재, 분석 미포함)

코드 수정만으로 분석에 편입 가능한 태그:

### 2.1 PR6~PR9 속도 — 6개 → `09_PR_Detailed` 또는 신규 카테고리

| # | DB 컬럼 | PLC | 측정 | 현업 §2.5 |
|---|---------|:---:|------|:---------:|
| 16 | `PR6L1_ACT_SPD_MS` (#107) | 52 | PR6 L1 속도 | 🟢 |
| 17 | `PR6L2_ACT_SPD_MS` (#114) | 52 | PR6 L2 속도 | 🟢 |
| 20 | `PR7L1_ACT_SPD_MS` (#121) | 52 | PR7 L1 속도 | 🟢 |
| 21 | `PR7L2_ACT_SPD_MS` (#128) | 52 | PR7 L2 속도 | 🟢 |
| 24 | `PR8L1_ACT_SPD_MS` (#135) | 52 | PR8 L1 속도 | 🟢 |
| 28 | `PR9L1_ACT_SPD_MS` (#142) | 52 | PR9 L1 속도 | 🟢 |

> 현재 `09_PR_Detailed`는 토크(ACT_TORQUE) 6개만 포함. 속도(ACT_SPD_MS) 6개를 추가하면 토크-속도 상관 분석 가능.

### 2.2 핀치롤 3/4 기준속도 — 2개 → `08_Pinchroll` 확장

| # | DB 컬럼 | PLC | 측정 | 현업 §2.3 |
|---|---------|:---:|------|:---------:|
| 7 | `PINCHROLL_3_REFERENCE_SPEED` (#63) | 25 | PR3 기준속도 | 🟢 |
| 10 | `PINCHROLL_4_REFERENCE_SPEED` (#64) | 25 | PR4 기준속도 | 🟢 |

> 현재 `08_Pinchroll`에는 REFERENCE_TORQUE는 있으나 REFERENCE_SPEED가 누락. 실제-기준 속도 비교 분석 가능.

### 2.3 추가 검토 — PR6~PR9 DB 미분석 잔여 컬럼

IBA_TAG_BY_DH.md에는 기재되지 않았으나 DB에 존재하는 PR6~PR9 컬럼:

| 유형 | 컬럼 패턴 | PR6 L1/L2 | PR7 L1/L2 | PR8 L1 | PR9 L1 | 소계 |
|------|----------|:---------:|:---------:|:------:|:------:|:----:|
| 속도% | `_ACT_SPD_PERC` | 2 | 2 | 1 | 1 | 6 |
| 전류% | `_ACT_CURR_PERC` | 2 | 2 | 1 | 1 | 6 |
| 전력% | `_ACT_POWER_PERC` | 2 | 2 | 1 | 1 | 6 |
| 기준속도 | `_REF_SPD_MS` | 2 | 2 | 1 | 1 | 6 |
| 기준토크 | `_REF_TORQUE` | 2 | 2 | 1 | 1 | 6 |
| | | | | | **합계** | **30** |

> 현재 분석 중 6개(토크) + 추가 6개(속도) = 12개. 나머지 30개는 품질 분석 관련성을 판단하여 선별 추가 권장.

---

## 3. 수집 선행 필요 — 24개 (DB 미존재)

IBA 수집 설정 + DB 컬럼 신설이 필요한 태그:

### 3.1 PR8L2/PR9L2 (PLC 52) — 4개

| # | PLC 태그 | 측정 | 비고 |
|---|---------|------|------|
| 25 | `PR8L2.ACT_SPD_MS` | PR8 L2 속도 | PLC에 존재, DB 미적재 |
| 27 | `PR8L2.ACT_TORQUE` | PR8 L2 토크 | PLC에 존재, DB 미적재 |
| 29 | `PR9L2.ACT_SPD_MS` | PR9 L2 속도 | PLC에 존재, DB 미적재 |
| 31 | `PR9L2.ACT_TORQUE` | PR9 L2 토크 | PLC에 존재, DB 미적재 |

> PR8/PR9는 현재 L1만 DB에 존재. L2 4개 컬럼 신설 후 기존 분석 파이프라인에 즉시 편입 가능.

### 3.2 VCC 본체 (PLC 54) — 8개

| # | PLC 태그 | 측정 |
|---|---------|------|
| 34 | `VCCL1.LOOP_ACT_SET` | VCC L1 루프 높이 설정값 |
| 35 | `VCCL2.LOOP_ACT_SET` | VCC L2 루프 높이 설정값 |
| 36 | `VCCL1.LOOP_ACT_HEIGHT` | VCC L1 루프 높이 실적값 |
| 37 | `VCCL2.LOOP_ACT_HEIGHT` | VCC L2 루프 높이 실적값 |
| 38 | `VCCL1.ACT_SPD_MS` | VCC L1 실제 속도 |
| 39 | `VCCL2.ACT_SPD_MS` | VCC L2 실제 속도 |
| 40 | `VCCL1.ACT_TORQUE` | VCC L1 실제 토크 |
| 41 | `VCCL2.ACT_TORQUE` | VCC L2 실제 토크 |

> 현업 설문 #8(권취 온도), #9(권취 Step)과 직접 관련. `VCC_TAG_DATA_REQUEST.md` §3.4에서 🔴→🟡로 상향 가능.

### 3.3 디스트리뷰터 (PLC 54) — 6개

| # | PLC 태그 | 측정 |
|---|---------|------|
| 42 | `DSTL1.VER_ACT_SPD` | DST L1 수직 속도 |
| 43 | `DSTL2.VER_ACT_SPD` | DST L2 수직 속도 |
| 44 | `DSTL1.VER_ACT_POS` | DST L1 수직 위치 |
| 45 | `DSTL2.VER_ACT_POS` | DST L2 수직 위치 |
| 46 | `DSTL1.VER_ACT_TORQUE` | DST L1 수직 토크 |
| 47 | `DSTL2.VER_ACT_TORQUE` | DST L2 수직 토크 |

> `VCC_TAG_DATA_REQUEST.md` §3.3에서 서술형으로 기술된 항목의 실제 PLC 태그명. 🔴→🟡로 상향 가능.

### 3.4 Water Box 온도 (PLC 63) — 2개

| # | PLC 태그 | 측정 |
|---|---------|------|
| 32 | `WB1L1_BAR_TEMP` | WB1 L1 소재 온도 (℃) |
| 33 | `WB1L2_BAR_TEMP` | WB1 L2 소재 온도 (℃) |

> 현업 설문 #5~#7(Water pump 유량/압력/온도)과 관련. **`VCC_TAG_DATA_REQUEST.md` v1.2에 미기재 — 추가 반영 필요.**

### 3.5 핀치롤 5 / PR005 (PLC 31, 33) — 4개

| # | PLC 태그 | 측정 |
|---|---------|------|
| 12 | `PR005 - Actual Speed` | PR5 실제 속도 |
| 13 | `PR005 - Reference Speed` | PR5 기준 속도 |
| 14 | `PR005 - Drive - Actual Torque` | PR5 토크 |
| 15 | `PR005 - Mill Speed Correction` | PR5 밀 속도 보정 |

> SH5 앞 중간 핀치롤. **`VCC_TAG_DATA_REQUEST.md` v1.2에 미기재 — 추가 반영 필요.**

---

## 4. 문서 업데이트 필요 사항

| 대상 문서 | 필요 조치 | 사유 |
|----------|----------|------|
| `VCC_TAG_DATA_REQUEST.md` v1.2 → v1.3 | WB1 2개 + PR005 4개 태그 신규 추가, VCC/DST 14개 🔴→🟡 상향 | IBA_TAG_BY_DH.md 신규 발견 미반영 |
| `steel_grade_iqr_analysis_v2.py` | `09_PR_Detailed` 속도 6개 + `08_Pinchroll` 기준속도 2개 추가 | DB 데이터 미활용 |
| `tag_filter_config.yaml` | 추가 태그 필터 규칙 설정 | 스크립트 확장 연동 |
| `README.md` v3.3 → v3.4 | 분석 커버리지 변경사항 반영 | 스크립트 수정 후 |
| `ATTENTION_TAGS_REPORT.md` | 확장 태그 포함 재생성 | 분석 재실행 후 |

---

*Generated: 2026-02-10 — IBA_TAG_BY_DH.md 교차 검증 기반*

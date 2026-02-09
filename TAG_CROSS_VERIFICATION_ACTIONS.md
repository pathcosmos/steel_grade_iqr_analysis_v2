# 현업 태그 교차 검증 후 조치 항목

> **기준 문서**: [`references/IBA_TAG_BY_DH.md`](references/IBA_TAG_BY_DH.md) — 현업 확인 47개 태그
> **검증일**: 2026-02-09
> **검증 대상**: ClickHouse `iba_timeseries_unified_alter` (224컬럼) + 분석 스크립트 `steel_grade_iqr_analysis_v2.py` (79태그)

---

## 1. 검증 결과 요약

```
현업 확인 47개 태그 검증 현황:

✅ DB 존재 + 분석 포함        ████████████░░░░░░░░░░░░  17개 (36%)
⚠️ DB 존재 + 분석 미포함      ███████░░░░░░░░░░░░░░░░░  11개 (23%)
❌ DB 미존재 + 수집 필요       ████████████░░░░░░░░░░░░  19개 (40%)
```

---

## 2. 수정/조사 필요 문서 목록

### 2.1 분석 스크립트 — 즉시 수정 가능 (코드 변경)

| 우선순위 | 대상 파일 | 조치 내용 | 관련 태그 수 |
|:--------:|----------|----------|:----------:|
| ⭐⭐⭐ | `scripts/steel_grade_iqr_analysis_v2.py` | `09_PR_Detailed` 카테고리에 PR6~PR9 속도 태그 추가 | +7개 |
| ⭐⭐ | `scripts/steel_grade_iqr_analysis_v2.py` | `08_Pinchroll` 카테고리에 PR3/4 REFERENCE_SPEED 추가 | +2개 |
| ⭐⭐ | `scripts/steel_grade_iqr_analysis_v2.py` | PR6~PR9 전류/전력/기준 태그 신규 카테고리 검토 | +27개 |

**상세 — `09_PR_Detailed` 확장 대상 (DB에 데이터 존재, 분석 미포함)**:

| DB 컬럼 | 타입 | 현재 분석 |
|---------|------|:---------:|
| `PR6L1_ACT_SPD_MS` (#107) | 속도 | ❌ → 추가 |
| `PR6L2_ACT_SPD_MS` (#114) | 속도 | ❌ → 추가 |
| `PR7L1_ACT_SPD_MS` (#121) | 속도 | ❌ → 추가 |
| `PR7L2_ACT_SPD_MS` (#128) | 속도 | ❌ → 추가 |
| `PR8L1_ACT_SPD_MS` (#135) | 속도 | ❌ → 추가 |
| `PR9L1_ACT_SPD_MS` (#142) | 속도 | ❌ → 추가 |
| `PINCHROLL_3_REFERENCE_SPEED` (#63) | 기준속도 | ❌ → 추가 |
| `PINCHROLL_4_REFERENCE_SPEED` (#64) | 기준속도 | ❌ → 추가 |

> 이 8개 태그 추가만으로 현업 요청 커버리지: 36% → 53%

**추가 검토 — PR6~PR9 DB 미분석 27개 컬럼**:

| 유형 | 컬럼 패턴 | PR6 L1/L2 | PR7 L1/L2 | PR8 L1 | PR9 L1 | 소계 |
|------|----------|:---------:|:---------:|:------:|:------:|:----:|
| 속도% | `_ACT_SPD_PERC` | 2 | 2 | 1 | 1 | 6 |
| 전류% | `_ACT_CURR_PERC` | 2 | 2 | 1 | 1 | 6 |
| 전력% | `_ACT_POWER_PERC` | 2 | 2 | 1 | 1 | 6 |
| 기준속도 | `_REF_SPD_MS` | 2 | 2 | 1 | 1 | 6 |
| 기준토크 | `_REF_TORQUE` | 2 | 2 | 1 | 1 | 6 |
| | | | | | **합계** | **30** |

> 속도 7개(위 표)를 빼면 나머지 **23개** 추가 가능. 품질 분석 관련성을 판단하여 선별 추가 권장.

---

### 2.2 필터 설정 — 스크립트 확장 시 함께 수정

| 우선순위 | 대상 파일 | 조치 내용 |
|:--------:|----------|----------|
| ⭐⭐⭐ | `config/tag_filter_config.yaml` | 신규 카테고리 또는 기존 카테고리 확장에 맞춰 필터 규칙 추가 |

**필요 작업**:
- `09_PR_Detailed` 확장 시 → 속도 태그에도 `coiling_transient: true` 적용
- PR 속도 태그 전용 카테고리 신설 시 → 별도 필터 임계값 설정
- `08_Pinchroll`에 REFERENCE_SPEED 추가 시 → 기존 필터 규칙 그대로 적용 가능

---

### 2.3 기존 문서 수정 필요

| 우선순위 | 대상 문서 | 조치 내용 | 사유 |
|:--------:|----------|----------|------|
| ⭐⭐⭐ | [`VCC_TAG_DATA_REQUEST.md`](VCC_TAG_DATA_REQUEST.md) v1.2 | `WB1L1/L2_BAR_TEMP` 2개, `PR005` 4개 태그 추가 반영 | IBA_TAG_BY_DH.md에서 신규 발견된 태그가 미기재 |
| ⭐⭐ | [`references/IBA_TAG_BY_DH.md`](references/IBA_TAG_BY_DH.md) | §1.1 PLC별 태그 수 오류 정정 | PLC21: 3→4, PLC52: 20→16, PLC54: 12→14 |
| ⭐⭐ | [`README.md`](README.md) v3.3 | §14 분석 스크립트 확장 결과 반영 | 스크립트 수정 후 분석 커버리지 변경사항 |
| ⭐ | [`ATTENTION_TAGS_REPORT.md`](ATTENTION_TAGS_REPORT.md) | 신규 태그 분석 후 재생성 | 현재 85태그 기준 → 확장 후 재분석 필요 |

---

### 2.4 DB/시스템 조사 필요 (외부 조치)

| 우선순위 | 조사 대상 | 조치 내용 | 관련 태그 | 담당 |
|:--------:|----------|----------|:---------:|:----:|
| ⭐⭐⭐ | `iba_tag_usage_check` 테이블 | PLC52/54/63/31/33 태그 목록 임포트 | 19개 전체 | DB 관리자 |
| ⭐⭐⭐ | ClickHouse `iba_timeseries_unified_alter` | PR8L2/PR9L2 컬럼 4개 신설 + IBA 수집 설정 | 4개 | IBA 관리자 |
| ⭐⭐⭐ | PLC54 (CPU12_GEN4) | VCC + 디스트리뷰터 14개 태그 IBA 수집 설정 | 14개 | IBA 관리자 |
| ⭐⭐⭐ | PLC63 (CPU13_GEN3) | WB1L1/L2_BAR_TEMP 2개 IBA 수집 + DB 컬럼 신설 | 2개 | IBA 관리자 |
| ⭐⭐ | PLC31/33 (HSD) | PR005 4개 태그 IBA 수집 + DB 컬럼 신설 | 4개 | IBA 관리자 |

**PLC 태그 목록 임포트 상세**:

현재 `iba_tag_usage_check`에는 PLC21/22/23만 임포트되어 있음. 아래 PLC의 태그 목록을 임포트하면 현업 확인 태그명의 정확성을 독립 검증할 수 있음:

| PLC | 모듈명 | 미임포트 태그 영역 | 예상 태그 |
|:---:|--------|------------------|----------|
| 24 | CPU2 REAL4 | 미확인 | — |
| 25 | CPU2 REAL5 | 핀치롤 기준속도 (이미 DB 적재) | 확인용 |
| 31 | PLC-HSD_02 | PR005 속도/보정 | 3개 |
| 33 | PLC-HSD_04 | PR005 토크 | 1개 |
| 52 | CPU12_GEN2 | PR6~PR9 L1/L2 | 42개 (DB 적재 확인) |
| 54 | CPU12_GEN4 | VCC + 디스트리뷰터 | 14개+ |
| 63 | CPU13_GEN3 | Water Box 온도 | 2개+ |
| 101 | 미확인 | 미확인 | — |
| 102 | MELSEC-구동용 | 가열로 (이미 DB 적재) | 확인용 |

---

### 2.5 VCC_TAG_DATA_REQUEST.md 추가 반영 항목 상세

`IBA_TAG_BY_DH.md` 교차 검증으로 발견된 신규 태그 — 현재 `VCC_TAG_DATA_REQUEST.md` v1.2에 미기재:

#### (A) Water Box 소재 온도 — §3.1에 추가

| PLC 태그명 | 측정 유형 | PLC | 출처 |
|-----------|----------|:---:|------|
| `WB1L1_BAR_TEMP` | WB1 L1 소재 온도 (℃) | 63 | 현업 확인 |
| `WB1L2_BAR_TEMP` | WB1 L2 소재 온도 (℃) | 63 | 현업 확인 |

> §3.1에서 서술형으로 기술된 "밀 출구 온도, SH8 입구 온도" 항목 중 이 2개 태그를 **실제 PLC 태그명**으로 기술 가능.
> 🔴 미확인 → 🟡 PLC 참조(현업 확인)로 상태 변경 가능.

#### (B) PR005 핀치롤 5 — §3.8 또는 신규 섹션에 추가

| PLC 태그명 | 측정 유형 | PLC | 출처 |
|-----------|----------|:---:|------|
| `PR005 - Actual Speed` | PR5 실제 속도 (m/s) | 31 | 현업 확인 |
| `PR005 - Reference Speed` | PR5 기준 속도 (m/s) | 31 | 현업 확인 |
| `PR005 - Drive - Actual Torque` | PR5 토크 (%) | 33 | 현업 확인 |
| `PR005 - Mill Speed Correction` | PR5 밀 속도 보정 (%) | 31 | 현업 확인 |

> 현재 VCC_TAG_DATA_REQUEST.md는 PR6~PR9만 다루고 있음. PR005(핀치롤 5)는 SH5 앞에 위치하는 중간 핀치롤로, 압연~권취 연결 구간의 장력/속도 제어에 중요.

#### (C) VCC/DST 실제 PLC 태그명 확정 — §3.3, §3.4 업데이트

현업이 PLC54(CPU12_GEN4)에서 확인한 실제 태그명:

| 현재 문서 상태 | 확정 PLC 태그명 | 섹션 |
|--------------|---------------|:----:|
| 🔴 서술형 "VCC 실제 속도" | `VCCL1.ACT_SPD_MS` / `VCCL2.ACT_SPD_MS` | §3.4 |
| 🔴 서술형 "VCC 실제 토크" | `VCCL1.ACT_TORQUE` / `VCCL2.ACT_TORQUE` | §3.4 |
| 🔴 서술형 "루프 높이 설정/실적" | `VCCL1/2.LOOP_ACT_SET` / `LOOP_ACT_HEIGHT` | §3.4 |
| 🔴 서술형 "디스트리뷰터 수직 속도" | `DSTL1.VER_ACT_SPD` / `DSTL2.VER_ACT_SPD` | §3.3 |
| 🔴 서술형 "디스트리뷰터 수직 위치" | `DSTL1.VER_ACT_POS` / `DSTL2.VER_ACT_POS` | §3.3 |
| 🔴 서술형 "디스트리뷰터 수직 토크" | `DSTL1.VER_ACT_TORQUE` / `DSTL2.VER_ACT_TORQUE` | §3.3 |

> 이 14개 태그는 v1.2에서 🔴 미확인(서술형)이었으나, 현업 확인에 의해 **🟡 PLC 참조(현업 확인)**로 상향 가능.

---

## 3. 실행 로드맵

### Phase 0: 문서 정비 (즉시, 코드 변경 없음)

- [ ] `IBA_TAG_BY_DH.md` PLC별 태그 수 오류 정정 (3건)
- [ ] `VCC_TAG_DATA_REQUEST.md` v1.3 — WB1 2개 + PR005 4개 추가, VCC/DST 14개 상태 업그레이드
- [ ] `README.md` v3.4 — 문서 변경사항 반영

### Phase 1: 분석 확장 (즉시, DB 데이터 이미 존재)

- [ ] `steel_grade_iqr_analysis_v2.py` — `09_PR_Detailed`에 속도 7개 추가
- [ ] `steel_grade_iqr_analysis_v2.py` — `08_Pinchroll`에 기준속도 2개 추가
- [ ] `tag_filter_config.yaml` — 확장 태그 필터 규칙 추가
- [ ] 4개 강종(B5/D4/D5/N5) 재분석 실행
- [ ] `ATTENTION_TAGS_REPORT.md` 재생성

### Phase 2: DB 확장 (외부 조치 필요)

- [ ] `iba_tag_usage_check` — PLC52/54/63/31/33 태그 목록 임포트
- [ ] ClickHouse — PR8L2/PR9L2 4개 컬럼 신설
- [ ] IBA 수집 설정 — PLC63 Water Box 2개 태그
- [ ] IBA 수집 설정 — PLC31/33 PR005 4개 태그
- [ ] IBA 수집 설정 — PLC54 VCC+디스트리뷰터 14개 태그
- [ ] 수집 시작 후 → Phase 1과 동일한 분석 파이프라인에 편입

### Phase 3: 전체 검증

- [ ] 전체 태그 재분석 및 `ATTENTION_TAGS_REPORT.md` 최종 갱신
- [ ] `README.md` 최종 버전 업데이트
- [ ] 현업 피드백 반영

---

## 4. 우선순위 판단 기준

| 기준 | 가중치 | 설명 |
|------|:------:|------|
| 품질 영향도 | 40% | 권취 품질 분석에 직접 기여하는 정도 |
| 실행 용이성 | 30% | 즉시 가능(코드만) vs 외부 조치 필요(DB/IBA) |
| 현업 관심도 | 20% | IBA_TAG_BY_DH.md 설문조사 순위 반영 |
| 데이터 가용성 | 10% | 이미 DB에 있는지 여부 |

### 우선순위 결과

| 순위 | 조치 | 태그 수 | 근거 |
|:----:|------|:-------:|------|
| 1 | PR6~PR9 속도 분석 추가 | +7 | DB 존재 + 현업 관심(#3 핀치롤 토크/속도) |
| 2 | PR3/4 기준속도 분석 추가 | +2 | DB 존재 + 실제-기준 비교 분석 가능 |
| 3 | VCC_TAG_DATA_REQUEST.md 신규 태그 반영 | +6 | 문서 완전성 + 수집 요청 근거 |
| 4 | VCC/DST 태그명 확정 반영 | 14 | 🔴→🟡 상향으로 수집 요청 신뢰도 향상 |
| 5 | PLC 태그 목록 임포트 | — | 태그명 독립 검증 기반 마련 |
| 6 | PR8L2/PR9L2 DB 컬럼 신설 | +4 | 외부 조치 필요, L1 대비 데이터 보완 |
| 7 | WB1/PR005 수집 시작 | +6 | 외부 조치 필요, 현업 관심(#5~#7 Water pump) |
| 8 | VCC/DST 수집 시작 | +14 | 외부 조치 필요, 현업 관심(#8~#9 권취 온도/Step) |

---

## 5. 참조 문서

| 문서 | 역할 |
|------|------|
| [`references/IBA_TAG_BY_DH.md`](references/IBA_TAG_BY_DH.md) | 현업 확인 태그 목록 (본 문서의 기준) |
| [`VCC_TAG_DATA_REQUEST.md`](VCC_TAG_DATA_REQUEST.md) | VCC/권취부 태그 수집 요청서 v1.2 |
| [`README.md`](README.md) | 프로젝트 메인 문서 v3.3 |
| [`ATTENTION_TAGS_REPORT.md`](ATTENTION_TAGS_REPORT.md) | 주의 필요 태그 분석 보고서 |
| `config/tag_filter_config.yaml` | 태그별 필터 설정 |
| `scripts/steel_grade_iqr_analysis_v2.py` | 강종별 IQR 분석 스크립트 |
| `docs/iba_timeseries_unified_alter_schema.md` | DB 스키마 정의 (224컬럼) |

---

*Generated: 2026-02-09 — IBA_TAG_BY_DH.md 교차 검증 기반*

# 현업 확인 권취 IBA 주요 태그 목록

> **출처**: DH 현업 (설비/공정 담당자)
> **목적**: 권취 품질 분석에 필수적인 IBA 태그 식별
> **DB 검증**: 2026-02-09 기준 ClickHouse `iba_timeseries_unified_alter` 교차 확인 완료

---

## 1. PLC별 태그 수집 현황

현업이 확인한 권취 관련 IBA 태그를 PLC 출처별로 정리합니다.

### 1.1 PLC 출처 요약

| PLC | 모듈명 | 설비 영역 | 태그 수 | DB 적재 |
|:---:|--------|----------|:-------:|:-------:|
| 102 | MELSEC-구동용 | 가열로 | 1개 | 🟢 전부 |
| 21 | CPU2 INT1 | 스탠드 14 + Finishing Block | 3개 | 🟢 전부 |
| 22 | CPU2 INT2 | 핀치롤 3/4 토크 | 2개 | 🟢 전부 |
| 25 | CPU2 REAL5 | 핀치롤 3/4 속도 | 4개 | 🟢 전부 |
| 31 | PLC-HSD_02 | PR005 속도/보정 | 3개 | ❌ 없음 |
| 33 | PLC-HSD_04 | PR005 토크 | 1개 | ❌ 없음 |
| **52** | **CPU12_GEN2** | **PR6~PR9 (L1/L2)** | **20개** | ⚠️ 일부 |
| **63** | **CPU13_GEN3** | **Water Box 온도** | **2개** | ❌ 없음 |
| **54** | **CPU12_GEN4** | **VCC + 디스트리뷰터** | **12개** | ❌ 없음 |

> **핵심**: PLC52/54/63의 태그가 `iba_tag_usage_check`에 미임포트 상태. 이 PLC들이 VCC 권취 영역의 핵심 데이터를 보유하고 있음이 현업에 의해 확인됨.

---

## 2. 태그 상세 목록

### 2.1 가열로 (PLC 102) — 🟢 DB 적재 완료

| # | PLC | 태그명 | 측정 유형 | 단위 | DB 컬럼명 |
|---|:---:|--------|-----------|:----:|-----------|
| 1 | 102 | Furnace Exit Discharge Billet Temperature | 추출 빌렛 온도 | ℃ | `FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE` |

### 2.2 스탠드 14 + Finishing Block (PLC 21) — 🟢 DB 적재 완료

| # | PLC | 태그명 | 측정 유형 | 단위 | DB 컬럼명 |
|---|:---:|--------|-----------|:----:|-----------|
| 2 | 21 | STAND 14 Actual Speed | 스탠드 14 실제 속도 | RPM | `STAND_14_ACTUAL_SPEED` |
| 3 | 21 | FINISHING BLOCK Actual Speed | FB 실제 속도 | RPM | `FINISHING_BLOCK_ACTUAL_SPEED` |
| 4 | 21 | FINISHING BLOCK Master Actual Torque | FB 마스터 토크 | % | `FINISHING_BLOCK_MASTER_ACTUAL_TORQUE` |
| 5 | 21 | FINISHING BLOCK Slave Actual Torque | FB 슬레이브 토크 | % | `FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE` |

### 2.3 핀치롤 3/4 (PLC 22, 25) — 🟢 DB 적재 완료

| # | PLC | 태그명 | 측정 유형 | 단위 | DB 컬럼명 |
|---|:---:|--------|-----------|:----:|-----------|
| 6 | 25 | Pinchroll 3 Actual Speed | PR3 실제 속도 | m/s | `PINCHROLL_3_ACTUAL_SPEED` |
| 7 | 25 | Pinchroll 3 Reference Speed | PR3 기준 속도 | m/s | `PINCHROLL_3_REFERENCE_SPEED` |
| 8 | 22 | Pinchroll 3 Actual Torque | PR3 실제 토크 | % | `PINCHROLL_3_ACTUAL_TORQUE` |
| 9 | 25 | Pinchroll 4 Actual Speed | PR4 실제 속도 | m/s | `PINCHROLL_4_ACTUAL_SPEED` |
| 10 | 25 | Pinchroll 4 Reference Speed | PR4 기준 속도 | m/s | `PINCHROLL_4_REFERENCE_SPEED` |
| 11 | 22 | Pinchroll 4 Actual Torque | PR4 실제 토크 | % | `PINCHROLL_4_ACTUAL_TORQUE` |

### 2.4 핀치롤 5 / PR005 (PLC 31, 33) — ❌ DB 미적재

| # | PLC | PLC 태그명 | 측정 유형 | 단위 | DB 상태 |
|---|:---:|-----------|-----------|:----:|:-------:|
| 12 | 31 | PR005 - Actual Speed | PR5 실제 속도 | m/s | ❌ |
| 13 | 31 | PR005 - Reference Speed | PR5 기준 속도 | m/s | ❌ |
| 14 | 33 | PR005 - Drive - Actual Torque | PR5 드라이브 토크 | % | ❌ |
| 15 | 31 | PR005 - Mill Speed Correction | PR5 밀 속도 보정 | % | ❌ |

> **참고**: PR005(핀치롤 5)는 SH5 앞에 위치하는 중간 핀치롤. DB에 미적재 상태로 수집 필요.

### 2.5 PR6~PR9 L1/L2 (PLC 52) — ⚠️ DB 일부 적재

| # | PLC | PLC 태그명 | 측정 유형 | 단위 | DB 상태 | 비고 |
|---|:---:|-----------|-----------|:----:|:-------:|------|
| 16 | 52 | PR6L1.ACT_SPD_MS | PR6 L1 실제 속도 | m/s | 🟢 | DB 컬럼 `PR6L1_ACT_SPD_MS` |
| 17 | 52 | PR6L2.ACT_SPD_MS | PR6 L2 실제 속도 | m/s | 🟢 | DB 컬럼 `PR6L2_ACT_SPD_MS` |
| 18 | 52 | PR6L1.ACT_TORQUE | PR6 L1 실제 토크 | % | 🟢 | DB 컬럼, **현재 분석 중** |
| 19 | 52 | PR6L2.ACT_TORQUE | PR6 L2 실제 토크 | % | 🟢 | DB 컬럼, **현재 분석 중** |
| 20 | 52 | PR7L1.ACT_SPD_MS | PR7 L1 실제 속도 | m/s | 🟢 | DB 컬럼 `PR7L1_ACT_SPD_MS` |
| 21 | 52 | PR7L2.ACT_SPD_MS | PR7 L2 실제 속도 | m/s | 🟢 | DB 컬럼 `PR7L2_ACT_SPD_MS` |
| 22 | 52 | PR7L1.ACT_TORQUE | PR7 L1 실제 토크 | % | 🟢 | DB 컬럼, **현재 분석 중** |
| 23 | 52 | PR7L2.ACT_TORQUE | PR7 L2 실제 토크 | % | 🟢 | DB 컬럼, **현재 분석 중** |
| 24 | 52 | PR8L1.ACT_SPD_MS | PR8 L1 실제 속도 | m/s | 🟢 | DB 컬럼 `PR8L1_ACT_SPD_MS` |
| 25 | 52 | **PR8L2.ACT_SPD_MS** | PR8 L2 실제 속도 | m/s | **❌** | **PLC에 존재하나 DB 미적재** |
| 26 | 52 | PR8L1.ACT_TORQUE | PR8 L1 실제 토크 | % | 🟢 | DB 컬럼, **현재 분석 중** |
| 27 | 52 | **PR8L2.ACT_TORQUE** | PR8 L2 실제 토크 | % | **❌** | **PLC에 존재하나 DB 미적재** |
| 28 | 52 | PR9L1.ACT_SPD_MS | PR9 L1 실제 속도 | m/s | 🟢 | DB 컬럼 `PR9L1_ACT_SPD_MS` |
| 29 | 52 | **PR9L2.ACT_SPD_MS** | PR9 L2 실제 속도 | m/s | **❌** | **PLC에 존재하나 DB 미적재** |
| 30 | 52 | PR9L1.ACT_TORQUE | PR9 L1 실제 토크 | % | 🟢 | DB 컬럼, **현재 분석 중** |
| 31 | 52 | **PR9L2.ACT_TORQUE** | PR9 L2 실제 토크 | % | **❌** | **PLC에 존재하나 DB 미적재** |

> **중요 발견**: 현업이 PR8L2/PR9L2 태그를 PLC52에서 확인함. DB 스키마에는 PR8L2/PR9L2 컬럼이 전혀 없으므로, **PLC에는 존재하지만 IBA 수집 대상에서 누락**된 것으로 판단됨. `VCC_TAG_DATA_REQUEST.md` v1.2에서 14개 신규 수집 필요 태그로 분류됨.

### 2.6 Water Box 온도 (PLC 63) — ❌ DB 미적재

| # | PLC | PLC 태그명 | 측정 유형 | 단위 | DB 상태 |
|---|:---:|-----------|-----------|:----:|:-------:|
| 32 | 63 | WB1L1_BAR_TEMP | Water Box 1 L1 소재 온도 | ℃ | ❌ |
| 33 | 63 | WB1L2_BAR_TEMP | Water Box 1 L2 소재 온도 | ℃ | ❌ |

> **참고**: Water Box 통과 소재 온도로, 냉각 효과 직접 측정 가능. `VCC_TAG_DATA_REQUEST.md` §3.1 Water Box 영역과 관련. PLC63(CPU13_GEN3)에서 수집 가능.

### 2.7 VCC 본체 (PLC 54) — ❌ DB 미적재

| # | PLC | PLC 태그명 | 측정 유형 | 단위 | DB 상태 |
|---|:---:|-----------|-----------|:----:|:-------:|
| 34 | 54 | VCCL1.LOOP_ACT_SET | VCC L1 루프 높이 설정값 | mm | ❌ |
| 35 | 54 | VCCL2.LOOP_ACT_SET | VCC L2 루프 높이 설정값 | mm | ❌ |
| 36 | 54 | VCCL1.LOOP_ACT_HEIGHT | VCC L1 루프 높이 실적값 | mm | ❌ |
| 37 | 54 | VCCL2.LOOP_ACT_HEIGHT | VCC L2 루프 높이 실적값 | mm | ❌ |
| 38 | 54 | VCCL1.ACT_SPD_MS | VCC L1 실제 속도 | m/s | ❌ |
| 39 | 54 | VCCL2.ACT_SPD_MS | VCC L2 실제 속도 | m/s | ❌ |
| 40 | 54 | VCCL1.ACT_TORQUE | VCC L1 실제 토크 | % | ❌ |
| 41 | 54 | VCCL2.ACT_TORQUE | VCC L2 실제 토크 | % | ❌ |

> **중요**: VCC 본체의 핵심 운전 파라미터(루프 높이, 속도, 토크) 8개의 **실제 PLC 태그명**이 현업에 의해 확인됨. `VCC_TAG_DATA_REQUEST.md` §3.4에서 🔴 미확인으로 분류된 항목이나, 이 문서에 의해 PLC54(CPU12_GEN4)에 존재함이 확인됨.

### 2.8 디스트리뷰터 (PLC 54) — ❌ DB 미적재

| # | PLC | PLC 태그명 | 측정 유형 | 단위 | DB 상태 |
|---|:---:|-----------|-----------|:----:|:-------:|
| 42 | 54 | DSTL1.VER_ACT_SPD | 디스트리뷰터 L1 수직 실제 속도 | mm/s | ❌ |
| 43 | 54 | DSTL2.VER_ACT_SPD | 디스트리뷰터 L2 수직 실제 속도 | mm/s | ❌ |
| 44 | 54 | DSTL1.VER_ACT_POS | 디스트리뷰터 L1 수직 실제 위치 | mm | ❌ |
| 45 | 54 | DSTL2.VER_ACT_POS | 디스트리뷰터 L2 수직 실제 위치 | mm | ❌ |
| 46 | 54 | DSTL1.VER_ACT_TORQUE | 디스트리뷰터 L1 수직 실제 토크 | % | ❌ |
| 47 | 54 | DSTL2.VER_ACT_TORQUE | 디스트리뷰터 L2 수직 실제 토크 | % | ❌ |

> **중요**: 디스트리뷰터의 수직 운전 파라미터(속도, 위치, 토크) 6개의 **실제 PLC 태그명**이 현업에 의해 확인됨. `VCC_TAG_DATA_REQUEST.md` §3.3에서 서술형으로 기술된 항목 중 일부가 여기서 태그명이 확정됨.

---

## 3. 현업 설문조사 결과

현업 담당자에게 "권취 품질 분석에 가장 중요한 데이터"를 설문한 결과:

| 순위 | 관심 항목 | 매핑 태그/영역 | 현재 분석 |
|:----:|----------|---------------|:--------:|
| 1 | 가열로 추출 온도 | `FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE` | ✅ |
| 2 | 가열로 체류시간 | DB에 직접 태그 없음 (추출 시각 차이로 계산 가능) | ❌ |
| 3 | Pinchroll Torque | PR3/4 + PR6~PR9 토크 | ✅ 일부 |
| 4 | 카리바/리브 방향 | 제품 규격 관련 (IBA 태그 아님) | ❌ |
| 5 | Water pump 유량 | Water Box 유량 → PLC63 영역 | ❌ |
| 6 | Water pump 압력 | Water Box 압력 → PLC63 영역 | ❌ |
| 7 | Water pump 온도 | `WB1L1/L2_BAR_TEMP` (PLC63) | ❌ |
| 8 | 권취 온도 | VCC 영역 온도 → PLC54 영역 | ❌ |
| 9 | 권취 Step (설정) | VCC 시퀀스 → PLC54 영역 | ❌ |
| 10 | Stand 14 토크 | `STAND_14_ACTUAL_TORQUE` | ✅ |
| 11 | Stand 1 토크 | `STAND_1_ACTUAL_TORQUE` | ✅ |
| 12 | Stand 2 토크 | `STAND_2_ACTUAL_TORQUE` | ✅ |

> **분석**: 현업 12개 요청 중 **4개만 분석 중** (33%). 수집 불가 항목(#2 체류시간, #4 카리바)을 제외하면, **나머지 6개는 PLC52/54/63 태그 수집으로 해결 가능**.

---

## 4. 현재 AI 분석 커버리지

현재 AI 분석 시스템이 다루는 카테고리:

| # | 카테고리 | 설명 | 태그 수 | 현업 요청 대비 |
|---|----------|------|:-------:|:-----------:|
| 01 | Furnace_Top_Temperature | 가열로 상부 온도 | 4개 | ✅ 충족 |
| 02 | Furnace_Bottom_Temperature | 가열로 하부 온도 | 3개 | ✅ 충족 |
| 03 | Furnace_Discharge_Temperature | 가열로 추출 온도 | 1개 | ✅ 충족 (설문 #1) |
| 04 | Furnace_Auxiliary | 가열로 보조설비 | 4개 | ✅ 충족 |
| 06 | Stand_Speed | 스탠드 속도 | 15개 | ✅ 충족 |
| 08 | Pinchroll | 핀치롤 | 8개 | ⚠️ 부분 (설문 #3) |
| 09 | PR_Detailed | PR 상세 토크 (L1/L2) | 6개 | ⚠️ 부분 (설문 #3) |

> **Gap**: 05_Stand_Torque(16개), 07_Stand_Load(15개), 09_Cooling_Water(2개)가 목록에 빠져 있으나 실제 분석에는 포함됨. 현업이 관심 없는 카테고리로 판단됨.

---

## 5. DB 적재 현황 종합

### 5.1 태그 수집/적재 현황 요약

```
현업 확인 태그 47개 총 현황:

🟢 DB 적재 완료 (분석 가능)     ██████████████████░░░░░░  28개 (60%)
   └─ 현재 분석 중                                        22개
   └─ 미분석 (뷰 확장 필요)                               6개

❌ DB 미적재 (수집 필요)         ██████████░░░░░░░░░░░░░░  19개 (40%)
   └─ PLC52: PR8L2/PR9L2                                  4개
   └─ PLC54: VCC + 디스트리뷰터                            14개
   └─ PLC63: Water Box 온도                                2개 (신규 발견*)
   └─ PLC31/33: PR005                                      4개 (신규 발견*)
```

### 5.2 PLC별 수집 조치 필요 사항

| PLC | 태그 수 | 조치 | 우선순위 |
|:---:|:-------:|------|:--------:|
| PLC52 (CPU12_GEN2) | 4개 | PR8L2/PR9L2 속도+토크 DB 적재 | ⭐⭐⭐ |
| PLC54 (CPU12_GEN4) | 14개 | VCC 루프/속도/토크 + 디스트리뷰터 전체 | ⭐⭐⭐ |
| PLC63 (CPU13_GEN3) | 2개 | Water Box 소재 온도 | ⭐⭐⭐ |
| PLC31/33 (HSD) | 4개 | PR005 속도/토크/보정 | ⭐⭐ |

> ***신규 발견**: `WB1L1/L2_BAR_TEMP`(PLC63)와 `PR005` 관련 4개 태그(PLC31/33)는 `VCC_TAG_DATA_REQUEST.md` v1.2에 미기재. 해당 문서에 추가 반영 필요.

---

## 6. 참조

| 문서 | 설명 |
|------|------|
| [`VCC_TAG_DATA_REQUEST.md`](../VCC_TAG_DATA_REQUEST.md) | VCC/권취부 태그 수집 요청서 v1.2 (DB 검증 완료) |
| `docs/iba_timeseries_unified_alter_schema.md` | ClickHouse DB 스키마 정의 (217개 컬럼) |
| `config/tag_filter_config.yaml` | 현재 분석 필터 설정 |

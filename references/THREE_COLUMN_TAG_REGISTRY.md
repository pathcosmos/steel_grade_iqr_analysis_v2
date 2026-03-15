# 3컬럼 분류 태그 레지스트리 (ClickHouse 실측 기준)

> **작성일**: 2026-03-15
> **DB 소스**: `iba_timeseries_unified_alter` (총 227 컬럼)
> **목적**: THREE_COLUMN_DEEP_ANALYSIS.md 의 3분류(PLC 공급 / 현업 수요 / AI 실행)에 대한 실제 태그 목록을 ClickHouse 조회 결과 기준으로 정리
> **범례**: ✅ DB 적재 완료 &nbsp;|&nbsp; ❌ DB 미적재 (PLC 존재, 수집 안 됨) &nbsp;|&nbsp; 💬 개념 항목 (직접 태그 없음)

---

## 요약 스코어카드

| 분류 | 정의 기준 | 총 태그/항목 | DB 적재 | DB 미적재 |
|:----:|---------|:-----------:|:------:|:--------:|
| **Column 1** PLC 공급 | 설비에 물리적으로 존재하는 PLC 태그 (현업 확인 기준) | 47개 | 27개 | 20개 |
| **Column 2** 현업 수요 | 현업 설문조사 품질 중요 항목 | 12개 항목 | 4개 항목 직접 매핑 | 8개 항목 미수집/개념 |
| **Column 3** AI 실행 | AI 분석 카테고리에 포함된 태그 | 95개 정의 | 91개 | 4개 (PR8/9 L2) |

---

## Column 1 — PLC 공급 (P) : 47개

현업이 확인한 설비 PLC 수집 태그 전체 목록. 아래 공정 구간별로 분류.

### 가열로 (Furnace)

| # | 태그명 | 설명 | DB |
|---|--------|------|:--:|
| 1 | `FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE` | 빌렛 추출 온도 | ✅ |

### 스탠드 (Stand)

| # | 태그명 | 설명 | DB |
|---|--------|------|:--:|
| 2 | `STAND_14_ACTUAL_SPEED` | 14번 스탠드 실제 속도 | ✅ |

> 📌 Stand 토크(STAND_1/2/14_ACTUAL_TORQUE 등)는 PLC 확인 47개 목록 외이나 **DB에 존재**하며 AI가 분석 중.

### 마무리 블록 (Finishing Block)

| # | 태그명 | 설명 | DB |
|---|--------|------|:--:|
| 3 | `FINISHING_BLOCK_ACTUAL_SPEED` | FB 실제 속도 | ✅ |
| 4 | `FINISHING_BLOCK_MASTER_ACTUAL_TORQUE` | FB 마스터 토크 | ✅ |
| 5 | `FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE` | FB 슬레이브 토크 | ✅ |

### PR3/4 핀치롤

| # | 태그명 | 설명 | DB |
|---|--------|------|:--:|
| 6 | `PINCHROLL_3_ACTUAL_SPEED` | PR3 실제 속도 | ✅ |
| 7 | `PINCHROLL_3_REFERENCE_SPEED` | PR3 기준 속도 | ✅ |
| 8 | `PINCHROLL_3_ACTUAL_TORQUE` | PR3 실제 토크 | ✅ |
| 9 | `PINCHROLL_4_ACTUAL_SPEED` | PR4 실제 속도 | ✅ |
| 10 | `PINCHROLL_4_REFERENCE_SPEED` | PR4 기준 속도 | ✅ |
| 11 | `PINCHROLL_4_ACTUAL_TORQUE` | PR4 실제 토크 | ✅ |

### PR005 (출구 롤러 / 입구 핀치롤)

| # | 태그명 | 설명 | DB |
|---|--------|------|:--:|
| 12 | `EXIT_FURNACE_RT_SEC_1_ACTUAL_SPEED` | 가열로 출구 롤러 Sec1 속도 | ✅ |
| 13 | `EXIT_FURNACE_RT_SEC_2_ACTUAL_SPEED` | 가열로 출구 롤러 Sec2 속도 | ✅ |
| 14 | `ENTRY_MILL_PINCHROLL_ACTUAL_SPEED` | 밀 입구 핀치롤 실제 속도 | ✅ |
| 15 | `ENTRY_MILL_PINCHROLL_REFERENCE_SPEED` | 밀 입구 핀치롤 기준 속도 | ✅ |

### PR6~9 (권취 라인 핀치롤)

| # | 태그명 | 설명 | DB |
|---|--------|------|:--:|
| 16 | `PR6L1_ACT_SPD_MS` | PR6 L1 실제 속도 (m/s) | ✅ |
| 17 | `PR6L2_ACT_SPD_MS` | PR6 L2 실제 속도 (m/s) | ✅ |
| 18 | `PR6L1_ACT_TORQUE` | PR6 L1 실제 토크 | ✅ |
| 19 | `PR6L2_ACT_TORQUE` | PR6 L2 실제 토크 | ✅ |
| 20 | `PR7L1_ACT_SPD_MS` | PR7 L1 실제 속도 (m/s) | ✅ |
| 21 | `PR7L2_ACT_SPD_MS` | PR7 L2 실제 속도 (m/s) | ✅ |
| 22 | `PR7L1_ACT_TORQUE` | PR7 L1 실제 토크 | ✅ |
| 23 | `PR7L2_ACT_TORQUE` | PR7 L2 실제 토크 | ✅ |
| 24 | `PR8L1_ACT_SPD_MS` | PR8 L1 실제 속도 (m/s) | ✅ |
| 25 | `PR8L2_ACT_SPD_MS` | PR8 L2 실제 속도 (m/s) | ❌ PLC52 미적재 |
| 26 | `PR8L1_ACT_TORQUE` | PR8 L1 실제 토크 | ✅ |
| 27 | `PR8L2_ACT_TORQUE` | PR8 L2 실제 토크 | ❌ PLC52 미적재 |
| 28 | `PR9L1_ACT_SPD_MS` | PR9 L1 실제 속도 (m/s) | ✅ |
| 29 | `PR9L2_ACT_SPD_MS` | PR9 L2 실제 속도 (m/s) | ❌ PLC52 미적재 |
| 30 | `PR9L1_ACT_TORQUE` | PR9 L1 실제 토크 | ✅ |
| 31 | `PR9L2_ACT_TORQUE` | PR9 L2 실제 토크 | ❌ PLC52 미적재 |

### Water Box

| # | 태그명 | 설명 | DB |
|---|--------|------|:--:|
| 32 | `WB1L1_BAR_TEMP` | Water Box L1 소재 온도 | ❌ PLC63 미수집 |
| 33 | `WB1L2_BAR_TEMP` | Water Box L2 소재 온도 | ❌ PLC63 미수집 |

### VCC 본체 (권취 냉각기)

| # | 태그명 | 설명 | DB |
|---|--------|------|:--:|
| 34 | `VCCL1.LOOP_ACT_SET` | VCC L1 루프 설정값 | ❌ PLC54 미수집 |
| 35 | `VCCL2.LOOP_ACT_SET` | VCC L2 루프 설정값 | ❌ PLC54 미수집 |
| 36 | `VCCL1.LOOP_ACT_HEIGHT` | VCC L1 루프 높이 | ❌ PLC54 미수집 |
| 37 | `VCCL2.LOOP_ACT_HEIGHT` | VCC L2 루프 높이 | ❌ PLC54 미수집 |
| 38 | `VCCL1.ACT_SPD_MS` | VCC L1 실제 속도 | ❌ PLC54 미수집 |
| 39 | `VCCL2.ACT_SPD_MS` | VCC L2 실제 속도 | ❌ PLC54 미수집 |
| 40 | `VCCL1.ACT_TORQUE` | VCC L1 실제 토크 | ❌ PLC54 미수집 |
| 41 | `VCCL2.ACT_TORQUE` | VCC L2 실제 토크 | ❌ PLC54 미수집 |

### 디스트리뷰터 (Distributor)

| # | 태그명 | 설명 | DB |
|---|--------|------|:--:|
| 42 | `DSTL1.ACT_SPD_MS` | DST L1 수직 속도 | ❌ DB 미수집 |
| 43 | `DSTL2.ACT_SPD_MS` | DST L2 수직 속도 | ❌ DB 미수집 |
| 44 | `DSTL1.ACT_POS_MM` | DST L1 수직 위치 | ❌ DB 미수집 |
| 45 | `DSTL2.ACT_POS_MM` | DST L2 수직 위치 | ❌ DB 미수집 |
| 46 | `DSTL1.ACT_TORQUE` | DST L1 토크 | ❌ DB 미수집 |
| 47 | `DSTL2.ACT_TORQUE` | DST L2 토크 | ❌ DB 미수집 |

### Column 1 집계

| 구간 | 총 태그 | DB 적재 | DB 미적재 |
|------|:------:|:------:|:--------:|
| 가열로 | 1 | 1 | 0 |
| 스탠드 | 1 | 1 | 0 |
| FB | 3 | 3 | 0 |
| PR3/4 | 6 | 6 | 0 |
| PR005 | 4 | 4 | 0 |
| PR6~9 | 16 | 12 | 4 (L2 미적재) |
| Water Box | 2 | 0 | 2 |
| VCC | 8 | 0 | 8 |
| DST | 6 | 0 | 6 |
| **합계** | **47** | **27** | **20** |

---

## Column 2 — 현업 수요 (O) : 12개 항목

현업 설문조사에서 품질에 중요하다고 판단한 항목. 일부는 직접 태그가 없고 계산/별도 수집이 필요.

| 순위 | 현업 항목 | 매핑 태그 | DB | 비고 |
|:---:|----------|----------|:--:|------|
| #1 | 추출 온도 | `FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE` | ✅ | AI Cat03 분석 중 |
| #2 | 체류시간 | (계산값) | 💬 | 가열로 입/출 시간 차 계산 필요 (MES) |
| #3 | PR Torque | `PINCHROLL_3_ACTUAL_TORQUE` | ✅ | AI Cat08 분석 중 |
| #3 | PR Torque | `PINCHROLL_4_ACTUAL_TORQUE` | ✅ | AI Cat08 분석 중 |
| #3 | PR Torque | `PR6L1_ACT_TORQUE` | ✅ | AI Cat09b 분석 중 |
| #3 | PR Torque | `PR6L2_ACT_TORQUE` | ✅ | AI Cat09b 분석 중 |
| #3 | PR Torque | `PR7L1_ACT_TORQUE` | ✅ | AI Cat09b 분석 중 |
| #3 | PR Torque | `PR7L2_ACT_TORQUE` | ✅ | AI Cat09b 분석 중 |
| #3 | PR Torque | `PR8L1_ACT_TORQUE` | ✅ | AI Cat09b 분석 중 |
| #3 | PR Torque | `PR8L2_ACT_TORQUE` | ❌ | PLC52 미적재 |
| #3 | PR Torque | `PR9L1_ACT_TORQUE` | ✅ | AI Cat09b 분석 중 |
| #3 | PR Torque | `PR9L2_ACT_TORQUE` | ❌ | PLC52 미적재 |
| #4 | 카리바 (교정기) | (MES 연동) | 💬 | 별도 시스템, DB 미수집 |
| #5 | Water pump 유량 | (태그명 미확정) | ❌ | PLC63 수집 필요 |
| #6 | Water pump 압력 | (태그명 미확정) | ❌ | PLC63 수집 필요 |
| #7 | Water pump 온도 | `WB1L1_BAR_TEMP`, `WB1L2_BAR_TEMP` | ❌ | PLC63 미수집 |
| #8 | 권취 온도 | `VCCL1.ACT_TORQUE` 등 VCC 관련 | ❌ | PLC54 미수집 |
| #9 | 권취 Step | `VCCL1.LOOP_ACT_SET` 등 | ❌ | PLC54 미수집 |
| #10 | Stand 14 토크 | `STAND_14_ACTUAL_TORQUE` | ✅ | AI Cat05 분석 중 (DB 존재) |
| #11 | Stand 1 토크 | `STAND_1_ACTUAL_TORQUE` | ✅ | AI Cat05 분석 중 |
| #12 | Stand 2 토크 | `STAND_2_ACTUAL_TORQUE` | ✅ | AI Cat05 분석 중 |

### Column 2 집계

| 구분 | 항목 수 | 내용 |
|------|:------:|------|
| AI 분석 중 (직접 태그 O) | 4개 항목 | #1 추출온도, #3 PR Torque(일부), #10~12 Stand 토크 |
| PLC 미적재 (수집 필요) | 5개 항목 | #5~9 Water Box/VCC 관련 |
| DB 자체 없음 (계산/외부) | 2개 항목 | #2 체류시간, #4 카리바 |
| PR Torque 일부 미적재 | 1개 항목 | #3 중 PR8L2/PR9L2 토크 2개 |
| **현업 충족률 (현재)** | **33%** | 4/12 항목 AI 분석 가능 |

---

## Column 3 — AI 실행 (A) : 95개 정의 → 91개 DB 적재

AI(`detailed_tag_iqr_analysis_v2.py` 및 `unified_core_analysis.py`)가 실제 분석에 사용하는 태그. 10개 카테고리.

### Cat01 — 가열로 상부 온도 (4개 / 전부 ✅)

| 태그명 | 설명 |
|--------|------|
| `HEATING_TOP_ZONE_NO_1_TEMPERATURE_ROOF` | 가열대 1존 천정 온도 |
| `HEATING_TOP_ZONE_NO_2_TEMPERATURE_ROOF` | 가열대 2존 천정 온도 |
| `SOAKING_TOP_ZONE_NO_1_TEMPERATURE_ROOF` | 균열대 1존 천정 온도 |
| `SOAKING_TOP_ZONE_NO_2_TEMPERATURE_ROOF` | 균열대 2존 천정 온도 |

### Cat02 — 가열로 하부 온도 (4개 / 전부 ✅)

| 태그명 | 설명 |
|--------|------|
| `HEATING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE` | 가열대 1존 바닥 반대면 온도 |
| `HEATING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE` | 가열대 2존 바닥 밀측 온도 |
| `SOAKING_BOTTOM_ZONE_NO_1_TEMPERATURE_OPP_SIDE` | 균열대 1존 바닥 반대면 온도 |
| `SOAKING_BOTTOM_ZONE_NO_2_TEMPERATURE_MILL_SIDE` | 균열대 2존 바닥 밀측 온도 |

### Cat03 — 가열로 추출 온도 (1개 / 전부 ✅)

| 태그명 | 설명 |
|--------|------|
| `FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE` | 빌렛 추출 온도 — 골든 존(A∩B∩C) |

### Cat04 — 가열로 보조설비 (10개 / 전부 ✅)

| 태그명 | 설명 |
|--------|------|
| `FURNACE_PRESSURE` | 가열로 압력 |
| `FURNACE_O2_ANALYZER` | 가열로 O2 농도 |
| `FURNACE_HYDRAULIC_TANK_OIL_TEMPERATURE` | 유압 탱크 오일 온도 |
| `COMBUSTION_AIR_TEMPERATURE` | 연소 공기 온도 |
| `MAIN_GAS_TEMPERATURE` | 주 가스 온도 |
| `MAIN_GAS_PRESSURE` | 주 가스 압력 |
| `MAIN_GAS_FLOW` | 주 가스 유량 |
| `MAIN_COMBUSTION_AIR_PRESSURE` | 주 연소 공기 압력 |
| `MAIN_WASTE_GAS_PRESSURE` | 주 배기 가스 압력 |
| `WASTE_GAS_FOR_MAIN_TEMPERATURE` | 주 배기 가스 온도 |

### Cat05 — 스탠드 토크 (16개 / 전부 ✅)

| 태그명 | 설명 |
|--------|------|
| `STAND_1_ACTUAL_TORQUE` | 1번 스탠드 실제 토크 — 골든 존 (#11) |
| `STAND_2_ACTUAL_TORQUE` | 2번 스탠드 실제 토크 — 골든 존 (#12) |
| `STAND_3_ACTUAL_TORQUE` | 3번 스탠드 실제 토크 |
| `STAND_4_ACTUAL_TORQUE` | 4번 스탠드 실제 토크 |
| `STAND_5_ACTUAL_TORQUE` | 5번 스탠드 실제 토크 |
| `STAND_6_ACTUAL_TORQUE` | 6번 스탠드 실제 토크 |
| `STAND_7_ACTUAL_TORQUE` | 7번 스탠드 실제 토크 |
| `STAND_8_ACTUAL_TORQUE` | 8번 스탠드 실제 토크 |
| `STAND_9_ACTUAL_TORQUE` | 9번 스탠드 실제 토크 |
| `STAND_10_ACTUAL_TORQUE` | 10번 스탠드 실제 토크 |
| `STAND_11_ACTUAL_TORQUE` | 11번 스탠드 실제 토크 |
| `STAND_12_ACTUAL_TORQUE` | 12번 스탠드 실제 토크 |
| `STAND_13_ACTUAL_TORQUE` | 13번 스탠드 실제 토크 |
| `STAND_14_ACTUAL_TORQUE` | 14번 스탠드 실제 토크 — 골든 존 (#10) |
| `FINISHING_BLOCK_MASTER_ACTUAL_TORQUE` | 마무리 블록 마스터 토크 |
| `FINISHING_BLOCK_SLAVE_ACTUAL_TORQUE` | 마무리 블록 슬레이브 토크 |

### Cat06 — 스탠드 속도 (15개 / 전부 ✅)

| 태그명 | 설명 |
|--------|------|
| `STAND_1_ACTUAL_SPEED` | 1번 스탠드 실제 속도 |
| `STAND_2_ACTUAL_SPEED` | 2번 스탠드 실제 속도 |
| `STAND_3_ACTUAL_SPEED` | 3번 스탠드 실제 속도 |
| `STAND_4_ACTUAL_SPEED` | 4번 스탠드 실제 속도 |
| `STAND_5_ACTUAL_SPEED` | 5번 스탠드 실제 속도 |
| `STAND_6_ACTUAL_SPEED` | 6번 스탠드 실제 속도 |
| `STAND_7_ACTUAL_SPEED` | 7번 스탠드 실제 속도 |
| `STAND_8_ACTUAL_SPEED` | 8번 스탠드 실제 속도 |
| `STAND_9_ACTUAL_SPEED` | 9번 스탠드 실제 속도 |
| `STAND_10_ACTUAL_SPEED` | 10번 스탠드 실제 속도 |
| `STAND_11_ACTUAL_SPEED` | 11번 스탠드 실제 속도 |
| `STAND_12_ACTUAL_SPEED` | 12번 스탠드 실제 속도 |
| `STAND_13_ACTUAL_SPEED` | 13번 스탠드 실제 속도 |
| `STAND_14_ACTUAL_SPEED` | 14번 스탠드 실제 속도 |
| `FINISHING_BLOCK_ACTUAL_SPEED` | 마무리 블록 실제 속도 |

### Cat07 — 스탠드 부하 (15개 / 전부 ✅)

| 태그명 | 설명 |
|--------|------|
| `STAND_1_LOAD` | 1번 스탠드 부하 |
| `STAND_2_LOAD` | 2번 스탠드 부하 |
| `STAND_3_LOAD` | 3번 스탠드 부하 |
| `STAND_4_LOAD` | 4번 스탠드 부하 |
| `STAND_5_LOAD` | 5번 스탠드 부하 |
| `STAND_6_LOAD` | 6번 스탠드 부하 |
| `STAND_7_LOAD` | 7번 스탠드 부하 |
| `STAND_8_LOAD` | 8번 스탠드 부하 |
| `STAND_9_LOAD` | 9번 스탠드 부하 |
| `STAND_10_LOAD` | 10번 스탠드 부하 |
| `STAND_11_LOAD` | 11번 스탠드 부하 |
| `STAND_12_LOAD` | 12번 스탠드 부하 |
| `STAND_13_LOAD` | 13번 스탠드 부하 |
| `STAND_14_LOAD` | 14번 스탠드 부하 |
| `FINISHING_BLOCK_LOAD` | 마무리 블록 부하 |

### Cat08 — 핀치롤 (12개 / 전부 ✅)

| 태그명 | 설명 |
|--------|------|
| `PINCHROLL_2_ACTUAL_SPEED` | PR2 실제 속도 |
| `PINCHROLL_3_ACTUAL_SPEED` | PR3 실제 속도 |
| `PINCHROLL_4_ACTUAL_SPEED` | PR4 실제 속도 |
| `PINCHROLL_2_ACTUAL_TORQUE` | PR2 실제 토크 |
| `PINCHROLL_3_ACTUAL_TORQUE` | PR3 실제 토크 — 골든 존 (#3) |
| `PINCHROLL_4_ACTUAL_TORQUE` | PR4 실제 토크 — 골든 존 (#3) |
| `PINCHROLL_2_REFERENCE_SPEED` | PR2 기준 속도 |
| `PINCHROLL_3_REFERENCE_SPEED` | PR3 기준 속도 |
| `PINCHROLL_4_REFERENCE_SPEED` | PR4 기준 속도 |
| `PINCHROLL_2_REFERENCE_TORQUE` | PR2 기준 토크 |
| `PINCHROLL_3_REFERENCE_TORQUE` | PR3 기준 토크 |
| `PINCHROLL_4_REFERENCE_TORQUE` | PR4 기준 토크 |

### Cat09 — 냉각수 (2개 / 전부 ✅)

| 태그명 | 설명 |
|--------|------|
| `INDIRECT_COOLING_WATER_FLOW` | 간접 냉각수 유량 |
| `INDIRECT_WATER_MAIN_TEMPERATURE` | 간접 냉각수 메인 온도 |

### Cat09b — PR 상세 토크/속도 (16개 정의 → 12개 ✅ / 4개 ❌)

| 태그명 | 설명 | DB |
|--------|------|:--:|
| `PR6L1_ACT_SPD_MS` | PR6 L1 실제 속도 | ✅ |
| `PR6L2_ACT_SPD_MS` | PR6 L2 실제 속도 | ✅ |
| `PR7L1_ACT_SPD_MS` | PR7 L1 실제 속도 | ✅ |
| `PR7L2_ACT_SPD_MS` | PR7 L2 실제 속도 | ✅ |
| `PR8L1_ACT_SPD_MS` | PR8 L1 실제 속도 | ✅ |
| `PR8L2_ACT_SPD_MS` | PR8 L2 실제 속도 | ❌ PLC52 미적재 |
| `PR9L1_ACT_SPD_MS` | PR9 L1 실제 속도 | ✅ |
| `PR9L2_ACT_SPD_MS` | PR9 L2 실제 속도 | ❌ PLC52 미적재 |
| `PR6L1_ACT_TORQUE` | PR6 L1 실제 토크 — 골든 존 (#3) | ✅ |
| `PR6L2_ACT_TORQUE` | PR6 L2 실제 토크 — 골든 존 (#3) | ✅ |
| `PR7L1_ACT_TORQUE` | PR7 L1 실제 토크 — 골든 존 (#3) | ✅ |
| `PR7L2_ACT_TORQUE` | PR7 L2 실제 토크 — 골든 존 (#3) | ✅ |
| `PR8L1_ACT_TORQUE` | PR8 L1 실제 토크 — 골든 존 (#3) | ✅ |
| `PR8L2_ACT_TORQUE` | PR8 L2 실제 토크 | ❌ PLC52 미적재 |
| `PR9L1_ACT_TORQUE` | PR9 L1 실제 토크 — 골든 존 (#3) | ✅ |
| `PR9L2_ACT_TORQUE` | PR9 L2 실제 토크 | ❌ PLC52 미적재 |

### Column 3 집계

| 카테고리 | 정의 태그 수 | DB 적재 | DB 미적재 |
|---------|:-----------:|:------:|:--------:|
| Cat01 가열로 상부 온도 | 4 | 4 | 0 |
| Cat02 가열로 하부 온도 | 4 | 4 | 0 |
| Cat03 가열로 추출 온도 | 1 | 1 | 0 |
| Cat04 가열로 보조설비 | 10 | 10 | 0 |
| Cat05 스탠드 토크 | 16 | 16 | 0 |
| Cat06 스탠드 속도 | 15 | 15 | 0 |
| Cat07 스탠드 부하 | 15 | 15 | 0 |
| Cat08 핀치롤 | 12 | 12 | 0 |
| Cat09 냉각수 | 2 | 2 | 0 |
| Cat09b PR 상세 | 16 | 12 | 4 |
| **합계** | **95** | **91** | **4** |

---

## DB에 존재하나 3분류 미포함 태그 (참고)

ClickHouse에 적재되어 있으나 현재 3개 분류 어디에도 포함되지 않은 태그 목록. 향후 분석 편입 검토 대상.

### PR6~9 추가 지표 (DB 존재, 분석 미포함) — 12개

| 태그명 | 설명 |
|--------|------|
| `PR6L1_REF_SPD_MS` | PR6 L1 기준 속도 |
| `PR6L1_REF_TORQUE` | PR6 L1 기준 토크 |
| `PR6L2_REF_SPD_MS` | PR6 L2 기준 속도 |
| `PR6L2_REF_TORQUE` | PR6 L2 기준 토크 |
| `PR7L1_REF_SPD_MS` | PR7 L1 기준 속도 |
| `PR7L1_REF_TORQUE` | PR7 L1 기준 토크 |
| `PR7L2_REF_SPD_MS` | PR7 L2 기준 속도 |
| `PR7L2_REF_TORQUE` | PR7 L2 기준 토크 |
| `PR8L1_REF_SPD_MS` | PR8 L1 기준 속도 |
| `PR8L1_REF_TORQUE` | PR8 L1 기준 토크 |
| `PR9L1_REF_SPD_MS` | PR9 L1 기준 속도 |
| `PR9L1_REF_TORQUE` | PR9 L1 기준 토크 |

### PR6~9 성능 비율 지표 (DB 존재, 분석 미포함) — 20개

| 태그명 | 설명 |
|--------|------|
| `PR6L1_ACT_SPD_PERC` ~ `PR9L1_ACT_SPD_PERC` | 실제 속도 백분율 (4개) |
| `PR6L1_ACT_CURR_PERC` ~ `PR9L1_ACT_CURR_PERC` | 실제 전류 백분율 (4개) |
| `PR6L1_ACT_POWER_PERC` ~ `PR9L1_ACT_POWER_PERC` | 실제 전력 백분율 (4개) |
| `PR6L2_ACT_SPD_PERC`, `PR6L2_ACT_CURR_PERC`, `PR6L2_ACT_POWER_PERC` | PR6 L2 성능 (3개) |
| `PR7L2_ACT_SPD_PERC`, `PR7L2_ACT_CURR_PERC`, `PR7L2_ACT_POWER_PERC` | PR7 L2 성능 (3개) |
| `PR8L1_ACT_SPD_PERC`, `PR8L1_ACT_CURR_PERC`, `PR8L1_ACT_POWER_PERC` | PR8 L1 성능 (3개) |
| `PR9L1_ACT_SPD_PERC`, `PR9L1_ACT_CURR_PERC`, `PR9L1_ACT_POWER_PERC` | PR9 L1 성능 (3개) |

### 스탠드 기준 속도 (DB 존재, 분석 미포함) — 15개

`STAND_1_REFERENCE_SPEED` ~ `STAND_14_REFERENCE_SPEED` (14개),  `FINISHING_BLOCK_REFERENCE_SPEED` (1개)

### 간접 냉각수 세부 온도 (DB 존재, 분석 미포함) — 36개

`INDIRECT_WATER_FOR_FIXED_BEAM_1~7_OUTLET_TEMPERATURE`,  `INDIRECT_WATER_FOR_MOVABLE_BEAM_1~6_OUTLET_TEMPERATURE`,  `INDIRECT_WATER_FOR_CHARGE_*/DISCHARGE_*/GATE_*/ITV_*` 등 설비별 세부 냉각수 출구 온도

### 연소/배기 팬 모터 온도 (DB 존재, 분석 미포함) — 14개

`COMBUSTION_AIR_BLOWER_MOTOR_*/BEARING_*`, `WASTE_GAS_FAN_MOTOR_*/BEARING_*` 등 전동기 권선/베어링 온도

### 재료 검출 센서 (DB 존재, 분석 미포함) — 10개

`DR01BFZI*`, `DT01BFZI1`, `DS01BFZI1`, `EL01~05BSL1`, `GL13BSL1`, `GM11BFZI1`, `GT15BFZI1`, `RT01BLV1_*` 등 빌렛/루프 감지 센서

---

## 3주체 벤 다이어그램 집계 (실측 기준)

| 패턴 | 의미 | 태그 수 | 대표 태그 |
|:----:|------|:------:|---------|
| **A∩B∩C** (골든 존) | PLC + 현업 + AI 모두 합의 | 9개 (DB기준) / 12개 (DB+존재기준) | 추출온도, PR3/4 토크, PR6~9_L1 토크, Stand1/2/14 토크 |
| **A∩B** only | PLC + 현업 합의, AI 미커버 | 14개 | WB온도, VCC 8개, PR8/9_L2 4개 |
| **A∩C** only | PLC + AI 합의, 현업 미언급 | 14개 | Stand14 속도, FB 3개, PR3/4 속도/기준, PR6~9 속도 |
| **A** only | PLC만 존재 | 10개 | PR005 4개, DST 6개 |

> **전체 정합도**: Jaccard J(P,O,A) = 0.14, Fleiss' Kappa κ = -0.21 (약한 불일치)
> **개선 로드맵**: PLC52 DB 적재(4개) → PLC63 수집(WB) → PLC54 수집(VCC) → MES 연동(체류시간/카리바) 순 진행 시 현업 충족률 33% → 92% 달성 가능

---

*작성: IBA 데이터 분석팀 | DB 기준일: 2026-03-15 | 원본 분석: THREE_COLUMN_DEEP_ANALYSIS.md*

# 추가 8개 태그 IQR 분석 결과

## 분석 배경

`TAG_CROSS_VERIFICATION_ACTIONS.md` 교차 검증 결과, ClickHouse DB의 `iba_timeseries_unified_alter` 테이블에 데이터가 존재하지만 기존 분석 스크립트(`steel_grade_iqr_analysis_v2.py`)에 포함되지 않은 **8개 태그**가 발견되었습니다.

이 폴더는 해당 8개 태그에 대한 **전 강종(B5/D4/D5/N5) × 전 규격(all-sizes)** IQR 분석 결과를 담고 있습니다.

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
- **규격**: 전 규격 (all-sizes)
- **분석 기법**: IQR (Interquartile Range) 이상치 탐지
- **필터**: run_only + special_ops + roll_change + coiling_transient

## 분석 결과 요약

### 강종별 규격 및 차트 수

| 강종 | 규격 | PNG 차트 수 |
|------|------|-------------|
| B5 | D13, D16 | 736 |
| D4 | D10, D13 | 1,368 |
| D5 | D10, D13 | 1,840 |
| N5 | D10, D12, D16, D20 | 3,368 |
| **합계** | **10 규격** | **7,312** |

## 폴더 구조

```
steel_grade_iqr_analysis_v2_additional_8tags/
├── README.md                          ← 본 문서
├── B5/
│   ├── D13/
│   │   ├── 08_Pinchroll/             (PINCHROLL 기준속도 2개 태그 차트)
│   │   ├── 09_PR_Detailed/           (PR 속도 6개 태그 차트)
│   │   ├── IQR_ANALYSIS_REPORT_B5_D13_KO.md
│   │   └── iqr_analysis_B5_D13_results.json
│   └── D16/
│       └── (동일 구조)
├── D4/
│   ├── D10/
│   └── D13/
├── D5/
│   ├── D10/
│   └── D13/
└── N5/
    ├── D10/
    ├── D12/
    ├── D16/
    └── D20/
```

## 수정된 파일

| 파일 | 수정 내용 |
|------|----------|
| `scripts/steel_grade_iqr_analysis_v2.py` | TAG_CATEGORIES에 8개 태그 추가, `--output-dir`/`--categories` CLI 옵션 추가 |
| `config/tag_filter_config.py` | `10_PR_Detailed` → `09_PR_Detailed` 통일, 6개 속도 태그 추가 |
| `config/tag_filter_config.yaml` | 08/09 카테고리 notes 업데이트 (태그 수, 속도 태그 명시) |
| ClickHouse VIEW | `v_iba_by_steel_grade` 뷰에 8개 컬럼 추가 (`CREATE OR REPLACE VIEW`) |

## 실행 명령어

```bash
# 특정 강종 + 특정 카테고리만 분석 (추가 태그용)
./venv/bin/python scripts/steel_grade_iqr_analysis_v2.py \
    --grade B5 --all-sizes \
    --output-dir steel_grade_iqr_analysis_v2_additional_8tags \
    --categories 08_Pinchroll 09_PR_Detailed
```

## 생성일

2026-02-20

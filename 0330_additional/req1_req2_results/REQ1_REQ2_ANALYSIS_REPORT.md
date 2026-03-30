# REQ #1+#2 분석 결과: 인과관계 + 가열로 vs 토크 선후관계

분석일: 2026-03-30 21:42
데이터: tag_defect_matrix (127일, 일별 집계)


## 1. Cross-Correlation 결과 (10쌍)

| # | 경로 | 가설 | Best Lag | CCF | 유의 | 방향 |
|:-:|------|:----:|:-------:|:---:|:----:|------|
| 1 | MAIN_GAS_FLOW → 폐가스 압력 | A | 0d | -0.484 | YES | simultaneous |
| 2 | 폐가스 압력 → Stand 1 토크 | A | 0d | -0.484 | YES | simultaneous |
| 3 | 폐가스 압력 → Stand 8 토크 | A | 0d | -0.485 | YES | simultaneous |
| 4 | Stand 6 → Stand 8 토크 | A | 0d | 0.989 | YES | simultaneous |
| 5 | Stand 8 → Stand 10 토크 | A | 0d | 0.990 | YES | simultaneous |
| 6 | Stand 10 → Stand 14 토크 | A | 0d | 0.996 | YES | simultaneous |
| 7 | Stand 14 → PR3 토크 | A | 0d | -0.579 | YES | simultaneous |
| 8 | 폐가스 압력 → PR3 토크 (전구간) | A | 0d | 0.323 | YES | simultaneous |
| 9 | Stand 8 → 폐가스 압력 (역방향) | B | 0d | -0.485 | YES | simultaneous |
| 10 | Stand 1 → 폐가스 압력 (역방향) | B | 0d | -0.484 | YES | simultaneous |

## 2. Stand 8 중점 분석

- Stand 8 토크 vs 불량률: rho=0.1705 (p=0.055241)
- 가열로 압력 vs 불량률: rho=-0.2626 (p=0.002853)
- Stand 8 vs 가열로: rho=-0.7221 (p=0.000000)

## 3. 핵심 판정

- 정방향(가열로→압연) 유의 쌍: 8/8
- 역방향(압연→가열로) 유의 쌍: 2/2

> **판정: 정방향(가열로→압연) 우세** — 가열로가 선행 지표로 판단됨

## 4. 한계 및 추가 조사

- 일별 집계 데이터로는 분 단위 물리적 lag(~1-2분)를 포착 불가
- 코일 단위 시계열 데이터로 ±5분 윈도우 분석 시 정밀도 향상 기대
- 역방향 가설 검증에는 가열로 자동 제어 메커니즘 현업 확인 필수

## 5. 생성된 파일

- `cross_correlation_results.csv` — CCF 10쌍 결과
- `process_flow_data.json` — 공정 흐름 경로 데이터
- `stand8_analysis.json` — Stand 8 상세 분석
- `chart1_process_flow_map.png` — 공정 흐름 인과 경로도
- `chart2_ccf_comparison.png` — CCF 비교 차트
- `chart3_stand8_analysis.png` — Stand 8 중점 분석 차트
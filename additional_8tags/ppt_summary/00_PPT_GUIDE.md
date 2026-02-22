# PPT 슬라이드 구성 가이드

> **목적**: 본 문서를 기반으로 PowerPoint 20~25장 분량의 경영진 보고 자료를 구성합니다.
> 각 슬라이드 번호에 해당하는 마크다운 파일과 차트 경로를 매핑합니다.

---

## 슬라이드 구성 (권장 25장)

### Part 1: 개요 (슬라이드 1-3)

| 슬라이드 | 제목 | 소스 파일 | 차트 |
|----------|------|-----------|------|
| 1 | 표지 | - | - |
| 2 | 분석 배경 및 범위 | `01_executive_summary.md` §1 | - |
| 3 | 핵심 판정 요약 | `01_executive_summary.md` §2-3 | `charts/overview/method_comparison_heatmap.png` |

### Part 2: 분석 기법 소개 (슬라이드 4-5)

| 슬라이드 | 제목 | 소스 파일 | 차트 |
|----------|------|-----------|------|
| 4 | 5가지 분석 기법 비교 | `02_methodology.md` §1 | - |
| 5 | 판정 기준 및 필터링 | `02_methodology.md` §2-3 | - |

### Part 3: 문제 태그 분석 (슬라이드 6-15)

| 슬라이드 | 제목 | 소스 파일 | 차트 |
|----------|------|-----------|------|
| 6 | 문제 태그 선별 기준 | `03_problem_tags_analysis.md` §1 | `charts/overview/top10_problem_tags.png` |
| 7 | 핀치롤 문제 태그 | `03_problem_tags_analysis.md` §2.1 | `charts/B5/IQR_PINCHROLL_*`, `charts/B5/CUSUM_PINCHROLL_*` |
| 8 | PR 토크 문제 태그 | `03_problem_tags_analysis.md` §2.2 | `charts/B5/IQR_PR*`, `charts/B5/CUSUM_PR*` |
| 9 | 스탠드 속도 문제 태그 | `03_problem_tags_analysis.md` §2.3 | `charts/D5/IQR_STAND_*_SPEED*` |
| 10 | 스탠드 부하 문제 태그 | `03_problem_tags_analysis.md` §2.4 | `charts/D5/IQR_STAND_*_LOAD*` |
| 11 | 가열로 설비 문제 태그 | `03_problem_tags_analysis.md` §2.5 | `charts/B5/CUSUM_MAIN_GAS_*` |
| 12 | 카테고리별 이상치 분포 | `03_problem_tags_analysis.md` §3 | `charts/overview/category_outlier_boxplot.png` |

### Part 4: 강종별 비교 (슬라이드 13-17)

| 슬라이드 | 제목 | 소스 파일 | 차트 |
|----------|------|-----------|------|
| 13 | 강종별 위험등급 분포 | `04_grade_comparison.md` §1 | `charts/overview/grade_risk_distribution.png` |
| 14 | 강종별 기법 문제 비율 | `04_grade_comparison.md` §2 | `charts/overview/method_coverage_comparison.png` |
| 15 | 강종×태그 히트맵 | `04_grade_comparison.md` §3 | `charts/overview/cross_grade_heatmap_iqr.png` |
| 16 | 공통 문제 vs 강종 특이 | `04_grade_comparison.md` §4 | - |
| 17 | 사이즈 영향 분석 | `04_grade_comparison.md` §5 | - |

### Part 5: 결론 및 권고 (슬라이드 18-22)

| 슬라이드 | 제목 | 소스 파일 | 차트 |
|----------|------|-----------|------|
| 18 | 핵심 발견 5가지 | `05_findings_and_actions.md` §1 | - |
| 19 | 조치 권고 (우선순위) | `05_findings_and_actions.md` §2 | - |
| 20 | 기법별 신뢰도 평가 | `05_findings_and_actions.md` §3 | - |
| 21 | 후속 분석 제안 | `05_findings_and_actions.md` §4 | - |
| 22 | Q&A | - | - |

---

## 차트 삽입 가이드

### 차트 경로

```
ppt_summary/charts/
├── overview/                                    ← 종합 차트 (6개, 신규 생성)
│   ├── method_comparison_heatmap.png            ← 기법×강종 이상치율 히트맵
│   ├── grade_risk_distribution.png              ← 강종별 IQR 위험등급 분포
│   ├── top10_problem_tags.png                   ← 다기법 교차 Top 10
│   ├── category_outlier_boxplot.png             ← 카테고리별 이상치율 박스플롯
│   ├── method_coverage_comparison.png           ← 기법별 문제 태그 비율
│   └── cross_grade_heatmap_iqr.png              ← 강종×태그 IQR 히트맵
├── B5/                                          ← B5 대표 차트 (83개)
├── D4/                                          ← D4 대표 차트 (84개)
├── D5/                                          ← D5 대표 차트 (87개)
└── N5/                                          ← N5 대표 차트 (88개)
```

### 권장 삽입 크기

| 차트 유형 | PPT 크기 | 비고 |
|-----------|---------|------|
| overview 차트 | 슬라이드 전체 (24cm × 13.5cm) | 16:9 비율로 생성됨 |
| 강종별 차트 | 슬라이드 60% (14cm × 10cm) | 우측 배치, 좌측에 텍스트 |
| 비교 차트 | 50% × 2 나란히 | 좌우 비교 레이아웃 |

### 파일 명명 규칙

- `IQR_{태그명}_{사이즈}_timeseries.png` — IQR 시계열 차트
- `CUSUM_{태그명}_combined.png` — CUSUM+EWMA 결합 차트
- `RollingZ_{태그명}.png` — Rolling Z-Score 차트

---

## 문서 파일 목록

| 파일 | 내용 | PPT 분량 |
|------|------|---------|
| `00_PPT_GUIDE.md` | 본 가이드 | - |
| `01_executive_summary.md` | 핵심 요약 | 2-3장 |
| `02_methodology.md` | 기법 소개 | 2장 |
| `03_problem_tags_analysis.md` | 문제 태그 집중 분석 | 6-8장 |
| `04_grade_comparison.md` | 강종별 비교 | 4-5장 |
| `05_findings_and_actions.md` | 발견 & 권고 | 3-4장 |

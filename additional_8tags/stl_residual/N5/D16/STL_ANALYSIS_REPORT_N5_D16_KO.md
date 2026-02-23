# 강종 [N5] 사이즈 [D16] STL 계절-추세 분해 분석 보고서

**분석 기간**: 2025-03-01 ~ 2025-08-31
**강종**: N5 | 사이즈: D16
**생성일시**: 2026-02-23 16:03:39

---

## 분석 개요

### 분석 방법론

**STL (Seasonal-Trend Decomposition using LOESS)**

시계열 데이터를 세 가지 성분으로 분해:
- **Trend (추세)**: 장기적인 변화 패턴
- **Seasonal (계절성)**: 주기적으로 반복되는 패턴
- **Residual (잔차)**: 추세와 계절성으로 설명되지 않는 변동

| 파라미터 | 값 | 설명 |
|----------|-----|------|
| seasonal | 25h | 계절 주기 |
| robust | True | 강건 추정 |

### 분석 결과 요약

| 구분 | 태그 수 | 비율 |
|------|---------|------|
| **총 분석 태그** | 23개 | 100% |

#### 잔차 이상치율 분포

| 구분 | 태그 수 | 비율 |
|------|---------|------|
| 🔴 높음 (≥15%) | 23개 | 100.0% |
| 🟠 중간 (5~15%) | 0개 | 0.0% |
| 🟢 낮음 (<5%) | 0개 | 0.0% |

#### 계절성 강도 분포

| 구분 | 태그 수 | 비율 |
|------|---------|------|
| 🔵 강함 (≥0.7) | 2개 | 8.7% |
| 중간 (0.4~0.7) | 1개 | 4.3% |
| 약함 (<0.4) | 20개 | 87.0% |

#### 전체 평균

| 지표 | 값 |
|------|-----|
| 평균 계절성 강도 | 0.163 |
| 평균 추세 강도 | 0.916 |

---

## 상위 문제 태그 (잔차 이상치율 기준)

| 순위 | 태그 | 카테고리 | 이상치율 | 계절성 강도 | 계절성 분류 |
|------|------|----------|----------|-------------|-------------|
| 1 | PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 47.49% | 0.958 | strong |
| 2 | PR6L2_ACT_SPD_MS | PR 상세 (토크+속도) | 46.19% | 0.673 | moderate |
| 3 | PINCHROLL_4_ACTUAL_SPEED | 핀치롤 | 45.96% | 0.178 | none |
| 4 | PINCHROLL_3_ACTUAL_SPEED | 핀치롤 | 44.56% | 0.381 | weak |
| 5 | PINCHROLL_3_ACTUAL_TORQUE | 핀치롤 | 44.47% | 0.126 | none |
| 6 | PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 44.44% | 0.990 | strong |
| 7 | PR7L1_ACT_TORQUE | PR 상세 (토크+속도) | 44.00% | 0.010 | none |
| 8 | PR7L2_ACT_TORQUE | PR 상세 (토크+속도) | 42.88% | 0.025 | none |
| 9 | PINCHROLL_2_REFERENCE_TORQUE | 핀치롤 | 42.59% | 0.028 | none |
| 10 | PR7L1_ACT_SPD_MS | PR 상세 (토크+속도) | 42.49% | 0.000 | none |
| 11 | PR8L1_ACT_SPD_MS | PR 상세 (토크+속도) | 42.30% | 0.150 | none |
| 12 | PINCHROLL_4_ACTUAL_TORQUE | 핀치롤 | 41.97% | 0.000 | none |
| 13 | PR9L1_ACT_TORQUE | PR 상세 (토크+속도) | 41.29% | 0.014 | none |
| 14 | PINCHROLL_4_REFERENCE_TORQUE | 핀치롤 | 40.31% | 0.000 | none |
| 15 | PINCHROLL_4_REFERENCE_SPEED | 핀치롤 | 40.18% | 0.038 | none |

---

## 강한 계절성 태그 목록

계절성 강도가 0.7 이상인 태그입니다. 이 태그들은 STL 분석이 특히 효과적입니다.

| 태그 | 카테고리 | 계절성 강도 | 잔차 이상치율 |
|------|----------|-------------|---------------|
| PR6L2_ACT_TORQUE | PR 상세 (토크+속도) | 0.990 | 44.44% |
| PR7L2_ACT_SPD_MS | PR 상세 (토크+속도) | 0.958 | 47.49% |

---

## 카테고리별 분석 결과

### 핀치롤 (08_Pinchroll)

- 분석 태그: 11개
- 평균 잔차 이상치율: 41.36%
- 평균 계절성 강도: 0.069

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| PINCHROLL_2_ACTUAL_SPEED | 38.07% | 0.000 | 0.947 |
| PINCHROLL_3_ACTUAL_SPEED | 44.56% | 0.381 | 0.761 |
| PINCHROLL_4_ACTUAL_SPEED | 45.96% | 0.178 | 0.911 |
| PINCHROLL_2_ACTUAL_TORQUE | 39.78% | 0.007 | 0.910 |
| PINCHROLL_3_ACTUAL_TORQUE | 44.47% | 0.126 | 0.846 |
| PINCHROLL_4_ACTUAL_TORQUE | 41.97% | 0.000 | 0.785 |
| PINCHROLL_2_REFERENCE_TORQUE | 42.59% | 0.028 | 0.989 |
| PINCHROLL_3_REFERENCE_TORQUE | 37.11% | 0.002 | 0.873 |
| PINCHROLL_4_REFERENCE_TORQUE | 40.31% | 0.000 | 0.861 |
| PINCHROLL_3_REFERENCE_SPEED | 40.00% | 0.000 | 0.790 |
| PINCHROLL_4_REFERENCE_SPEED | 40.18% | 0.038 | 0.984 |

#### STL 분해 차트

**PINCHROLL_4_ACTUAL_SPEED** (이상치율: 45.96%, 계절성: 0.178)

![PINCHROLL_4_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_4_ACTUAL_SPEED_stl_decomposition.png)

**PINCHROLL_3_ACTUAL_SPEED** (이상치율: 44.56%, 계절성: 0.381)

![PINCHROLL_3_ACTUAL_SPEED](08_Pinchroll/PINCHROLL_3_ACTUAL_SPEED_stl_decomposition.png)

**PINCHROLL_3_ACTUAL_TORQUE** (이상치율: 44.47%, 계절성: 0.126)

![PINCHROLL_3_ACTUAL_TORQUE](08_Pinchroll/PINCHROLL_3_ACTUAL_TORQUE_stl_decomposition.png)


### PR 상세 (토크+속도) (09_PR_Detailed)

- 분석 태그: 12개
- 평균 잔차 이상치율: 41.22%
- 평균 계절성 강도: 0.249

| 태그 | 이상치율 | 계절성 강도 | 추세 강도 |
|------|----------|-------------|-----------|
| PR6L1_ACT_TORQUE | 38.32% | 0.000 | 0.955 |
| PR6L2_ACT_TORQUE | 44.44% | 0.990 | 1.000 |
| PR7L1_ACT_TORQUE | 44.00% | 0.010 | 0.928 |
| PR7L2_ACT_TORQUE | 42.88% | 0.025 | 0.999 |
| PR8L1_ACT_TORQUE | 31.63% | 0.000 | 0.930 |
| PR9L1_ACT_TORQUE | 41.29% | 0.014 | 0.959 |
| PR6L1_ACT_SPD_MS | 36.24% | 0.000 | 0.907 |
| PR6L2_ACT_SPD_MS | 46.19% | 0.673 | 0.997 |
| PR7L1_ACT_SPD_MS | 42.49% | 0.000 | 0.781 |
| PR7L2_ACT_SPD_MS | 47.49% | 0.958 | 0.999 |
| PR8L1_ACT_SPD_MS | 42.30% | 0.150 | 0.977 |
| PR9L1_ACT_SPD_MS | 37.37% | 0.163 | 0.968 |

#### STL 분해 차트

**PR7L2_ACT_SPD_MS** (이상치율: 47.49%, 계절성: 0.958)

![PR7L2_ACT_SPD_MS](09_PR_Detailed/PR7L2_ACT_SPD_MS_stl_decomposition.png)

**PR6L2_ACT_SPD_MS** (이상치율: 46.19%, 계절성: 0.673)

![PR6L2_ACT_SPD_MS](09_PR_Detailed/PR6L2_ACT_SPD_MS_stl_decomposition.png)

**PR6L2_ACT_TORQUE** (이상치율: 44.44%, 계절성: 0.990)

![PR6L2_ACT_TORQUE](09_PR_Detailed/PR6L2_ACT_TORQUE_stl_decomposition.png)



---

## 해석 가이드

### STL 분해 해석

1. **추세 (Trend)**
   - 장기적인 상승/하락 패턴
   - 설비 노화, 계절적 변화 등 반영
   - 추세 강도 높을수록 장기 변화가 뚜렷함

2. **계절성 (Seasonal)**
   - 주기적으로 반복되는 패턴 (24시간 기준)
   - 계절성 강도 ≥ 0.7: 강한 주기적 패턴
   - 계절성이 강한 태그는 STL 분석이 효과적

3. **잔차 (Residual)**
   - 추세와 계절성으로 설명되지 않는 변동
   - **순수한 이상치**를 포함
   - 잔차 기반 IQR로 "진짜" 이상치 탐지

### 계절성 강도 분류

| 분류 | 강도 범위 | 해석 |
|------|----------|------|
| Strong | ≥ 0.7 | 명확한 주기적 패턴, STL 매우 효과적 |
| Moderate | 0.4 ~ 0.7 | 적당한 주기적 패턴, STL 효과적 |
| Weak | 0.2 ~ 0.4 | 약한 주기적 패턴 |
| None | < 0.2 | 주기적 패턴 거의 없음 |

### Standard IQR vs STL Residual IQR

| 방법 | 장점 | 단점 |
|------|------|------|
| Standard IQR | 간단, 빠름 | 계절성에 영향받음 |
| STL Residual IQR | 계절성 제거, 순수 이상치 | 계산 복잡, 데이터 필요 |

**권장**: 계절성 강도 ≥ 0.4인 태그에는 STL Residual IQR 사용

---

## 메타데이터

| 항목 | 값 |
|------|-----|
| 분석 스크립트 | steel_grade_stl_analysis.py |
| 분석 기간 | 2025-03-01 ~ 2025-08-31 |
| 강종 | N5 |
| 계절 주기 | 25시간 |
| 생성일시 | 2026-02-23 16:03:39 |
| 총 분석 태그 | 23개 |

---

*본 보고서는 자동 생성되었습니다.*

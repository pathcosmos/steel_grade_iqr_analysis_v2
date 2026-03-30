# REQ #3 분석 결과: 잠정 관리 기준 (대안 B - 실측값 기반)

분석일: 2026-03-30 21:44
데이터: IBA 2026.01~02 (84919행), 코일 결과 (4952건)

> **주의**: 설정값(Setpoint) 데이터 미확보로 대안 B(실측값 기반) 적용. 설정값 확보 시 Gap 정량화 추가 가능.

## 1. 잠정 관리 기준 (전체 데이터 기준)

| Tag | Normal Range (Q10~Q90) | UCL | LCL | Alarm Upper | Alarm Lower |
|-----|:-----:|:---:|:---:|:---:|:---:|
| INDIRECT_WATER_FOR_FURNACE_PRESSURE_CONTROL_DAMPER | 10.10 ~ 35.27 | 61.96 | -16.60 | 70.86 | -25.50 |
| MAIN_GAS_FLOW | -34.20 ~ 2155.61 | 4652.17 | -2530.75 | 5484.35 | -3362.94 |
| FURNACE_EXIT_DISCHARGE_BILLET_TEMPERATURE | 944.71 ~ 1120.98 | 1301.72 | 763.97 | 1361.97 | 703.73 |
| STAND_8_ACTUAL_TORQUE | 0.00 ~ 40.10 | 92.92 | -52.82 | 110.53 | -70.43 |
| STAND_14_ACTUAL_TORQUE | 0.00 ~ 43.14 | 102.90 | -59.76 | 122.82 | -79.68 |
| PINCHROLL_3_REFERENCE_TORQUE | 35.00 ~ 100.00 | 102.88 | 32.12 | 103.84 | 31.16 |

## 2. 산정 방법
- 정상 범위: [Q10, Q90] 구간
- 관리 한계 (UCL/LCL): Q90 + 1.5*IQR / Q10 - 1.5*IQR
- 경보 한계 (UAL/LAL): Q90 + 2.0*IQR / Q10 - 2.0*IQR

## 3. 한계
- 강종/사이즈/계절별 세분화 미실행 (IBA 원본에 강종 미포함)
- 설정값 Gap 정량화 불가 (설정값 미확보)
- 코일-IBA 매칭 후 불량/정상 분리 관리 기준 필요

## 4. 생성된 파일
- management_standards_overall.csv - 잠정 관리 기준표
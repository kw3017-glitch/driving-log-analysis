# 프로젝트 05: ADAS 개입 필요도 점수 모델

## 목적
주행 로그 데이터 기반으로  
ADAS(Advanced Driver Assistance System)가  
**언제·어느 수준으로 개입해야 하는지**를 점수로 판단합니다.

기존 주행 이벤트 분석 결과를 종합하여  
ADAS 개입 필요도를 하나의 수치(0~100)로 정량화합니다.

---

## 입력 데이터
- 주행 로그 CSV
  - time_sec
  - speed_kmh
  - accel_mps2

---

## 활용 지표 (기존 프로젝트 연계)
- 급가속 / 급제동 이벤트 수 (Project 02)
- 거리당 이벤트 빈도 (events per km) (Project 03)
- 급제동 비율 (Project 04)
- 속도 변동성 (표준편차)
- 공격적 주행 점수 (Aggressiveness Score, Project 04)

---

## ADAS 개입 필요도 점수 설계
여러 위험 지표를 가중 합산하여  
ADAS 개입 필요도 점수를 산출합니다.

- Aggressiveness Score
- 거리당 위험 이벤트 빈도
- 급제동 비율
- 속도 변동성

> 단일 이벤트가 아닌 **종합 위험도 기반 판단**으로  
> 오경보(False Positive)를 최소화하도록 설계

---

## 개입 레벨 정의
| 점수 범위 | ADAS 개입 수준 |
|---------|---------------|
| 0 – 30  | No Intervention |
| 31 – 55 | Monitoring Only |
| 56 – 75 | ADAS Alert Recommended |
| 76 – 100 | ADAS Active Intervention |

---

## 출력 결과
- ADAS Risk Score (0 ~ 100)
- Intervention Level
- 주요 위험 지표 요약

---

## 실무 활용 예
- ADAS 경고/제어 개입 로직 검증
- 위험 운전자 조기 식별
- 주행 데이터 기반 안전성 평가
- ADAS QA 및 알고리즘 튜닝 참고 지표

---

## 프로젝트 특징
- 기존 주행 분석 프로젝트(01~04) 결과 재사용
- 데이터 부족 시 과대 평가 방지 로직 포함
- ADAS 관점의 의사결정 구조 설계

---


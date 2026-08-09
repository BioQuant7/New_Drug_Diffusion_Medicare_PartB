# 새로 나온 약은 얼마나 빨리 쓰이게 될까

미국 Medicare Part B 데이터(2012–2024)로 신약 50개의 출시 후
환자 수 곡선을 그리고, 확산 속도를 가른 요인을 분석했습니다.

## 결론

**1. 편의성은 임계값 효과다**
절대 투여시간은 무관합니다. 같은 계열 안에서 최선 대비 2.5배를 넘으면
무너지고, 그 아래는 차이가 없습니다.
Gazyva는 4시간 투여인데 멀쩡하고, Cinqair는 30분인데 무너졌습니다.
차이는 더 편한 대안이 있느냐였습니다.

**2. 편의성이 비슷하면 후발이 이긴다**
Iluvien→Yutiq, Astagraf→Envarsus, Orbactiv→Kimyrsa, Kadcyla→Enhertu.
계열 내에서 먼저 나온 약이 반복적으로 밀렸습니다.
처음 세운 가설("선발이 시장을 가져간다")과 반대입니다.

## 데이터

- [Medicare Part B Spending by Drug](https://data.cms.gov/summary-statistics-on-use-and-payments/medicare-medicaid-spending-by-drug/medicare-part-b-spending-by-drug)
  — Historical Data zip, Manufacturer 파일
- openFDA API — 승인 연도 조회

받은 파일을 `data/` 폴더에 넣고 셀을 순서대로 실행하면 됩니다.
용량 문제로 데이터 파일은 저장소에 포함하지 않았습니다.

## 방법

환자 수 기준 확산 곡선 → 정점 대비 하락률 산출 →
같은 표적을 노리는 약끼리 묶어 계열 내 비교 →
투여 편의성을 계열 내 상대값으로 변환

통계는 평균·중앙값 비교와 산점도만 사용했습니다.
표본이 작아 회귀 대신 사례 비교로 진행했습니다.

## 한계

- Medicare Advantage 가입자 제외(전체의 35% 이상), 65세 이상 중심
- 병원 투여 주사제만. 먹는 약과 자가주사는 제외
- H1(새로움 가설)은 직접 검증하지 못하고 선발/후발 비교로 간접 확인
- PD-1/PD-L1 6개가 투여 방식이 같은데 70배 격차가 난 이유는 미해결

## 환경

Python 3.12 · pandas · matplotlib · requests
※ openFDA 조회 결과이므로 재실행 시점에 따라 매칭 수가 달라질 수 있습니다.
  본 결과는 2026-08-09 기준입니다.

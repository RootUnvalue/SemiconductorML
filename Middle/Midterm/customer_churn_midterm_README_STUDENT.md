# Problem 2 — Customer Churn: 데이터 설명

파일: `customer_churn_midterm.csv`

이 데이터는 수업 평가를 위해 생성한 가상의 고객 기록입니다. 실제 고객 기록이 아닙니다.
- 1,000개 Sample, 20개 Feature, Target `Churn`, 분할 표시 `DataSplit`
- `Churn`: 1 = 고객 이탈, 0 = 서비스 유지
- `DataSplit`: `TRAIN` = 800개, `TEST` = 200개. TEST 200개는 모든 학생이 동일하게 사용해야 합니다.
- `DataSplit`은 Feature가 아니며, Model의 Input에 포함해서는 안 됩니다.
- Feature의 수와 구성은 학생이 결정합니다. 선정/제외의 근거를 보고서에 제시해야 합니다.
- 800개의 TRAIN 데이터를 모두 최종 학습에 사용할 필요는 없습니다. 단, TEST는 최종 평가에만 사용하십시오.
- 모든 Feature는 숫자로 인코딩되어 있습니다. 일부 정수 코드는 실제 양적 의미를 갖지 않을 수 있습니다.

## Feature 설명

| Feature | 의미 |
|---|---|
| `TenureMonths` | 고객이 서비스를 이용한 기간 (개월) |
| `CustomerAge` | 고객 나이 (세) |
| `SupportTickets6M` | 최근 6개월 고객지원 요청 건수 |
| `LatePayments12M` | 최근 12개월 납부 지연 횟수 |
| `DroppedCalls30D` | 최근 30일 통화 중 연결 끊김 횟수 |
| `SatisfactionScore` | 고객 만족도 (1~10점) |
| `DiscountPct` | 현재 요금 할인율 (%) |
| `ContractMonthsRemaining` | 계약 만료까지 남은 기간 (개월) |
| `CompetitorPriceAdvantagePct` | 경쟁사 가격 우위 (%); 양수이면 경쟁사 요금이 상대적으로 저렴함 |
| `MonthlyFeeUSD` | 월 서비스 이용료 (USD) |
| `EstimatedAnnualFeeUSD` | 추정 연간 서비스 이용료 (USD) |
| `AvgMonthlyDataGB` | 평균 월 데이터 사용량 (GB) |
| `QuarterlyDataGB` | 분기 데이터 사용량 (GB) |
| `WeekendUsagePct` | 전체 이용량 중 주말 사용 비율 (%) |
| `DeviceAgeMonths` | 사용 중인 단말기 보유 기간 (개월) |
| `StoreVisits12M` | 최근 12개월 오프라인 매장 방문 횟수 |
| `LuckyNumber` | 고객이 선택한 행운의 숫자 |
| `FavoriteColorCode` | 고객 선호색의 숫자 코드 |
| `AccountSerialCode` | 고객 계정의 임의 일련번호 |
| `SurveyCoinFlip` | 가입 설문에서 선택한 동전 앞/뒷면 코드 (0/1) |

## 데이터 미리보기 (Google Colab)

```python
import pandas as pd
df = pd.read_csv('customer_churn_midterm.csv')
print(df.shape)
display(df.head())
print(df['DataSplit'].value_counts())
```

참고: 일부 Feature 간에는 중복된 정보가 있을 수 있습니다. 어떤 Feature가 분석에 유용한지는 직접 판단하십시오.

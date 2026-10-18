# MLB Player-Season Data — 학생용 데이터 설명서

## 데이터 개요

- 파일명: `MLB_2000_2025_PlayerSeasons_Edu.csv`
- 기간: 2000–2025년 MLB 정규시즌 기록
- 기록 단위: 한 행은 한 선수의 한 시즌을 나타냅니다. 한 시즌에 여러 팀에서 뛴 선수의 기록은 시즌 단위로 합쳐져 있습니다.
- 포함 대상: 타자, 투수, 투타 겸업 선수, FA 및 비FA 선수
- 자료의 성격: 선수의 시즌별 경기 통계는 실제 MLB 기록을 기반으로 합니다. 그러나 FA 계약 여부와 계약 시점은 교육 목적으로 생성한 모의 정보이며, 실제 계약 이력을 나타내지 않습니다.

이 데이터는 Machine Learning 중간시험의 분석 실습을 위한 자료입니다. 모의 FA 계약 정보에 대한 분석 결과를 실제 MLB 선수의 FA 계약 효과에 대한 사실로 해석해서는 안 됩니다.

## 선수·시즌 기본정보

| Column | 설명 | 단위·값 |
|---|---|---|
| `playerID` | 선수를 식별하는 고유 ID | 문자 |
| `player_name` | 선수 이름 | 문자 |
| `yearID` | 해당 기록의 시즌 연도 | 년 |
| `age_approx` | 시즌 연도에서 출생연도를 뺀 대략적인 나이 | 세 (근사값) |
| `teams` | 해당 시즌 소속 팀 코드 | 여러 팀은 `\|`로 구분 |
| `leagues` | 해당 시즌 리그 코드 | AL, NL 등; 여러 리그는 `\|`로 구분 |
| `season_role` | 해당 시즌 기록을 바탕으로 구분한 선수 역할 | `Batter`, `Pitcher`, `Two-way` |
| `G_all` | 해당 시즌의 전체 출전 경기 수 | 경기 |
| `G_pitcher` | 투수로 출전한 경기 수 | 경기 |
| `birthYear` | 출생연도 | 년 |
| `bats` | 타격 방향 | R: 우타, L: 좌타, S: 양타 |
| `throws` | 투구 방향 | R: 우투, L: 좌투 |

`age_approx`는 출생일을 기준으로 계산한 정확한 시즌 나이가 아닙니다. `season_role`은 기록으로부터 구분한 교육용 분류이며, 선수의 공식 포지션 명칭과 반드시 일치하지는 않습니다.

## 모의 FA 계약 정보

아래 `FA_`로 시작하는 항목은 모두 실제 계약정보가 아닌 모의 데이터입니다.

| Column | 설명 | 단위·값 |
|---|---|---|
| `FA_Player_Simulated` | 이 선수에게 모의 FA 계약 이벤트가 배정되었는지 여부 | 1: 배정, 0: 미배정 |
| `FA_ContractThisYear_Simulated` | 해당 시즌이 모의 FA 계약의 첫 시즌인지 여부 | 1: 해당 시즌, 0: 그 외 |
| `FA_ContractYear` | 모의 FA 계약의 첫 시즌 연도 | 년; 해당하지 않으면 빈칸 |
| `FA_RelativeYear` | 모의 FA 계약 첫 시즌을 기준으로 한 상대 연도 | 0: 첫 시즌, -1: 직전 시즌, +1: 다음 시즌 |
| `FA_EventType` | 모의 FA 계약 이벤트 표시 | `SIMULATED` 또는 빈칸 |

모의 FA 계약이 배정된 선수는 여러 시즌의 행에서 `FA_Player_Simulated=1`로 나타날 수 있습니다. `FA_ContractThisYear_Simulated=1`은 계약 첫 시즌에 해당하는 한 행을 가리킵니다.

## 타격 기록: `bat_` 접두사

| Column | 설명 | 단위 |
|---|---|---|
| `bat_G` | 타자로 기록된 출전 경기 수 | 경기 |
| `bat_AB` | 타수 (At Bats) | 회 |
| `bat_R` | 득점 (Runs) | 점 |
| `bat_H` | 안타 (Hits) | 개 |
| `bat_2B` | 2루타 (Doubles) | 개 |
| `bat_3B` | 3루타 (Triples) | 개 |
| `bat_HR` | 홈런 (Home Runs) | 개 |
| `bat_RBI` | 타점 (Runs Batted In) | 점 |
| `bat_SB` | 도루 성공 (Stolen Bases) | 회 |
| `bat_CS` | 도루 실패 (Caught Stealing) | 회 |
| `bat_BB` | 볼넷 (Bases on Balls) | 회 |
| `bat_SO` | 삼진 (Strikeouts) | 회 |
| `bat_HBP` | 몸에 맞는 공 (Hit By Pitch) | 회 |
| `bat_SF` | 희생플라이 (Sacrifice Flies) | 회 |
| `bat_AVG` | 타율 (Batting Average): 안타 수를 타수로 나눈 값 | 비율 (예: 0.275) |
| `bat_OBP` | 출루율 (On-Base Percentage): 타석에서 출루한 비율을 나타내는 지표 | 비율 |
| `bat_SLG` | 장타율 (Slugging Percentage): 타수당 총 루타 수 | 비율 형태의 수치 |
| `bat_OPS` | 출루율과 장타율의 합 (OBP + SLG) | 비율 형태의 수치 |

## 투구 기록: `pit_` 접두사

| Column | 설명 | 단위 |
|---|---|---|
| `pit_W` | 승리 (Wins) | 승 |
| `pit_L` | 패배 (Losses) | 패 |
| `pit_G` | 투수 출전 경기 수 | 경기 |
| `pit_GS` | 선발 등판 수 (Games Started) | 경기 |
| `pit_CG` | 완투 (Complete Games) | 경기 |
| `pit_SHO` | 완봉 (Shutouts) | 경기 |
| `pit_SV` | 세이브 (Saves) | 개 |
| `pit_IPouts` | 투수가 기록한 아웃 수 | 아웃 (Outs) |
| `pit_IP` | 투구이닝: `pit_IPouts`를 3으로 나눈 값 | 이닝 (십진수) |
| `pit_H` | 피안타 (Hits Allowed) | 개 |
| `pit_ER` | 자책점 (Earned Runs) | 점 |
| `pit_HR` | 피홈런 (Home Runs Allowed) | 개 |
| `pit_BB` | 허용 볼넷 (Walks Allowed) | 회 |
| `pit_SO` | 탈삼진 (Strikeouts) | 개 |
| `pit_HBP` | 허용 몸에 맞는 공 (Hit Batters) | 회 |
| `pit_BFP` | 상대 타자 수 (Batters Faced) | 명·타석 수 |
| `pit_ERA` | 평균자책점 (Earned Run Average): 9이닝당 자책점 | 점/9이닝 |
| `pit_WHIP` | 이닝당 피안타와 볼넷의 합 (Walks plus Hits per Inning Pitched) | 건/이닝 |

주의: `pit_IP`는 십진수 이닝입니다. 예를 들어 10개의 아웃은 `pit_IP = 3.333333`으로 표현됩니다. 야구 중계에서 사용하는 `3.1이닝` 표기와 혼동하지 마십시오.

## 빈칸과 숫자의 의미

- 빈칸은 자료의 원래 기록이 없거나, 해당 선수·시즌에 적용되지 않거나, 계산할 수 없거나, 교육 목적으로 일부 값을 누락시킨 경우 등에 나타날 수 있습니다.
- 빈칸은 숫자 0과 같은 의미가 아닙니다.
- 일부 선수의 시즌 기록에는 교육 목적으로 부분적인 결측치가 포함되어 있습니다.
- FA 계약 관련 값은 모의 정보이며, 선수의 실제 기록을 계약 전후에 맞춰 인위적으로 올리거나 낮춘 것이 아닙니다.

## 자료 출처와 사용 범위

- 실제 선수·시즌 기록 기반: SABR/Sean Lahman, Lahman Baseball Database (2025 release), https://sabr.org/lahman-database/
- 원본 자료 라이선스: Creative Commons Attribution-ShareAlike 3.0 (CC BY-SA 3.0), https://creativecommons.org/licenses/by-sa/3.0/
- 학생에게 제공된 통합 CSV는 교육용으로 재구성된 자료로, 모의 FA 계약 정보와 일부 의도적 결측치를 포함합니다.

본 설명서는 Column의 의미를 안내하기 위한 것입니다. 보고서에서 어떤 기록과 비교 대상을 사용할지는 학생이 스스로 판단해야 합니다.

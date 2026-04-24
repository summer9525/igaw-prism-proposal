# PRISM 리포트 자동 생성을 위한 데이터 테이블 명세

> 데이터팀에서 아래 테이블에 데이터를 채워주시면, 리포트가 자동 생성됩니다.
> 각 테이블은 리포트의 특정 파트에 매핑됩니다.
> 업종/기업이 바뀌어도 동일한 테이블 구조를 사용합니다.

---

## 📌 공통 파라미터 (리포트 생성 시 입력)

| 파라미터 | 설명 | 예시 |
|---------|------|------|
| `report_company` | 분석 대상 기업 | SSG.COM |
| `report_industry` | 업종 | 이커머스 |
| `report_quarter` | 분석 기간 | 2026 Q1 |
| `competitors` | 경쟁사 리스트 (최대 5개) | 쿠팡, 컬리, 네이버쇼핑 |

---

## 테이블 1. 헤더 KPI (→ 리포트 상단 4개 KPI)

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `company` | string | 분석 대상 기업 | SSG.COM |
| `mau` | integer | 월간 활성 사용자 수 | 8920000 |
| `mau_change_pct` | float | 전분기 대비 MAU 변화율(%) | -3.2 |
| `wallet_share_vs_top_competitor` | float | 1위 경쟁사 대비 지갑점유율(%) | 18.4 |
| `wallet_share_description` | string | 지갑점유율 설명 | 쿠팡 고객 중 SSG 결제 비중 |
| `churn_risk_vip_count` | integer | 이탈 위험 VIP 수 | 127000 |
| `churn_risk_criteria` | string | 이탈 위험 기준 | 최근 30일 경쟁사 사용 급증 |
| `conquest_target_count` | integer | 탈취 가능 타겟 수 | 342000 |
| `conquest_target_description` | string | 탈취 타겟 설명 | 경쟁사 헤비유저 중 전환 잠재력 상위 |

---

## 테이블 2. 업종 벤치마크 (→ Part 1)

### 2-1. 상위 10% 유저 벤치마크

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `industry` | string | 업종 | 이커머스 |
| `top10_monthly_usage_min` | integer | 상위 10% 월 사용 시간(분) | 128 |
| `top10_monthly_payment` | integer | 상위 10% 월 결제액(만원) | 324000 |
| `top10_conversion_rate` | float | 상위 10% 결제 전환율(%) | 34.7 |
| `top10_30d_revisit_rate` | float | 상위 10% 30일 재방문율(%) | 72.6 |

### 2-2. 경쟁사 MAU 비교

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `app_name` | string | 앱 이름 | 쿠팡 |
| `mau` | integer | MAU | 31420000 |
| `mau_change_pct` | float | 전분기 대비 변화율(%) | +1.8 |
| `is_target_company` | boolean | 분석 대상 기업 여부 | false |

### 2-3. 카테고리별 결제 점유율

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `category` | string | 카테고리명 | 신선식품 |
| `target_company_share` | float | 자사 점유율(%) | 28.3 |
| `competitor_1_name` | string | 경쟁사1 이름 | 쿠팡 |
| `competitor_1_share` | float | 경쟁사1 점유율(%) | 31.7 |
| `competitor_2_name` | string | 경쟁사2 이름 | 컬리 |
| `competitor_2_share` | float | 경쟁사2 점유율(%) | 32.4 |
| `competitor_3_name` | string | 경쟁사3 이름 | 네이버 |
| `competitor_3_share` | float | 경쟁사3 점유율(%) | 7.6 |
| `risk_level` | string | 위험도 (높음/방어/강점) | 높음 |

---

## 테이블 3. 오디언스 세그먼트 (→ Part 2, 3)

### 3-1. 서브 세그먼트 정의

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `segment_id` | string | 세그먼트 ID | A |
| `segment_name` | string | 세그먼트 이름 | 판교 IT 맞벌이 |
| `segment_size` | integer | 규모(명) | 84000 |
| `f_tag_conditions` | string | F-Tag 조건 | GPS(판교) + IT직종 + 연봉 8천만↑ |
| `strategy_type` | string | 전략 유형 (공격/방어/확장) | 공격 |
| `strategy_label` | string | 전략 라벨 | 반드시 공략 대상 |

### 3-2. 세그먼트별 경쟁사 사용 현황

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `segment_id` | string | 세그먼트 ID | A |
| `app_name` | string | 앱 이름 | 쿠팡 |
| `monthly_payment` | integer | 월 결제액(원) | 287000 |
| `payment_change_pct` | float | 전분기 대비 변화율(%) | +14 |
| `monthly_usage_min` | integer | 월 사용 시간(분) | — |
| `weekly_visit` | float | 주간 방문 횟수 | — |
| `usage_change_pct` | float | 사용 변화율(%) | — |

### 3-3. 세그먼트별 자사 사용 현황

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `segment_id` | string | 세그먼트 ID | A |
| `monthly_payment` | integer | 자사 월 결제액(원) | 31000 |
| `payment_change_pct` | float | 전분기 대비 변화율(%) | -22 |
| `weekly_visit` | float | 주간 앱 사용 횟수 | 1.2 |
| `visit_change_pct` | float | 사용 변화율(%) | -40 |
| `category_share_1` | string | 주요 카테고리1 점유율 | 프리미엄 가전: 42.3% |
| `category_share_2` | string | 주요 카테고리2 점유율 | 와인/주류: 28.1% |
| `offline_link_rate` | float | 오프라인 연계율(%) | 67.4 |

---

## 테이블 4. 이탈 경로 추적 (→ Part 4)

### 4-1. 이탈 규모 요약

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `total_churn_users` | integer | 전체 이탈 징후 유저 수 | 473000 |
| `churn_pct_of_mau` | float | MAU 대비 비율(%) | 5.3 |
| `destination_app` | string | 이동 경쟁사 | 쿠팡 |
| `destination_count` | integer | 이동 유저 수 | 284000 |
| `destination_pct` | float | 이동 비율(%) | 60.0 |

### 4-2. 이탈 시점 패턴

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `time_slot` | string | 시간대 | 19~21시 |
| `time_label` | string | 시간대 라벨 | 퇴근 후 |
| `churn_pct` | float | 해당 시간대 이탈 비율(%) | 38.7 |
| `is_peak` | boolean | 피크 시간대 여부 | true |

### 4-3. 카테고리별 이탈 현황

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `category` | string | 이탈 카테고리 | 생활용품 |
| `destination_app` | string | 이동 경쟁사 | 쿠팡 |
| `churn_rate` | float | 이탈률(%) | -34.2 |
| `churn_reason` | string | 이탈 사유 | 로켓배송 당일/익일 배송 + 가격 경쟁력 |

---

## 테이블 5. 지갑 점유율 (→ Part 5)

### 5-1. 소득 구간별 지갑 점유율

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `income_bracket` | string | 소득 구간 | 연봉 1억 이상 |
| `target_user_count` | integer | 자사 고객 수 | 142000 |
| `target_monthly_payment` | integer | 자사 월 결제액(원) | 84000 |
| `competitor_monthly_payment` | integer | 1위 경쟁사 월 결제액(원) | 321000 |
| `wallet_share` | float | 자사 지갑점유율(%) | 20.7 |
| `gap` | integer | 결제액 Gap(원) | -237000 |

### 5-2. 지역별 점유율

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `region` | string | 지역명 | 판교/분당 |
| `worker_count` | integer | 직장인 규모 | 421000 |
| `target_share` | float | 자사 점유율(%) | 8.2 |
| `top_competitor_share` | float | 1위 경쟁사 점유율(%) | 48.7 |
| `target_rank` | integer | 자사 순위 | 4 |

---

## 테이블 6. 전략 제안 (→ Part 6)

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `strategy_id` | integer | 전략 번호 | 1 |
| `strategy_name` | string | 전략명 | 쿠팡 프리미엄 불만족군 탈취 |
| `strategy_type` | string | 전략 유형 | Conquesting |
| `timeline` | string | 실행 기간 | 단기 2주 |
| `target_count` | integer | 타겟 수(명) | 184000 |
| `target_conditions` | string[] | 타겟 조건 리스트 | ["쿠팡 월 결제 15만↑", "강남/서초/송파/분당 거주"] |
| `action_plans` | string[] | 실행 방안 리스트 | ["DSP 타겟 광고 19~21시", "프리미엄 15% 할인"] |
| `expected_conversion_rate` | float | 예상 전환율(%) | 4.2 |
| `expected_new_users` | integer | 예상 신규 확보(명) | 7728 |
| `expected_monthly_revenue` | integer | 예상 월 매출 증분(원) | 1160000000 |

---

## 테이블 7. VIP 이탈 방지 (→ Part 7)

### 7-1. 이탈 징후 기준

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `criteria_id` | integer | 기준 번호 | 1 |
| `criteria_description` | string | 기준 설명 | 최근 30일 앱 사용 시간 40%↑ 감소 |

### 7-2. VIP 현황

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `churn_risk_vip_count` | integer | 이탈 위험 VIP 수 | 127000 |
| `avg_monthly_payment` | integer | 월 평균 결제액(원) | 193000 |
| `total_monthly_loss` | integer | 전원 이탈 시 월 손실(원) | 24460000000 |
| `annual_loss` | integer | 연간 손실(원) | 293500000000 |
| `winback_rate` | float | Win-back 예상 회수율(%) | 30 |
| `monthly_defense` | integer | 월 방어 매출(원) | 7340000000 |

### 7-3. Win-back 시나리오

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `step_day` | string | 실행 시점 | D+1 |
| `action_type` | string | 액션 유형 | 개인화 푸시 |
| `action_description` | string | 액션 상세 | 자주 찾던 카테고리 신상품 알림 |

---

## 테이블 8. P-Tag 예측 오디언스 (→ Part 6-2)

### 8-1. 이탈 예측 오디언스

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `prediction_type` | string | 예측 유형 | 이탈 예측 |
| `probability_threshold` | float | 확률 임계값(%) | 70 |
| `audience_count` | integer | 식별 오디언스 수 | 184000 |
| `competitor_app` | string | 경쟁 앱 | 쿠팡 |
| `competitor_usage_rate` | float | 경쟁 앱 사용률(%) | 92.4 |
| `competitor_monthly_usage_min` | integer | 경쟁 앱 월 사용 시간(분) | 48 |
| `competitor_usage_trend` | string | 추세 (급증/증가/유지/감소) | 급증 |
| `competitor_monthly_payment` | integer | 경쟁 앱 월 결제액(원) | 248000 |
| `competitor_top_category` | string | 경쟁 앱 주요 카테고리 | 생활용품, 식품 |
| `demo_age_range` | string | 주요 연령대 | 30~44세 |
| `demo_gender_ratio` | string | 성별 비율 | 여성 68% |
| `demo_region` | string | 주요 거주지 | 판교·분당 |
| `demo_income_bracket` | string | 소득 구간 | 7천~1억 |

### 8-2. 구매 예측 오디언스

| 컬럼명 | 타입 | 설명 | 예시 |
|--------|------|------|------|
| `prediction_type` | string | 예측 유형 | 구매 예측 |
| `probability_threshold` | float | 확률 임계값(%) | 60 |
| `audience_count` | integer | 식별 오디언스 수 | 228000 |
| `predicted_category` | string | 예측 구매 카테고리 | 프리미엄 가전 |
| `purchase_probability` | float | 구매 확률(%) | 72.4 |
| `expected_avg_price` | integer | 예상 객단가(원) | 480000 |
| `competitive_position` | string | 경쟁 포지션 | SSG 우위 |
| `demo_age_range` | string | 주요 연령대 | 35~54세 |
| `demo_gender_ratio` | string | 성별 비율 | 여성 54% |
| `demo_region` | string | 주요 거주지 | 강남·서초 |
| `demo_income_bracket` | string | 소득 구간 | 1억 이상 |

---

## 📋 테이블 요약

| # | 테이블명 | 리포트 파트 | 행 수 기준 |
|---|---------|-----------|-----------|
| 1 | 헤더 KPI | 상단 | 1행 (기업당) |
| 2-1 | 상위 10% 벤치마크 | Part 1 | 1행 (업종당) |
| 2-2 | 경쟁사 MAU | Part 1 | 경쟁사 수 + 1 |
| 2-3 | 카테고리별 점유율 | Part 1 | 카테고리 수 |
| 3-1 | 세그먼트 정의 | Part 2 | 세그먼트 수 (3~5개) |
| 3-2 | 세그먼트별 경쟁사 사용 | Part 2, 3 | 세그먼트 × 경쟁사 |
| 3-3 | 세그먼트별 자사 사용 | Part 2, 3 | 세그먼트 수 |
| 4-1 | 이탈 규모 | Part 4 | 경쟁사 수 + 1 |
| 4-2 | 이탈 시점 | Part 4 | 시간대 수 (4~6개) |
| 4-3 | 카테고리별 이탈 | Part 4 | 카테고리 수 |
| 5-1 | 소득별 지갑점유율 | Part 5 | 소득 구간 수 |
| 5-2 | 지역별 점유율 | Part 5 | 지역 수 |
| 6 | 전략 제안 | Part 6 | 전략 수 (3개) |
| 7-1 | 이탈 징후 기준 | Part 7 | 기준 수 (4~5개) |
| 7-2 | VIP 현황 | Part 7 | 1행 |
| 7-3 | Win-back 시나리오 | Part 7 | 단계 수 (4개) |
| 8-1 | 이탈 예측 오디언스 | Part 6-2 | 경쟁사 수 |
| 8-2 | 구매 예측 오디언스 | Part 6-2 | 카테고리 수 |

---

## 🔄 자동 생성 흐름

```
데이터팀이 테이블 채움
    ↓
PRISM 엔진이 테이블 읽음
    ↓
템플릿에 데이터 주입
    ↓
LLM이 해석 텍스트 생성 (Executive Summary, callout 인사이트)
    ↓
HTML 리포트 자동 출력
```

> **참고:** Executive Summary, callout 내 해석 텍스트, 전략 제안 텍스트는 위 테이블 데이터를 기반으로 LLM이 자동 생성합니다. 데이터팀은 숫자만 채워주시면 됩니다.

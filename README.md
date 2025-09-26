## Task 1 — Data Preparation

Goal: Create a summary table to evaluate marketing campaign performance

Output: `data/marketing_summary_by_date_channel_campaign.csv`

Preview:

| date       | media_source       | campaign         | installs | revenue | costs   | impressions | clicks |
|------------|--------------------|------------------|----------|----------|------------|--------------|-----------|
| 2024-03-01 | tiktokglobal_int   | tt_campaign_1     | 254 | 0.00 | 373.68 | 55620 | 2201 |
| 2024-03-01 | tiktokglobal_int   | tt_campaign_4     | 93  | 0.00 | 130.91 | 27650 | 675 |
| 2024-03-02 | tiktokglobal_int   | tt_campaign_1     | 218 | 11.82 | 370.28 | 85610 | 1470 |

---

## Task 2 — TikTok Campaign Analysis

Goal: Identify which campaigns on the tiktokglobal_int channel are effective based on the criterion ROAS_7 > 0.18

Output: `data/tiktok campaign eval.csv`

Preview:

| campaign       | costs       | total_revenue_7 | roas_7 | status          |
|----------------|--------------|----------------------|----------|-------------------|
| tt_campaign_4  | 892.36        | 400.75                  | 0.4491  | эффективная     |
| tt_campaign_3  | 4893.33       | 1316.01                 | 0.2689  | эффективная     |
| tt_campaign_1  | 9331.25       | 2191.31                 | 0.2348  | эффективная     |
| tt_campaign_2  | 2879.35       | 440.45                   | 0.1530  | неэффективная  |

---

## Task 3 — Attribution Validation

Goal: Check the correctness of user attribution for the googleadwords_int channel.

Results:
 - Total users: 29,767
 - With attribution: 20,711
 - Without attribution: 9,056 (30.42%)
 - With googleadwords_int: 1,457 (7.03% of attributed users)

Conclusions:
 - 30% of users lack attribution, which may indicate an issue in install tracking or attribution setup.
 - The googleadwords_int share is only 7%, which seems unusually low.
 - Potential data loss or incorrect processing for googleadwords_int users — further investigation recommended.

---

## Tech Stack:
 - Python, pandas
 - SQLite (sqlite3)
 - Jupyter Notebook


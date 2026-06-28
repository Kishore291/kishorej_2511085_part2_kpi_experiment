# Part 2: KPI Framework & A/B Experiment Analysis

## 1. Business Context
This repository contains the completion of Part 2 of the Business Analytics Capstone Project. The objective was to analyze the results of a 30-day A/B test for a new marketing campaign (Treatment) against the existing baseline (Control). The goal was to determine if the new campaign successfully drives business growth without compromising operational stability or revenue quality.

## 2. Dataset Description
* **File:** `experiment_data` (Excel)
* **Scope:** 30-day tracking window.
* **Volume:** 1,400 total users (690 in the Control group, 710 in the Treatment group).
* **Data Points:** User acquisition behavior (landing page visits, trial starts, onboarding completion), financial outcomes (conversion to paid, 30-day revenue), and satisfaction metrics (support tickets, refund requests).

## 3. North Star Metric Selected
**Paid Conversion Rate**
This was chosen as the North Star metric because it represents actual business value and user commitment, moving beyond top-of-funnel vanity metrics (like page visits) to measure true revenue-generating actions.

## 4. KPI Tree Summary
* **Leading Indicators:** Landing Page Visit Rate, Trial Start Rate, Onboarding Completion Rate.
* **Primary Metric (North Star):** Paid Conversion Rate.
* **Guardrail Metrics:** Support Ticket Rate, Average Revenue per Converted User, Average Days to Convert, Refund Rate.

## 5. Experiment Analysis Approach
The data was analyzed using summary statistics to compare the Control and Treatment groups across all KPI tree metrics. Relative percentage differences were calculated to determine the initial business impact before applying rigorous statistical testing.

## 6. Hypothesis Test Summary
* **Test Used:** Two-Proportion Z-Test (Two-Tailed, alpha = 0.05).
* **Result:** The Treatment group showed a 121% relative lift in the Paid Conversion Rate (from 3.19% to 7.04%). 
* **P-Value:** 0.0011
* **Conclusion:** The Null Hypothesis was successfully rejected. The massive increase in conversions is statistically significant and not due to random chance.

## 7. Guardrail Metrics Considered
* **Support Ticket Rate:** Spiked by 68% (High Operational Risk).
* **Average Revenue per Converted User:** Dropped by 53% (High Financial Risk).
* **Average Days to Convert:** Decreased by 28% (Positive outcome; faster sales cycle).
* **Refund Rate:** Remained stable at 0% (No immediate satisfaction risk).

## 8. Final Recommendation
**Decision: DO NOT LAUNCH (Iterate & Continue Testing).**
Despite the statistically significant 121% lift in conversion rate, the new campaign introduces unacceptable operational and financial risks. The 53% drop in revenue per converted user indicates the campaign is cannibalizing high-tier sales, and the 68% spike in support tickets threatens to overwhelm customer service operations. 

## 9. Assumptions and Limitations
* **Assumptions:** It is assumed that the 30-day window captures the complete conversion cycle for the majority of users.
* **Limitations:** We lack qualitative data detailing *why* the support tickets spiked. Furthermore, the 30-day timeframe prevents us from analyzing long-term retention or lifetime value (LTV) of the users acquired through the Treatment campaign.

## 10. Screenshots Included
Visual proof of the analysis can be found in the `screenshots/` directory:
* `experiment_summary.png`: Summary table of all calculated metrics and relative differences.
* `hypothesis_test_output.png`: Evidence of the Z-test and P-value calculation.

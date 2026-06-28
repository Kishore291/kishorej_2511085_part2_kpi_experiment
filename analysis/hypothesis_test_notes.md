# Hypothesis Test Notes: Part 2 A/B Experiment

## 1. Metric Being Tested
**Paid Conversion Rate** (The percentage of users who successfully transitioned from a free/trial state to a paid subscription).

## 2. Reason for Choosing this Metric
Paid Conversion Rate was selected as the North Star Metric because it most directly aligns with the core business objective: increasing revenue. While landing page visits or trial starts indicate top-of-funnel interest, only paid conversions validate whether the new Treatment campaign effectively drives actual business value and user commitment.

## 3. Hypotheses
* **Null Hypothesis ($H_0$):** The new campaign (Treatment) has no effect on the paid conversion rate. The conversion rate of the Treatment group is equal to the conversion rate of the Control group ($P_{treatment} = P_{control}$).
* **Alternate Hypothesis ($H_A$):** The new campaign (Treatment) significantly changes the paid conversion rate. The conversion rate of the Treatment group is different from the Control group ($P_{treatment} \neq P_{control}$).

## 4. Test Type (One-Tailed vs. Two-Tailed)
**Two-Tailed Test.** *Reasoning:* While the business goal is to *increase* conversions, using a two-tailed test is the gold standard for business A/B testing. It rigorously tests for any statistically significant difference in either direction. This is crucial for risk management, as it ensures we also accurately detect if the new campaign inadvertently harms the conversion rate compared to the control.

## 5. Significance Level Used
**$\alpha = 0.05$ (5%)**
*Reasoning:* A 5% significance level provides a strong balance between the risk of a false positive (launching a campaign that doesn't actually work) and a false negative (missing out on a winning campaign). We require 95% confidence that the observed 121% lift did not occur by random chance.

## 6. Interpretation Logic & Business Decision
* **If p-value < 0.05:** We reject the Null Hypothesis. We conclude that the Treatment campaign had a statistically significant impact on paid conversions. **Business Decision:** Proceed with launching the campaign to 100% of the user base (provided guardrail metrics like Support Tickets and Refunds remain within acceptable risk thresholds).

---

## 7. A/B Test Analysis Results

### Summary of Test Inputs
* **Metric:** Paid Conversion Rate
* **Test Type:** Two-Proportion Z-Test (Two-Tailed)
* **Control Group:** $n_c = 690$ users | Conversions: 22 | Rate ($p_c$) = 3.19%
* **Treatment Group:** $n_t = 710$ users | Conversions: 50 | Rate ($p_t$) = 7.04%
* **Pooled Proportion ($p$):** 5.14%

### Test Output & Calculations
To determine statistical significance, we calculate the standard error and the Z-statistic using the following parameters:
* **Standard Error (SE):** Calculated as $\sqrt{p(1-p)(\frac{1}{n_c} + \frac{1}{n_t})} \approx 0.0118$
* **Z-Statistic (Z):** Calculated as $\frac{p_t - p_c}{SE} \approx 3.26$

### P-Value & Evidence
* **P-Value:** **0.0011** (Calculated from $Z = 3.26$)
* **Significance Level ($\alpha$):** 0.05

### Decision Rule
* **Rule:** If the P-value is less than the significance level ($\alpha = 0.05$), we reject the Null Hypothesis ($H_0$).
* **Outcome:** Since $0.0011 < 0.05$, we successfully reject the Null Hypothesis.

### Business Interpretation
The results are statistically significant. The treatment campaign generated an absolute lift of 3.85% and a relative lift of 121% in paid conversions compared to the control group. Because the p-value ($0.0011$) is well below our 5% threshold, we can be over 99.8% confident that this massive improvement is a direct result of the new campaign and not due to random chance.

Mathematically, the primary objective of the experiment was a resounding success. However, before proceeding with a 100% rollout, we must contextualize these primary gains against the negative impact observed in our guardrail metrics (specifically, the 68% relative increase in support tickets and the 53% drop in average revenue per converted user).
* **If p-value >= 0.05:** We fail to reject the Null Hypothesis. We conclude that any observed difference between the groups is likely due to random chance. **Business Decision:** Do not launch the new campaign, as it does not reliably drive more paid conversions than the current baseline

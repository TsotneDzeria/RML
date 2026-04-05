# Compliance Memo: COMPAS Fairness and Bias Analysis

**To:** Regulatory Oversight Committee | **From:** Lead Data Scientist | **Date:** April 4, 2026 | **Subject:** Summary of Risk Assessment Algorithm Audit

---

## Executive Summary

This memo summarizes the audit of the COMPAS recidivism risk assessment tool. Our findings indicate statistically significant racial disparities in both score assignment and predictive accuracy, suggesting that the model may not meet the equitable standards required for judicial decision-making support.

## Metrics and Findings

We employed three primary fairness metrics to evaluate the system:

### 1. Adverse Impact Ratio (AIR) and Marginal Effect (ME)

African-American defendants had an AIR of 0.56 relative to Caucasian defendants, well below the 0.80 four-fifths threshold, with a favorable-outcome rate 33 percentage points lower (ME = 0.33). Native Americans showed the most extreme disparity (AIR = 0.24, ME = 0.57), though this group is very small (n = 11). Asian, Hispanic, and Other groups all had AIRs above 1.0, indicating no adverse impact relative to Caucasians. By sex, Females showed a slight advantage over Males (AIR = 1.06), with no practically significant disparity.

### 2. Intersectional Analysis (Race × Sex)

Using Caucasian/Male as the reference group, African-American/Male defendants were the worst-affected subgroup (AIR = 0.53, sel. rate = 0.40, n = 2,626), followed by African-American/Female (AIR = 0.64, sel. rate = 0.49). Caucasian/Female fell just above the threshold at AIR = 0.90. All other intersectional subgroups exceeded parity.

### 3. Error Rate Disparity (FPR/FNR)

The False Positive Rate for African-American defendants (32.0%) was nearly four times that of Caucasian defendants (8.6%), confirmed as highly significant by z-test (z = 15.09, p < 0.001). Native Americans showed an FPR of 66.7% (p < 0.001), though on a very small sample. Conversely, the False Negative Rate for African-Americans (18.4%) was substantially lower than for Caucasians (49.4%, z = −16.10, p < 0.001), meaning the model under-predicts recidivism for Caucasians while over-predicting it for African-Americans. Hispanic and Other groups showed significantly elevated FNRs (66.1% and 77.4% respectively, both p < 0.001) but FPRs comparable to Caucasians.

### 4. Standardized Mean Difference (SMD)

African-American defendants had an SMD of 81.8 (×100 scale) and Native Americans 160.2, both far exceeding the ±20 practical-significance threshold, confirming a large shift in assigned risk scores. By sex, the SMD of −20.1 for Females sits at the threshold boundary and was not flagged as practically significant.

## Limitations and Caveats

While the statistical evidence of bias is robust, the following limitations must be considered:

- **Lack of Causality:** The metrics identify correlations and outcomes but do not isolate the specific causal mechanisms (e.g., systemic policing biases vs. algorithmic design) driving these disparities.
- **Label Bias:** The recidivism outcome is measured by re-arrest, which is a proxy for criminal behavior and may itself be influenced by racially disparate policing patterns.
- **Omitted Variables:** The analysis is restricted to the features provided in the ProPublica dataset. Unobserved socioeconomic factors may influence recidivism rates independent of the variables analyzed.
- **Small Subgroups:** Several subgroups (Native American n = 11, Asian n = 31) are too small for reliable inference; their results should be interpreted with caution.

## Conclusion

The current implementation of the COMPAS system demonstrates significant disparate impact and unequal error distributions, most acutely affecting African-American defendants — particularly African-American males. The model simultaneously over-classifies African-Americans as high-risk (elevated FPR) and under-classifies Caucasians (elevated FNR), producing asymmetric errors that compound racial inequality. We recommend a review of the model's weightings and an investigation into alternative, less-discriminatory assessment methodologies.

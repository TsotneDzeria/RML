## Compliance Memo: COMPAS Fairness and Bias Analysis

**To:** Regulatory Oversight Committee  
**From:** Lead Data Scientist  
**Date:** April 4, 2026
**Subject:** Summary of Risk Assessment Algorithm Audit

### Executive Summary
This memo summarizes the audit of the COMPAS recidivism risk assessment tool. Our findings indicate statistically significant racial disparities in both score assignment and predictive accuracy, suggesting that the model may not meet the equitable standards required for judicial decision-making support.

### Metrics and Findings
We employed three primary fairness metrics to evaluate the system:
1. **Adverse Impact Ratio (AIR):** We observed an AIR of 1.74 for African-American defendants relative to Caucasian defendants, far exceeding the 0.80 threshold typically used to identify disparate impact. Conversely, the Hispanic/Female intersectional group showed an AIR of 0.27, indicating severe under-classification relative to the reference group.
2. **Error Rate Disparity (FPR/FNR):** The False Positive Rate (FPR) for Black defendants (42.3%) was nearly double that of White defendants (22.0%). Furthermore, the False Negative Rate (FNR) was significantly higher for White defendants (49.6%) compared to Black defendants (28.5%). Z-tests confirmed these disparities are statistically significant (p < 0.0001).
3. **Standardized Mean Difference (SMD):** Cohen’s d indicated a 'medium' to 'large' effect size in score distributions between racial groups, confirming that the disparity is not merely a product of sample size but represents a substantial shift in assigned risk levels.

### Limitations and Caveats
While the statistical evidence of bias is robust, the following limitations must be considered:
*   **Lack of Causality:** The metrics identify correlations and outcomes but do not isolate the specific causal mechanisms (e.g., systemic policing biases vs. algorithmic design) driving these disparities.
*   **Label Bias:** The 'recidivism' outcome is measured by re-arrest, which is a proxy for criminal behavior and may itself be influenced by racially disparate policing patterns.
*   **Omitted Variables:** The analysis is restricted to the features provided in the ProPublica dataset; unobserved socioeconomic factors may influence recidivism rates independent of the variables analyzed.

### Conclusion
The current implementation of the COMPAS system demonstrates significant disparate impact and unequal error distributions. We recommend a review of the model's weightings and an investigation into alternative, less-discriminatory assessment methodologies.

**Memorandum**
**To:** Court Auditor
**Re:** Explainability Audit of the COMPAS Replacement Model

This memo summarizes the findings from using three explanation methods on a gradient-boosted classifier trained with the COMPAS recidivism dataset. It covers what the model seems to have learned, the limits of the methods used, and the recommended further monitoring.

**What the explanations reveal**
Both SHAP and LIME consistently show that prior arrest history and age are the main factors driving high-risk predictions for all four individuals studied. SHAP values confirm that higher prior counts push individual predictions above average, while older age pulls them down. The counterfactual analysis shows that it is possible to change the predictions by altering priors_count or crime_factor alone, without needing to change 'race_factor' or 'gender_factor'. This is a necessary condition for considering the model free of direct proxy discrimination on those features, although it does not guarantee fairness overall.

**Limitations of the methods**  
No single method is enough on its own. LIME only focuses on local accuracy and does not ensure consistency with the overall model behavior. This means its feature rankings can change between runs. SHAP has stronger guarantees but its marginalization procedure relies on feature independence, which may not be true for this dataset. Neither method is causal. A positive SHAP value for 'priors_count' indicates that the feature pushed the prediction above the average, but it does not mean that changing it would change the outcome. The counterfactuals meet proximity and accuracy but do not fully address diversity or plausibility as defined by Dandl et al.

**Recommended monitoring**  
Transparency is essential but does not guarantee alignment. These explanations should be part of a documented audit process instead of being treated as a one-time compliance report. At a minimum, the model should be monitored for different error rates across racial groups, and the plausibility of counterfactual recourse should be verified regularly as the model is updated.

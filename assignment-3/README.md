# COMPAS Fairness and Bias Audit — Individual Homework 3

## Purpose

This repository contains a disparate impact audit of the COMPAS recidivism risk assessment tool, completed for DNSC 6330: Responsible Machine Learning (Lecture 03). Using a gradient-boosted tree (GBT) model trained in Lecture 02 on the ProPublica COMPAS dataset, the analysis evaluates algorithmic fairness across race and sex through four tasks:

1. **Discrimination testing (AIR, ME, SMD):** Computes the Adverse Impact Ratio, Marginal Effect, and Standardized Mean Difference by race and sex using the `solas-ai-disparity` library, with Caucasian and Male as reference groups respectively.
2. **Intersectional analysis (Race × Sex):** Constructs race–sex subgroups, calculates selection rates and AIR relative to Caucasian/Male, and identifies the worst-affected subgroup.
3. **Error-rate disparity (FPR/FNR):** Computes False Positive and False Negative Rates by race, tests each against the Caucasian reference group using two-proportion z-tests, and reports statistical significance.
4. **Compliance memo:** Summarizes findings, metrics, and limitations in a 300-word memo addressed to a hypothetical regulator.

## Python Libraries

| Library | Version | Purpose |
|---|---|---|
| `pandas` | ≥ 1.5 | Data manipulation and aggregation |
| `numpy` | ≥ 1.23 | Numerical operations |
| `scikit-learn` | ≥ 1.2 | GBT model training and predictions (Lecture 02) |
| `matplotlib` | ≥ 3.6 | Publication-quality bar chart of FPR/FNR |
| `solas-ai-disparity` | ≥ 0.3 | AIR, ME, and SMD computation via legally grounded disparity tests |
| `statsmodels` | ≥ 0.13 | Two-proportion z-tests (`proportions_ztest`) |
| `scipy` | ≥ 1.9 | Supporting statistical functions |

## Reproducing the Results

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

### 2. Install dependencies

```bash
pip install pandas numpy scikit-learn matplotlib statsmodels scipy solas-ai-disparity
```

### 3. Run the notebook

Open the Jupyter/Colab notebook and run all cells in order:

```bash
jupyter notebook HW3_Individual.ipynb
```

The notebook expects the cleaned COMPAS dataset produced by the Lecture 01–02 pipeline. If running from scratch, ensure the data cleaning and GBT model training cells from Lecture 02 execute first, as downstream fairness analyses depend on the columns `y_pred`, `y_pred_prob`, `y_fav`, `two_year_recid`, `race`, and `sex`.


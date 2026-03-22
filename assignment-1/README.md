# COMPAS Recidivism Analysis (Python Implementation)

## 1. Purpose of the Analysis

This project reproduces the COMPAS recidivism analysis originally conducted by ProPublica by translating the full analytical workflow from R into Python. The analysis includes exploratory data analysis (EDA), data preprocessing, feature construction, logistic regression modeling, and model evaluation.

The primary objective is to understand how COMPAS risk scores relate to demographic characteristics (such as race, age, and gender) and criminal history variables. Additionally, the analysis evaluates model performance and investigates potential disparities across racial groups using metrics such as false positive rate (FPR) and false negative rate (FNR).

---

## 2. Python Libraries Used

The following Python libraries were used to implement the workflow:

- pandas – data loading, cleaning, and manipulation  
- numpy – numerical computations  
- matplotlib – data visualization  
- statsmodels – logistic regression modeling and statistical analysis  

---

## 3. Instructions for Reproducing the Results

### Step 1: Clone the repository
git clone <your-repo-link>  
cd <repository-name>

### Step 2: Install required dependencies
pip install pandas numpy matplotlib statsmodels

### Step 3: Run the analysis
- Open the Jupyter Notebook or Python script included in the repository  
- If using Jupyter Notebook, run:  
  jupyter notebook  
- Run all cells sequentially from top to bottom  

### Step 4: Data source
The dataset is automatically loaded from:  
https://raw.githubusercontent.com/propublica/compas-analysis/master/compas-scores-two-years.csv  

No manual download is required.

---

## Notes on Reproducibility and Differences

- The Python implementation closely follows the original R workflow  
- Minor differences in outputs may occur due to:
  - categorical variable encoding differences  
  - reference group handling in regression models  
  - numerical precision and rounding  
- Despite these differences, the analytical conclusions remain consistent  

---

## Summary

This project demonstrates a complete translation of an end-to-end machine learning workflow from R to Python, including:

- data preprocessing and feature engineering  
- exploratory data analysis  
- logistic regression modeling  
- model evaluation and fairness analysis  

The results provide insight into how predictive models behave across demographic groups and highlight the importance of fairness in machine learning systems.

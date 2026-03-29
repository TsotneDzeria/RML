# Individual Assignment 2. DNSC 6330 Responsible Machine Learning

## Purpose of the Analysis

This notebook uses methods to understand a computer model that predicts if someone will commit a crime again. The model was trained on data from people in Broward County, Florida. We want to see what the model has learned if its predictions make sense and if they align with fair and responsible machine learning.

The analysis is based on an example from Lecture 01 and Lecture 02. It uses three methods to explain the models predictions. The first method, SHAP shows how each piece of information affects the models predictions. It gives an overview and detailed plots for each person. The second method, LIME creates a model for each persons prediction to explain how the main model works. The third method, DiCE finds the changes that can flip a prediction giving people a way to change their outcome.

The four individuals examined are the highest-risk and lowest-risk defendants from the African-American and Caucasian subgroups in the test set. Explanations are compared across these individuals to surface any differences in how the model treats them.

## Python Libraries Used

The following libraries are needed to run this notebook.

* pandas is used for loading, cleaning and changing data.

* numpy is used for math operations.

* scikit-learn is used for training the model preparing data and evaluating results. This includes tools like LogisticRegression, GradientBoostingClassifier, Pipeline, ColumnTransformer, StandardScaler and OneHotEncoder.

* shap is used to compute values and create plots.

* lime is used to generate explanations for individual predictions.

* dice-ml is used to generate explanations for changing predictions via the DiCE framework.

* matplotlib is used for creating visualizations.

## Instructions for Reproducing the Results

The notebook was developed and tested in Google Colab. The steps below will allow you to reproduce the full analysis.

Step 1: Open the notebook in Google Colab or a local Jupyter environment with Python 3.

Step 2: Install the needed libraries that're not already in Colab. Run this in a code cell at the top of the notebook.

```

pip install shap lime dice-ml

```

Step 3: Run all cells from top to bottom. The data is loaded from a GitHub repository. No manual download is needed.

Step 4: Review the outputs. The notebook produces group-level performance metrics broken down by race, SHAP beeswarm and waterfall plots for the four selected individuals, LIME feature attribution tables for the same individuals, and DiCE counterfactual tables showing the minimal feature changes required to flip each prediction.

All random settings are fixed to 42 to ensure the results' reproducibility across runs.

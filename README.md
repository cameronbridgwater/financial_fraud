# Fraud Detection Project

This project analyzes transaction data to explore patterns associated with fraudulent activity and build predictive models that can distinguish fraud from non-fraud transactions.

## Project Overview

The workflow is organized into four steps:

1. **Exploration** — inspect the data, identify patterns, and understand feature distributions.
2. **Cleaning and preprocessing** — remove or transform features, engineer new variables, and prepare modeling datasets.
3. **Modeling** — train and tune classification models, then compare their performance.
4. **Reporting** — summarize findings and present the results clearly.

The project focuses on a highly imbalanced classification problem, so accuracy alone is not a reliable metric. Precision, recall, F1 score, and ROC AUC are more informative for evaluating performance.

## Data

The dataset contains transaction-level information, including:

- Transaction type.
- Transaction amount.
- Original and destination account balances.
- Flags and metadata related to fraud.

Some fields behave like identifiers and are not especially useful for prediction. Other fields, especially balance-related variables, appear to contain stronger signal.

## Key Findings from EDA

Exploratory analysis suggests several important patterns:

- Fraud is rare compared with non-fraud cases.
- Certain transaction types appear more associated with fraud than others.
- Transaction amount and balance-related variables show meaningful variation.
- Several numeric features are strongly skewed.
- Some balance variables are highly correlated with one another.

Because the fraud class is so small, the project emphasizes finding features and models that can better separate the two classes rather than relying on raw accuracy.

## Feature Engineering and Cleaning

The preprocessing step focuses on keeping features that appear useful and simplifying those that are redundant.

Typical actions include:

- Dropping identifier-like columns.
- Encoding transaction type.
- Creating engineered features from balance changes.
- Considering whether highly correlated balance variables should be reduced.
- Keeping extreme values when they appear meaningful to the fraud pattern.

The dataset is also split into different versions for comparison, including an all-transactions version and a fraud-focused version that keeps only the transaction types where fraud appears.

## Modeling Approach

Several classification models are compared so the project can balance interpretability and predictive power.

Models used include:

- Logistic Regression.
- Random Forest.
- XGBoost.

The modeling pipeline includes preprocessing steps such as scaling numeric features and one-hot encoding categorical features where needed. Hyperparameter tuning is used to improve each model and make comparisons more meaningful.

## Evaluation Strategy

Because the data is imbalanced, the project uses metrics that better reflect fraud detection performance:

- Precision.
- Recall.
- F1 score.
- ROC AUC.

These metrics help show whether a model can correctly identify fraud without producing too many false alarms. Accuracy is reported only as a secondary metric.

## Interpretation Notes

One important modeling question is whether multicollinearity matters here. For classification, it matters most when using linear models such as logistic regression, where correlated features can make coefficient estimates unstable and harder to interpret. For tree-based models, correlated features are usually less of a problem for prediction, though they can still make feature importance harder to read.

That means correlated balance variables do not automatically need to be removed. Whether to keep or drop them depends on the model and whether the goal is prediction, interpretation, or both.

## Repository Structure

```text
README.md
step1-explore.ipynb
step2-transform.ipynb
step3-model.ipynb
step4-report.ipynb
01eda.ipynb
02clean.ipynb
logistic_regression.ipynb
random_forests.ipynb
naive_bayes.ipynb
hyperparameters.ipynb
hyperparameters_solutions.ipynb
```

## How to Use

1. Start with the exploration notebook to understand the dataset.
2. Move to the cleaning notebook to prepare features.
3. Run the modeling notebook to train and compare classifiers.
4. Review the report notebook for the final summary.

## Project Goal

The goal is to build a fraud detection workflow that is clear, reproducible, and grounded in the data. The project aims to identify which features matter most, how preprocessing choices affect results, and which models perform best on an imbalanced fraud classification task.

If you want, I can also turn this into a more polished GitHub README with badges, setup instructions, and a stronger project summary.

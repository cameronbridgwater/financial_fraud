# Fraud Detection Analysis

Analyzes transaction data to detect fraudulent activity using exploratory analysis and classification models. **Best-performing model: XGBoost**.

## 🎯 Project Overview

Built a fraud detection workflow to understand which transaction features are most useful for separating fraud from non-fraud cases. **Key insights:**
- **Fraud is highly imbalanced**: only a very small share of transactions are fraudulent.
- **Transaction type matters**: fraud appears to cluster in specific transaction types.
- **Balance variables are important**: several account balance features show strong relationships with fraud.
- **Extreme values may be meaningful**: outliers are not always noise in this dataset.

## 📊 Data Overview

**Source**: Transaction-level fraud dataset

**Target**: `isFraud` = 1 for fraudulent transactions, 0 otherwise

### 📁 Dataset Files

- **step1-explore.ipynb** — Exploratory data analysis and visualization.
- **step2-transform.ipynb** — Data cleaning, feature engineering, and preprocessing.
- **step3-model.ipynb** — Classification modeling and evaluation.
- **step4-report.ipynb** — Final summary and reporting.

These files represent the main stages of the project workflow, from exploration through modeling and reporting.

### 🎯 Key Features (Top Impact)

| Feature | Data Type | Description | Notes |
|---------|-----------|-------------|-------|
| **type** | Categorical | Transaction type | Important for fraud patterns |
| **amount** | Numeric | Transaction amount | Higher values may be informative |
| **oldbalanceOrg** | Numeric | Sender balance before transaction | Strongly related to fraud behavior |
| **newbalanceOrig** | Numeric | Sender balance after transaction | Often highly correlated with other balance vars |
| **oldbalanceDest** | Numeric | Receiver balance before transaction | Useful for balance-change patterns |
| **newbalanceDest** | Numeric | Receiver balance after transaction | Useful for balance-change patterns |

### 🔧 Preprocessing Applied

- **Feature selection**: Dropped identifier-like columns such as `nameOrig` and `nameDest`.
- **Encoding**: One-hot encoding for `type`.
- **Feature engineering**: Created balance-difference and time-based features.
- **Correlation review**: Checked highly correlated balance variables for multicollinearity.
- **Dataset variants**: Built both all-transaction and fraud-focused versions.

## 🤖 Models & Performance

| Model | Purpose | Status |
|-------|---------|--------|
| **Logistic Regression** | Baseline linear classifier | Good for interpretability |
| **Random Forest** | Nonlinear tree-based model | Captures interactions |
| **XGBoost** | Boosted tree model | **Best performing model** |

**Evaluation focus:** precision, recall, F1 score, and ROC AUC.

## 📈 Key Insights

| Finding | Interpretation |
|---------|----------------|
| **Fraud is rare** | Accuracy alone is not enough |
| **Some transaction types are more suspicious** | Type is likely a strong predictor |
| **Balance features are highly correlated** | Multicollinearity may matter for linear models |
| **Extreme transaction amounts matter** | Large values may help identify fraud |
| **Fraud-focused subsets can be useful** | TRANSFER and CASH_OUT may contain the clearest signal |

## 📁 Project Structure

- **fraud-detection-project/**
  - **code/**
    - `step1-explore.ipynb` — EDA and pattern discovery  
    - `step2-transform.ipynb` — Cleaning and feature engineering  
    - `step3-model.ipynb` — Model training and evaluation  
  - **data/**
    - `raw_transaction_data.csv`
    - `cleaned_transaction_data.csv`
    - `fraud_only_data.csv`
  - **report/**
    - `step4-report.ipynb` — Final report  

## 🛠️ Tech Stack

- **pandas** — Data manipulation  
- **scikit-learn** — Preprocessing and classification models  
- **xgboost** — Gradient boosting classifier  
- **seaborn** — Visualization  
- **matplotlib** — Charts  
- **numpy** — Numerical operations  
- **jupyter** — Notebook workflow  

### 📦 Requirements

- **pandas**
- **scikit-learn**
- **xgboost**
- **seaborn**
- **matplotlib**
- **numpy**
- **jupyter**

## 🎯 Modeling Notes

1. **Use recall carefully** — catching fraud matters, but false positives also matter.
2. **Do not rely on accuracy** — the dataset is too imbalanced.
3. **Compare linear and tree-based models** — they handle redundancy differently.
4. **Keep feature engineering practical** — balance changes and transaction type are likely more useful than identifiers.

## 📈 Next Steps

- [ ] Tune model thresholds for better fraud recall.
- [ ] Compare feature importance across models.
- [ ] Test whether dropping correlated features improves interpretability.
- [ ] Add confusion matrix and ROC visuals.
- [ ] Finalize the reporting notebook with best model results.

---

**Built by Cameron Bridgwater | The Knowledge House Data Analytics Fellow | NYC | April 2026**
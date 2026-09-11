# Machine Failure Prediction for Predictive Maintenance

An end-to-end machine learning study for predicting machine failures using sensor and operational data.

This project explores how feature engineering, imbalanced classification, model selection, threshold optimization, error analysis, and explainable machine learning can be combined to develop a machine failure prediction model.

The project uses the **Machine Predictive Maintenance Classification** dataset from Kaggle.

---

## Project Overview

Unexpected machine failures can lead to production downtime, maintenance costs, and operational disruptions.

The objective of this project is to build a binary classification model that estimates whether a machine observation is associated with a failure.

The prediction target is:

- `0` — No Failure
- `1` — Machine Failure

Rather than focusing only on accuracy, this study evaluates the models using metrics that are more appropriate for an imbalanced classification problem:

- Recall
- Precision
- F1-score
- PR-AUC
- ROC-AUC

The analysis also investigates how different feature representations and classification algorithms affect model performance.

---

## Dataset

Dataset:

**Machine Predictive Maintenance Classification**

Source:

https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification

The dataset contains:

- 10,000 observations
- 10 original columns
- 3,39% machine failure observations
- 96,61% no-failure observations

### Original Features

| Feature | Description |
|---|---|
| `UDI` | Unique identifier |
| `Product ID` | Product identifier |
| `Type` | Product type |
| `Air temperature [K]` | Air temperature |
| `Process temperature [K]` | Process temperature |
| `Rotational speed [rpm]` | Rotational speed |
| `Torque [Nm]` | Torque |
| `Tool wear [min]` | Tool wear time |
| `Target` | Machine failure target |
| `Failure Type` | Failure category |

`UDI` and `Product ID` are removed because they are identifiers.

`Failure Type` is also excluded from the predictive features to avoid potential target leakage, since it contains information directly related to the failure outcome.

---

## Project Workflow

The project follows the following workflow:

```text
Raw Dataset
     │
     ▼
Data Quality Check
     │
     ▼
Exploratory Data Analysis
     │
     ▼
Data Cleaning
     │
     ▼
Feature Engineering
     │
     ▼
Train / Test Split
     │
     ├───────────────┐
     ▼               ▼
Original Features   Engineered Features
     │               │
     └───────┬───────┘
             ▼
       Baseline Models
             │
             ▼
 Logistic Regression
             │
             ▼
       Random Forest
             │
             ▼
          XGBoost
             │
             ▼
    Cross-Validation
             │
             ▼
    Threshold Analysis
             │
             ▼
      Error Analysis
             │
             ▼
       SHAP Analysis
             │
             ▼
    Hold-Out Test Set
             │
             ▼
       Final Evaluation

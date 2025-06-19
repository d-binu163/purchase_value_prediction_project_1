# 🧠 Predicting Purchase Value from Multi-Session User Behavior

This project aims to predict the **purchase value** of users based on their session-level behavioral data from an e-commerce platform. Various machine learning models were applied, optimized, and evaluated. The best-performing model was a **stacked ensemble of XGBoost and Random Forest**, with SHAP explainability applied.

---

## 📁 Project Structure

.
├── data/ # Raw or demo input data (optional)

├── notebooks/

│ └── final_model.ipynb # Final Jupyter notebook

├── models/

│ ├── final_model.pkl # Trained stacked model

│ └── preprocessor.pkl # Trained preprocessing pipeline

├── reports/

│ └── summary_report.pdf # Final project summary

├── visuals/

│ ├── model_comparison.png # Comparison plot of models

│ └── shap_summary.png # SHAP feature importance plot

├── requirements.txt

├── LICENSE (MIT)

└── README.md


---

## 📌 Problem Statement

> Predict the **monetary value of purchases** made by users during sessions using clickstream and session metadata.

---

## 🧪 Workflow

- ✅ Data cleaning & handling of nulls and dummy values
- ✅ Feature engineering (date extraction, time of day bucketing)
- ✅ Categorical reduction (via grouping & cardinality cutoffs)
- ✅ Feature selection using:
  - Cramér’s V, ANOVA, Point Biserial
  - RFE & Feature Importance from XGBoost
  - PCA
- ✅ Training ML models (Linear, KNN, SGD, RF, XGB, MLP)
- ✅ Stacking best models for ensemble prediction
- ✅ SHAP analysis for explainability
- ✅ Exporting final model and preprocessor

---

## 📈 Model Performance Summary

| Model              | R²       | RMSE       | Time (s) |
|--------------------|----------|------------|----------|
| **Stacked**        | **0.801**| **10.43**  | 26.08    |
| XGB_RFE            | 0.799    | 10.53      | 105.26   |
| RF_RFE             | 0.794    | 10.81      | 1478.00  |
| Random Forest      | 0.787    | 11.16      | 386.26   |
| KNN                | 0.769    | 12.10      | 194.40   |
| Linear Regression  | 0.561    | 23.03      | 5.28     |

---

## 🧠 Top Features (via SHAP)

- `timeOnSite`
- `pageViews`
- `geoNetwork.continent`
- `channelGrouping`
- `device.deviceCategory`

---

## 📦 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ML-Purchase-Prediction.git
   cd ML-Purchase-Prediction



## 📃 License

This project is licensed under the MIT License.
For educational and non-commercial use.

# 📊 Predicting Purchase Value from User Sessions  
*Final Project Summary Report*

---

## 📝 Problem Statement
In a digital ecosystem, understanding and predicting a user's purchase behavior based on their session data is a crucial aspect of driving personalized marketing and improving sales.  
This project aims to **predict the purchase value** of a user based on their **session-level features** using various machine learning models, while balancing **performance and runtime**.

---

## 📁 Dataset Description
The dataset consists of anonymized user session data from an e-commerce demo platform. It includes:

- Session timestamps, country, device info  
- Engagement metrics (page views, bounces, time on site)  
- Transaction data (`purchaseValue`)  
- Geography and traffic source info  

**Shape:** 115,313 rows × 12+ features (after processing)  
**Target:** `purchaseValue` (continuous variable)

---

## ⚙️ Workflow Overview

1. **Data Cleaning & Handling Missing Values**
   - Dropped high-null and redundant columns
   - Filled select missing values
   - Handled “(not set)” and “not available” dummy entries

2. **Feature Engineering**
   - Converted timestamp features into `day`, `month`, `time of day`
   - Removed datetime columns afterward

3. **Exploratory Data Analysis**
   - Univariate, bivariate, multivariate analysis
   - Categorical reduction based on cardinality and correlation
   - Used ANOVA, Point Biserial, and Cramér’s V for statistical relevance

4. **Feature Selection**
   - Recursive Feature Elimination (RFE)
   - Feature Importance from XGBoost
   - PCA for dimensionality reduction

5. **Modeling & Evaluation**
   - Trained: Linear, SGD, KNN, SVR, RandomForest, XGBoost, MLP
   - Tuned with `GridSearchCV` and `RandomizedSearchCV`
   - Compared using R², RMSE, and runtime
   - Final model: **Stacked Ensemble**

---

## 🤖 Model Performance Summary

| Model              | R²       | RMSE       | Time (s)     |
|--------------------|----------|------------|--------------|
| **Stacked**        | **0.801**| **10.43**  | 26.08        |
| XGB_RFE            | 0.799    | 10.53      | 105.26       |
| XGB_FI             | 0.799    | 10.54      | 100.70       |
| RF_RFE             | 0.794    | 10.81      | 1478.00      |
| XGBoost            | 0.789    | 11.09      | 200.45       |
| Random Forest      | 0.787    | 11.16      | 386.26       |
| KNN                | 0.769    | 12.10      | 194.40       |
| Linear Regression  | 0.561    | 23.03      | 5.28         |
| SGD Regression     | 0.561    | 23.04      | 51.12        |

📌 **Best Trade-off:** `XGB_RFE`  
📌 **Best Overall Performance:** `Stacking (XGB + RF)`  
📌 **Fastest Model:** `Linear Regression` (but poor accuracy)

---

## 🧠 Explainability

Used **SHAP (SHapley Additive exPlanations)** to understand:
- Which features drive predictions most
- Found top predictors include:
  - `timeOnSite`
  - `pageViews`
  - `geoNetwork.continent`
  - `channelGrouping`
  - `device.deviceCategory`

---

## 🏁 Conclusion

- **Stacking XGB_RFE, XGB_FI, and RF_RFE** yielded the **best performance** (R² = 0.801).
- **Runtime trade-off** is important — XGB alone with RFE gives almost the same performance with 1/4th runtime.
- The most predictive features are related to **session duration, page views, and geographic traffic sources**.

---

## 🔮 Future Work

- Try **LightGBM** or **CatBoost** for possibly faster performance
- Use **AutoML** frameworks (e.g., AutoSklearn, TPOT)
- Convert model into a **Flask/Streamlit app** for deployment
- Improve prediction granularity by exploring sequential user behavior

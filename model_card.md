# Formal Model Card: Churn Prediction Ensemble

This model card details the intent, performance boundaries, and maintenance guidelines for our machine-learning retention engine.

---

##  Model Overview
* **Intended Use:** Identification of D2C subscribers likely to abandon the platform within an upcoming 60-day target tracking window.
* **Architecture:** Random Forest Classifier Ensemble (200 estimators, depth 8, balanced class-weights configuration).
* **Baseline Reference:** Standardized Class-Weighted Logistic Regression Classifier.

---

##  Feature Importance Rankings

| Rank Priority | Inspected Customer Behavioral Vector | Relative Feature Importance Weight |
| :---: | :--- | :---: |
| 1 | **Recency** | 71.36% |
| 2 | **Monetary_Value** | 18.46% |
| 3 | **Frequency** | 5.72% |
| 4 | **Support_Complaints** | 4.47% |
| 5 | **Web_Interactions** | 0.00% |

---

##  Evaluation Data and Performance Metrics
* **Data Limits:** Transactional records strictly bounded at or before the chronological ceiling (**2025-09-30**).
* **Splitting Protocol:** Stratified random splits (60% Train / 20% Validation / 20% Test).
* **Baseline Benchmarking:** Our final machine learning ensemble successfully outperformed the baseline framework on independent validation split pools (**85.07% ROC-AUC** vs **85.97% ROC-AUC**).

---

##  Known Limitations & Algorithmic Guardrails
* **Cold Start Constraints:** New platform users with fewer than 30 days of logging history cannot be reliably scored.
* **Demographic Bias Risk:** The system inherently prioritizes high-spend tiers due to financial weight metrics. This must be monitored to ensure entry-level accounts aren't completely ignored by customer service.

---

##  Monitoring & Maintenance Lifecycle
* **Drift Check Cadence:** Run automatic Population Stability Index (PSI) reports every 30 days to check for shifts in consumer distributions.
* **Re-training Strategy:** Trigger a complete pipeline update every quarter using fresh, time-fenced transaction data.

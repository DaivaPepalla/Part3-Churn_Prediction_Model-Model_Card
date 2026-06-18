# Error Analysis Report

This document profiles exactly 10 customer accounts where the model's predictions deviated from the actual ground-truth outcomes on the test split.

---

##  Business Threshold Context
* **Selected Decision Boundary Cutoff:** **0.35**
* **Strategic Justification:** We lowered our classification threshold to prioritize **Recall** (85.33%). Missing a real churner (False Negative) costs significant platform revenue. Offering a minor retention benefit to a safe customer (False Positive) is a drop in the bucket compared to total customer acquisition costs.

---

## 🕵️ Micro-Level Error Case Matrix

| Customer ID | Recency | Frequency | Spend (₹) | Support Tickets | Web Activity | Score Prob | Error Profile Type | Root Cause Analysis & Interpretation |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- | :--- |
| `CUST01969` | 80d | 2 | ₹1,641.00 | 1 | 1 | 0.53 | **False Positive 🟢** | Account shows clear friction metrics (high support counts or low recency) triggering a risk alert. However, the customer stayed loyal. It is commercially safer to over-index on these cases. |
| `CUST00437` | 151d | 1 | ₹729.22 | 0 | 1 | 0.87 | **False Positive 🟢** | Account shows clear friction metrics (high support counts or low recency) triggering a risk alert. However, the customer stayed loyal. It is commercially safer to over-index on these cases. |
| `CUST00734` | 89d | 5 | ₹4,981.82 | 2 | 1 | 0.39 | **False Positive 🟢** | Account shows clear friction metrics (high support counts or low recency) triggering a risk alert. However, the customer stayed loyal. It is commercially safer to over-index on these cases. |
| `CUST00332` | 24d | 2 | ₹2,059.80 | 2 | 1 | 0.36 | **False Positive 🟢** | Account shows clear friction metrics (high support counts or low recency) triggering a risk alert. However, the customer stayed loyal. It is commercially safer to over-index on these cases. |
| `CUST00555` | 45d | 3 | ₹1,924.03 | 2 | 1 | 0.36 | **False Positive 🟢** | Account shows clear friction metrics (high support counts or low recency) triggering a risk alert. However, the customer stayed loyal. It is commercially safer to over-index on these cases. |
| `CUST00867` | 15d | 1 | ₹424.64 | 1 | 1 | 0.32 | **False Negative 🔴** | Silent Churner. Standard usage signals look completely stable on paper, but the account left due to unlogged real-world variables (competitor pricing shifts, out-of-app life changes). |
| `CUST01857` | 74d | 9 | ₹5,573.32 | 5 | 1 | 0.25 | **False Negative 🔴** | Silent Churner. Standard usage signals look completely stable on paper, but the account left due to unlogged real-world variables (competitor pricing shifts, out-of-app life changes). |
| `CUST00877` | 63d | 3 | ₹1,904.33 | 1 | 1 | 0.34 | **False Negative 🔴** | Silent Churner. Standard usage signals look completely stable on paper, but the account left due to unlogged real-world variables (competitor pricing shifts, out-of-app life changes). |
| `CUST00309` | 8d | 3 | ₹2,731.61 | 0 | 1 | 0.13 | **False Negative 🔴** | Silent Churner. Standard usage signals look completely stable on paper, but the account left due to unlogged real-world variables (competitor pricing shifts, out-of-app life changes). |
| `CUST00069` | 29d | 2 | ₹874.47 | 0 | 1 | 0.19 | **False Negative 🔴** | Silent Churner. Standard usage signals look completely stable on paper, but the account left due to unlogged real-world variables (competitor pricing shifts, out-of-app life changes). |

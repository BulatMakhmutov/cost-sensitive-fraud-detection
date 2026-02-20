# Cost-Sensitive Fraud Detection

End-to-end fraud detection pipeline with threshold optimization and business cost evaluation on a highly imbalanced dataset (~0.17% fraud rate).

---

## 📌 Project Overview

Fraud detection is a classic example of an imbalanced classification problem, where fraudulent transactions represent a very small fraction of total activity.

This project demonstrates how to:

- Handle extreme class imbalance
- Use appropriate evaluation metrics (Precision, Recall, PR-AUC)
- Optimize decision thresholds
- Incorporate asymmetric business costs
- Align model decisions with business impact

---

## ⚙️ Methodology

### 1️⃣ Exploratory Data Analysis (EDA)

- Verified extreme class imbalance (~0.17% fraud)
- Analyzed transaction amount distribution
- Applied log transformation to reduce skewness

### 2️⃣ Baseline Model

- Logistic Regression classifier
- Train-test split with stratification
- Evaluated using:
  - Confusion Matrix
  - Precision & Recall
  - F1-score

Accuracy was avoided due to class imbalance.

---

### 3️⃣ Feature Scaling

- Applied `StandardScaler`
- Observed impact on Precision-Recall trade-off
- Improved model convergence

---

### 4️⃣ Threshold Optimization

The default threshold (0.5) is not optimal in highly imbalanced datasets.

- Analyzed predicted probabilities
- Evaluated multiple thresholds
- Compared Precision–Recall trade-offs

---

### 5️⃣ Business Cost Optimization

To simulate a realistic fraud detection setting:

- False Negative (missed fraud) cost: **1000**
- False Positive (false alert) cost: **10**

Total expected business cost:

Total Cost = FN * 1000 + FP * 10


A grid search over thresholds identified an optimal decision threshold that significantly reduced total expected cost compared to the default 0.5 threshold.

---

### 6️⃣ Precision-Recall Evaluation

- Computed PR curve
- PR-AUC ≈ 0.73
- Demonstrated strong performance under extreme class imbalance

PR-AUC is more informative than ROC-AUC in rare-event detection problems.

---

## 🎯 Key Insights

- Accuracy is misleading in highly imbalanced datasets.
- Default probability thresholds are rarely optimal.
- Threshold tuning significantly impacts Recall–Precision trade-offs.
- Fraud detection should be treated as a cost-sensitive optimization problem.
- Business-aligned decision rules can dramatically reduce expected loss.

---

## 🚀 Production Considerations

In a real-world deployment:

- Continuous monitoring would be required
- Periodic retraining to address concept drift
- Probability calibration may improve threshold stability
- More advanced models (e.g., Gradient Boosting) could be explored

---

## 🛠️ Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib

---

## 📂 Dataset

Kaggle Credit Card Fraud Detection dataset.

---

## 👤 Author

Bulat Makhmutov  

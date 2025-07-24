# Drug-Efficacy-Analysis-Using-Real-World-Evidence



# 💊 Drug Efficacy Evaluation: Drug_D vs Drug_S

## DecodeX 2025 – Real World Evidence (RWE) Hackathon  
**Team Name**: Orion  
**Team Members**: Sanya Saxena, Harsh Tantak, Prashant Srivastava  
🏥 **Objective**: To evaluate the **real-world efficacy** of Drug_D and Drug_S by analyzing asthma patient outcomes while accounting for selection bias and treatment assignment imbalance.

---

## 🎯 Business Objective

To provide **unbiased, actionable insights** on which drug better reduces **asthma exacerbations** in the first year of treatment by:

- Adjusting for **selection bias** in observational data
- Using **inverse probability weighting (IPW)** and **PCA-based severity scoring**
- Comparing clinical and cost outcomes

---

## 📦 Dataset Overview

A real-world dataset from LifeMed Research, comprising:

- **Identity Features** (e.g., Patient ID)
- **Pre-Index Features**: Demographics, diagnostic history (e.g., bronchitis, sinusitis, GERD)
- **Pre-Treatment Usage**: Previous drug usage, asthma days, pharma costs
- **Post-Index Outcomes**: Number of exacerbations after treatment

---

## ⚖️ Key Challenges

- **Non-randomized treatment assignment**
- **Imbalanced groups** (Drug_S vs Drug_D)
- **High multicollinearity** and **redundant features**

---

## 🧪 Data Preparation & Balancing

- Dropped redundant features (e.g., constant columns)
- Assessed imbalance via **Standardized Mean Differences (SMD)**
- Applied **Inverse Probability Treatment Weighting (IPTW)** to simulate randomized control

---

## 🧠 Feature Engineering

- **Propensity Scores** estimated via logistic regression
- **PCA-based Severity Scoring**:
  - Combined asthma treatment intensity into a single score (0–100 scale)
  - Grouped into **Mild**, **Moderate**, and **Severe** categories

---

## 📈 Statistical Analysis

- **Chi-square tests** on categorical comorbidities (bronchitis, laryngitis, etc.)
- **T-tests** on continuous variables (age, costs, days)
- **Results**:
  - Drug_S patients had **fewer exacerbations** (mean = 0.0800 vs 0.1648 for Drug_D)
  - **Statistically significant difference** (T = -20.24, p < 0.0001)
  - **Absolute Risk Reduction (ARR)** = 0.0768 (~47%)

---

## 🤖 Predictive Modeling

### Model: **XGBoost Regressor** (with Poisson objective)

- **Target**: Number of exacerbations
- **Preprocessing**: IPW applied, standardization of costs/severity
- **Split**: 80% train, 20% test

### Evaluation Metrics:

| Metric | Score |
|--------|-------|
| RMSE   | 0.4521 |
| MAE    | 0.3187 |
| R²     | 0.6823 |

---

## 📊 Key Insights

- **Drug_S** is more effective in reducing asthma exacerbations
- **Consistent** and **predictable** performance (shown via KDE plot)
- **Drug_D** has **lower cost** but **higher exacerbation rates**
- **Tradeoff**: Drug_S = better outcomes, Drug_D = lower financial burden

---

## 🔍 Comparative Summary

| Metric | Drug_S | Drug_D |
|--------|--------|--------|
| Mean Exacerbations | 0.0800 | 0.1648 |
| Adherence Rate     | 0.31   | 0.24   |
| Avg Pre-Asthma Cost (Severe) | 1619.63 | 916.46 |

---

## 🧬 Final Conclusion

- **Drug_S** significantly reduces asthma exacerbations and improves patient adherence
- **Clinically meaningful** benefit with ~47% **risk reduction**
- Despite higher costs, **Drug_S is preferred** for severe asthma management

---

## 📌 Clinical Recommendation

> **Prescribe Drug_S** for asthma patients where outcome consistency and reduced exacerbation risk are a priority.  
> Consider **Drug_D** for cost-sensitive patients with milder conditions.

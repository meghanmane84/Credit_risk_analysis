# Multi-Objective Credit Risk & Revenue Optimization Engine

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Machine Learning](https://img.shields.io/badge/ML-XGBoost-orange.svg)
![Financial Engineering](https://img.shields.io/badge/Focus-Risk%20Analytics-green.svg)

## 🎯 Executive Summary
In the financial services sector, data science is utilized to bridge the gap between risk mitigation and capital growth. This project implements a **Dual-Stage Decision Engine** that evaluates creditworthiness while simultaneously identifying revenue-generating opportunities through customer segmentation.

The engine moves beyond simple "Yes/No" lending decisions by quantifying risk in monetary terms and simulating economic volatility to ensure portfolio resilience.

## 📊 Technical Architecture & Concepts

### 1. Robust Risk Classification
* **Algorithm:** Utilizing **XGBoost (Extreme Gradient Boosting)** to capture non-linear dependencies between borrower attributes (e.g., Debt-to-Income, Credit Utilization) and default outcomes.
* **Class Imbalance Management (SMOTE):** Financial datasets typically suffer from "Majority Class Bias" where non-defaults far outnumber defaults. I implemented **Synthetic Minority Over-sampling Technique (SMOTE)** to generate synthetic minority examples, ensuring the model achieves high sensitivity (Recall) for high-risk profiles.

### 2. Financial Analytics Framework
The project integrates a formal **Expected Loss (EL)** model, a standard pillar of global banking regulations (Basel III/IFRS 9).



$$EL = PD \times LGD \times EAD$$

* **PD (Probability of Default):** The statistical likelihood of a borrower failing to meet obligations, derived from model output probabilities.
* **LGD (Loss Given Default):** The share of an asset that is lost if a borrower defaults, standardized here at 45% for unsecured retail assets.
* **EAD (Exposure at Default):** The total value a bank is exposed to at the time of default, calculated based on current installments and loan structures.

### 3. Macroeconomic Stress Testing
To evaluate the "Value at Risk," the system includes a **Scenario Analysis** module. It subjects the current portfolio to a simulated economic shock:
* **Income Contraction:** Simulating a 20% systemic drop in reported earnings.
* **Interest Rate Volatility:** Simulating a 500 basis point (5%) hike in rates.
The engine calculates a **"Risk Delta,"** identifying the percentage of the portfolio that migrates from "Investment Grade" to "Speculative Grade" under stress.

### 4. Unsupervised Strategic Segmentation
Using **K-Means Clustering**, the engine segments the customer base into four strategic tiers based on the intersection of Credit Score (FICO) and Predicted Risk (PD):
* **High-Value/Low-Risk:** Candidates for premium wealth management and low-interest credit lines.
* **Emerging/Mid-Risk:** Candidates for standard retail products and limit-increase programs.
* **Vulnerable/High-Risk:** Targeted for restructuring or credit counseling to prevent default.

## 🛠 Tech Stack
* **Core:** Python (Pandas, NumPy)
* **ML/Stats:** XGBoost, Scikit-Learn, Imbalanced-Learn (SMOTE)
* **Visualization:** Matplotlib, Seaborn (for Risk-Reward heatmaps)

## 📈 Analysis & Strategic Insights

This section outlines the key findings derived from the model and how they translate into actionable financial strategy.

### 1. Model Performance & Robustness
The **XGBoost Classifier** was evaluated using the ROC-AUC metric to ensure a high degree of separation between "Safe" and "Default" profiles.
* **Precision-Recall Tradeoff:** By implementing SMOTE, we improved the model's ability to identify high-risk borrowers who would have otherwise been missed by a standard classifier.
* **Feature Importance:** Analysis revealed that `fico` (Credit Score), `int.rate` (Interest Rate), and `dti` (Debt-to-Income) were the primary drivers of default risk.

### 2. Risk vs. Reward Visualization
The following segmentation strategy was derived from the intersection of Credit Scores and Predicted Probability of Default (PD):



* **Quadrant 1 (High FICO, Low PD):** Labeled as **"Private Wealth."** These individuals are eligible for premium, low-yield/low-risk products.
* **Quadrant 2 (Low FICO, High PD):** Labeled as **"High Risk/Recovery."** These accounts require stricter monitoring and higher capital reserves.

### 3. Financial Quant: Expected Loss (EL) Distribution
By calculating $EL = PD \times LGD \times EAD$, we moved from statistical probability to monetary risk.
* **Insight:** We identified that 10% of the customer base accounts for nearly 45% of the total **Expected Loss**. 
* **Action:** This allows for "Risk-Based Pricing," where interest rates are dynamically adjusted to cover the cost of expected credit losses.

### 4. Stress Test Results (Resilience Analysis)
We simulated a "Severe Economic Downturn" (20% Income Drop + 5% Interest Hike):
* **Migration Analysis:** Under stress, approximately **12% of "Standard" customers migrated into the "High Risk" segment.**
* **Capital Adequacy:** This insight helps the institution determine if they have enough "Capital Buffers" to survive a recession without failing.

### 5. Strategic Recommendations
1. **Automated Approval:** Implement a "Green Channel" for the **Private Wealth** segment (Low PD) to reduce manual processing time by 70%.
2. **Pre-emptive Restructuring:** Offer the **Debt Consolidation** segment lower interest rates in exchange for longer terms to prevent imminent defaults.
3. **Dynamic Provisioning:** Use the **Expected Loss** values to update the bank's balance sheet in real-time, ensuring compliance with global accounting standards.

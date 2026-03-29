# J.P. Morgan Quantitative Research: Credit Risk & Portfolio Stress Testing

**Author:** Risalat Masrafi  
**Institution:** Singapore Polytechnic  
**Date:** February 2026

---

## 🎯 Executive Summary
This project develops a high-fidelity quantitative risk engine designed to evaluate a **$41.6M loan portfolio**. By integrating **Machine Learning (Inference)** with **Stochastic Simulation (Monte Carlo)**, the engine quantifies credit risk across varying economic regimes, providing actionable metrics for capital adequacy and regulatory compliance (Basel III/CCAR frameworks).

---

## 🛠️ Technical Workflow

### 1. Probability of Default (PD) Modeling
* **Algorithm:** Implemented a **Logistic Regression** classifier to estimate individual default probabilities.
* **Feature Engineering:** Utilized `StandardScaler` to normalize high-variance features like `Income` and `Total Debt`.
* **Risk Drivers:** Identified **Credit Lines Outstanding** and **Total Debt-to-Income** as the primary deterministic drivers of borrower insolvency.
* **Separation:** Achieved high model discrimination, resulting in a bimodal PD distribution that clearly separates "Prime" from "Subprime" assets.

### 2. Mortgage Portfolio Quantization (FICO Optimization)
* **Objective:** Discretized continuous FICO scores into a 10-tier risk-homogenous rating system.
* **Optimization:** Applied **Log-Likelihood Maximization** to determine optimal "cut-off" points, ensuring maximum statistical variance between rating buckets while maintaining intra-bucket homogeneity.

### 3. Stochastic Monte Carlo Simulation
To account for **Systemic Risk**, I engineered a simulation engine that tests the portfolio across 10,000 "Possible Futures":
* **Regime Switching:** Modeled three economic states: **Normal (90%)**, **Recession (1.5x Stress)**, and **Systemic Crisis (3.0x Stress)**.
* **Vectorized Computation:** Utilized NumPy matrix-vector multiplication for high-performance loss aggregation across 10,000 universes.

---

## 📊 Key Risk Metrics & Results
The simulation of the **$41.60M** portfolio yielded the following critical financial insights:

| Metric | Value | Financial Significance |
| :--- | :--- | :--- |
| **Portfolio Exposure (EAD)** | $41,596,770 | Total Capital at Risk |
| **Average Expected Loss (EL)** | $8,275,787 | Annual "Cost of Doing Business" |
| **99% Value at Risk (VaR)** | **$8,915,241** | **Regulatory Capital Requirement** |
| **Unexpected Loss (UL)** | $639,454 | Required Capital Buffer (Equity) |

### **Regime-Specific Stress Test (99% VaR)**
* **Normal Economy:** $8.33M
* **Recession Scenario:** $8.62M
* **Systemic Crisis:** $8.98M

> **Strategic Insight:** The "Three-Peak" loss distribution proves that credit risk is non-linear; the jump from a Normal to a Crisis regime requires a **~$650k liquidity buffer** to ensure bank solvency.

---

## 🚀 Technical Stack
* **Language:** Python 3.x
* **Data Science:** Pandas, NumPy, Scikit-Learn
* **Visualization:** Matplotlib, Seaborn (Multimodal Distribution Plotting)
* **Concepts:** Stochastic Modeling, Value at Risk (VaR), Log-Likelihood Optimization, Logistic Inference.

---

## 📈 Future Enhancements
* **Transition Matrices:** Implement Markov Chain models to track credit migration between FICO buckets.
* **Recovery Rate (LGD):** Move beyond 100% loss assumptions by modeling collateral hair-cuts.
* **Macro-Correlation:** Integrate live FRED API data to dynamically update economic state probabilities.
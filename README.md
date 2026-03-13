# J.P. Morgan Quantitative Research: Credit Risk & Mortgage Portfolio Valuation

**Author:** Risalat Masrafi  
**Institution:** Singapore Polytechnic  
**Date:** February 2026

---

## Project Overview
The objective of this project is to develop a comprehensive quantitative risk and valuation engine for J.P. Morgan's lending desks. The project focuses on two core strategic mandates:
1.  **Personal Loan Risk Engine:** A predictive model to assess the **Probability of Default (PD)** for loan applicants, enabling the calculation of "Expected Loss."
2.  **Mortgage Portfolio Quantization:** An optimized rating system that discretizes continuous FICO scores into ten risk-homogenous categories.

## Dataset Description
The analysis utilizes `Task 3 and 4_Loan_Data.csv`, containing 10,000 loan records with features including:
* **Credit Lines Outstanding:** Number of open credit lines.
* **Loan/Debt Outstanding:** Total financial obligations.
* **Income:** Annual earnings of the borrower.
* **FICO Score:** A measure of consumer credit risk.
* **Years Employed:** Employment stability metric.
* **Default:** Target variable (1 for default, 0 for successful repayment).

## Methodology

### Task 1 & 2: Default Prediction & Expected Loss
* **Modeling:** Developed a **Logistic Regression** model to predict the probability of default.
* **Key Drivers:** Identified that `Credit Lines Outstanding` and `Total Debt` are the most significant indicators of default risk.
* **Financial Impact:** Used the PD to calculate **Expected Loss** on a per-loan basis (Expected Loss = PD × Loan Amount), assuming a zero recovery rate for simplicity.

### Task 3 & 4: FICO Score Optimization
* **The Challenge:** Categorizing continuous FICO scores into "buckets" that maximize the difference in default rates between groups while minimizing the variance within them.
* **Optimization Logic:** Implemented a **Log-Likelihood Maximization** approach to find the mathematically optimal "cut-off" points for a 10-tier rating system.
* **Quantization:** Converted the complex FICO spectrum into a simplified 1-10 rating scale used for internal bank reporting.

## Getting Started

### Prerequisites
Install the necessary Python stack:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
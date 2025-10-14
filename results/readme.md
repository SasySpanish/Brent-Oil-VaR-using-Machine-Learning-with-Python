# Results

This folder contains visualizations of backtesting results:  
- [Traditional VaR backtesting results](backtesting_traditional_var.md)  
- [ML Models backtesting results](backtesting_ml_models.md)


# Value at Risk Backtesting Results

This section summarizes the **backtesting results** for all Value at Risk (VaR) estimation models applied to **Brent Crude Oil returns**, comparing both **traditional econometric approaches** and **machine learning techniques** in terms of calibration and accuracy.

---

## Traditional Models

Five classical methods were tested:

| Model | VaR (%) | Violations | Kupiec Test | Coverage | MAE | MSE | Notes |
|:------|:--------|:-----------|:-------------|:----------|:----|:----|:------|
| Parametric VaR | -3.77 | 4.52% | 6.22 | 95.48% | 0.0314 | 0.00110 | Conservative, tends to overestimate risk |
| Historical VaR | -3.63 | 5.01% | -0.09 | 94.99% | 0.0302 | 0.00102 | Well-calibrated, purely data-driven |
| Parametric GARCH VaR | -3.48 | 5.12% | -0.65 | 94.88% | 0.0283 | 0.00106 | Captures conditional volatility |
| Historical GARCH VaR | -3.51 | 5.01% | -0.09 | 94.99% | 0.0285 | 0.00107 | Slightly more accurate than Historical VaR |
| Quantile Regression | -3.47 | 5.01% | -0.09 | 94.99% | **0.0279** | **0.00104** | **Best calibration and precision** |

**Summary:**  
The *Quantile Regression* model achieved the lowest error values and near-perfect calibration, outperforming all other traditional methods. Both *Historical VaR* and *GARCH-based VaR* also provided stable and well-calibrated risk estimates.

---

## Machine Learning Models

Six machine learning models were evaluated:

| Model | Violations | Kupiec Test | Coverage | Quantile Loss | MAE | MSE | Notes |
|:------|:------------|:------------|:-----------|:----------------|:----|:----|:------|
| Quantile Regression Forest | 5.08% | -0.23 | 94.92% | 0.00156 | 0.0224 | 0.00078 | Moderate calibration and precision |
| Gradient Boosting | 4.97% | 0.02 | 95.03% | 0.00145 | 0.0221 | 0.00072 | Balanced model, reliable calibration |
| XGBoost | 4.92% | 0.03 | 95.08% | 0.00141 | 0.0219 | 0.00071 | Consistent and accurate |
| **LightGBM** | **5.19%** | **-0.18** | **94.81%** | **0.00137** | **0.0220** | **0.00070** | **Most accurate predictions** |
| **CatBoost** | **4.99%** | **0.01** | **95.01%** | 0.00139 | 0.0222 | 0.00071 | **Best calibration** |
| Neural Network | 5.03% | -0.10 | 94.97% | 0.00152 | 0.0223 | 0.00074 | Competitive, but less stable |

**Summary:**  
- **CatBoost** showed the most reliable calibration (violations ≈ 5%, Kupiec ≈ 0).  
- **LightGBM** achieved the best predictive accuracy (lowest loss, MAE, and MSE).  
- Boosting models (GB, XGB, LGB, CAT) provided the most balanced and effective VaR estimates overall, outperforming both Quantile Regression Forest and Neural Networks.

---

## Overall Insights

| Criterion | Best Traditional | Best ML | Key Takeaway |
|:-----------|:----------------|:--------|:--------------|
| Calibration | Quantile Regression | CatBoost | Both maintain violations near theoretical 5% |
| Accuracy | Quantile Regression | LightGBM | Machine Learning models reduce forecast error |
| Stability | GARCH Models | Gradient Boosting | Incorporating volatility or boosting improves robustness |

Overall, **machine learning methods—particularly CatBoost and LightGBM—demonstrate superior adaptability and precision** in modeling nonlinear dependencies and dynamic volatility patterns in crude oil prices, while **traditional approaches like Quantile Regression remain strong benchmarks for calibration consistency**.

---

## Visual Overview

- Traditional Models Backtesting:  
  ![Traditional VaR](images/var_backtest.png)

- Machine Learning Models Backtesting:  
  ![ML VaR](images/ml_backtest.png)

- Boosting Models Comparison (Losses):  
  ![Boosting Comparison](images/all_boost_loss.png)




Those highlight that boosting-based ML models (especially LightGBM) outperform other approaches in accuracy, coverage, and calibration. These results are consistent with the conclusions presented in the main analysis.

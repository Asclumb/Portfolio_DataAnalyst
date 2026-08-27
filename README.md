# Fachlevi Asclumb's Portfolio
Computational notebooks demonstrating statistical modeling, machine learning classification, and quantitative risk analysis. All notebooks are fully reproducible with locked random seeds and comprehensive visualizations.

---

## 💸[Financial Behavior Classification using XGBoost](https://colab.research.google.com/drive/1TsUnKwVKeduWpB0iswYQYgVw1RNUuChp?usp=sharing)
*Predicting Financial Profiles from Spending Patterns Using Behavioral Ratios*

This notebook builds a machine learning classifier that predicts financial profiles (Hemat / Normal / Boros) from behavioral spending ratios rather than raw income. Two people earning the same salary can end up with completely different financial profiles — disiplin, not salary, drives the outcome. The pipeline includes data preprocessing, feature engineering (Savings Rate, Wants Ratio, Needs Ratio), hyperparameter tuning via GridSearchCV, and evaluation via confusion matrix and classification metrics. The final tuned XGBoost model achieves >85% accuracy on unseen data, with key insights visualized through bar charts, scatter plots (Wants vs Savings), and feature importance rankings.

**Key Tools & Libraries:**
> - **XGBoost** for gradient boosting classification with hyperparameter grid search;
> - **scikit-learn** for train/test split, LabelEncoder, and classification metrics (accuracy, precision, recall, F1);
> - **pandas & numpy** for data manipulation, ratio engineering, and numerical operations;
> - **matplotlib & seaborn** for publication-ready greyscale visualizations (bar charts, scatter plots, confusion matrix, boxplots);
> - **Jupyter notebooks** with full inline markdown explanations and section-by-section walkthrough.

**Reproducibility:** The pipeline is fully reproducible across all 9 sections. Simply change the dataset import path to run the same workflow on different behavioral finance datasets.

---

## ♻️[Estimating Value at Risk for ANTM Stock Using Monte Carlo Simulation With Modified Distribution Student's T](https://colab.research.google.com/drive/18FZXWhEbTe6_ZkHaTLixR_wlVdp8JXXw?usp=sharing)
*Validating Fat-Tailed Distributions and Running Geometric Brownian Motion Simulations with Student's t Shocks*

This notebook is the computational appendix to an undergraduate thesis on quantitative risk management. It estimates Value at Risk (VaR) for Indonesian mining stock ANTM using a Monte Carlo simulation engine powered by Student's t distribution instead of the standard Normal assumption. The analysis uncovers that ANTM's daily log-returns exhibit significant leptokurtosis (fat tails), which classical Kolmogorov-Smirnov tests confirm: Student's t is the best-fitting distribution over Normal and LogNormal alternatives. A GBM simulation with 10,000 paths and Student's t shocks then estimates VaR across four investment horizons (1 day, 1 month, 2 months, 3 months), showing how tail risk compounds over time. Includes manual walkthroughs of the GBM formula, Q-Q plots validating the distributional fit, and sensitivity analysis comparing Student's t VaR against a Normal-shock baseline.

**Key Tools & Libraries:**
> - **yfinance** for pulling historical daily closing prices from Yahoo Finance (ANTM.JK, May 2023–May 2024);
> - **scipy.stats** for Kolmogorov-Smirnov goodness-of-fit testing, Maximum Likelihood parameter estimation, and t-distribution PDF/quantile generation;
> - **numpy** for vectorized GBM simulation (10,000 simulations × 63 days), percentile calculations, and random number generation with Student's t shocks;
> - **pandas** for time-series data organization and results aggregation;
> - **matplotlib** for publication-ready greyscale visualizations (price paths with percentile bands, return histograms with VaR cutoff, Q-Q plots, comparison bar charts);
> - **Jupyter notebooks** with full LaTeX formulas, detailed commented code, and bilingual output (English explanations, Indonesian tabular results for thesis alignment).

**Reproducibility & Generalization:** The Monte Carlo engine is fully stock-agnostic — simply change the `TICKER`, `START_DATE`, and `END_DATE` variables in Section 1, and the entire pipeline (log-returns, distribution testing, MLE, simulation, VaR) runs unchanged on any other stock listed on Yahoo Finance. All random seeds are locked (16221026) for full reproducibility.


---

## 📈 Author

**Fachlevi Asclumb** — Statistics graduate (2026), Institut Teknologi Kalimantan  

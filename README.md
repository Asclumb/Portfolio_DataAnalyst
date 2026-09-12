# Fachlevi Asclumb's Portfolio
Computational notebooks demonstrating statistical modeling, machine learning classification, and quantitative risk analysis. All notebooks are fully reproducible with locked random seeds and comprehensive visualizations.

---

#### 💸 [Financial Behavior Classification using XGBoost](https://colab.research.google.com/drive/1TsUnKwVKeduWpB0iswYQYgVw1RNUuChp?usp=sharing)
*Predicting Financial Profiles from Spending Habits Using Behavioral Ratios*

This notebook builds a machine learning classifier that predicts financial profiles (Hemat, Normal, Boros) from spending habits rather than income alone. Two people earning the same salary can end up with completely different financial profiles because personal discipline, not salary, drives the outcome. The pipeline includes data cleaning, feature engineering (Savings Rate, Wants Ratio, Needs Ratio), hyperparameter tuning using GridSearchCV, and performance evaluation through confusion matrices. The final tuned XGBoost model achieves over 85% accuracy on new data, with clear visual insights into spending behaviors and feature importance rankings.

**Key Tools & Libraries:**
> - **XGBoost** for gradient boosting classification with hyperparameter grid search;
> - **scikit-learn** for train and test split, LabelEncoder, and classification metrics (accuracy, precision, recall, F1);
> - **pandas & numpy** for data manipulation, ratio engineering, and numerical operations;
> - **matplotlib & seaborn** for clean greyscale visualizations (bar charts, scatter plots, confusion matrix, boxplots);
> - **Jupyter notebooks** with full inline markdown explanations and section by section walkthrough.

**Reproducibility:** The pipeline is fully reproducible across all sections. Simply change the dataset import path to run the same workflow on different financial datasets.

---

#### 📉 [Estimating Investment Risk for ANTM Stock Using Monte Carlo Simulation](https://colab.research.google.com/drive/18FZXWhEbTe6_ZkHaTLixR_wlVdp8JXXw?usp=sharing)
*Simulating Future Price Movements and Calculating Maximum Potential Loss*

This notebook is the computational appendix to an undergraduate thesis on quantitative risk management. It calculates the Value at Risk (potential maximum loss) for Indonesian mining stock ANTM using a Monte Carlo simulation engine. Because real stock market prices frequently experience sudden jumps and extreme events, the model uses Student's t distribution instead of the standard normal assumption. A simulation of 10,000 future price scenarios across multiple time horizons (1 day to 3 months) demonstrates how investment risk compounds over time, providing practical risk metrics for investors and fund managers.

**Key Tools & Libraries:**
> - **yfinance** for pulling historical daily closing prices from Yahoo Finance;
> - **scipy.stats** for distribution goodness of fit testing and parameter estimation;
> - **numpy** for running 10,000 simulated price paths and computing risk percentiles;
> - **pandas** for time series organization and summary tables;
> - **matplotlib** for clear visualizations including price projection cones, risk cutoff lines, and comparison bar charts;
> - **Jupyter notebooks** with complete formula explanations and bilingual results.

**Reproducibility:** The simulation engine works for any publicly traded stock. Simply change the ticker symbol and date range in Section 1 to run the analysis on any other company.

---

#### 🐦 [Twitter Web Scraping and Public Sentiment Analysis](./Twitter-OSINT-Sentiment/)
*Collecting 5,300+ Tweets and Analyzing Public Opinions Using Natural Language Processing*

This project demonstrates an automated data collection and text analysis pipeline that gathers public discussions from Twitter and evaluates community sentiment on major global news. By leveraging browser automation and token based extraction, the system successfully collected over 5,345 original English tweets without requiring costly enterprise API subscriptions. The text data was cleaned, normalized, and processed using Natural Language Processing (NLP) and VADER sentiment analysis to categorize public attitudes into positive, neutral, and negative perceptions, revealing key concerns regarding economic costs and calls for peace.

**Key Tools & Libraries:**
> - **Selenium WebDriver & Tweet-Harvest** for automated web browsing, session handling, and keyword search execution;
> - **pandas & regex (re)** for text cleaning, noise removal, and tabular structuring;
> - **NLTK (VADER & WordNet)** for vocabulary filtering, lemmatization, and sentiment polarity scoring;
> - **matplotlib, seaborn & WordCloud** for sentiment distribution charts and visual word clouds;
> - **Jupyter Notebooks** organized into clear steps covering scraping, data processing, and visual analysis.

**Reproducibility:** The search filters and keywords can be modified in minutes to track brand reputation, product feedback, or customer satisfaction for any business topic.

---

## 📈 Author

**Fachlevi Asclumb** — Statistics graduate (2026), Institut Teknologi Kalimantan  
NIM: 16221026
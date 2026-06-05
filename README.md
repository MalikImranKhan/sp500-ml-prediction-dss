# S&P 500 Directional Prediction — ML Comparison & Power BI DSS

**MSc Data Analytics Dissertation | London Metropolitan University | 2026**

## Project Overview

Comparative study of Random Forest and LSTM neural networks for predicting 
the next-day directional movement of the S&P 500 index. Model outputs 
deployed as an interactive Power BI Decision Support System for 
non-technical financial stakeholders.

## Research Question

Can machine learning models predict S&P 500 direction using multivariate 
features, and can their outputs be deployed as an accessible DSS?

## Key Results

| Model | Accuracy | P-Value | Sharpe Ratio | Final $1 |
|-------|----------|---------|--------------|----------|
| Random Forest (Tuned) | 48.50% | 0.763 | -0.23 | $0.93 |
| LSTM + Class Weights (Final) | 49.90% | 0.536 | +0.29 | $1.07 |

Neither model achieved statistical significance (p > 0.05) — confirming 
the Efficient Market Hypothesis on the world's most efficiently priced index.

## Key Discovery — Class Imbalance Problem

The LSTM initially predicted UP on every single day (Down Recall = 0%).
Three controlled experiments identified and resolved this:

- **Experiment A** — Price only → lazy model confirmed
- **Experiment B** — All 5 features → still lazy (features not the solution)
- **Experiment C** — Class weighting → genuine binary classifier ✅

## Features Used

| Feature | Description | Why Chosen |
|---------|-------------|------------|
| Close Price | Daily SPY closing price | Price momentum baseline |
| Volume | Daily trading volume | Market conviction |
| VIX | CBOE Volatility Index | Forward-looking fear gauge |
| TNX | 10-Year Treasury Yield | Macroeconomic environment |
| RSI (14-day) | Relative Strength Index | Momentum — most important (0.2199) |

## Methodology

- **Framework:** CRISP-DM
- **Data:** 10 years daily data (Jan 2014 – Dec 2023), 2,502 observations
- **Train/Test Split:** 80/20 chronological (no random shuffle)
- **Validation:** 5-fold walk-forward validation
- **RF Sensitivity:** 12 combinations (3 windows × 4 tree counts)
- **LSTM Sensitivity:** 3 window sizes (5, 10, 22 days)
- **Both models independently selected 10-day window as optimal**

## Tech Stack
Python · TensorFlow · Keras · Scikit-learn · Pandas · NumPy
SQL (SQLite) · Power BI · Google Colab (GPU)

## Power BI Dashboard — 4 Pages

1. **Model Overview** — KPI cards, accuracy comparison bar chart
2. **Equity Curves** — Portfolio growth over test period
3. **Trading Signals** — Daily BUY/HOLD recommendations with actual outcomes
4. **Model Deep Dive** — Sensitivity heatmap, feature importance, training history

## How to Run

1. Open `Dissertation_Complete_7_.ipynb` in Google Colab
2. Runtime → Run all
3. Download the generated CSV files
4. Load CSVs into Power BI Desktop

## Author

**Imran Khan** | MSc Data Analytics | London Metropolitan University  
[LinkedIn](https://linkedin.com/in/imrankhan151)

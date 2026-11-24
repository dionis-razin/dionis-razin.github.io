# Monte Carlo Portfolio Risk Simulation

Python implementation of a Monte Carlo simulation to estimate 1-month portfolio tail risk (**95% Value at Risk** and **Expected Shortfall**) and demonstrate how rising asset correlations break diversification during market stress.

## Overview
- **Data & Parameters:** Downloads daily closing prices via `yfinance` and computes daily returns, annualized return/volatility, and the historical correlation matrix.
- **Correlated Simulation:** Generates 10,000 1-month (21 trading days) return paths in `NumPy` using **Cholesky decomposition** to preserve empirical correlations between assets.
- **Risk Metrics:** Computes **95% VaR** (5th percentile loss) and **95% Expected Shortfall / CVaR** (average loss across the worst 5% of scenarios).
- **Correlation Stress Test:** Shifts the correlation matrix toward `1.0` to quantify non-linear risk scaling when diversification fails.
- **Visualizations:** Correlation heatmap (`seaborn`) and simulated return distribution with VaR/ES thresholds (`matplotlib`).

## Portfolio & Data
- **Assets:** Equally weighted (20% each) across 5 US equities: `AAPL`, `MSFT`, `GOOGL`, `JPM`, `XOM`.
- **Period:** January 2024 – November 2026 (daily closing prices via `yfinance`).

## Key Results
- **Baseline 95% VaR (1-month):** `-[XX.XX]%`
- **Baseline 95% Expected Shortfall (1-month):** `-[XX.XX]%`
- **Stress Test:** Increasing average pairwise correlation from `[0.XX]` to `[0.XX]` raised 95% VaR by `+[XX.X]%`.

## How to Run
1. Open `monte_carlo_portfolio_risk.ipynb` in **Google Colab** (click the badge at the top of the notebook) or locally in Jupyter / VS Code.
2. If running locally, install the required libraries:
   ```bash
   pip install yfinance numpy pandas matplotlib seaborn

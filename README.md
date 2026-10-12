# Pairs Trading Monte Carlo – Coca-Cola vs PepsiCo

Numerical Methods in Finance – Project 1

This project analyzes a pairs trade between Coca-Cola (KO) and PepsiCo (PEP) using Monte Carlo simulation.

The trade consists of:

- Long USD 100,000 of PEP
- Short USD 100,000 of KO
- USD 100,000 initial cash earning 5% annually

The objective is to simulate 1,000,000 daily paths over a 60-trading-day horizon and study the effect of correlation and mean reversion on the trade.

## Methodology

Historical KO and PEP data are obtained using Yahoo Finance.

Model parameters are estimated using historical data available before the trade entry date to avoid look-ahead bias. A 5-year calibration window is used as the baseline, with 2-year and 10-year windows considered as sensitivity checks.

Three models are compared:

1. Independent random walks
2. Correlated random walks using Cholesky decomposition
3. A local Ornstein-Uhlenbeck mean-reversion scenario for the relative price

The correlated random walk is used as the baseline model.

## Main findings

KO and PEP daily returns exhibit strong positive correlation, with a 5-year estimate of approximately 0.68.

The historical relative price does not provide strong evidence of stationarity around a fixed long-run level, so mean reversion is treated as an alternative scenario rather than the main forecasting assumption.

For the October 9 to October 16 valuation under the correlated random walk:

- Expected pairs-trade P&L: approximately -USD 258
- Expected total P&L including cash interest: approximately -USD 158
- 5th percentile total P&L: approximately -USD 3,502
- 95th percentile total P&L: approximately +USD 3,212

A local z-score is used to define the entry and exit rule.

The OU model produces a substantially more positive expected P&L, illustrating that the result is highly sensitive to the mean-reversion assumption. This highlights model risk as an important part of the analysis.

## Files

- `pairs_trading.ipynb` – full analysis and Monte Carlo simulation
- `KO_PEP_Pairs_Trading_Slides.pptx` – 3-slide project summary

## Python libraries

The analysis uses:

`numpy`, `pandas`, `matplotlib`, `scipy`, `statsmodels`, and `yfinance`.

## Disclaimer

This project was completed for academic purposes and is not investment advice.

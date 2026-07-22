# Multi-Asset Portfolio Optimization and Robustness Analysis

## Overview

This project examines portfolio construction across a diversified ETF universe using mean-variance optimization, allocation constraints, rolling out-of-sample testing, and bootstrap resampling.

The objective is not only to identify portfolios with attractive historical risk-return characteristics, but also to test how sensitive optimized allocations are to estimation error and changing market conditions.

## Asset Universe

The analysis uses nine ETFs representing multiple asset classes:

- SPY: U.S. equities
- QQQ: U.S. technology / growth
- EFA: Developed international equities
- EEM: Emerging-market equities
- TLT: Long-term U.S. Treasuries
- LQD: Investment-grade corporate bonds
- GLD: Gold
- VNQ: Real estate
- DBC: Broad commodities

The main analysis uses historical adjusted prices from January 2010 through December 2025.

## Methodology

The notebook includes:

- Historical return, volatility, and correlation analysis
- Equal-weight portfolio benchmarking
- Long-only minimum-variance and maximum-Sharpe optimization
- Efficient-frontier construction
- Comparison of baseline portfolios with 5%-35% allocation constraints
- Simulation of 30,000 random portfolios
- Performance evaluation using annualized return, volatility, Sharpe ratio, and maximum drawdown
- Rolling out-of-sample testing using a two-year estimation window and 21-trading-day re-optimization intervals
- Bootstrap resampling with 300 samples to evaluate portfolio-weight sensitivity to estimation error

## Key Results

- Baseline maximum-Sharpe optimization produced concentrated allocations, while 5%-35% allocation bounds reduced concentration at the cost of some estimated in-sample efficiency.
- In the rolling out-of-sample backtest, the constrained maximum-Sharpe strategy improved the Sharpe ratio from 0.75 for the equal-weight benchmark to 0.90.
- Maximum drawdown improved from 22.85% for equal weight to 19.60% for the rolling constrained strategy.
- SPY produced the highest absolute return over the evaluation period, but with higher volatility and a deeper drawdown.
- Bootstrap analysis showed that optimized portfolio weights remain sensitive to estimation error. Allocation constraints reduced weight variability for most assets and limited extreme portfolio shifts.

## Repository Structure

- `portfolio_analysis_final.ipynb` - Full analysis, optimization, backtesting, visualizations, and conclusions
- `README.md` - Project overview and key findings

## Tools

Python libraries used:

- NumPy
- pandas
- SciPy
- Matplotlib
- Seaborn
- yfinance

## Limitations

The analysis does not include transaction costs, taxes, or a nonzero risk-free rate. The rolling strategy relies on historical estimates of expected returns and covariance. Bootstrap samples are drawn independently from daily historical returns and therefore do not preserve serial dependence.

Potential extensions include transaction-cost modeling, covariance shrinkage, alternative expected-return models, and block bootstrap methods.

## Disclaimer

This project is for educational and research purposes only and does not constitute investment advice.

# Project-MMA823---Algorithmic-Trading-Financial-Analytics-
This project explores a statistical arbitrage strategy known as **Pairs Trading**. By identifying historically correlated tech stocks within the S&P 500, the project implements a mean-reverting long-short trading approach using Python.


## Overview
**Objective:**  
Build and evaluate a Pairs Trading strategy using daily adjusted close prices of selected tech sector stocks from the S&P 500 index.

**Approach:**
- Identify pairs of tech stocks with high historical correlation.
- Use the spread (difference in price) between pairs to detect trading signals.
- Simulate buy/sell decisions when the spread diverges from its mean, expecting eventual convergence.


## Key Components
### 1. Data Collection
- S&P 500 tech stock tickers fetched from Wikipedia
- Historical stock price data pulled using `yfinance`

### 2. Pairs Identification
- Calculate Pearson correlation between all tech stock pairs
- Filter for highly correlated pairs (e.g., correlation > 0.9)

### 3. Trading Logic
- Compute price spreads between pairs
- Define entry/exit thresholds based on z-scores
- Backtest the strategy with simple long-short logic

### 4. Performance Evaluation
- Track cumulative returns and visualize performance
- Compare to a buy-and-hold benchmark


## Tech Stack
- Python
- pandas, numpy
- matplotlib, seaborn
- yfinance
- statsmodels
- Jupyter Notebook


## 📁 Repository Structure
├── MMA823_Final_Project.ipynb # Main notebook implementing the strategy
├── README.md # Project overview
└── Algo Trading_ver1.pptx # Presentation explaining the entire Project
└── MMA 823 Project Report_Final.pdf # Project Report


## Results Summary
- Identified multiple highly correlated stock pairs (e.g., AAPL-MSFT)
- Strategy shows promising mean-reversion behavior under simulated backtesting
- Highlights risks such as false signals and lagging convergence


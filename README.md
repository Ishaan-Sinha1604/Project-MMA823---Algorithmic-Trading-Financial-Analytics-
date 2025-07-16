# Project-MMA823---Algorithmic-Trading-Financial-Analytics-
This project explores a statistical arbitrage strategy known as **Pairs Trading**. By identifying historically correlated tech stocks (**time-series data**) within the S&P 500, the project implements a mean-reverting long-short trading approach using Python.

---
## Overview
**Objective:**  
Build and evaluate a Pairs Trading strategy using daily adjusted close prices of selected tech sector stocks from the S&P 500 index.

**Approach:**
- Identify pairs of tech stocks with high historical correlation.
- Use the spread (difference in price) between pairs to detect trading signals.
- Simulate buy/sell decisions when the spread diverges from its mean, expecting eventual convergence.

---
## Key Components
### 1. Data Collection
- S&P 500 tech stock tickers fetched from Wikipedia
- Historical stock price data pulled using `yfinance`

### 2. Pairs Identification
- Identify pairs of tech stocks with high historical **cointegration**, i.e., they share a long-term statistical relationship, even if they are non-stationary individually
- Select stock pairs with lowest **p-value** in the cointegration test. This indicates a strong chance that these stocks are statistically related historically
- Pick one stock pair from these. We chose Microsoft (MSFT) and Accenture (ACN)
- Calculate the **spread** between the pair
- Perform **Augmented Dickey-Fuller (ADF) test** to determine whether the spread is stationary over time or not

### 3. Feature Engineering
- Calculate ratio of prices of the pair of stocks. We calculated ACN/MSFT (ratio of Accenture to Microsoft stock prices)
- Calculate 60 day Moving Average of Ratio, 5 day Moving Average of Ratio, 60 day Standard Deviation
- Calculate the **Z-Score**: how many standard deviations the short-term MA is from the long-term MA

### 4. Trading Strategy
- `zscore > 1` : ratio is high - short the ratio (short Accenture, long Microsoft)
- `zscore < -1` : ratio is low → long the ratio (long Accenture, short Microsoft)
- Exit positions when the z-score approaches zero
- Add a stoploss if portfolio value reaches below 80% of the initial amount
- Backtest the strategy with simple long-short logic

### 5. Model Tuning
- Split data into training set (80%) and testing set (20%)
- Create a Function to simulate the trading strategy and manage portfolio positions
- Run this function for multiple values of long term MAs on the training set
- Select the best long term MA value (in our case it was 56)
- Test this window length on testing set

### 4. Performance Evaluation
- Simulate the trading strategy
- Track cumulative returns and visualize performance
- Compare to S&P 500 Index growth
  
---
## Tech Stack
- Python
- pandas, numpy
- matplotlib, seaborn
- yfinance
- statsmodels
- Jupyter Notebook

---
## Repository Structure
```
├── MMA823_Final_Project.ipynb           # Main notebook implementing the strategy
├── README.md                            # Project overview
└── Algo Trading_ver1.pptx               # Presentation explaining the entire Project
└── MMA 823 Project Report_Final.pdf     # Project Report
```
---
## Results Summary
- Over a 2-year simulation period, the strategy resulted in a $5015 incrase in portfolio value
- This is 50% increase in 2 years
- A total of 44 trades were made throughout this period
- There is not a single point when a significant drop is observed in the net portfolio value
- S&P 500 Index grew about 25% during this time period

---

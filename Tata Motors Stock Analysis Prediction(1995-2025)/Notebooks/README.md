1. Overview

Historical daily stock market data for Tata Motors Limited listed on NSE India
Covers 30 years of trading data from 1995 to 2025
Intended for financial analysis, time-series modelling, and stock price prediction


2. File Details

File Name: Tata Motors Stock Analysis Prediction(1995-2025).csv
Format: CSV (Comma-Separated Values)
Frequency: Daily (trading days only)
Time Period: 1995 – 2025
Exchange: NSE (National Stock Exchange of India)
Stock: Tata Motors Limited


3. Column Descriptions

Index — Row index, renamed from Unnamed: 0
Date — Trading date in YYYY-MM-DD format
Symbol — NSE ticker symbol of the stock
Open — Opening price on that trading day (₹)
High — Highest price reached during the day (₹)
Low — Lowest price reached during the day (₹)
Close — Closing price at end of trading day (₹)
Volume — Total number of shares traded during the day
Turnover — Total value of shares traded (Volume × Price) in ₹
Trades — Number of individual trade transactions executed
Daily_Return_% — Percentage change in closing price from previous day
MA_20 — 20-day simple moving average of closing price
MA_50 — 50-day simple moving average of closing price
Month — Month extracted from the Date column (1–12)
Year — Year extracted from the Date column
Cumulative — Cumulative return product from the start date
Peak — Running maximum of cumulative return
Drawdown — Difference between cumulative return and its peak


4. Key Statistics

Closing Price Range: ₹70 – ₹1,150+
Typical Price Zone (IQR): ₹270 – ₹500
Median Closing Price: ~₹400
Distribution Shape: Positively skewed with high kurtosis — long right tail with extreme upper outliers
Volatility: High — 10x price spread over the full period
Volume Range: Up to 400 million shares traded in a single day


5. Data Quality Notes

Missing Values: Present in the raw file — rows with nulls were dropped during preprocessing
Duplicates: Checked and confirmed minimal or none
Outliers: Significant upper-end outliers in Close (above ₹900) detected via Z-score (|z| > 3) — these reflect real market events, not data errors
OHLC Redundancy: Open, High, Low, Close are highly correlated (~0.99) — using all four together may cause multicollinearity in models
Daily Returns: Mostly independent and noisy — low correlation with price or volume variables


6. Derived / Engineered Columns
These were computed during analysis and are not part of the original raw file:

Daily_Return_% — Percentage return from the previous trading day's close
MA_20 / MA_50 — Rolling moving averages for trend detection
Cumulative — Compounded return from the first date: (1 + Daily_Return_%/100).cumprod()
Peak — Running maximum of cumulative return to track all-time highs
Drawdown — Deviation from peak, representing loss from the highest point
Month / Year — Datetime features extracted for seasonality analysis


7. Suggested Use Cases

Time-Series Forecasting — Predict future closing prices using ARIMA, LSTM, or Prophet
Trend Analysis — Study long-term market regimes using moving averages and drawdown patterns
Volatility Modelling — Apply GARCH or rolling std to model risk over time
Seasonality Detection — Use monthly heatmaps to identify return patterns across calendar months
Feature Engineering — Derive RSI, Bollinger Bands, MACD from OHLCV columns for ML pipelines
Portfolio Risk Analysis — Use drawdown and cumulative return for risk-adjusted performance metrics


8. Important Notes

All prices are in Indian Rupees (₹)
Data covers trading days only — weekends and market holidays are excluded
Dataset reflects unadjusted prices — no stock split or dividend adjustments applied
For accurate return modelling, use log returns instead of simple percentage returns due to the non-normal distribution

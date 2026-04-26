1. Overviewevents, not data errors

OHLC Redundancy: Open, High, Low, Close are highly correlated (~0.99) — using all four together may cause multicollinearity in models

Daily Returns: Mostly independent and noisy — low correlation with price or volume variables


6. Derived / Engineered Columns
 
Daily_Return_% — Percentage return from the previous trading day's close

MA_20 / MA_50 — Rolling moving averages for trend detection

Cumulative — Compounded return from the first date: (1 + Daily_Return_%/100).cumprod()

Peak — Running maximum of cumulative return to track all-time highs

Drawdown — Deviation from peak, representing loss from the highest point

Month / Year — Datetime features extracted for seasonality analysis


8. Suggested Use Cases

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

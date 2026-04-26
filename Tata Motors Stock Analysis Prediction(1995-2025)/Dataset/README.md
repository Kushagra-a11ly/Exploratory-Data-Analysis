![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/48789243202a0a26b9dad8cd49b822d5e4840b38/Tata%20Motors%20Stock%20Analysis%20Prediction(1995-2025)/dataset-cover.png)





Tata Motors Stock Price Dataset (1995–2025)

## 1. Introduction

1. This dataset contains historical stock price data for Tata Motors Limited (NSE: TATAMOTORS) spanning from January 1995 to August 2025.
2. The data is sourced from the National Stock Exchange (NSE) of India and includes detailed daily trading information along with derived technical indicators.
3. It is designed for time-series analysis, financial modeling, and machine learning applications.


## 2. Dataset Composition

| Attribute | Detail |
|-----------|--------|
| Exchange | National Stock Exchange of India (NSE) |
| Ticker Symbol | TATAMOTORS |
| Asset Class | Equity — Large Cap / NIFTY 50 Constituent |
| Data Frequency | Daily (per trading session) |
| Coverage Period | January 1995 – August 2025 |
| Approximate Row Count | ~7,500 trading sessions |
| Total Feature Columns | 14 |
| Missing Values | None (post-cleaning) |
| File Format | CSV (UTF-8 encoded) |

---

## 3. Feature Reference

### 3.1 Market Price Data

| Column | Type | Description |
|--------|------|-------------|
| `Date` | Date | Trading session date aligned to NSE market calendar. Format: `YYYY-MM-DD`. |
| `Symbol` | String | NSE ticker — consistently `TATAMOTORS` across all rows. |
| `Open` | Float (₹) | First executed trade price at session open. |
| `High` | Float (₹) | Highest traded price during the session. |
| `Low` | Float (₹) | Lowest traded price during the session. |
| `Close` | Float (₹) | Official NSE closing price at end of session. |
| `PrevClose` | Float (₹) | Prior session's closing price; basis for return calculation. |

### 3.2 Volume & Market Microstructure

| Column | Type | Description |
|--------|------|-------------|
| `Volume` | Integer | Total shares traded during the session. Measures liquidity and participation. |
| `Turnover` | Float (₹) | Aggregate monetary value of all trades executed during the session. |
| `VWAP` | Float (₹) | Volume Weighted Average Price — total turnover ÷ total volume. Standard institutional execution benchmark. |
| `Trades` | Integer | Number of discrete order matches in the session. Proxy for market depth beyond raw volume. |

### 3.3 Derived & Technical Features

| Column | Type | Description |
|--------|------|-------------|
| `Daily_Return_%` | Float | Session return: percentage change from `PrevClose` to `Close`. |
| `Cumulative_Return_%` | Float | Running compounded return indexed from the first record in the dataset. |
| `MA_20` | Float (₹) | 20-session simple moving average of `Close`. Short-term trend and momentum indicator. |
| `MA_50` | Float (₹) | 50-session simple moving average of `Close`. Medium-term trend; used in crossover systems. |

---

## 4. Use Cases

- **Time-Series Forecasting** — Train ARIMA, SARIMA, LSTM, GRU, or Temporal Fusion Transformer models on 30 years of daily close data spanning structurally distinct market regimes.
- **Algorithmic Strategy Backtesting** — Backtest moving average crossover systems, momentum strategies, mean-reversion signals, and volume-confirmation filters against authentic exchange-sourced history.
- **ML for Return Prediction** — Use OHLCV, VWAP, trade counts, and moving averages as raw features or inputs to custom feature engineering pipelines for directional or return-magnitude models.
- **Volatility & Risk Analysis** — Compute rolling volatility, historical VaR, CVaR, maximum drawdown profiles, and Sharpe/Sortino ratios across multiple investment horizons.
- **Exploratory Data Analysis** — Analyse price trends, volume seasonality, return distributions, autocorrelation structure, and long-run performance attribution.
- **Academic & Financial Research** — Supports event studies, emerging market equity research, microstructure-to-price-outcome analysis, and long-run return attribution in the Indian market context.

---

## 5. Getting Started

### Prerequisites

```bash
pip install pandas matplotlib
```

### Load & Explore

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('tatamotors_historical.csv', parse_dates=['Date'])
df.set_index('Date', inplace=True)

# Quick overview
print(df.shape)       # (~7500, 13)
print(df.head())
print(df.describe())
```

### Plot Closing Price with Moving Averages

```python
fig, ax = plt.subplots(figsize=(14, 5))
ax.plot(df['Close'], label='Close', linewidth=0.9)
ax.plot(df['MA_20'], label='MA 20', linewidth=1.2)
ax.plot(df['MA_50'], label='MA 50', linewidth=1.2)
ax.legend()
ax.set_title('TATAMOTORS — Daily Close with Moving Averages (1995–2025)')
plt.tight_layout()
plt.show()
```

![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/48789243202a0a26b9dad8cd49b822d5e4840b38/Tata%20Motors%20Stock%20Analysis%20Prediction(1995-2025)/dataset-cover.png)

# Tata Motors Limited — Historical Daily Stock Price Dataset

**Exchange:** NSE India &nbsp;|&nbsp; **Ticker:** TATAMOTORS &nbsp;|&nbsp; **Period:** January 1995 – August 2025 &nbsp;|&nbsp; **Format:** CSV &nbsp;|&nbsp; **License:** CDLA-Permissive-2.0

---

## Table of Contents

1. [Overview](#1-overview)
2. [About Tata Motors](#2-about-tata-motors)
3. [Dataset Composition](#3-dataset-composition)
4. [Feature Reference](#4-feature-reference)
5. [Use Cases](#5-use-cases)
6. [Getting Started](#6-getting-started)
7. [Notes & Considerations](#7-notes--considerations)
8. [License](#8-license)

---

## 1. Overview

- Compiled from **official NSE records**, covering every trading session from **January 1995 to August 2025**.
- Contains over **7,500 daily trading sessions** of OHLCV data, microstructure metrics, and pre-computed technical indicators.
- Data is **fully cleaned and enriched** — no missing values, no imputed or synthetic entries.
- Structured for immediate use in **quantitative research, financial modelling, and machine learning** workflows.
- Captures 30 years of market history including bull markets, financial crises, corporate restructuring cycles, and the ongoing EV transition.

---

## 2. About Tata Motors

- **Tata Motors Limited** is the automotive flagship of the Tata Group — one of India's oldest and most diversified industrial conglomerates.
- Headquartered in **Mumbai**, with a product portfolio spanning passenger vehicles, commercial trucks, electric vehicles, and premium brands via its subsidiary **Jaguar Land Rover (JLR)**.
- A constituent of the **NIFTY 50** index, making it one of the most liquid and institutionally traded equities on the NSE.
- The 30-year price history in this dataset covers all major market-moving events:

  | Period | Event |
  |--------|-------|
  | Late 1990s | Post-liberalisation bull market |
  | 2000–2001 | Dot-com correction |
  | 2008 | Global financial crisis & JLR acquisition |
  | 2011–2016 | JLR-linked debt cycle |
  | 2020–2021 | COVID-19 shock and recovery |
  | 2022–2025 | EV re-rating & JLR return to profitability |

---

## 3. Dataset Composition

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

## 4. Feature Reference

### 4.1 Market Price Data

| Column | Type | Description |
|--------|------|-------------|
| `Date` | Date | Trading session date aligned to NSE market calendar. Format: `YYYY-MM-DD`. |
| `Symbol` | String | NSE ticker — consistently `TATAMOTORS` across all rows. |
| `Open` | Float (₹) | First executed trade price at session open. |
| `High` | Float (₹) | Highest traded price during the session. |
| `Low` | Float (₹) | Lowest traded price during the session. |
| `Close` | Float (₹) | Official NSE closing price at end of session. |
| `PrevClose` | Float (₹) | Prior session's closing price; basis for return calculation. |

### 4.2 Volume & Market Microstructure

| Column | Type | Description |
|--------|------|-------------|
| `Volume` | Integer | Total shares traded during the session. Measures liquidity and participation. |
| `Turnover` | Float (₹) | Aggregate monetary value of all trades executed during the session. |
| `VWAP` | Float (₹) | Volume Weighted Average Price — total turnover ÷ total volume. Standard institutional execution benchmark. |
| `Trades` | Integer | Number of discrete order matches in the session. Proxy for market depth beyond raw volume. |

### 4.3 Derived & Technical Features

| Column | Type | Description |
|--------|------|-------------|
| `Daily_Return_%` | Float | Session return: percentage change from `PrevClose` to `Close`. |
| `Cumulative_Return_%` | Float | Running compounded return indexed from the first record in the dataset. |
| `MA_20` | Float (₹) | 20-session simple moving average of `Close`. Short-term trend and momentum indicator. |
| `MA_50` | Float (₹) | 50-session simple moving average of `Close`. Medium-term trend; used in crossover systems. |

---

## 5. Use Cases

- **Time-Series Forecasting** — Train ARIMA, SARIMA, LSTM, GRU, or Temporal Fusion Transformer models on 30 years of daily close data spanning structurally distinct market regimes.
- **Algorithmic Strategy Backtesting** — Backtest moving average crossover systems, momentum strategies, mean-reversion signals, and volume-confirmation filters against authentic exchange-sourced history.
- **ML for Return Prediction** — Use OHLCV, VWAP, trade counts, and moving averages as raw features or inputs to custom feature engineering pipelines for directional or return-magnitude models.
- **Volatility & Risk Analysis** — Compute rolling volatility, historical VaR, CVaR, maximum drawdown profiles, and Sharpe/Sortino ratios across multiple investment horizons.
- **Exploratory Data Analysis** — Analyse price trends, volume seasonality, return distributions, autocorrelation structure, and long-run performance attribution.
- **Academic & Financial Research** — Supports event studies, emerging market equity research, microstructure-to-price-outcome analysis, and long-run return attribution in the Indian market context.

---

## 6. Getting Started

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

---

## 7. Notes & Considerations

- **Moving Average Warm-Up Removed** — The first 50 rows (where `MA_20` and `MA_50` carry `NaN` values due to their look-back window requirements) have been excluded. All retained rows are fully populated across every column.
- **No Imputation Applied** — Price, volume, and turnover columns reflect official NSE-published figures without any imputation, interpolation, or forward-filling. No synthetic or estimated values are present.
- **Return Calculation Basis** — `Daily_Return_%` and `Cumulative_Return_%` are derived directly from NSE-recorded `Close` and `PrevClose` values. No adjustments for dividends, bonus issues, or rights entitlements have been applied beyond what is already reflected in official NSE records.
- **Corporate Action Advisory** — Users constructing long-run return series or comparing absolute price levels across distant periods should independently verify the full corporate action history of TATAMOTORS (splits, bonuses, rights issues) to ensure price-level continuity where required by their methodology.
- **Market Calendar Alignment** — Dates are aligned to the NSE trading calendar. Weekends, public holidays, and exchange-declared market closures are excluded from the dataset.

---

## 8. License

This dataset is released under the **[Community Data License Agreement (CDLA) — Permissive, Version 2.0](https://cdla.dev/permissive-2-0/)**.

- Free to use for research, education, and non-commercial applications.
- Modification and redistribution permitted with attribution.
- Data sourced from the **National Stock Exchange of India (NSE)**.
- All rights in the original exchange data remain with NSE.

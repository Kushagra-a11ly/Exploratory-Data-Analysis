# Tata Motors Limited — Stock Analysis & Prediction (1995–2025)


> **Exploratory Data Analysis (EDA)** on 30 years of daily stock data for Tata Motors Limited (NSE: TATAMOTORS) — covering price structure, volume behavior, return seasonality, market microstructure, and drawdown risk across ~7,500 trading sessions.

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Dataset Summary](#2-dataset-summary)
3. [Feature Reference](#3-feature-reference)
4. [Tools & Libraries](#4-tools--libraries)
5. [Data Cleaning & Preprocessing](#5-data-cleaning--preprocessing)
6. [Analysis & Visualisations](#6-analysis--visualisations)
   - [Closing Price Distribution](#61-closing-price-distribution)
   - [Outlier Analysis](#62-outlier-analysis)
   - [Volume vs. Closing Price](#63-volume-vs-closing-price)
   - [Correlation Heatmap](#64-correlation-heatmap)
   - [Pairplot Analysis](#65-pairplot-analysis)
   - [Price Trend & Moving Averages](#66-price-trend--moving-averages)
   - [Monthly Return Heatmap](#67-monthly-return-heatmap)
   - [Trades vs. Price vs. Volume](#68-trades-vs-price-vs-volume)
   - [Drawdown Analysis](#69-drawdown-analysis)
7. [Statistical Summary](#7-statistical-summary)
8. [Consolidated Findings](#8-consolidated-findings)
9. [Recommended Next Steps](#9-recommended-next-steps)
10. [How to Run](#10-how-to-run)
11. [Repository Structure](#11-repository-structure)
12. [License](#12-license)

---

## 1. Project Overview

- End-to-end **Exploratory Data Analysis** on Tata Motors Limited daily stock price data spanning **January 1995 to August 2025**.
- Analyses **price structure, volume behaviour, return seasonality, market microstructure, and drawdown risk** across three decades of NSE exchange-sourced data.
- Designed as a **foundation for downstream tasks** including time-series forecasting, algorithmic strategy backtesting, and machine learning model development.
- Covers all major market-defining events in the stock's history:

  | Period | Event |
  |--------|-------|
  | Late 1990s | Post-liberalisation bull market |
  | 2000–2001 | Dot-com correction |
  | 2008 | Global financial crisis & JLR acquisition |
  | 2011 | Eurozone sovereign debt crisis |
  | 2020–2021 | COVID-19 crash and stimulus-driven recovery |
  | 2022–2025 | EV structural re-rating & JLR return to profitability |

---

## 2. Dataset Summary

| Attribute | Detail |
|-----------|--------|
| **Exchange** | National Stock Exchange of India (NSE) |
| **Ticker Symbol** | TATAMOTORS |
| **Asset Class** | Equity — Large Cap / NIFTY 50 Constituent |
| **Data Frequency** | Daily (per trading session) |
| **Coverage Period** | January 1995 – August 2025 |
| **Approximate Rows** | ~7,500 trading sessions |
| **Feature Columns** | 14 |
| **Missing Values** | None (post-cleaning) |
| **File Format** | CSV (UTF-8 encoded) |

---

## 3. Feature Reference

### Market Price Data

| Column | Type | Description |
|--------|------|-------------|
| `Date` | Date | Trading session date — format `YYYY-MM-DD`, aligned to NSE calendar |
| `Symbol` | String | NSE ticker — consistently `TATAMOTORS` across all rows |
| `Open` | Float (₹) | First executed trade price at session open |
| `High` | Float (₹) | Highest traded price during the session |
| `Low` | Float (₹) | Lowest traded price during the session |
| `Close` | Float (₹) | Official NSE closing price at end of session |
| `PrevClose` | Float (₹) | Prior session's closing price; basis for return calculation |

### Volume & Market Microstructure

| Column | Type | Description |
|--------|------|-------------|
| `Volume` | Integer | Total shares traded during the session |
| `Turnover` | Float (₹) | Aggregate monetary value of all trades executed |
| `VWAP` | Float (₹) | Volume Weighted Average Price — total turnover ÷ total volume |
| `Trades` | Integer | Number of discrete order matches per session |

### Derived & Technical Features

| Column | Type | Description |
|--------|------|-------------|
| `Daily_Return_%` | Float | Percentage change from `PrevClose` to `Close` |
| `Cumulative_Return_%` | Float | Running compounded return indexed from first record |
| `MA_20` | Float (₹) | 20-session simple moving average of `Close` |
| `MA_50` | Float (₹) | 50-session simple moving average of `Close` |

---

## 4. Tools & Libraries

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, manipulation, resampling, and aggregation |
| `numpy` | Numerical operations, z-score computation, masking |
| `matplotlib` | Line charts, trend plots, drawdown visualisation |
| `seaborn` | Statistical plots — histograms, boxplots, heatmaps, pairplots, scatterplots |
| `scipy.stats` | Skewness, kurtosis, and z-score outlier detection |

---

## 5. Data Cleaning & Preprocessing

| Step | Action |
|------|--------|
| **Missing Value Check** | `df.isnull().sum()` — identified columns with null entries before cleaning |
| **Column Removal** | `Unnamed: 0` index column dropped via `df.drop(columns=['Unnamed: 0'])` |
| **Trades Imputation** | `Trades` column filled using forward-fill then back-fill (`ffill` / `bfill`) |
| **MA Recalculation** | `MA_20` and `MA_50` recomputed using `rolling(20/50, min_periods=1).mean()` on `Close` |
| **Date Parsing** | `Date` converted to datetime using `pd.to_datetime(df['Date'], dayfirst=True)` |
| **Feature Extraction** | `Month` and `Year` extracted from `Date` for temporal and seasonal analysis |
| **Post-clean Validation** | `isnull().sum()` re-run after all steps — confirmed zero missing values |

**Exploratory checks performed:**
- `df.head()` / `df.tail()` — structural consistency check
- `df.shape` — confirmed ~7,500 rows × 14 columns
- `df.info()` — validated data types and non-null counts
- `df.describe()` — statistical summary of all numerical columns
- `df['Symbol'].value_counts()` — confirmed single symbol throughout
- `df.corr(numeric_only=True)` — full correlation matrix
- `df.memory_usage()` — dataset memory footprint
- `df.sample(5)` — random row sampling for sanity checks

---

## 6. Analysis & Visualisations

### 6.1 Closing Price Distribution

**Chart:** Histogram with KDE (`sns.histplot`)

(img_alt)[Closing Price Distribution](images/01_closing_price_distribution.png)

**Key Insights:**
- Multi-modal distribution with distinct peaks at ₹150–250, ₹350–500, and ₹900–1,050 — each represents a separate market regime across the 30-year history.
- The ₹300–500 range is the stock's historical **fair value zone**, where price acceptance, liquidity, and consolidation have been consistently highest.
- Strong **positive skewness** — rare upside spikes inflate the mean above the median; extreme gains are infrequent but material.
- A 14× price spread (₹100 to ₹1,400+) confirms extreme long-run volatility and sensitivity to macro events and corporate developments.
- The non-normal, multi-peaked shape is incompatible with Gaussian assumptions — **regime-switching models, log transformations, or quantile-based methods** are required for analytical work.

---

### 6.2 Outlier Analysis

**Chart:** Boxplot (`sns.boxplot`) + z-score method (`scipy.stats.zscore`, threshold ±3)

![Outlier Analysis](images/02_outlier_analysis.png)

**Key Insights:**
- Median closing price ≈ ₹400; IQR spans ₹270–₹530 — 50% of all trading sessions fall within this ₹260 band.
- Numerous high-end outliers cluster above ₹850, indicating frequent speculative surges relative to the central distribution.
- The lower whisker is compressed vs. the upper, reflecting **asymmetric volatility** — upside extremes are more frequent and severe than downside ones.
- Outliers above ₹900 flagged by z-score > 3 correspond to statistically exceptional price levels tied to specific macro or corporate events.
- Positive skewness in the boxplot is fully consistent with histogram findings in Section 6.1.

---

### 6.3 Volume vs. Closing Price

**Chart:** Scatterplot (`sns.scatterplot`)

![Volume vs Closing Price](images/03_volume_vs_price.png)

**Key Insights:**
- All-time price highs (₹800–₹1,400) occur almost exclusively at **low-to-moderate volume** — price peaks were not participation-driven; they emerged during institutionally-quiet sessions.
- The densest cluster lies in ₹100–₹400 with widely scattered volume — broad retail participation occurs at lower valuations.
- Even at very high volumes (200M–400M shares), prices remain in the ₹150–₹350 range — volume surges do not generate proportional price increases.
- Clear **heteroscedasticity** — price variability is highest at low volumes and compresses at elevated volumes.
- Extreme outliers suggest irregular, event-driven activity: index rebalancing, circuit breakers, or institutional block trades.

---

### 6.4 Correlation Heatmap

**Chart:** Lower-triangle heatmap (`sns.heatmap`, `coolwarm` palette)

![Correlation Heatmap](images/04_correlation_heatmap.png)

**Key Insights:**
- `Open`, `High`, `Low`, `Close`, `PrevClose`, and `VWAP` all show **near-perfect 1.00 correlation** — functionally redundant as independent model features.
- `Volume` shows a consistent **-0.18 correlation** with all price variables — a weak but persistent inverse relationship.
- `Turnover` and `Trades` form an independent **liquidity cluster** (mutual correlation 0.80–0.93) operating separately from the price cluster.
- `Daily_Return_%` is effectively uncorrelated with all features (max ~0.09) — daily returns are noise-dominated with no meaningful linear predictability.
- `MA_20` and `MA_50` each show ~0.99 correlation with `Close` and 0.99 with each other — redundant as independent model inputs.

---

### 6.5 Pairplot Analysis

**Chart:** 5×5 pairplot grid (`sns.pairplot`) — Open, High, Low, Close, Volume

![Pairplot Analysis](images/05_pairplot.png)

**Key Insights:**
- All OHLC scatter pairs form tight **45-degree diagonal lines** — confirming near-perfect multicollinearity across all price variables.
- Diagonal KDE plots for price variables are **bimodal** (peaks at ₹150–200 and ₹400–500) — two dominant historical price regimes.
- Volume shows **no linear relationship** with any price variable — all volume-price panels show funnel-shaped, non-linear clouds.
- Volume diagonal KDE is **extremely right-skewed** with a sharp spike near zero — extreme volume days are statistically rare.
- Strong **heteroscedasticity** in all volume-price panels — variance in volume expands sharply as price decreases.

---

### 6.6 Price Trend & Moving Averages

**Chart:** Multi-line chart — `Close`, `MA_20`, `MA_50`

![Price Trend & Moving Averages](images/06_price_trend_ma.png)

**Key Insights:**
- Clear **long-term upward trajectory** with distinct cyclical phases — sharp drawdowns followed by prolonged recoveries.
- `MA_20` and `MA_50` track the price closely with minimal lag — confirms strong **trend persistence** throughout the series.
- Downside moves are sharp and rapid; recoveries are extended and gradual — **asymmetric market dynamics** typical of cyclical equities.
- The all-time high near ₹1,400 followed by a sharp pullback at the right edge suggests a recent peak formation and consolidation phase.
- The structure supports a **four-regime view**: low-price phase (pre-2007) → volatile JLR-cycle high (2007–2014) → prolonged correction and recovery (2015–2021) → current high-price expansion.

---

### 6.7 Monthly Return Heatmap

**Chart:** Year × Month pivot heatmap (`sns.heatmap`, `RdYlGn` palette, centered at 0)

![Monthly Return Heatmap](images/07_monthly_heatmap.png)

**Notable Data Points:**

| Period | Return | Event |
|--------|--------|-------|
| Sep 2011 | **-334.0%** | Worst recorded month — Eurozone crisis |
| Apr 2020 | **+260.2%** | COVID-19 stimulus rebound |
| Oct 2019 | **+226.4%** | Highest single-month gain |
| Oct 2021 | **+202.5%** | Second-highest monthly gain |
| Jan 2021 | **+188.2%** | Strong January bullish momentum |
| Mar 2020 | **-181.3%** | COVID-19 crash continuation |
| Feb 2020 | **-164.2%** | COVID-19 crash onset |
| Oct 2008 | **-303.6%** | Global financial crisis |
| Mar 2001 | **-211.0%** | Dot-com correction impact |

**Key Insights:**
- **January** is the most reliably bullish month — positive returns across 2021 (+188.2%), 2012 (+144.1%), and 1999 (+147.4%).
- **October** is the highest-variance month — both the best (Oct 2019: +226.4%) and one of the worst (Oct 2008: -303.6%) months on record.
- **February and March** are structurally weak — recurring negative returns make early calendar months the highest-risk window.
- **2020** was the most volatile year in the full 30-year dataset — deepest consecutive losses (Feb/Mar) and strongest recoveries (Apr/Aug/Nov) within the same calendar year.

---

### 6.8 Trades vs. Price vs. Volume

**Chart:** Bubble scatterplot — `Trades` (x-axis), `Close` (y-axis), `Volume` (bubble size)

![Trades vs Price vs Volume](images/08_trades_price_volume.png)

**Key Insights:**
- All-time price highs (₹900–₹1,400) occur at **very low trade counts** (<0.4M) — record highs were achieved during low-participation, institutionally-driven sessions.
- Heaviest trading days (>0.8M trades) are confined **below ₹500** — maximum crowd activity coincides with cheaper price levels.
- Largest volume bubbles (>240M shares) cluster in **₹200–₹400** — the historically most contested price zone for institutional accumulation and distribution.
- One outlier at ~1.5M trades / ₹500 close almost certainly corresponds to a specific macro event driving simultaneous participation and liquidity extremes.
- Clear **inverse relationship between trade count and price** — TATAMOTORS attracts maximum participation during downturns, not rallies.

---

### 6.9 Drawdown Analysis

**Methodology:**
```python
df['Cumulative'] = (1 + df['Daily_Return_%'] / 100).cumprod()
df['Peak']       = df['Cumulative'].cummax()
df['Drawdown']   = df['Cumulative'] - df['Peak']
# Drawdown = 0 → new all-time high; negative → loss from most recent peak
```

**Chart:** Drawdown over time (red line)

![Drawdown Analysis](images/09_drawdown.png)

**Key Insights:**
- The early period (1995–1996) shows drawdown reaching approximately **-0.60** — the worst capital loss phase in the dataset window.
- A sharp near-vertical drawdown event around **November 1995** was followed by a prolonged multi-month recovery through mid-1996.
- Two distinct troughs form a **double-bottom structure** — the stock retested its lows before mounting a sustained recovery.
- The most recent period shows recovery toward near-zero drawdown (new high) followed by a fresh drawdown to **~-0.30** — a new corrective phase.
- TATAMOTORS spends the **majority of observed time in negative drawdown territory** — consistent with high-volatility cyclical equities; rewards timing over passive holding.

---

## 7. Statistical Summary

| Metric | Value |
|--------|-------|
| **Distribution Shape** | Multi-modal, positively skewed, heavy-tailed — non-Gaussian |
| **Price Range** | ₹50 to ₹1,400+ (full historical range) |
| **Median Close** | ~₹400 |
| **IQR (25th–75th pct)** | ~₹270 to ₹530 |
| **Skewness** | Positive — mean significantly above median; right tail dominant |
| **Kurtosis** | Leptokurtic — excess kurtosis confirms heavy tails and fat-tail risk |
| **Daily Return** | Near-zero mean; high variance; effectively uncorrelated (noise-dominated) |
| **Max Monthly Return** | +260.2% (April 2020 — COVID stimulus rebound) |
| **Min Monthly Return** | -334.0% (September 2011 — Eurozone crisis) |
| **Peak Drawdown** | ~-60% in early dataset window (1995–1996) |

---

## 8. Consolidated Findings

- **Price is fundamentally non-normal** — multi-modal distribution, positive skewness, and heavy tails invalidate standard Gaussian risk models; quantile-based or regime-switching approaches are required.
- **OHLC variables are operationally redundant** — `Open`, `High`, `Low`, `Close`, `PrevClose`, and `VWAP` share near-perfect correlation; only one should be retained as a model feature.
- **Volume is a structurally independent signal** — the liquidity cluster (`Volume`, `Turnover`, `Trades`) operates independently of price and carries information not captured by OHLC alone.
- **All-time highs are low-participation events** — peak prices consistently occur at low volume and low trade count; maximum crowd activity coincides with lower prices.
- **Seasonality is asymmetric and actionable** — January and October–April windows show consistent positive bias; February and March are the highest-risk months historically.
- **Drawdown risk is severe and prolonged** — maximum drawdowns of -60%+ and extended recovery cycles make passive holding high-risk; active risk management is essential.
- **2020 was the defining volatility year** — COVID-19 produced both the sharpest crash and fastest recovery in the 30-year record; any model must account for this structural outlier.
- **Daily returns are near-random** — low autocorrelation confirms noise-dominated short-term dynamics; predictive signal is only actionable at weekly, monthly, or longer horizons.

---

## 9. Recommended Next Steps

- **Time-Series Forecasting** — Apply ARIMA, SARIMA, LSTM, or Temporal Fusion Transformer models to the full `Close` series across identified market regimes.
- **Feature Engineering** — Derive RSI, Bollinger Bands, ATR, and rate-of-change features from OHLCV data for ML classification and regression pipelines.
- **Volatility Modelling** — Fit GARCH or EGARCH models to `Daily_Return_%` to capture volatility clustering and conditional heteroscedasticity.
- **Strategy Backtesting** — Design and backtest MA crossover, momentum, and mean-reversion strategies with full transaction cost and slippage modelling.
- **Risk Profiling** — Compute rolling VaR, CVaR, and Sharpe/Sortino ratios across multiple holding period horizons.

---

## 10. How to Run

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scipy
```

### Steps

1. Clone the repository:
```bash
git clone https://github.com/your-username/tatamotors-stock-eda.git
cd tatamotors-stock-eda
```

2. Place the dataset CSV in the project root:
```
tatamotors_historical.csv
```

3. Launch the notebook:
```bash
jupyter notebook Tata_Motors_Stock_Analysis_Prediction_1995-2025_.ipynb
```

4. Run all cells: `Cell → Run All`

> **Note:** Ensure the filename in `pd.read_csv()` matches your local dataset filename exactly.

---

## 11. Repository Structure

```
📁 tatamotors-stock-eda/
│
├── 📓 Tata_Motors_Stock_Analysis_Prediction_1995-2025_.ipynb   ← Main analysis notebook
├── 📄 tatamotors_historical.csv                                 ← Dataset (1995–2025)
├── 📄 TataMotors_EDA_Report.docx                               ← Full detailed report
├── 📄 README.md                                                 ← This file
│
└── 📁 images/
    ├── 01_closing_price_distribution.png
    ├── 02_outlier_analysis.png
    ├── 03_volume_vs_price.png
    ├── 04_correlation_heatmap.png
    ├── 05_pairplot.png
    ├── 06_price_trend_ma.png
    ├── 07_monthly_heatmap.png
    ├── 08_trades_price_volume.png
    └── 09_drawdown.png
```

---

- Free to use for research, education, and non-commercial applications.
- Modification and redistribution permitted with attribution.
- Data sourced from the **National Stock Exchange of India (NSE)**.
- All rights in the original exchange data remain with NSE.

---

*This project is intended for educational and portfolio purposes only. All analysis is based on the provided dataset and does not constitute financial or investment advice.*

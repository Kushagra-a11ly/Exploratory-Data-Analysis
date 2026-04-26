# Tata Motors Stock Analysis & Prediction (1995–2025)

**Domain:** Finance & Equity Markets &nbsp;|&nbsp; **Ticker:** NSE: TATAMOTORS &nbsp;|&nbsp; **Period:** January 1995 – August 2025 &nbsp;|&nbsp; **Language:** Python 3

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Libraries Used](#2-libraries-used)
3. [Dataset Summary](#3-dataset-summary)
4. [Data Cleaning & Preprocessing](#4-data-cleaning--preprocessing)
5. [Exploratory Data Analysis](#5-exploratory-data-analysis)
   - 5.1 [Closing Price Distribution](#51-closing-price-distribution)
   - 5.2 [Outlier Analysis](#52-outlier-analysis)
   - 5.3 [Volume vs Closing Price](#53-volume-vs-closing-price)
   - 5.4 [Correlation Heatmap](#54-correlation-heatmap)
   - 5.5 [Pairplot Analysis](#55-pairplot-analysis)
   - 5.6 [Price Trend & Moving Averages](#56-price-trend--moving-averages)
   - 5.7 [Monthly Return Heatmap](#57-monthly-return-heatmap)
   - 5.8 [Trades vs Price vs Volume](#58-trades-vs-price-vs-volume)
   - 5.9 [Drawdown Analysis](#59-drawdown-analysis)
6. [Statistical Analysis](#6-statistical-analysis)
7. [Key Findings & Insights](#7-key-findings--insights)
8. [How to Run](#8-how-to-run)

---

## 1. Project Overview

- End-to-end **Exploratory Data Analysis (EDA)** on 30 years of daily stock data for Tata Motors Limited (NSE: TATAMOTORS).
- Covers the full lifecycle from raw data loading and cleaning to advanced visualisation and statistical profiling.
- Analyses **price structure, volume behaviour, return seasonality, drawdown risk, and market microstructure** across ~7,500 trading sessions.
- Designed as a foundation for downstream tasks including time-series forecasting, strategy backtesting, and machine learning model development.

---

## 2. Libraries Used

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, manipulation, resampling, and aggregation |
| `numpy` | Numerical operations, z-score computation, masking |
| `matplotlib` | Line charts, drawdown plots, time-series visualisation |
| `seaborn` | Statistical plots — histograms, boxplots, heatmaps, pairplots, scatterplots |
| `scipy.stats` | Skewness, kurtosis, and z-score outlier detection |

---

## 3. Dataset Summary

- **File:** `Tata Motors Stock Analysis Prediction(1995-2025).csv`
- **Rows:** ~7,500 trading sessions
- **Columns:** 14 features covering price, volume, microstructure, and derived indicators
- **Key columns used in analysis:**

  | Column | Description |
  |--------|-------------|
  | `Date` | Trading session date (`YYYY-MM-DD`) |
  | `Open`, `High`, `Low`, `Close` | OHLC price data in ₹ |
  | `PrevClose` | Previous session closing price |
  | `Volume` | Shares traded per session |
  | `Turnover` | Total monetary value of trades (₹) |
  | `VWAP` | Volume Weighted Average Price |
  | `Trades` | Number of order matches per session |
  | `Daily_Return_%` | Percentage return from `PrevClose` to `Close` |
  | `Cumulative_Return_%` | Running compounded return from dataset start |
  | `MA_20` | 20-session simple moving average |
  | `MA_50` | 50-session simple moving average |

---

## 4. Data Cleaning & Preprocessing

- **Missing values** — Identified using `isnull().sum()`; removed via `dropna(inplace=True)`. Post-cleaning: zero missing values across all columns.
- **Duplicate check** — Verified using `duplicated().sum()`; no duplicate records found.
- **Column renaming** — `Unnamed: 0` renamed to `Index` for clarity.
- **Date parsing** — `Date` column converted to `datetime` format using `pd.to_datetime()`.
- **Feature engineering** — `Month` and `Year` columns extracted from `Date` for temporal analysis.
- **Derived risk metrics** — `Cumulative`, `Peak`, and `Drawdown` columns computed during EDA for risk profiling.

---

## 5. Exploratory Data Analysis

### 5.1 Closing Price Distribution

- **Plot:** Histogram with KDE (`sns.histplot`)
- **Observations:**
  - Multi-modal distribution with distinct peaks at ₹150–250, ₹350–500, and ₹900–1050 — indicating three separate market regimes.
  - ₹300–500 represents the highest-density fair value zone with maximum price acceptance.
  - Strong positive (right) skew — rare but sharp upside spikes inflate the mean above the median.
  - Price range of ₹100–₹1,100+ (a 10x spread) confirms extreme long-run volatility.
  - Non-normal distribution warrants use of log transformations or quantile-based methods for modelling.

---

### 5.2 Outlier Analysis

- **Plot:** Boxplot (`sns.boxplot`)
- **Method:** Z-score method (`scipy.stats.zscore`), threshold = ±3
- **Observations:**
  - Median close ≈ ₹400; IQR spans approximately ₹270–₹500.
  - Numerous high-end outliers above ₹850, indicating frequent speculative surges.
  - Few lower outliers — negative shocks are comparatively contained.
  - Outliers above ₹900 flagged as potential overextension zones.

---

### 5.3 Volume vs Closing Price

- **Plot:** Scatterplot (`sns.scatterplot`)
- **Observations:**
  - Highest closing prices (₹800–₹1,150) occur at **low-to-moderate volume** — price peaks are not participation-driven.
  - Densest trading cluster sits in the ₹100–₹400 range with widely scattered volumes.
  - Even at very high volumes (200M–400M shares), prices remain in the ₹150–₹350 band — volume surges do not drive prices higher.
  - Heteroscedastic pattern — price variance is higher at low volumes and compresses at higher volumes.
  - Outliers suggest irregular, event-driven trading activity (circuit breakers, macro shocks).

---

### 5.4 Correlation Heatmap

- **Plot:** Lower-triangle heatmap with annotations (`sns.heatmap`, `coolwarm` palette)
- **Observations:**
  - `Open`, `High`, `Low`, `Close` — near-perfect positive correlation; highly redundant as independent features.
  - `Drawdown` and `Peak` are price-derived — not independent signals.
  - `Volume`, `Turnover`, and `Trades` form a distinct liquidity cluster, largely independent of price.
  - `Daily_Return_%` is mostly uncorrelated — confirms noisy, near-random daily return behaviour.
  - `Month` shows negligible correlation — weak seasonality in raw returns.
  - `Year` shows moderate positive correlation — reflects the long-run upward price trend.

---

### 5.5 Pairplot Analysis

- **Plots:** Grid pairplot — price OHLC + volume; extended pairplot with `Symbol` hue
- **Observations:**
  - All OHLC scatter pairs form tight 45° diagonal lines — extreme multicollinearity across price variables.
  - Bimodal price KDE with peaks at ₹150–200 and ₹400–500 — confirms two distinct historical price regimes.
  - Historical price range: ₹50 to ₹1,200+; majority of observations clustered at lower levels prior to the recent run-up.
  - Volume shows no linear relationship with price — high-volume days occur at all price levels.
  - Volume KDE is sharply right-skewed — extreme volume days are rare but disproportionately significant.

---

### 5.6 Price Trend & Moving Averages

- **Plot:** Multi-line chart — `Close`, `MA_20`, `MA_50`
- **Observations:**
  - Clear long-term upward trajectory with distinct cyclical drawdown and recovery phases.
  - `MA_20` and `MA_50` track the price closely with minimal lag — strong trend persistence throughout the series.
  - Downside moves are sharp; recoveries are prolonged — asymmetric market dynamics.
  - Volume spikes align temporally with high-volatility periods.
  - Recent sharp uptrend followed by a pullback suggests a potential consolidation phase.

---

### 5.7 Monthly Return Heatmap

- **Plot:** Pivot heatmap of mean `Daily_Return_%` by Year × Month (`coolwarm`)
- **Notable data points:**

  | Period | Return | Event |
  |--------|--------|-------|
  | Sep 2011 | **-333.97%** | Worst single month — Eurozone crisis impact |
  | Apr 2020 | **+260.21%** | COVID-19 stimulus-driven rebound |
  | Oct 2019 | **+226.40%** | Highest recorded monthly gain |
  | Oct 2021 | **+202.52%** | Second-highest gain |
  | Jan 2021 | **+188.23%** | Strong January effect |
  | Feb 2020 | **-164.18%** | COVID-19 crash onset |
  | Mar 2020 | **-181.33%** | COVID-19 crash continuation |

- **Seasonal patterns:**
  - **January** — historically strong bullish bias across multiple years.
  - **February–March** — structurally weak; recurring negative returns.
  - **October & April** — highest-gain months historically.
  - **2020** — most volatile year overall; extreme losses and recoveries within the same calendar year.

---

### 5.8 Trades vs Price vs Volume

- **Plot:** Bubble scatterplot — `Trades` (x), `Close` (y), `Volume` (bubble size), `Symbol` (hue)
- **Observations:**
  - Peak prices (₹900–₹1,200) occur at **low trade counts** (<0.4M) — all-time highs were institutional, low-noise events.
  - Heaviest trading days (>0.8M trades) are confined below ₹500 — mass retail participation coincides with lower price levels.
  - Largest volume bubbles (>240M shares) cluster in the ₹200–₹400 band — the most historically contested price zone.
  - One outlier at ~1.5M trades with ₹500 close likely corresponds to a major macro event (index rebalancing or earnings surprise).
  - Inverse relationship between trade count and price — TATAMOTORS attracts maximum crowd activity during downturns, not rallies.

---

### 5.9 Drawdown Analysis

- **Plot:** Line chart of drawdown from cumulative peak (red)
- **Methodology:** `Cumulative = (1 + Daily_Return_%/100).cumprod()` → `Peak = cummax()` → `Drawdown = Cumulative - Peak`
- **Observations:**
  - Maximum drawdown approaches **-85%** in the earliest period — worst capital destruction phase in recorded history.
  - Two distinct drawdown troughs (~-80% and ~-85%) form a classic double-bottom structure before sustained recovery.
  - Mid-period shows a slow, multi-year recovery from -80% to -40% with multiple failed recovery attempts.
  - Most recent period: near-zero drawdown (new all-time high) followed by a sharp fresh drawdown to ~-50%.
  - Stock spends most of its time below previous peaks — characteristic of a high-volatility, cyclical equity.

---

## 6. Statistical Analysis

- **Skewness & Kurtosis** — Computed via `scipy.stats`; confirms positive skew and heavy tails in the `Close` distribution.
- **Monthly resampling** — `resample('M')['Close'].mean()` used to compute monthly average closing prices.
- **Turnover aggregation** — `groupby('Symbol')['Turnover'].agg(['mean', 'sum'])` computes per-symbol liquidity profile.
- **Crosstab analysis** — Month-vs-Symbol distribution computed with row-normalised percentages to assess calendar-based trading patterns.
- **Memory profiling** — `df.memory_usage()` used to assess dataset footprint.
- **Random sampling** — `df.sample(5)` used for sanity checks during cleaning and exploration.

---

## 7. Key Findings & Insights

- **Price structure is non-normal** — Multi-modal, positively skewed, and heavy-tailed; standard Gaussian models will underestimate risk.
- **OHLC variables are redundant** — `Open`, `High`, `Low`, and `Close` are near-perfectly correlated; only one is needed as a model feature.
- **Volume is an independent signal** — Liquidity metrics (`Volume`, `Turnover`, `Trades`) are structurally separate from price and carry independent information.
- **Price peaks are low-participation events** — All-time highs occurred during quiet sessions; extreme volume days correspond to mid-range or lower prices.
- **Seasonality exists but is asymmetric** — January and October–April windows show consistent bullish bias; February–March are structurally weak.
- **Drawdown is severe and prolonged** — Maximum drawdown of ~-85% and long recovery cycles make passive holding high-risk; timing of entry and exit matters significantly.
- **2020 was the defining volatility year** — COVID-19 created the sharpest crash and fastest recovery sequence in the 30-year record.
- **Daily returns are near-random** — Low autocorrelation in `Daily_Return_%` confirms noise-dominated short-term dynamics; trend signals emerge only at longer horizons.

---

## 8. How to Run

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scipy
```

### Steps

1. Clone or download this repository.
2. Place `Tata Motors Stock Analysis Prediction(1995-2025).csv` in the project root directory.
3. Launch Jupyter Notebook:

```bash
jupyter notebook Tata_Motors_Stock_Analysis_Prediction_1995-2025_.ipynb
```

4. Run all cells sequentially (`Cell → Run All`).

### Notes

- Ensure the CSV filename matches exactly as referenced in the notebook's `pd.read_csv()` call.
- All plots render inline; no external image exports are required.
- The notebook is self-contained — no external API calls or additional data sources are needed.

---

*Data sourced from the National Stock Exchange of India (NSE). All analysis is for educational and research purposes only and does not constitute financial advice.*

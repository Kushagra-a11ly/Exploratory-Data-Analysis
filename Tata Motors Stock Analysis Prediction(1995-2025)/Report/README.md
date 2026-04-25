TATAMOTORS — NSE Stock EDA (1995–2025)

Exploratory Data Analysis of Tata Motors Limited (NSE: TATAMOTORS)**
30 Years of Market Data | January 1995 – December 2025**
Confidential — For Internal Research Purposes Only | April 2026**

Overview

This project presents a comprehensive end-to-end Exploratory Data Analysis (EDA) of Tata Motors stock using 30 years of daily trading data.

The analysis covers:

* Data cleaning and preprocessing
* Statistical profiling
* Trend and regime identification
* Market behavior analysis
* Eight key visualizations

It captures the full lifecycle of the stock—from early growth phases and macroeconomic shocks to the recent EV-driven rally.

Key Insights

* Price Growth:₹70 → ₹1,150+ (~15x return)
* Returns:Non-normal, positively skewed, fat-tailed
* Volume vs Price:Weak predictive relationship
* Most Volatile Year: 2020 (COVID-driven)
* Drawdowns:Long recovery cycles after major crashes

Dataset Details

| Property  | Details             |
| --------- | ------------------- |
| Period    | Jan 1995 – Dec 2025 |
| Frequency | Daily               |
| Records   | 7,500+              |
| Exchange  | NSE                 |
| Currency  | INR (Unadjusted)    |

Columns

* Price: Open, High, Low, Close
* Market Activity: Volume, Turnover, Trades
* Derived Features:

  * Daily_Return_%
  * MA_20, MA_50
  * Cumulative Return
  * Peak
  * Drawdown

⚙️ Tech Stack

* pandas — Data processing & feature engineering
* numpy — Numerical computation
* matplotlib — Visualization
* seaborn — Statistical plots
* scipy — Skewness, kurtosis, outlier detection

🔍 Analytical Workflow

1. Data Loading & Inspection

   * CSV import, datatype validation, summary statistics

2. **Data Cleaning**

   * Missing values handling
   * Duplicate checks
   * Date parsing
   * Feature extraction (Month, Year)

3. **Exploratory Analysis**

   * Correlation matrix
   * Grouped analysis
   * Monthly resampling
   * Turnover aggregation

4. **Visualization**

   * 8 analytical charts

5. **Statistical Profiling**

   * Skewness & kurtosis
   * Outlier detection
   * Multicollinearity analysis

---

## 📈 Visualizations

### 1. Closing Price Distribution

* Three price regimes: ₹150–250, ₹350–500, ₹900–1,050
* Core value zone: ₹300–₹500
* Positively skewed distribution

### 2. Outlier Analysis (Box Plot)

* Median: ~₹400
* IQR: ₹270–₹500
* Strong upper outliers (>₹850)

### 3. Volume vs Price

* Weak relationship
* High prices often occur at low-to-moderate volume

### 4. Correlation Heatmap

* OHLC highly correlated (~0.99)
* Volume cluster independent
* Returns uncorrelated

### 5. Moving Averages (MA-20 & MA-50)

* Clear long-term uptrend
* Crossovers signal trend reversals
* Sharp declines, slow recoveries

### 6. Monthly Returns Heatmap

* Best: April 2020 (+260%)
* Worst: September 2011 (-333%)
* January strong; Feb–Mar weak
* 2020 most volatile year

### 7. Pair Plot

* Confirms OHLC redundancy
* Bimodal price distribution
* Volume independence

8. Trades vs Price vs Volume

* High prices = low trade participation
* ₹200–₹400 = accumulation zone
* Inverse trade-price relationship


📉 Statistical Summary

| Metric           | Insight                   |
| ---------------- | ------------------------- |
| Skewness         | Positive (upward bias)    |
| Kurtosis         | High (fat tails)          |
| Outliers         | >₹900 (real events)       |
| OHLC Correlation | ~0.99 (multicollinearity) |
| Price Range      | ₹70 – ₹1,150+             |
| Core Zone        | ₹270 – ₹500               |

🧠 Modeling Implications

Quantitative Modeling

* Use **Close price** (avoid OHLC redundancy)
* Apply:

  * Log transformations
  * Quantile regression
  * Regime-switching models
* Engineer volume-based features
* Avoid relying on seasonality
* Incorporate drawdown risk (-85% historical)

Technical Analysis

* MA crossovers = reliable signals
* Volume confirmation not required
* ₹270–₹500 = mean-reversion zone
* > ₹900 = overextension zone

 ⚠️ Limitations

* Prices are **not adjusted** for splits/dividends
* Only NSE equity considered (no DVR/ADR)
* No predictive modeling included
* September 2011 extreme value may be anomalous
* Not investment advice


## 📁 Project Structure

```
TATAMOTORS-EDA/
├── README.md
├── data/
│   └── Tata_Motors_Stock_Analysis_Prediction(1995-2025).csv
├── notebooks/
│   └── tatamotors_eda.ipynb
├── outputs/
│   ├── visual_1_closing_price_distribution.png
│   ├── visual_2_outlier_boxplot.png
│   ├── visual_3_volume_vs_price.png
│   ├── visual_4_correlation_heatmap.png
│   ├── visual_5_moving_averages.png
│   ├── visual_6_monthly_returns_heatmap.png
│   ├── visual_7_pair_plot.png
│   └── visual_8_trades_price_volume_bubble.png
└── report/
    └── TATAMOTORS_EDA_Report.pdf
```

---

## 📌 Disclaimer

This project is intended for research and educational purposes only.
Past performance is not indicative of future results.

⭐ Future Improvements

* Adjust prices for corporate actions
* Incorporate macroeconomic indicators
* Build interactive dashboard (Streamlit/Power BI)

---

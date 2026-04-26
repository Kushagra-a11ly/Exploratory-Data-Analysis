![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/48789243202a0a26b9dad8cd49b822d5e4840b38/Tata%20Motors%20Stock%20Analysis%20Prediction(1995-2025)/dataset-cover.png)


Tata Motors Historical Stock Price Dataset
A longitudinal daily price history for NSE-listed TATAMOTORS spanning January 1995 to August 2025 — enriched with OHLCV data, market microstructure metrics, and pre-computed technical indicators, built for time-series forecasting, algorithmic strategy development, and machine learning research.

Type
Time-Series
Domain
Finance & Equity Markets
Granularity
Daily (Trading Session)
Format
CSV
📋
Table of Contents
Overview
About Tata Motors
Dataset Composition
Feature Reference
Use Cases
Getting Started
Notes & Considerations
License
📌
Overview
For over three decades, Tata Motors Limited has stood as one of the most closely watched equities on the National Stock Exchange of India — a bellwether for the country's automotive sector, a barometer of domestic consumption, and a stock that has moved markets with every strategic decision from the landmark acquisition of Jaguar Land Rover in 2008 to its ongoing transformation into an electric vehicle powerhouse.

This dataset captures that entire journey. Compiled from official NSE records and spanning January 1995 through August 2025, this is a longitudinal daily price history containing over 7,500 trading sessions of OHLCV data, market microstructure metrics, and pre-computed technical indicators — cleaned, enriched, and structured for immediate use in quantitative research, financial modelling, and machine learning applications.

🏭
About Tata Motors
Tata Motors Limited is the automotive flagship of the Tata Group, one of India's oldest and most diversified industrial conglomerates. Headquartered in Mumbai, the company manufactures a broad portfolio spanning passenger vehicles, commercial trucks, electric vehicles, and premium automotive brands through its wholly-owned subsidiary, Jaguar Land Rover. As a constituent of the NIFTY 50 index, TATAMOTORS is among the most liquid and institutionally traded equities on the NSE.

The stock's 30-year trading record encompasses some of the most consequential moments in modern Indian financial history — the post-liberalisation bull market of the late 1990s, the dot-com correction, the 2008 global financial crisis, the JLR acquisition and its subsequent debt cycle, the COVID-19 pandemic shock and recovery of 2020–2021, and the current structural re-rating driven by EV adoption and JLR's return to profitability. Each of these episodes is legible in the data.

🗂️
Dataset Composition
Attribute	Detail
Exchange	National Stock Exchange of India (NSE)
Ticker Symbol	TATAMOTORS
Asset Class	Equity — Large Cap / NIFTY 50 Constituent
Data Frequency	Daily (per trading session)
Coverage Period	January 1995 – August 2025
Approximate Row Count	~7,500 trading sessions
Total Feature Columns	14
Missing Values	None (post-cleaning)
File Format	CSV (UTF-8 encoded)
🔬
Feature Reference
Market Price Data
Date
Calendar date of the trading session, aligned to NSE market holidays. Format: YYYY-MM-DD.
Symbol
NSE ticker identifier. Consistently recorded as TATAMOTORS throughout the full dataset.
Open
Price at which the first executed trade occurred at session open, in Indian Rupees (₹).
High
Highest traded price recorded during the session, in ₹.
Low
Lowest traded price recorded during the session, in ₹.
Close
Official NSE-published closing price at end of session, in ₹.
PrevClose
Closing price from the immediately preceding trading session. Used as the basis for daily return calculation.
Volume & Market Microstructure
Volume
Total number of equity shares traded during the session. A key measure of market participation and liquidity.
Turnover
Aggregate monetary value of all trades executed during the session, denominated in ₹. Reflects total capital flow through the stock on a given day.
VWAP
Volume Weighted Average Price — calculated as total turnover divided by total volume. Widely used as a benchmark in institutional order execution.
Trades
Number of discrete order matches executed during the session. Serves as a proxy for depth of market participation beyond raw volume.
Derived & Technical Features
Daily_Return_%
Single-session percentage return, computed as the percentage change from PrevClose to Close. Represents the raw daily return for a buy-and-hold position.
Cumulative_Return_%
Running compounded return indexed from the first record in the dataset. Provides a continuous performance trajectory across the full 30-year span.
MA_20
20-session simple moving average of the daily closing price. A standard short-term trend indicator for momentum and dynamic support/resistance analysis.
MA_50
50-session simple moving average of the daily closing price. Represents medium-term price trend, widely used in crossover-based trading systems.
🎯
Use Cases
📉
Time-Series Forecasting
Train and evaluate autoregressive models (ARIMA, SARIMA), deep learning architectures (LSTM, GRU, Temporal Fusion Transformer), and modern sequence models on 30 years of daily close data across structurally distinct market regimes.

⚙️
Algorithmic Strategy Backtesting
Design and backtest rule-based trading strategies — including MA crossover systems, momentum strategies, mean-reversion signals, and volume-confirmation filters — against authentic, exchange-sourced price history.

🤖
Machine Learning for Return Prediction
Use OHLCV data, VWAP, trade counts, daily returns, and moving averages as direct model features or inputs to feature engineering pipelines for classification or regression models targeting directional price movement.

📊
Volatility & Risk Analysis
Compute rolling volatility measures, historical Value-at-Risk (VaR), Conditional VaR (CVaR), maximum drawdown profiles, and Sharpe/Sortino ratios across different investment horizons and market regimes.

🔍
Exploratory Data Analysis
Conduct price trend analysis, volume seasonality studies, return distribution modelling, autocorrelation structure analysis, and long-run performance attribution using the full breadth of included features.

🎓
Financial & Academic Research
Suitable for event studies around corporate announcements, sector-level research in emerging market equities, and analysis of the relationship between market microstructure metrics and price outcomes.

🚀
Getting Started
Load the dataset and begin exploration with the following Python snippet:

# Load the dataset import pandas as pd import matplotlib.pyplot as plt df = pd.read_csv('tatamotors_historical.csv', parse_dates=['Date']) df.set_index('Date', inplace=True) # Quick overview print(df.shape) # (~7500, 13) print(df.head()) print(df.describe()) # Plot closing price with moving averages fig, ax = plt.subplots(figsize=(14, 5)) ax.plot(df['Close'], label='Close', linewidth=0.9, color='#58a6ff') ax.plot(df['MA_20'], label='MA 20', linewidth=1.2, color='#e3b341') ax.plot(df['MA_50'], label='MA 50', linewidth=1.2, color='#ff7b72') ax.legend() plt.title('TATAMOTORS — Daily Close with Moving Averages (1995–2025)') plt.tight_layout() plt.show()
⚠️
Notes & Considerations
⚠️ Moving Average Warm-Up Removal
The first 50 rows of raw data — where MA_20 and MA_50 carry NaN values due to their respective look-back window requirements — have been excluded from the final dataset. All retained rows are fully populated across every column with no leading missing values.

⚠️ No Imputation Applied
Price, volume, and turnover columns reflect official NSE-published figures without any imputation, interpolation, or forward-filling. The data is presented exactly as recorded. There are no synthetic or estimated values in the dataset.

⚠️ Return Calculation Basis
Daily_Return_% and Cumulative_Return_% have been derived directly from NSE-recorded Close and PrevClose values. No adjustment for dividends, bonus issues, rights entitlements, or stock splits has been applied beyond what is already reflected in the NSE's official historical records.

⚠️ Corporate Action Advisory
Users constructing long-run return series or comparing absolute price levels across distant time periods should independently verify and account for the full history of corporate actions affecting TATAMOTORS — including stock splits, bonus share issuances, and rights issues — to ensure price continuity where required by their specific methodology.

📄
License
🔓
Community Data License Agreement (CDLA) — Permissive, Version 2.0
This dataset is made available for open use in research, education, and non-commercial applications. Users are free to use, modify, and redistribute with attribution. Data sourced from the National Stock Exchange of India (NSE). All rights in original exchange data remain with NSE.

National Stock Exchange of India  ·  TATAMOTORS  ·  Equity  ·  Daily Frequency  ·  

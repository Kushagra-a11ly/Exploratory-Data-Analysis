![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/48789243202a0a26b9dad8cd49b822d5e4840b38/Tata%20Motors%20Stock%20Analysis%20Prediction(1995-2025)/dataset-cover.png)





Tata Motors Stock Price Dataset (1995–2025)

📌 Introduction

This dataset contains historical stock price data for Tata Motors Limited (NSE: TATAMOTORS) spanning from January 1995 to August 2025.

The data is sourced from the National Stock Exchange (NSE) of India and includes detailed daily trading information along with derived technical indicators.

It is designed for time-series analysis, financial modeling, and machine learning applications.

 Dataset Composition
AttributeDetailExchangeNational Stock Exchange of India (NSE)Ticker SymbolTATAMOTORSAsset ClassEquity — Large Cap / NIFTY 50 ConstituentData FrequencyDaily (per trading session)Coverage PeriodJanuary 1995 – August 2025Approximate Row Count~7,500 trading sessionsTotal Feature Columns14Missing ValuesNone (post-cleaning)File FormatCSV (UTF-8 encoded)

4. Feature Reference
4.1 Market Price Data
ColumnTypeDescriptionDateDateTrading session date aligned to NSE market calendar. Format: YYYY-MM-DD.SymbolStringNSE ticker — consistently TATAMOTORS across all rows.OpenFloat (₹)First executed trade price at session open.HighFloat (₹)Highest traded price during the session.LowFloat (₹)Lowest traded price during the session.CloseFloat (₹)Official NSE closing price at end of session.PrevCloseFloat (₹)Prior session's closing price; basis for return calculation.
4.2 Volume & Market Microstructure
ColumnTypeDescriptionVolumeIntegerTotal shares traded during the session. Measures liquidity and participation.TurnoverFloat (₹)Aggregate monetary value of all trades executed during the session.VWAPFloat (₹)Volume Weighted Average Price — total turnover ÷ total volume. Standard institutional execution benchmark.TradesIntegerNumber of discrete order matches in the session. Proxy for market depth beyond raw volume.
4.3 Derived & Technical Features
ColumnTypeDescriptionDaily_Return_%FloatSession return: percentage change from PrevClose to Close.Cumulative_Return_%FloatRunning compounded return indexed from the first record in the dataset.MA_20Float (₹)20-session simple moving average of Close. Short-term trend and momentum indicator.MA_50Float (₹)50-session simple moving average of Close. Medium-term trend; used in crossover systems.

5. Use Cases

Time-Series Forecasting — Train ARIMA, SARIMA, LSTM, GRU, or Temporal Fusion Transformer models on 30 years of daily close data spanning structurally distinct market regimes.
Algorithmic Strategy Backtesting — Backtest moving average crossover systems, momentum strategies, mean-reversion signals, and volume-confirmation filters against authentic exchange-sourced history.
ML for Return Prediction — Use OHLCV, VWAP, trade counts, and moving averages as raw features or inputs to custom feature engineering pipelines for directional or return-magnitude models.
Volatility & Risk Analysis — Compute rolling volatility, historical VaR, CVaR, maximum drawdown profiles, and Sharpe/Sortino ratios across multiple investment horizons.
Exploratory Data Analysis — Analyse price trends, volume seasonality, return distributions, autocorrelation structure, and long-run performance attribution.
Academic & Financial Research — Supports event studies, emerging market equity research, microstructure-to-price-outcome analysis, and long-run return attribution in the Indian market context.

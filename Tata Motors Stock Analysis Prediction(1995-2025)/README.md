![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/48789243202a0a26b9dad8cd49b822d5e4840b38/Tata%20Motors%20Stock%20Analysis%20Prediction(1995-2025)/dataset-cover.png)





<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Tata Motors Dataset — README</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: #0d1117;
    color: #c9d1d9;
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
    font-size: 15px;
    line-height: 1.7;
    padding: 0;
    min-height: 100vh;
  }

  .page {
    max-width: 960px;
    margin: 0 auto;
    padding: 40px 32px 80px;
  }

  /* ── HEADER ── */
  .header {
    padding-bottom: 20px;
    border-bottom: 1px solid #21262d;
    margin-bottom: 24px;
  }

  .header-title-row {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 14px;
  }

  .header-icon {
    font-size: 36px;
    line-height: 1;
  }

  .header-title {
    font-size: 28px;
    font-weight: 700;
    color: #f0f6fc;
    letter-spacing: -0.02em;
  }

  .header-desc {
    font-size: 14px;
    color: #8b949e;
    line-height: 1.6;
    margin-bottom: 16px;
    padding-left: 2px;
    border-left: 3px solid #21262d;
    padding-left: 12px;
  }

  .tag-row {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tag {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-size: 12px;
    font-weight: 500;
    padding: 4px 0;
  }

  .tag-label {
    color: #8b949e;
    font-weight: 400;
  }

  .tag-value {
    padding: 3px 10px;
    border-radius: 4px;
    font-weight: 600;
    font-size: 12px;
    letter-spacing: 0.01em;
  }

  .tv-blue   { background: #1f6feb; color: #fff; }
  .tv-orange { background: #d14424; color: #fff; }
  .tv-green  { background: #1a7f37; color: #fff; }
  .tv-gray   { background: #30363d; color: #c9d1d9; }

  /* ── SECTION HEADINGS ── */
  .section {
    margin-bottom: 36px;
  }

  .section-heading {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 20px;
    font-weight: 600;
    color: #f0f6fc;
    margin-bottom: 16px;
    padding-bottom: 10px;
    border-bottom: 1px solid #21262d;
  }

  .section-heading .icon {
    font-size: 20px;
  }

  /* ── TABLE OF CONTENTS ── */
  .toc-list {
    list-style: none;
    padding: 0;
  }

  .toc-list li {
    padding: 3px 0;
  }

  .toc-list a {
    color: #58a6ff;
    text-decoration: none;
    font-size: 14.5px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .toc-list a::before {
    content: '•';
    color: #30363d;
    font-size: 18px;
    line-height: 1;
  }

  .toc-list a:hover { text-decoration: underline; }

  /* ── BODY TEXT ── */
  .prose p {
    color: #c9d1d9;
    font-size: 14.5px;
    line-height: 1.8;
    margin-bottom: 14px;
  }

  .prose p:last-child { margin-bottom: 0; }

  /* ── DATASET COMPOSITION TABLE ── */
  .data-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 14px;
    border: 1px solid #21262d;
    border-radius: 8px;
    overflow: hidden;
  }

  .data-table th {
    background: #161b22;
    color: #8b949e;
    font-weight: 500;
    font-size: 12px;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    padding: 10px 16px;
    text-align: left;
    border-bottom: 1px solid #21262d;
  }

  .data-table td {
    padding: 10px 16px;
    border-bottom: 1px solid #21262d;
    color: #c9d1d9;
    vertical-align: top;
  }

  .data-table tr:last-child td { border-bottom: none; }

  .data-table tr:nth-child(even) td { background: #0d1117; }
  .data-table tr:nth-child(odd) td { background: #161b22; }

  .data-table td:first-child {
    color: #f0f6fc;
    font-weight: 500;
    white-space: nowrap;
    width: 220px;
  }

  /* ── FEATURE GROUPS ── */
  .feature-group {
    margin-bottom: 24px;
  }

  .feature-group-title {
    font-size: 13px;
    font-weight: 600;
    color: #58a6ff;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-bottom: 10px;
    padding: 6px 12px;
    background: #1c2a3a;
    border-left: 3px solid #1f6feb;
    border-radius: 0 4px 4px 0;
  }

  .feature-list {
    list-style: none;
    padding: 0;
    border: 1px solid #21262d;
    border-radius: 6px;
    overflow: hidden;
  }

  .feature-list li {
    padding: 10px 16px;
    border-bottom: 1px solid #21262d;
    font-size: 14px;
    line-height: 1.6;
    display: flex;
    gap: 10px;
    align-items: flex-start;
  }

  .feature-list li:last-child { border-bottom: none; }
  .feature-list li:nth-child(odd) { background: #161b22; }
  .feature-list li:nth-child(even) { background: #0d1117; }

  .feat-name {
    font-family: 'Courier New', monospace;
    font-size: 12.5px;
    font-weight: 600;
    color: #79c0ff;
    background: #1c2a3a;
    padding: 2px 8px;
    border-radius: 4px;
    white-space: nowrap;
    flex-shrink: 0;
    margin-top: 1px;
  }

  .feat-desc {
    color: #8b949e;
    font-size: 13.5px;
    line-height: 1.65;
  }

  /* ── USE CASES ── */
  .usecase-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .usecase-card {
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 8px;
    padding: 16px;
  }

  .usecase-card-title {
    font-size: 14px;
    font-weight: 600;
    color: #f0f6fc;
    margin-bottom: 6px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .usecase-card-title .uc-icon {
    font-size: 16px;
  }

  .usecase-card p {
    font-size: 13px;
    color: #8b949e;
    line-height: 1.65;
    margin: 0;
  }

  /* ── GETTING STARTED ── */
  .code-block {
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 8px;
    padding: 16px 20px;
    font-family: 'Courier New', monospace;
    font-size: 13px;
    color: #c9d1d9;
    overflow-x: auto;
    line-height: 1.7;
    margin-bottom: 16px;
  }

  .code-block .comment { color: #8b949e; }
  .code-block .kw      { color: #ff7b72; }
  .code-block .fn      { color: #d2a8ff; }
  .code-block .str     { color: #a5d6ff; }
  .code-block .var     { color: #79c0ff; }

  /* ── NOTES ── */
  .note-card {
    background: #161b22;
    border: 1px solid #21262d;
    border-left: 3px solid #e3b341;
    border-radius: 0 8px 8px 0;
    padding: 14px 16px;
    margin-bottom: 12px;
  }

  .note-card-title {
    font-size: 13px;
    font-weight: 600;
    color: #e3b341;
    margin-bottom: 6px;
    display: flex;
    align-items: center;
    gap: 7px;
  }

  .note-card p {
    font-size: 13.5px;
    color: #8b949e;
    line-height: 1.65;
    margin: 0;
  }

  /* ── LICENSE ── */
  .license-box {
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 8px;
    padding: 16px 20px;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .license-icon { font-size: 28px; }

  .license-info h4 {
    font-size: 14px;
    font-weight: 600;
    color: #f0f6fc;
    margin-bottom: 4px;
  }

  .license-info p {
    font-size: 13px;
    color: #8b949e;
    margin: 0;
  }

  /* ── FOOTER ── */
  .footer {
    margin-top: 48px;
    padding-top: 20px;
    border-top: 1px solid #21262d;
    text-align: center;
    font-size: 12px;
    color: #484f58;
    letter-spacing: 0.04em;
  }

  /* ── INLINE HIGHLIGHT ── */
  .hl { color: #f0f6fc; font-weight: 500; }

  @media (max-width: 600px) {
    .usecase-grid { grid-template-columns: 1fr; }
    .page { padding: 24px 16px 60px; }
    .header-title { font-size: 22px; }
  }
</style>
</head>
<body>
<div class="page">

  <!-- HEADER -->
  <div class="header">
    <div class="header-title-row">
      <span class="header-icon">📈</span>
      <h1 class="header-title">Tata Motors Historical Stock Price Dataset</h1>
    </div>
    <p class="header-desc">
      A longitudinal daily price history for NSE-listed TATAMOTORS spanning January 1995 to August 2025 — 
      enriched with OHLCV data, market microstructure metrics, and pre-computed technical indicators, 
      built for time-series forecasting, algorithmic strategy development, and machine learning research.
    </p>
    <div class="tag-row">
      <span class="tag"><span class="tag-label">Type</span><span class="tag-value tv-blue">Time-Series</span></span>
      <span class="tag"><span class="tag-label">Domain</span><span class="tag-value tv-orange">Finance &amp; Equity Markets</span></span>
      <span class="tag"><span class="tag-label">Granularity</span><span class="tag-value tv-green">Daily (Trading Session)</span></span>
      <span class="tag"><span class="tag-label">Format</span><span class="tag-value tv-gray">CSV</span></span>
    </div>
  </div>

  <!-- TABLE OF CONTENTS -->
  <div class="section" id="toc">
    <h2 class="section-heading"><span class="icon">📋</span> Table of Contents</h2>
    <ul class="toc-list">
      <li><a href="#overview">Overview</a></li>
      <li><a href="#about">About Tata Motors</a></li>
      <li><a href="#composition">Dataset Composition</a></li>
      <li><a href="#features">Feature Reference</a></li>
      <li><a href="#usecases">Use Cases</a></li>
      <li><a href="#getting-started">Getting Started</a></li>
      <li><a href="#notes">Notes &amp; Considerations</a></li>
      <li><a href="#license">License</a></li>
    </ul>
  </div>

  <!-- OVERVIEW -->
  <div class="section" id="overview">
    <h2 class="section-heading"><span class="icon">📌</span> Overview</h2>
    <div class="prose">
      <p>
        For over three decades, <span class="hl">Tata Motors Limited</span> has stood as one of the most closely watched 
        equities on the National Stock Exchange of India — a bellwether for the country's automotive sector, a barometer 
        of domestic consumption, and a stock that has moved markets with every strategic decision from the landmark 
        acquisition of Jaguar Land Rover in 2008 to its ongoing transformation into an electric vehicle powerhouse.
      </p>
      <p>
        This dataset captures that entire journey. Compiled from official NSE records and spanning 
        <span class="hl">January 1995 through August 2025</span>, this is a longitudinal daily price history containing 
        over <span class="hl">7,500 trading sessions</span> of OHLCV data, market microstructure metrics, and 
        pre-computed technical indicators — cleaned, enriched, and structured for immediate use in quantitative research, 
        financial modelling, and machine learning applications.
      </p>
    </div>
  </div>

  <!-- ABOUT THE COMPANY -->
  <div class="section" id="about">
    <h2 class="section-heading"><span class="icon">🏭</span> About Tata Motors</h2>
    <div class="prose">
      <p>
        Tata Motors Limited is the automotive flagship of the Tata Group, one of India's oldest and most diversified 
        industrial conglomerates. Headquartered in Mumbai, the company manufactures a broad portfolio spanning passenger 
        vehicles, commercial trucks, electric vehicles, and premium automotive brands through its wholly-owned subsidiary, 
        <span class="hl">Jaguar Land Rover</span>. As a constituent of the <span class="hl">NIFTY 50 index</span>, 
        TATAMOTORS is among the most liquid and institutionally traded equities on the NSE.
      </p>
      <p>
        The stock's 30-year trading record encompasses some of the most consequential moments in modern Indian financial 
        history — the post-liberalisation bull market of the late 1990s, the dot-com correction, the 2008 global financial 
        crisis, the JLR acquisition and its subsequent debt cycle, the COVID-19 pandemic shock and recovery of 2020–2021, 
        and the current structural re-rating driven by EV adoption and JLR's return to profitability. Each of these episodes 
        is legible in the data.
      </p>
    </div>
  </div>

  <!-- DATASET COMPOSITION -->
  <div class="section" id="composition">
    <h2 class="section-heading"><span class="icon">🗂️</span> Dataset Composition</h2>
    <table class="data-table">
      <thead>
        <tr>
          <th>Attribute</th>
          <th>Detail</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>Exchange</td><td>National Stock Exchange of India (NSE)</td></tr>
        <tr><td>Ticker Symbol</td><td>TATAMOTORS</td></tr>
        <tr><td>Asset Class</td><td>Equity — Large Cap / NIFTY 50 Constituent</td></tr>
        <tr><td>Data Frequency</td><td>Daily (per trading session)</td></tr>
        <tr><td>Coverage Period</td><td>January 1995 – August 2025</td></tr>
        <tr><td>Approximate Row Count</td><td>~7,500 trading sessions</td></tr>
        <tr><td>Total Feature Columns</td><td>14</td></tr>
        <tr><td>Missing Values</td><td>None (post-cleaning)</td></tr>
        <tr><td>File Format</td><td>CSV (UTF-8 encoded)</td></tr>
      </tbody>
    </table>
  </div>

  <!-- FEATURE REFERENCE -->
  <div class="section" id="features">
    <h2 class="section-heading"><span class="icon">🔬</span> Feature Reference</h2>

    <div class="feature-group">
      <div class="feature-group-title">Market Price Data</div>
      <ul class="feature-list">
        <li><span class="feat-name">Date</span><span class="feat-desc">Calendar date of the trading session, aligned to NSE market holidays. Format: YYYY-MM-DD.</span></li>
        <li><span class="feat-name">Symbol</span><span class="feat-desc">NSE ticker identifier. Consistently recorded as TATAMOTORS throughout the full dataset.</span></li>
        <li><span class="feat-name">Open</span><span class="feat-desc">Price at which the first executed trade occurred at session open, in Indian Rupees (₹).</span></li>
        <li><span class="feat-name">High</span><span class="feat-desc">Highest traded price recorded during the session, in ₹.</span></li>
        <li><span class="feat-name">Low</span><span class="feat-desc">Lowest traded price recorded during the session, in ₹.</span></li>
        <li><span class="feat-name">Close</span><span class="feat-desc">Official NSE-published closing price at end of session, in ₹.</span></li>
        <li><span class="feat-name">PrevClose</span><span class="feat-desc">Closing price from the immediately preceding trading session. Used as the basis for daily return calculation.</span></li>
      </ul>
    </div>

    <div class="feature-group">
      <div class="feature-group-title">Volume &amp; Market Microstructure</div>
      <ul class="feature-list">
        <li><span class="feat-name">Volume</span><span class="feat-desc">Total number of equity shares traded during the session. A key measure of market participation and liquidity.</span></li>
        <li><span class="feat-name">Turnover</span><span class="feat-desc">Aggregate monetary value of all trades executed during the session, denominated in ₹. Reflects total capital flow through the stock on a given day.</span></li>
        <li><span class="feat-name">VWAP</span><span class="feat-desc">Volume Weighted Average Price — calculated as total turnover divided by total volume. Widely used as a benchmark in institutional order execution.</span></li>
        <li><span class="feat-name">Trades</span><span class="feat-desc">Number of discrete order matches executed during the session. Serves as a proxy for depth of market participation beyond raw volume.</span></li>
      </ul>
    </div>

    <div class="feature-group">
      <div class="feature-group-title">Derived &amp; Technical Features</div>
      <ul class="feature-list">
        <li><span class="feat-name">Daily_Return_%</span><span class="feat-desc">Single-session percentage return, computed as the percentage change from PrevClose to Close. Represents the raw daily return for a buy-and-hold position.</span></li>
        <li><span class="feat-name">Cumulative_Return_%</span><span class="feat-desc">Running compounded return indexed from the first record in the dataset. Provides a continuous performance trajectory across the full 30-year span.</span></li>
        <li><span class="feat-name">MA_20</span><span class="feat-desc">20-session simple moving average of the daily closing price. A standard short-term trend indicator for momentum and dynamic support/resistance analysis.</span></li>
        <li><span class="feat-name">MA_50</span><span class="feat-desc">50-session simple moving average of the daily closing price. Represents medium-term price trend, widely used in crossover-based trading systems.</span></li>
      </ul>
    </div>
  </div>

  <!-- USE CASES -->
  <div class="section" id="usecases">
    <h2 class="section-heading"><span class="icon">🎯</span> Use Cases</h2>
    <div class="usecase-grid">
      <div class="usecase-card">
        <div class="usecase-card-title"><span class="uc-icon">📉</span> Time-Series Forecasting</div>
        <p>Train and evaluate autoregressive models (ARIMA, SARIMA), deep learning architectures (LSTM, GRU, Temporal Fusion Transformer), and modern sequence models on 30 years of daily close data across structurally distinct market regimes.</p>
      </div>
      <div class="usecase-card">
        <div class="usecase-card-title"><span class="uc-icon">⚙️</span> Algorithmic Strategy Backtesting</div>
        <p>Design and backtest rule-based trading strategies — including MA crossover systems, momentum strategies, mean-reversion signals, and volume-confirmation filters — against authentic, exchange-sourced price history.</p>
      </div>
      <div class="usecase-card">
        <div class="usecase-card-title"><span class="uc-icon">🤖</span> Machine Learning for Return Prediction</div>
        <p>Use OHLCV data, VWAP, trade counts, daily returns, and moving averages as direct model features or inputs to feature engineering pipelines for classification or regression models targeting directional price movement.</p>
      </div>
      <div class="usecase-card">
        <div class="usecase-card-title"><span class="uc-icon">📊</span> Volatility &amp; Risk Analysis</div>
        <p>Compute rolling volatility measures, historical Value-at-Risk (VaR), Conditional VaR (CVaR), maximum drawdown profiles, and Sharpe/Sortino ratios across different investment horizons and market regimes.</p>
      </div>
      <div class="usecase-card">
        <div class="usecase-card-title"><span class="uc-icon">🔍</span> Exploratory Data Analysis</div>
        <p>Conduct price trend analysis, volume seasonality studies, return distribution modelling, autocorrelation structure analysis, and long-run performance attribution using the full breadth of included features.</p>
      </div>
      <div class="usecase-card">
        <div class="usecase-card-title"><span class="uc-icon">🎓</span> Financial &amp; Academic Research</div>
        <p>Suitable for event studies around corporate announcements, sector-level research in emerging market equities, and analysis of the relationship between market microstructure metrics and price outcomes.</p>
      </div>
    </div>
  </div>

  <!-- GETTING STARTED -->
  <div class="section" id="getting-started">
    <h2 class="section-heading"><span class="icon">🚀</span> Getting Started</h2>
    <div class="prose">
      <p>Load the dataset and begin exploration with the following Python snippet:</p>
    </div>
    <div class="code-block">
<span class="comment"># Load the dataset</span>
<span class="kw">import</span> <span class="var">pandas</span> <span class="kw">as</span> <span class="var">pd</span>
<span class="kw">import</span> <span class="var">matplotlib.pyplot</span> <span class="kw">as</span> <span class="var">plt</span>

<span class="var">df</span> = <span class="var">pd</span>.<span class="fn">read_csv</span>(<span class="str">'tatamotors_historical.csv'</span>, parse_dates=[<span class="str">'Date'</span>])
<span class="var">df</span>.<span class="fn">set_index</span>(<span class="str">'Date'</span>, inplace=<span class="kw">True</span>)

<span class="comment"># Quick overview</span>
<span class="fn">print</span>(<span class="var">df</span>.shape)       <span class="comment"># (~7500, 13)</span>
<span class="fn">print</span>(<span class="var">df</span>.<span class="fn">head</span>())
<span class="fn">print</span>(<span class="var">df</span>.<span class="fn">describe</span>())

<span class="comment"># Plot closing price with moving averages</span>
<span class="var">fig</span>, <span class="var">ax</span> = <span class="var">plt</span>.<span class="fn">subplots</span>(figsize=(<span class="str">14, 5</span>))
<span class="var">ax</span>.<span class="fn">plot</span>(<span class="var">df</span>[<span class="str">'Close'</span>], label=<span class="str">'Close'</span>, linewidth=<span class="str">0.9</span>, color=<span class="str">'#58a6ff'</span>)
<span class="var">ax</span>.<span class="fn">plot</span>(<span class="var">df</span>[<span class="str">'MA_20'</span>], label=<span class="str">'MA 20'</span>, linewidth=<span class="str">1.2</span>, color=<span class="str">'#e3b341'</span>)
<span class="var">ax</span>.<span class="fn">plot</span>(<span class="var">df</span>[<span class="str">'MA_50'</span>], label=<span class="str">'MA 50'</span>, linewidth=<span class="str">1.2</span>, color=<span class="str">'#ff7b72'</span>)
<span class="var">ax</span>.<span class="fn">legend</span>()
<span class="var">plt</span>.<span class="fn">title</span>(<span class="str">'TATAMOTORS — Daily Close with Moving Averages (1995–2025)'</span>)
<span class="var">plt</span>.<span class="fn">tight_layout</span>()
<span class="var">plt</span>.<span class="fn">show</span>()
    </div>
  </div>

  <!-- NOTES & CONSIDERATIONS -->
  <div class="section" id="notes">
    <h2 class="section-heading"><span class="icon">⚠️</span> Notes &amp; Considerations</h2>

    <div class="note-card">
      <div class="note-card-title">⚠️ Moving Average Warm-Up Removal</div>
      <p>The first 50 rows of raw data — where MA_20 and MA_50 carry NaN values due to their respective look-back window requirements — have been excluded from the final dataset. All retained rows are fully populated across every column with no leading missing values.</p>
    </div>

    <div class="note-card">
      <div class="note-card-title">⚠️ No Imputation Applied</div>
      <p>Price, volume, and turnover columns reflect official NSE-published figures without any imputation, interpolation, or forward-filling. The data is presented exactly as recorded. There are no synthetic or estimated values in the dataset.</p>
    </div>

    <div class="note-card">
      <div class="note-card-title">⚠️ Return Calculation Basis</div>
      <p>Daily_Return_% and Cumulative_Return_% have been derived directly from NSE-recorded Close and PrevClose values. No adjustment for dividends, bonus issues, rights entitlements, or stock splits has been applied beyond what is already reflected in the NSE's official historical records.</p>
    </div>

    <div class="note-card">
      <div class="note-card-title">⚠️ Corporate Action Advisory</div>
      <p>Users constructing long-run return series or comparing absolute price levels across distant time periods should independently verify and account for the full history of corporate actions affecting TATAMOTORS — including stock splits, bonus share issuances, and rights issues — to ensure price continuity where required by their specific methodology.</p>
    </div>
  </div>

  <!-- LICENSE -->
  <div class="section" id="license">
    <h2 class="section-heading"><span class="icon">📄</span> License</h2>
    <div class="license-box">
      <span class="license-icon">🔓</span>
      <div class="license-info">
        <h4>Community Data License Agreement (CDLA) — Permissive, Version 2.0</h4>
        <p>This dataset is made available for open use in research, education, and non-commercial applications. Users are free to use, modify, and redistribute with attribution. Data sourced from the National Stock Exchange of India (NSE). All rights in original exchange data remain with NSE.</p>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    National Stock Exchange of India &nbsp;·&nbsp; TATAMOTORS &nbsp;·&nbsp; Equity &nbsp;·&nbsp; Daily Frequency &nbsp;·&nbsp; January 1995 – August 2025
  </div>

</div>
</body>
</html>

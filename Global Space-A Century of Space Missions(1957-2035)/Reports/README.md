# 🚀 Global Space Missions Dataset — Exploratory Data Analysis Report

> A comprehensive statistical and visual analysis of **10,500+ space missions** spanning **1957–2035**, covering mission status, agency performance, launch vehicle usage, cost distributions, temporal growth trends, and predictive forecasting.

---

## 📋 Report Overview

| Property | Detail |
|----------|--------|
| **Records** | 10,500+ space mission records |
| **Features** | 26 attributes per record |
| **Time Span** | 1957 – 2035+ (historical, ongoing, and projected) |
| **Agencies** | 12 major agencies + joint missions |
| **Data Type** | Synthetic / Balanced |
| **Format** | CSV, UTF-8 comma-delimited |
| **Version** | 1.0 — May 2026 |

### Mission Phase Breakdown

| Phase | Count | Period |
|-------|-------|--------|
| ✅ Past | ~6,835 | 1957 – 2023 |
| 🔄 Ongoing | ~2,105 | 2020 – 2026 |
| 🔜 Future / Upcoming | ~1,560 | 2026 – 2035+ |

---

## 🗂️ Project Structure

```
space-missions-eda/
│
├── Space_Missions_Dataset.csv        # Source dataset
├── eda_analysis.ipynb                # Main analysis notebook
├── Space_Missions_EDA_Report.docx    # Full visual report (18 charts)
└── README.md                         # Project documentation
```

---

## 🧹 Data Cleaning

Missing values were handled before analysis as follows:

| Column | Treatment |
|--------|-----------|
| `Duration` | Filled with `0` |
| `Crew_Members` | Filled with `0` |
| `Partner_Agencies` | Filled with `'None'` |
| `Failure_Reason` | Filled with `'Successful Mission'` |
| `Key_Achievement` | Filled with `'Not Specified'` |
| `End_Date` | Filled with `'Ongoing'` |
| `Data_Returned` | Filled with `0` |

---

## 📊 Analyses Performed (18 Visualisations)

### Section 3 — Exploratory Visualisations

| # | Analysis | Key Finding |
|---|----------|-------------|
| 3.1 | Mission Status Distribution | Success dominates at ~4,350 missions (~41%); Failed = ~8.7% |
| 3.2 | Agency Mission Launch Counts | NASA leads (~980); SpaceX close second (~950) |
| 3.3 | Mission Category Distribution | All 19 categories within a ~95-mission band — balanced synthetic sampling |
| 3.4 | Launch Vehicle Usage Share | Ariane 5 leads at 20.2%; Ariane family holds 35% combined |
| 3.5 | Mission Cost Distribution | Median ~$7,500M; near-uniform violin shape — synthetic artefact |
| 3.6 | Crew Type Proportion | 74.9% Uncrewed vs. 25.1% Crewed — crewed share ~3–5× real-world rates |
| 3.7 | Top Mission Destinations | Mercury leads (~598) — contradicts reality (only 3 real Mercury missions) |
| 3.8 | Mission Growth Over Time | 60-year flatline → 4× surge to ~460 missions by 2026 |
| 3.9 | Agency Type Contribution | Government ~82% vs. Private ~18% |
| 3.10 | Top Countries in Space Missions | USA leads at ~2,800 — nearly 3× every other nation |

### Section 4 — Forecasting & Predictive Analysis

| # | Analysis | Key Finding |
|---|----------|-------------|
| 4.1 | Future Mission Trend Forecast | 3-year rolling average; post-2028 stabilisation at ~150–170/year |
| 4.2 | Mission Cost Trend Prediction | Regression nearly flat (+$200M over 78 years); R² very low |
| 4.3 | Mission Success Rate Trend | Stable 0.60–0.82 until 2018; post-2018 collapse is a labelling artefact |
| 4.4 | Future Launch Vehicle Demand | Fixed ~18–20% forecast uplift across all vehicles — formulaic, not demand-driven |

### Section 5 — Advanced Analysis

| # | Analysis | Key Finding |
|---|----------|-------------|
| 5.1 | Agency Cost Efficiency | ISRO/JAXA most efficient at ~$900M; SpaceX least at ~$7,350M |
| 5.4 | Cost Outliers — Boxplot | Zero outliers detected via IQR; symmetric IQR = $7,200M wide |
| 5.5 | Cost Trend Over Time | Oscillates in $6,500M–$8,500M band; no inflation signal; white noise pattern |
| 5.6 | Yearly Mission Growth | Double-peak structure (2020, 2026); post-2028 floor ~50% above pre-2018 baseline |

---

## 📐 Statistical Summary — Cost Distribution

| Metric | Value |
|--------|-------|
| Skewness | ~0.0 (near-perfect symmetry) |
| Kurtosis | ~-1.2 (platykurtic — confirms uniform sampling) |
| Mean | ~$7,500M |
| Median | ~$7,500M |
| IQR | ~$7,200M |
| Range | $0M to ~$15,000M |
| Outliers Detected | **None** (IQR and Z-score methods both return zero) |

---

## 🏆 Top-Level Findings

1. **US Dominance** — The USA accounts for ~2,800 missions (3:1 margin over every other nation), amplified by NASA, DoD, SpaceX, and Blue Origin combined.
2. **Commercial Disruption** — SpaceX rose to second-place agency ranking within 22 years of founding, nearly matching NASA's historical mission count.
3. **Volume Regime Change** — Annual missions surged 4× from ~115 (2018) to ~460 (2026), marking a structural transition driven by commercial megaconstellations.
4. **Cost Anomaly** — Mission cost data shows no real-world dynamics (no inflation, no commercial cost reduction) — the clearest signal of synthetic data generation.
5. **ISRO Efficiency** — ISRO-linked collaborations deliver the lowest average mission costs (~$900M), validating India's global reputation for frugal engineering.
6. **Synthetic Limitations** — All categories, destinations, launch vehicles, and agency rankings fall within narrow balanced bands — the dataset is built for ML practice, not real-world analysis.

---

## ⚠️ Dataset Limitations

> This dataset is **synthetic and intentionally balanced**. Key deviations from real-world spaceflight data:

| Category | Limitation |
|----------|------------|
| **Destinations** | Uniformly distributed — Mercury equals Earth Orbit in count; Earth Orbit dominates in reality by orders of magnitude |
| **Mission Costs** | No inflationary trend over 78 years; no post-2015 commercial reduction — contradicts SpaceX's 60–90% cost disruption |
| **Crewed Proportion** | 25.1% crewed vs. ~5–8% in real-world spaceflight history |
| **Success Rate** | Collapses post-2018 due to unresolved future mission labels — not a genuine performance decline |
| **Agency Rankings** | Reflect balanced sampling, not true historical launch volumes |
| **Launch Vehicle** | Ariane 5 leads despite retirement in 2023; New Shepard far exceeds its real-world ~25 flights |
| **Future Missions** | Post-2028 volume collapse may be a dataset boundary effect, not genuine market contraction |

---

## ✅ Recommended Use Cases

- Machine learning classification and regression benchmarking (success prediction, cost estimation, destination classification)
- Data visualisation skill-building and dashboard development practice
- EDA methodology training — cleaning, outlier detection, time series analysis
- STEM education and interactive space exploration storytelling

---

## 🛠️ Dependencies

```
pandas
numpy
matplotlib
seaborn
scikit-learn
scipy
```

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

---

## 🚀 Quick Start

```python
import pandas as pd

df = pd.read_csv('Space_Missions_Dataset.csv')
df['Launch_Date'] = pd.to_datetime(df['Launch_Date'])
df.info()
df.describe(include='all')
```

---

## 📄 License

For educational and analytical purposes only. Dataset origin: synthetic, generated for practice use.
All mission names, agency identifiers, and historical references are derived from publicly available information.

---

*Global Space Missions Dataset  |  EDA Report v1.0  |  May 2026*

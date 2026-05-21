![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/b1aaba4d4b2e952f1daa57828250bfc2b53e5d14/Global%20Space-A%20Century%20of%20Space%20Missions(1957-2035)/Dataset%20Cover.jpg)

# 🚀 Global Space Missions Dataset — Exploratory Data Analysis

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Viz-4C72B0?style=for-the-badge&logo=python&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Charting-11557C?style=for-the-badge&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML%20Models-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-Statistics-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)
![Dataset](https://img.shields.io/badge/Dataset-10%2C500%2B%20Missions-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

---

## Overview

This notebook delivers a full **Exploratory Data Analysis (EDA)** of the Global Space Missions Dataset — a structured collection of 10,500+ mission records spanning 1957 to 2035+. The analysis covers data cleaning, univariate and bivariate exploration, time-series trend analysis, cost modelling, outlier detection, and forward-looking forecasts across 15 visualisation sections.

Every chart is accompanied by professional analyst-grade insights examining not only what the data shows, but why it matters — including explicit flags where dataset construction patterns deviate from real-world spaceflight dynamics.

---

## Dataset

| Property | Value |
|----------|-------|
| File | `Space_Missions_Dataset.csv` |
| Records | 10,500+ |
| Features | 26 columns |
| Time Span | 1957 – 2035+ |
| Agencies | 12 + Joint Missions |

---

## Libraries Used

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, cleaning, aggregation, filtering |
| `matplotlib` | Figure management, area charts, bar charts |
| `seaborn` | Count plots, violin plots, box plots, line plots |
| `numpy` | Numerical operations and array handling |
| `scikit-learn` | Linear regression for cost trend prediction |
| `scipy.stats` | Skewness, kurtosis, z-score outlier detection |

---

## Data Cleaning

The following preprocessing steps were applied before analysis:

| Column | Treatment |
|--------|-----------|
| `Duration` | Null values filled with `0` |
| `Crew_Members` | Null values filled with `0` |
| `Partner_Agencies` | Null values filled with `'None'` |
| `Failure_Reason` | Null values filled with `'Successful Mission'` |
| `Key_Achievement` | Null values filled with `'Not Specified'` |
| `End_Date` | Null values filled with `'Ongoing'` |
| `Data_Returned` | Null values filled with `0` |
| `Launch_Date` | Parsed to `datetime` for all time-series analyses |

---

## Analysis Sections

| # | Question | Chart Type | Key Finding |
|---|----------|------------|-------------|
| 1 | Which mission statuses occur most frequently? | Count plot | Success dominates at ~41%; Partial Success is smallest at ~6% |
| 2 | Which agencies launched the most missions? | Horizontal bar | NASA leads (~980); SpaceX second (~950) ahead of all government agencies |
| 3 | What are the most common mission categories? | Count plot | All 19 categories compressed into ~500–595 range — balanced sampling confirmed |
| 4 | Which launch vehicles are most used? | Donut chart | Ariane 5 leads at 20.2%; Ariane family combined holds 35% |
| 5 | How is mission cost distributed? | Violin plot | Uniform rectangular distribution — synthetic cost generation confirmed |
| 6 | What is the distribution of crew types? | Donut chart | 74.9% Uncrewed vs 25.1% Crewed — crewed share elevated vs real-world |
| 7 | Which destinations are most targeted? | Lollipop chart | Mercury leads — contradicts real-world history; ~40-mission range across all destinations |
| 8 | How have missions changed over time? | Area line chart | Flat 60-year plateau → 4.4× surge to 460 missions at 2026 peak |
| 9 | Which agency types dominate? | Bar chart | Government 82% vs Private 18% — historical ratio, not current market |
| 10 | Which countries lead in space missions? | Horizontal bar | USA (~2,800) leads by 3×; remaining 9 countries within 160-mission band |
| 11 | How will missions grow in the future? | Dual line + forecast | 4× surge 2018–2026; 70% collapse 2026–2028; new floor ~150–175 |
| 12 | How will mission cost change over time? | Scatter + regression | Near-flat $200M rise over 78 years — cost is time-independent in this dataset |
| 13 | Will missions become more successful? | Line chart | Stable 0.60–0.82 through 2018; collapse to 0.0 post-2023 is a labelling artefact |
| 14 | Which rockets will dominate future launches? | Stacked bar | Ariane 5 leads despite retirement; Falcon 9 understated vs real-world dominance |
| 15 | Which agencies are most cost-efficient? | Line chart | ISRO/JAXA most efficient (~$900M); SpaceX least efficient (~$7,350M) |

---

## Advanced Analysis

Beyond the 15 core visualisations, the notebook includes the following deeper explorations:

**Cost Analysis**
- Average mission cost by Agency Type × Mission Category cross-tabulation
- Cost comparison pivot table: Agency Type vs Mission Status
- IQR-based outlier detection — no outliers flagged due to uniform distribution
- Z-score outlier detection (threshold: |z| > 3)
- Cost trend over time with mean-reversion pattern confirmed

**Failure Analysis**
- Agency type failure rate cross-tabulation (normalised by row)
- Government vs Private failure rate comparison

**Distribution Analysis**
- Skewness and kurtosis of `Cost_USD_Million`
- Box plot outlier visualisation

**Performance Aggregation**
- Agency-level cost summary: mean, sum, max
- Success rate by agency type (percentage normalised)

**Utility Operations**
- Random sampling, memory usage profiling
- Sort by cost descending
- Query filtering (`Cost_USD_Million > 1000`)
- Derived feature engineering: `Cost_per_Day = Cost_USD_Million / Duration`

---

## Key Analytical Findings

---

## Dataset Limitations & Analyst Notes

> The following limitations should be considered before using this dataset for operational or research purposes.

**Synthetic Cost Distribution** — `Cost_USD_Million` follows a near-uniform distribution between ~$0 and ~$16,000M. Real-world mission costs are heavily right-skewed. Standard statistical methods assuming normality will produce unreliable results on this variable.

**Balanced Category Sampling** — All mission categories, destinations, and agencies are represented in near-equal counts. Real-world distributions are highly skewed. Do not use raw category counts as proxies for market share or historical frequency.

**Future Mission Labelling** — Missions classified as Upcoming or Future have no resolved outcomes. Including them in success rate calculations drives the metric toward zero — filter to `Mission_Phase = 'Past'` before any success rate analysis.

**Private Sector Underrepresentation** — The aggregate 18% private share is a time-averaged figure suppressed by six decades of government-only records. Post-2015 analysis will show a substantially higher private share.

**Retired Vehicle Forecasts** — Ariane 5 appears with a positive forecast segment despite retirement in 2023. Treat this as a labelling artefact and apply retirement flags before any demand forecasting work.

---

## How to Run

```bash
# Install dependencies
pip install pandas matplotlib seaborn numpy scikit-learn scipy

# Launch notebook
jupyter notebook Space_Missions_EDA.ipynb
```

**Input file required:** `Space_Missions_Dataset.csv` in the same directory as the notebook.

---

## Output

The notebook produces 15 primary visualisations and 8+ advanced analytical outputs, all rendered inline. No external output files are generated unless explicitly exported.

---

*Prepared by the Data Analytics Division · Global Space Missions EDA · May 2026*

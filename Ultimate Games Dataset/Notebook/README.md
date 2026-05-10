# 🎮 Ultimate Games Dataset — Exploratory Data Analysis

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13-4C72B0)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-11557c)
![Plotly](https://img.shields.io/badge/Plotly-5.x-3F4F75?logo=plotly&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![License](https://img.shields.io/badge/License-MIT-green)
![Dataset](https://img.shields.io/badge/Dataset-15%2C000%20Games-purple)

A structured, insight-driven Exploratory Data Analysis on the **Ultimate Games Dataset** — 15,000 video games spanning 1979 to 2026 across 43 features. This notebook covers data cleaning, univariate and multivariate analysis, outlier detection, correlation intelligence, and publisher/platform profiling.

---

## 📁 Project Structure

```
📦 ultimate-games-eda/
├── 📓 eda_games.ipynb          # Main analysis notebook
├── 📄 ultimate_games_dataset.csv
└── 📄 README.md
```

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Setup & Installation](#-setup--installation)
- [Data Cleaning](#-data-cleaning)
- [Analysis Sections](#-analysis-sections)
- [Key Findings](#-key-findings)
- [Libraries Used](#-libraries-used)
- [Dataset Reference](#-dataset-reference)

---

## 🔍 Overview

This EDA explores the full breadth of the Ultimate Games Dataset to answer meaningful questions about the gaming industry — how genres have evolved, how critics and users diverge, how platform reach affects popularity, and where engagement truly concentrates. Each section includes a visualization paired with structured, domain-relevant insights.

---

## ⚙️ Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/your-username/ultimate-games-eda.git
cd ultimate-games-eda
```

**2. Install dependencies**
```bash
pip install pandas matplotlib seaborn plotly scipy streamlit
```

**3. Launch the notebook**
```bash
jupyter notebook eda_games.ipynb
```

> Ensure `ultimate_games_dataset.csv` is placed in the same directory as the notebook before running.

---

## 🧹 Data Cleaning

| Step | Action |
|---|---|
| Null handling — `user_rating` (2.58%) | Filled with column mean |
| Null handling — `metacritic` (5.91%) | Filled with column mean |
| Duplicate check | No duplicates found |
| Date parsing | `release_date` converted to `datetime` |

> **Note:** `avg_playtime_hours = 0` for 1,063 games and `ratings_count = 0` for 2,161 games are **not** errors — they reflect missing tracking data, not literal zero values.

---

## 📊 Analysis Sections

### 1. 🎯 Genre Dominance Analysis
Bar chart of the top 10 genre combinations by game count.
- Hybrid genres (e.g., *Adventure|Indie*, *Casual|Indie*) consistently outperform standalone categories
- Players demonstrably prefer multi-genre experiences over single-genre titles

---

### 2. 📅 Game Releases Over Time
Line plot of annual game releases from 1979 to 2026.
- Near-zero output pre-2000 reflecting high entry barriers and hardware-controlled markets
- Peak at ~1,600 releases around 2015–2016 driven by Steam Greenlight's low-barrier model
- Post-2022 decline is a **dataset recency lag artifact**, not a real market contraction

---

### 3. ⭐ User Rating Distribution
Histogram with KDE overlay of user ratings across all games.
- Left-skewed distribution — users rate generously, with most scores between 3.5–4.0
- Ratings below 2.0 are rare, suggesting positivity bias or abstention by dissatisfied users
- Near-perfect scores (4.5+) are reserved, lending weight to highly-rated titles

---

### 4. 🆚 Critic vs User Ratings (Scatter)
Scatter plot of Metacritic score vs. user rating, segmented by multiplayer status.
- Weak-to-moderate positive correlation between critic and user scores
- Highest disagreement occurs in the 50–75 Metacritic range
- Multiplayer titles cluster in the 60–90 critic score band

---

### 5. 🎮 Multiplayer Effect on Ratings (Box Plot)
Box plot comparing user rating distributions for multiplayer vs. single-player games.
- Single-player median (~3.5) consistently exceeds multiplayer median (~3.2)
- Multiplayer games exhibit wider IQR, reflecting higher satisfaction inconsistency
- Peak scores (4.75–5.0) are achievable in both categories — excellence is format-agnostic

---

### 6. 🌍 Platform Reach vs Popularity (Regression)
Regression plot of platform count against popularity score.
- Clear positive relationship: broader platform availability correlates with higher popularity
- High-variance scatter at every platform count — availability alone doesn't guarantee success
- Highest scores appear at mid-range platform counts (5–8), not at the maximum

---

### 7. 🔞 ESRB Rating Distribution
Count plot of game distribution across ESRB content categories.
- **Not Rated** dominates at 10,205 games — most indie/digital titles skip ESRB classification
- Teen (T) leads among rated categories at 1,575 games
- Adults Only (AO) remains commercially marginal due to platform and retail restrictions

---

### 8. 🔥 Engagement Score Density (KDE)
KDE plot of the engagement score distribution across all games.
- Severe right-skew — the vast majority of titles generate near-zero sustained engagement
- A few breakout titles with scores of 30–45+ drive a disproportionate share of player hours
- Classic long-tail / power-law dynamics confirmed across the full dataset

---

### 9. 🌡️ Correlation Intelligence Heatmap
Heatmap of Pearson correlations across 7 key numerical variables.

| Pair | Correlation | Implication |
|---|---|---|
| `ratings_count` ↔ `reviews_count` | **0.99** | Near-perfect redundancy |
| `library_count` ↔ `ratings_count` | **0.91** | Strong engagement funnel |
| `user_rating` ↔ `metacritic` | **0.66** | Related but divergent |
| `avg_playtime_hours` ↔ all others | **0.12–0.19** | Playtime is genre-driven, not popularity-driven |

---

### 10. 🏢 Publisher Market Share
Horizontal bar chart of the top 10 publishers by game volume.
- EA and Ubisoft lead named publishers — high-volume franchise strategy confirmed
- Nintendo ranks third by volume but punches above its weight in quality metrics
- "Not Specified" entries at ~1,500 games represent a significant metadata gap

---

### 11. 🕐 Game Production by Decade
Bar chart of total games released per decade from the 1970s to 2020s.
- 1970s: **2** games → 2010s: **8,571** games — a 4,285× increase
- The 2020s are already at 4,453 with half the decade remaining
- Each decade from 1980–2000 delivered roughly 3× the output of its predecessor

---

### 12. ⏱️ Playtime Outlier Detection
Box plot of average playtime hours highlighting the outlier distribution.
- Core IQR compressed near 0–10 hours — most games are short-form experiences
- Outliers begin around 130–150 hours; extreme cases extend to ~370 hours
- Near-zero median may reflect records defaulting to zero due to missing tracking data

---

### 13. 🎵 Popularity Across Game Modes (Violin Plot)
Violin plot of popularity score distribution across four game mode categories.
- Single + Multiplayer hybrid titles achieve the highest median popularity (~30)
- Single-player shows a distinctive bimodal distribution — high-risk, high-reward dynamics
- "Not Specified" entries show negative popularity scores — a composite scoring artifact

---

### 14. 🏆 Achievements vs Engagement (Scatter)
Scatter plot examining the relationship between achievement count and engagement score.
- Peak engagement (35–42) occurs in games with **fewer than 100** achievements
- Engagement flattens beyond 1,000 achievements — diminishing returns on achievement inflation
- Inverse correlation challenges the assumption that more achievements drive more engagement

---

### 15. 📐 Univariate & Statistical Analysis
Supplementary analyses including:
- Histogram distributions for `popularity_score`, `engagement_score`, and `release_year`
- Groupby aggregations by theme and game mode
- Pivot table of popularity by theme × game mode
- Crosstab of theme × rating tier (raw and normalized)
- IQR-based outlier detection on popularity score
- Skewness and kurtosis computation via `scipy.stats`
- Multi-platform game count analysis
- Top 10 games by popularity score
- Memory usage profiling
- `query()` and `eval()` demonstrations

---

## 💡 Key Findings

1. **Hybrid genres dominate** — multi-genre titles consistently outperform standalone categories in both volume and reception
2. **The gaming market is a power-law ecosystem** — a small minority of titles account for the majority of engagement, popularity, and player hours
3. **Critics and users agree moderately (r = 0.66)** — but diverge significantly for mid-tier titles in the 50–75 Metacritic range
4. **Playtime is genre-driven, not popularity-driven** — it shows near-zero correlation with every other engagement metric
5. **Achievement inflation is counterproductive** — peak engagement is achieved by games with fewer achievements, not more
6. **Platform breadth helps, but doesn't guarantee success** — content quality and timing remain decisive variables
7. **The 2010s were peak gaming** — 8,571 releases in a single decade, more than all prior decades combined

---

## 📦 Libraries Used

| Library | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, aggregation |
| `matplotlib` | Base plotting and figure control |
| `seaborn` | Statistical visualizations |
| `plotly` | Interactive charts |
| `scipy` | Skewness and kurtosis computation |
| `numpy` | Numerical operations |
| `streamlit` | Dashboard scaffolding (imported) |

---

## 📂 Dataset Reference

| Property | Value |
|---|---|
| Rows | 15,000 |
| Columns | 43 |
| Year Range | 1979 – 2026 |
| Format | CSV |
| License | MIT |

See the [dataset README](./DATASET_README.md) for full column documentation and null value notes.

---

<p align="center">
  Built for analysts, built for curiosity. 🕹️
</p>

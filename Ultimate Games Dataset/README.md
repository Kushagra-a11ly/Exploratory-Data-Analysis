![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/af9a362c8b71bbe91f9648d913aad419b8895aa7/Ultimate%20Games%20Dataset/Ultimate_Games_Dataset.png)

# 🎮 Ultimate Games Dataset — End-to-End Exploratory Data Analysis

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13-4C72B0?logo=python&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-11557c)
![Plotly](https://img.shields.io/badge/Plotly-5.x-3F4F75?logo=plotly&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.x-013243?logo=numpy&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-1.x-8CAAE6?logo=scipy&logoColor=white)

![Dataset](https://img.shields.io/badge/Dataset-15%2C000%20Games-purple)
![Features](https://img.shields.io/badge/Features-43%20Columns-blueviolet)
![Year Range](https://img.shields.io/badge/Years-1979–2026-orange)
![Format](https://img.shields.io/badge/Format-CSV-yellow)
![Purpose](https://img.shields.io/badge/Purpose-EDA%20Only-red)
![License](https://img.shields.io/badge/License-MIT-brightgreen)
![Status](https://img.shields.io/badge/Status-Complete-success)

</div>

<br/>

> A full-cycle, insight-driven Exploratory Data Analysis on **15,000 video games** spanning 1979 to 2026 — covering data profiling, cleaning, univariate and multivariate analysis, outlier detection, correlation intelligence, and domain-specific storytelling across 15 visualizations.

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Repository Structure](#-repository-structure)
- [Dataset Summary](#-dataset-summary)
- [Column Reference](#-column-reference)
- [Setup & Installation](#-setup--installation)
- [EDA Pipeline](#-eda-pipeline)
  - [Phase 1 — Data Profiling](#phase-1--data-profiling)
  - [Phase 2 — Data Cleaning](#phase-2--data-cleaning)
  - [Phase 3 — Univariate Analysis](#phase-3--univariate-analysis)
  - [Phase 4 — Bivariate & Multivariate Analysis](#phase-4--bivariate--multivariate-analysis)
  - [Phase 5 — Advanced Analytics](#phase-5--advanced-analytics)
- [Visualizations & Insights](#-visualizations--insights)
- [Key Findings](#-key-findings)
- [Libraries Used](#-libraries-used)
- [License](#-license)

---

## 🔍 Project Overview

The gaming industry has grown from a niche hobby in the late 1970s into one of the world's largest entertainment markets. This project applies a structured EDA methodology to uncover the patterns, anomalies, and dynamics embedded in a dataset of 15,000 games across 43 features — examining everything from genre evolution and publisher strategy to engagement behavior and the critic-versus-user divide.

Each analysis step is paired with structured, domain-relevant insights written for both data practitioners and gaming industry observers.

> ⚠️ **Intended Use:** This project and dataset are strictly for **Exploratory Data Analysis**. Not intended for commercial use or production systems.

---

## 📁 Repository Structure

```
📦 ultimate-games-eda/
├── 📓 eda_games.ipynb             # Complete EDA notebook (15 analyses)
├── 📄 ultimate_games_dataset.csv  # Source dataset — 15,000 rows × 43 cols
└── 📄 README.md                   # This file
```

---

## 📊 Dataset Summary

| Property | Value |
|---|---|
| **Rows** | 15,000 |
| **Columns** | 43 |
| **Year Range** | 1979 – 2026 |
| **File Format** | CSV |
| **License** | MIT |

### Null & Zero Value Reference

| Column | Issue | Volume | Interpretation |
|---|---|---|---|
| `user_rating` | Null | 2.58% | No user reviews — `rating_tier = 'unrated'` |
| `metacritic` | Null | 5.91% | Not listed on Metacritic — `metacritic_tier = 'no_score'` |
| `avg_playtime_hours` | Zero | 1,063 games | Missing tracking data — **not** literal zero hours played |
| `ratings_count` | Zero | 2,161 games | No community ratings recorded |

> These are **semantically meaningful** absences — not data entry errors. Handle them with domain awareness rather than blind imputation.

---

## 🗂 Column Reference

<details>
<summary><strong>🪪 Identity (6 columns)</strong></summary>

| Column | Description |
|---|---|
| `serial_no` | Sequential row identifier |
| `game_id` | Unique game identifier |
| `title` | Game title |
| `url_slug` | URL-safe version of the title |
| `cover_image_url` | Link to the game's cover art |
| `official_website` | Official game or developer website |

</details>

<details>
<summary><strong>📅 Release Info (3 columns)</strong></summary>

| Column | Description |
|---|---|
| `release_date` | Full release date |
| `release_year` | Year of release (integer) |
| `decade` | Decade of release (e.g., 1990s, 2000s) |

</details>

<details>
<summary><strong>🕹️ Game Characteristics (8 columns)</strong></summary>

| Column | Description |
|---|---|
| `all_genres` | Pipe-separated list of genres |
| `theme` | Primary thematic setting (e.g., fantasy, sci-fi) |
| `art_style` | Visual style (e.g., pixel art, 3D realistic) |
| `view_dimension` | Perspective type (e.g., 2D, 3D, isometric) |
| `game_mode` | Play modes supported (e.g., single-player, co-op) |
| `is_multiplayer` | Boolean — supports multiplayer |
| `is_multi_platform` | Boolean — available on multiple platforms |
| `controls` | Primary control scheme |

</details>

<details>
<summary><strong>🏢 Developers & Publishers (2 columns)</strong></summary>

| Column | Description |
|---|---|
| `developers` | Studio(s) that developed the game |
| `publishers` | Publisher(s) who released the game |

</details>

<details>
<summary><strong>🖥️ Platforms & Stores (3 columns)</strong></summary>

| Column | Description |
|---|---|
| `all_platforms` | All platforms the game is available on |
| `platform_count` | Number of platforms |
| `available_stores` | Digital storefronts (e.g., Steam, GOG, Epic) |

</details>

<details>
<summary><strong>⭐ Ratings & Reviews (7 columns)</strong></summary>

| Column | Description |
|---|---|
| `user_rating` | Community user rating (nullable) |
| `rating_tier` | Categorical tier (e.g., great, good, unrated) |
| `metacritic` | Metacritic critic score (nullable) |
| `metacritic_tier` | Categorical Metacritic tier |
| `ratings_count` | Number of user ratings submitted |
| `reviews_count` | Number of written reviews |
| `esrb_rating` | ESRB content rating (E, T, M, AO, etc.) |

</details>

<details>
<summary><strong>🔥 Engagement & Popularity (6 columns)</strong></summary>

| Column | Description |
|---|---|
| `popularity_score` | Derived popularity metric |
| `engagement_score` | Derived engagement metric |
| `library_count` | Number of users with this game in their library |
| `avg_playtime_hours` | Average hours played per user |
| `achievements_count` | Number of in-game achievements |
| `game_series_count` | Number of games in the same series |

</details>

<details>
<summary><strong>📋 Player Status Tracking (6 columns)</strong></summary>

| Column | Description |
|---|---|
| `status_owned` | Count of users who own the game |
| `status_beaten` | Count of users who have beaten it |
| `status_playing` | Count of users currently playing |
| `status_dropped` | Count of users who dropped it |
| `status_toplay` | Count of users planning to play |
| `status_yet` | Count of users yet to start |

</details>

<details>
<summary><strong>🏷️ Tags & Description (2 columns)</strong></summary>

| Column | Description |
|---|---|
| `all_tags` | Community and editorial tags |
| `description_clean` | Cleaned plain-text description |

</details>

---

## ⚙️ Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/your-username/ultimate-games-eda.git
cd ultimate-games-eda
```

**2. Install dependencies**
```bash
pip install pandas numpy matplotlib seaborn plotly scipy streamlit
```

**3. Launch the notebook**
```bash
jupyter notebook eda_games.ipynb
```

> Place `ultimate_games_dataset.csv` in the same directory as the notebook before running any cells.

---

## 🔬 EDA Pipeline

The analysis follows a structured five-phase pipeline, progressing from raw data understanding through to multivariate and statistical analysis.

```
Raw CSV  →  Phase 1: Profiling  →  Phase 2: Cleaning  →  Phase 3: Univariate
                                                               ↓
                                         Phase 5: Advanced  ←  Phase 4: Multivariate
```

---

### Phase 1 — Data Profiling

Initial inspection of the dataset's structure, completeness, and data types before any transformation.

```python
df = pd.read_csv('ultimate_games_dataset.csv')

df.shape          # (15000, 43)
df.dtypes         # Column type audit
df.info()         # Non-null counts per column
df.describe(include='all')  # Statistical summary
df.isnull().sum() # Null counts per column
df.duplicated().sum()       # Duplicate row check → 0
df.memory_usage(deep=True)  # Memory footprint
```

**Profiling outcomes:**
- 15,000 rows × 43 columns confirmed
- Zero duplicate rows detected
- Nulls isolated to `user_rating` (2.58%) and `metacritic` (5.91%)
- `release_date` stored as string — requires datetime conversion
- Semantic zeros identified in `avg_playtime_hours` and `ratings_count`

---

### Phase 2 — Data Cleaning

Targeted transformations based on profiling findings. Only necessary modifications applied — no aggressive preprocessing.

```python
# Null imputation
df['user_rating'] = df['user_rating'].fillna(df['user_rating'].mean())
df['metacritic']  = df['metacritic'].fillna(df['metacritic'].mean())

# Date type correction
df['release_date'] = pd.to_datetime(df['release_date'], errors='coerce')
```

| Step | Method | Rationale |
|---|---|---|
| `user_rating` nulls | Mean imputation | Preserves distribution center for EDA use |
| `metacritic` nulls | Mean imputation | Avoids skew from complete-case exclusion |
| Duplicate rows | None needed | Zero duplicates confirmed in profiling |
| Date parsing | `pd.to_datetime` | Enables temporal slicing and aggregation |
| Semantic zeros | Left as-is | `0` carries meaning — not treated as missing |

---

### Phase 3 — Univariate Analysis

Distribution-level examination of individual variables to understand shape, spread, and anomalies.

```python
# Numerical distributions
num_cols = ['popularity_score', 'engagement_score', 'release_year']
df[num_cols].hist(figsize=(12, 6), bins=20)

# Categorical frequency
df['esrb_rating'].value_counts()
df['decade'].value_counts().sort_index()
df['is_multi_platform'].value_counts()
```

**Distributions examined:**
- `popularity_score` — bell-shaped, right-truncated, bimodal tendency
- `engagement_score` — severely right-skewed, zero-concentrated
- `release_year` — exponential ramp from 2010 onward
- `user_rating` — left-skewed, modal peak at 3.75
- `esrb_rating` — dominated by unrated titles (10,205 of 15,000)

---

### Phase 4 — Bivariate & Multivariate Analysis

Cross-variable comparisons to reveal relationships, segment performance, and identify market dynamics.

```python
# Critic vs user ratings segmented by multiplayer
sns.scatterplot(data=df, x='metacritic', y='user_rating', hue='is_multiplayer')

# Platform reach vs popularity regression
sns.regplot(data=df, x='platform_count', y='popularity_score')

# Multiplayer vs single-player rating distributions
sns.boxplot(data=df, x='is_multiplayer', y='user_rating')

# Popularity by game mode
sns.violinplot(data=df, x='game_mode', y='popularity_score')

# Correlation heatmap
num = df[['user_rating', 'metacritic', 'ratings_count', 'reviews_count',
          'library_count', 'avg_playtime_hours', 'popularity_score']]
sns.heatmap(num.corr(), annot=True, cmap='Spectral')
```

---

### Phase 5 — Advanced Analytics

Statistical methods and aggregation techniques for deeper inference beyond visualization.

```python
# Groupby aggregation
df.groupby('theme')['popularity_score'].agg(['mean', 'sum', 'count'])
df.groupby(['theme', 'game_mode'])['engagement_score'].agg(['mean', 'max'])

# Pivot table
pd.pivot_table(df, values='popularity_score',
               index='theme', columns='game_mode', aggfunc='mean')

# Crosstab (raw + normalized)
pd.crosstab(df['theme'], df['rating_tier'])
pd.crosstab(df['theme'], df['rating_tier'], normalize='index') * 100

# IQR-based outlier detection
Q1, Q3 = df['popularity_score'].quantile([0.25, 0.75])
IQR = Q3 - Q1
outliers = df[(df['popularity_score'] < Q1 - 1.5*IQR) |
              (df['popularity_score'] > Q3 + 1.5*IQR)]

# Skewness & kurtosis
from scipy.stats import skew, kurtosis
print("Skewness:", skew(df['popularity_score']))
print("Kurtosis:", kurtosis(df['popularity_score']))

# Functional queries
df.query("popularity_score > 80")
df.eval("score_ratio = popularity_score / engagement_score")
```

---

## 📈 Visualizations & Insights

| # | Chart | Type | Key Takeaway |
|---|---|---|---|
| 1 | Genre Dominance | Bar | Hybrid genres (*Adventure\|Indie*) dominate — multi-genre titles outperform standalone |
| 2 | Releases Over Time | Line | Peak at ~1,600 releases in 2015–16; post-2022 decline is a data lag artifact |
| 3 | User Rating Distribution | Histogram + KDE | Left-skewed; modal peak at 3.75; ratings below 2.0 are rare |
| 4 | Critic vs User Ratings | Scatter | Moderate correlation (r ≈ 0.66); highest divergence in the 50–75 Metacritic band |
| 5 | Multiplayer Effect | Box Plot | Single-player median (3.5) exceeds multiplayer (3.2); multiplayer has wider IQR |
| 6 | Platform Reach vs Popularity | Regression | Positive trend confirmed; peak scores at mid-range platform counts (5–8), not max |
| 7 | ESRB Distribution | Count Plot | 10,205 unrated games (68%); Teen leads among rated categories at 1,575 |
| 8 | Engagement Score Density | KDE | Near-zero for most titles; long tail dominated by a handful of breakout games |
| 9 | Correlation Heatmap | Heatmap | `ratings_count` ↔ `reviews_count` = 0.99; playtime uncorrelated with all metrics |
| 10 | Publisher Market Share | Bar | EA and Ubisoft lead; ~1,500 unattributed entries represent a metadata gap |
| 11 | Production by Decade | Bar | 2 games in 1970s → 8,571 in 2010s; 4,285× growth in four decades |
| 12 | Playtime Outliers | Box Plot | Core IQR: 0–10 hrs; outliers extend to ~370 hrs |
| 13 | Popularity by Game Mode | Violin | Hybrid mode achieves highest median (~30); single-player shows bimodal shape |
| 14 | Achievements vs Engagement | Scatter | Inverse relationship — peak engagement at <100 achievements, not more |
| 15 | Univariate Distributions | Histograms | All three metrics right-skewed — confirms power-law market structure |

---

## 💡 Key Findings

### 🏆 Market Structure
> The gaming market operates as a **power-law ecosystem** — a small minority of titles account for the majority of engagement, popularity, and player hours. Most released games generate near-zero engagement and are statistically invisible.

### 🎯 Genre Strategy
> **Hybrid genres dominate**. Multi-genre combinations consistently outperform standalone categories in both release volume and user reception. *Adventure|Indie* and *Casual|Indie* lead the market.

### 🆚 Critic–User Divergence
> Critics and users share a moderate agreement (r = 0.66) but diverge significantly in the **50–75 Metacritic range** — the zone of highest subjectivity where player experience departs most sharply from professional critique.

### ⏱️ Playtime Is Genre-Driven
> Average playtime shows near-zero correlation (0.12–0.19) with every engagement and popularity metric. Time spent is dictated by **content depth and genre mechanics**, not by how popular or well-rated a game is.

### 🏅 Achievement Inflation Backfires
> Peak engagement (scores of 35–42) occurs in games with **fewer than 100 achievements**. Engagement plateaus and flattens beyond 1,000 achievements — studios deploying achievement inflation as a retention strategy are misallocating resources.

### 🌍 Platform Breadth Has Diminishing Returns
> While platform count positively correlates with popularity, the **highest-scoring titles appear at mid-range platform counts (5–8)**, not the maximum. Content quality and timing remain decisive over sheer distribution breadth.

### 📅 The 2010s Were Peak Gaming
> **8,571 games** were released in the 2010s alone — more than all prior decades combined. The 2020s are on pace to rival this total, with 4,453 already recorded through roughly half the decade.

---

## 📦 Libraries Used

| Library | Version | Purpose |
|---|---|---|
| `pandas` | 2.x | Data loading, cleaning, aggregation, querying |
| `numpy` | 1.x | Numerical operations and array handling |
| `matplotlib` | 3.x | Base plotting, figure configuration |
| `seaborn` | 0.13 | Statistical visualizations |
| `plotly` | 5.x | Interactive chart scaffolding |
| `scipy` | 1.x | Skewness and kurtosis computation |
| `streamlit` | latest | Dashboard scaffolding (imported) |

---

## 📄 License

This project is released under the **MIT License**. You are free to use, share, and adapt it for personal or academic purposes with attribution.

> **Reminder:** This dataset and notebook are intended for **EDA only** and should not be used as a production data source or in commercial applications without independent verification of data accuracy.

---

<div align="center">

**15,000 games. 43 features. One thorough analysis.** 🕹️

*Built for analysts, built for curiosity.*

</div>

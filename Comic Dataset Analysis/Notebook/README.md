![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/6c9eb875968176c1daeaeddc7ec0704ec0d4c9f8/Comic%20Dataset%20Analysis/dataset-cover%20(1).png)


# 📚 Comic Books Dataset — Exploratory Data Analysis

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-2.0-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/Plotly-5.x-3F4F75?style=for-the-badge&logo=plotly&logoColor=white"/>
  <img src="https://img.shields.io/badge/Seaborn-0.13-4C72B0?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Matplotlib-3.8-11557C?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/SciPy-1.11-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Completed-2ecc71?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Charts-10-e74c3c?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/License-MIT-f39c12?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Domain-Comics%20%26%20Manga-9b59b6?style=for-the-badge"/>
</p>

---

## Overview

A comprehensive Exploratory Data Analysis of the **Comic Books Dataset** — a multi-dimensional collection covering global comic titles across genres, countries, formats, age ratings, production status, and audience scores. The analysis addresses 10 core research questions through statistical summaries, correlation analysis, outlier detection, and time-series exploration — producing 10 targeted visualizations using Plotly, Seaborn, and Matplotlib.

---

## Dataset Summary

| Property | Details |
|----------|---------|
| **File** | `Comic Books Dataset.csv` |
| **Domain** | Global Comics, Manga, Manhwa, Webtoons |
| **Total Records** | 10,000+ titles (post-cleaning) |
| **Key Dimensions** | Genre, Country, Format, Age Rating, Status, Color Style |
| **Numeric Features** | Rating, Page Count, Volume Count, Release Year |
| **Format** | CSV / UTF-8 |

---

## Tech Stack

| Library | Version | Role |
|---------|---------|------|
| `pandas` | 2.0+ | Data loading, cleaning, groupby, aggregation |
| `numpy` | 1.24+ | Numerical operations and array manipulation |
| `matplotlib` | 3.8+ | Base plotting engine and violin plots |
| `seaborn` | 0.13+ | Statistical visualizations — violin, heatmap |
| `plotly.express` | 5.x | Interactive charts — bar, line, pie, funnel, scatter |
| `squarify` | 0.4+ | Treemap visualization for genre-country distribution |
| `scipy.stats` | 1.11+ | Z-score outlier detection, skewness, kurtosis |

---

## Installation

```bash
# Clone the repository
git clone https://github.com/your-username/comic-books-eda.git
cd comic-books-eda

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

**`requirements.txt`**
```
pandas
numpy
matplotlib
seaborn
plotly
squarify
scipy
jupyter
```

---

## Usage

```bash
# Launch the notebook
jupyter notebook comic_eda.ipynb

# Or run the script
python comic_eda.py
```

Ensure `Comic Books Dataset.csv` is placed in the project root before running.

---

## Project Structure

```
comic-books-eda/
├── Comic Books Dataset.csv        # Source dataset
├── comic_eda.ipynb                # Main analysis notebook
├── comic_eda.py                   # Script version
├── charts/                        # Exported chart outputs (PNG/HTML)
│   ├── 01_genre_ratings.html
│   ├── 02_production_trend.html
│   ├── 03_age_ratings.html
│   ├── 04_country_ratings.html
│   ├── 05_format_popularity.html
│   ├── 06_color_style_violin.png
│   ├── 07_genre_country_treemap.png
│   ├── 08_correlation_heatmap.html
│   ├── 09_page_count_scatter.html
│   └── 10_production_funnel.html
├── requirements.txt
└── README.md
```

---

## Visualizations & Research Questions

| # | Chart Type | Research Question | Key Finding |
|---|-----------|-------------------|-------------|
| 1 | Bar (Plotly) | Which genres generate the highest audience engagement? | Adventure/Action leads at ~9.8/10; action-hybrid genres dominate the top 4 |
| 2 | Line (Plotly) | How has comic production evolved over the years? | 3× growth from 2009–2023; sharp decline begins 2024 |
| 3 | Funnel (Plotly) | Which age groups receive the highest ratings? | All categories within 0.038 points — age rating has no impact on score |
| 4 | Bar (Plotly) | Which countries produce the highest-rated comics? | France/Iran and France/Spain lead; co-productions outperform solo nations |
| 5 | Donut Pie (Plotly) | Which comic formats are most popular? | Market fragmented across 16+ formats; Japanese formats hold 27% combined |
| 6 | Violin (Seaborn) | What creates the strongest audience consistency? | B&W has widest upper distribution; all medians cluster at ~8.0 |
| 7 | Treemap (Squarify) | Which genre-country combos dominate globally? | Superhero/Thriller leads at 94; superhero occupies 8 of top 30 slots |
| 8 | Heatmap (Plotly) | Which business metrics are correlated? | Max correlation is 0.42 (Page Count–Volume Count); rating is independent |
| 9 | Bubble Scatter (Plotly) | What is the relationship between page count and ratings? | No correlation — quality achieved at all lengths; rating floor rises for long comics |
| 10 | Funnel (Plotly) | What does the production pipeline look like? | 5,005 completed vs 434 cancelled — healthy 11.5:1 completion ratio |

---

## Key Findings

### 🎭 Genre & Audience
- **Adventure/Action dominates** with a ~9.8/10 average — action-hybrid genres sweep the top 4 positions
- A two-tier structure exists: elite top-4 cluster (9.3+) and a mid-tier plateau of 20+ genres between 8.0–8.3
- **Superhero/Thriller** is the most globally distributed genre-country combination at 94 occurrences

### 🌍 Country & Format
- **Franco-international co-productions** (France/Iran, France/Spain) lead country ratings at ~9.0–9.1
- **Japanese formats** (Tankobon, Digital Manga, Manga Volume) collectively hold 27%+ of the format market
- The webtoon ecosystem commands ~12.6% combined share — a mobile-first format with serious global scale

### 📈 Production & Status
- Comic production **tripled from 2009 to 2023**, peaking at ~595 titles before a sharp 2024 decline
- **5,005 completed** vs **434 cancelled** — an 11.5:1 ratio reflecting a healthy publishing ecosystem
- **741 titles on hiatus** represent a meaningful reader retention risk requiring active platform management

### 📊 Statistical Insights
- All business metrics are weakly correlated — **maximum r = 0.42** (Page Count vs Volume Count)
- **Rating is statistically independent** of page count, release year, and volume count (r ≤ 0.16)
- Age rating has virtually **zero influence on audience scores** — all categories within 0.038 points of each other

---

## Advanced Analysis

```python
# Outlier Detection — Z-Score Method
from scipy.stats import zscore
df['zscore_rating'] = zscore(df['Rating (out of 10)'])
outliers = df[df['zscore_rating'].abs() > 3]

# Outlier Detection — IQR Method
Q1 = df['Rating (out of 10)'].quantile(0.25)
Q3 = df['Rating (out of 10)'].quantile(0.75)
IQR = Q3 - Q1
outliers = df[(df['Rating (out of 10)'] < Q1 - 1.5 * IQR) |
              (df['Rating (out of 10)'] > Q3 + 1.5 * IQR)]

# Distribution Shape
from scipy.stats import skew, kurtosis
print("Skewness:", skew(df['Rating (out of 10)']))
print("Kurtosis:", kurtosis(df['Rating (out of 10)']))

# Derived Metric
df.eval("Rating_per_Page = `Rating (out of 10)` / `Page Count`")

# Genre Performance Aggregation
df.groupby('Genre')['Rating (out of 10)'].agg(['mean', 'count'])\
  .sort_values(by='mean', ascending=False)

# Studio Performance
df.groupby('Studio/Publisher')['Rating (out of 10)'].agg(['mean', 'count']).head(10)
```

---

## Data Preprocessing Steps

```python
# Load
df = pd.read_csv("Comic Books Dataset.csv")

# Inspect
df.info()           # Data types + null counts
df.describe()       # Statistical summary
df.isnull().sum()   # Missing value check
df.sample(5)        # Sanity check
df.memory_usage()   # RAM profile

# Clean
df.dropna(inplace=True)

# Feature Engineering
df['Release Year'] = pd.to_datetime(df['Release Year'], format='%Y')
df['Year'] = df['Release Year'].dt.year
```

---

## License

```
MIT License — free to use, modify, and distribute with attribution.
Dataset used for educational and analytical purposes only.
```

---

<p align="center">Made with ❤️ for data-driven insights into the global comic book industry</p>

![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/6c9eb875968176c1daeaeddc7ec0704ec0d4c9f8/Comic%20Dataset%20Analysis/dataset-cover%20(1).png)

# 📚 Comic Books Global EDA — 10,000 Comics · 2000–2026

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-2.0+-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/Plotly-5.x-3F4F75?style=for-the-badge&logo=plotly&logoColor=white"/>
  <img src="https://img.shields.io/badge/Seaborn-0.13+-4C72B0?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Matplotlib-3.8+-11557C?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/SciPy-1.11+-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Completed-2ecc71?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Visualizations-10-e74c3c?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Entries-10%2C000-3498db?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Columns-17-9b59b6?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/License-CC0%20%2F%20MIT-f39c12?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Size-2.13%20MB-1abc9c?style=for-the-badge"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/🇯🇵%20Manga-3%2C575-FF6B6B?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/🇺🇸%20USA-3%2C150-4ECDC4?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/🇰🇷%20Manhwa-897-45B7D1?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/🇨🇳%20Manhua-550-96CEB4?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/🇪🇺%20Europe-560-FFEAA7?style=for-the-badge"/>
</p>

---

## 🌐 Project Overview

A **full-stack Exploratory Data Analysis** of the Global Comic Books Dataset — the most comprehensive comic dataset on Kaggle — covering **Manga, Manhwa, Manhua, Marvel, DC, Image, Dark Horse, and European comics** in one unified project.

This project spans the complete data science lifecycle: raw data ingestion → cleaning → statistical exploration → 10 targeted visualizations → insight synthesis. It addresses core questions about genre performance, production trends, country ratings, format popularity, audience consistency, business metric correlations, and production pipeline health — across **10,000 titles, 26 years, 6 global regions, and 17 features**.

> **Dataset:** Comic Books Dataset (CC0: Public Domain) — combines 40+ real verified entries with synthetically generated data following realistic distributions. Suitable for EDA, ML, and data visualization practice.

---

## 📋 Dataset at a Glance

| Property | Value |
|----------|-------|
| **File** | `Comic Books Dataset.csv` |
| **Total Entries** | 10,000 comics |
| **Time Period** | 2000 – 2026 |
| **Total Columns** | 17 |
| **File Size** | ~2.13 MB |
| **File Format** | CSV (UTF-8) |
| **License** | CC0: Public Domain |
| **Average Rating** | 8.06 / 10 |
| **Most Common Genre** | Action / Fantasy |
| **Most Common Format** | Tankobon (Manga volume) |

---

## 🗂️ Column Reference

| Column | Type | Description | Example |
|--------|------|-------------|---------|
| `comic_id` | String | Unique ID (`CMC-00001` format) | CMC-00042 |
| `Title` | String | Official name of the comic / series | Attack on Titan |
| `Writer` | String | Lead writer / author | Hajime Isayama |
| `Artist` | String | Illustrator / inker | Hajime Isayama |
| `Studio/Publisher` | String | Publishing company | Kodansha (Kodansha USA) |
| `Release Year` | Integer | Year of first publication | 2009 |
| `Format` | String | Release format | Tankobon / Webtoon / Graphic Novel |
| `Theme (Color Style)` | String | Visual art style | Black & White / Full Color Digital |
| `Genre` | String | Primary genre classification | Action / Dark Fantasy |
| `Country of Origin` | String | Country of first publication | Japan |
| `Page Count` | Integer | Total approximate page count | 5,988 |
| `Rating (out of 10)` | Float | Aggregated reader score (MAL / Goodreads) | 9.7 |
| `Status` | String | Current publication status | Completed / Ongoing / Hiatus / Cancelled |
| `Language` | String | Original publication language | Japanese |
| `Age Rating` | String | Target audience classification | Teen+ / Mature / All Ages |
| `Awards` | String | Notable awards won or nominated for | Kodansha Manga Award Winner |
| `Volume Count` | Integer | Total number of volumes / issues | 34 |

---

## 🌍 Regional Coverage

| Region | Titles | Publishers |
|--------|--------|------------|
| 🇯🇵 Japan (Manga) | ~3,575 | Shueisha, Kodansha, Square Enix, Kadokawa, Shogakukan, Hakusensha |
| 🇺🇸 USA | ~3,150 | Marvel, DC, DC Vertigo, DC Black Label, Image, Dark Horse, BOOM! Studios, IDW, Oni Press |
| 🇰🇷 South Korea (Manhwa/Webtoon) | ~897 | Naver / Line Webtoon, Kakao, Lezhin, Tapas Media |
| 🇨🇳 China (Manhua) | ~550 | Tencent Comics, Bilibili Comics, Kuaikan Comics |
| 🇫🇷🇪🇸🇩🇪 Europe | ~560 | Dargaud, Casterman, Dupuis, L'Association, Titan Comics (UK), 2000 AD |
| 🌐 Others (UK, CA, AU, NZ) | ~268 | Various indie and international publishers |

---

## 🏆 Notable Comics Included

| Title | Origin | Rating |
|-------|--------|--------|
| One Piece | 🇯🇵 Japan | ⭐ 9.9 |
| Berserk | 🇯🇵 Japan | ⭐ 9.8 |
| Attack on Titan | 🇯🇵 Japan | ⭐ 9.7 |
| Saga | 🇺🇸 USA | ⭐ 9.7 |
| Vagabond | 🇯🇵 Japan | ⭐ 9.7 |
| All-Star Superman | 🇺🇸 USA | ⭐ 9.6 |
| Fullmetal Alchemist | 🇯🇵 Japan | ⭐ 9.6 |
| Mister Miracle | 🇺🇸 USA | ⭐ 9.5 |
| Chainsaw Man | 🇯🇵 Japan | ⭐ 9.5 |
| Solo Leveling | 🇰🇷 South Korea | ⭐ 9.4 |
| Blacksad | 🇫🇷 France / Spain | ⭐ 9.3 |

---

## 🛠️ Tech Stack

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

## ⚙️ Installation

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
pandas>=2.0
numpy>=1.24
matplotlib>=3.8
seaborn>=0.13
plotly>=5.0
squarify
scipy>=1.11
jupyter
```

---

## ▶️ Usage

```bash
# Launch the interactive notebook
jupyter notebook comic_eda.ipynb

# Or run the full analysis as a script
python comic_eda.py
```

> Ensure `Comic Books Dataset.csv` is placed in the project root before running.

---

## 📁 Project Structure

```
comic-books-eda/
├── Comic Books Dataset.csv           # Source dataset (10,000 entries, 17 columns)
├── comic_eda.ipynb                   # Main analysis notebook
├── comic_eda.py                      # Script version of the full EDA
├── charts/                           # Exported chart outputs
│   ├── 01_genre_ratings.html         # Top performing genres by audience rating
│   ├── 02_production_trend.html      # Comic production trend over time
│   ├── 03_age_ratings.html           # Ratings across age categories
│   ├── 04_country_ratings.html       # Country-wise average ratings
│   ├── 05_format_popularity.html     # Comic format popularity (donut)
│   ├── 06_color_style_violin.png     # Rating distribution by color style
│   ├── 07_genre_country_treemap.png  # Top 30 genre distribution across countries
│   ├── 08_correlation_heatmap.html   # Correlation between business metrics
│   ├── 09_page_count_scatter.html    # Page count vs ratings (bubble)
│   └── 10_production_funnel.html     # Production status funnel
├── requirements.txt
└── README.md
```

---

## 📊 Visualizations & Research Questions

| # | Chart Type | Research Question | Key Finding |
|---|-----------|-------------------|-------------|
| 1 | Bar (Plotly) | Which genres generate the highest audience engagement? | Adventure/Action leads at ~9.8/10; action-hybrids dominate top 4 |
| 2 | Line (Plotly) | How has comic production evolved over the years? | 3× growth 2009–2023; sharp post-2024 decline to 2015 levels |
| 3 | Funnel (Plotly) | Which age groups receive the highest ratings? | All age categories within 0.038 points — age rating is irrelevant to score |
| 4 | Bar (Plotly) | Which countries produce the highest-rated comics? | France/Iran & France/Spain lead; co-productions outperform solo nations |
| 5 | Donut Pie (Plotly) | Which comic formats are most popular? | 16+ formats; Japanese formats hold 27% combined — no dominant single format |
| 6 | Violin (Seaborn) | What creates the strongest audience consistency? | All medians ~8.0; B&W has widest upper distribution; digital has lowest floor |
| 7 | Treemap (Squarify) | Which genre-country combos dominate globally? | Superhero/Thriller leads at 94; superhero holds 8 of top 30 global slots |
| 8 | Heatmap (Plotly) | Which business metrics are correlated? | Max r = 0.42 (Page Count–Volume Count); rating is statistically independent |
| 9 | Bubble Scatter (Plotly) | What is the relationship between page count and ratings? | No correlation — quality at all lengths; rating floor rises beyond 8k pages |
| 10 | Funnel (Plotly) | What does the production pipeline look like? | 5,005 completed vs 434 cancelled — healthy 11.5:1 completion ratio |

---

## 🔑 Key Findings

### 🎭 Genre & Audience
- **Adventure/Action dominates** with a ~9.8/10 average — action-hybrid genres sweep the top 4 positions
- A clear two-tier structure: elite top-4 cluster (9.3+) and a dense mid-tier plateau of 20+ genres between 8.0–8.3
- **Superhero/Thriller** is the most globally distributed genre-country combination at 94 occurrences across countries

### 🌍 Country & Format
- **Franco-international co-productions** (France/Iran, France/Spain) lead all country ratings at ~9.0–9.1
- **Japanese formats** (Tankobon, Digital Manga, Manga Volume) collectively command 27%+ of the global format market
- The webtoon ecosystem (Webtoon + Webtoon Chapter Collection + Digital Webtoon) holds a combined ~12.6% market share

### 📈 Production & Status
- Comic output **tripled from 2009 to 2023**, peaking at ~595 annual titles before a sharp post-2024 correction
- **5,005 completed** vs **434 cancelled** — an 11.5:1 ratio reflects a healthy, completion-oriented publishing ecosystem
- **741 hiatus titles** represent an active reader retention risk that platforms need to address

### 📐 Statistical Insights
- **Rating is statistically independent** of page count, release year, and volume count (max r = 0.16)
- Age rating has **zero meaningful influence** on audience scores — all five categories within 0.038 points of each other
- Page Count and Volume Count are the strongest correlated pair at **r = 0.42** — long comics span more volumes naturally

---

## 🔬 Advanced Analysis

```python
# Outlier Detection — Z-Score Method
from scipy.stats import zscore
df['zscore_rating'] = zscore(df['Rating (out of 10)'])
outliers_z = df[df['zscore_rating'].abs() > 3]

# Outlier Detection — IQR Method
Q1 = df['Rating (out of 10)'].quantile(0.25)
Q3 = df['Rating (out of 10)'].quantile(0.75)
IQR = Q3 - Q1
outliers_iqr = df[
    (df['Rating (out of 10)'] < Q1 - 1.5 * IQR) |
    (df['Rating (out of 10)'] > Q3 + 1.5 * IQR)
]

# Distribution Shape Analysis
from scipy.stats import skew, kurtosis
print("Skewness:", skew(df['Rating (out of 10)']))
print("Kurtosis:", kurtosis(df['Rating (out of 10)']))

# Correlation Matrix
df.corr(numeric_only=True)

# Genre Performance Aggregation
df.groupby('Genre')['Rating (out of 10)'].agg(['mean', 'count'])\
  .sort_values(by='mean', ascending=False)

# Studio / Publisher Performance
df.groupby('Studio/Publisher')['Rating (out of 10)'].agg(['mean', 'count']).head(10)

# Derived Metric — Rating Efficiency
df.eval("Rating_per_Page = `Rating (out of 10)` / `Page Count`")

# Multi-key Sort
df.sort_values(['Genre', 'Rating (out of 10)'], ascending=[True, False])

# Critical Threshold Filtering
df.query("`Rating (out of 10)` > 9.0 and Status == 'Completed'")
```

---

## 🧹 Data Preprocessing Pipeline

```python
import pandas as pd

# 1. Load
df = pd.read_csv("Comic Books Dataset.csv")

# 2. Inspect
df.shape                    # Rows × columns
df.info()                   # Data types + null counts
df.describe()               # Statistical summary
df.isnull().sum()           # Missing value audit
df.sample(5)                # Random sanity check
df.memory_usage(deep=True)  # RAM profile

# 3. Clean
df.dropna(inplace=True)
df.isnull().sum()           # Confirm zero nulls

# 4. Explore Categorical Distributions
df['Genre'].value_counts()
df['Status'].value_counts()
df['Country of Origin'].value_counts()
df['Language'].nunique()

# 5. Feature Engineering
df['Release Year'] = pd.to_datetime(df['Release Year'], format='%Y')
df['Year'] = df['Release Year'].dt.year
```

---

## 🎨 Understanding Theme (Color Style)

One of the most unique columns in this dataset — it captures the **visual identity** of each comic, something no other dataset on Kaggle tracks.

| Theme | Meaning | Notable Examples |
|-------|---------|-----------------|
| `Black & White` | Traditional manga ink style | Attack on Titan, Berserk, Death Note |
| `Full Color` | Standard Western comic coloring | Marvel, DC, Image Comics |
| `Full Color (Digital)` | Vertical scroll webtoon coloring | Solo Leveling, Tower of God, Lore Olympus |
| `Full Color (Pastel)` | Soft pastel digital palette | Lore Olympus |
| `Full Color / Limited Palette` | Stylized restricted colors | Hawkeye (Matt Fraction run) |
| `Grayscale` | Between B&W and full color | Select indie and European comics |
| `Watercolor` | Hand-painted watercolor style | Descender / Ascender |

---

## 📈 Dataset Production Statistics

| Metric | Value |
|--------|-------|
| **Average Rating** | 8.06 / 10 |
| **Highest Rated** | One Piece (9.9), Berserk (9.8), Saga (9.7) |
| **Completed Series** | ~50% (5,005 titles) |
| **Ongoing Series** | ~38% (3,820 titles) |
| **On Hiatus** | ~7% (741 titles) |
| **Cancelled** | ~4% (434 titles) |
| **Peak Release Period** | 2018 – 2022 |
| **Production Peak Year** | 2023 (~595 titles) |
| **Completion Ratio** | 11.5 : 1 (completed vs cancelled) |

---

## ⚠️ Notes & Limitations

- Combines **real verified entries** (40+ famous titles) with **synthetically generated data** following realistic distributions — suitable for EDA, ML practice, and visualization projects
- Ratings are approximate aggregates inspired by MAL, Goodreads, and community scores — not official publisher data
- Page counts are approximate totals across all volumes
- Some titles may carry variant spellings due to translation differences across regions
- Manhua and lesser-known indie titles may have limited real-world verification

---

## 📜 License

| Scope | License |
|-------|---------|
| **Dataset** | CC0: Public Domain — free for any use without restriction |
| **Analysis Code** | MIT License — free to use, modify, and distribute with attribution |

---

## 💬 Inspiration

Built to fill a massive gap on Kaggle — there was almost no structured comic book data available, especially covering non-US traditions like **Manga, Manhwa, and Manhua**. This project brings the global comic world into one clean, analysis-ready CSV and pairs it with a complete EDA pipeline for researchers, students, and data enthusiasts alike.

---

<p align="center">
  <img src="https://img.shields.io/badge/Made%20with-❤️%20for%20Comics%20%26%20Data-e74c3c?style=for-the-badge"/>
</p>

<p align="center">If this project helped you, consider leaving a ⭐ on GitHub or an upvote on Kaggle</p>

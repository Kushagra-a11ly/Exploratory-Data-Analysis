# 📊 Comic Books Dataset — Exploratory Data Analysis

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-Interactive%20Charts-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Viz-4C72B0?style=for-the-badge&logo=python&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Figure%20Rendering-11557C?style=for-the-badge&logo=python&logoColor=white)
![Dataset](https://img.shields.io/badge/Dataset-10%2C000%2B%20Comics-orange?style=for-the-badge&logo=databricks&logoColor=white)
![Report](https://img.shields.io/badge/Report-DOCX-2B579A?style=for-the-badge&logo=microsoftword&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

---

## 🗂️ Table of Contents

- [Overview](#overview)
- [Dataset Summary](#dataset-summary)
- [Analysis Sections](#analysis-sections)
- [Key Findings](#key-findings)
- [Tools & Libraries](#tools--libraries)
- [Methodology](#methodology)
- [Report Output](#report-output)

---

## Overview

This project delivers a full **Exploratory Data Analysis (EDA)** of the Global Comic Books Dataset — a collection of 10,000+ comic titles spanning multiple countries, genres, formats, age categories, and production stages. The goal is to surface data-driven insights for publishers, platform operators, and content strategists looking to understand what drives audience satisfaction, market share, and production health in the global comics industry.

---

## Dataset Summary

| Metric | Value |
|--------|-------|
| 📚 Total Comics | 10,000+ |
| ✅ Completed Titles | 5,005 (49% of catalogue) |
| ⭐ Average Audience Rating | 8.06 / 10 |
| 📅 Peak Production Year | 2023 (~595 releases) |
| 🌍 Countries Covered | 20+ (solo + collaborative) |
| 🎨 Color Styles Analysed | 8 |
| 📐 Formats Tracked | 16+ |
| 🏷️ Age Categories | 5 |

---

## Analysis Sections

### 1.Top Performing Genres by Audience Rating
![image_alt]()
Ranks all comic genres by mean audience rating (out of 10) to identify which genre combinations generate the strongest viewer engagement.


| Rank | Genre | Rating |
|------|-------|--------|
| 1 | Adventure / Action | ~9.8 |
| 2 | Historical / Action | ~9.3 |
| 3 | Action / Mystery | ~9.3 |
| 4 | Action / Sci-Fi | ~9.3 |
| 5+ | Action / Supernatural and below | ~8.3 and under |

> Action-hybrid genres sweep the top 4 positions. From rank 5 onward, 20+ genres cluster within a 0.3-point band (8.0–8.3), making them nearly interchangeable in audience perception.

---

### 2.Comic Production Trend Over Time
![image_alt]()
A time-series view of annual comic production volumes from 2000 to 2026, capturing the industry's growth arc, peak, and recent correction.

| Period | Output | Trend |
|--------|--------|-------|
| 2000–2008 | ~210–245 / year | Flat consolidation |
| 2009–2023 | ~245 → ~595 | Nearly 3× growth |
| 2023 | ~595 | All-time peak |
| 2024–2026 | ~595 → ~450 | Sharp correction |

> 2026 production (~450) has fallen back to 2015 levels — a drop of ~145 titles in just three years. Whether this is cyclical or structural is the key industry question.

---

### 3.Ratings Across Age Categories
![image_alt]()
Compares average audience ratings across the five official age classification categories to assess whether content maturity level influences perceived quality.

| Age Category | Avg Rating |
|-------------|------------|
| Young Adult | 8.078 |
| All Ages | 8.075 |
| Teen+ | 8.062 |
| Mature 17+ | 8.051 |
| Mature | 8.040 |

> The entire range spans just **0.038 points**. Age classification has virtually no impact on audience scores — story quality and execution are the real drivers.

---

### 4.Country-wise Average Ratings
![image_alt]()
Compares average audience ratings by country (or collaborative country pair) of origin to identify which national comic traditions resonate most with global audiences.

**Top performers:**
- 🥇 France / Iran — ~9.1
- 🥈 France / Spain — ~9.0
- 🥉 Japan, South Korea/Japan, South Korea, South Korea/USA — 8.1–8.2

> **Collaborative origin tags consistently outperform solo-nation entries.** Franco-international and East Asian co-productions lead the global market. Even the lowest-ranked countries (Belgium, Switzerland, Spain) still average 7.7–7.8.

---

### 5.Comic Format Popularity
![image_alt]()
A donut chart breaking down the relative market share of all comic delivery formats, from traditional print to digital-first and platform-native formats.


| Format Bloc | Combined Share |
|-------------|---------------|
| Japanese formats (Tankobon, Digital Manga, Manga Volume) | ~27% |
| Physical print (Graphic Novel, Trade Paperback, Single Issue, Hardcover) | ~26% |
| Digital formats (Digital Manga, Digital Single Issue, Digital Webtoon, Digital Manhua) | ~20%+ |
| Webtoon ecosystem (Webtoon, Webtoon Chapter Collection, Digital Webtoon) | ~12.6% |

> No single format commands a majority — the market is highly fragmented across 16+ formats, with the largest individual share at just 9.06%.

---

### 6.Rating Distribution by Theme / Color Style
![image_alt]()
Violin plots showing the full distribution of audience ratings segmented by visual color style, assessing whether artistic approach influences satisfaction scores.

| Color Style | Notable Characteristic |
|-------------|----------------------|
| Black & White | Highest concentration of top-tier (9–10) titles |
| Full Color / Limited Palette | Narrowest variance — most predictable quality |
| Full Color (Digital) | Widest downward spread — reaches ~6.0 |
| Watercolor / Full Color (Pastel) | Compact, symmetrical — IQR tight around 7.8–8.2 |

> All 8 styles share an identical median of ~8.0. Color style alone does not move the needle on audience satisfaction.

---

### 7.Top 30 Genre Distribution Across Countries
![image_alt]()
A treemap visualising the top 30 genre-country combinations by count, revealing which genre archetypes have achieved the broadest international distribution.

| Rank | Genre | Count |
|------|-------|-------|
| 1 | Superhero / Thriller | 94 |
| 2 | Superhero / Action | 91 |
| 3 | Superhero / Psychological | 82 |
| 4 | Superhero / Drama | 79 |
| … | Non-superhero peak (Mecha/Sci-Fi) | 68 |

> Superhero genres hold **8 of the top 30 slots**. Non-superhero genres cap out at 68, highlighting a clear ceiling versus superhero's global franchise dominance.

---

### 8.Correlation Between Business Metrics
![image_alt]()
A correlation heatmap examining pairwise relationships between Page Count, Release Year, Rating, and Volume Count.

| Pair | Correlation | Interpretation |
|------|-------------|----------------|
| Page Count ↔ Volume Count | 0.42 | Strongest link — depth and length scale together |
| Page Count ↔ Rating | 0.16 | Negligible |
| Release Year ↔ Rating | 0.03 | No recency bias whatsoever |
| Release Year ↔ Volume Count | 0.10 | Negligible |

> **Maximum correlation in the entire matrix is just 0.42.** Rating is statistically independent of all four measured dimensions — comic success is driven by qualitative factors.

---

### 9.Page Count vs. Ratings
![image_alt]()
A bubble scatter chart plotting individual comics by page count against audience rating, with bubble size representing volume count and colour indicating genre.

**Key observations:**
- Top-rated titles (9–10) appear at **all** page counts from 0 to 15k
- The vast majority cluster **below 5k pages**
- A single Action/Sci-Fi title at ~15k pages holds a **perfect 10 rating**
- Titles beyond 8k pages rarely fall below 8.0 — long-runners self-select for quality
- Genre diversity is **uniform** across all page count ranges

> Length does not predict quality. Quality is entirely format-agnostic.

---

### 10.Production Status Funnel
![image_alt]()
A funnel chart breaking down the current production status of all titles: Completed, Ongoing, Hiatus, and Cancelled.

| Status | Count | Share |
|--------|-------|-------|
| ✅ Completed | 5,005 | 49.3% |
| 🟡 Ongoing | 3,820 | 37.6% |
| ⏸️ Hiatus | 741 | 7.3% |
| ❌ Cancelled | 434 | 4.3% |

> **Completed-to-Cancelled ratio: 11.5:1** — for every cancelled title, 11+ reach proper completion. Hiatus titles (741) represent the key retention risk.

---

## Key Findings

```
✅  Action-hybrid genres dominate — Adventure/Action leads at ~9.8/10
✅  Industry peaked in 2023 (~595 titles); 2026 output back to 2015 levels
✅  Age classification has zero meaningful impact on ratings (0.038-point spread)
✅  Collaborative productions (France/Iran, South Korea/Japan) outperform solo nations
✅  Japanese formats collectively hold ~27% market share
✅  Webtoon ecosystem captures ~12.6% and growing
✅  Rating is statistically independent of page count, volume count, and recency
✅  Long-running series (8k+ pages) self-select for quality — rarely below 8.0
✅  Superhero genres hold 8 of the top 30 global genre-country slots
✅  11.5:1 completed-to-cancelled ratio reflects a healthy publishing ecosystem
```

---

## Tools & Libraries

| Tool | Purpose |
|------|---------|
| ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white) | Data loading, cleaning, aggregation |
| ![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=flat&logo=plotly&logoColor=white) | Bar charts, scatter plots, funnel charts, heatmaps |
| ![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat&logo=python&logoColor=white) | Violin plots and statistical visualisations |
| ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logo=python&logoColor=white) | Figure management and treemap rendering (Squarify) |
| ![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat&logo=scipy&logoColor=white) | Skewness, kurtosis, z-score outlier detection |
| ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white) | DOCX report generation (`docx` npm package) |

---

## Methodology

- **Data cleaning:** Null rows dropped; type inference validated across all columns
- **Outlier detection:** Z-score method (|z| > 3) and IQR method (1.5× IQR fence) applied in parallel
- **Time-series aggregation:** Annual level (release year)
- **Rating scale:** 0–10 for all titles
- **All visualisations** reflect post-cleaning data only

> **Limitation:** The dataset does not include reader demographic data. Age category ratings reflect the average rating *assigned to* comics in each classification — not ratings *provided by* readers of that age group.

---

## Report Output

The analysis is packaged as a fully formatted Word document:

```
Comic_Books_EDA_Report.docx
├── Title Page (KPI banner)
├── Executive Summary + findings table
├── Sections 1–10 (chart + insight table per section)
├── Strategic Recommendations (6 priorities)
└── Methodology & Data Notes
```

**To regenerate the report:**
```bash
npm install docx
node report.js
# → /mnt/user-data/outputs/Comic_Books_EDA_Report.docx
```

---

*Prepared by the Data Analytics Division · Comic Books Dataset EDA · 2024*

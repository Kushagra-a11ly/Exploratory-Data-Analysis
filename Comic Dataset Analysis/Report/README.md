# 📚 Comic Books EDA  Report 

> An automated Word document pipeline that transforms 10 chart visualisations and structured insights into a fully formatted, print-ready analysis report of the global comic book industry.

---

## What This Does

`report.js` generates a professional `.docx` report from scratch — complete with a styled title page, KPI banners, insight tables, embedded charts, strategic recommendations, and paginated headers/footers. No manual formatting required.

---

## Before You Run

**1. Install the dependency**
```bash
npm install docx
```

**2. Place all 10 chart images in `/home/claude/`**

These are generated separately (Python/Plotly/Seaborn) and must exist before the script runs:

```
*_1_Top_Performing_Genres_by_Audience_Rating.png
*_2_Comic_Production_Trend_Over_Time.png
*_3_Ratings_Across_Age_Categories.png
*_4_Country-wise_Average_Ratings.png
*_5_Comic_Format_Popularity.png
*_6_Rating_Distribution_by_Theme__Color_Style.png
*_7_Top_30_Genre_Distribution_Across_Countries.png
*_8_Correlation_Between_Business_Metrics.png
*_9_Page_Count_vs_Ratings.png
*_10_Production_Status_Funnel.png
```

**3. Run it**
```bash
node report.js
# Output → /mnt/user-data/outputs/Comic_Books_EDA_Report.docx
```

---

## Report Contents

| # | Section | What It Covers |
|---|---------|----------------|
| — | Title Page | KPI snapshot: 10k+ titles, 8.06 avg rating, 2023 peak |
| — | Executive Summary | Cross-dimension findings at a glance |
| 1 | Top Performing Genres | Mean ratings by genre — Action hybrids dominate |
| 2 | Production Trend | Annual output 2000–2026 — peak, growth, correction |
| 3 | Age Category Ratings | Maturity rating vs audience score (spoiler: no difference) |
| 4 | Country-wise Ratings | National and co-production performance comparison |
| 5 | Format Popularity | Market share across 16+ comic delivery formats |
| 6 | Color Style Distribution | Violin plots — does art style affect ratings? |
| 7 | Genre × Country Mix | Top 30 genre-country combos by global distribution |
| 8 | Business Metric Correlations | Heatmap: page count, rating, volume, release year |
| 9 | Page Count vs Ratings | Bubble chart — does length predict quality? |
| 10 | Production Status Funnel | Completed / Ongoing / Hiatus / Cancelled breakdown |
| — | Strategic Recommendations | 6 priorities for publishers and platform operators |
| — | Methodology | Data cleaning, tools, and limitations |

---

## Headline Numbers

```
10,000+   comics analysed
  5,005   completed titles (49% of catalogue)
   8.06   average audience rating out of 10
   2023   peak production year (~595 releases)
  11.5:1  completed-to-cancelled ratio
    ~27%  market share held by Japanese formats
  0.038   rating spread across ALL five age groups
```

---

## Tech Stack

| Layer | Tool |
|-------|------|
| Report generation | Node.js + `docx` npm package |
| Data analysis | Python, Pandas, SciPy |
| Visualisation | Plotly Express, Seaborn, Matplotlib |
| Source data | Comic Books Dataset (CSV) |

---

## Notes

- Output path is hardcoded to `/mnt/user-data/outputs/` — change line 558 of `report.js` to redirect elsewhere
- All image filenames are mapped with explicit aspect ratios inside `report.js` — update the `aspect` object if charts are regenerated at different dimensions
- Page size is US Letter (8.5 × 11 in); margins are set to 0.75 in on all sides

---

*Prepared by the Data Analytics Division*

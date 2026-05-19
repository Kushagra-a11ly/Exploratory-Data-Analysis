# Comic Books Dataset — EDA Report

## Overview

This repository contains the automated Word document generator for the **Comic Books Dataset Exploratory Data Analysis Report** — a comprehensive analysis of 10,000+ comic titles covering genres, formats, countries of origin, age categories, visual styles, and business metrics.

---

## Files

| File | Description |
|------|-------------|
| `report.js` | Main document generator script (Node.js) |
| `Comic_Books_EDA_Report.docx` | Generated Word report output |
| `*.png` | Chart images embedded in the report (10 total) |

---

## Requirements

### Runtime
- **Node.js** v14+
- **npm** package: `docx`

```bash
npm install docx
```

### Chart Images
The following 10 PNG files must be present in the same directory as `report.js` before running:

| Filename | Section |
|----------|---------|
| `..._1_Top_Performing_Genres_by_Audience_Rating.png` | Section 1 |
| `..._2_Comic_Production_Trend_Over_Time.png` | Section 2 |
| `..._3_Ratings_Across_Age_Categories.png` | Section 3 |
| `..._4_Country-wise_Average_Ratings.png` | Section 4 |
| `..._5_Comic_Format_Popularity.png` | Section 5 |
| `..._6_Rating_Distribution_by_Theme__Color_Style.png` | Section 6 |
| `..._7_Top_30_Genre_Distribution_Across_Countries.png` | Section 7 |
| `..._8_Correlation_Between_Business_Metrics.png` | Section 8 |
| `..._9_Page_Count_vs_Ratings.png` | Section 9 |
| `..._10_Production_Status_Funnel.png` | Section 10 |

---

## Usage

```bash
node report.js
```

The output file `Comic_Books_EDA_Report.docx` will be written to `/mnt/user-data/outputs/`.

---

## Report Structure

1. **Title Page** — KPI summary (10,000+ titles, 5,005 completed, 8.06 avg rating, 2023 peak)
2. **Executive Summary** — Key findings across all 10 dimensions
3. **Section 1** — Top Performing Genres by Audience Rating
4. **Section 2** — Comic Production Trend Over Time
5. **Section 3** — Ratings Across Age Categories
6. **Section 4** — Country-wise Average Ratings
7. **Section 5** — Comic Format Popularity
8. **Section 6** — Rating Distribution by Theme / Color Style
9. **Section 7** — Top 30 Genre Distribution Across Countries
10. **Section 8** — Correlation Between Business Metrics
11. **Section 9** — Page Count vs. Ratings
12. **Section 10** — Production Status Funnel
13. **Strategic Recommendations** — 6 actionable priorities
14. **Methodology & Data Notes**

---

## Key Findings

- **Adventure/Action** leads all genres at ~9.8/10; Action-hybrid genres sweep the top 4
- The global comic industry **peaked in 2023** (~595 titles) before a sharp correction to ~450 in 2026
- Audience ratings are **uniform across all age groups** (8.04–8.08 range)
- **France/Iran and France/Spain** top country ratings; East Asian markets dominate the mid-tier
- **Japanese formats** (Tankobon, Digital Manga, Manga Volume) collectively lead at ~27% market share
- **Rating is independent** of page count, volume count, and release year
- Completed-to-Cancelled ratio of **11.5:1** reflects a healthy publishing ecosystem

---

## Data Source

**Dataset:** Comic Books Dataset (`Comic Books Dataset.csv`)  
**Tools:** Python · Pandas · Plotly · Seaborn · Matplotlib · SciPy  
**Prepared by:** Data Analytics Division

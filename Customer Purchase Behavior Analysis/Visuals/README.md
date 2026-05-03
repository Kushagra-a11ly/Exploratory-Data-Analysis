

Customer Purchase Behaviour — Exploratory Data Analysis

A comprehensive EDA of 3,900 customer transactions across 4 product categories, 6 payment methods, and 50 U.S. states.

📋 Table of Contents

- [Project Overview](#project-overview)
- [Dataset Summary](#dataset-summary)
- [Key Metrics at a Glance](#key-metrics-at-a-glance)
- [Visual Analyses](#visual-analyses)
- [Key Findings](#key-findings)
- [Promotional Effectiveness](#promotional-effectiveness)
- [Recommendations](#recommendations)
- [Analytical Next Steps](#analytical-next-steps)
- [Important Caveats](#important-caveats)
- [Dependencies](#dependencies)

📌 Project Overview

This project performs a full exploratory data analysis on the Customer Purchase Behaviour dataset.

The analysis spans demographic profiling, revenue breakdown by category and season, promotional effectiveness, loyalty patterns, geographic distribution, and payment method usage.

The goal is to surface actionable commercial insights and identify the true drivers of customer spending — or, as this analysis reveals, confirm that no single variable in this dataset meaningfully predicts how much a customer spends per transaction.

📊 Dataset Summary

| Dimension | Detail |
|-----------|--------|
| Total Records | 3,900 customer transactions |
| Attributes | 18 columns — demographic, behavioural, and transactional |
| Spend Range | $20–$100 (hard bounds; mean ~$60) |
| Categories | Clothing, Accessories, Footwear, Outerwear |
| Seasons | Spring, Summer, Fall, Winter |
| Payment Methods | Credit Card, Debit Card, Cash, PayPal, Venmo, Bank Transfer |
| Geography | 50 U.S. States |
| Missing Values | None — fully complete dataset |
| Data Quality | Synthetically generated — uniform distributions across all variables |

📈 Key Metrics at a Glance

| Metric | Value |
|--------|-------|
| Average Spend | ~$60 |
| Total Customers | 3,900 |
| Average Review Rating | ~3.7 / 5 |
| Average Past Orders | ~25 |
| Top Revenue Category | Clothing (~$104,000) |
| Strongest Season | Spring |
| Most Used Payment Method | Credit Card (17.8%) |
| Dominant Size | Medium (M) across all categories |

🔬 Visual Analyses

The report covers **10 visual analyses** across 5 analytical themes:
 
1️⃣ Revenue by Category
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Total%20Revenue%20by%20Category.jpg)
- Clothing dominates at over $100,000 — more than the other three categories combined
- Accessories is a reliable secondary engine at ~$74,000
- Outerwear is the chronic underperformer at ~$19,000, even in winter

2️⃣ Spending Behaviour by Gender
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Spending%20Behaviour%20by%20Gender.jpg)
- Male and female customers show **identical median spend (~$60)**
- IQR is the same for both genders ($40–$80)
- Gender has **no predictive power** over purchase amount

### 3️⃣ Age vs. Spending Trend
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Age%20vs.%20Spending%20Trend.jpg)
- Regression line is **virtually flat at ~$60** across all ages (r ≈ -0.01)
- Every age cohort (18–70) spends within the same $20–$100 band
- Highest customer density in the **25–45 age band**

### 4️⃣ Effect of Discount on Purchase Amount
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Effect%20of%20Discount%20on%20Purchase%20Amount.jpg)
- Discounted customers spend **~$59 vs. ~$60** without discount — negligible $1 difference
- Discounts are **not lifting basket size**; tight error bars confirm this is statistically stable
- Potential pure margin erosion with no incremental revenue gain

### 5️⃣ Seasonal Revenue Heatmap
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Effect%20of%20Discount%20on%20Purchase%20Amount.jpg)

| Category | Fall | Spring | Summer | Winter |
|----------|------|--------|--------|--------|
| Clothing | $26,220 | $27,692 | $23,078 | $27,274 |
| Accessories | $19,874 | $17,007 | $19,028 | $18,291 |
| Footwear | $8,665 | $9,555 | $9,393 | $8,480 |
| Outerwear | $5,259 | $4,425 | $4,278 | $4,562 |

- **Spring** is the strongest overall trading season
- **Outerwear** fails to peak even in winter — fundamental visibility or product problem

### 6️⃣ Size Distribution Across Categories
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Size%20Distribution%20Across%20Categories.jpg)
- **Medium (M)** is the top size in every category without exception
- **Outerwear** has critically low stock across all sizes (XL barely ~30 units)
- **Clothing**: Large over-stocked vs. Small — potential lost sales risk
- **Accessories**: Healthiest size balance across all categories

### 7️⃣ Revenue by Top Locations
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Size%20Distribution%20Across%20Categories.jpg)
- Revenue spans only **~$600** across the top 10 states (<11% spread)
- **Montana leads** despite being one of the least populous states — a sampling artefact
- **New York** appears mid-table — anomalous for the largest U.S. consumer market

### 8️⃣ Payment Method Distribution
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Payment%20Method%20Distribution.jpg)
- **Credit Card** leads marginally at ~697 transactions (~17.8%)
- All other 5 methods cluster within a **20-count band** of each other
- Implausibly uniform — another synthetic data fingerprint

### 9️⃣ Correlation Matrix
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Correlation%20Matrix.jpg)

| Variable Pair | r | Interpretation |
|---------------|---|----------------|
| Purchase Amount ↔ Review Rating | 0.031 | Near zero — satisfaction doesn't predict spend |
| Purchase Amount ↔ Age | -0.010 | Effectively zero — age irrelevant to spend |
| Purchase Amount ↔ Previous Purchases | 0.008 | Near zero — loyalty doesn't drive basket size |
| Age ↔ Previous Purchases | 0.040 | Near zero — loyalty not age-stratified |
| Review Rating ↔ Age | -0.022 | Near zero — satisfaction independent of age |

> ⚠️ All off-diagonal correlations fall within **-0.04 to +0.04** — statistically near-impossible in real retail data.

### 🔟 Age Distribution of Customers
![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/4fea14b695298e07eabea214f123734bb04523f2/Customer%20Purchase%20Behavior%20Analysis/Visuals/Age%20Distribution%20of%20Customers.jpg)
- Remarkably flat — every age bin sits between **350–420 customers**
- No natural demographic skew across a 50-year age span
- **Root cause** of the flat trends observed throughout the entire analysis

---

## 🔑 Key Findings

### ✅ Confirmed Findings
- Clothing is the **dominant revenue category** across all seasons, sizes, and metrics
- Outerwear **consistently underperforms** on every dimension — revenue, volume, seasonal demand, stock depth
- **Spring** is the strongest overall trading season
- **Medium (M)** is the top size in every category — highest stockout risk
- Accessories provides the most **seasonally stable** revenue contribution

### ❌ Null Findings (Variables That Do NOT Predict Spend)

| Variable | Hypothesis | Verdict |
|----------|-----------|---------|
| Age | Older customers spend more | ❌ Rejected — no age-spend relationship |
| Gender | Gender predicts basket size | ❌ Rejected — identical distributions |
| Loyalty (Previous Purchases) | Loyal customers spend more | ❌ Rejected — zero correlation |
| Discounts | Discounts lift basket size | ❌ Rejected — marginal negative effect |
| Promo Codes | Promos increase spend | ❌ Rejected — no category-level lift |
| Subscription Status | Subscribers spend more | ❌ Rejected — identical to non-subscribers |
| Payment Method | Method correlates with spend | ❌ Rejected — uniform across methods |

---

## 🎯 Promotional Effectiveness

| Promotional Variable | Active Avg Spend | Inactive Avg Spend | Net Effect | Verdict |
|----------------------|-----------------|-------------------|------------|---------|
| Discount Applied | ~$59 | ~$60 | -$1 | No lift — marginal negative |
| Promo Code Used | ~$60 | ~$60 | $0 | No lift — identical distributions |
| Subscription Status | ~$60 | ~$60 | $0 | No lift — identical distributions |

> 💡 **Pattern:** Three consecutive promotional variables all produce near-zero spend uplift, suggesting customers operate with a fixed **~$60 mental price anchor** that no current intervention is breaking through.

---

## 📋 Recommendations

### 🔴 High Priority
| Action | Rationale |
|--------|-----------|
| Audit Outerwear category | Underperforms across all 10 visuals — product, pricing, or visibility problem |
| Re-evaluate discount & promo ROI | No basket size uplift detected — measure frequency and acquisition instead |
| Spring season focus | Highest total revenue season — concentrate promotional and inventory budget |

### 🟡 Medium Priority
| Action | Rationale |
|--------|-----------|
| Review size S stock in Clothing | L-to-S imbalance may cause stockouts and missed conversions |
| Maintain all payment methods | No method dominant enough to rationalise removing any option |

### 🟢 Low Priority
| Action | Rationale |
|--------|-----------|
| Validate all insights on real data | Synthetic dataset — findings are directional only |

---

## 🚀 Analytical Next Steps

1. **Build a multivariate model** — incorporate income, category affinity, and geography to identify real spend drivers beyond age, gender, and loyalty
2. **Conduct CLV analysis** — determine if subscription and loyalty programmes drive long-term frequency gains even without basket size uplift
3. **Run a controlled A/B experiment** — measure discount impact on purchase **frequency**, not just transaction amount
4. **Normalise geographic revenue** by state population before drawing any location-based investment conclusions
5. **Source real transactional data** — validate all directional hypotheses from this analysis against a non-synthetic dataset

---

## ⚠️ Important Caveats

> **This dataset is synthetically generated.**

All correlation coefficients fall within **-0.04 to +0.04** — statistically impossible in real-world retail data. Evidence of synthetic generation includes:

- Perfectly uniform age distribution across a 50-year span
- Hard spend boundaries at exactly $20 and $100 across all categories
- Payment method usage within a 20-count band across 6 diverse methods
- Revenue within 11% range across all 50 U.S. states regardless of population
- Near-zero correlations across every numeric variable pair

**All findings should be treated as directional hypotheses for validation — not as strategic facts — until re-validated against real, unbalanced transactional data.**

---

## 🛠️ Dependencies

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
```

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, cleaning, and manipulation |
| `matplotlib` | Base plotting engine |
| `seaborn` | Statistical visualisations (histplots, boxplots, heatmaps, scatterplots) |
| `numpy` | Numerical operations and array handling |

---

## 📁 File Structure

```
customer-purchase-behaviour-eda/
│
├── README.md # This file
├── Customer Purchase Behaviour.csv # Source dataset
├── eda_analysis.py # Full analysis script
└── Customer_Purchase_Behaviour_Visual_Report.docx # Visual report (13 pages)
```

---

*Report generated: April 2026 | Data Analytics Division*
*Dataset: Customer Purchase Behaviour (3,900 records, 18 attributes)*

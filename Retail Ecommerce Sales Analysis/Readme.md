![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/cc4b410da91d1757ace0fa501009df24d4f864e0/Retail%20Ecommerce%20Sales%20Analysis/Cover%20image.png)

# Retail Ecommerce Sales Analysis — Exploratory Data Analysis (EDA)

**Domain:** Retail & E-Commerce Analytics &nbsp;|&nbsp; **Language:** Python 3 &nbsp;|&nbsp; **Type:** EDA / Business Intelligence

> A complete exploratory data analysis project uncovering customer behavior, product performance, regional profitability, and revenue patterns from retail transactional data.

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Dataset Description](#2-dataset-description)
3. [Project Objectives](#3-project-objectives)
4. [Tools & Technologies](#4-tools--technologies)
5. [Methodology](#5-methodology)
6. [Key Findings & Insights](#6-key-findings--insights)
   - 6.1 [Sales Distribution](#61-sales-distribution)
   - 6.2 [Temporal & Seasonal Trends](#62-temporal--seasonal-trends)
   - 6.3 [Regional Performance](#63-regional-performance)
   - 6.4 [Category & Sub-Category Analysis](#64-category--sub-category-analysis)
   - 6.5 [Discount Impact on Profitability](#65-discount-impact-on-profitability)
   - 6.6 [Customer Segmentation](#66-customer-segmentation)
   - 6.7 [Anomaly & Outlier Detection](#67-anomaly--outlier-detection)
7. [Conclusion](#7-conclusion)
8. [Future Scope](#8-future-scope)
9. [How to Run](#9-how-to-run)

---

## 1. Project Overview

- Performs an **in-depth Exploratory Data Analysis** on a real-world–style retail ecommerce transactional dataset.
- Analyses patterns across **customer segments, product categories, regional markets, pricing structures, and profitability drivers**.
- Combines structured EDA, statistical profiling, and visual storytelling to surface actionable business intelligence.
- Demonstrates how retail businesses can leverage data to optimize **marketing, inventory management, operations, and strategic planning**.

---

## 2. Dataset Description

- **Format:** CSV / Excel — order-level transactional records
- **Scope:** Individual purchase transactions with customer, product, pricing, and geographic dimensions

| Column | Type | Description |
|--------|------|-------------|
| `Order_ID` | String | Unique identifier for each purchase transaction |
| `Order_Date` | Date | Date on which the transaction was placed |
| `Customer_ID` | String | Unique identifier for each customer |
| `Segment` | Categorical | Customer segment — Consumer, Corporate, Home Office |
| `Region` | Categorical | Geographic region — East, West, Central, South |
| `Category` | Categorical | Product category — Furniture, Office Supplies, Technology |
| `Sub_Category` | Categorical | Granular product classification within each category |
| `Product_ID` | String | Unique identifier for the sold product |
| `Quantity` | Integer | Number of units purchased per order line |
| `Price` | Float (₹) | Unit selling price before discount |
| `Discount` | Float | Fractional discount applied to the transaction |
| `Sales` | Float (₹) | Total revenue after discount (`Price × Quantity × (1 - Discount)`) |
| `Profit` | Float (₹) | Net profit generated per order line |

- This structure supports deep analysis of **pricing sensitivity, customer value, revenue distribution, and operational efficiency**.

---

## 3. Project Objectives

- Analyse sales performance across time periods, customer segments, and geographic regions.
- Identify top-selling and highest-profit product categories and sub-categories.
- Quantify the impact of discount strategies on revenue generation and profit margins.
- Visualize profit trends, sales distributions, and segment-level buying behavior.
- Explore correlations among quantity, price, discount, sales, and profit.
- Detect anomalies, outliers, and irregular purchasing patterns that may indicate data quality issues or exceptional business events.

---

## 4. Tools & Technologies

| Tool / Library | Purpose |
|----------------|---------|
| `Python 3` | Core language for analysis and computation |
| `Pandas` | Data ingestion, cleaning, transformation, and aggregation |
| `NumPy` | Numerical operations and statistical computations |
| `Matplotlib` | Static charts — bar plots, line charts, histograms |
| `Seaborn` | Statistical visualizations — heatmaps, boxplots, pairplots, distributions |
| `Plotly` | Interactive visualizations for advanced exploratory analysis |
| `Jupyter Notebook` | Interactive, cell-based analysis and presentation environment |
| `Excel / CSV` | Source data format and lightweight data handling |

---

## 5. Methodology

- **Data Loading & Inspection** — Loaded the dataset, reviewed shape, column types, and initial summary statistics.
- **Data Cleaning** — Handled missing values, corrected data types, removed duplicates, and validated key numeric columns.
- **Feature Engineering** — Extracted `Month`, `Year`, and `Quarter` from `Order_Date` for temporal analysis; computed derived profit margin ratios where applicable.
- **Univariate Analysis** — Explored individual variable distributions (sales, profit, quantity, discount) using histograms, KDE plots, and descriptive statistics.
- **Bivariate & Multivariate Analysis** — Examined pairwise relationships between price, discount, sales, and profit; cross-tabulated segment and regional performance.
- **Group-Level Aggregation** — Profiled performance by category, sub-category, region, and customer segment using grouped summaries.
- **Temporal Analysis** — Resampled data by month and quarter to identify seasonality, trend cycles, and peak sales windows.
- **Outlier Detection** — Applied statistical methods (IQR, z-score) to identify extreme transactions and irregular buying behavior.
- **Visualization** — All findings communicated through clearly labelled, consistently styled charts.

---

## 6. Key Findings & Insights

### 6.1 Sales Distribution

- Sales distribution is **strongly right-skewed** — a small number of high-value transactions disproportionately influence total revenue.
- **70–80% of all transactions** fall below ₹4,000, indicating high price sensitivity among the majority of customers.
- The highest transaction density occurs in the **₹1,000–₹2,000** band — the core commercial price range.
- A long right tail extends up to ₹13,000, representing a premium purchase segment with distinct behavior.
- The skewed distribution makes **log transformation advisable** prior to any statistical modelling or machine learning tasks.

---

### 6.2 Temporal & Seasonal Trends

- Sales exhibit **clear monthly and quarterly fluctuations** — not uniformly distributed across the calendar year.
- Identifiable peak periods are likely aligned with **festive seasons, promotional events, or platform-specific discount windows**.
- Seasonal patterns provide a reliable basis for **demand forecasting, promotional campaign scheduling, and inventory pre-positioning**.

---

### 6.3 Regional Performance

- **Significant profitability differences exist across regions** — not all high-revenue regions are high-profit regions.
- Certain regions generate strong sales volumes but show compressed or negative profit margins, suggesting pricing or cost inefficiencies.
- Regional analysis identifies **priority markets for marketing investment** and regions requiring operational review.

---

### 6.4 Category & Sub-Category Analysis

- Revenue and profitability are **unevenly distributed across categories** — Technology, Furniture, and Office Supplies show distinct performance profiles.
- A concentrated set of sub-categories drives the majority of total profit, following a Pareto-style distribution.
- Identifies **high-margin niches** where inventory investment and promotional focus would deliver the greatest return.

---

### 6.5 Discount Impact on Profitability

- Discount levels have a **measurable and significant negative impact on profit margins** — higher discounts do not proportionally increase volume to compensate for margin erosion.
- Certain discount bands result in **negative profit per transaction**, indicating loss-making promotional strategies.
- Findings support a case for **discount optimization** — targeted, data-driven discounting rather than blanket percentage reductions.

---

### 6.6 Customer Segmentation

- **Consumer, Corporate, and Home Office segments** exhibit distinctly different purchasing behaviors in terms of order size, frequency, category preference, and price sensitivity.
- Segment-level profiling supports the development of **targeted marketing strategies and personalised pricing approaches**.
- Corporate segment orders tend toward higher average order values; Consumer segment shows the highest transaction volume but lower per-order profitability.

---

### 6.7 Anomaly & Outlier Detection

- Statistical outlier detection (IQR and z-score methods) reveals a subset of **extreme transactions** in both sales and profit dimensions.
- High-value outliers may represent bulk corporate orders, negotiated contracts, or data entry anomalies — warranting case-by-case review.
- Negative profit outliers highlight specific product-discount-region combinations that are structurally loss-making.

---

## 7. Conclusion

- This analysis successfully transforms raw transactional data into **structured, actionable business intelligence** across pricing, customer, product, and regional dimensions.
- Key findings confirm **strong sales seasonality**, significant category-level performance differences, and a clear inverse relationship between aggressive discounting and profitability.
- Customer segmentation insights provide a concrete basis for **targeted marketing, retention strategy, and pricing differentiation**.
- Correlation and anomaly detection outputs give businesses the tools to **refine pricing models, manage inventory more precisely, and redesign promotional structures**.
- Overall, this EDA framework establishes a **rigorous, reproducible foundation for data-driven decision-making** in the retail ecommerce context.

---

## 8. Future Scope

- **Predictive Modelling** — Build regression models to forecast sales and profit at the order, category, or region level.
- **Customer Lifetime Value (CLV) Analysis** — Extend the segmentation framework to model long-run customer value and churn risk.
- **Interactive Dashboard** — Deploy findings as a live business intelligence dashboard using Plotly Dash or Power BI.
- **Discount Optimization Model** — Develop a data-driven discount recommendation engine to maximize profit per transaction.
- **Automated Reporting Pipeline** — Schedule recurring EDA reports as the dataset is updated, enabling continuous business monitoring.

---

## 9. How to Run

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn plotly
```

### Steps

1. Clone or download this repository.
2. Place the dataset CSV file in the project root directory.
3. Launch Jupyter Notebook:

```bash
jupyter notebook Retail_Ecommerce_Sales_Analysis.ipynb
```

4. Run all cells sequentially (`Cell → Run All`).

### Notes

- Ensure the dataset filename matches the path referenced in the notebook's `pd.read_csv()` call.
- All Matplotlib and Seaborn plots render inline within the notebook.
- Plotly charts require a compatible Jupyter environment (`jupyterlab` or `notebook>=6.x`).

---

*This project is intended for educational and portfolio purposes. All analysis is based on the provided dataset and does not constitute commercial or investment advice.*

Amazon Sale Report — Exploratory Data Analysis (EDA)
Domain: E-Commerce & Retail Analytics  |  Language: Python 3  |  Type: EDA / Data Analysis

Table of Contents

Project Overview
Objectives
Tools & Libraries
Dataset Description
Methodology
Insights & Findings
Outcomes
How to Run


1. Project Overview

Performs an in-depth Exploratory Data Analysis (EDA) on the Amazon Sale Report dataset.
Analyses sales trends, order patterns, product performance, and fulfillment insights to derive actionable business conclusions.
Transforms raw sales data into structured, meaningful intelligence using Python-based visualization and data-handling libraries.
Designed to serve as a data-driven foundation for business strategy, marketing targeting, and operational optimization.


2. Objectives

Clean and preprocess the raw Amazon sales dataset to ensure analytical integrity.
Explore and understand relationships between key variables — categories, states, order status, and fulfillment channels.
Visualize customer behavior, sales trends, and category-level performance patterns.
Derive actionable, data-driven insights to support sales strategy and operational decisions.


3. Tools & Libraries
Tool / LibraryPurposePython 3Core language for data analysis and computationPandasData loading, manipulation, cleaning, and aggregationNumPyNumerical operations and array-based computationsMatplotlibStatic charts, trend lines, and bar visualizationsSeabornStatistical and aesthetic plots — heatmaps, countplots, distributions

4. Dataset Description

Source: Amazon Sale Report (raw transactional sales data)
Domain: E-commerce retail — orders, fulfillment, categories, and geography
Key variables analysed:
VariableDescriptionOrder StatusShipped, cancelled, pending, returned — fulfillment lifecycleProduct CategoryCategory-level revenue and volume breakdownStateGeographic distribution of orders and revenueFulfillment MethodChannel through which orders were processed and dispatchedSales ChannelPlatform or medium through which the sale was madeDate / MonthTemporal dimension for trend and seasonality analysis



5. Methodology

Data Cleaning — Handled missing values, corrected data types, removed duplicates, and standardized column formats.
Univariate Analysis — Explored individual variable distributions using histograms, countplots, and summary statistics.
Bivariate Analysis — Examined relationships between sales, categories, geographies, and fulfillment channels.
Temporal Analysis — Resampled data by month to identify seasonal trends and sales peaks.
Categorical Profiling — Aggregated revenue and order counts by category, state, and fulfillment method.
Visualization — All findings communicated through clearly labelled, publication-quality charts.


6. Insights & Findings

Sales Performance — A small number of top-performing states contribute disproportionately to total revenue, identifying high-priority geographic targets for focused marketing and inventory allocation.
Order Trends — Shipped orders dominate the order status distribution, reflecting strong overall fulfillment efficiency; cancellation rates remain minimal across the dataset.
Category Insights — A concentrated set of product categories drives the majority of revenue, highlighting profitable niches where inventory investment and promotional spend would yield the highest returns.
Seasonal Patterns — Sales volumes show clear monthly peaks, likely aligned with festive seasons, discount windows, or platform-specific sale events — providing a basis for demand forecasting and campaign planning.
Operational Insight — Fulfillment method and sales channel have a measurable impact on order success rates, suggesting that channel-specific strategies could further improve conversion and reduce order failures.


7. Outcomes

Demonstrates how EDA techniques can surface hidden patterns in large-scale e-commerce sales data and convert them into strategic business conclusions.
Establishes a reusable analytical workflow — from raw data ingestion and cleaning through to visual storytelling — applicable to similar retail or marketplace datasets.
Serves as a portfolio-ready case study showcasing analytical thinking, data visualization, and insight communication through data.


8. How to Run
Prerequisites
bashpip install pandas numpy matplotlib seaborn
Steps

Clone or download this repository.
Place the Amazon Sale Report CSV file in the project root directory.
Launch Jupyter Notebook:

bashjupyter notebook Amazon_Sale_Report_EDA.ipynb

Run all cells sequentially (Cell → Run All).

Notes

Ensure the dataset filename matches the path referenced in the notebook's pd.read_csv() call.
All visualizations render inline within the notebook — no external exports required.
The notebook is fully self-contained; no external APIs or additional data sources are needed.



![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/c1f2a32f2c91341c6259bda2939b3a565395d93a/Car%20%20Price%20Analysis/Cover%20image.png)


# 🚗 Car Price Analysis Dataset

**Domain:** Automotive & Market Analysis &nbsp;|&nbsp; **Records:** 2,500 &nbsp;|&nbsp; **Features:** 10 &nbsp;|&nbsp; **Format:** CSV

---

## Table of Contents

1. [Overview](#1-overview)
2. [Dataset Summary](#2-dataset-summary)
3. [Features Description](#3-features-description)
4. [Potential Use Cases](#4-potential-use-cases)
5. [Key Observations](#5-key-observations)
6. [Data Quality](#6-data-quality)
7. [License & Usage](#7-license--usage)
8. [Author Notes](#8-author-notes)

---

## 1. Overview

- A comprehensive collection of **2,500 automobile records** designed for data analysis, machine learning, and statistical modelling within the automotive domain.
- Captures a wide range of vehicle attributes — from **technical specifications to market pricing** — making it a versatile resource for researchers, data scientists, and analysts.
- Covers both the **used and new car market** across seven major global brands, four fuel types, and two transmission categories.
- Structured and cleaned for **immediate use** in analytical workflows, visualisation pipelines, and machine learning experiments without requiring additional preprocessing.

---

## 2. Dataset Summary

| Attribute | Detail |
|-----------|--------|
| **Total Records** | 2,500 rows |
| **Total Features** | 10 columns |
| **File Format** | CSV |
| **Domain** | Automotive / Market Analysis |
| **Primary Use Case** | Pricing Prediction, Trend Analysis, Vehicle Comparison |
| **Missing Values** | None |
| **Preprocessing Required** | None — ready for immediate use |

---

## 3. Features Description

| Column | Type | Description |
|--------|------|-------------|
| `Brand` | Categorical | Vehicle manufacturer (e.g., Toyota, BMW, Tesla) |
| `Model` | Categorical | Specific model name (e.g., Corolla, X5, Model S) |
| `Year` | Integer | Year of manufacture — range: 2000 to 2024 |
| `Engine_Size` | Float | Engine displacement in litres — range: 1.0 to 6.0 |
| `Fuel_Type` | Categorical | Fuel category — Petrol, Diesel, Electric, or Hybrid |
| `Transmission` | Categorical | Gearbox type — Manual or Automatic |
| `Mileage` | Integer | Total distance driven by the vehicle (km / miles) |
| `Condition` | Categorical | Vehicle condition rating — New, Used, or Like New |
| `Price` | Integer | Market price of the vehicle in local currency (₹) |

---

## 4. Potential Use Cases

- **Price Prediction** — Build regression or ensemble models to estimate vehicle market value based on technical specifications, condition, and brand.
- **Market Trend Analysis** — Explore how pricing, fuel type preferences, and brand share patterns evolve across manufacturing years.
- **Vehicle Segmentation** — Apply clustering techniques to identify distinct market segments based on vehicle attributes and pricing tiers.
- **Brand Benchmarking** — Compare brands systematically across average price, mileage accumulation, and inventory distribution.
- **Transmission & Fuel Insights** — Analyse consumer preference patterns and pricing differentials across fuel types and transmission categories.

---

## 5. Key Observations

- All seven brands — Tesla, BMW, Audi, Ford, Honda, Mercedes-Benz, and Toyota — are nearly equally represented at approximately **14–15% market share each**, indicating a well-balanced brand distribution.
- Average prices across all brands fall within a narrow **₹51,000–₹54,000 range**, confirming that brand alone is a weak price differentiator in this dataset.
- **No strong linear correlation exists** between any two numerical features, making this dataset particularly well-suited for non-linear modelling approaches such as Random Forest, Gradient Boosting, or neural networks.
- **Manual transmission vehicles slightly outnumber Automatic** across all brands, with the gap being most pronounced in Ford and most balanced in Toyota.

---

## 6. Data Quality

| Quality Check | Status |
|---------------|--------|
| Missing Values | ✅ None across all columns |
| Column Formatting | ✅ Consistent and standardised throughout |
| Categorical Class Distribution | ✅ Balanced across all categorical variables |
| Duplicate Records | ✅ None detected |
| Preprocessing Required | ✅ Dataset is analysis-ready as supplied |

---

## 7. License & Usage

- This dataset is intended strictly for **educational, research, and non-commercial analytical purposes**.
- Appropriate **attribution is required** if the dataset is used in published work, academic submissions, or shared projects.
- Commercial use or redistribution without explicit permission is **not permitted**.

---

## 8. Author Notes

> Each row represents a single vehicle entry with its complete set of associated attributes. The dataset has been structured, validated, and cleaned to ensure immediate usability across statistical workflows, visualisation pipelines, and machine learning experiments — no additional preprocessing steps are required prior to analysis.

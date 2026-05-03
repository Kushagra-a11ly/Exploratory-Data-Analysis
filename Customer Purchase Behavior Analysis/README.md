# 🛍️ Customer Shopping Behavior Dataset

> A structured, transaction-level dataset capturing retail and e-commerce customer behavior —
> built for exploratory analysis, segmentation, forecasting, and machine learning.


## 📑 Table of Contents

- [Overview](#-overview)
- [Objectives](#-objectives)
- [Dataset Structure](#-dataset-structure)
- [Feature Reference](#-feature-reference)
- [Use Cases](#-use-cases)
- [Getting Started](#-getting-started)
- [Notes & Considerations](#-notes--considerations)
- [License](#-license)

---

## 📌 Overview

This dataset provides a comprehensive view of customer shopping behavior across retail and e-commerce channels.
Each row represents a **single customer transaction**, combining demographic attributes with detailed purchase and behavioral data.

It is designed to support data-driven decision-making in areas such as:

- 📣 Marketing optimization
- 👥 Customer segmentation
- 📦 Demand forecasting
- 📊 Business intelligence

---

## 🎯 Objectives

| # | Goal |
|---|------|
| 1 | Understand customer purchasing behavior across demographics |
| 2 | Identify trends in age, gender, and geographic segments |
| 3 | Analyze the impact of discounts and promotional strategies |
| 4 | Evaluate seasonal effects on sales volume and spend |
| 5 | Study payment preferences and transaction patterns |
| 6 | Support predictive modeling and recommendation systems |

---

## 🗂️ Dataset Structure

```
Type          : Structured (Tabular)
Granularity   : Transaction-level
Variables     : Mix of categorical and numerical features
Format        : CSV / Tabular
```

The dataset combines four categories of information:

| Category | Description |
|----------|-------------|
| **Customer Demographics** | Who is buying |
| **Product Information** | What is being bought |
| **Transaction Details** | How and when it was purchased |
| **Behavioral Indicators** | Purchase frequency, loyalty signals, and preferences |

---

## 📋 Feature Reference

| Column | Type | Description |
|--------|------|-------------|
| `Customer ID` | Categorical | Unique identifier for each customer |
| `Age` | Numerical | Customer age in years |
| `Gender` | Categorical | Customer gender (Male / Female) |
| `Item Purchased` | Categorical | Name of the specific product purchased |
| `Category` | Categorical | Product category (e.g., Clothing, Accessories, Footwear) |
| `Purchase Amount (USD)` | Numerical | Total transaction value in US dollars |
| `Location` | Categorical | Customer's geographic region or state |
| `Size` | Categorical | Item size (S, M, L, XL, etc.) |
| `Color` | Categorical | Color of the purchased product |
| `Season` | Categorical | Season of purchase (Spring, Summer, Fall, Winter) |
| `Review Rating` | Numerical | Customer product rating (1–5 scale) |
| `Subscription Status` | Categorical | Whether the customer has an active subscription (Yes / No) |
| `Payment Method` | Categorical | Payment method used in this specific transaction |
| `Shipping Type` | Categorical | Delivery option selected (Standard, Express, etc.) |
| `Discount Applied` | Categorical | Whether a discount was applied (Yes / No) |
| `Promo Code Used` | Categorical | Whether a promo code was used (Yes / No) |
| `Previous Purchases` | Numerical | Total number of prior purchases by the customer |
| `Preferred Payment Method` | Categorical | Customer's habitual payment preference |
| `Frequency of Purchases` | Categorical | Purchase cadence (Weekly, Monthly, Annually, etc.) |

> ⚠️ **Note:** `Payment Method` and `Preferred Payment Method` are distinct fields.
> The former reflects what was used in a specific transaction; the latter reflects the customer's stated or historical preference.

---

## 💡 Use Cases

### 📈 Exploratory Data Analysis (EDA)
- Visualize spending trends across age groups, genders, and regions
- Identify seasonal purchase spikes and category performance
- Analyze product popularity and review rating distributions

### 👥 Customer Segmentation
- Cluster customers by purchase frequency, spend, and loyalty indicators
- Identify high-value customers and at-risk churners
- Build targeted campaigns for distinct behavioral groups

### 💰 Revenue & Sales Analysis
- Measure the uplift from discounts and promo codes
- Calculate average order value (AOV) across segments
- Benchmark performance by location, category, or season

### 🤖 Predictive Modeling
- Build churn prediction or lifetime value (LTV) models
- Develop product recommendation systems
- Forecast demand by category and season

---

## 🚀 Getting Started

### 1. Load the Dataset

**Python**
```python
import pandas as pd

df = pd.read_csv("shopping_behavior.csv")
print(df.shape)
df.head()
```

**R**
```r
df <- read.csv("shopping_behavior.csv")
head(df)
```

### 2. Initial Exploration

```python
# Summary statistics
df.describe(include="all")

# Missing value audit
df.isnull().sum()

# Distribution of key columns
df["Category"].value_counts()
df["Purchase Amount (USD)"].hist(bins=30)
```

### 3. Preprocessing Checklist

- [ ] Encode categorical variables (Label Encoding or One-Hot Encoding)
- [ ] Normalize / scale numerical features for ML pipelines
- [ ] Handle missing or inconsistent values
- [ ] Verify distinction between `Payment Method` and `Preferred Payment Method`
- [ ] Parse or bin `Age` and `Frequency of Purchases` as needed

---

## ⚠️ Notes & Considerations

| Topic | Detail |
|-------|--------|
| **Categorical Encoding** | Most columns are categorical and require encoding before use in ML models |
| **Duplicate Detection** | Verify that `Customer ID` entries are unique per transaction vs. per customer |
| **Feature Leakage** | Use behavioral fields like `Previous Purchases` carefully in predictive models |
| **Scalability** | Structure supports scaling; account for dataset size in performance-sensitive operations |
| **Privacy** | No PII beyond anonymized IDs — handle in compliance with applicable data privacy regulations |

---

## 📄 License

Specify the applicable license here (e.g., `MIT`, `CC BY 4.0`, or `Proprietary`).

---

<p align="center">
  Made with ❤️ for data-driven retail analytics
</p>

# 🚗 Car Price Prediction Dataset

**Domain:** Automotive & Market Pricing &nbsp;|&nbsp; **Records:** 2,500 &nbsp;|&nbsp; **Features:** 10 &nbsp;|&nbsp; **Format:** CSV &nbsp;|&nbsp; **Task:** Regression / Price Prediction

---

## Table of Contents

1. [Overview](#1-overview)
2. [Dataset Summary](#2-dataset-summary)
3. [Column Descriptions](#3-column-descriptions)
4. [Statistical Summary](#4-statistical-summary)
5. [Categorical Distributions](#5-categorical-distributions)
   - [Brand](#brand)
   - [Fuel Type](#fuel-type)
   - [Transmission](#transmission)
   - [Condition](#condition)
6. [Models Included](#6-models-included)
7. [Potential Use Cases](#7-potential-use-cases)
8. [Data Quality Notes](#8-data-quality-notes)
9. [Recommended Libraries](#9-recommended-libraries)
10. [Quick Load](#10-quick-load)
11. [License & Usage](#11-license--usage)

---

## 1. Overview

- Contains **2,500 detailed automobile records** spanning multiple brands, models, and manufacturing years from 2000 to 2023.
- Designed to support a wide range of data science tasks in the automotive domain — including **price prediction, trend analysis, vehicle segmentation, and brand benchmarking**.
- Each row represents a single vehicle with its complete set of attributes, making it **immediately usable** for analytical and modelling workflows without additional preprocessing.
- Features a rich mix of **numerical and categorical variables** covering technical specifications, usage history, and market pricing.

---

## 2. Dataset Summary

| Attribute | Detail |
|-----------|--------|
| **File Name** | `car_price_prediction.csv` |
| **Total Records** | 2,500 rows |
| **Total Features** | 10 columns |
| **File Format** | CSV (Comma-Separated Values) |
| **Domain** | Automotive / Market Pricing |
| **Primary Task** | Regression / Price Prediction |
| **Missing Values** | None |
| **Duplicate Records** | None detected |

---

## 3. Column Descriptions

| Column | Data Type | Description |
|--------|-----------|-------------|
| `Car ID` | Integer | Unique identifier for each vehicle record (1–2,500) |
| `Brand` | String | Manufacturer name — 7 brands: Audi, BMW, Ford, Honda, Mercedes, Tesla, Toyota |
| `Model` | String | Specific vehicle model — 28 unique models (e.g., Corolla, X5, Model S) |
| `Year` | Integer | Manufacturing year — range: 2000 to 2023 |
| `Engine Size` | Float | Engine displacement in litres — range: 1.0L to 6.0L |
| `Fuel Type` | String | Fuel category — Petrol, Diesel, Electric, or Hybrid |
| `Transmission` | String | Gearbox type — Manual or Automatic |
| `Mileage` | Integer | Total distance driven in miles — range: 15 to 299,967 |
| `Condition` | String | Vehicle condition — New, Used, or Like New |
| `Price` | Float | Market price in USD — range: $5,011.27 to $99,982.59 |

---

## 4. Statistical Summary

| Feature | Min | Mean | Median | Max | Std Dev |
|---------|-----|------|--------|-----|---------|
| `Year` | 2000 | 2011.6 | 2012 | 2023 | 6.99 |
| `Engine Size` | 1.0L | 3.47L | 3.4L | 6.0L | 1.43 |
| `Mileage` | 15 | 149,750 | 149,085 | 299,967 | 87,920 |
| `Price` | $5,011 | $52,638 | $53,485 | $99,983 | $27,296 |

---

## 5. Categorical Distributions

### Brand

| Brand | Count | Share |
|-------|-------|-------|
| Toyota | 374 | 14.96% |
| Audi | 368 | 14.72% |
| BMW | 358 | 14.32% |
| Mercedes | 353 | 14.12% |
| Honda | 352 | 14.08% |
| Tesla | 348 | 13.92% |
| Ford | 347 | 13.88% |

### Fuel Type

| Fuel Type | Count | Share |
|-----------|-------|-------|
| Diesel | 655 | 26.20% |
| Petrol | 630 | 25.20% |
| Electric | 614 | 24.56% |
| Hybrid | 601 | 24.04% |

### Transmission

| Type | Count | Share |
|------|-------|-------|
| Manual | 1,308 | 52.32% |
| Automatic | 1,192 | 47.68% |

### Condition

| Condition | Count | Share |
|-----------|-------|-------|
| Used | 855 | 34.20% |
| Like New | 836 | 33.44% |
| New | 809 | 32.36% |

---

## 6. Models Included

> 28 unique vehicle models across 7 brands

`3 Series` · `5 Series` · `A3` · `A4` · `Accord` · `C-Class` · `CR-V` · `Camry` · `Civic` · `Corolla` · `E-Class` · `Explorer` · `Fiesta` · `Fit` · `Focus` · `GLA` · `GLC` · `Model 3` · `Model S` · `Model X` · `Model Y` · `Mustang` · `Prius` · `Q5` · `Q7` · `RAV4` · `X3` · `X5`

---

## 7. Potential Use Cases

- **Price Prediction** — Train regression models (Linear Regression, XGBoost, Random Forest) to predict vehicle market value based on specifications, condition, and age.
- **Market Trend Analysis** — Study how pricing patterns evolve across manufacturing years and fuel type categories.
- **Vehicle Segmentation** — Apply clustering algorithms to group vehicles by similar characteristics or price tiers.
- **Brand & Model Benchmarking** — Compare average pricing, mileage accumulation, and inventory distribution across brands and models.
- **Feature Importance Analysis** — Identify which attributes (year, mileage, fuel type, etc.) most significantly drive price variation.
- **EDA & Visualisation** — The rich mix of categorical and numerical features makes this dataset ideal for exploratory data analysis exercises and portfolio projects.

---

## 8. Data Quality Notes

| Check | Status |
|-------|--------|
| Missing Values | ✅ None across all 10 columns |
| Duplicate Records | ✅ None detected |
| Class Distribution | ✅ Balanced across Brand, Fuel Type, Condition, and Transmission |
| Column Formatting | ✅ Consistent — no mixed types or encoding issues |
| Preprocessing Required | ✅ None — dataset is analysis-ready as supplied |
| Inter-Feature Correlation | ⚠️ Near-zero across all numerical features — non-linear models recommended over simple linear approaches |

---

## 9. Recommended Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_absolute_error, r2_score
```

---

## 10. Quick Load

```python
import pandas as pd

df = pd.read_csv('car_price_prediction.csv')
print(df.shape)      # (2500, 10)
print(df.dtypes)
print(df.describe())
```

---

## 11. License & Usage

- This dataset is intended for **educational, research, and non-commercial analytical purposes** only.
- Appropriate **attribution is required** if used in published work, academic submissions, or shared repositories.
- Commercial use or redistribution without explicit permission is **not permitted**.

---

*Last Updated: 2025 &nbsp;|&nbsp; Records: 2,500 &nbsp;|&nbsp; Features: 10 &nbsp;|&nbsp; Domain: Automotive Pricing*

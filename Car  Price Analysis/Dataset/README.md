# 🚗 Car Price Prediction Dataset

## Overview

This dataset contains detailed records of automobiles spanning multiple brands, models, and manufacturing years. It is designed to support a wide range of data science and machine learning tasks in the automotive domain — including price prediction, trend analysis, segmentation, and vehicle comparison. Each row represents a single vehicle with its complete set of attributes, making it immediately usable for analytical and modelling workflows without additional preprocessing.

---

## Dataset Summary

| Attribute            | Details                                      |
|----------------------|----------------------------------------------|
| **File Name**        | `car_price_prediction.csv`                   |
| **Total Records**    | 2,500 rows                                   |
| **Total Features**   | 10 columns                                   |
| **File Format**      | CSV (Comma-Separated Values)                 |
| **Domain**           | Automotive / Market Pricing                  |
| **Primary Task**     | Regression / Price Prediction                |
| **Missing Values**   | None                                         |
| **Duplicate Records**| None detected                                |

---

## Column Descriptions

| Column          | Data Type | Description                                                                 |
|-----------------|-----------|-----------------------------------------------------------------------------|
| `Car ID`        | Integer   | Unique identifier for each vehicle record (1–2500)                          |
| `Brand`         | String    | Manufacturer name — 7 brands: Audi, BMW, Ford, Honda, Mercedes, Tesla, Toyota |
| `Model`         | String    | Specific vehicle model — 28 unique models (e.g., Corolla, X5, Model S)     |
| `Year`          | Integer   | Manufacturing year, ranging from 2000 to 2023                               |
| `Engine Size`   | Float     | Engine displacement in litres, ranging from 1.0L to 6.0L                   |
| `Fuel Type`     | String    | Fuel category — Petrol, Diesel, Electric, Hybrid                            |
| `Transmission`  | String    | Gearbox type — Manual or Automatic                                          |
| `Mileage`       | Integer   | Total distance driven in miles, ranging from 15 to 299,967                 |
| `Condition`     | String    | Vehicle condition — New, Used, or Like New                                  |
| `Price`         | Float     | Market price in USD, ranging from $5,011.27 to $99,982.59                  |

---

## Statistical Summary

| Feature       | Min       | Mean       | Median     | Max        | Std Dev    |
|---------------|-----------|------------|------------|------------|------------|
| `Year`        | 2000      | 2011.6     | 2012       | 2023       | 6.99       |
| `Engine Size` | 1.0L      | 3.47L      | 3.4L       | 6.0L       | 1.43       |
| `Mileage`     | 15        | 149,750    | 149,085    | 299,967    | 87,920     |
| `Price`       | $5,011    | $52,638    | $53,485    | $99,983    | $27,296    |

---

## Categorical Distributions

### Brand
| Brand    | Count | Share  |
|----------|-------|--------|
| Toyota   | 374   | 14.96% |
| Audi     | 368   | 14.72% |
| BMW      | 358   | 14.32% |
| Mercedes | 353   | 14.12% |
| Honda    | 352   | 14.08% |
| Tesla    | 348   | 13.92% |
| Ford     | 347   | 13.88% |

### Fuel Type
| Fuel Type | Count | Share  |
|-----------|-------|--------|
| Diesel    | 655   | 26.20% |
| Petrol    | 630   | 25.20% |
| Electric  | 614   | 24.56% |
| Hybrid    | 601   | 24.04% |

### Transmission
| Type      | Count | Share  |
|-----------|-------|--------|
| Manual    | 1,308 | 52.32% |
| Automatic | 1,192 | 47.68% |

### Condition
| Condition | Count | Share  |
|-----------|-------|--------|
| Used      | 855   | 34.20% |
| Like New  | 836   | 33.44% |
| New       | 809   | 32.36% |

---

## Models Included

> 28 unique vehicle models across 7 brands

`3 Series` · `5 Series` · `A3` · `A4` · `Accord` · `C-Class` · `CR-V` · `Camry` · `Civic` · `Corolla` · `E-Class` · `Explorer` · `Fiesta` · `Fit` · `Focus` · `GLA` · `GLC` · `Model 3` · `Model S` · `Model X` · `Model Y` · `Mustang` · `Prius` · `Q5` · `Q7` · `RAV4` · `X3` · `X5`

---

## Potential Use Cases

- **Price Prediction** — Train regression models (Linear Regression, XGBoost, Random Forest) to predict vehicle market value based on specs, condition, and age
- **Market Trend Analysis** — Study how pricing patterns evolve across manufacturing years and fuel types
- **Vehicle Segmentation** — Apply clustering algorithms to group vehicles by similar characteristics or price tiers
- **Brand & Model Benchmarking** — Compare average pricing, mileage, and inventory distribution across brands
- **Feature Importance Analysis** — Identify which attributes (year, mileage, fuel type, etc.) most significantly drive price variation
- **EDA & Visualization** — Rich categorical and numerical mix makes this ideal for exploratory data analysis exercises

---

## Data Quality Notes

- ✅ **No missing values** across all 10 columns
- ✅ **No duplicate records** detected
- ✅ **Balanced class distribution** across Brand, Fuel Type, Condition, and Transmission
- ✅ **Consistent formatting** — no mixed types or encoding issues
- ✅ **Ready to use** — no preprocessing or cleaning required before modelling
- ⚠️ **Near-zero inter-feature correlations** — features are largely independent; non-linear models are recommended over simple linear approaches

---

## Recommended Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_absolute_error, r2_score
```

## Quick Load

```python
import pandas as pd

df = pd.read_csv('car_price_prediction.csv')
print(df.shape)       # (2500, 10)
print(df.dtypes)
print(df.describe())
```

---

## License & Usage

This dataset is intended for **educational, research, and non-commercial analytical purposes**. Please provide appropriate attribution if used in published work, academic projects, or shared repositories.

---

*Last Updated: 2025 · Records: 2,500 · Features: 10 · Domain: Automotive Pricing*

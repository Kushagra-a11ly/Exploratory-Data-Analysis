![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/c1f2a32f2c91341c6259bda2939b3a565395d93a/Car%20%20Price%20Analysis/Cover%20image.png)



# 🚗 Car Price Prediction — Exploratory Data Analysis

> A comprehensive EDA of 2,500 automobile records spanning 7 global brands, 28 models, and 4 fuel types, uncovering pricing dynamics, brand positioning, and feature independence through 18 visualisations.

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Features](#features)
- [Statistical Summary](#statistical-summary)
- [Installation & Setup](#installation--setup)
- [Analysis Walkthrough](#analysis-walkthrough)
- [Key Findings](#key-findings)
- [Visualisations](#visualisations)
- [Next Steps & Roadmap](#next-steps--roadmap)
- [Tech Stack](#tech-stack)

---

## Project Overview

This project performs a full **Exploratory Data Analysis (EDA)** on a car price prediction dataset to understand pricing structure, feature distributions, brand behaviour, and inter-variable relationships before building a predictive model.

The analysis reveals a highly curated, near-uniformly distributed dataset where **no single numerical feature independently predicts price** — pointing toward non-linear ensemble models as the recommended modelling approach.

---

## Dataset

| Property | Value |
|---|---|
| **File** | `car_price_prediction.csv` |
| **Records** | 2,500 rows |
| **Features** | 10 columns |
| **Format** | CSV (Comma-Separated Values) |
| **Domain** | Automotive / Market Pricing |
| **Primary Task** | Regression / Price Prediction |
| **Missing Values** | None |
| **Duplicate Records** | None detected |
| **Price Range** | $5,011 — $99,983 |
| **Brands** | 7 |
| **Models** | 28 unique |
| **Fuel Types** | 4 |

---

## Features

| Column | Type | Description |
|---|---|---|
| `Car ID` | Integer | Unique record identifier (1–2,500) |
| `Brand` | String | Manufacturer — Audi, BMW, Ford, Honda, Mercedes, Tesla, Toyota |
| `Model` | String | Specific vehicle model — 28 unique models |
| `Year` | Integer | Manufacturing year — range: 2000–2023 |
| `Engine Size` | Float | Engine displacement in litres — range: 1.0L–6.0L |
| `Fuel Type` | String | Petrol, Diesel, Electric, or Hybrid |
| `Transmission` | String | Manual or Automatic |
| `Mileage` | Integer | Total distance driven in miles — range: 15–299,967 |
| `Condition` | String | New, Used, or Like New |
| `Price` | Float | Market price in USD — range: $5,011–$99,983 |

---

## Statistical Summary

| Feature | Min | Mean | Median | Max | Std Dev |
|---|---|---|---|---|---|
| **Year** | 2000 | 2011.6 | 2012 | 2023 | 6.99 |
| **Engine Size (L)** | 1.0 | 3.47 | 3.4 | 6.0 | 1.43 |
| **Mileage** | 15 | 149,750 | 149,085 | 299,967 | 87,920 |
| **Price (USD)** | $5,011 | $52,638 | $53,485 | $99,983 | $27,296 |

---

## Installation & Setup

### Prerequisites

- Python 3.8+
- pip

### Clone the Repository

```bash
git clone https://github.com/your-username/car-price-prediction-eda.git
cd car-price-prediction-eda
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

**`requirements.txt`**

```
pandas
numpy
matplotlib
seaborn
scipy
jupyter
```

### Run the Notebook

```bash
jupyter notebook car_price_eda.ipynb
```

Or run the script directly:

```bash
python eda.py
```

---

## Analysis Walkthrough

The EDA is structured into **18 visualisations** across the following analytical phases:

### 1. Data Cleaning & Preprocessing

```python
# Duplicate check
df.drop_duplicates()

# Null check
df.isnull().sum()

# Unique value counts per categorical feature
df['Brand'].value_counts()

# Correlation matrix
df.corr(numeric_only=True)

# IQR-based outlier detection on Price
Q1 = df['Price'].quantile(0.25)
Q3 = df['Price'].quantile(0.75)

# Skewness and kurtosis
from scipy import stats
stats.skew(df['Price'])
stats.kurtosis(df['Price'])
```

### 2. Univariate Analysis

- **Price distribution** — KDE histogram to assess shape, skewness, and dominant price bands
- **Year distribution** — Line chart of manufacturing year counts (2000–2023)
- **Transmission split** — Count chart for Manual vs. Automatic
- **Brand market share** — Pie chart of inventory by manufacturer

### 3. Bivariate Analysis

- **Price by Brand** — Boxplots revealing spread and outliers per manufacturer
- **Price by Condition** — Boxplots comparing New, Used, and Like New
- **Average Price by Fuel Type** — Bar chart with confidence intervals
- **Average Price by Brand** — Horizontal bar chart for brand-level ranking
- **Average Price by Year** — Line chart tracking depreciation over time
- **Average Mileage by Brand** — Bar chart with confidence intervals
- **Mileage vs. Price** — Scatter plot testing the usage-value relationship
- **Engine Size vs. Price** — Scatter plot testing displacement as a price driver

### 4. Multivariate Analysis

- **Correlation Matrix** — Heatmap across all numerical features (magma palette)
- **Pair Plot** — 4×4 grid across Price, Mileage, Engine Size, Year
- **Model Price Comparison by Brand** — Grouped bar chart at model level
- **Inventory by Brand and Transmission** — Grouped count chart
- **Mileage vs. Price by Transmission** — Faceted scatter plot
- **Hexbin Density — Mileage vs. Price** — Density map (plasma palette)

---

## Key Findings

### Price Structure

- Price distribution is **remarkably flat and uniform** — no dominant price band, near-zero skewness and kurtosis.
- This strongly suggests the dataset was **deliberately sampled** to represent all segments proportionally — not drawn from a real-world distribution.

### Feature Independence

- **All numerical features are operationally independent** — every off-diagonal correlation is near zero (max: 0.037 between Year and Price).
- Mileage, Engine Size, and Year all fail to explain price variation individually or in combination.

### Brand Positioning

- **BMW** commands the highest average price (~$54,000); **Ford** the lowest (~$51,000).
- The entire brand price range spans only ~$3,000 — brand alone is a weak price differentiator.
- **Tesla** ranks second in average price, narrowly ahead of Mercedes-Benz, reflecting successful premium positioning.

### Fuel Type

- **Diesel** vehicles carry the highest average price (~$55,000); **Electric** the lowest (~$51,000).
- All four fuel types fall within a ~$4,000 range — fuel type is not a strong price signal.

### Condition

- New, Used, and Like New vehicles share **nearly identical median prices** (~$52,000–$55,000).
- Condition rating does not meaningfully separate price.

### Transmission

- **52% Manual | 48% Automatic** — a near-even split across all seven brands.
- Toyota is the only brand with an exactly balanced Manual/Automatic inventory.

### Market Share

- Brand shares range from **13.9% to 15.0%** — statistically unusual uniformity confirming curated sampling.

---

## Visualisations

| # | Chart | Type | Purpose |
|---|---|---|---|
| 1 | Price Distribution | Histogram + KDE | Overall pricing landscape |
| 2 | Price by Brand | Boxplot | Brand-level spread and positioning |
| 3 | Mileage vs. Price | Scatter | Usage-value relationship |
| 4 | Average Price by Fuel Type | Bar + CI | Powertrain price premiums |
| 5 | Transmission Distribution | Count Chart | Manual vs. Automatic split |
| 6 | Correlation Matrix | Heatmap | Numerical feature relationships |
| 7 | Engine Size vs. Price | Scatter | Displacement as a price driver |
| 8 | Price by Condition | Boxplot | Condition-based pricing |
| 9 | Cars by Manufacturing Year | Line Chart | Inventory trends (2000–2023) |
| 10 | Average Mileage by Brand | Bar + CI | Brand ownership patterns |
| 11 | Average Price by Brand | Horizontal Bar | Brand price ranking |
| 12 | Average Price by Year | Line Chart | Depreciation trajectory |
| 13 | Model Price Comparison | Grouped Bar | Model-level price variation |
| 14 | Inventory by Brand & Transmission | Grouped Count | Supply breakdown |
| 15 | Pair Plot | 4×4 Grid | All bivariate relationships |
| 16 | Mileage vs. Price by Transmission | Faceted Scatter | Transmission-segmented pricing |
| 17 | Brand Market Share | Pie Chart | Inventory distribution |
| 18 | Mileage vs. Price Density | Hexbin | Dominant listing combinations |

---

## Next Steps & Roadmap

### Feature Engineering

- Create interaction terms: `Brand × Fuel Type`, `Year × Mileage`
- Encode categorical variables using **target encoding** or **one-hot encoding**
- Derive age feature: `Current Year − Manufacturing Year`

### Baseline Modelling

```python
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor
from xgboost import XGBRegressor

# Train and compare
models = {
    "Linear Regression": LinearRegression(),
    "Random Forest": RandomForestRegressor(n_estimators=100),
    "XGBoost": XGBRegressor(n_estimators=100)
}
```

### Hyperparameter Tuning

```python
from sklearn.model_selection import GridSearchCV
# or
import optuna
```

Tune: tree depth, learning rate, regularisation parameters, number of estimators.

### Interpretability

```python
import shap
explainer = shap.TreeExplainer(model)
shap_values = explainer.shap_values(X_test)
shap.summary_plot(shap_values, X_test)
```

SHAP values to interpret per-prediction feature contributions.

### Segmented Modelling

Train separate models per brand or condition group — test whether within-segment models outperform a global model.

### Deployment

- Export final model as a **REST API endpoint** (FastAPI or Flask)
- Integrate into a vehicle pricing dashboard or web tool

---

## Tech Stack

| Tool | Purpose |
|---|---|
| **Python 3.x** | Core language |
| **Pandas** | Data loading, cleaning, and manipulation |
| **NumPy** | Numerical operations |
| **Matplotlib** | Base plotting layer |
| **Seaborn** | Statistical visualisation |
| **SciPy** | Skewness and kurtosis computation |
| **Jupyter Notebook** | Interactive analysis environment |

---

## Project Structure

```
car-price-prediction-eda/
│
├── data/
│   └── car_price_prediction.csv
│
├── notebooks/
│   └── car_price_eda.ipynb
│
├── outputs/
│   └── figures/              
│
├── eda.py                     
├── requirements.txt
└── README.md
```

---

## License

This project is released under the [MIT License](LICENSE).

---

## Author

**Your Name**
[GitHub](https://github.com/your-username) · [LinkedIn](https://linkedin.com/in/your-profile) · [Email](mailto:you@example.com)

---


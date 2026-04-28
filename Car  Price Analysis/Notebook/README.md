# 📓 Car Price Prediction — Exploratory Data Analysis Notebook

## Overview

This notebook presents a structured, end-to-end Exploratory Data Analysis (EDA) of the **Car Price Prediction dataset**, containing 2,500 vehicle records across 10 attributes. The analysis moves from basic data profiling through univariate and bivariate exploration, culminating in advanced multi-factor aggregations and statistical diagnostics. Each visualization is paired with data-driven insights to support downstream modelling decisions.

---

## Notebook Structure

| Section | Description |
|---|---|
| **1. Data Loading & Inspection** | Load dataset, inspect shape, columns, types, and null values |
| **2. Frequency Analysis** | Value counts for Brand, Fuel Type, Transmission, and Condition |
| **3. Grouped Aggregations** | Mean price by Brand, Fuel Type, and Transmission |
| **4. Visualizations** | 15+ charts covering distributions, relationships, and trends |
| **5. Advanced Exploration** | Pivot tables, crosstabs, multi-factor pricing, time-series trends |
| **6. Statistical Diagnostics** | Skewness, kurtosis, outlier detection via IQR method |
| **7. Utility Queries** | Filtering, sampling, and memory profiling |

---

## Analysis Walkthrough

### 🔹 1. Data Loading & Inspection
```python
df = pd.read_csv('car_price_prediction.csv')
df.shape        # (2500, 10)
df.info()
df.describe()
df.isnull().sum()
df = df.drop_duplicates()
```
Confirms a clean dataset — no nulls, no duplicates, immediately analysis-ready.

---

### 🔹 2. Frequency & Distribution Analysis

Examines how vehicles are distributed across categorical features:

| Feature | Key Finding |
|---|---|
| **Brand** | Toyota leads (374), all 7 brands nearly equal (~14–15%) |
| **Fuel Type** | Diesel most common (655), Hybrid least (601) |
| **Transmission** | Manual (1,308) slightly outnumbers Automatic (1,192) |
| **Condition** | Used (855) > Like New (836) > New (809) |

---

### 🔹 3. Grouped Price & Mileage Analysis

```python
df.groupby('Brand')['Price'].mean().sort_values(ascending=False)
df.groupby('Fuel Type')['Price'].mean()
df.groupby('Transmission')['Price'].mean()
df.groupby('Brand').agg({'Price': ['mean', 'max', 'min'], 'Mileage': 'mean', 'Engine Size': 'mean'})
```

Reveals that **brand-level price differences are minimal** (~$3,000 spread), and transmission type has negligible influence on average price.

---

### 🔹 4. Visualizations

#### 📊 Price Distribution (`histplot`)
Uniform spread across $5,000–$100,000 with no dominant price band — a balanced mix of budget, mid-range, and premium vehicles.

#### 📦 Price by Brand (`boxplot`)
BMW and Mercedes show slightly higher medians. Ford and Tesla exhibit wide spreads indicating diverse model ranges.

#### 🔵 Mileage vs Price (`scatterplot`)
Completely random cloud — no meaningful correlation between mileage and price.

#### 📊 Average Price by Fuel Type (`barplot`)
Diesel leads (~$55,000), Electric lowest (~$51,000). All four types within a narrow $4,000 band.

#### 📊 Transmission Distribution (`countplot`)
52% Manual vs 48% Automatic — near-even split across the dataset.

#### 🌡️ Correlation Matrix (`heatmap`)
All off-diagonal values near zero — full feature independence confirmed. No multicollinearity risk for modelling.

#### 🔵 Engine Size vs Price (`scatterplot`)
No pattern across engine sizes 1–6L. Smaller engines (1–3L) dominate volume.

#### 📦 Price by Condition (`boxplot`)
Median prices nearly identical across New, Used, and Like New — condition is not a strong price driver.

#### 📈 Cars by Manufacturing Year (`line plot`)
Volatile year-to-year counts. Peak at 2020 (~122 units). Sharpest drop in 2006 (~86 units).

#### 📊 Average Mileage by Brand (`barplot`)
Ford highest (~155,000 mi), Mercedes lowest (~145,000 mi). All within a 10,000-mile range.

#### 📊 Average Price by Brand (`horizontal barplot`)
BMW tops at ~$54,000, Ford lowest at ~$51,000. Tesla edges Mercedes for second place.

#### 📈 Average Price by Year (`line plot`)
Slow downward trend 2000–2024. Peak in 2004–2005, sharpest trough in 2021.

#### 📊 Model Price by Brand (`barplot`)
28 models across 7 brands, all clustered $47,000–$60,000. Ford Mustang lowest, BMW GLC highest.

#### 📊 Inventory by Brand & Transmission (`countplot with hue`)
Manual dominates every brand. Toyota is the only brand with near-equal split.

#### 🔵 Pair Plot (`pairplot`)
All variable pairs form structureless clouds — confirms no linear relationships anywhere in the dataset.

#### 🌡️ Mileage vs Price by Transmission (`FacetGrid`)
Mirror-image plots for Manual and Automatic — transmission adds zero explanatory power to the mileage-price relationship.

#### 🥧 Brand Market Share (`pie chart`)
Perfectly balanced 13.9%–15.0% spread — statistically unusual, suggests curated sampling.

#### 🔷 Density: Mileage vs Price (`hexbin`)
Even density across the full grid — no hotspot, no dominant mileage-price combination.

---

### 🔹 5. Advanced Exploration

```python
# Multi-factor pricing
df.groupby(['Brand', 'Fuel Type'])['Price'].mean()
df.groupby(['Brand', 'Condition'])['Price'].agg(['mean', 'median', 'count'])

# Pivot analysis
df.pivot_table(values='Price', index='Brand', columns='Fuel Type', aggfunc='mean')

# Crosstab
pd.crosstab(df['Transmission'], df['Fuel Type'])

# Time-series trend
df.groupby('Year')['Price'].mean()
df.groupby('Year')['Mileage'].mean().plot(kind='line', color='green')
```

---

### 🔹 6. Statistical Diagnostics

```python
from scipy.stats import skew, kurtosis

print("Skewness:", skew(df['Price']))
print("Kurtosis:", kurtosis(df['Price']))

# IQR Outlier Detection
Q1 = df['Price'].quantile(0.25)
Q3 = df['Price'].quantile(0.75)
IQR = Q3 - Q1
outliers = df[(df['Price'] < Q1 - 1.5*IQR) | (df['Price'] > Q3 + 1.5*IQR)]
```

Price distribution shows near-zero skewness and low kurtosis — approximately uniform, with minimal outlier presence.

---

### 🔹 7. Utility Tools

```python
df.sample(5)                                          # Random sample
df.query("Price > 50000 and Mileage < 50000")         # Conditional filtering
df.memory_usage(deep=True)                            # Memory profiling
```

---

## Key Findings Summary

| Finding | Detail |
|---|---|
| **No strong correlations** | All numeric features are near-independent; non-linear models recommended |
| **Brand has minimal price impact** | Only ~$3,000 spread between highest (BMW) and lowest (Ford) brand averages |
| **Condition doesn't shift median price** | New, Used, and Like New share nearly identical median values |
| **Mileage is not a price predictor** | Random scatter across all mileage ranges at all price points |
| **Dataset is well-balanced** | Uniform distribution across brands, fuel types, and conditions |
| **Pricing is uniformly distributed** | No dominant price band — equal representation from $5K to $100K |

---

## Dependencies

```python
pandas
numpy
matplotlib
seaborn
scipy
```

Install all at once:
```bash
pip install pandas numpy matplotlib seaborn scipy
```

---

## How to Run

```bash
# Clone or download the notebook
jupyter notebook car_price_eda.ipynb

# Ensure the dataset is in the same directory
# car_price_prediction.csv must be present
```

---

## File Structure

```
📁 project/
├── 📓 car_price_analysis.ipynb        # Main analysis notebook
├── 📄 car_price_prediction.csv   # Source dataset (2,500 records)
├── 📄 README.md                  # Dataset documentation
└── 📄 NOTEBOOK_README.md         # This file
```

---

## Author Notes

> This notebook is structured for clarity and reproducibility. Each visualization section is self-contained with its own insights block, making it easy to reference specific analyses independently. The advanced exploration section extends the EDA into multi-dimensional aggregations suitable for feature engineering in subsequent modelling phases.

---

*Notebook Type: EDA · Language: Python 3 · Charts: 15+ · Dataset: 2,500 records · Features Analysed: 10*

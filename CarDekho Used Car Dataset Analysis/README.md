![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/e65152d2b26f90536a2777d7efd25c5bdbe18163/CarDekho%20Used%20Car%20Dataset%20Analysis/dataset-cover.png)



# 🚗 CarDekho Used Car Dataset — Exploratory Data Analysis (EDA)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c?style=for-the-badge&logo=matplotlib&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-4c72b0?style=for-the-badge)
![Scipy](https://img.shields.io/badge/SciPy-Statistics-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-Automotive%20%7C%20India-orange?style=for-the-badge)

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [Dataset Description](#dataset-description)
3. [Feature Information](#feature-information)
4. [Libraries Used](#libraries-used)
5. [EDA Questions & Key Insights](#eda-questions--key-insights)
   - [Q1. Top 15 Most Common Car Brands](#q1-top-15-most-common-car-brands)
   - [Q2. Vehicle Age vs Selling Price](#q2-vehicle-age-vs-selling-price)
   - [Q3. KM Driven vs Selling Price](#q3-km-driven-vs-selling-price)
   - [Q4. Top 15 Brands by Average Selling Price](#q4-top-15-brands-by-average-selling-price)
   - [Q5. Distribution of Engine Capacity](#q5-distribution-of-engine-capacity)
   - [Q6. Average Engine Capacity by Brand](#q6-average-engine-capacity-by-brand)
   - [Q7. Fuel Type Distribution](#q7-fuel-type-distribution)
   - [Q8. Transmission Type Distribution](#q8-transmission-type-distribution)
   - [Q9. Seller Type Distribution](#q9-seller-type-distribution)
   - [Q10. Correlation Heatmap of Numeric Features](#q10-correlation-heatmap-of-numeric-features)
   - [Q11. Average Selling Price by Brand and Fuel Type](#q11-average-selling-price-by-brand-and-fuel-type)
   - [Q12. Engine Capacity Distribution (Detailed)](#q12-engine-capacity-distribution-detailed)
   - [Q13. Max Power Distribution](#q13-max-power-distribution)
6. [Outlier Detection](#outlier-detection)
7. [Statistical Summary](#statistical-summary)
8. [Conclusion](#conclusion)

---

## Project Overview

The used car market in India is a dynamic and ever-evolving landscape where prices fluctuate based on a wide range of factors — brand, mileage, age, fuel type, engine capacity, and current market conditions. This project performs a comprehensive **Exploratory Data Analysis (EDA)** on the **CarDekho Used Car Dataset** to uncover pricing patterns, market trends, and feature relationships that can serve as the foundation for a **machine learning price prediction model**.

---

## Dataset Description

| Property | Details |
|---|---|
| Source | CarDekho Used Car Dataset |
| Domain | Automotive / Used Car Market (India) |
| Primary Use Case | Used Car Price Prediction |
| Format | CSV |
| Total Features | 12 |

---

## Feature Information

| Feature | Description |
|---|---|
| `car_name` | Full name of the car including brand and model |
| `brand` | Brand name of the car |
| `model` | Exact model name of the car |
| `seller_type` | Type of seller (Individual / Dealer / Trustmark Dealer) |
| `fuel_type` | Fuel used in the car (Petrol / Diesel / CNG / LPG / Electric) |
| `transmission_type` | Transmission type (Manual / Automatic) |
| `vehicle_age` | Number of years since the car was purchased |
| `mileage` | Fuel efficiency in km per litre |
| `engine` | Engine capacity in CC (cubic centimeters) |
| `max_power` | Maximum power output in BHP |
| `seats` | Total number of seats in the car |
| `selling_price` | Listed sale price on the platform (target variable) |

---

## Libraries Used

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
from scipy.stats import zscore, skew, kurtosis
```

---

## EDA Questions & Key Insights

### Q1. Top 15 Most Common Car Brands

```python
brand_counts = df['brand'].value_counts().head(15)
plt.figure(figsize=(12,5))
sns.barplot(x=brand_counts.index, y=brand_counts.values, color='teal')
plt.xticks(rotation=45)
plt.title('Top 15 Car Brands by Count')
plt.ylabel('Number of Cars')
plt.xlabel('Brand')
plt.show()
```

**Insights:**
- Maruti dominates the Indian car market with ~5,000 units — nearly 67% more than second-place Hyundai (~3,000), reinforcing its position as the undisputed mass-market leader.
- Hyundai and Honda form a distant but strong second tier, suggesting a competitive mid-range segment where Korean and Japanese brands hold significant consumer trust.
- A sharp drop-off occurs after Honda (~1,500), with Mahindra, Toyota, and Ford clustering around 800–1,050 units, indicating a fragmented mid-market with no clear challenger to the top three.
- European luxury brands (BMW, Mercedes-Benz, Skoda, Audi, Volkswagen) collectively appear in the lower half, reflecting their niche premium positioning in a price-sensitive, value-driven market.
- Datsun and Jaguar's minimal presence signals either weak brand traction or limited model offerings, highlighting the difficulty of sustaining market share at both the budget and ultra-luxury ends of the spectrum.

---

### Q2. Vehicle Age vs Selling Price

```python
plt.figure()
sns.scatterplot(x='vehicle_age', y='selling_price', data=df, color='darkorange')
plt.title('Vehicle Age vs Selling Price')
plt.xlabel('Vehicle Age')
plt.ylabel('Selling Price')
plt.show()
```

**Insights:**
- A strong negative correlation exists between vehicle age and selling price, confirming the expected depreciation trend — newer vehicles (0–5 years) command significantly higher prices than older ones.
- The most extreme price outliers (~₹40M and ~₹25M) appear in the 1–4 year age range, likely representing luxury or high-end vehicles that retain premium valuations even as used cars.
- The highest price density and widest spread occur between 0–10 years, suggesting this is the most active and competitive segment of the used car market.
- Beyond 10 years, selling prices compress sharply and cluster near zero, indicating rapid value erosion and limited buyer willingness to pay a premium for aging vehicles.
- A few outliers exist at 25–29 years with near-zero prices, likely representing vintage or end-of-life vehicles with negligible resale value, pulling the tail of the distribution further right.

---

### Q3. KM Driven vs Selling Price

```python
plt.figure()
sns.scatterplot(x='km_driven', y='selling_price', data=df, color='green')
plt.title('KM Driven vs Selling Price')
plt.xlabel('Kilometers Driven')
plt.ylabel('Selling Price')
plt.show()
```

**Insights:**
- A clear inverse relationship exists between kilometers driven and selling price — vehicles with lower mileage consistently fetch higher prices, validating mileage as a key depreciation driver in used car valuation.
- The highest-priced vehicles (₹25M–₹40M) are concentrated below 50,000 KM, suggesting that low-mileage luxury cars retain their premium value far better than high-usage counterparts.
- The majority of data points are densely clustered near 0–200,000 KM, indicating that most used car transactions involve relatively low-to-moderate mileage vehicles, reflecting a younger, well-maintained inventory.
- Beyond 500,000 KM, selling prices flatten near zero with very few transactions, implying that high-mileage vehicles have minimal resale appeal and represent the weakest segment of the market.
- A notable outlier at ~3.8M KM with a non-zero price likely represents a data anomaly or a specialized commercial vehicle, warranting further investigation before inclusion in predictive modeling.

---

### Q4. Top 15 Brands by Average Selling Price

```python
avg_price_by_brand = df.groupby('brand')['selling_price'].mean().sort_values(ascending=False).head(15)
plt.figure(figsize=(12,6))
sns.barplot(x=avg_price_by_brand.index, y=avg_price_by_brand.values, color='skyblue')
plt.xticks(rotation=45)
plt.title('Top 15 Brands by Average Selling Price')
plt.ylabel('Average Selling Price')
plt.xlabel('Brand')
plt.show()
```

**Insights:**
- Ferrari leads by a massive margin at ~₹40M average selling price, nearly 60% higher than second-place Rolls-Royce (~₹24M), cementing its status as the most aspirational and highest-valued brand in the used luxury car market.
- A steep three-tier hierarchy is visible — ultra-luxury (Ferrari, Rolls-Royce), premium luxury (Bentley, Maserati, Porsche, Lexus), and accessible luxury (BMW, Jaguar, Mercedes-Benz, Audi) — reflecting distinct consumer segments with sharply different price tolerances.
- Bentley at ~₹9.5M sits significantly below Rolls-Royce despite being in the same ultra-luxury space, suggesting either higher depreciation rates or a broader model range skewing its average downward.
- Mercedes-AMG and Land Rover cluster closely around ₹4M–₹5M, indicating strong but competitive resale positioning within the performance and SUV luxury segments respectively.
- The surprise inclusion of ISUZU in the top 15 — typically a commercial vehicle brand — hints at a niche high-value model or limited dataset entries inflating its average, flagging it as a potential outlier for data quality review.

---

### Q5. Distribution of Engine Capacity

```python
plt.figure(figsize=(8,5))
sns.histplot(df['engine'], bins=30, kde=True, color='coral')
plt.title('Distribution of Engine Capacity (CC)')
plt.xlabel('Engine Capacity (cc)')
plt.ylabel('Count')
plt.show()
```

**Insights:**
- The distribution is heavily right-skewed with a dominant peak at ~1,200 CC (~5,400 units), confirming that small-engine, fuel-efficient vehicles make up the overwhelming majority of the used car market — consistent with India's price and mileage-sensitive consumer base.
- A secondary cluster is visible between 1,500–2,500 CC, representing mid-range sedans, SUVs, and diesel vehicles, forming a distinct but much smaller second tier of market preference.
- The sharp drop-off after 1,200 CC and again after 2,500 CC suggests two natural market breakpoints — one separating economy from mid-range, and another separating mid-range from premium engine segments.
- Engine capacities above 3,000 CC are extremely rare in this dataset, reflecting the high ownership cost, taxation, and limited demand for large-displacement vehicles in the Indian used car ecosystem.
- The multimodal nature of the distribution (multiple small peaks at 1,000, 1,500, 2,000, and 2,500 CC) indicates standardized engine sizing across manufacturers, with consumers gravitating toward specific, well-known engine configurations rather than a continuous spread.

---

### Q6. Average Engine Capacity by Brand

```python
engine_by_brand = df.groupby('brand')['engine'].mean().sort_values(ascending=False)
plt.figure(figsize=(12,8))
colors = sns.color_palette("Spectral", len(engine_by_brand))
plt.barh(engine_by_brand.index, engine_by_brand.values, color=colors)
plt.title('Average Engine Capacity by Brand', fontsize=16, fontweight='bold')
plt.xlabel('Average Engine Capacity (cc)')
plt.ylabel('Brand')
plt.gca().invert_yaxis()
plt.tight_layout()
plt.show()
```

**Insights:**
- Rolls-Royce (~6,500 CC) and Bentley (~6,000 CC) lead by a significant margin, reflecting their signature large-displacement, high-torque engines that are central to their ultra-luxury brand identity and driving experience.
- A clear engine-size hierarchy mirrors the pricing hierarchy — ultra-luxury brands (Rolls-Royce, Bentley, Ferrari) average 4,000–6,500 CC, while mass-market brands (Maruti, Renault, Datsun) average just 1,000–1,200 CC, confirming engine capacity as a strong proxy for brand positioning.
- The 2,500–3,200 CC mid-zone is occupied by performance and near-luxury brands like Porsche, Mercedes-AMG, ISUZU, and Maserati, forming a distinct performance-oriented cluster between mass-market and ultra-luxury segments.
- Indian domestic brands — Maruti, Tata, Mahindra, and Renault — all fall below 2,200 CC on average, consistent with their focus on affordable, fuel-efficient vehicles tailored to cost-conscious Indian consumers.
- Datsun records the lowest average engine capacity (~1,050 CC), reinforcing its positioning as an entry-level budget brand with minimal powertrain ambition, sitting at the opposite end of the spectrum from Rolls-Royce.

---

### Q7. Fuel Type Distribution

```python
plt.figure(figsize=(8,5))
sns.countplot(x='fuel_type', data=df, hue='fuel_type', palette='Set2', legend=False)
plt.title('Fuel Type Distribution')
plt.xlabel('Fuel Type')
plt.ylabel('Count')
plt.show()
```

**Insights:**
- Petrol (~7,700) and Diesel (~7,500) dominate the used car market almost equally, together accounting for over 95% of all listings — reflecting the long-standing duopoly of internal combustion engines in India's automotive landscape.
- The near-parity between Petrol and Diesel suggests a balanced consumer preference, with Petrol marginally ahead, possibly due to recent diesel taxation policies and urban restrictions discouraging diesel vehicle ownership.
- CNG vehicles (~350) represent a distant third, indicating a slowly growing but still niche alternative fuel segment — primarily driven by urban commuters seeking lower running costs amid rising petrol and diesel prices.
- LPG and Electric vehicles are nearly invisible in the dataset, collectively accounting for less than 1% of listings, highlighting the nascent stage of alternative fuel adoption in India's used car ecosystem.
- The near-zero Electric vehicle presence is particularly telling — despite growing new EV sales, the used EV market remains virtually non-existent, suggesting either low resale activity, consumer hesitation around used battery health, or limited early EV ownership to begin with.

---

### Q8. Transmission Type Distribution

```python
plt.figure(figsize=(8,5))
sns.countplot(x='transmission_type', data=df, hue='transmission_type', palette='coolwarm', legend=False)
plt.title('Transmission Type Distribution')
plt.xlabel('Transmission Type')
plt.ylabel('Count')
plt.show()
```

**Insights:**
- Manual transmission overwhelmingly dominates the used car market at ~12,200 units versus ~3,200 Automatic, a roughly 80:20 split — reflecting India's deeply entrenched preference for manual gearboxes driven by lower purchase cost and cheaper maintenance.
- The 4:1 ratio between Manual and Automatic listings suggests that automatic vehicles, while growing in new car sales, have yet to make a significant dent in the used car supply chain, likely due to their relatively recent mass-market adoption in India.
- The limited Automatic inventory (~3,200 units) could create a supply-demand imbalance, potentially driving higher resale prices for automatic vehicles as urban buyer preference gradually shifts toward convenience-oriented driving.
- The dominance of manual transmissions aligns strongly with the earlier finding of small-engine, budget-friendly vehicles (Maruti, Hyundai, Honda) leading the market — segments where manual gearboxes remain the default offering.
- As India's urban infrastructure grows and traffic congestion worsens, the Automatic segment is expected to grow significantly in future datasets, making current automatic listings a potentially undervalued and high-demand asset class in used car trading.

---

### Q9. Seller Type Distribution

```python
plt.figure(figsize=(8,5))
sns.countplot(x='seller_type', data=df, hue='seller_type', palette='viridis', legend=False)
plt.title('Seller Type Distribution')
plt.xlabel('Seller Type')
plt.ylabel('Count')
plt.show()
```

**Insights:**
- Dealers dominate the used car market at ~9,500 listings (~62%), nearly double the Individual sellers (~5,700 at ~37%), indicating a highly organized and commercially driven resale ecosystem rather than a peer-to-peer marketplace.
- The strong dealer presence suggests increasing professionalization of India's used car industry, with organized players like CarDekho, Cars24, and OLX Autos likely contributing significantly to the dealer-listed inventory.
- Individual sellers at ~37% still represent a substantial share, indicating that private peer-to-peer transactions remain a significant and trusted channel — often preferred by buyers seeking negotiation flexibility and direct ownership history.
- Trustmark Dealers account for a negligible ~150 listings (<1%), suggesting that certified or quality-assured dealer programs are still in their infancy in India's used car market, representing a significant untapped growth opportunity.
- The near-absence of Trustmark Dealers points to a trust gap in the market — as consumer awareness around vehicle quality certification grows, this segment could expand rapidly, potentially reshaping buyer confidence and pricing premiums in the organized used car space.

---

### Q10. Correlation Heatmap of Numeric Features

```python
plt.figure(figsize=(12,8))
sns.heatmap(
    df.corr(numeric_only=True),
    annot=True, fmt=".2f", cmap="coolwarm",
    cbar=True, linewidths=0.5
)
plt.title("Correlation Heatmap of Numeric Features", fontsize=16, fontweight='bold')
plt.show()
```

**Insights:**
- Max power (0.75) and engine capacity (0.59) are the strongest positive predictors of selling price, confirming that performance-oriented specifications drive premium valuations far more than age or mileage in the used car market.
- Mileage shows a strong negative correlation with both engine size (-0.63) and max power (-0.53), revealing a fundamental trade-off — high-performance, large-engine vehicles are inherently less fuel-efficient, creating two distinct buyer segments: economy-focused vs performance-focused.
- Vehicle age (-0.24) and km driven (-0.08) have surprisingly weak correlations with selling price, suggesting that engine power and capacity are far more dominant pricing factors than depreciation-based metrics — a critical insight for building accurate price prediction models.
- The strong engine-to-max_power correlation (0.81) indicates near-multicollinearity between these two features, meaning only one may be needed in a regression model to avoid redundancy and overfitting.
- Mileage's negative correlation with selling price (-0.31) and seats (-0.44) suggests that fuel-efficient, smaller-engine vehicles tend to have fewer seats, reinforcing the pattern that compact economy cars dominate the low-price, high-mileage segment of the market.

---

### Q11. Average Selling Price by Brand and Fuel Type

```python
pivot = df.pivot_table(index='brand', columns='fuel_type', values='selling_price', aggfunc='mean')
plt.figure(figsize=(12,8))
sns.heatmap(pivot, annot=True, fmt=".0f", cmap="YlGnBu", linewidths=0.5)
plt.title("Average Selling Price by Brand and Fuel Type", fontsize=16, fontweight='bold')
plt.xlabel("Fuel Type")
plt.ylabel("Brand")
plt.show()
```

**Insights:**
- Ferrari Petrol (~₹39.5M) and Rolls-Royce Petrol (~₹24.2M) stand out as extreme high-value outliers — both exclusively petrol-powered, reinforcing that ultra-luxury brands have zero dependency on alternative fuels and command unmatched resale premiums.
- Maserati Diesel (~₹6.1M) and Porsche Diesel (~₹4.78M) are the highest diesel-priced entries, indicating that luxury diesel variants retain strong value due to their performance-tuned engines appealing to a niche but affluent buyer segment.
- Mass-market brands like Maruti, Hyundai, and Honda show multi-fuel presence (CNG, Diesel, Petrol, LPG), with prices tightly clustered between ₹188K–₹694K — reflecting their broad, affordable product range designed to cater to every fuel preference and budget.
- Toyota is the only brand with a notable Electric average (~₹1.85M), highlighting its early mover advantage in the hybrid/electric space, while the near-complete absence of Electric entries across other brands confirms the used EV market remains largely undeveloped.
- LPG presence is limited to only Hyundai (~₹247K) and Maruti (~₹188K), both at very low price points — suggesting LPG is a budget-driven aftermarket modification rather than a factory-fitted feature, and is losing relevance as CNG infrastructure expands across Indian cities.

---

### Q12. Engine Capacity Distribution (Detailed)

```python
plt.figure()
sns.histplot(df['engine'], kde=True, color='teal')
plt.title('Engine Capacity Distribution')
plt.xlabel('Engine Capacity')
plt.ylabel('Frequency')
plt.show()
```

**Insights:**
- The distribution is sharply right-skewed with a dominant spike at ~1,200 CC (~3,600 frequency), confirming that small-displacement engines are by far the most common in the used car market.
- Multiple distinct spikes are visible at standardized engine sizes (998, 1197, 1248, 1498, 1968, 2494 CC), revealing that manufacturers deliberately cluster around specific displacement milestones to optimize tax brackets and emission norms.
- A secondary cluster of spikes between 1,500–2,500 CC represents the mid-range diesel and SUV segment, with notably lower frequencies (~200–550).
- Engine capacities beyond 3,000 CC are extremely sparse, isolating large-displacement vehicles as a rare luxury segment with negligible volume contribution to the overall used car pool.
- The highly granular, spiky nature of the distribution underscores that engine capacity is a discrete, manufacturer-defined specification — an important consideration when engineering features for machine learning price prediction models.

---

### Q13. Max Power Distribution

```python
plt.figure()
sns.histplot(df['max_power'], kde=True, color='crimson')
plt.title('Max Power Distribution')
plt.xlabel('Max Power')
plt.ylabel('Frequency')
plt.show()
```

**Insights:**
- The distribution is heavily right-skewed with a dominant cluster between 60–100 bhp (~1,800 peak frequency), confirming that low-to-moderate power output vehicles make up the vast majority of used car listings.
- Multiple sharp spikes between 60–150 bhp mirror the engine capacity distribution's spiky pattern, reinforcing that max power is a manufacturer-defined discrete specification tightly coupled to specific engine configurations.
- A secondary, flatter cluster between 150–250 bhp represents performance-oriented mid-range vehicles (SUVs, diesel sedans, entry-level luxury cars), forming a distinct but low-volume power segment.
- Power outputs beyond 300 bhp are extremely rare, isolating high-performance luxury and sports cars (Ferrari, Rolls-Royce, Porsche) as a negligible volume but high-value niche within the dataset.
- The strong alignment between this distribution and the engine capacity distribution further validates max power and engine CC as highly correlated features (r = 0.81), reinforcing the case for using only one in a lean predictive pricing model.

---

## Outlier Detection

```python
from scipy.stats import zscore

# Z-score Method
df['price_z'] = zscore(df['selling_price'])
outliers_z = df[df['price_z'].abs() > 3]
print("Z-score outliers in selling price:")
print(outliers_z[['car_name', 'selling_price']])

# IQR Method
Q1 = df['selling_price'].quantile(0.25)
Q3 = df['selling_price'].quantile(0.75)
IQR = Q3 - Q1
outliers_iqr = df[(df['selling_price'] < Q1 - 1.5 * IQR) | (df['selling_price'] > Q3 + 1.5 * IQR)]
print("IQR outliers in selling price:")
print(outliers_iqr[['car_name', 'selling_price']])
```

Both the Z-score (threshold > 3) and IQR methods were applied to identify extreme outliers in `selling_price`. Ultra-luxury brands like Ferrari and Rolls-Royce consistently appear as high-end outliers. These should be treated carefully during model training — either capped, log-transformed, or segmented — to prevent them from skewing regression models.

---

## Statistical Summary

```python
from scipy.stats import skew, kurtosis

print("Skewness of Selling Price:", skew(df['selling_price']))
print("Kurtosis of Selling Price:", kurtosis(df['selling_price']))
```

| Metric | Interpretation |
|---|---|
| High Positive Skewness | Selling price is right-skewed; majority of cars are low-priced with a few extreme high-value outliers |
| High Kurtosis | Heavy-tailed distribution; outliers (luxury cars) have a disproportionate statistical influence |
| Recommended Transformation | Log transformation of `selling_price` is advised before model training |

---

## Conclusion

This EDA reveals that India's used car market is dominated by affordable, small-engine, manual, petrol/diesel vehicles from mass-market brands like Maruti and Hyundai. Key pricing drivers are `max_power` and `engine` capacity rather than `vehicle_age` or `km_driven`. The market is increasingly professionalized through dealer channels, while alternative fuels and automatic transmissions remain underrepresented but growing segments. These insights directly inform feature selection and preprocessing strategies for building a robust used car price prediction model.

---

> **Author:** Data Analysis Project
> **Dataset:** CarDekho Used Car Dataset
> **Tools:** Python, Pandas, Matplotlib, Seaborn, Scipy

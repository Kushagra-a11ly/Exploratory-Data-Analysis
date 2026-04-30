![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/72ee38864f722dc5d5f802200d1fb60618f3e8f6/EV%20Market%20Analytics%20Dataset/dataset-cover.png)
 
# ⚡ EV Market Analytics — Exploratory Data Analysis

> A full end-to-end EDA on 2,000 real-world electric vehicle records spanning 20 global manufacturers, 6 body types, and 4 market segments — uncovering pricing dynamics, performance relationships, brand positioning, range behaviour, and sales trends across the 2020–2026 EV era.

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Schema Reference](#schema-reference)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [Analysis Walkthrough](#analysis-walkthrough)
- [Key Findings](#key-findings)
- [Visualisations & Insights](#visualisations--insights)
- [Advanced Analysis](#advanced-analysis)

---

## Project Overview

This project performs a comprehensive **Exploratory Data Analysis** on the EV Market Analytics Dataset — a globally sourced collection of 2,000 electric vehicle records covering pricing, specifications, performance, sales, and customer data from 2020 to 2026.

The analysis answers 10 real business questions using a structured progression from basic data profiling through to multivariate analysis, grouped aggregations, pivot tables, and engineered features.

| Domain | Questions Answered |
|---|---|
| **Pricing** | What does the EV pricing landscape look like? Which brands are premium vs budget? |
| **Performance** | Does battery size determine range? Do faster cars cost more? |
| **Market Position** | Which brands dominate? Which segments offer best value? |
| **Trends** | Is EV adoption increasing over time? |
| **Relationships** | What features influence each other? How do multiple specs interact? |

---

## Dataset

| Property | Value |
|---|---|
| **File** | `EV Market Analytics Dataset.csv` |
| **Records** | 2,000 EV models / variants |
| **Time Period** | 2020 – 2026 |
| **Coverage** | Global — 20 major EV manufacturers |
| **Domain** | Automotive / EV Market Intelligence |
| **Primary Task** | EDA / Price Prediction / Market Analysis |
| **Missing Values** | Checked via `df.isnull().sum()` |
| **Duplicates** | Verified clean |

---

## Schema Reference

### 🪪 Identity & Classification

| Column | Description |
|---|---|
| `brand` | Manufacturer name (20 brands including Tesla, BYD, BMW, Lucid, Rivian) |
| `model` | Specific vehicle model — 28 unique models |
| `year` | Manufacturing / listing year (2020–2026) |
| `body_type` | Truck, SUV, Van, Hatchback, Coupe, Sedan |
| `market_segment` | Budget, Mid-range, Premium, Luxury |

### 💰 Pricing

| Column | Description |
|---|---|
| `price_usd` | Market price in USD |
| `price_per_mile` | Engineered feature — price divided by range (value efficiency metric) |

### 🔋 Battery & Range

| Column | Description |
|---|---|
| `battery_capacity_kwh` | Battery size in kilowatt-hours (40–120 kWh) |
| `range_miles` | EPA-rated range in miles (150–450 miles) |
| `charging_speed_kw` | Maximum charging speed in kilowatts |
| `range_efficiency` | Engineered feature — range miles per kWh |

### ⚡ Performance

| Column | Description |
|---|---|
| `acceleration_0_60_mph` | 0–60 mph time in seconds (lower = faster) |
| `top_speed_mph` | Maximum speed in mph |
| `horsepower` | Engine output in horsepower |
| `torque_nm` | Torque output in Newton-metres |

### 🧍 Practicality

| Column | Description |
|---|---|
| `seating_capacity` | Number of passenger seats |
| `cargo_volume_cubic_ft` | Boot / cargo space in cubic feet |
| `weight_kg` | Vehicle weight in kilograms |

### 📊 Market & Customer

| Column | Description |
|---|---|
| `annual_sales_units` | Units sold per year |
| `customer_rating` | Customer satisfaction score |
| `safety_rating` | Official safety rating |
| `autopilot_level` | Autonomous driving level (0–5) |
| `warranty_years` | Manufacturer warranty in years |

---

## Tech Stack

| Tool | Purpose |
|---|---|
| **Python 3.x** | Core language |
| **Pandas** | Data loading, cleaning, grouping, pivoting |
| **NumPy** | Numerical operations and feature engineering |
| **Matplotlib** | Base plotting layer |
| **Seaborn** | Statistical visualisation (histplot, boxplot, scatterplot, heatmap, pairplot, countplot) |
| **Jupyter Notebook** | Interactive analysis environment |

---

## Project Structure

```
ev-market-eda/
│
├── data/
│   └── EV Market Analytics Dataset.csv
│
├── notebooks/
│   └── ev_market_eda.ipynb          # Full analysis notebook
│
├── outputs/
│   └── figures/                     # All 10 exported visualisations
│       ├── 01_price_distribution.png
│       ├── 02_brand_count.png
│       ├── 03_battery_vs_range.png
│       ├── 04_acceleration_vs_price.png
│       ├── 05_correlation_matrix.png
│       ├── 06_price_by_brand.png
│       ├── 07_range_by_body_type.png
│       ├── 08_sales_trend.png
│       ├── 09_pair_plot.png
│       └── 10_value_for_money.png
│
└── README.md
```

---

## Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ev-market-eda.git
cd ev-market-eda
```

### 2. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Launch the Notebook

```bash
jupyter notebook notebooks/ev_market_eda.ipynb
```

---

## Analysis Walkthrough

### Phase 1 — Data Profiling

```python
df = pd.read_csv('EV Market Analytics Dataset.csv')

df.shape          # (2000, n_columns)
df.info()         # dtypes and non-null counts
df.describe()     # statistical summary
df.isnull().sum() # missing value check
df.dtypes         # column type verification
```

### Phase 2 — Categorical Exploration

```python
df['brand'].value_counts()     # brand frequency
df['body_type'].unique()       # distinct body types
df['model'].nunique()          # count of unique models
```

### Phase 3 — Correlation & Grouping

```python
df.corr(numeric_only=True)                              # full correlation matrix
df.groupby('brand')['price_usd'].mean()                 # avg price by brand
df.groupby('body_type')['range_miles'].mean()           # avg range by body type
df.groupby('market_segment')['annual_sales_units'].mean() # avg sales by segment
```

### Phase 4 — Visualisation (10 Charts)

All 10 charts are produced using Seaborn and Matplotlib — see [Visualisations & Insights](#visualisations--insights) below.

### Phase 5 — Advanced Aggregation & Feature Engineering

```python
# Multi-column groupby
df.groupby(['brand', 'body_type']).agg({
    'price_usd': 'mean',
    'range_miles': 'max',
    'customer_rating': 'mean'
})

# Pivot table
df.pivot_table(values='price_usd', index='brand', columns='body_type', aggfunc='mean')

# Crosstab with normalisation
pd.crosstab(df['body_type'], df['market_segment'], normalize='index')

# Feature engineering
df['price_per_mile'] = df['price_usd'] / df['range_miles']
df.eval('range_efficiency = range_miles / battery_capacity_kwh')

# Query and filter
df.query('price_usd > 50000')
df.sort_values('price_usd')
```

---

## Key Findings

| # | Finding | Implication |
|---|---|---|
| 1 | Battery capacity and range correlate at **0.98** | They are functionally the same variable — use only one in modelling |
| 2 | Horsepower and torque correlate at **0.99** | Perfect multicollinearity — drop one before modelling |
| 3 | Price peaks at **$65K–$75K** with a right-skewed tail | Market is mass-market driven; ultra-premium is a niche |
| 4 | **Charging speed** shows near-zero correlation with everything | Spec decisions are made independently of vehicle performance |
| 5 | **Body type** has no meaningful impact on median range | Range is determined by battery, not vehicle shape |
| 6 | **Tesla** has 55% more listings than second-placed BYD | Market dominance is real but inventory-concentrated |
| 7 | **Budget EVs** deliver the lowest price-per-mile by a wide margin | Value proposition is clear and consistent in this segment |
| 8 | **Lucid and Porsche** operate in an isolated ultra-luxury tier | Pricing behaviour is entirely different from rest of market |
| 9 | EV sales grew ~17x from 2020 to 2025 | Adoption curve was steep; 2026 drop warrants data-quality scrutiny |
| 10 | Range distribution shows a **bimodal hint** | Two buyer clusters may exist: urban short-range and long-distance |

---

## Visualisations & Insights

### 1. Distribution of EV Prices
**Question:** What is the overall pricing landscape of EVs?

```python
sns.histplot(df['price_usd'], kde=True, bins=30)
```

| # | Insight |
|---|---|
| 1 | **Right-Skewed Distribution** — majority of EVs concentrated in $40K–$90K with a long tail beyond $200K |
| 2 | **Market Sweet Spot at ~$65K–$75K** — the most competitive and densely populated price band |
| 3 | **Mass-Market Dominance Below $100K** — over 75% of listings fall under $100K |
| 4 | **Thin Premium Segment Beyond $150K** — frequency drops sharply, ultra-premium is a niche |
| 5 | **Entry-Level Scarcity Under $30K** — truly budget EVs remain underrepresented; an affordability gap exists |

---

### 2. Number of Vehicles by Brand
**Question:** Which brands dominate the dataset?

```python
sns.countplot(y='brand', data=df, order=df['brand'].value_counts().index, palette='viridis')
```

| # | Insight |
|---|---|
| 1 | **Tesla's Commanding Lead** — ~430 vehicles, nearly 55% more than second-placed BYD (~280) |
| 2 | **BYD & Volkswagen Anchor the Second Tier** — ~280 and ~200 units respectively |
| 3 | **Tight Mid-Pack Competition** — Kia, Hyundai, BMW, GM/Chevrolet, Ford all within 130–165 range |
| 4 | **Sharp Drop-Off After Top 10** — Mercedes, Toyota, Rivian, Fisker, NIO all below 40 units |
| 5 | **Niche Brands Hold Minimal Share** — Porsche, Volvo, Polestar, Xiaomi, Lucid, Honda each under 20 |

---

### 3. Battery Capacity vs Range
**Question:** Does battery size determine range?

```python
sns.scatterplot(x='battery_capacity_kwh', y='range_miles', hue='market_segment', palette='Set2')
```

| # | Insight |
|---|---|
| 1 | **Strong Positive Correlation** — near-linear relationship across all segments confirms battery as primary range driver |
| 2 | **All Four Segments Span the Full Spectrum** — segment pricing is driven by factors beyond battery size alone |
| 3 | **50–60 Mile Vertical Spread at Every Capacity** — aerodynamics, weight, and drivetrain efficiency matter significantly |
| 4 | **Premium Shows Widest Range Variance** — performance and features are prioritised over range consistency |
| 5 | **Budget EVs Punch Above Their Battery Weight** — strong efficiency optimisation in lower-tier engineering |

---

### 4. Acceleration vs Price
**Question:** Do faster cars cost more?

```python
sns.scatterplot(x='acceleration_0_60_mph', y='price_usd', hue='body_type', palette='coolwarm')
```

| # | Insight |
|---|---|
| 1 | **Faster doesn't always mean pricier** — high-priced vehicles appear at almost every acceleration level |
| 2 | **3–5 second range holds the biggest outliers** — $150K–$260K vehicles concentrated here (Trucks & Sedans) |
| 3 | **Most of the market sits comfortably under $100K** — across all body types and acceleration bands |
| 4 | **Slower EVs haven't given up on price** — SUVs and Vans push $150K+ even at 7–8 second 0–60 times |
| 5 | **Body type blends together at every speed** — style and performance are independent buyer decisions |

---

### 5. Correlation Matrix
**Question:** What features influence each other?

```python
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='Spectral', fmt=".2f")
```

| # | Insight |
|---|---|
| 1 | **Battery and range (0.98)** — functionally identical; using both in a model is redundant |
| 2 | **Horsepower and torque (0.99)** — perfect correlation; one must be dropped before modelling |
| 3 | **Acceleration vs top speed (-0.97)** — lower 0–60 time = higher top speed; pure physics |
| 4 | **Price driven by performance cluster** — strongest correlations are horsepower, torque, and range (all 0.76) |
| 5 | **Most features are independent** — safety rating, seating, weight, and warranty near zero across the board |

---

### 6. Price Distribution by Brand
**Question:** Which brands are premium vs budget?

```python
sns.boxplot(x='price_usd', y='brand', data=df, palette='pastel')
```

| # | Insight |
|---|---|
| 1 | **Lucid and Porsche in a league of their own** — medians above $150K, whiskers past $250K |
| 2 | **Mercedes stretches furthest outside the ultra-luxury two** — box spans $100K–$175K with wide variance |
| 3 | **Toyota, Hyundai, Kia, and BYD fight the same battle** — tight boxes in the $30K–$80K band |
| 4 | **Tesla's box is deceptively wide** — Model 3 to Model S lives in the same dataset |
| 5 | **Honda is barely in the EV conversation** — narrowest, leftmost box; still finding its EV footing |

---

### 7. Range by Body Type
**Question:** Which vehicle types offer better range?

```python
sns.boxplot(x='body_type', y='range_miles', data=df, palette='muted')
```

| # | Insight |
|---|---|
| 1 | **Body type barely moves the needle** — every median sits at ~255–270 miles |
| 2 | **Coupe edges out the rest, but only just** — lighter and more aerodynamic, but the gap isn't significant |
| 3 | **The spread is more interesting than the middle** — all types span 150–450 miles identically |
| 4 | **Vans are more competitive than their reputation** — matches SUVs and Sedans on median range |
| 5 | **Trucks have the widest IQR** — most unpredictable range of any body type |

---

### 8. EV Sales Trend Over Time
**Question:** Is EV adoption increasing?

```python
sales_trend = df.groupby('year')['annual_sales_units'].sum()
plt.plot(sales_trend.index, sales_trend.values, marker='o', color='teal')
```

| # | Insight |
|---|---|
| 1 | **Six years of growth nearly wiped out in one** — 2025 peak of ~88M reversed sharply in 2026 |
| 2 | **2020–2025 growth curve is extraordinary** — units roughly doubled every 18 months |
| 3 | **2025 was the peak — ceiling or cliff is the question** — policy changes, saturation, or data cutoff could all explain it |
| 4 | **2026 figure warrants caution** — a drop of this magnitude is more likely a reporting gap than a real collapse |
| 5 | **Underlying trajectory still points upward** — 2026 levels are still 3x what they were in 2022 |

---

### 9. Pair Plot — Price, Range, Battery & Charging Speed
**Question:** How do multiple features interact together?

```python
sns.pairplot(df[['price_usd','range_miles','battery_capacity_kwh','charging_speed_kw']], corner=True)
```

| # | Insight |
|---|---|
| 1 | **Battery and range form a near-perfect diagonal** — the cleanest relationship in the entire dataset |
| 2 | **Price is right-skewed** — long tail of expensive outliers makes price the hardest variable to predict |
| 3 | **Charging speed shows no pattern with anything** — infrastructure decisions are made independently of vehicle specs |
| 4 | **Range distribution hints at bimodality** — possible two buyer clusters: urban commuters and long-distance drivers |
| 5 | **No dominant battery pack size** — manufacturers haven't converged on a standard; the market is still deciding what "enough" means |

---

### 10. Value for Money by Segment
**Question:** Which segment offers the best value?

```python
df['price_per_mile'] = df['price_usd'] / df['range_miles']
sns.boxplot(x='market_segment', y='price_per_mile', data=df, color='lightcoral')
```

| # | Insight |
|---|---|
| 1 | **Budget EVs win on value — and it's not close** — median ~$150/mile with the tightest box of any segment |
| 2 | **Luxury buyers pay 3x per mile compared to Budget** — the premium is for brand and interior, not range |
| 3 | **Luxury's outlier cloud above $900/mile** — at that point buyers are purchasing exclusivity, not utility |
| 4 | **Mid-range is where value and quality meet** — ~$210/mile with consistent, predictable pricing |
| 5 | **Premium is under the most pressure to justify itself** — pays more than Mid-range without Luxury's brand cachet |

---

## Advanced Analysis

### Multi-Column GroupBy

```python
df.groupby(['brand', 'body_type']).agg({
    'price_usd': 'mean',
    'range_miles': 'max',
    'customer_rating': 'mean'
})
```

### Segment Pricing Summary

```python
df.groupby('market_segment')['price_usd'].agg(['mean', 'sum'])
```

### Brand × Body Type Pivot Table

```python
df.pivot_table(values='price_usd', index='brand', columns='body_type', aggfunc='mean')
```

### Crosstab — Body Type vs Segment

```python
pd.crosstab(df['body_type'], df['market_segment'])
pd.crosstab(df['body_type'], df['market_segment'], normalize='index')  # with percentages
```

### Feature Engineering

```python
df['price_per_mile']    = df['price_usd'] / df['range_miles']
df['range_efficiency']  = df.eval('range_miles / battery_capacity_kwh')
```

### Utility Queries

```python
df.query('price_usd > 50000')   # filter premium vehicles
df.sort_values('price_usd')     # rank by price
df.memory_usage()               # check DataFrame footprint
df.sample(5)                    # random sample check
```

---

## License

This project is released under the [MIT License](LICENSE).

---

## Author

**Your Name**
Kushagra Mukund Dhamani

---

> *"The most interesting story in this dataset isn't what correlates — it's what doesn't. Charging speed, body type, and condition barely move the price needle. The EV market prices performance packages, not individual specs."*

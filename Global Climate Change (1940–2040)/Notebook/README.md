![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/c5d794cb1d582ec3beed144f0ced0448d3671d04/Global%20Climate%20Change%20(1940%E2%80%932040)/dataset-cover.png)


# 🌍 Global Climate Change Dataset — Exploratory Data Analysis (EDA)
### Historical Records + Future Projections | 1940 – 2040

> A comprehensive end-to-end EDA project analyzing global climate trends across 6 regions, 4 scenarios, and 10 climate indicators — spanning a full century of environmental data.

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-EDA-lightblue)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-teal)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Plots-orange)
![Dataset](https://img.shields.io/badge/Dataset-1940–2040-green)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📁 Project Structure

```
climate-eda/
│
├── climate_dataset_extended_1940_2040.csv   # Main dataset
├── climate_eda.ipynb                        # Full Jupyter Notebook
├── README.md                                # Project documentation
└── visuals/                                 # Exported chart images
```

---

## 📌 Dataset Overview

| Property | Details |
|----------|---------|
| **File** | `climate_dataset_extended_1940_2040.csv` |
| **Year Range** | 1940 – 2040 (100 years) |
| **Scenarios** | Historical, Current (2020–2026), BAU, Green |
| **Regions** | North America, South America, Europe, Asia, Africa, Oceania |
| **Total Features** | 10 climate & socio-economic columns |
| **Format** | CSV / UTF-8 |

---

## 🧾 Feature Description

| Column | Type | Description | Unit |
|--------|------|-------------|------|
| `Year` | Integer | Year of observation | 1940 – 2040 |
| `Country` | String | Country name | Text |
| `Region` | String | Geographic region | Text |
| `Scenario` | String | Climate scenario | Historical / BAU / Green / Current |
| `CO2_Emissions_mt` | Float | Carbon dioxide emissions | Metric tons |
| `Temp_Anomaly_C` | Float | Temperature deviation from baseline | °C |
| `Renewable_Energy_%` | Float | Share of renewables in energy mix | % |
| `Extreme_Events` | Integer | Count of extreme climate events | Count |
| `Sea_Level_mm` | Float | Sea level rise from baseline | mm |
| `Methane_ppb` | Float | Atmospheric methane concentration | ppb |
| `GDP_Billion` | Float | National GDP | USD Billion |
| `Climate_Policy_Index` | Float | Composite climate policy strength score | Index |
| `Population_Million` | Float | National population | Millions |

---

## 🛠️ Libraries Used

```python
import pandas as pd          # Data loading, cleaning, aggregation
import numpy as np           # Numerical operations
import matplotlib.pyplot as plt  # Base plotting
import seaborn as sns        # Statistical visualizations
from scipy.stats import skew, kurtosis  # Distribution analysis
```

---

## 🔍 Data Preprocessing

```python
df = pd.read_csv('climate_dataset_extended_1940_2040.csv')

df.shape          # Dataset dimensions
df.info()         # Data types and null counts
df.describe()     # Statistical summary
df.isnull().sum() # Missing value check
df.dtypes         # Column data types

df['Region'].value_counts()   # Region distribution
df['Scenario'].unique()       # Unique scenario labels
df['Country'].nunique()       # Total distinct countries
```

> ⚠️ Missing values may appear in early years (1940–1960). Future values (2026–2040) are simulated projections — not official scientific forecasts.

---

## 📊 Analysis & Visualizations

### 1. 🌐 Average CO₂ Emissions by Region

```python
region_co2 = df.groupby('Region')['CO2_Emissions_mt'].mean().sort_values()
sns.barplot(x=region_co2.values, y=region_co2.index, palette="rocket")
```

**Key Insights:**
- Oceania & Africa lead with the highest average CO₂ (~450 mt)
- Asia is the lowest emitter (~330 mt) despite being the most populous region
- Europe & South America are nearly identical (~390 mt)
- A ~120 mt gap exists between the highest and lowest emitting regions

---

### 2. 🌡️ CO₂ Emissions vs Temperature Anomaly (by Scenario)

```python
sns.scatterplot(data=df, x='CO2_Emissions_mt', y='Temp_Anomaly_C',
                hue='Scenario', palette="Spectral", s=80)
```

**Key Insights:**
- Green scenario clusters between −0.5°C to +1.5°C — the safest zone
- BAU reaches 800+ CO₂ and +2.5°C — the most alarming trajectory
- Positive correlation exists across all four scenarios without exception
- Current (2020–2026) closely mirrors historical emission patterns

---

### 3. ♻️ Top 10 Countries by Renewable Energy Usage

```python
top = df.groupby('Country')['Renewable_Energy_%'].mean().sort_values(ascending=False).head(10)
sns.barplot(x=top.values, y=top.index, palette="crest")
```

**Key Insights:**
- All top 10 countries sit at ~18% renewable usage — a global plateau
- Germany leads, consistent with its Energiewende energy transition policy
- UAE's presence is surprising given its fossil-fuel-dominant economy
- Developed and developing nations share nearly identical renewable percentages

---

### 4. 🌪️ Extreme Climate Events by Region

```python
events = df.groupby('Region')['Extreme_Events'].sum().sort_values()
sns.barplot(x=events.values, y=events.index, palette="inferno")
```

**Key Insights:**
- Asia records ~58,000 extreme events — nearly double Europe's count
- Europe is second with ~29,000 events, driven by heatwaves and floods
- Africa and North America are nearly equal at ~14,000 events each
- Asia's count is 11× higher than Oceania's ~5,000 events

---

### 5. 🔗 Climate Variables Correlation Matrix

```python
corr = df.corr(numeric_only=True)
sns.heatmap(corr, annot=True, cmap='icefire', fmt='.2f')
```

**Key Insights:**
- Sea Level & Methane are almost perfectly correlated (0.99)
- Temperature Anomaly strongly predicts Sea Level (0.98), Methane (0.98), and Extreme Events (0.96)
- CO₂ Emissions show weak correlation with GDP (0.02) and Population (0.07)
- Renewable Energy & Climate Policy are strongly linked (0.85)

---

### 6. 📋 Policy Strength vs CO₂ Emissions

```python
sns.regplot(data=df, x='Climate_Policy_Index', y='CO2_Emissions_mt',
            scatter_kws={'color':'midnightblue'}, line_kws={'color':'orange'})
```

**Key Insights:**
- Regression line shows a counterintuitive positive slope — suggesting policy lag effects
- High emission outliers (700–800 CO₂) exist at all policy index levels
- Weak policies (index 10–30) produce the most volatile and unpredictable emission ranges
- Very strong policies (60+) show a marginally tighter emission band around 300–500

---

### 7. 🌊 Average Sea Level Rise Over Time

```python
sea = df.groupby('Year')['Sea_Level_mm'].mean()
plt.plot(sea.index, sea.values, linewidth=3)
```

**Key Insights:**
- Sea levels rose linearly from 0mm (1940) to ~248mm (2040) — no slowdown visible
- Rate averages ~2.5mm per year consistently across the entire century
- No policy intervention is reflected in the trend line
- Post-2020 projection continues unabated, adding ~50mm in the final 20 years

---

### 8. 🔥 Methane Concentration by Scenario

```python
sns.boxplot(data=df, x='Scenario', y='Methane_ppb', palette="Pastel1")
```

**Key Insights:**
- BAU has the highest median methane (~1400 ppb) with a range reaching ~1700 ppb
- Green scenario shows the lowest median (~1275 ppb) and the tightest spread
- Current (2020–2026) closely mirrors historical methane patterns
- BAU carries the most uncertainty with the widest interquartile range

---

### 9. 💰 GDP vs CO₂ Emissions by Region

```python
sns.scatterplot(data=df, x='GDP_Billion', y='CO2_Emissions_mt',
                hue='Region', palette="Dark2", s=90)
```

**Key Insights:**
- No clear linear relationship exists between GDP and CO₂ emissions
- Asia dominates emission intensity across all GDP levels
- North America produces the highest individual emission peaks (700–800+ CO₂)
- Africa shows low GDP but widely spread emissions — driven by energy mix factors

---

### 10. 📈 Yearly Average Temperature Anomaly

```python
temp = df.groupby('Year')['Temp_Anomaly_C'].mean()
sns.lineplot(x=temp.index, y=temp.values, linewidth=3)
```

**Key Insights:**
- Temperature rose ~2°C over 100 years — from −0.27°C (1940) to +1.77°C (2040)
- The 1.5°C Paris Agreement threshold is breached around 2030–2035
- Warming visibly accelerates post-1980 with industrial expansion
- Post-2020 shows no signs of plateauing — on track to exceed +2°C before 2050

---

### 11. 🌊 Predicted Sea Level Rise by Region

```python
sns.lineplot(data=df, x='Year', y='Sea_Level_mm', hue='Region', linewidth=3)
```

**Key Insights:**
- All six regions show near-identical trajectories — sea level rise is a global phenomenon
- Oceania carries the widest uncertainty band, reaching ~280mm by 2040
- Growth rate visibly accelerates post-1980 across all regions
- All regions converge at ~245mm by 2040, threatening coastal infrastructure worldwide

---

### 12. 🧩 Predictors of Temperature Anomaly (Clustermap)

```python
sns.clustermap(corr, cmap='vlag', annot=True, figsize=(10,8), linewidths=0.5)
```

**Key Insights:**
- Temp Anomaly, Sea Level & Methane form a near-perfect cluster (0.98–0.99)
- Renewable Energy & Climate Policy cluster together (0.85) as inseparable drivers
- CO₂ Emissions stand isolated from all core climate variables
- Year itself (0.91–0.94) is a strong proxy predictor of all climate deterioration

---

## 🔢 Advanced Statistical Analysis

```python
# Regional + Scenario Aggregation
result = df.groupby(['Region', 'Scenario']).agg(
    CO2_Avg=('CO2_Emissions_mt', 'mean'),
    Temp_Avg=('Temp_Anomaly_C', 'mean'),
    Events_Total=('Extreme_Events', 'sum')
).reset_index()

# Pivot Table: CO₂ by Region vs Scenario
pivot = df.pivot_table(
    values='CO2_Emissions_mt',
    index='Region',
    columns='Scenario',
    aggfunc='mean'
)

# Cross-tabulation: Scenario frequency by Region
cross = pd.crosstab(df['Region'], df['Scenario'])

# Distribution Analysis
from scipy.stats import skew, kurtosis
skew_value  = skew(df['CO2_Emissions_mt'])     # Symmetry check
kurt_value  = kurtosis(df['CO2_Emissions_mt']) # Tail heaviness

# Filtered Query
df.query("CO2_Emissions_mt > 500 and Temp_Anomaly_C > 1.5")
```

---

## 💡 Key Takeaways

| # | Finding |
|---|---------|
| 1 | Temperature has risen ~2°C in 100 years — the Paris 1.5°C threshold is nearly breached |
| 2 | Sea levels are rising at ~2.5mm/year with no slowdown visible across any region |
| 3 | BAU scenario is dramatically worse across all indicators — methane, CO₂, temperature |
| 4 | Green scenario consistently produces the best outcomes for every climate variable |
| 5 | CO₂ emissions are NOT driven by GDP or population — structural factors dominate |
| 6 | Renewable energy and climate policy must be advanced together — they are inseparable |
| 7 | Asia bears the highest burden of extreme climate events at 11× the rate of Oceania |
| 8 | Methane and sea level are nearly perfectly correlated (0.99) — a critical feedback loop |

---

## ⚙️ How to Run

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/climate-eda.git
cd climate-eda

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scipy

# 3. Launch Jupyter Notebook
jupyter notebook climate_eda.ipynb
```

---

## ⚠️ Disclaimer

> Future values (2026–2040) are **simulated projections** for research and educational purposes only. They are **not** official scientific forecasts from IPCC, NASA, NOAA, or any governmental body. Always cross-reference with authoritative sources for policy or academic decisions.

---

## 📜 Citation

```
Climate Change Extended Dataset EDA (1940–2040).
Analysis performed using Python (Pandas, Seaborn, Matplotlib, SciPy).
Future projections are model-based simulations for educational use only.
```

---

*Made with 🌱 for a data-driven understanding of our planet's climate future.*

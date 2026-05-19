![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/c5d794cb1d582ec3beed144f0ced0448d3671d04/Global%20Climate%20Change%20(1940%E2%80%932040)/dataset-cover.png)


# 🌍 Global Climate Change Dataset & EDA
### Historical Records + Future Projections | 1940 – 2040

> A comprehensive end-to-end climate analysis project combining 100 years of historical and projected data across 6 regions, 4 scenarios, and 13 climate indicators — with full exploratory data analysis, visualizations, and key findings.

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0)](https://seaborn.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Plots-11557C)](https://matplotlib.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-Educational_Use-green)](/)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen)](/)
[![Dataset](https://img.shields.io/badge/Dataset-1940–2040-blue)](/)

---

## 📑 Table of Contents

1. [Project Overview](#-project-overview)
2. [Project Structure](#-project-structure)
3. [Dataset Information](#-dataset-information)
4. [Feature Description](#-feature-description)
5. [Libraries Used](#-libraries-used)
6. [Data Preprocessing](#-data-preprocessing)
7. [Analysis & Visualizations](#-analysis--visualizations)
8. [Advanced Statistical Analysis](#-advanced-statistical-analysis)
9. [Key Takeaways](#-key-takeaways)
10. [Use Cases](#-use-cases)
11. [How to Run](#-how-to-run)
12. [Data Quality Notes](#-data-quality-notes)
13. [Disclaimer & Citation](#-disclaimer--citation)

---

## 🧭 Project Overview

Climate change is no longer a future problem — it is a **present global reality.**

This project delivers a full end-to-end exploratory data analysis of the **Global Climate Change Extended Dataset (1940–2040)**, combining historical climate observations with model-based future projections. It is designed to help researchers, data scientists, students, economists, and AI practitioners explore how the global climate crisis has evolved across an entire century.

| Property | Details |
|----------|---------|
| **Dataset** | `climate_dataset_extended_1940_2040.csv` |
| **Year Range** | 1940 – 2040 (100 years) |
| **Scenarios** | Historical · Current (2020–2026) · BAU · Green |
| **Regions** | North America · South America · Europe · Asia · Africa · Oceania |
| **Features** | 13 climate & socio-economic columns |
| **Format** | CSV / UTF-8 |
| **File Size** | Approx. 1 – 50 MB |
| **Visualizations** | 12 charts (bar, scatter, line, box, heatmap, clustermap) |

---

## 📁 Project Structure

```
climate-eda/
│
├── 📄 climate_dataset_extended_1940_2040.csv   # Main dataset (raw)
├── 📓 climate_eda.ipynb                        # Full Jupyter Notebook (EDA)
├── 📝 README.md                                # Project documentation
└── 📊 visuals/                                 # Exported chart images
    ├── co2_by_region.png
    ├── co2_vs_temp_anomaly.png
    ├── renewable_energy_top10.png
    ├── extreme_events_by_region.png
    ├── correlation_matrix.png
    ├── policy_vs_emissions.png
    ├── sea_level_over_time.png
    ├── methane_by_scenario.png
    ├── gdp_vs_co2.png
    ├── temp_anomaly_yearly.png
    ├── sea_level_by_region.png
    └── clustermap_predictors.png
```

---

## 📌 Dataset Information

This dataset captures long-term environmental and socio-economic climate indicators across multiple global regions, structured to support a wide range of analytical workloads:

| Climate Indicators | Socio-Economic Indicators |
|--------------------|--------------------------|
| 🌡️ Global temperature anomalies | 💰 GDP by country (Billion USD) |
| 🌊 Sea level rise (mm) | 👥 Population exposure (Millions) |
| ❄️ Arctic ice extent decline | 📋 Climate Policy Index |
| 🌪️ Extreme weather event counts | ♻️ Renewable energy share (%) |
| 🌿 CO₂ & Methane concentrations | 🔥 Climate risk escalation scores |

---

## 🧾 Feature Description

| Column | Type | Description | Unit |
|--------|------|-------------|------|
| `Year` | Integer | Year of observation | 1940 – 2040 |
| `Country` | String | Country name | Text |
| `Region` | String | Geographic region grouping | Text |
| `Scenario` | String | Climate trajectory scenario | Historical / BAU / Green / Current |
| `CO2_Emissions_mt` | Float | Carbon dioxide emissions | Metric tons |
| `Temp_Anomaly_C` | Float | Temperature deviation from baseline | °C |
| `Renewable_Energy_%` | Float | Share of renewables in total energy mix | % |
| `Extreme_Events` | Integer | Count of recorded extreme climate events | Count |
| `Sea_Level_mm` | Float | Sea level rise from 1940 baseline | mm |
| `Methane_ppb` | Float | Atmospheric methane concentration | ppb |
| `GDP_Billion` | Float | National GDP | USD Billion |
| `Climate_Policy_Index` | Float | Composite climate policy strength score | Index (0–100) |
| `Population_Million` | Float | National population | Millions |

---

## 🛠️ Libraries Used

```python
import pandas as pd               # Data loading, cleaning, aggregation
import numpy as np                # Numerical operations and array handling
import matplotlib.pyplot as plt   # Base plotting and figure management
import seaborn as sns             # Statistical data visualizations
from scipy.stats import skew, kurtosis  # Distribution shape analysis
```

---

## 🔍 Data Preprocessing

```python
# Load dataset
df = pd.read_csv('climate_dataset_extended_1940_2040.csv')

# Basic inspection
df.shape               # Dataset dimensions (rows × columns)
df.head()              # First 5 rows
df.tail()              # Last 5 rows
df.info()              # Data types and non-null counts
df.describe()          # Statistical summary (mean, std, min, max, quartiles)
df.dtypes              # Column-level data types

# Data quality checks
df.isnull().sum()      # Missing value count per column
df.sample(5)           # Random sample for sanity check
df.memory_usage(deep=True)  # Memory footprint

# Categorical exploration
df['Region'].value_counts()    # Region distribution
df['Scenario'].unique()        # Distinct scenario labels
df['Country'].nunique()        # Total number of unique countries

# Correlation overview
df.corr(numeric_only=True)     # Pairwise correlation matrix

# Group-level aggregations
df.groupby('Region')['CO2_Emissions_mt'].mean()
df.groupby('Region')[['CO2_Emissions_mt', 'Temp_Anomaly_C']].mean()
```

> ⚠️ **Note:** Missing values may appear in early historical years (1940–1960) due to limited monitoring infrastructure. Imputation or interpolation may be required before model training.

---

## 📊 Analysis & Visualizations

### 1. 🌐 Average CO₂ Emissions by Region

```python
region_co2 = df.groupby('Region')['CO2_Emissions_mt'].mean().sort_values()
sns.barplot(x=region_co2.values, y=region_co2.index, palette="rocket")
```

| # | Insight |
|---|---------|
| 1 | Oceania & Africa lead at ~450 mt — significantly above all other regions |
| 2 | Asia is the lowest emitter (~330 mt) despite being the world's most populous region |
| 3 | Europe & South America are nearly equal at ~390 mt |
| 4 | A ~120 mt gap separates the highest and lowest emitting regions |
| 5 | North America sits in the middle at ~405 mt, reflecting moderate-high output |

---

### 2. 🌡️ CO₂ Emissions vs Temperature Anomaly

```python
sns.scatterplot(data=df, x='CO2_Emissions_mt', y='Temp_Anomaly_C',
                hue='Scenario', palette="Spectral", s=80)
```

| # | Insight |
|---|---------|
| 1 | Green scenario clusters between −0.5°C to +1.5°C — the safest temperature zone |
| 2 | BAU reaches 800+ CO₂ and +2.5°C — the most alarming trajectory of all scenarios |
| 3 | A positive correlation between CO₂ and temperature exists across all four scenarios |
| 4 | Current (2020–2026) closely mirrors historical patterns — no significant divergence yet |
| 5 | Emission range widens drastically in BAU — inaction exponentially expands the ceiling |

---

### 3. ♻️ Top 10 Countries by Renewable Energy Usage

```python
top = df.groupby('Country')['Renewable_Energy_%'].mean() \
        .sort_values(ascending=False).head(10)
sns.barplot(x=top.values, y=top.index, palette="crest")
```

| # | Insight |
|---|---------|
| 1 | All top 10 countries sit at ~18% — indicating a global renewable adoption plateau |
| 2 | Germany leads, consistent with its Energiewende (energy transition) policy |
| 3 | UAE's inclusion is surprising for a fossil-fuel-dominant economy |
| 4 | Developed and developing nations share nearly identical renewable percentages |
| 5 | Bangladesh achieving ~18% renewables is remarkable for a lower-income nation |

---

### 4. 🌪️ Extreme Climate Events by Region

```python
events = df.groupby('Region')['Extreme_Events'].sum().sort_values()
sns.barplot(x=events.values, y=events.index, palette="inferno")
```

| # | Insight |
|---|---------|
| 1 | Asia records ~58,000 extreme events — nearly double Europe's count |
| 2 | Europe is second at ~29,000 events, driven by heatwaves, floods, and wildfires |
| 3 | Africa and North America are nearly equal at ~14,000 events each |
| 4 | Oceania has the fewest at ~5,000 events — largely due to landmass and population |
| 5 | The Asia–Oceania gap is 11× — the starkest regional climate disparity in the dataset |

---

### 5. 🔗 Climate Variables Correlation Matrix

```python
corr = df.corr(numeric_only=True)
sns.heatmap(corr, annot=True, cmap='icefire', fmt='.2f')
```

| # | Insight |
|---|---------|
| 1 | Sea Level & Methane are almost perfectly correlated (0.99) |
| 2 | Temperature Anomaly is highly correlated with Sea Level (0.98) and Extreme Events (0.96) |
| 3 | CO₂ Emissions are weakly correlated with GDP (0.02) and Population (0.07) |
| 4 | GDP & Population show uniformly low correlations across all climate variables |
| 5 | Renewable Energy & Climate Policy are strongly linked (0.85) |

---

### 6. 📋 Policy Strength vs CO₂ Emissions

```python
sns.regplot(data=df, x='Climate_Policy_Index', y='CO2_Emissions_mt',
            scatter_kws={'color': 'midnightblue'}, line_kws={'color': 'orange'})
```

| # | Insight |
|---|---------|
| 1 | Regression line shows a counterintuitive positive slope — attributable to policy lag effects |
| 2 | High emission outliers (700–800 CO₂) exist at every policy index level |
| 3 | Weak policies (index 10–30) produce the most volatile, unpredictable emission ranges |
| 4 | Strong policies (60+) show a marginally tighter emission band around 300–500 |
| 5 | Low emissions appear at both extremes of the policy index — a non-linear pattern |

---

### 7. 🌊 Average Sea Level Rise Over Time

```python
sea = df.groupby('Year')['Sea_Level_mm'].mean()
plt.plot(sea.index, sea.values, linewidth=3)
```

| # | Insight |
|---|---------|
| 1 | Sea levels rose linearly from 0mm (1940) to ~248mm (2040) — zero slowdown visible |
| 2 | Rate averages ~2.5mm per year consistently across the entire 100-year span |
| 3 | No climate policy intervention is reflected anywhere in the trend |
| 4 | Post-2020 projection continues unabated, adding ~50mm in the final 20 years |
| 5 | Total ~248mm (25cm) rise threatens coastal cities and island nations globally |

---

### 8. 🔥 Methane Concentration by Scenario

```python
sns.boxplot(data=df, x='Scenario', y='Methane_ppb', palette="Pastel1")
```

| # | Insight |
|---|---------|
| 1 | BAU has the highest median methane (~1400 ppb) with an upper range of ~1700 ppb |
| 2 | Green scenario shows the lowest median (~1275 ppb) and the smallest IQR spread |
| 3 | Current (2020–2026) closely mirrors historical methane levels — minimal divergence |
| 4 | BAU carries the widest uncertainty band — inaction creates volatile outcomes |
| 5 | Green scenario stabilizes methane, reducing both level and variability simultaneously |

---

### 9. 💰 GDP vs CO₂ Emissions by Region

```python
sns.scatterplot(data=df, x='GDP_Billion', y='CO2_Emissions_mt',
                hue='Region', palette="Dark2", s=90)
```

| # | Insight |
|---|---------|
| 1 | No clear linear relationship exists between national GDP and CO₂ emissions |
| 2 | Asia dominates emission intensity across the full GDP spectrum |
| 3 | North America produces the highest individual emission peaks (700–800+ CO₂) |
| 4 | South America clusters in the mid-GDP, mid-emission zone consistently |
| 5 | Africa shows low GDP but widely spread emissions — driven by energy mix factors |

---

### 10. 📈 Yearly Average Temperature Anomaly

```python
temp = df.groupby('Year')['Temp_Anomaly_C'].mean()
sns.lineplot(x=temp.index, y=temp.values, linewidth=3)
```

| # | Insight |
|---|---------|
| 1 | Temperature rose ~2°C over 100 years — from −0.27°C (1940) to +1.77°C (2040) |
| 2 | The 1.5°C Paris Agreement threshold is breached around 2030–2035 |
| 3 | Warming visibly accelerates post-1980 with global industrial expansion |
| 4 | Pre-1960 shows the last era of relative temperature stability (~0°C fluctuation) |
| 5 | Post-2020 shows no sign of plateauing — on track to exceed +2°C before 2050 |

---

### 11. 🌊 Predicted Sea Level Rise by Region

```python
sns.lineplot(data=df, x='Year', y='Sea_Level_mm', hue='Region', linewidth=3)
```

| # | Insight |
|---|---------|
| 1 | All six regions show near-identical trajectories — sea level rise is a global crisis |
| 2 | Uncertainty bands widen significantly post-2000 across all regions |
| 3 | Oceania carries the widest uncertainty band, reaching ~280mm by 2040 |
| 4 | Growth rate visibly accelerates post-1980, mirroring temperature trend acceleration |
| 5 | All regions converge at ~245mm by 2040, threatening coastal infrastructure worldwide |

---

### 12. 🧩 Predictors of Temperature Anomaly (Clustermap)

```python
sns.clustermap(corr, cmap='vlag', annot=True, figsize=(10, 8), linewidths=0.5)
```

| # | Insight |
|---|---------|
| 1 | Temp Anomaly, Sea Level & Methane form a near-perfect cluster (0.98–0.99) |
| 2 | Renewable Energy & Climate Policy cluster together (0.85) as inseparable twin drivers |
| 3 | CO₂ Emissions stand isolated from all core climate variables in their own cluster |
| 4 | GDP & Population are climate-irrelevant — poor predictors of footprint or vulnerability |
| 5 | Year (0.91–0.94) is a master proxy for all climate deterioration — time alone predicts worsening |

---

## 🔢 Advanced Statistical Analysis

```python
# ── Regional + Scenario Aggregation ─────────────────────────────────────────
result = df.groupby(['Region', 'Scenario']).agg(
    CO2_Avg      = ('CO2_Emissions_mt', 'mean'),
    Temp_Avg     = ('Temp_Anomaly_C',   'mean'),
    Events_Total = ('Extreme_Events',   'sum')
).reset_index()

# ── Pivot Table: CO₂ by Region vs Scenario ───────────────────────────────────
pivot = df.pivot_table(
    values  = 'CO2_Emissions_mt',
    index   = 'Region',
    columns = 'Scenario',
    aggfunc = 'mean'
)

# ── Cross-tabulation: Scenario frequency per Region ──────────────────────────
cross = pd.crosstab(df['Region'], df['Scenario'])

# ── Distribution Shape Analysis ──────────────────────────────────────────────
from scipy.stats import skew, kurtosis
print("Skewness :", skew(df['CO2_Emissions_mt']))    # Symmetry of distribution
print("Kurtosis :", kurtosis(df['CO2_Emissions_mt'])) # Tail heaviness

# ── Sorting & Filtering ───────────────────────────────────────────────────────
df_sorted = df.sort_values(by='CO2_Emissions_mt', ascending=False)
df.sort_values(by=['Region', 'CO2_Emissions_mt'], ascending=[True, False])
df.query("CO2_Emissions_mt > 500 and Temp_Anomaly_C > 1.5")
```

---

## 💡 Key Takeaways

| # | Finding | Implication |
|---|---------|-------------|
| 1 | Temperature rose ~2°C in 100 years; 1.5°C Paris threshold breached ~2030–2035 | Urgent immediate action required |
| 2 | Sea levels rising at ~2.5mm/year with zero slowdown across all regions | Coastal infrastructure at serious risk |
| 3 | BAU scenario is dramatically worse across every single indicator | Inaction has compounding consequences |
| 4 | Green scenario delivers the best outcomes for all climate variables | Policy-driven transition works |
| 5 | CO₂ emissions are NOT driven by GDP or population size | Structural reforms are the key lever |
| 6 | Renewable energy and climate policy must be advanced together (0.85 correlation) | Integrated policy design is essential |
| 7 | Asia bears 11× more extreme events than Oceania | Regional climate equity is a critical issue |
| 8 | Methane & sea level are near-perfectly correlated (0.99) | A self-reinforcing feedback loop exists |

---

## 📊 Use Cases

| Domain | Applications |
|--------|-------------|
| 🤖 **Machine Learning & AI** | Climate forecasting · ARIMA / LSTM / Prophet models · Anomaly detection · Risk classification |
| 📊 **Data Science** | EDA · Interactive dashboards · Correlation analysis · Scenario comparisons |
| 🎓 **Academic Research** | Environmental science · Climate economics · Policy impact studies · Sustainability research |
| 📰 **Storytelling** | Kaggle notebooks · Medium / TDS articles · Policy presentations · Climate awareness campaigns |

---

## 🧠 Ideal For

| Audience | Primary Use |
|----------|------------|
| 👨‍💻 Data Scientists | EDA, feature engineering, ML modeling |
| 🌿 Climate Researchers | Trend analysis, regional comparisons |
| 💰 Economists | Climate-economic impact studies |
| 🎓 Students & Educators | Learning projects, course assignments |
| 🤖 AI Engineers | Time-series forecasting, deep learning |
| 🌱 Sustainability Analysts | Policy simulation, risk assessment |
| 🏆 Kaggle Competitors | Notebooks, competitions, storytelling |
| 📰 Journalists | Data-driven climate journalism |

---

## ⚙️ How to Run

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/climate-eda.git
cd climate-eda

# 2. Install all dependencies
pip install pandas numpy matplotlib seaborn scipy jupyter

# 3. Launch the Jupyter Notebook
jupyter notebook climate_eda.ipynb
```

```python
# Minimal quick-start — run in any Python environment
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv("climate_dataset_extended_1940_2040.csv")
print(df.shape)
print(df.describe())

df.groupby("Year")["Temp_Anomaly_C"].mean().plot(
    title="Average Temperature Anomaly Over Time",
    color="tomato", figsize=(12, 5)
)
plt.tight_layout()
plt.show()
```

---

## 🧹 Data Quality Notes

> ⚠️ **Missing Values** — Missing values may exist in early years (1940–1960) due to sparse global monitoring. Imputation or interpolation is recommended before training models.

> 🔭 **Future Projections** — Values for 2026–2040 are **model-based simulated projections** for research and educational use only. They are **NOT** official forecasts from IPCC, NASA, or NOAA.

> 📉 **Outliers** — Emission spikes during industrialization periods may appear as outliers. Box plots and z-score filtering are recommended during preprocessing.

---

## ⚠️ Disclaimer & Citation

> Future values (2026–2040) are **projected/simulated trends** for research and educational purposes only. Always cross-reference with authoritative sources — [NASA Climate](https://climate.nasa.gov/), [NOAA](https://www.noaa.gov/), [IPCC Reports](https://www.ipcc.ch/) — for policy or academic decisions.

**To cite this project:**
```
Climate Change Extended Dataset & EDA (1940–2040).
Analysis performed using Python (Pandas, Seaborn, Matplotlib, SciPy).
Future projections (2026–2040) are model-based simulations for educational use only.
```

---

## 📬 Contributing & Feedback

Found an issue or have suggestions? Open an issue or submit a pull request.
Contributions that improve data quality, extend projection range, or add new analyses are welcome.

---

*Made with 🌱 for a data-driven understanding of our planet's climate future.*

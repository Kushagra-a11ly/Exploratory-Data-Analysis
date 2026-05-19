
# 🌍 Global Climate Change EDA
### Exploratory Data Analysis · 1940–2040 · Historical Records + Future Projections

---

## Overview

A comprehensive Exploratory Data Analysis of the **Global Climate Change Extended Dataset**, spanning 100 years of climate observation and model-based projection (1940–2040). The analysis covers six geographic regions, four climate scenarios, and 13 socio-economic and environmental features — producing 12 targeted visualizations and a suite of advanced statistical findings.

> ⚠️ **Disclaimer:** Future values (2026–2040) are model-based simulated projections created for research and educational purposes only. They are **not** official scientific forecasts from IPCC, NASA, NOAA, or any governmental body.

---

## Dataset

| Property       | Details                                                                 |
|----------------|-------------------------------------------------------------------------|
| **File**       | `climate_dataset_extended_1940_2040.csv`                                |
| **Year Range** | 1940 – 2040 (100 years)                                                 |
| **Scenarios**  | Historical · Current (2020–2026) · BAU · Green                         |
| **Regions**    | North America · South America · Europe · Asia · Africa · Oceania        |
| **Features**   | 13 climate & socio-economic columns                                     |
| **Format**     | CSV / UTF-8                                                             |

### Features

| Column                | Type    | Description                                      | Unit         |
|-----------------------|---------|--------------------------------------------------|--------------|
| `Year`                | Integer | Year of observation                              | 1940–2040    |
| `Country`             | String  | Country name                                     | Text         |
| `Region`              | String  | Geographic region grouping                       | Text         |
| `Scenario`            | String  | Climate trajectory scenario                      | Hist/BAU/Green/Current |
| `CO2_Emissions_mt`    | Float   | Carbon dioxide emissions                         | Metric tons  |
| `Temp_Anomaly_C`      | Float   | Temperature deviation from baseline              | °C           |
| `Renewable_Energy_%`  | Float   | Share of renewables in total energy mix          | %            |
| `Extreme_Events`      | Integer | Count of extreme climate events                  | Count        |
| `Sea_Level_mm`        | Float   | Sea level rise from 1940 baseline                | mm           |
| `Methane_ppb`         | Float   | Atmospheric methane concentration                | ppb          |
| `GDP_Billion`         | Float   | National GDP                                     | USD Billion  |
| `Climate_Policy_Index`| Float   | Composite policy strength score                  | Index 0–100  |
| `Population_Million`  | Float   | National population                              | Millions     |

---

## Tech Stack

| Library       | Role                                                                 |
|---------------|----------------------------------------------------------------------|
| `pandas`      | Data loading, cleaning, aggregation, groupby operations             |
| `numpy`       | Numerical computation and array manipulation                        |
| `matplotlib`  | Base visualization engine — axes, labels, color, layout control     |
| `seaborn`     | Statistical charts — bar, scatter, box, heatmap, clustermap, regplot|
| `scipy.stats` | Distribution analysis — skewness and kurtosis of CO₂ emissions      |

---

## Installation

```bash
# Clone the repository
git clone https://github.com/your-username/climate-eda.git
cd climate-eda

# Create and activate a virtual environment (recommended)
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

**`requirements.txt`**
```
pandas
numpy
matplotlib
seaborn
scipy
```

---

## Usage

```bash
# Run the full EDA notebook
jupyter notebook climate_eda.ipynb

# Or execute the script directly
python climate_eda.py
```

Ensure `climate_dataset_extended_1940_2040.csv` is placed in the project root before running.

---

## Visualizations

| # | Chart | Research Question |
|---|-------|-------------------|
| 1 | Average CO₂ Emissions by Region | Which regions contribute the highest CO₂ emissions? |
| 2 | CO₂ Emissions vs Temperature Anomaly | Is temperature anomaly increasing with CO₂ emissions? |
| 3 | Top 10 Countries by Renewable Energy | Which countries invest most in renewable energy? |
| 4 | Extreme Climate Events by Region | Which regions face the most extreme climate events? |
| 5 | Climate Variables Correlation Matrix | How strongly are climate variables correlated? |
| 6 | Policy Strength vs CO₂ Emissions | Are stronger climate policies reducing emissions? |
| 7 | Average Sea Level Rise Over Time | How has sea level changed over 100 years? |
| 8 | Methane Concentration by Scenario | Which scenario produces the highest methane concentration? |
| 9 | GDP vs CO₂ Emissions by Region | Which regions have the highest GDP and emissions together? |
| 10 | Yearly Average Temperature Anomaly | Which years recorded the highest average temperature anomaly? |
| 11 | Predicted Sea Level Rise by Region | Which regions face the most severe sea level rise? |
| 12 | Predictors of Temperature Anomaly (Clustermap) | Which variables most strongly predict temperature anomaly? |

---

## Key Findings

### 🌡️ Temperature & Emissions
- Global temperature rose **~2°C over 100 years**; the Paris Agreement's 1.5°C threshold is projected to be breached around **2030–2035**
- The **BAU scenario** is dramatically worse across every indicator — methane, CO₂, temperature, and sea level
- The **Green scenario** consistently delivers the best outcomes across all climate variables
- CO₂ emissions are **not driven by GDP or population** — structural energy-mix and industrial factors dominate

### 🌊 Sea Level, Methane & Extreme Events
- Sea levels are rising at **~2.5 mm/year** with no slowdown — projected to reach **~248 mm by 2040**
- Methane and sea level are near-perfectly correlated (**r = 0.99**), forming an active feedback loop
- **Asia bears 11× more extreme climate events than Oceania**, demanding equity-centred financing
- Renewable energy adoption and climate policy strength are tightly coupled (**r = 0.85**)

---

## Advanced Statistical Analysis

```python
# Multi-dimensional aggregation
result = df.groupby(['Region', 'Scenario']).agg(
    CO2_Avg      = ('CO2_Emissions_mt', 'mean'),
    Temp_Avg     = ('Temp_Anomaly_C', 'mean'),
    Events_Total = ('Extreme_Events', 'sum')
).reset_index()

# Pivot table — CO₂ by Region vs Scenario
pivot = df.pivot_table(
    values='CO2_Emissions_mt', index='Region',
    columns='Scenario', aggfunc='mean'
)

# Distribution shape of CO₂ emissions
from scipy.stats import skew, kurtosis
print('Skewness:', skew(df['CO2_Emissions_mt']))   # Right-skewed → industrialization spikes
print('Kurtosis:', kurtosis(df['CO2_Emissions_mt'])) # Heavy tails → frequent extreme outliers

# Filter critical threshold records
df.query("CO2_Emissions_mt > 500 and Temp_Anomaly_C > 1.5")
```

---

## Project Structure

```
climate-eda/
├── climate_dataset_extended_1940_2040.csv   # Source dataset
├── climate_eda.ipynb                        # Main analysis notebook
├── climate_eda.py                           # Script version
├── charts/                                  # Exported visualizations (PNG)
├── requirements.txt
└── README.md
```

---

## Recommended Next Steps

| Action | Rationale |
|--------|-----------|
| Build time-series models (ARIMA, LSTM, Prophet) | Year correlates 0.91–0.94 with all major climate indicators |
| Develop scenario classification models | Four scenarios are analytically distinct; suitable for ML classification |
| Apply IQR / z-score outlier filtering before modelling | Industrialization-era emission spikes will distort regression algorithms |
| Interpolate missing values in 1940–1960 | Sparse early monitoring data needs explicit handling before ML pipelines |
| Conduct region-specific sub-analyses | Asia's event dominance and Oceania's sea level variability warrant separate models |
| Explore non-linear models for policy-emission dynamics | Linear regression alone cannot capture the counterintuitive policy-CO₂ relationship |


## Citation

```
Climate Change Extended Dataset EDA (1940–2040).
Analysis performed using Python (Pandas, Seaborn, Matplotlib, SciPy).
Future projections (2026–2040) are model-based simulations for educational use only.
```

---

## License

This project is released for educational and research purposes. Future projection data is synthetic and must not be used as a basis for official policy or academic claims without cross-referencing authoritative sources.

---

<p align="center">Made with 🌱 for a data-driven understanding of our planet's climate future.</p>

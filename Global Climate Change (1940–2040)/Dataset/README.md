![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/c5d794cb1d582ec3beed144f0ced0448d3671d04/Global%20Climate%20Change%20(1940%E2%80%932040)/dataset-cover.png)


# 🌍 Global Climate Change Dataset (1940–2040)

> A comprehensive historical + future projection dataset designed for climate analysis, machine learning, forecasting, sustainability research, and environmental storytelling.

![Years](https://img.shields.io/badge/Years-1940–2040-blue)
![Format](https://img.shields.io/badge/Format-CSV-green)
![Regions](https://img.shields.io/badge/Regions-6-teal)
![Features](https://img.shields.io/badge/Features-10-orange)
![ML Ready](https://img.shields.io/badge/ML-Ready-brightgreen)

---

## 📌 Overview

This dataset combines **historical climate trends (1940–2025)** with **future climate projections (2026–2040)** to help researchers, data scientists, students, economists, and AI practitioners explore how the global climate crisis evolved across an entire century.

It captures long-term environmental and socio-economic climate indicators including:

- 🌡️ Global temperature anomalies
- 🌊 Sea level rise
- ❄️ Arctic ice extent decline
- 🌪️ Extreme weather events
- 🌿 CO₂ concentration growth
- 🔥 Climate risk escalation
- 🌎 Sustainability-related indicators
- 📈 Future climate forecasting trends

---

## 📂 File Information

| Property | Details |
|----------|---------|
| **File Name** | `climate_change_1940_2040.csv` |
| **Format** | CSV (Comma-Separated Values) |
| **Encoding** | UTF-8 |
| **File Size** | Approx. 1–50 MB |
| **Year Range** | 1940 – 2040 |
| **Regions** | North America, South America, Europe, Asia, Africa, Oceania |

---

## 🧾 Column / Feature Description

| Column Name | Data Type | Description | Unit / Format |
|-------------|-----------|-------------|---------------|
| `Year` | Integer | Year of observation | 1940 – 2040 |
| `Country/Region` | String | Geographic region or country | Text label |
| `Temperature_Anomaly` | Float | Deviation from baseline global temperature | °C |
| `CO2_Emissions` | Float | Carbon dioxide emissions (total or per capita) | Metric tons |
| `Methane_Emissions` | Float | Methane emission levels | ppb |
| `Sea_Level_Rise` | Float | Sea level rise over baseline | mm / cm |
| `Ice_Cover_Percentage` | Float | Arctic / Antarctic ice coverage | % |
| `Renewable_Energy_Usage` | Float | Share of renewable energy in total consumption | % |
| `Climate_Risk_Index` | Float | Composite climate risk score | Index score |
| `Population_Exposure` | Integer | Population affected by climate risks | Millions |

---

## 🎯 Why This Dataset Matters

Climate change is no longer a future problem — it is a **present global reality**.

This dataset was created to provide a long-range perspective (1940–2040) on how environmental systems have transformed over time and where current trajectories may lead. By combining historical observations with projected trends, it helps answer questions such as:

- ❓ How rapidly has global warming accelerated since the industrial era?
- ❓ What patterns exist in sea-level rise and Arctic ice loss over decades?
- ❓ How are extreme weather events evolving across different regions?
- ❓ Can AI models forecast future climate risks with acceptable accuracy?
- ❓ What might the world's climate look like by 2040 under current trajectories?

---

## 📊 Potential Use Cases

### 🤖 Machine Learning & AI
- Climate forecasting models
- Regression and time-series prediction (ARIMA, LSTM, Prophet)
- Anomaly detection in climate indicators
- Risk prediction and classification systems

### 📊 Data Science Projects
- Exploratory Data Analysis (EDA)
- Interactive dashboards and visualizations
- Statistical correlation and trend analysis
- Scenario comparison (Historical vs BAU vs Green)

### 🎓 Academic Research
- Climate economics and policy analysis
- Environmental science and sustainability studies
- Cross-regional climate impact comparisons
- Long-term environmental trend modeling

### 📰 Content & Storytelling
- Medium / Towards Data Science articles
- Kaggle notebooks and competition projects
- Climate awareness data visualizations
- Public policy presentations and reports

---

## 🧹 Data Quality Notes

> ⚠️ **Missing Values** — Missing values may exist in early historical years (1940–1960) due to limited global monitoring infrastructure. Imputation or interpolation may be required before modeling.

> 🔭 **Future Projections** — Values for 2026–2040 are **model-based simulated projections** created for research and educational purposes. They should **NOT** be interpreted as official scientific forecasts from IPCC or any governmental body.

> 📉 **Outliers** — Outliers may appear in emission spikes during heavy industrialization periods. Exploratory analysis with box plots or z-score filtering is recommended before training predictive models.

---

## 🧠 Ideal For

| Audience | Use |
|----------|-----|
| 👨‍💻 Data Scientists | EDA, feature engineering, ML modeling |
| 🌿 Climate Researchers | Trend analysis, regional comparisons |
| 💰 Economists | Climate-economic impact studies |
| 🎓 Students & Educators | Learning projects, course assignments |
| 🤖 AI Engineers | Time-series forecasting, deep learning |
| 🌱 Sustainability Analysts | Policy simulation, risk assessment |
| 🏆 Kaggle Competitors | Notebooks, competitions, storytelling |
| 📰 Journalists | Data-driven climate journalism |

---

## 🚀 Quick Start

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("climate_change_1940_2040.csv")

# Preview
print(df.head())
print(df.info())
print(df.describe())

# Plot temperature anomaly over time
df.groupby("Year")["Temperature_Anomaly"].mean().plot(
    title="Average Temperature Anomaly Over Time",
    xlabel="Year",
    ylabel="Temperature Anomaly (°C)",
    color="tomato",
    figsize=(12, 5)
)
plt.tight_layout()
plt.show()
```

---

## 📈 Suggested Analyses

```python
# 1. Correlation matrix
df.corr(numeric_only=True).style.background_gradient(cmap="coolwarm")

# 2. Regional CO2 emissions comparison
df.groupby("Country/Region")["CO2_Emissions"].mean().sort_values().plot(kind="barh")

# 3. Sea level rise trend
df.groupby("Year")["Sea_Level_Rise"].mean().plot()

# 4. Scenario comparison (if Scenario column exists)
df.groupby(["Year", "Scenario"])["Temperature_Anomaly"].mean().unstack().plot()
```

---

## 📜 Citation

If you use this dataset in your work, please credit it as:

```
Climate Change Extended Dataset (1940–2040).
Compiled for research, educational, and AI experimentation purposes.
Future values (2026–2040) represent simulated projections and are
not official scientific forecasts.
```

---

## ⚠️ Disclaimer

> Future values (2026–2040) are **projected/simulated trends** created for research, educational, and analytical purposes only. They should not be interpreted as official scientific forecasts. Always cross-reference with authoritative sources such as [NASA Climate](https://climate.nasa.gov/), [NOAA](https://www.noaa.gov/), or [IPCC Reports](https://www.ipcc.ch/) for policy decisions.

---

## 📬 Contributing & Feedback

Found an issue or have suggestions? Feel free to open an issue or submit a pull request. Contributions that improve data quality, add new features, or extend the projection range are welcome.

---

*Made with 🌱 for a better understanding of our planet's climate future.*

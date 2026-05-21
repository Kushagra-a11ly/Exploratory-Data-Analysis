![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/b1aaba4d4b2e952f1daa57828250bfc2b53e5d14/Global%20Space-A%20Century%20of%20Space%20Missions(1957-2035)/Dataset%20Cover.jpg)
# 🚀 Space Missions Dataset — Exploratory Data Analysis

A comprehensive exploratory data analysis (EDA) of a synthetic space missions dataset spanning 1957–2035, covering mission status, agency performance, launch vehicles, cost distributions, and temporal growth trends.

---

## 📁 Project Structure

```
space-missions-eda/
│
├── Space_Missions_Dataset.csv      # Source dataset
├── eda_analysis.ipynb              # Main analysis notebook
└── README.md                       # Project documentation
```

---

## 📊 Dataset Overview

| Attribute        | Detail                              |
|------------------|--------------------------------------|
| Records          | ~10,500 missions                    |
| Time Span        | 1957 – 2035 (historical + projected)|
| Key Features     | Agency, Status, Destination, Cost, Duration, Crew, Launch Vehicle, Mission Category |
| Data Type        | Synthetic / Balanced                |

### Key Columns

- `Mission_Name`, `Launch_Date`, `End_Date` — Mission identity and timeline
- `Agency`, `Agency_Type`, `Country_Region` — Operator details
- `Status` — Success / Failed / Ongoing / Upcoming / Partial Success
- `Destination`, `Mission_Category` — Target and type classification
- `Launch_Vehicle` — Rocket used
- `Cost_USD_Million` — Mission budget
- `Duration`, `Crew_Members`, `Data_Returned` — Operational metrics
- `Failure_Reason`, `Key_Achievement`, `Partner_Agencies` — Contextual fields

---

## 🧹 Data Cleaning

Missing values were handled as follows:

| Column             | Treatment                     |
|--------------------|-------------------------------|
| `Duration`         | Filled with `0`               |
| `Crew_Members`     | Filled with `0`               |
| `Partner_Agencies` | Filled with `'None'`          |
| `Failure_Reason`   | Filled with `'Successful Mission'` |
| `Key_Achievement`  | Filled with `'Not Specified'` |
| `End_Date`         | Filled with `'Ongoing'`       |
| `Data_Returned`    | Filled with `0`               |

---

## 📈 Analyses Performed

### 1. Mission Status Distribution
- Success (~41%) dominates; ~30% missions are ongoing.
- Failed missions represent ~8.7% of the dataset.

### 2. Agency Mission Counts
- NASA leads (~980 missions), closely followed by SpaceX (~950).
- Private operators (SpaceX, Blue Origin) collectively rival major government agencies.

### 3. Mission Category Distribution
- All 19 categories fall within a narrow ~95-mission band — consistent with balanced synthetic sampling.

### 4. Launch Vehicle Usage
- Ariane 5 holds the largest share (20.2%), followed by Ariane 6 (14.8%) and Falcon 9 (13.8%).

### 5. Mission Cost Distribution
- Median cost ~$7,500M; near-uniform distribution — atypical of real-world cost data.
- Negative values present; data quality flag raised.

### 6. Crew Type Proportion
- 74.9% Uncrewed vs. 25.1% Crewed.
- Crewed proportion (~25%) is significantly elevated vs. real-world rates (~5–8%).

### 7. Top Mission Destinations
- Mercury leads (~598 missions) — a synthetic artefact given only 3 real Mercury missions exist.
- All destinations span a compressed ~40-mission range.

### 8. Mission Growth Over Time
- Flat ~100 missions/year for 60 years (1957–2017), then a 4x surge to ~460 by 2026.
- Sharp post-2026 contraction to ~140 missions may reflect dataset boundary effects.

### 9. Agency Type Contribution
- Government agencies: ~82% | Private operators: ~18%.
- Private share is historically compressed; modern figures (post-2020) would show ~40–60% private.

### 10. Top Countries by Mission Count
- USA leads with ~2,800 missions — nearly 3× the count of the next closest nation.
- Russia, China, Europe, and Japan cluster tightly between ~910–950.

### 11. Mission Cost Trend Over Time
- No meaningful cost trend; values oscillate within $6,500M–$8,500M across all decades.
- Absence of post-2015 cost reduction contradicts real-world commercial spaceflight dynamics.

### 12. Mission Success Rate Over Time
- Stable 0.60–0.82 success rate from 1957–2018.
- Post-2018 collapse to 0.0 is a labelling artefact from unresolved future missions.

### 13. Future Launch Vehicle Demand
- Forecast segments calculated as a fixed ~18–20% uplift on current counts — formulaic rather than demand-driven.

### 14. Agency Cost Efficiency
- ISRO/JAXA ranks most cost-efficient at ~$900M average.
- SpaceX ranks least efficient at ~$7,350M — contradicts real-world pricing.

### 15. Outlier Detection (IQR + Z-Score)
- No outliers detected via standard methods — consistent with the near-uniform cost distribution.

---

## 🔬 Advanced Analysis

```python
# Agency + Mission Category average cost
df.groupby(['Agency_Type', 'Mission_Category'])['Cost_USD_Million'].mean()

# Pivot: Agency Type vs Mission Status
pd.pivot_table(df, values='Cost_USD_Million', index='Agency_Type', columns='Status', aggfunc='mean')

# Failure rate by agency type
pd.crosstab(df['Agency_Type'], df['Status'], normalize='index')

# Outlier detection (IQR)
Q1, Q3 = df['Cost_USD_Million'].quantile([0.25, 0.75])
IQR = Q3 - Q1
outliers = df[(df['Cost_USD_Million'] < Q1 - 1.5*IQR) | (df['Cost_USD_Million'] > Q3 + 1.5*IQR)]

# Z-score method
from scipy.stats import zscore
df['z'] = zscore(df['Cost_USD_Million'].dropna())
df[df['z'] > 3]

# Derived feature
df.eval("Cost_per_Day = Cost_USD_Million / Duration")
```

---

## ⚠️ Dataset Limitations

> This dataset is **synthetic and balanced**. Key deviations from real-world spaceflight data include:

- **Mission destinations** are uniformly distributed — Mercury has as many entries as Earth Orbit.
- **Mission costs** show no inflationary trend and no post-2015 commercial reduction.
- **Crewed mission proportion** (~25%) is ~3–5× higher than historical reality.
- **Success rate** collapses post-2018 due to unresolved future mission labels, not actual failures.
- **Agency rankings** reflect balanced sampling, not true historical launch volumes.

These characteristics make the dataset suitable for **machine learning benchmarking and visualisation practice**, but it should **not** be used to draw conclusions about real-world spaceflight economics or agency performance without external validation.

---

## 🛠️ Dependencies

```
pandas
numpy
matplotlib
seaborn
scikit-learn
scipy
```

Install via:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

---

## 🚀 Getting Started

```python
import pandas as pd
df = pd.read_csv('Space_Missions_Dataset.csv')
df['Launch_Date'] = pd.to_datetime(df['Launch_Date'])
df.info()
```

---

## 📌 Key Takeaways

1. The USA dominates total mission count by a 3:1 margin over all other nations.
2. A structural regime change in annual launch volume began in 2018, driven by commercial megaconstellations.
3. Cost data shows no real trend — uniform distribution confirms synthetic generation.
4. ISRO-linked collaborations represent the most cost-efficient mission profiles.
5. The dataset is best suited for classification modelling and EDA skill-building, not empirical space industry research.

---

## 📄 License

This project is for educational and analytical purposes. Dataset origin: synthetic / generated for practice use.

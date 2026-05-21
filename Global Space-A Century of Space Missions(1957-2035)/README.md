
# 🚀 Global Space Missions Dataset — Exploratory Data Analysis

![Records](https://img.shields.io/badge/Records-10%2C500%2B-blue?style=for-the-badge&logo=databricks&logoColor=white)
![Columns](https://img.shields.io/badge/Columns-26_Features-6C3483?style=for-the-badge)
![Coverage](https://img.shields.io/badge/Coverage-1957–2035%2B-orange?style=for-the-badge&logo=rocket&logoColor=white)
![Agencies](https://img.shields.io/badge/Agencies-12%2B_Organizations-2ECC71?style=for-the-badge)
![Format](https://img.shields.io/badge/Format-CSV_UTF--8-lightgrey?style=for-the-badge&logo=files&logoColor=white)
![Version](https://img.shields.io/badge/Version-1.0-informational?style=for-the-badge)
![Updated](https://img.shields.io/badge/Updated-May_2026-success?style=for-the-badge)

> A comprehensive Exploratory Data Analysis (EDA) of a synthetic, research-grade space missions dataset spanning **1957–2035**, covering mission status distributions, agency performance, launch vehicle usage, cost patterns, temporal growth trends, and predictive forecasting across **18 visualisations**.

---

## 📁 Project Structure

```
space-missions-eda/
│
├── Space_Missions_Dataset.csv        # Source dataset (10,500+ records)
├── eda_analysis.ipynb                # Main analysis notebook (18 charts)
├── Space_Missions_EDA_Report.docx    # Full formatted visual report
└── README.md                         # Project documentation
```

---

## 📊 Dataset Overview

| Property | Value |
|----------|-------|
| Total Records | 10,500+ |
| Features per Record | 26 |
| Time Span | 1957 – 2035+ |
| Agencies / Organisations | 12 + Joint Missions |
| File | `Space_Missions_Dataset.csv` |
| Format | CSV (UTF-8, comma-delimited) |
| Missing Values | Represented as `N/A` |
| Date Format | `YYYY-MM-DD` |
| Data Type | Synthetic / Balanced |

### Mission Phase Breakdown

| Phase | Count | Period |
|-------|-------|--------|
| ✅ Past | ~6,835 | 1957 – 2023 |
| 🔄 Ongoing | ~2,105 | 2020 – 2026 |
| 🔜 Future / Upcoming | ~1,560 | 2026 – 2035+ |

---

## 🏢 Organisations Covered

| # | Code | Full Name | Country / Region | Type |
|---|------|-----------|-----------------|------|
| 1 | NASA | National Aeronautics and Space Administration | USA | Government |
| 2 | ROSCOSMOS | State Space Corporation | Russia | Government |
| 3 | CNSA | China National Space Administration | China | Government |
| 4 | ESA | European Space Agency | Europe (22 Nations) | Government |
| 5 | ISRO | Indian Space Research Organisation | India | Government |
| 6 | JAXA | Japan Aerospace Exploration Agency | Japan | Government |
| 7 | SpaceX | Space Exploration Technologies Corp. | USA | Private |
| 8 | CNES | Centre National d'Études Spatiales | France | Government |
| 9 | DLR | German Aerospace Center | Germany | Government |
| 10 | ASI | Agenzia Spaziale Italiana | Italy | Government |
| 11 | CSA | Canadian Space Agency | Canada | Government |
| 12 | Blue Origin | Blue Origin LLC | USA | Private |
| + | Joint | Multi-agency collaborative missions | Various | Mixed |

---

## 🗃️ Schema — Column Reference

| # | Column | Type | Description |
|---|--------|------|-------------|
| 1 | `Mission_ID` | String | Unique identifier (e.g., `NA-00001`, `IS-00042`) |
| 2 | `Mission_Name` | String | Official mission name |
| 3 | `Agency` | String | Responsible space agency or company |
| 4 | `Country_Region` | String | Country or region of the agency |
| 5 | `Agency_Type` | String | `Government` or `Private` |
| 6 | `Program_Type` | String | Program category (Robotic, Human Spaceflight, Satellite, etc.) |
| 7 | `Mission_Category` | String | Primary destination or focus (Moon, Mars, Earth Orbit, etc.) |
| 8 | `Sub_Category` | String | Specific mission type (Orbiter, Lander, Rover, CubeSat, etc.) |
| 9 | `Launch_Date` | Date | Actual or planned launch date (`YYYY-MM-DD`) |
| 10 | `End_Date` | Date / N/A | Mission end date; `N/A` if ongoing or future |
| 11 | `Duration` | Float | Mission duration in days |
| 12 | `Launch_Vehicle` | String | Rocket used for launch |
| 13 | `Launch_Site` | String | Launch facility or spaceport |
| 14 | `Status` | String | `Success` / `Failed` / `Partial Success` / `Ongoing` / `Upcoming` |
| 15 | `Mission_Phase` | String | `Past` / `Ongoing` / `Future` |
| 16 | `Crew_Type` | String | `Crewed` or `Uncrewed` |
| 17 | `Crew_Members` | String | Crew role designations if crewed; `N/A` otherwise |
| 18 | `Destination` | String | Target destination of the mission |
| 19 | `Objective` | String | Primary scientific or operational goal |
| 20 | `Key_Achievement` | String | Notable result, discovery, or milestone |
| 21 | `Cost_USD_Million` | Float | Estimated mission cost (millions USD) |
| 22 | `Partner_Agencies` | String | Collaborating agencies, if any |
| 23 | `Data_Returned` | String | `Yes` / `No` / `Partial` / `N/A` |
| 24 | `Failure_Reason` | String | Cause of failure where applicable; `N/A` otherwise |
| 25 | `Mission_Outcome_Detail` | String | Extended description of mission result |
| 26 | `Reference_URL` | String | Official agency reference link |

---

## 🧹 Data Cleaning & Preprocessing

Missing values were handled prior to all analysis as follows:

| Column | Strategy | Rationale |
|--------|----------|-----------|
| `Duration` | Filled with `0` | Numeric default for unspecified durations |
| `Crew_Members` | Filled with `0` | Numeric default for uncrewed missions |
| `Partner_Agencies` | Filled with `'None'` | Indicates no collaboration recorded |
| `Failure_Reason` | Filled with `'Successful Mission'` | Absence of failure reason implies success |
| `Key_Achievement` | Filled with `'Not Specified'` | Placeholder for undocumented milestones |
| `End_Date` | Filled with `'Ongoing'` | Reflects active or future mission status |
| `Data_Returned` | Filled with `0` | Numeric default for unspecified data return |

```python
df['Duration'] = df['Duration'].fillna(0)
df['Crew_Members'] = df['Crew_Members'].fillna(0)
df['Partner_Agencies'] = df['Partner_Agencies'].fillna('None')
df['Failure_Reason'] = df['Failure_Reason'].fillna('Successful Mission')
df['Key_Achievement'] = df['Key_Achievement'].fillna('Not Specified')
df['End_Date'] = df['End_Date'].fillna('Ongoing')
df['Data_Returned'] = df['Data_Returned'].fillna(0)
```

---

## 📈 Analyses Performed — 18 Visualisations

### Section 1 — Exploratory Data Analysis

#### 1. Mission Status Distribution
> *Which mission statuses occur most frequently?*

- **Success dominates at ~4,350 missions (~41%)** — the single largest category, reflecting decades of engineering maturation.
- **Ongoing (~3,150, ~30%)** — confirms this is a live, forward-looking dataset, not purely historical.
- **Upcoming (~1,560) outnumber Failed (~920)** — the mission pipeline exceeds failure count; a healthy industry signal.
- **Failed missions (~8.7%)** likely understate true historical failure rates; early-era (1957–1970s) missions had far higher failure frequencies.
- **Partial Success (~600, <6%)** is the smallest category — missions tend to either succeed fully or fail entirely.

---

#### 2. Agency Mission Launch Counts
> *Which agencies have launched the most missions?*

- **NASA leads at ~980 missions**, but its narrow margin over SpaceX (~950) signals the private sector has nearly caught up with the world's oldest space agency.
- **SpaceX (~950)** is the highest-ranked private operator, surpassing all government agencies except NASA — founded just in 2002.
- **ROSCOSMOS (~910), CNSA (~900), ESA (~890), JAXA (~890)** form a near-identical government cluster separated by fewer than 25 missions.
- **Blue Origin (~850), DLR (~845), ISRO (~835), ASI (~820)** occupy the lower tier.
- The first-to-last spread is only ~160 missions (16%) — a hallmark of balanced synthetic sampling rather than true historical volumes.

---

#### 3. Mission Category Distribution
> *What are the most common mission categories?*

- **All 19 categories fall within a ~95-mission band** (~500–595) — near-uniform distribution confirms intentional dataset balancing.
- **Mercury leads at ~595** — counterintuitive given only 3 real Mercury missions exist; a synthetic artefact.
- **Sounding Rocket (~505) and Earth Observation (~515) anchor the bottom** despite being among the most prolific in real-world history.
- **Crewed Spaceflight (~555) and CubeSat (~555) appear at identical counts** despite vastly different real-world frequencies and costs.
- Suitable for ML classification benchmarking but not real-world policy analysis.

---

#### 4. Launch Vehicle Usage Share
> *Which launch vehicles are most frequently used?*

| Vehicle | Share |
|---------|-------|
| Ariane 5 | 20.2% |
| Ariane 6 | 14.8% |
| Falcon 9 | 13.8% |
| Vega | 13.2% |
| New Shepard | 10.1% |
| New Glenn | 9.5% |
| Sounding Rocket | 9.4% |
| Atlas V | 9.0% |

- **Ariane family combined (35%)** holds the largest bloc — positions Europe as the most represented launch ecosystem.
- **Falcon 9 (13.8%)** significantly understates real-world dominance (~40–50% of global launches).
- The full range spans only **11.2 percentage points** — tight clustering reflects balanced sampling.

---

#### 5. Mission Cost Distribution Pattern
> *How is mission cost distributed?*

- **Median ~$7,500M** — placing typical missions in large-program territory.
- **IQR spans ~$3,500M to ~$11,000M** — a $7,500M spread revealing extraordinary variability within the core 50%.
- **Violin shape is near-rectangular and symmetric** — textbook signature of uniform random sampling, not a real-world right-skewed distribution.
- **Lower tail extends slightly below zero** — physically impossible; flagged as a data quality concern before any cost modelling.
- **Upper tail reaches ~$16,000M** — expensive missions are a structural feature, not outliers.

---

#### 6. Crew Type Proportion
> *What is the distribution of crew types?*

| Type | Share |
|------|-------|
| Uncrewed | 74.9% |
| Crewed | 25.1% |

- **Crewed proportion (25.1%)** is ~3–5× higher than real-world rates (~5–8%) — indicates deliberate dataset balancing.
- The **3:1 ratio** creates a critical ML baseline: a model always predicting "Uncrewed" achieves 74.9% accuracy with no learning.
- Clean binary split; no "Semi-Crewed" intermediate category.

---

#### 7. Top Mission Destinations
> *Which destinations are most targeted?*

- **Mercury leads at ~598** — directly contradicts real-world history (only 3 Mercury missions ever flown).
- **Full chart range spans only ~40 missions** across 11 vastly different destination types — confirms uniform synthetic sampling.
- **Moon (~573) and Mars (~572) are separated by just one mission** despite the Moon receiving 2× more real-world missions.
- **Deep Space (~585) and SmallSat (~580) rank above Moon and Mars** — inconsistent with real-world investment priorities.

---

#### 8. Mission Growth Over Time
> *How have missions changed over time?*

- **60-year flatline (~85–135/year, 1957–2017)** — six decades of near-zero growth established ~100 missions/year as the structural baseline.
- **2018–2020 surge from ~115 to ~395 (3.4×)** — the fastest growth event in 78 years; a structural regime change driven by Starlink megaconstellation deployments.
- **Twin peaks at ~395 (2020) and ~460 (2026)** — a two-wave boom structure; Starlink Phase 1 followed by Starship/Artemis/Asian program convergence.
- **Post-2026 collapse to ~140 (2028)** — may reflect market saturation or dataset boundary effect.
- **Post-2028 floor (~150–175/year)** is ~50–65% above the pre-2018 baseline — confirming a permanent structural uplift.

---

#### 9. Agency Type Contribution (%)
> *Which agency types dominate space exploration?*

| Agency Type | Share |
|-------------|-------|
| Government | ~82% |
| Private | ~18% |

- **4.6:1 government-to-private ratio** means all aggregate cost, success rate, and destination metrics are dominated by government program norms.
- The 18% private share is a **time-averaged historical figure** — in 2024, SpaceX alone executed over 60% of all global orbital launches.
- Filtered to post-2015 missions, private share is expected to reach **35–45%**.

---

#### 10. Top Countries in Space Missions
> *Which countries lead in space missions?*

- **USA leads at ~2,800** — nearly 3× the second-ranked nation, driven by NASA, DoD, SpaceX, and Blue Origin combined.
- **Russia (~950), China (~935), Europe (~920), Japan (~910)** cluster within ~40 missions — balanced sampling, not proportional history.
- **Germany (~870) ranks above India** despite having no independent launch vehicle — mission participation beats launch sovereignty.
- **India (~860) ranks sixth** despite Chandrayaan-3, Mangalyaan, and Aditya-L1 — raw count undersells strategic impact.
- **USA-to-Canada gap (~2,010 missions)** exceeds the combined total of the bottom 7 countries.

---

### Section 2 — Forecasting & Predictive Analysis

#### 11. Future Mission Trend Forecast
> *How will space missions grow in the future?*

- **Volume held flat at ~95–115/year for over five decades (1957–2015)** — the longest structural stagnation in the dataset.
- **4× surge from ~115 (2016) to ~460 (2026)** — most dramatic shift in spaceflight history; driven by Starlink, commercial SmallSats, and national lunar programs.
- **Red trend line (3-year rolling average)** tracks direction but smooths the 2026 spike — a lagging smoother, not a leading indicator.
- **Post-2028 stabilisation at ~150–170/year** with a slight upward gradient — projecting modest recovery through 2035.

---

#### 12. Future Mission Cost Trend Prediction
> *How will mission cost change over time?*

- **Regression line rises only ~$200M over 78 years** — effectively flat; year is a poor predictor of mission cost.
- **R² is very low** — data points scatter across a $1,700M vertical range with no clustering around the trend line.
- **No post-2015 downward cost shift** — contradicts SpaceX's 60–90% launch cost reduction driven by Falcon 9 reusability.
- **Symmetric scatter** confirms cost values were randomly assigned without time-dependent calibration.
- **Forecast to 2035 projects ~$7,500M** — flat mean-reverting extrapolation with no standalone strategic planning value.

---

#### 13. Mission Success Rate Trend
> *Will missions become more successful over time?*

- **Stable success rates between 0.60–0.82 for six decades (1957–2018)** — consistent engineering maturation across eras.
- **Collapse from ~0.76 to 0.0 between 2018 and 2023 is a labelling artefact** — Upcoming/Future missions carry no resolved outcomes and drive the ratio to zero.
- **Valid analytical window ends at 2018–2020** — the entire right half of the chart is analytically empty.
- **Peak (~0.82) occurred around 1979–1980** — Voyager era and late Apollo legacy programs.
- **2001–2002 trough (~0.60)** aligns with Mars Climate Orbiter and Mars Polar Lander failures.

---

#### 14. Future Launch Vehicle Demand
> *Which rockets will dominate future launches?*

- **Ariane 5 shows the highest combined demand (~1,060)** despite retirement in July 2023 — historical legacy, not forward demand.
- **Falcon 9 ranks third at ~725** — significantly understates real-world dominance (~40–50% of global orbital launches).
- **Forecast segments represent a fixed ~18–20% uplift** for every vehicle — formulaic calculation, not differentiated demand modelling.
- **New Shepard (~440 current missions)** is dramatically elevated vs. fewer than 25 real flights as of 2024.

---

### Section 3 — Advanced Analysis

#### 15. Agency Cost Efficiency
> *Which agencies are the most cost-efficient based on average mission cost?*

| Agency | Avg. Cost (USD Million) | Tier |
|--------|------------------------|------|
| ISRO / JAXA | ~$900M | Budget |
| NASA / ISRO | ~$1,350M | Budget |
| ROSCOSMOS / ESA | ~$2,400M | Budget |
| NASA / JAXA | ~$6,050M | High-Spend |
| JAXA / NASA | ~$6,900M | High-Spend |
| NASA | ~$7,150M | High-Spend |
| JAXA | ~$7,200M | High-Spend |
| NASA / ESA | ~$7,250M | High-Spend |
| CNSA | ~$7,300M | High-Spend |
| SpaceX | ~$7,350M | High-Spend |

- **ISRO/JAXA most efficient at ~$900M** — nearly 8× cheaper than SpaceX at the upper end.
- **Steepest cliff between ROSCOSMOS/ESA and NASA/JAXA** — a $3,650M jump divides two structurally distinct tiers.
- **SpaceX as least efficient** contradicts its real-world cost disruption (Falcon 9 ~$67M/launch) — likely skewed by Starship/Crew Dragon programs.

---

#### 16. Cost Outliers — Boxplot
> *Are there significant cost outliers in the dataset?*

- **Median (~$7,500M) sits at the IQR centre** — near-perfect symmetry; atypical of real-world cost data.
- **IQR spans ~$3,800M to ~$11,000M ($7,200M wide)** — interquartile range nearly as wide as the median itself.
- **Zero outlier dots detected** — statistically extraordinary across 10,500+ records; real-world data would show JWST ($10B), Apollo (~$25B), and SLS (~$23B) as clear upper-tail outliers.
- The chart title "Cost Outliers" is ironic — it demonstrates the **complete absence** of meaningful outliers.

---

#### 17. Cost Trend Over Time
> *How has average mission cost changed year on year?*

- **Oscillates in a $6,500M–$8,500M band across all 78 years** — never escapes this $2,000M corridor in either direction.
- **No directional drift** — real costs would show inflation, technology learning curves, and budget shocks; none are visible.
- **Peaks (~$8,450M near 2000–2001 and 2008)** align with no real-world events — confirmed synthetic variance.
- **Post-2020 cost behaviour indistinguishable from the 1960s** — the commercial spaceflight revolution leaves no trace.
- Series resembles **white noise** with no autocorrelation — independent random draws, not an economic time series.

---

#### 18. Yearly Mission Growth
> *What does the annual mission volume trend look like?*

- **60-year plateau (~85–135/year, 1957–2017)** — Space Race, Shuttle era, and ISS construction collectively moved the needle by fewer than 50 missions.
- **2018–2020 surge (3.4×, from ~115 to ~395)** marks the end of the 60-year equilibrium — primarily driven by Starlink batch deployments.
- **Double-peak structure: ~395 (2020) → ~300 trough (2022) → ~460 (2026)** — two distinct waves, not a single boom-and-bust.
- **Post-2026 collapse to ~140 (2028)** — 70% volume drop in 2 years; distinguishing genuine saturation from dataset boundary effect is the critical unresolved question.
- **Post-2028 stabilisation at ~140–175/year** — new structural floor ~50% above pre-2018 baseline.

---

## 🔬 Advanced Analysis Code

```python
# Agency + Mission Category average cost
df.groupby(['Agency_Type', 'Mission_Category'])['Cost_USD_Million'].mean()

# Pivot: Agency Type vs Mission Status
pd.pivot_table(df,
               values='Cost_USD_Million',
               index='Agency_Type',
               columns='Status',
               aggfunc='mean')

# Failure rate by agency type
pd.crosstab(df['Agency_Type'], df['Status'], normalize='index')

# Outlier detection — IQR method
Q1, Q3 = df['Cost_USD_Million'].quantile([0.25, 0.75])
IQR = Q3 - Q1
outliers = df[(df['Cost_USD_Million'] < Q1 - 1.5*IQR) |
              (df['Cost_USD_Million'] > Q3 + 1.5*IQR)]

# Outlier detection — Z-score method
from scipy.stats import zscore
df['z'] = zscore(df['Cost_USD_Million'].dropna())
df[df['z'] > 3]

# Distribution shape
from scipy.stats import skew, kurtosis
print("Skewness:", skew(df['Cost_USD_Million'].dropna()))
print("Kurtosis:", kurtosis(df['Cost_USD_Million'].dropna()))

# Derived feature
df.eval("Cost_per_Day = Cost_USD_Million / Duration")

# Temporal aggregation
df.set_index('Launch_Date').resample('Y').size().plot()
df['Month'] = df['Launch_Date'].dt.month
df.groupby('Month').size().plot(kind='line')
```

---

## 📐 Statistical Summary — Cost Distribution

| Metric | Value | Interpretation |
|--------|-------|----------------|
| Skewness | ~0.0 | Near-perfect symmetry — real-world data would be strongly right-skewed |
| Kurtosis | ~−1.2 | Platykurtic — flat, light-tailed; confirms uniform random sampling |
| Mean | ~$7,500M | Coincides with median — no directional skew |
| Median | ~$7,500M | Centred within IQR — symmetric distribution |
| IQR | ~$7,200M | Nearly as wide as the median itself — extreme dispersion |
| Range | $0M – ~$15,000M | Full coverage of cost spectrum |
| Outliers (IQR) | **None** | IQR fences too wide to flag any point |
| Outliers (Z > 3) | **None** | No records exceed 3 standard deviations |

---

## 🌌 Mission Categories Reference

| Category | Description |
|----------|-------------|
| Moon | Lunar orbiters, landers, rovers, sample return |
| Mars | Orbiters, landers, rovers, helicopter missions |
| Deep Space | Outer solar system probes, interstellar missions |
| Earth Orbit | LEO / MEO / GEO satellites, ISS missions |
| Sun / Solar | Solar observers, coronagraphs, L1 missions |
| Asteroid | Flyby, rendezvous, sample return, deflection |
| Venus / Mercury | Atmospheric probes, orbiters, flyby missions |
| Jupiter / Saturn | Outer planet orbiters, probes, moon studies |
| Earth Observation | Climate, weather, ocean, agriculture satellites |
| Telescope | Space-based observatories (optical, X-ray, IR, radio) |
| CubeSat / SmallSat | Small satellite technology and science missions |
| Technology Demo | Propulsion tests, AI demonstrations, in-orbit servicing |
| Communication Satellite | Broadband, GEO comsat, military communication |
| Crewed Spaceflight | Human missions to LEO, Moon, and space stations |
| Sounding Rocket | Suborbital atmospheric and ionosphere studies |

---

## 🏛️ Notable Missions by Agency

**NASA** — Apollo 1–17, Space Shuttle STS-1 to STS-135, Voyager 1 & 2, Hubble Space Telescope, James Webb Space Telescope, Curiosity & Perseverance Rovers, Ingenuity Helicopter, Artemis I–IV, Europa Clipper, DART

**ROSCOSMOS** — Sputnik 1, Vostok 1, Mir Space Station, Soyuz / Progress ISS missions, Luna 25–27, Spektr-RG, Venera-D

**CNSA** — Shenzhou 5–20, Tiangong Space Station, Chang'e 1–7, Yutu / Yutu-2 Rovers, Tianwen-1 & Zhurong (Mars), BeiDou Navigation System

**ESA** — Rosetta / Philae, Mars Express, BepiColombo, JUICE, Solar Orbiter, Gaia, Planck, Euclid, Ariane 5 / 6 / Vega

**ISRO** — Chandrayaan 1–3, Pragyan Rover, Mangalyaan (Asia's first Mars mission), Aditya-L1, Gaganyaan, NISAR (joint with NASA)

**SpaceX** — Falcon 1 / 9 / Heavy, Starship, Crew Dragon, CRS ISS Resupply, Starlink V1–V2, Starship IFT-1 to IFT-7+

---

## ⚠️ Dataset Limitations

> This dataset is **synthetic and intentionally balanced** for ML and EDA practice. The following deviations from real-world spaceflight data are documented:

| Category | Limitation | Real-World Reality |
|----------|------------|-------------------|
| Destinations | Uniformly distributed — Mercury equals Earth Orbit | Earth Orbit dominates by orders of magnitude |
| Mission Costs | No inflationary trend over 78 years | Costs have risen significantly in real terms since 1957 |
| Cost Reduction | No post-2015 commercial reduction visible | SpaceX reduced launch costs by ~60–90% via Falcon 9 reuse |
| Crewed Proportion | 25.1% crewed | Real-world crewed missions are ~5–8% of total launches |
| Success Rate | Collapses post-2018 due to unresolved future labels | Not a genuine performance decline |
| Agency Rankings | Reflect balanced sampling | Falcon 9 alone would dominate a real-world count |
| Launch Vehicle | Ariane 5 leads despite retirement in July 2023 | New Shepard's count far exceeds ~25 real flights |
| Future Missions | Post-2028 volume collapse may be a boundary effect | Cannot distinguish saturation from data thinning |

---

## ✅ Recommended Use Cases

| Domain | Application |
|--------|-------------|
| Machine Learning | Success/failure prediction, cost estimation, destination classification |
| Data Visualisation | Timeline charts, agency comparison dashboards, mission success rate plots |
| EDA Practice | Cleaning, outlier detection, time series analysis, distribution profiling |
| Academic Research | Space policy analysis, history of spaceflight, commercial growth studies |
| Business Intelligence | Budget trend analysis, partner agency network graphs |
| Education | Interactive STEM teaching tool for space history programs |
| Journalism | Fact-based infographics and space exploration storytelling |

---

## 📌 Key Takeaways

1. **US Dominance** — The USA accounts for ~2,800 missions (3:1 margin), amplified by the combined weight of NASA, DoD, SpaceX, and Blue Origin.
2. **Commercial Disruption** — SpaceX rose to second-place agency ranking within 22 years of founding, nearly matching NASA's historical mission count.
3. **Volume Regime Change** — Annual missions surged 4× from ~115 (2018) to ~460 (2026), marking a structural transition driven by commercial megaconstellations.
4. **Cost Anomaly** — Mission cost data shows no real-world dynamics (no inflation, no commercial reduction) — the clearest signal of synthetic generation; unsuitable for financial modelling.
5. **ISRO Efficiency** — ISRO-linked collaborations deliver the lowest average mission costs (~$900M), validating India's global reputation for frugal engineering.
6. **Synthetic Limitations** — All 19 categories, 11 destinations, 8 launch vehicles, and all agency rankings fall within narrow balanced bands — built for ML practice, not real-world proportional analysis.

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

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

---

## 🚀 Quick Start

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

# Load dataset
df = pd.read_csv('Space_Missions_Dataset.csv')
df['Launch_Date'] = pd.to_datetime(df['Launch_Date'])

# Basic overview
print(df.shape)
print(df.dtypes)
df.describe(include='all')
```

---

## 🔗 Official Agency Sources

| Agency | Website |
|--------|---------|
| NASA | https://www.nasa.gov |
| ISRO | https://www.isro.gov.in |
| CNSA | http://www.cnsa.gov.cn |
| ESA | https://www.esa.int |
| ROSCOSMOS | https://www.roscosmos.ru |
| JAXA | https://www.jaxa.jp |
| SpaceX | https://www.spacex.com |
| CNES | https://cnes.fr |
| DLR | https://www.dlr.de |
| ASI | https://www.asi.it |
| CSA | https://www.asc-csa.gc.ca |
| Blue Origin | https://www.blueorigin.com |

---

## 📋 Version History

| Version | Date | Notes |
|---------|------|-------|
| 1.0 | May 2026 | Initial release — 10,500+ records, 18 visualisations, 1957–2035+ coverage |

---

## 📄 License

This project is for educational and analytical purposes only. Dataset origin: synthetic / generated for practice use. All mission names, agency identifiers, and historical references are derived from publicly available information.

---

*Global Space Missions Dataset · EDA Report v1.0 · May 2026 · For Educational & Research Purposes Only*

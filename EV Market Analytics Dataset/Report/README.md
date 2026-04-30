# ⚡ EV Market Analytics

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Dataset](#-dataset)
- [Project Structure](#-project-structure)
- [Analysis Pipeline](#-analysis-pipeline)
  - [Data Loading & Inspection](#1-data-loading--inspection)
  - [Data Cleaning & Exploration](#2-data-cleaning--exploration)
  - [GroupBy & Aggregation](#3-groupby--aggregation)
  - [Feature Engineering](#4-feature-engineering)
  - [Visualizations](#5-visualizations)
- [Key Findings](#-key-findings)
- [Visual Summaries](#-visual-summaries)
- [Strategic Conclusions](#-strategic-conclusions)
- [Technologies Used](#-technologies-used)
- [Getting Started](#-getting-started)
- [Report](#-report)
- [License](#-license)

---

## 🔭 Overview

This project delivers a full end-to-end **Exploratory Data Analysis (EDA)** of the global electric vehicle market. Using a multi-dimensional dataset covering brands, body types, market segments, pricing, performance metrics, and annual sales from **2020 to 2026**, the analysis surfaces actionable insights across:

- **Pricing dynamics** — where the market concentrates, what is missing, and where premium buyers live
- **Brand competition** — which players dominate, which are emerging, and which are barely present
- **Battery & range technology** — what actually determines how far an EV goes
- **Performance vs. price** — whether speed commands a premium
- **Value for money** — which segment gives buyers the most range per dollar

> The project also includes a **full written report** (`EV_Market_Analytics_Report.docx`) with embedded charts, detailed insight narratives, and strategic recommendations for manufacturers, investors, and policymakers.

---

## 📦 Dataset

| Attribute | Detail |
|---|---|
| **File** | `EV Market Analytics Dataset.csv` |
| **Coverage Period** | 2020 – 2026 |
| **Brands Covered** | 20+ (Tesla, BYD, Volkswagen, BMW, Mercedes, Lucid, Porsche, and more) |
| **Body Types** | Sedan · SUV · Truck · Hatchback · Coupe · Van |
| **Market Segments** | Budget · Mid-range · Premium · Luxury |
| **Records** | ~2,000+ vehicle entries |

**Key columns:**

| Column | Description |
|---|---|
| `price_usd` | Vehicle list price in USD |
| `range_miles` | EPA-rated driving range per charge |
| `battery_capacity_kwh` | Battery pack size in kilowatt-hours |
| `charging_speed_kw` | Peak DC fast-charging rate |
| `horsepower` | Peak motor output |
| `torque_nm` | Peak torque in Newton-metres |
| `acceleration_0_60_mph` | 0–60 mph sprint time in seconds |
| `top_speed_mph` | Electronically limited top speed |
| `annual_sales_units` | Units sold in the given year |
| `customer_rating` | Aggregated customer satisfaction score |
| `safety_rating` | NHTSA / NCAP safety score |
| `warranty_years` | Manufacturer warranty duration |
| `market_segment` | Budget / Mid-range / Premium / Luxury classification |
| `body_type` | Vehicle body style |
| `brand` | Manufacturer brand name |
| `year` | Model year of record |

---

## 🗂 Project Structure

```
ev-market-analytics/
│
├── EV Market Analytics Dataset.csv      # Raw input dataset
├── analysis.py                          # Main EDA script
├── EV_Market_Analytics_Report.docx      # Full written report with embedded charts
├── README.md                            # This file
│
└── figures/                             # Exported chart images
    ├── 01_price_distribution.png
    ├── 02_vehicles_by_brand.png
    ├── 03_battery_vs_range.png
    ├── 04_acceleration_vs_price.png
    ├── 05_correlation_matrix.png
    ├── 06_price_by_brand.png
    ├── 07_range_by_body_type.png
    ├── 08_sales_trend.png
    ├── 09_pair_plot.png
    └── 10_value_for_money.png
```

---

## 🔬 Analysis Pipeline

### 1. Data Loading & Inspection

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

# Load the dataset
df = pd.read_csv('EV Market Analytics Dataset.csv')

# Initial inspection
df.head()       # First 5 rows — spot structure and column types at a glance
df.tail()       # Last 5 rows — check for trailing anomalies or truncation
df.shape        # (rows, columns) — understand dataset scale
df.columns      # Full list of feature names
df.info()       # Data types + non-null counts per column
df.describe()   # Summary statistics: mean, std, min, 25%, 50%, 75%, max
df.dtypes       # Per-column dtype confirmation
```

---

### 2. Data Cleaning & Exploration

```python
# Missing Value Detection
df.isnull().sum()
# → Zero nulls confirmed — dataset is complete; no imputation required.

# Categorical Frequency
df['brand'].value_counts()
# → Tesla leads at ~430 entries — 55% more than second-place BYD (~280).

# Distinct Category Values
df['body_type'].unique()
# → ['Sedan', 'SUV', 'Truck', 'Hatchback', 'Coupe', 'Van']
#   6 body styles with consistent labelling — no typos or variants.

# Unique Model Count
df['model'].nunique()
# → High count relative to rows signals rich model diversity across brands.

# Numeric Correlation Matrix
df.corr(numeric_only=True)
# → Key correlations:
#     battery_capacity_kwh  <->  range_miles       r =  0.98
#     horsepower            <->  torque_nm          r =  0.99
#     acceleration_0_60     <->  top_speed_mph      r = -0.97
#     price_usd             <->  horsepower         r =  0.76
#     charging_speed_kw     <->  price_usd          r ~  0.00
```

**Cleaning findings at a glance:**

| Check | Command | Result |
|---|---|---|
| Missing values | `isnull().sum()` | ✅ Zero nulls — no imputation needed |
| Brand distribution | `value_counts()` | Tesla 2× next competitor; long tail beyond Top 10 |
| Body type labels | `unique()` | 6 clean, consistent categories |
| Model diversity | `nunique()` | High unique count confirms broad model coverage |
| Feature correlations | `corr()` | Battery–Range redundant (r = 0.98); charging speed independent |

---

### 3. GroupBy & Aggregation

```python
# Average price per brand
df.groupby('brand')['price_usd'].mean()

# Max range per body type
df.groupby('body_type')['range_miles'].mean()

# Mean annual sales per market segment
df.groupby('market_segment')['annual_sales_units'].mean()

# Multi-column: Brand x Body Type → Price, Range, Rating
df.groupby(['brand', 'body_type']).agg({
    'price_usd': 'mean',
    'range_miles': 'max',
    'customer_rating': 'mean'
})

# Segment-level price statistics
df.groupby('market_segment')['price_usd'].agg(['mean', 'sum'])

# Pivot table: Brand x Body Type → Mean Price
df.pivot_table(values='price_usd', index='brand',
               columns='body_type', aggfunc='mean')

# Cross-tabulation with row-normalised percentages
pd.crosstab(df['body_type'], df['market_segment'])
pd.crosstab(df['body_type'], df['market_segment'], normalize='index')
```

---

### 4. Feature Engineering

```python
# Value-for-money composite metric
df['price_per_mile'] = df['price_usd'] / df['range_miles']
# Budget median: ~$150/mile | Luxury median: ~$480/mile (3.2x gap)

# Range efficiency metric
df.eval('range_efficiency = range_miles / battery_capacity_kwh')
# Identifies vehicles extracting the most range per kWh of battery

# Utility operations
df.sample(5)                       # Random spot-check
df.memory_usage()                  # Memory profile
df.sort_values('price_usd')        # Sort by price ascending
df.query('price_usd > 50000')      # Filter to premium+ vehicles
```

---

### 5. Visualizations

Ten production-quality charts spanning three chart families:

| Family | Charts Included |
|---|---|
| **Distribution** | Price histogram · Brand count bar · Range by body type |
| **Relationship** | Battery vs. Range scatter · Acceleration vs. Price scatter · Pair plot |
| **Comparison** | Correlation heatmap · Price by Brand box · Sales trend line · Value by Segment |

---

## 📊 Key Findings

| # | Metric | Finding | Implication |
|---|---|---|---|
| 1 | 💰 **Price Sweet Spot** | $65K – $75K | Most competitive, densely populated price band |
| 2 | 🏆 **Top Brand by Volume** | Tesla (~430 vehicles) | 55% more records than 2nd-place BYD |
| 3 | 🔋 **Battery–Range Correlation** | r = 0.98 | Battery size dominates range prediction |
| 4 | ⚡ **HP–Torque Correlation** | r = 0.99 | Both variables are effectively interchangeable |
| 5 | 💵 **Best Value Segment** | Budget (~$150/mile) | 3.2× better value per mile than Luxury |
| 6 | 🚫 **Charging Speed** | r ~0.00 with price/range | Priced as an add-on, not a core specification |
| 7 | 📅 **Peak Sales Year** | 2025 (~88M units) | All-time high; 2026 figure likely partial-year |
| 8 | ⚙️ **Strongest Price Driver** | Horsepower & Torque (r = 0.76) | The full performance package sets price |
| 9 | 🏎️ **Speed vs. Price** | No clear linear relationship | High-priced vehicles exist at all acceleration levels |
| 10 | 📦 **Body Type vs. Range** | Median ~255–270 mi across all types | Form factor does not meaningfully determine range |

---

## 📈 Visual Summaries

| # | Chart | One-Line Insight |
|---|---|---|
| 1 | **Price Distribution** | Right-skewed; $65K–$75K is the peak; sub-$30K EVs are underrepresented |
| 2 | **Vehicles by Brand** | Tesla leads by a wide margin; sharp long tail after the Top 10 |
| 3 | **Battery vs. Range** | Near-linear (r = 0.98) across all four market segments |
| 4 | **Acceleration vs. Price** | Speed does not predict price; outliers above $200K exist at every 0–60 level |
| 5 | **Correlation Matrix** | Battery–Range and HP–Torque are each effectively single variables |
| 6 | **Price by Brand** | Lucid and Porsche are ultra-luxury outliers; Honda barely registers |
| 7 | **Range by Body Type** | All six body types share near-identical medians (~255–270 mi) |
| 8 | **Sales Trend 2020–2026** | 18× growth from 2020 to 2025 peak; 2026 dip likely a data artifact |
| 9 | **Pair Plot** | Charging speed uncorrelated with everything; range shows a bimodal hint |
| 10 | **Value for Money** | Budget delivers 3× the range-per-dollar of Luxury; Premium struggles to justify itself |

---

## 🎯 Strategic Conclusions

### Market Structure
The EV market is **strongly bimodal** — a price-sensitive mass market clustered at $40K–$90K, and a thin, high-margin ultra-luxury tier above $150K. The Premium segment faces the greatest strategic pressure and must justify its position through technology differentiation rather than price or brand alone.

### Technology
Battery capacity (r = 0.98) is the single most powerful range predictor. Charging speed is **effectively uncorrelated with all other variables** — suggesting it is treated as an add-on rather than a core specification, and represents a significant differentiation opportunity. Manufacturers seeking value leadership should target **efficiency (miles per kWh)** over raw capacity.

### Brand Strategy
Tesla's inventory dominance and wide price spread signal a deliberate multi-tier strategy. BYD and Volkswagen form a credible second tier. Lucid and Porsche operate as pure luxury plays. Emerging brands — Rivian, Fisker, NIO — remain low-volume and face the twin challenge of scaling production while maintaining quality perception.

### Sales Trajectory
The 2020–2025 growth curve is among the fastest expansions recorded for any major consumer product category, roughly doubling every 18 months. The 2026 dip most likely reflects **partial-year data** rather than genuine market contraction. Policy continuity around incentives and charging infrastructure will determine whether 2025 was a temporary plateau or a permanent ceiling.

---

### Recommendations by Stakeholder

| Stakeholder | Recommendation |
|---|---|
| 🏭 **Manufacturers** | Close the sub-$30K affordability gap to unlock next-wave mass adoption |
| 🏭 **Manufacturers** | Invest in fast-charging standardisation as a product differentiation lever |
| 📈 **Investors** | Prioritise mid-market brands with clear, defensible value propositions |
| 📈 **Investors** | Monitor Lucid and Porsche for ultra-luxury margin expansion signals |
| 🏛️ **Policymakers** | Sustain EV purchase incentives to avoid demand contraction post-2025 |
| 🏛️ **Policymakers** | Fund public charging infrastructure to eliminate the range-anxiety barrier |

---

## 🛠 Technologies Used

| Library | Version | Role |
|---|---|---|
| `pandas` | 2.0+ | Data loading, cleaning, groupby, aggregation, pivot tables |
| `matplotlib` | 3.8+ | Base chart rendering and figure management |
| `seaborn` | 0.13+ | Statistical visualizations (histplot, boxplot, heatmap, pairplot, scatterplot) |
| `numpy` | 1.26+ | Numerical operations and array handling |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10 or higher
- pip package manager

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/your-username/ev-market-analytics.git
cd ev-market-analytics
```

**2. Create a virtual environment** *(recommended)*

```bash
python -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows
```

**3. Install dependencies**

```bash
pip install pandas matplotlib seaborn numpy
```

**4. Add the dataset**

Place `EV Market Analytics Dataset.csv` in the project root directory.

**5. Run the analysis**

```bash
python analysis.py
```

All 10 charts will render inline. To export figures to disk, add the following before each `plt.show()` call:

```python
plt.savefig('figures/filename.png', dpi=150, bbox_inches='tight')
```

---

### Troubleshooting

| Problem | Solution |
|---|---|
| `FileNotFoundError` on CSV load | Confirm the dataset is in the project root, not a subdirectory |
| Blank charts on macOS | Add `import matplotlib; matplotlib.use('TkAgg')` before other imports |
| `corr()` deprecation warning | Pass `numeric_only=True` — already included in this project |
| `ModuleNotFoundError` | Re-run `pip install pandas matplotlib seaborn numpy` in your active environment |

---

## 📄 Report

The full written report (`EV_Market_Analytics_Report.docx`) is structured as follows:

```
EV Market Analytics Report
│
├── Cover Page
├── Executive Summary
│   └── 6-metric findings table
│
├── Data Loading, Cleaning & Exploration
│   ├── Library imports & dataset loading
│   ├── Initial inspection commands (head, tail, shape, info, describe)
│   ├── Cleaning operations (isnull, value_counts, unique, nunique, corr)
│   └── What each step reveals (annotated insight table)
│
├── Chart Analysis — Sections 1 through 10
│   └── Each section: context paragraph · embedded chart · 5 labelled insights
│
└── Conclusions & Strategic Implications
    ├── Market Structure
    ├── Technology Insights
    ├── Brand Strategy
    ├── Sales Trajectory
    └── Recommendations (Manufacturers · Investors · Policymakers)
```

---

## 📜 License

This project is released under the [MIT License](LICENSE).  
The dataset is provided for educational and analytical purposes only.

---

<div align="center">

*Built with Python · Pandas · Seaborn · Matplotlib*

**⭐ If this project was useful, consider giving the repository a star.**

</div>

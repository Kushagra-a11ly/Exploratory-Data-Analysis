# ⚡ EV Market Analytics Dataset — 2020 to 2026

> A complete, realistic, and reproducible Electric Vehicle market dataset covering 2,000 models across 20 global manufacturers — built for price prediction, market analysis, and EV comparison research.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset at a Glance](#dataset-at-a-glance)
- [Column Definitions](#column-definitions)
- [Key Statistics](#key-statistics)
- [Data Characteristics & Realism](#data-characteristics--realism)
- [Use Cases & Analysis Ideas](#use-cases--analysis-ideas)
- [How to Generate the Dataset](#how-to-generate-the-dataset)
- [Data Quality Notes](#data-quality-notes)

---

## Overview

This dataset provides a complete and realistic snapshot of the global Electric Vehicle market from 2020 to 2026. Every record is synthetically generated with deliberate realism — pricing follows brand tier logic, battery and range are physically correlated, performance variants are faster, and customer ratings reflect real-world range anxiety patterns.

It is designed as a drop-in dataset for machine learning pipelines, EDA projects, dashboards, and research presentations — no cleaning required.

| Property | Value |
|---|---|
| **Dataset Size** | 2,000 EV models / variants |
| **Time Period** | 2020 – 2026 |
| **Geographic Coverage** | Global |
| **Manufacturers** | 20 major EV brands |
| **Columns** | 22 |
| **Missing Values** | None |
| **Target Variable** | `price_usd` |
| **Output File** | `ev_market_2026.csv` |
| **Random Seed** | 42 (fully reproducible) |

---

## Dataset at a Glance

```
Rows    : 2,000
Columns : 22
Price   : $25,001 – $199,876  |  Median ~$52,000
Range   : 150 – 450 miles     |  Most 200–350 miles
Battery : 40 – 120 kWh        |  Larger = Premium variants
Rating  : 3.0 – 5.0           |  Average ~4.2
Sales   : 500 – 500K units/yr |  Tesla Model Y leads at 400K–500K
Segment : Budget 25% | Mid-range 40% | Premium 25% | Luxury 10%
```

---

## Column Definitions

### 🪪 Identity

| Column | Type | Range / Values | Description |
|---|---|---|---|
| `brand` | Categorical | 20 brands | Tesla, BYD, Rivian, Lucid, NIO, Hyundai, Kia, BMW, Mercedes, Audi, Volkswagen, Ford, GM/Chevrolet, Toyota, Polestar, Fisker, Porsche, Volvo, Xiaomi, Honda |
| `model` | Categorical | ~5 per brand | Tesla Model 3/Y/S/X/Cybertruck, BYD Seagull/Qin/Atto 3, Rivian R1T/R1S, etc. |
| `year` | Integer | 2020 – 2026 | Model year — weighted toward recent years |
| `variant` | Categorical | 5 types | Base, Standard, Long Range, Performance, Premium |
| `country_of_origin` | Categorical | 6 countries | US, China, Germany, South Korea, Sweden, Japan |

### 💰 Pricing *(Target Variable)*

| Column | Type | Range | Description |
|---|---|---|---|
| `price_usd` | Float | $25K – $200K | **TARGET** — Realistic pricing based on brand, model, variant, and year |
| `market_segment` | Categorical | 4 tiers | Budget, Mid-range, Premium, Luxury |

### 🔋 Battery & Range

| Column | Type | Range | Description |
|---|---|---|---|
| `battery_capacity_kwh` | Float | 40 – 120 kWh | Battery pack size — larger batteries correspond to premium variants |
| `range_miles` | Float | 150 – 450 miles | EPA/WLTP-equivalent range — strongly correlated with battery |
| `charging_speed_kw` | Float | 50 – 350 kW | DC fast charging capability — premium brands reach 200–350 kW |

### ⚡ Performance

| Column | Type | Range | Description |
|---|---|---|---|
| `acceleration_0_60_mph` | Float | 2.0 – 8.0 sec | 0–60 mph time — Performance variants: 2.5–4.5s; Base: 5.0–8.0s |
| `top_speed_mph` | Float | 100 – 200 mph | Maximum vehicle speed |
| `horsepower` | Integer | 150 – 1,000 hp | Total system output |
| `torque_nm` | Integer | 200 – 1,200 Nm | Maximum torque in Newton-metres |
| `drive_type` | Categorical | 3 types | AWD, FWD, RWD |

### 🧍 Practicality

| Column | Type | Range | Description |
|---|---|---|---|
| `seating_capacity` | Integer | 2 – 7 | Number of passenger seats |
| `body_type` | Categorical | 6 types | Sedan, SUV, Truck, Hatchback, Coupe, Van |
| `cargo_volume_cubic_ft` | Float | 15 – 80 cu ft | Boot / cargo space |
| `weight_kg` | Float | 1,500 – 3,000 kg | Vehicle curb weight |

### 📊 Market & Customer

| Column | Type | Range | Description |
|---|---|---|---|
| `safety_rating` | Integer | 3 – 5 stars | NCAP safety rating — most EVs score 4–5 |
| `autopilot_level` | Integer | 0 – 3 | SAE automation level — Tesla/Mercedes reach L2–L3 |
| `annual_sales_units` | Integer | 500 – 500K | Annual production volume |
| `customer_rating` | Float | 3.0 – 5.0 | Satisfaction score — strongly correlated with range |
| `warranty_years` | Integer | 3 – 8 years | Manufacturer warranty — luxury brands vary 3–8 yrs; mass market 3–5 yrs |

---

## Key Statistics

| Metric | Value |
|---|---|
| **Price (min / median / max)** | $25,001 / ~$52,000 / $199,876 |
| **Range (min / max)** | 150 miles / 450 miles |
| **Battery Capacity** | 40 kWh – 120 kWh |
| **Customer Rating (avg)** | ~4.2 out of 5.0 |
| **Top Selling Model** | Tesla Model Y — 400K–500K units/year |
| **Segment Split** | Budget 25% \| Mid-range 40% \| Premium 25% \| Luxury 10% |
| **Year Coverage** | 2024–2026 represents 71% of inventory |

---

## Data Characteristics & Realism

This dataset is synthetically generated but designed to mirror real-world EV market behaviour across every dimension.

**Brand Distribution**
Tesla holds ~20% of records; BYD ~15% — weighted proportionally to actual 2024–2025 global market share. No brand is over- or under-sampled without justification.

**Pricing Logic**
Price is determined by a hierarchy of factors: brand tier → model → variant → year. German luxury brands (BMW, Mercedes, Audi, Porsche) occupy the $50K–$150K band; Tesla is consistent and volume-heavy; Lucid and Porsche anchor the ultra-premium tier.

**Battery–Range Correlation**
`range_miles ≈ battery_capacity_kwh × 3.5 + noise` — this directly mirrors the physics of real EV efficiency. The 0.98 correlation between these two columns is intentional and realistic.

**Performance Variants**
Performance trims achieve 0–60 times of 2.5–4.5 seconds. Base and Standard trims sit at 5.0–8.0 seconds. This creates realistic variance in the acceleration–price scatter.

**Charging Speed Tiers**
Tesla, Lucid, and Porsche offer 200–350 kW DC fast charging. Most other brands sit at 50–150 kW — reflecting real-world infrastructure gaps between premium and mainstream EV ecosystems.

**Range Anxiety Reflected in Ratings**
Customer satisfaction is intentionally correlated with range. Shorter-range vehicles consistently score lower — a pattern well-documented in real consumer surveys and EV ownership studies.

**Automation Levels**
Tesla and Mercedes receive SAE L2–L3 autopilot levels. Most other brands sit at L0–L1, accurately reflecting the current state of the autonomous driving market.

**Year Weighting**
2024–2026 models make up 71% of inventory — consistent with how used and current EV markets are skewed toward recent model years.

---

## Use Cases & Analysis Ideas

### 1. EV Price Prediction *(Primary ML Task)*
Build regression models to predict `price_usd` from vehicle specs.

```python
features = ['battery_capacity_kwh', 'range_miles', 'horsepower', 'brand', 'variant', 'year']
target   = 'price_usd'

# Baseline → Linear Regression
# Then compare → XGBoost, Random Forest, Neural Network
# Metric → MAE on held-out test set
```

### 2. Range vs. Price — Value Analysis
Which EVs deliver the most range per dollar spent?

```python
df['range_per_dollar'] = df['range_miles'] / df['price_usd']
df['price_per_mile']   = df['price_usd']   / df['range_miles']
```
Identify overpriced luxury models vs. underrated budget value picks.

### 3. Brand Comparison Dashboard
Multi-dimensional brand benchmarking across avg price, range, charging speed, customer rating, segment distribution, year-over-year pricing trends, and safety ratings.

### 4. Market Share & Sales Trends (2020–2026)
- Total units sold by brand and year
- Which segment is growing fastest? (Hint: Budget)
- Body type adoption trends over time
- Country of origin market penetration by year

### 5. Battery Technology Evolution
Track year-on-year improvements:
- Average battery capacity per year
- Charging speed improvements
- Range-per-kWh efficiency gains
- Cost-per-kWh trajectory estimate

### 6. Customer Rating Prediction
What drives satisfaction? Feature importance ranking:

| Driver | Strength |
|---|---|
| Range | Strongest |
| Warranty | Strong |
| Charging Speed | Moderate |
| Price-to-Features Ratio | Moderate |
| Safety Rating | Supporting |

### 7. What Specs Actually Drive Sales Volume?
- Do faster 0–60 times increase sales? (Usually not for budget buyers)
- How important is range by price tier?
- Safety rating impact on volume
- Brand loyalty vs. specification-driven purchasing

### 8. Budget EV vs. Luxury — Feature Gap Analysis
Compare the `<$35K` and `>$100K` segments head-to-head:

| Metric | Budget | Luxury |
|---|---|---|
| Range | ~200 miles | ~350 miles |
| Charging Speed | ~80 kW | ~250 kW |
| 0–60 Time | ~6.5 sec | ~3.0 sec |
| Customer Rating | ~3.8 | ~4.6 |

Do these gaps justify the price premium? Where does mid-range close the gap?

---

## How to Generate the Dataset

### Prerequisites

```bash
pip install numpy pandas
```

### Run the Generation Script

```bash
python build_ev_dataset.py
```

### Output

```
ev_market_2026.csv  —  2,000 rows × 22 columns
Execution time      —  < 1 second
Random seed         —  42 (fully reproducible)
```

The script uses `numpy` and `pandas` with seed `42` — every run produces an identical dataset.

---

## Data Quality Notes

| Check | Status |
|---|---|
| Missing values | ✅ None — dataset is fully complete |
| Duplicate records | ✅ None detected |
| Battery ↔ Range correlation | ✅ Realistic (r = 0.98) |
| Price ↔ Specs correlation | ✅ Tier-consistent |
| Brand ↔ Safety / Charging | ✅ Accurately reflected |
| Variant pricing order | ✅ Performance > Long Range > Standard > Base |
| Year weighting | ✅ 2024–2026 = 71% of records |
| Sales realism | ✅ Tesla Model Y dominates; luxury brands are rare |
| Range anxiety effect | ✅ Lower range = lower customer ratings |

---

# 🚗 Indian Used Car Market — Exploratory Data Analysis

> A visual-first EDA uncovering pricing patterns, brand hierarchies, fuel preferences, and feature correlations across 15,000+ used car listings in India.


![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)
![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)

---

## 📌 Project Overview

This project explores the Indian used car market through structured visual analysis — identifying the key drivers of resale value, market segmentation patterns, and feature relationships that inform a downstream pricing model.

**Dataset:** 15,000+ used car listings | **Tools:** Python · Pandas · Matplotlib · Seaborn · Plotly

---

## 📊 EDA Questions & Visual Insights

---

### Q1 — Top 15 Most Common Car Brands

![Top 15 Car Brands]()

**Key Takeaways**
- Maruti dominates with ~5,000 units — nearly **67% more** than second-place Hyundai (~3,000), cementing its position as India's undisputed mass-market leader
- Hyundai and Honda form a strong second tier, reflecting high consumer trust in Korean and Japanese brands
- A sharp drop-off after Honda (~1,500) reveals a fragmented mid-market with no clear challenger to the top three
- European luxury brands (BMW, Mercedes-Benz, Skoda, Audi, Volkswagen) cluster in the lower half — niche players in a price-sensitive market
- Datsun and Jaguar's minimal presence signals limited model offerings and weak brand traction at opposite ends of the spectrum

---

### Q2 — Vehicle Age vs. Selling Price

![Vehicle Age vs Selling Price]()

**Key Takeaways**
- Strong negative correlation between vehicle age and price confirms the expected depreciation curve — 0–5 year vehicles command significantly higher prices
- Extreme outliers (~₹40M, ~₹25M) appear in the 1–4 year range, likely representing high-end luxury vehicles retaining premium valuations
- The widest price spread and highest density fall between 0–10 years — the most active segment of the used car market
- Beyond 10 years, prices compress sharply near zero, indicating rapid value erosion and limited buyer willingness to pay
- A handful of 25–29 year outliers near zero likely represent end-of-life or vintage vehicles with negligible resale value

---

### Q3 — Kilometers Driven vs. Selling Price

![Kilometers Driven vs Selling Price]()

**Key Takeaways**
- Clear inverse relationship — lower-mileage vehicles consistently fetch higher prices, validating mileage as a key depreciation driver
- Highest-priced vehicles (₹25M–₹40M) are concentrated below 50,000 KM — low-mileage luxury cars retain premium value far better than high-usage counterparts
- The majority of listings cluster between 0–200,000 KM, reflecting a younger, well-maintained inventory
- Beyond 500,000 KM, resale prices flatten near zero — high-mileage vehicles have minimal market appeal
- A notable outlier at ~3.8M KM likely represents a data anomaly or commercial vehicle — flagged for treatment before modelling

---

### Q4 — Brands with Highest Average Selling Price

![Average Selling Price by Brand]()

**Key Takeaways**
- Ferrari leads at ~₹40M — nearly **60% higher** than Rolls-Royce (~₹24M), reinforcing its status as the most aspirational brand in the used luxury segment
- A clear three-tier hierarchy emerges: ultra-luxury (Ferrari, Rolls-Royce) → premium luxury (Bentley, Maserati, Porsche, Lexus) → accessible luxury (BMW, Jaguar, Mercedes-Benz, Audi)
- Bentley at ~₹9.5M sits well below Rolls-Royce, suggesting higher depreciation rates or a broader model range skewing its average down
- Mercedes-AMG and Land Rover cluster around ₹4M–₹5M — strong resale positioning in performance and SUV luxury segments
- ISUZU's inclusion flags a potential data quality issue — its average may be inflated by a small number of high-value entries

---

### Q5 — Engine Capacity Distribution

![Engine Capacity Distribution]()

**Key Takeaways**
- Heavily right-skewed with a dominant peak at ~1,200 CC (~5,400 units), consistent with India's price and fuel-efficiency-sensitive consumer base
- A secondary cluster between 1,500–2,500 CC represents mid-range sedans, SUVs, and diesel vehicles
- Two natural market breakpoints appear: after 1,200 CC (economy vs. mid-range) and after 2,500 CC (mid-range vs. premium)
- Engine capacities above 3,000 CC are extremely rare — high ownership costs and limited demand suppress large-displacement vehicles
- The multimodal distribution (spikes at 1,000 / 1,500 / 2,000 / 2,500 CC) reveals standardized sizing across manufacturers

---

### Q6 — Average Engine Capacity by Brand

![Average Engine Capacity by Brand]()

**Key Takeaways**
- Rolls-Royce (~6,500 CC) and Bentley (~6,000 CC) lead by a wide margin — large-displacement engines are central to ultra-luxury brand identity
- Engine size mirrors pricing hierarchy almost perfectly: ultra-luxury at 4,000–6,500 CC vs. mass-market at 1,000–1,200 CC, confirming displacement as a strong proxy for brand positioning
- The 2,500–3,200 CC mid-zone is occupied by performance brands — Porsche, Mercedes-AMG, and Maserati
- Indian domestic brands (Maruti, Tata, Mahindra, Renault) all fall below 2,200 CC, consistent with their affordability-focused product range
- Datsun records the lowest average (~1,050 CC) — the polar opposite of Rolls-Royce

---

### Q7 — Fuel Type Distribution

![Fuel Type Distribution]()

**Key Takeaways**
- Petrol (~7,700) and Diesel (~7,500) dominate almost equally, together accounting for over **95%** of all listings — a long-standing ICE duopoly
- Near-parity suggests balanced consumer preference, with Petrol marginally ahead possibly due to diesel taxation and urban entry restrictions
- CNG (~350) represents a slowly growing niche driven by urban commuters seeking lower running costs
- LPG and Electric vehicles together account for less than 1% of listings — alternative fuel adoption remains nascent
- The near-zero Electric presence is particularly telling: despite growing new EV sales, the used EV market is virtually non-existent

---

### Q8 — Transmission Type Distribution

![Transmission Type Distribution]()

**Key Takeaways**
- Manual (~12,200) overwhelmingly dominates over Automatic (~3,200) at a roughly **80:20 split**, driven by lower purchase cost and cheaper maintenance
- The 4:1 ratio confirms automatics have yet to make a significant dent in used car supply
- Limited Automatic inventory could create a supply-demand imbalance — potentially driving higher resale prices as urban preferences shift
- Manual dominance aligns strongly with the prevalence of small-engine, budget-friendly brands (Maruti, Hyundai, Honda)
- As urbanization and traffic congestion grow, Automatic listings are expected to increase significantly in future datasets

---

### Q9 — Seller Type Distribution

![Seller Type Distribution]()

**Key Takeaways**
- Dealers dominate at ~9,500 listings (~62%), nearly double Individual sellers (~5,700 / 37%), indicating a commercially organized resale ecosystem
- Strong dealer presence reflects the professionalization of India's used car industry through organized players like CarDekho, Cars24, and OLX Autos
- Individual sellers at 37% still represent a significant peer-to-peer channel — preferred by buyers seeking negotiation flexibility and direct ownership history
- Trustmark Dealers account for a negligible ~150 listings (<1%), representing a major untapped opportunity in the quality-certification space
- As consumer awareness around certification grows, Trustmark Dealers could reshape buyer confidence and command pricing premiums

---

### Q10 — Correlation Heatmap (Numeric Features)

![Correlation Heatmap]()

**Key Takeaways**
- Max power (r = 0.75) and engine capacity (r = 0.59) are the strongest positive predictors of selling price — performance specs drive premium valuations more than depreciation factors
- Mileage shows strong negative correlations with engine size (−0.63) and max power (−0.53), revealing a fundamental trade-off between fuel efficiency and performance
- Vehicle age (−0.24) and km driven (−0.08) have surprisingly weak correlations with selling price — a critical signal for feature selection in ML models
- Engine-to-max_power correlation of 0.81 indicates near-multicollinearity — retaining both in a regression risks redundancy and overfitting
- Mileage's negative correlation with seats (−0.44) confirms that compact economy cars cluster at the lower price end

---

### Q11 — Average Selling Price by Brand & Fuel Type

![Average Selling Price by Brand and Fuel Type]()

**Key Takeaways**
- Ferrari Petrol (~₹39.5M) and Rolls-Royce Petrol (~₹24.2M) are extreme outliers — both exclusively petrol-powered, confirming ultra-luxury brands' zero dependency on alternative fuels
- Maserati Diesel (~₹6.1M) and Porsche Diesel (~₹4.78M) are the highest diesel entries, reflecting performance-tuned engines with strong value retention
- Mass-market brands (Maruti, Hyundai, Honda) show multi-fuel presence with prices clustered between ₹188K–₹694K across all fuel types
- Toyota is the only brand with a notable Electric average (~₹1.85M), highlighting an early mover advantage in the hybrid/electric used car space
- LPG is limited to Hyundai (~₹247K) and Maruti (~₹188K) — a budget-driven aftermarket modification losing relevance as CNG expands

---

### Q12 — Engine Capacity Distribution (Detailed)

![Engine Capacity Detailed Distribution]()

**Key Takeaways**
- Sharply right-skewed with a dominant spike at ~1,200 CC (~3,600 frequency) — small-displacement engines are by far the most common
- Distinct spikes at standardized sizes (998, 1197, 1248, 1498, 1968, 2494 CC) reveal manufacturers clustering around displacement milestones to optimize tax brackets and emission norms
- A secondary cluster of spikes between 1,500–2,500 CC represents the mid-range diesel and SUV segment at lower frequencies (~200–550)
- Engine capacities beyond 3,000 CC are extremely sparse — large-displacement vehicles contribute negligible volume to the used car pool
- The discrete, spiky distribution confirms engine capacity is a manufacturer-defined specification — important context for feature engineering

---

### Q13 — Maximum Power Distribution

![Maximum Power Distribution]()

**Key Takeaways**
- Heavily right-skewed with a dominant cluster between 60–100 bhp (~1,800 peak frequency), consistent with budget-brand dominance
- Multiple sharp spikes between 60–150 bhp mirror the engine capacity pattern — max power is also a discrete, manufacturer-defined specification
- A secondary cluster between 150–250 bhp represents performance-oriented mid-range vehicles (SUVs, diesel sedans, entry-level luxury)
- Power outputs beyond 300 bhp are extremely rare — high-performance luxury and sports cars form a negligible-volume but high-value niche
- Max power and engine CC correlate at r = 0.81 — reinforcing the case for using only one in a lean predictive pricing model

---

## 🔑 Summary of Key Findings

| Theme | Finding |
|---|---|
| **Market Structure** | Maruti + Hyundai + Honda hold the mass market; luxury brands are a niche |
| **Price Drivers** | Max power (r=0.75) and engine size (r=0.59) predict price better than age or mileage |
| **Depreciation** | Age and km driven have weaker effects than expected — performance specs matter more |
| **Fuel Landscape** | Petrol/Diesel dominate 95%+ of listings; EVs are virtually absent in used market |
| **Transmission** | Manual at 80% — but Automatic is a growing, potentially under-supplied segment |
| **Seller Ecosystem** | Dealers lead at 62%; Trustmark certification is a major untapped growth area |
| **Feature Engineering** | Engine CC and max power are near-multicollinear (r=0.81) — use one, not both |

---


## 📁 Repository Structure

```
├── data/
│   └── used_cars.csv
├── notebooks/
│   └── eda.ipynb
├── visuals/
│   └── *.png
└── README.md
```

---

*Part of a larger end-to-end project — EDA → Feature Engineering → ML Pricing Model*

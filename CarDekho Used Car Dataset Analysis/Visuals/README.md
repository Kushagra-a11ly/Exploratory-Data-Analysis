# CarDekho Used Car Dataset — Exploratory Data Analysis

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
### Q1. What are the top 15 most common car brands?
![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/0bd7addb8a864e6a7491f4eb92b941bcf3251e29/CarDekho%20Used%20Car%20Dataset%20Analysis/Visuals/1.Top%2015%20Car%20Brands%20by%20Count.png)

**Key Insights:**
- Maruti dominates the Indian car market with ~5,000 units — nearly **67% more** than second-place Hyundai (~3,000), reinforcing its position as the undisputed mass-market leader.
- Hyundai and Honda form a distant but strong second tier, suggesting a competitive mid-range segment where Korean and Japanese brands hold significant consumer trust.
- A sharp drop-off occurs after Honda (~1,500), with Mahindra, Toyota, and Ford clustering around 800–1,050 units, indicating a fragmented mid-market with no clear challenger to the top three.
- European luxury brands (BMW, Mercedes-Benz, Skoda, Audi, Volkswagen) collectively appear in the lower half, reflecting their niche premium positioning in a price-sensitive, value-driven market.
- Datsun and Jaguar's minimal presence signals either weak brand traction or limited model offerings, highlighting the difficulty of sustaining market share at both the budget and ultra-luxury ends of the spectrum.

---

### Q2. How does vehicle age impact the selling price?

![image_alt]()
**Key Insights:**
- A strong negative correlation exists between vehicle age and selling price, confirming the expected depreciation trend — newer vehicles (0–5 years) command significantly higher prices than older ones.
- The most extreme price outliers (~₹40M and ~₹25M) appear in the 1–4 year age range, likely representing luxury or high-end vehicles that retain premium valuations even as used cars.
- The highest price density and widest spread occur between 0–10 years, suggesting this is the most active and competitive segment of the used car market.
- Beyond 10 years, selling prices compress sharply and cluster near zero, indicating rapid value erosion and limited buyer willingness to pay a premium for aging vehicles.
- A few outliers exist at 25–29 years with near-zero prices, likely representing vintage or end-of-life vehicles with negligible resale value.

---

### Q3. Does higher mileage driven reduce the selling price?

![image_alt]()

**Key Insights:**
- A clear inverse relationship exists between kilometers driven and selling price — vehicles with lower mileage consistently fetch higher prices, validating mileage as a key depreciation driver.
- The highest-priced vehicles (₹25M–₹40M) are concentrated below 50,000 KM, suggesting that low-mileage luxury cars retain their premium value far better than high-usage counterparts.
- The majority of data points cluster near 0–200,000 KM, reflecting a younger, well-maintained inventory dominates the market.
- Beyond 500,000 KM, selling prices flatten near zero — high-mileage vehicles have minimal resale appeal.
- A notable outlier at ~3.8M KM likely represents a data anomaly or specialized commercial vehicle, warranting further investigation before modeling.

---

### Q4. Which brands have the highest average selling prices?

![image_alt]()

**Key Insights:**
- Ferrari leads at ~₹40M average selling price, nearly **60% higher** than second-place Rolls-Royce (~₹24M), cementing its status as the most aspirational brand in the used luxury car market.
- A steep three-tier hierarchy is visible — ultra-luxury (Ferrari, Rolls-Royce), premium luxury (Bentley, Maserati, Porsche, Lexus), and accessible luxury (BMW, Jaguar, Mercedes-Benz, Audi).
- Bentley at ~₹9.5M sits significantly below Rolls-Royce, suggesting either higher depreciation rates or a broader model range skewing its average downward.
- Mercedes-AMG and Land Rover cluster around ₹4M–₹5M, showing strong resale positioning in performance and SUV luxury segments.
- ISUZU's surprise inclusion in the top 15 flags a potential data quality issue — its average may be inflated by limited, high-value entries.

---

### Q5. How is engine capacity distributed across the dataset?

![image_alt]()
**Key Insights:**
- The distribution is heavily right-skewed with a dominant peak at ~1,200 CC (~5,400 units), confirming small-engine vehicles dominate — consistent with India's price and fuel-efficiency-sensitive consumer base.
- A secondary cluster is visible between 1,500–2,500 CC, representing mid-range sedans, SUVs, and diesel vehicles.
- Two natural market breakpoints appear: after 1,200 CC (economy vs mid-range) and after 2,500 CC (mid-range vs premium).
- Engine capacities above 3,000 CC are extremely rare, reflecting high ownership costs and limited demand for large-displacement vehicles in India.
- The multimodal distribution (peaks at 1,000, 1,500, 2,000, 2,500 CC) indicates standardized engine sizing across manufacturers.

---

### Q6. Which brands have the highest or lowest average engine capacity?

![image_alt]()
**Key Insights:**
- Rolls-Royce (~6,500 CC) and Bentley (~6,000 CC) lead by a significant margin, reflecting their large-displacement, high-torque engines central to ultra-luxury identity.
- Engine-size hierarchy directly mirrors pricing hierarchy — ultra-luxury brands average 4,000–6,500 CC vs mass-market brands at 1,000–1,200 CC, confirming engine capacity as a strong proxy for brand positioning.
- The 2,500–3,200 CC mid-zone is occupied by performance brands like Porsche, Mercedes-AMG, and Maserati.
- Indian domestic brands (Maruti, Tata, Mahindra, Renault) all fall below 2,200 CC — consistent with their affordability-focused product range.
- Datsun records the lowest average (~1,050 CC), the opposite extreme from Rolls-Royce.

---

### Q7. Which fuel type is most commonly used in cars?

![image_alt]()
**Key Insights:**
- Petrol (~7,700) and Diesel (~7,500) dominate almost equally, together accounting for over **95%** of all listings — a long-standing ICE duopoly.
- The near-parity suggests a balanced consumer preference, with Petrol marginally ahead possibly due to diesel taxation policies and urban entry restrictions.
- CNG vehicles (~350) represent a slowly growing niche, driven by urban commuters seeking lower running costs.
- LPG and Electric vehicles collectively account for less than 1% of listings, highlighting the nascent stage of alternative fuel adoption.
- The near-zero Electric presence is particularly telling — despite growing new EV sales, the used EV market remains virtually non-existent.

---

### Q8. What is the distribution of transmission types?

![image_alt]()
**Key Insights:**
- Manual (~12,200) overwhelmingly dominates over Automatic (~3,200) at a roughly **80:20 split**, driven by lower purchase cost and cheaper maintenance preferences.
- The 4:1 ratio suggests automatic vehicles have yet to make a significant dent in the used car supply chain.
- Limited Automatic inventory (~3,200 units) could create a supply-demand imbalance, potentially driving higher resale prices for automatics as urban preferences shift.
- The manual dominance aligns strongly with the dominance of small-engine, budget-friendly brands (Maruti, Hyundai, Honda).
- As urbanization and traffic congestion grow, Automatic listings are expected to grow significantly in future datasets.

---

### Q9. Which seller type dominates the used car market?

![image_alt]()
**Key Insights:**
- Dealers dominate at ~9,500 listings (~62%), nearly double Individual sellers (~5,700 at ~37%), indicating a highly organized and commercially driven resale ecosystem.
- The strong dealer presence reflects the increasing professionalization of India's used car industry through organized players like CarDekho, Cars24, and OLX Autos.
- Individual sellers at ~37% still represent a significant peer-to-peer channel — preferred by buyers seeking negotiation flexibility and direct ownership history.
- Trustmark Dealers account for a negligible ~150 listings (<1%), representing an enormous untapped growth opportunity in the quality-certification space.
- As consumer awareness grows around certification programs, Trustmark Dealers could reshape buyer confidence and command pricing premiums.

---

### Q10. Are there any strong correlations between numeric features?

![image_alt]()
**Key Insights:**
- Max power (r = 0.75) and engine capacity (r = 0.59) are the strongest positive predictors of selling price, confirming performance specs drive premium valuations more than depreciation factors.
- Mileage shows a strong negative correlation with both engine size (−0.63) and max power (−0.53), revealing a fundamental trade-off between fuel efficiency and performance.
- Vehicle age (−0.24) and km driven (−0.08) have surprisingly weak correlations with selling price — a critical insight for feature selection in ML models.
- The engine-to-max_power correlation (0.81) indicates near-multicollinearity — retaining both in a regression model risks redundancy and overfitting.
- Mileage's negative correlation with seats (−0.44) confirms that compact economy cars (small, fuel-efficient, fewer seats) cluster at the lower price end.

---

### Q11. How does average selling price vary by brand and fuel type?

![image_alt]()
**Key Insights:**
- Ferrari Petrol (~₹39.5M) and Rolls-Royce Petrol (~₹24.2M) are extreme high-value outliers — both exclusively petrol-powered, confirming ultra-luxury brands' zero dependency on alternative fuels.
- Maserati Diesel (~₹6.1M) and Porsche Diesel (~₹4.78M) are the highest diesel-priced entries, reflecting performance-tuned diesel engines with strong value retention.
- Mass-market brands (Maruti, Hyundai, Honda) show multi-fuel presence with prices clustered between ₹188K–₹694K across all fuel types.
- Toyota is the only brand with a notable Electric average (~₹1.85M), highlighting its early mover advantage in the hybrid/electric used car space.
- LPG is limited to Hyundai (~₹247K) and Maruti (~₹188K) — suggesting LPG is a budget-driven aftermarket modification losing relevance as CNG expands.

---

### Q12. How are engine capacities distributed (detailed)?
![image_alt]()

**Key Insights:**
- The distribution is sharply right-skewed with a dominant spike at ~1,200 CC (~3,600 frequency), confirming small-displacement engines are by far the most common.
- Multiple distinct spikes at standardized sizes (998, 1197, 1248, 1498, 1968, 2494 CC) reveal manufacturers clustering around specific displacement milestones to optimize tax brackets and emission norms.
- A secondary cluster of spikes between 1,500–2,500 CC represents the mid-range diesel and SUV segment at lower frequencies (~200–550).
- Engine capacities beyond 3,000 CC are extremely sparse — large-displacement vehicles contribute negligible volume to the used car pool.
- The spiky, discrete nature of the distribution underscores that engine capacity is a manufacturer-defined specification — important for feature engineering in ML models.

---

### Q13. What is the distribution of maximum power values?


![image_alt]()

**Key Insights:**
- The distribution is heavily right-skewed with a dominant cluster between 60–100 bhp (~1,800 peak frequency), consistent with budget-friendly brand dominance.
- Multiple sharp spikes between 60–150 bhp mirror the engine capacity pattern — max power is also a discrete, manufacturer-defined specification.
- A secondary cluster between 150–250 bhp represents performance-oriented mid-range vehicles (SUVs, diesel sedans, entry-level luxury cars).
- Power outputs beyond 300 bhp are extremely rare, isolating high-performance luxury and sports cars as a negligible-volume but high-value niche.
- Max power and engine CC are highly correlated (r = 0.81) — reinforcing the case for using only one in a lean predictive pricing model.

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

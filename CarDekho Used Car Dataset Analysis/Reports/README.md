# 🚗 CarDekho Used Car Dataset — Exploratory Data Analysis (EDA)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.24%2B-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7%2B-11557c?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12%2B-4c72b0?style=for-the-badge)
![SciPy](https://img.shields.io/badge/SciPy-1.10%2B-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Domain](https://img.shields.io/badge/Domain-Automotive%20%7C%20India-orange?style=for-the-badge)
![Analysis](https://img.shields.io/badge/Analysis-EDA-purple?style=for-the-badge)
![ML Ready](https://img.shields.io/badge/ML-Price%20Prediction%20Ready-red?style=for-the-badge&logo=scikit-learn&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

---

## 📋 Table of Contents

1. [Executive Summary](#-executive-summary)
2. [Market Context](#-market-context)
3. [Market Structure](#-market-structure-a-dual-segment-reality)
4. [Key Pricing Drivers](#-key-pricing-drivers)
5. [Market Composition](#-market-composition-highlights)
6. [Dataset Overview](#-dataset-overview)
7. [Feature Reference](#-feature-reference)
8. [Project Structure](#-project-structure)
9. [EDA Questions & Key Insights](#-eda-questions--key-insights)
10. [Outlier Detection & Statistical Analysis](#-outlier-detection--statistical-analysis)
11. [Key Takeaways](#-key-takeaways)
12. [Next Steps & Recommendations](#-next-steps--recommendations)
13. [Conclusion](#-conclusion)

---

## 🎯 Executive Summary

This report presents a comprehensive Exploratory Data Analysis (EDA) of the **CarDekho Used Car Dataset**, encompassing over **15,000 used car listings** from India's dynamic secondary automobile market. Sourced from CarDekho — one of India's largest automotive platforms — the dataset spans a wide spectrum of vehicles, from entry-level hatchbacks priced below ₹200,000 to ultra-luxury supercars commanding upwards of ₹40 million. The analysis investigates **13 structured business questions** across six analytical dimensions: brand distribution, pricing dynamics, engine specifications, fuel preferences, transmission patterns, and seller channel behavior.

| Metric | Value |
|---|---|
| Total Listings | 15,000+ |
| Dataset Features | 12 |
| EDA Questions Answered | 13 |
| Fuel Types Covered | 5 |
| Brands Analysed | 30+ |
| Strongest Price Predictor | Max Power (r = 0.75) |
| Engine–Power Correlation | r = 0.81 (near-multicollinear) |
| Petrol + Diesel Share | ~95% of all listings |
| Manual Transmission Share | ~80% of all listings |
| Dealer Listing Share | ~62% of all listings |

---

## 🌍 Market Context

India's used car market is one of the **fastest-growing in the world**, with an estimated transaction volume exceeding **4 million vehicles annually**. The market has undergone rapid formalization over the past decade, driven by the rise of organized platforms such as CarDekho, Cars24, and OLX Autos.

Unlike mature Western markets where depreciation and mileage are the primary valuation anchors, the Indian used car ecosystem is shaped by a unique interplay of:

- Price sensitivity and affordability thresholds
- Fuel economy consciousness (kmpl as a purchase criterion)
- Brand perception and trust
- Engine performance specifications (increasingly dominant)

This dataset captures that complexity — presenting a market where Maruti's 800cc hatchbacks coexist alongside Rolls-Royce V12s, and where manual transmission still commands an **80% market share** despite rising urbanization. Understanding these structural dynamics is essential not only for accurate price prediction but also for strategic decision-making by **dealers, insurers, and OEM remarketing arms**.

---

## 🏗️ Market Structure: A Dual-Segment Reality

The most defining structural characteristic of this dataset is its pronounced **dual-segment nature**. Two distinct and economically divergent markets coexist within the same platform:

### Mass-Market Tier (~90%+ of dataset)

| Attribute | Detail |
|---|---|
| Brands | Maruti, Hyundai, Honda, Mahindra, Toyota, Ford |
| Volume | ~13,500+ listings |
| Price Range | ₹150,000 – ₹1,500,000 |
| Engine | 800 CC – 1,500 CC (typical) |
| Transmission | Predominantly Manual |
| Fuel | Multi-fuel (Petrol, Diesel, CNG) |
| Buyer Profile | Cost-sensitive urban & semi-urban buyers |
| Key Insight | High volume but narrow price band — strong competition on value |

### Luxury Tier (<5% of dataset)

| Attribute | Detail |
|---|---|
| Brands | Ferrari, Rolls-Royce, Bentley, Maserati, Porsche |
| Volume | ~300–500 listings |
| Price Range | ₹2,500,000 – ₹40,000,000+ |
| Engine | 3,000 CC – 6,750 CC (typical) |
| Transmission | Predominantly Automatic |
| Fuel | Exclusively Petrol |
| Buyer Profile | Ultra-high-net-worth individuals (UHNIs) |
| Key Insight | Extreme price outliers — require separate modeling treatment |

---

## 📈 Key Pricing Drivers

A central finding of this analysis is that the traditional used car valuation model — anchored in depreciation via vehicle age and kilometers driven — **does not hold** in this dataset with the expected strength. Instead, **performance-oriented technical specifications** emerge as the dominant price predictors:

| Feature | Correlation (r) | Strength | What This Means |
|---|---|---|---|
| `max_power` | +0.75 | ★★★ Strong | Strongest single predictor — buyers pay a clear premium for higher BHP output |
| `engine` (CC) | +0.59 | ★★★ Strong | Large-displacement engines signal luxury and performance; strongly priced in |
| `seats` | +0.12 | ★ Weak | Marginal positive — larger vehicles (SUVs) command modest premiums |
| `mileage` (kmpl) | −0.31 | ★★ Moderate | Fuel-efficient cars are typically smaller and cheaper — inverse relationship |
| `vehicle_age` | −0.24 | ★★ Moderate | Newer cars fetch more, but the effect is weaker than performance specs |
| `km_driven` | −0.08 | ★ Very Weak | Surprisingly weak — mileage is a poor price signal in this market |

> ⚠️ **Critical Modeling Note:** The near-multicollinearity between `max_power` and `engine CC` (r = 0.81) is a critical modeling consideration — retaining both features in a regression model risks redundancy and inflated variance. Feature selection or dimensionality reduction (e.g., PCA) is strongly advised.

---

## 📊 Market Composition Highlights

### Fuel Type Split

| Fuel Type | Count | Share | Note |
|---|---|---|---|
| Petrol | ~7,700 | ~49% | Marginal leader |
| Diesel | ~7,500 | ~48% | Near-parity with Petrol |
| CNG | ~350 | ~2% | Growing urban segment |
| LPG | <100 | <1% | Aftermarket modification only |
| Electric | <50 | <0.1% | Nascent used EV market |

> ICE (Internal Combustion Engine) duopoly is overwhelming at **97%+** of all listings.

### Transmission & Seller Split

| Category | Count | Share |
|---|---|---|
| Manual Transmission | ~12,200 | ~79% |
| Automatic Transmission | ~3,200 | ~21% |
| Dealer Listings | ~9,500 | ~62% |
| Individual Seller Listings | ~5,700 | ~37% |
| Trustmark Dealer Listings | ~150 | <1% |

> Dealer dominance at **62%** signals significant market formalization and professionalization.

---

## 📌 Dataset Overview

| Property | Details |
|---|---|
| Source | CarDekho Used Car Marketplace |
| Domain | Automotive / Used Car Market — India |
| Primary Use Case | Used Car Price Prediction (Supervised Regression) |
| Format | CSV |
| Total Features | 12 (7 Numerical, 5 Categorical) |
| Target Variable | `selling_price` (INR) |

---

## 🧾 Feature Reference

| # | Feature | Type | Description |
|---|---|---|---|
| 1 | `car_name` | Categorical | Full name of the car including brand and specific model |
| 2 | `brand` | Categorical | Brand name of the car |
| 3 | `model` | Categorical | Exact model name of the car under a particular brand |
| 4 | `seller_type` | Categorical | Type of seller (Individual / Dealer / Trustmark Dealer) |
| 5 | `fuel_type` | Categorical | Fuel type (Petrol / Diesel / CNG / LPG / Electric) |
| 6 | `transmission_type` | Categorical | Transmission type (Manual / Automatic) |
| 7 | `vehicle_age` | Numerical | Number of years since the car was originally purchased |
| 8 | `mileage` | Numerical | Fuel efficiency in km per litre (kmpl) |
| 9 | `engine` | Numerical | Engine displacement capacity in CC (cubic centimeters) |
| 10 | `max_power` | Numerical | Maximum power output in BHP |
| 11 | `seats` | Numerical | Total seating capacity in the car |
| 12 | `selling_price` | Numerical | 🎯 **Target** — listed sale price on the platform (INR) |

---

## 📁 Project Structure

```
📦 CarDekho-EDA
 ┣ 📂 data
 ┃ ┗ 📄 CarDekho Used Car Dataset.csv
 ┣ 📂 notebooks
 ┃ ┗ 📓 CarDekho_EDA.ipynb
 ┣ 📂 visuals
 ┃ ┣ 🖼️ q1_brand_count.png
 ┃ ┣ 🖼️ q2_vehicle_age_vs_price.png
 ┃ ┣ 🖼️ q3_km_driven_vs_price.png
 ┃ ┣ 🖼️ q4_avg_price_by_brand.png
 ┃ ┣ 🖼️ q5_engine_distribution.png
 ┃ ┣ 🖼️ q6_engine_by_brand.png
 ┃ ┣ 🖼️ q7_fuel_type.png
 ┃ ┣ 🖼️ q8_transmission_type.png
 ┃ ┣ 🖼️ q9_seller_type.png
 ┃ ┣ 🖼️ q10_correlation_heatmap.png
 ┃ ┣ 🖼️ q11_brand_fuel_heatmap.png
 ┃ ┣ 🖼️ q12_engine_capacity_detail.png
 ┃ ┗ 🖼️ q13_max_power_distribution.png
 ┣ 📄 README.md
 ┗ 📄 CarDekho_EDA_Report.docx
```

---

## 📦 Libraries Used

```python
import pandas as pd                          # Data manipulation & analysis
import numpy as np                           # Numerical computing
import matplotlib.pyplot as plt              # Core plotting
import seaborn as sns                        # Statistical visualizations
from scipy.stats import zscore, skew, kurtosis  # Statistical analysis
```

**Install all dependencies:**

```bash
pip install pandas numpy matplotlib seaborn scipy
```

---

## 📊 EDA Questions & Key Insights

---

### Q1. What are the top 15 most common car brands?

**Key Insights:**
- Maruti dominates the Indian car market with ~5,000 units — nearly **67% more** than second-place Hyundai (~3,000), reinforcing its position as the undisputed mass-market leader.
- Hyundai and Honda form a distant but strong second tier, suggesting a competitive mid-range segment where Korean and Japanese brands hold significant consumer trust.
- A sharp drop-off occurs after Honda (~1,500), with Mahindra, Toyota, and Ford clustering around 800–1,050 units, indicating a fragmented mid-market with no clear challenger to the top three.
- European luxury brands (BMW, Mercedes-Benz, Skoda, Audi, Volkswagen) collectively appear in the lower half, reflecting their niche premium positioning in a price-sensitive, value-driven market.
- Datsun and Jaguar's minimal presence signals either weak brand traction or limited model offerings, highlighting the difficulty of sustaining market share at both the budget and ultra-luxury ends of the spectrum.

---

### Q2. How does vehicle age impact the selling price?

**Key Insights:**
- A strong negative correlation exists between vehicle age and selling price, confirming the expected depreciation trend — newer vehicles (0–5 years) command significantly higher prices than older ones.
- The most extreme price outliers (~₹40M and ~₹25M) appear in the 1–4 year age range, likely representing luxury or high-end vehicles that retain premium valuations even as used cars.
- The highest price density and widest spread occur between 0–10 years, suggesting this is the most active and competitive segment of the used car market.
- Beyond 10 years, selling prices compress sharply and cluster near zero, indicating rapid value erosion and limited buyer willingness to pay a premium for aging vehicles.
- A few outliers exist at 25–29 years with near-zero prices, likely representing vintage or end-of-life vehicles with negligible resale value.

---

### Q3. Does higher mileage driven reduce the selling price?

**Key Insights:**
- A clear inverse relationship exists between kilometers driven and selling price — vehicles with lower mileage consistently fetch higher prices, validating mileage as a key depreciation driver.
- The highest-priced vehicles (₹25M–₹40M) are concentrated below 50,000 KM, suggesting that low-mileage luxury cars retain their premium value far better than high-usage counterparts.
- The majority of data points cluster near 0–200,000 KM, reflecting a younger, well-maintained inventory dominates the market.
- Beyond 500,000 KM, selling prices flatten near zero — high-mileage vehicles have minimal resale appeal.
- A notable outlier at ~3.8M KM likely represents a data anomaly or specialized commercial vehicle, warranting further investigation before modeling.

---

### Q4. Which brands have the highest average selling prices?

**Key Insights:**
- Ferrari leads at ~₹40M average selling price, nearly **60% higher** than second-place Rolls-Royce (~₹24M), cementing its status as the most aspirational brand in the used luxury car market.
- A steep three-tier hierarchy is visible — ultra-luxury (Ferrari, Rolls-Royce), premium luxury (Bentley, Maserati, Porsche, Lexus), and accessible luxury (BMW, Jaguar, Mercedes-Benz, Audi).
- Bentley at ~₹9.5M sits significantly below Rolls-Royce, suggesting either higher depreciation rates or a broader model range skewing its average downward.
- Mercedes-AMG and Land Rover cluster around ₹4M–₹5M, showing strong resale positioning in performance and SUV luxury segments.
- ISUZU's surprise inclusion in the top 15 flags a potential data quality issue — its average may be inflated by limited, high-value entries.

---

### Q5. How is engine capacity distributed across the dataset?

**Key Insights:**
- The distribution is heavily right-skewed with a dominant peak at ~1,200 CC (~5,400 units), confirming small-engine vehicles dominate — consistent with India's price and fuel-efficiency-sensitive consumer base.
- A secondary cluster is visible between 1,500–2,500 CC, representing mid-range sedans, SUVs, and diesel vehicles.
- Two natural market breakpoints appear: after 1,200 CC (economy vs mid-range) and after 2,500 CC (mid-range vs premium).
- Engine capacities above 3,000 CC are extremely rare, reflecting high ownership costs and limited demand for large-displacement vehicles in India.
- The multimodal distribution (peaks at 1,000, 1,500, 2,000, 2,500 CC) indicates standardized engine sizing across manufacturers.

---

### Q6. Which brands have the highest or lowest average engine capacity?

**Key Insights:**
- Rolls-Royce (~6,500 CC) and Bentley (~6,000 CC) lead by a significant margin, reflecting their large-displacement, high-torque engines central to ultra-luxury identity.
- Engine-size hierarchy directly mirrors pricing hierarchy — ultra-luxury brands average 4,000–6,500 CC vs mass-market brands at 1,000–1,200 CC, confirming engine capacity as a strong proxy for brand positioning.
- The 2,500–3,200 CC mid-zone is occupied by performance brands like Porsche, Mercedes-AMG, and Maserati.
- Indian domestic brands (Maruti, Tata, Mahindra, Renault) all fall below 2,200 CC — consistent with their affordability-focused product range.
- Datsun records the lowest average (~1,050 CC), the opposite extreme from Rolls-Royce.

---

### Q7. Which fuel type is most commonly used in cars?

**Key Insights:**
- Petrol (~7,700) and Diesel (~7,500) dominate almost equally, together accounting for over **95%** of all listings — a long-standing ICE duopoly.
- The near-parity suggests a balanced consumer preference, with Petrol marginally ahead possibly due to diesel taxation policies and urban entry restrictions.
- CNG vehicles (~350) represent a slowly growing niche, driven by urban commuters seeking lower running costs.
- LPG and Electric vehicles collectively account for less than 1% of listings, highlighting the nascent stage of alternative fuel adoption.
- The near-zero Electric presence is particularly telling — despite growing new EV sales, the used EV market remains virtually non-existent.

---

### Q8. What is the distribution of transmission types?

**Key Insights:**
- Manual (~12,200) overwhelmingly dominates over Automatic (~3,200) at a roughly **80:20 split**, driven by lower purchase cost and cheaper maintenance preferences.
- The 4:1 ratio suggests automatic vehicles have yet to make a significant dent in the used car supply chain.
- Limited Automatic inventory (~3,200 units) could create a supply-demand imbalance, potentially driving higher resale prices for automatics as urban preferences shift.
- The manual dominance aligns strongly with the dominance of small-engine, budget-friendly brands (Maruti, Hyundai, Honda).
- As urbanization and traffic congestion grow, Automatic listings are expected to grow significantly in future datasets.

---

### Q9. Which seller type dominates the used car market?

**Key Insights:**
- Dealers dominate at ~9,500 listings (~62%), nearly double Individual sellers (~5,700 at ~37%), indicating a highly organized and commercially driven resale ecosystem.
- The strong dealer presence reflects the increasing professionalization of India's used car industry through organized players like CarDekho, Cars24, and OLX Autos.
- Individual sellers at ~37% still represent a significant peer-to-peer channel — preferred by buyers seeking negotiation flexibility and direct ownership history.
- Trustmark Dealers account for a negligible ~150 listings (<1%), representing an enormous untapped growth opportunity in the quality-certification space.
- As consumer awareness grows around certification programs, Trustmark Dealers could reshape buyer confidence and command pricing premiums.

---

### Q10. Are there any strong correlations between numeric features?

**Key Insights:**
- Max power (r = 0.75) and engine capacity (r = 0.59) are the strongest positive predictors of selling price, confirming performance specs drive premium valuations more than depreciation factors.
- Mileage shows a strong negative correlation with both engine size (−0.63) and max power (−0.53), revealing a fundamental trade-off between fuel efficiency and performance.
- Vehicle age (−0.24) and km driven (−0.08) have surprisingly weak correlations with selling price — a critical insight for feature selection in ML models.
- The engine-to-max_power correlation (0.81) indicates near-multicollinearity — retaining both in a regression model risks redundancy and overfitting.
- Mileage's negative correlation with seats (−0.44) confirms that compact economy cars (small, fuel-efficient, fewer seats) cluster at the lower price end.

---

### Q11. How does average selling price vary by brand and fuel type?

**Key Insights:**
- Ferrari Petrol (~₹39.5M) and Rolls-Royce Petrol (~₹24.2M) are extreme high-value outliers — both exclusively petrol-powered, confirming ultra-luxury brands' zero dependency on alternative fuels.
- Maserati Diesel (~₹6.1M) and Porsche Diesel (~₹4.78M) are the highest diesel-priced entries, reflecting performance-tuned diesel engines with strong value retention.
- Mass-market brands (Maruti, Hyundai, Honda) show multi-fuel presence with prices clustered between ₹188K–₹694K across all fuel types.
- Toyota is the only brand with a notable Electric average (~₹1.85M), highlighting its early mover advantage in the hybrid/electric used car space.
- LPG is limited to Hyundai (~₹247K) and Maruti (~₹188K) — suggesting LPG is a budget-driven aftermarket modification losing relevance as CNG expands.

---

### Q12. How are engine capacities distributed (detailed)?

**Key Insights:**
- The distribution is sharply right-skewed with a dominant spike at ~1,200 CC (~3,600 frequency), confirming small-displacement engines are by far the most common.
- Multiple distinct spikes at standardized sizes (998, 1197, 1248, 1498, 1968, 2494 CC) reveal manufacturers clustering around specific displacement milestones to optimize tax brackets and emission norms.
- A secondary cluster of spikes between 1,500–2,500 CC represents the mid-range diesel and SUV segment at lower frequencies (~200–550).
- Engine capacities beyond 3,000 CC are extremely sparse — large-displacement vehicles contribute negligible volume to the used car pool.
- The spiky, discrete nature of the distribution underscores that engine capacity is a manufacturer-defined specification — important for feature engineering in ML models.

---

### Q13. What is the distribution of maximum power values?

**Key Insights:**
- The distribution is heavily right-skewed with a dominant cluster between 60–100 bhp (~1,800 peak frequency), consistent with budget-friendly brand dominance.
- Multiple sharp spikes between 60–150 bhp mirror the engine capacity pattern — max power is also a discrete, manufacturer-defined specification.
- A secondary cluster between 150–250 bhp represents performance-oriented mid-range vehicles (SUVs, diesel sedans, entry-level luxury cars).
- Power outputs beyond 300 bhp are extremely rare, isolating high-performance luxury and sports cars as a negligible-volume but high-value niche.
- Max power and engine CC are highly correlated (r = 0.81) — reinforcing the case for using only one in a lean predictive pricing model.

---

## 🔎 Outlier Detection & Statistical Analysis

### Outlier Detection Methods

Two complementary methods were applied to detect extreme outliers in the `selling_price` distribution:

| Method | Approach | Treatment Recommendation |
|---|---|---|
| **Z-Score** | Flag records with \|z\| > 3 standard deviations from the mean price | Log-transform `selling_price`; cap or segment luxury brands above ₹10M |
| **IQR** | Flag records outside Q1 − 1.5×IQR to Q3 + 1.5×IQR price range | Remove or Winsorize extreme values; train separate model for luxury segment |

> Both methods consistently flag **Ferrari, Rolls-Royce, and Bentley** as high-end outliers. These should be treated carefully during ML model preprocessing.

### Statistical Properties of Selling Price

| Statistic | Observed Value | Implication for Modeling |
|---|---|---|
| Skewness | High Positive | Most cars are low-priced; a few extreme luxury outliers pull the mean upward |
| Kurtosis | High (Leptokurtic) | Heavy-tailed distribution; outliers exert disproportionate statistical influence |
| Distribution Shape | Right-skewed | Log transformation of `selling_price` strongly recommended before model training |
| Outlier Brands | Ferrari, Rolls-Royce, Bentley | Consider segmenting luxury vs mass-market models or applying log/cap treatment |

### Analytical Implications & Modeling Recommendations

The following preprocessing steps are recommended before any supervised regression model is trained:

1. **Log-transform `selling_price`** — The target variable's extreme right skew violates normality assumptions of linear models. A log or Box-Cox transformation will substantially improve model fit and residual behavior.
2. **Outlier segmentation** — Ultra-luxury brands (Ferrari, Rolls-Royce, Bentley, Porsche, Maserati) represent a statistically distinct population. Consider training separate models for the luxury segment (>₹5M) and the mass-market segment (<₹5M) to avoid cross-segment distortion.
3. **Feature selection for multicollinearity** — `engine CC` and `max_power` share a correlation of 0.81. Use VIF analysis and retain only `max_power` (r = 0.75 with price) or apply PCA to create a composite performance feature.
4. **Encode categorical features carefully** — `seller_type`, `fuel_type`, `transmission_type`, and `brand` require encoding. For `brand`, target encoding (mean price per brand) may outperform one-hot encoding given large cardinality.
5. **Missing value imputation** — `mileage`, `engine`, `max_power`, and `seats` contain null values that must be imputed (median for numerical, mode for categorical) before modeling.

---

## 💡 Key Takeaways

| # | Finding | Implication |
|---|---|---|
| 1 | **Maruti dominates** | Most listed brand — India's undisputed mass-market used car choice |
| 2 | **Max Power (r = 0.75)** | Strongest predictor of selling price — performance specs matter most |
| 3 | **Engine CC (r = 0.59)** | Second strongest predictor; highly collinear with Max Power (r = 0.81) |
| 4 | **Vehicle Age (r = −0.24)** | Weak price predictor — performance specs outweigh depreciation factors |
| 5 | **Petrol + Diesel = 95%+** | ICE duopoly dominates — EV and LPG adoption negligible in used market |
| 6 | **Manual = ~80% share** | India's cost-sensitive buyers strongly prefer manual transmission |
| 7 | **Dealers = ~62% listings** | Used car market increasingly professional and organized |
| 8 | **Right-skewed prices** | Log transformation of `selling_price` strongly recommended before modeling |

---

## 🚀 Next Steps & Recommendations

| Step | Phase | Action |
|---|---|---|
| 1 | Data Cleaning | Handle missing values in `mileage`, `engine`, `max_power`, and `seats` columns |
| 2 | Outlier Treatment | Cap or remove price outliers using IQR / Z-score; segment luxury brands |
| 3 | Feature Engineering | Log-transform `selling_price`; encode categorical features (`brand`, `fuel_type`, etc.) |
| 4 | Baseline Modeling | Train Linear Regression and Ridge/Lasso as baseline models |
| 5 | Advanced Models | Build Random Forest, XGBoost, and LightGBM for higher accuracy |
| 6 | Feature Importance | Analyze top predictors; confirm `max_power` vs `engine` redundancy |
| 7 | Model Evaluation | Compare RMSE, MAE, and R² across models with cross-validation |
| 8 | Deployment | Build a Flask/Streamlit app for real-time used car price prediction |

---

## ✅ Conclusion

This Exploratory Data Analysis of the CarDekho Used Car Dataset provides a comprehensive picture of India's used car market landscape. The market is structurally bifurcated between a **high-volume, budget-driven mass-market tier** and a **low-volume, high-value luxury tier** — each with distinct pricing dynamics and buyer behavior patterns.

The analysis establishes that **maximum power output and engine capacity** are the primary determinants of used car resale value, outweighing traditional depreciation factors like vehicle age and kilometers driven. Petrol and diesel vehicles continue to dominate the market by an overwhelming margin, while electric vehicle adoption remains negligible in the used car ecosystem.

The used car supply chain is increasingly professionalized, with dealers accounting for nearly **two-thirds of all listings** — a trend that mirrors the formalization of India's organized retail sector. Trustmark certification represents a significant untapped growth opportunity that could reshape buyer trust and price premiums in the coming years.

These findings provide a robust analytical foundation for subsequent machine learning price prediction modeling, with clear guidance on feature selection, outlier treatment, and preprocessing transformations necessary to build **accurate, generalizable models**.

---

## 📜 License

This project is licensed under the **MIT License** — free to use for educational, research, and commercial purposes.

---

> **Dataset:** CarDekho Used Car Dataset
> **Domain:** Indian Automotive / Used Car Market
> **Tools:** Python · Pandas · NumPy · Matplotlib · Seaborn · SciPy
> **Analysis Date:** May 2026

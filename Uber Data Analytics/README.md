# Uber  Analytics — Exploratory Data Analysis

**Delhi, India · Full Year 2024 · 148,770 Bookings · 21 Features**

## Executive Summary

This repository presents a comprehensive exploratory data analysis of Uber's ride operations in Delhi, India, conducted across the full calendar year of 2024. The study encompasses 148,770 booking records across 21 operational variables, with the objective of identifying performance inefficiencies, revenue optimisation opportunities, and data quality gaps that warrant strategic attention.

The analysis is structured across 14 visualisation modules, supported by statistical methodology, and culminates in a set of evidence-based operational recommendations.

---

## Platform Performance Overview

| Metric | Absolute Value | Percentage Share |
|---|---|---|
| Total Bookings | 148,770 | 100.00% |
| Completed Rides | ~93,000 | 65.96% |
| Driver-Initiated Cancellations | ~27,000 | 18.15% |
| Customer-Initiated Cancellations | ~11,000 | 7.45% |
| No Driver Assigned | ~11,000 | 7.40% |
| Incomplete Rides | ~9,500 | 6.04% |
| Vehicle Categories | 6 | — |
| Payment Methods | 5 | — |

---

## Repository Structure

```
uber-eda/
├── Uber_Data_Analytics.csv   # Source dataset (148,770 rows × 21 columns)
├── uber_eda.ipynb            # Primary analysis notebook
└── README.md                 # Project documentation
```

---

## Dataset Schema

| # | Column | Type | Description |
|---|--------|------|-------------|
| 1 | `Date` | Date | Date of booking |
| 2 | `Time` | Time | Time of booking |
| 3 | `Booking ID` | String | Unique ride identifier |
| 4 | `Booking Status` | Categorical | Completed / Cancelled by Driver / Cancelled by Customer / No Driver Found / Incomplete |
| 5 | `Customer ID` | String | Unique customer identifier |
| 6 | `Vehicle Type` | Categorical | Auto · Go Mini · Go Sedan · eBike/Bike · Premier Sedan · UberXL |
| 7 | `Pickup Location` | String | Origin of journey |
| 8 | `Drop Location` | String | Destination of journey |
| 9 | `Avg VTAT` | Float | Average driver-to-pickup time (minutes) |
| 10 | `Avg CTAT` | Float | Average pickup-to-destination time (minutes) |
| 11 | `Cancelled Rides by Customer` | Integer | Customer cancellation indicator |
| 12 | `Reason for Cancelling by Customer` | Categorical | Root cause of customer-initiated cancellation |
| 13 | `Cancelled Rides by Driver` | Integer | Driver cancellation indicator |
| 14 | `Driver Cancellation Reason` | Categorical | Root cause of driver-initiated cancellation |
| 15 | `Incomplete Rides` | Integer | Incomplete ride indicator |
| 16 | `Incomplete Rides Reason` | Categorical | Root cause of incomplete ride |
| 17 | `Booking Value` | Float | Fare amount in Indian Rupees (₹) |
| 18 | `Ride Distance` | Float | Journey distance in kilometres (km) |
| 19 | `Driver Ratings` | Float | Customer-assigned driver rating (1–5) |
| 20 | `Customer Rating` | Float | Driver-assigned customer rating (1–5) |
| 21 | `Payment Method` | Categorical | UPI · Cash · Credit Card · Uber Wallet · Debit Card |

---

## Analytical Framework

```
SOURCE DATA  →  INSPECTION  →  CLEANSING  →  ANALYSIS  →  VISUALISATION  →  FINDINGS  →  RECOMMENDATIONS
```

---

## Data Preparation Methodology

All transformations applied to the dataset are documented below, along with the analytical justification for each decision.

| Column | Treatment | Justification |
|--------|-----------|---------------|
| `Cancelled Rides by Customer / Driver` | `fillna(0)` | Absence of cancellation flag denotes a non-cancelled booking |
| `Cancellation Reason (Customer / Driver)` | `fillna('Not Cancelled')` | Absence of reason field confirms no cancellation occurred |
| `Incomplete Rides` | `fillna(0)` | Absence of flag indicates successful ride completion |
| `Incomplete Rides Reason` | `fillna('Completed')` | Absence of reason confirms completion without incident |
| `Driver Ratings` | `fillna(mean)` | Mean imputation preserves the distributional centre of the variable |
| `Customer Rating` | `fillna(mean)` | Mean imputation preserves the distributional centre of the variable |
| `Booking Value` | `fillna(0)` | Absence of fare value indicates no charge was applied |
| `Ride Distance` | `fillna(0)` | Absence of distance value indicates no journey was completed |
| `Payment Method` | `fillna('Not Applicable')` | Flags records with unresolved payment status for further investigation |
| `Avg CTAT / Avg VTAT` | `fillna(median)` | Median imputation mitigates the influence of right-skewed distributional tails |
| Column names | Standardised: strip, lowercase, underscore-delimited | Ensures uniform programmatic access throughout the notebook |

---

## Research Objectives

The analysis is structured around the following ten business-oriented questions:

1. What proportion of ride bookings result in successful completion, and what factors account for non-completion?
2. Which vehicle category generates the greatest total revenue contribution?
3. What are the primary drivers of driver-initiated cancellations, and at what frequency do they occur?
4. How is fare value distributed across the platform's booking portfolio?
5. Does journey distance serve as a reliable predictor of booking value?
6. At which hours and days does demand reach its peak?
7. Which payment method is most prevalent, and what operational implications does this carry?
8. Do driver or customer ratings demonstrate any statistically significant correlation with commercial performance?
9. Which pickup zones generate the highest booking volumes?
10. Which variables exert the most significant influence on ride revenue?

---

## Analysis Findings

### 01 · Booking Status Distribution

The platform achieves successful completion on approximately two-thirds of all bookings recorded. However, a non-completion rate of 34% — applied to an annual volume of 148,770 bookings — represents a substantial operational loss. Driver-initiated cancellations (~27,000) constitute the single most prevalent failure category, indicative of systematic selective ride rejection rather than isolated incidents. Customer cancellations (~11,000) and unassigned bookings (~11,000) are statistically equivalent in volume, suggesting that a significant proportion of customer cancellations occur during extended wait periods when driver assignment fails.

### 02 · Revenue by Vehicle Type

The Auto and Go Mini categories collectively generate approximately ₹2.33 Crore, exceeding the combined revenue of all remaining vehicle types. This distribution confirms that the platform operates primarily as a volume-driven, budget-segment business rather than a premium service model. The eBike and UberXL categories contribute negligible revenue relative to their operational complexity and may not be commercially viable at current demand levels.

### 03 · Pair Plot — Key Numerical Features

Among the six numerical variables examined, `Booking Value` and `Ride Distance` demonstrate the only statistically meaningful relationship (r ≈ 0.42). Distance accounts for less than 20% of the variance in fare value, indicating the presence of other significant pricing determinants. Wait-time distributions for both VTAT and CTAT are heavily right-skewed, with the majority of records concentrated near zero and a minority of severe outliers. Rating values are compressed within the 4.0–5.0 range, rendering the lower half of the rating scale operationally redundant.

### 04 · Driver Cancellation Reasons

Driver cancellations are distributed with near-uniform frequency across four root causes: personal and vehicle-related issues, customer-related issues, capacity and overcrowding, and customer health concerns (approximately 25% each). The absence of a dominant causal factor indicates that no single intervention will resolve the cancellation problem in isolation. Overcrowding-related cancellations represent a process failure — passenger count information should be captured and validated at the point of booking, not upon driver arrival.

### 05 · Booking Value Distribution

In excess of 60,000 bookings fall within the lowest fare bracket, reinforcing the characterisation of the platform as a high-frequency, low-unit-value operation. Booking frequency declines sharply above ₹500, with a secondary concentration observable between ₹200 and ₹600 attributable to mid-tier vehicle usage on longer urban commutes. Revenue growth strategy must therefore prioritise operational efficiency and volume retention over premium segment development.

### 06 · Ride Distance vs. Booking Value

Fare values for rides of equivalent distances exhibit substantial variance — ranging from ₹0 to in excess of ₹4,000 — confirming that distance is an insufficient basis for fare prediction in isolation. The greatest degree of fare dispersion is observed on short-distance trips (under 10 km), where premium vehicle bookings on brief routes are prevalent. Long-haul journeys (40–50 km) similarly span the full fare spectrum, suggesting that dynamic pricing mechanisms for extended journeys may not be optimally calibrated.

### 07 · Driver Ratings Distribution

Approximately 84.7% of driver ratings fall within the High category (4–5 stars). Within the ride-hailing sector, this concentration is characteristic of rating inflation rather than genuine service quality differentiation. The 15.3% of drivers rated as Medium represents a considerable volume of below-standard ride experiences at the scale of this platform. The binary High/Medium classification system does not provide sufficient resolution to identify either exceptional performers or consistently underperforming drivers.

### 08 · Bookings by Hour

The 18:00 hour records the highest booking volume of any hour in the dataset. Driver availability must be strategically concentrated between 17:00 and 19:00 to meet this demand. The morning demand peak at 09:00, while present, is less pronounced than expected for a major metropolitan commuter market. Consistent late-night demand between 22:00 and 23:00 warrants dedicated supply allocation rather than residual capacity assignment. A persistent baseline demand exists throughout the 00:00–04:00 period, attributable to shift workers and airport transfers.

### 09 · Top Pickup Locations

The ten highest-volume pickup zones exhibit a booking spread of only 33 across fundamentally different location categories — business districts, public transit terminals, and medical facilities. The uniformity of this distribution is statistically atypical for real-world demand data and may reflect data sampling methodology. The geographic distribution of demand across southern, central, and western Delhi confirms that demand is decentralised, necessitating a distributed driver positioning strategy.

### 10 · Payment Method Distribution

The "Not Applicable" classification accounts for approximately 48,000 records, constituting the single largest payment category and rendering comprehensive payment analysis unreliable until this gap is resolved. Among classified records, UPI is the dominant payment method (~46,000 transactions), consistent with India's broader digital payments landscape. Cash transactions (~26,000) remain operationally significant. The Uber Wallet (~12,000 transactions) represents an underutilised customer retention mechanism with unrealised commercial potential.

### 11 · Cancellation by Vehicle Type

The Auto category records both the highest volume of completed rides (~23,000) and the highest absolute number of driver cancellations (~6,500), reflecting acute supply-demand pressure within this segment. The Go Mini category demonstrates the most favourable cancellation ratio relative to its booking volume. "No Driver Found" outcomes are present across all six vehicle types without exception, confirming that driver supply shortfalls are a platform-wide structural issue rather than a category-specific operational failure.

### 12 · Correlation Heatmap

| | Booking Value | Ride Distance | Driver Ratings | Customer Rating |
|---|---|---|---|---|
| **Booking Value** | 1.00 | 0.42 | 0.00 | 0.00 |
| **Ride Distance** | 0.42 | 1.00 | 0.00 | 0.00 |
| **Driver Ratings** | 0.00 | 0.00 | 1.00 | −0.001 |
| **Customer Rating** | 0.00 | 0.00 | −0.001 | 1.00 |

Ride distance is the sole variable exhibiting a statistically meaningful correlation with booking value. Rating variables demonstrate no measurable correlation with any commercial outcome. Predictive modelling efforts would benefit substantially from the inclusion of additional variables such as surge multiplier, zone classification, time-of-day indicators, driver tenure, and vehicle condition.

### 13 · Revenue by Day of Week

Saturday and Sunday consistently generate approximately 50% greater revenue than any individual weekday. Weekday revenue is stable and predictable across Monday through Thursday, forming a dependable commuter baseline. Friday represents the most significant unrealised revenue opportunity in the dataset — despite its proximity to peak weekend demand, its performance is broadly comparable to mid-week days. Failure to scale driver supply in alignment with weekend demand results in foregone revenue during the platform's highest-value operating period.

### 14 · Ratings Distribution Comparison

Driver ratings are concentrated narrowly around a peak of 4.2. Customer ratings exhibit a broader, multi-modal distribution with identifiable clusters near 4.35, 4.6, and 5.0 — a pattern consistent with drivers anchoring their assessments to round-number thresholds rather than applying continuous evaluation. Both rating distributions are effectively truncated below 3.5. Under prevailing rating conditions, a score of 4.0 should be interpreted as a meaningful indicator of service quality concern rather than an acceptable outcome.

---

## Vehicle Fleet Performance Summary

| Vehicle | Completion Rate | Average Distance | Key Observation |
|---------|----------------|------------------|-----------------|
| Auto | 91.1% | 25.99 km | Highest revenue contribution; highest absolute cancellation volume |
| Go Mini | 91.0% | 25.99 km | Most consistent performance relative to booking volume |
| Go Sedan | 91.1% | 25.98 km | Disproportionately elevated driver cancellation rate |
| Premier Sedan | 91.2% | 25.95 km | Revenue underperformance relative to Go Sedan category |
| eBike / Bike | 91.1% | 26.11 km | Marginal revenue contribution at current scale |
| UberXL | 92.2% | 25.72 km | Highest completion rate in fleet; lowest booking volume |

The UberXL category achieves the highest completion rate across the fleet (92.2%), attributable to more intentional booking behaviour among its customer base and correspondingly lower cancellation propensity.

---

## Cancellation Analysis

**Customer-initiated cancellation reasons:**

| Reason | Proportional Share |
|--------|--------------------|
| Wrong Address Provided | 22.5% |
| Driver-Related Issues | 22.4% |
| Driver Not in Transit | 22.2% |
| Change of Travel Plans | 21.9% |
| Application Malfunction | 11.0% |

**Driver-initiated cancellation reasons:**

| Reason | Proportional Share |
|--------|--------------------|
| Customer-Related Issues | 25.3% |
| Capacity / Overcrowding | 25.0% |
| Personal or Vehicle Issues | 24.9% |
| Customer Conduct | 24.8% |

Both cancellation distributions exhibit near-uniform dispersion across all reported causes. This pattern is indicative of systemic operational friction rather than isolated incidents, and necessitates a multi-pronged intervention strategy.

---

## Key Findings

| Domain | Summary Finding |
|---|---|
| **Supply Adequacy** | Approximately 11,000 "No Driver Found" outcomes reflect a platform-wide supply deficit, not localised shortfalls |
| **Cancellation Management** | Approximately 27,000 driver cancellations are distributed evenly across four root causes, each requiring independent remediation |
| **Revenue Concentration** | Auto and Go Mini account for approximately ₹2.33 Crore; eBike and UberXL combined contribute approximately ₹51 Lakh |
| **Fare Predictability** | Ride distance (r = 0.42) is the only statistically meaningful fare predictor within the current feature set |
| **Demand Patterns** | Peak demand occurs at 18:00; weekend revenue exceeds weekday averages by approximately 50% |
| **Payment Data Integrity** | UPI leads among classified transactions; approximately 48,000 records remain unclassified |
| **Rating System Validity** | Bilateral rating inflation is structurally embedded; a rating of 4.0 constitutes a performance concern, not a neutral midpoint |

---

## Strategic Recommendations

**① Structural Reform of the Cancellation Management Framework**
- Enforce passenger group size capture at the point of booking to eliminate capacity-related cancellations prior to driver dispatch
- Implement a dynamic, escalating cancellation penalty framework to disincentivise selective ride rejection by drivers
- Develop a proactive driver scheduling and wellness monitoring system to reduce personal and vehicle-related service interruptions

**② Targeted Supply-Side Intervention**
- Conduct granular mapping of all "No Driver Found" events by geographic zone and time of day; apply demand-specific incentive structures accordingly
- Deploy predictive demand forecasting to pre-position driver supply within the 17:00–19:00 peak window; passive surge reliance is insufficient at this demand level

**③ Weekend Revenue Optimisation**
- Activate dedicated weekend driver incentive programmes calibrated to the observed ~50% demand premium relative to weekday baselines
- Develop a targeted Friday evening demand activation strategy to capture the transition into the weekend peak — currently the most undercaptured revenue window in the dataset

**④ Data Governance and Quality Remediation**
- Initiate a formal investigation into the approximately 48,000 "Not Applicable" payment records; payment behaviour analysis cannot be conducted reliably until this is resolved
- Expand driver cancellation reason taxonomy to disaggregate broad categories such as "Customer-Related Issues" into actionable sub-classifications
- Augment future data collection to include: surge multiplier, zone-level supply-demand ratio, driver tenure, and vehicle condition indicators

**⑤ Portfolio Prioritisation**
- The Auto and Go Mini categories constitute the primary revenue engine of the platform; investment in supply protection, cancellation reduction, and driver incentivisation within these categories should be prioritised accordingly
- The Uber Wallet payment channel represents an underutilised customer loyalty mechanism; wallet users exhibit high-frequency repeat booking behaviour and warrant targeted engagement
- The eBike and UberXL categories require formal strategic review; neither demonstrates self-sustaining commercial performance at current demand levels

---

## Potential Modelling Applications

This dataset supports the development of the following analytical and predictive models:

- **Cancellation Risk Classification** — pre-trip prediction of cancellation probability prior to driver acceptance
- **Revenue Forecasting** — time-series modelling of daily and weekly booking value trends
- **Supply-Demand Optimisation** — spatial and temporal mapping of driver supply deficits for targeted intervention
- **Driver Performance Segmentation** — clustering by cancellation rate, rating profile, earnings distribution, and vehicle type
- **Customer Behavioural Segmentation** — segmentation by vehicle preference, payment method, and booking frequency
- **Surge Pricing Modelling** — decomposition of unexplained fare variance to surface latent surge pricing patterns
- **Rating System Evaluation** — investigation of bilateral rating inflation and its commercial implications at scale

---

## Advanced Analytical Queries

```python
# Revenue disaggregation by Vehicle Type and Payment Method
df.groupby(['Vehicle Type', 'Payment Method'])['Booking Value'].agg(['sum', 'mean'])

pd.pivot_table(
    df,
    values='Booking Value',
    index='Vehicle Type',
    columns='Payment Method',
    aggfunc='sum'
)

# Cancellation rate cross-tabulation, normalised by vehicle type
pd.crosstab(
    df['Vehicle Type'],
    df['Booking Status'],
    normalize='index'
) * 100

# Outlier identification using the Interquartile Range method
Q1  = df['Booking Value'].quantile(0.25)
Q3  = df['Booking Value'].quantile(0.75)
IQR = Q3 - Q1
outliers = df[
    (df['Booking Value'] < Q1 - 1.5 * IQR) |
    (df['Booking Value'] > Q3 + 1.5 * IQR)
]

# Distributional shape assessment
from scipy.stats import skew, kurtosis
print(f"Skewness : {skew(df['Booking Value'].dropna()):.4f}")
print(f"Kurtosis : {kurtosis(df['Booking Value'].dropna()):.4f}")

# Isolation of high-value completed bookings
df.query("`Booking Value` > 1000 and `Booking Status` == 'Completed'")
```

---

## Technology Stack

| Tool | Version | Function |
|------|---------|----------|
| Python | 3.9+ | Primary programming language |
| pandas | ≥ 1.5 | Data ingestion, transformation, and aggregation |
| NumPy | ≥ 1.23 | Numerical computation |
| Matplotlib | ≥ 3.6 | Base-layer visualisation |
| Seaborn | ≥ 0.12 | Statistical visualisation and charting |
| SciPy | ≥ 1.9 | Distributional statistics (skewness, kurtosis) |
| Jupyter | latest | Interactive notebook environment |

---

## Reproduction Instructions

```bash
# Clone the repository
git clone https://github.com/yourusername/uber-eda.git
cd uber-eda

# Install required dependencies
pip install pandas numpy matplotlib seaborn scipy jupyter

# Launch the analysis notebook
jupyter notebook uber_eda.ipynb
```

> The source file `Uber_Data_Analytics.csv` must be present in the same directory as the notebook prior to execution.

---

## Data Conventions

- All monetary figures are denominated in **Indian Rupees (₹)**
- All distance measurements are expressed in **kilometres (km)**
- `Avg VTAT` and `Avg CTAT` are recorded in **minutes**
- The `Hour` variable used in demand analysis is derived programmatically from the `Time` column and must be extracted prior to executing the relevant notebook cell

---

## Data Quality Assessment

| Dimension | Status | Notes |
|---|---|---|
| Completeness | ✅ Satisfactory | Missing values are minimal across all 21 columns |
| Consistency | ✅ Satisfactory | Categorical variables are standardised throughout |
| Temporal Coverage | ✅ Complete | Full calendar year 2024 at daily granularity |
| Geographic Scope | ✅ Comprehensive | Multiple pickup and drop zones across Delhi |
| Class Balance | ✅ Adequate | All vehicle types and time periods are represented |
| Payment Classification | ⚠️ Requires Remediation | Approximately 48,000 records carry an unresolved "Not Applicable" payment status |

---

*Prepared for analytical and educational purposes · Uber Ride Operations · Delhi, India · Full Year 2024 · 148,770 bookings · 21 variables*

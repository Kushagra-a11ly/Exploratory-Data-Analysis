# 🚗 Uber Ride Analytics — Exploratory Data Analysis

> End-to-end EDA of **148,770 Uber bookings** spanning booking outcomes, revenue patterns, vehicle performance, cancellation behaviour, payment trends, and customer satisfaction — using Python, Pandas, Seaborn, and Matplotlib.

---

## 📁 Project Structure

```
uber-eda/
│
├── Uber_Data_Analytics.csv        # Raw dataset (148,770 rows × 21 columns)
├── uber_eda.ipynb                 # Main analysis notebook
└── README.md                     # Project documentation
```

---

## 🎯 Objectives

This notebook investigates the following business questions:

1. What percentage of rides are completed vs. cancelled?
2. Which vehicle type generates the most revenue?
3. Why do drivers cancel — and how often?
4. How are ride prices distributed across the platform?
5. Does ride distance reliably predict booking value?
6. When is demand highest throughout the day and week?
7. Which payment method dominates — and what does that signal?
8. Are driver and customer ratings correlated with commercial performance?
9. Which pickup locations drive the most bookings?
10. What features most strongly impact revenue?

---

## 🔄 Workflow

```
Load Data → Inspect → Clean → Analyse → Visualise → Insight → Recommend
```

---

## 🧹 Data Cleaning & Preprocessing

The following transformations were applied before analysis:

| Column | Treatment |
|---|---|
| `Cancelled Rides by Customer / Driver` | `fillna(0)` |
| `Reason for cancelling by Customer / Driver` | `fillna('Not Cancelled')` |
| `Incomplete Rides` | `fillna(0)` |
| `Incomplete Rides Reason` | `fillna('Completed')` |
| `Driver Ratings` | `fillna(mean)` |
| `Customer Rating` | `fillna(mean)` |
| `Booking Value` | `fillna(0)` |
| `Ride Distance` | `fillna(0)` |
| `Payment Method` | `fillna('Not Applicable')` |
| `Avg CTAT / Avg VTAT` | `fillna(median)` |
| Column names | Stripped, lowercased, spaces replaced with `_` |

---

## 📊 Analysis Sections

### 1. Booking Status Distribution
Countplot of all booking outcomes. Reveals that while ~93K rides complete successfully, ~27K driver cancellations and ~11K "No Driver Found" events represent significant operational leakage.

**Key finding:** Customer cancellations and "No Driver Found" are near-identical in volume (~11K each) — strongly suggesting that frustrated customers cancel while waiting, making supply availability the root cause of both problems.

---

### 2. Revenue by Vehicle Type
Summed bar chart of `Booking Value` across vehicle categories.

| Vehicle Type | Total Revenue |
|---|---|
| Auto | ~₹1.29 Cr |
| Go Mini | ~₹1.04 Cr |
| Go Sedan | ~₹93 L |
| Premier Sedan | ~₹79 L |
| Bike | ~₹63 L |
| eBike | ~₹36 L |
| Uber XL | ~₹15 L |

**Key finding:** Auto and Go Mini together account for the majority of platform revenue, driven by volume rather than fare size.

---

### 3. Pair Plot — Key Numerical Features
Corner pairplot across `Avg VTAT`, `Avg CTAT`, `Booking Value`, `Ride Distance`, `Driver Ratings`, and `Customer Rating`.

**Key findings:**
- `Booking Value` and `Ride Distance` show a moderate positive relationship
- Wait time distributions are heavily right-skewed with outlier tails
- Ratings are compressed into a 3.0–5.0 band with mass near 4.5 — classic rating inflation

---

### 4. Driver Cancellation Reasons
Horizontal countplot of `Driver Cancellation Reason`.

All four active reasons (Personal & Car Issues, Customer-Related, Overcrowding, Sick Customer) are near-uniformly distributed at ~6–8K each — indicating systemic friction with no single dominant cause.

---

### 5. Booking Value Distribution
Histogram with KDE overlay of `Booking Value`.

**Key finding:** The distribution is heavily right-skewed — ~60K+ rides in the lowest fare bucket. The platform is optimised for volume, not value. Rides above ₹1000 exist but are rare.

---

### 6. Ride Distance vs. Booking Value
Scatter plot of `Ride Distance` against `Booking Value`.

**Key finding:** Distance alone does not determine price. Rides at the same distance span ₹0–₹4000+, confirming that vehicle type, surge pricing, and time-of-day contribute heavily to fare variance.

---

### 7. Driver Ratings Distribution
Pie chart of `Driver_Rating_Category` (Low 0–2 / Medium 2–4 / High 4–5).

| Category | Share |
|---|---|
| High (4–5) | 84.7% |
| Medium (2–4) | 15.3% |
| Low (0–2) | ~0.0% |

**Key finding:** 15.3% medium-rated drivers at scale translates to thousands of below-average rides daily — a structural quality issue masked by surface-level high averages.

---

### 8. Bookings by Hour
Countplot of ride volume across all 24 hours.

| Time Window | Volume |
|---|---|
| 18:00 (Peak) | ~12,500 rides |
| 09:00–10:00 | ~9,500 rides |
| 12:00–14:00 | ~5,500–7,000 rides (trough) |
| 22:00–23:00 | ~5,500–8,000 rides |
| 00:00–04:00 | ~1,400–1,500 rides/hour |

---

### 9. Top Pickup Locations
Bar chart of the 10 highest-demand pickup zones across Delhi.

Notable locations include AIIMS (healthcare demand), Dwarka Sector 21 (metro last-mile), and Barakhamba Road (central business district). Demand is geographically decentralised — no single zone dominates.

---

### 10. Payment Method Distribution
Countplot of `Payment Method`.

**Key finding:** ~48K "Not Applicable" records represent a data quality issue that must be resolved before payment behaviour can be reliably analysed. Among valid methods, UPI leads at ~46K, followed by Cash at ~26K.

---

### 11. Cancellation by Vehicle Type
Grouped countplot of `Booking Status` across `Vehicle Type`.

**Key finding:** Every vehicle category shows "No Driver Found" events — confirming this is a platform-wide supply shortage rather than a category-specific problem.

---

### 12. Correlation Heatmap
Heatmap of correlations across `Booking Value`, `Ride Distance`, `Driver Ratings`, `Customer Rating`.

| Feature Pair | Correlation |
|---|---|
| Booking Value ↔ Ride Distance | **0.42** |
| Driver Ratings ↔ Booking Value | ~0.00 |
| Customer Rating ↔ Booking Value | ~0.00 |
| Driver Ratings ↔ Customer Ratings | -0.001 |

**Key finding:** Distance is the only meaningful predictor in this matrix. Ratings are entirely decoupled from commercial performance — satisfaction is driven by unmeasured experience variables.

---

### 13. Revenue by Day of Week
Summed bar chart of `Booking Value` across all seven days.

**Key finding:** Saturday and Sunday each generate ~₹9.6–9.7Cr — roughly 50% more than any weekday (~₹6.4–6.7Cr). Friday does not outperform other weekdays, suggesting untapped Friday evening demand.

---

### 14. Ratings Distribution Comparison (KDE)
Overlapping KDE plots of `Driver Ratings` and `Customer Rating`.

**Key finding:** Driver ratings peak at 4.2 (narrow, concentrated); customer ratings peak at 4.35 (wider, multi-modal). Both distributions almost completely ignore scores below 3.5 — rating inflation is present on both sides.

---

## 🔬 Advanced Exploration

The notebook also includes:

- **Revenue pivot table** — `Booking Value` by `Vehicle Type` × `Payment Method`
- **Cancellation cross-tabs** — percentage breakdowns by vehicle type and booking status
- **Outlier detection** — IQR method applied to `Booking Value`; boxplot visualisation
- **Skewness & Kurtosis** — statistical shape analysis of the booking value distribution
- **Top-value ride queries** — filtered view of completed rides with `Booking Value > ₹1000`

---

## 💡 Key Takeaways

| Theme | Finding |
|---|---|
| **Supply** | ~11K "No Driver Found" events signal chronic supply shortages across all zones and hours |
| **Cancellations** | ~27K driver cancellations are evenly split across four root causes — no single fix suffices |
| **Revenue** | Auto and Go Mini drive the most revenue; eBike and Uber XL are near-irrelevant |
| **Pricing** | Booking value is only moderately correlated with distance (r=0.42); vehicle type matters more |
| **Demand** | Evening peak (18:00) outpaces morning peak; weekends generate ~50% more revenue than weekdays |
| **Payments** | UPI dominates real payments; ~48K unclassified records need data quality remediation |
| **Ratings** | Rating inflation compresses scores into a narrow 4.0–5.0 band; a 4.0 is a genuine warning signal |

---

## 🛠️ Tech Stack

| Library | Version | Purpose |
|---|---|---|
| `pandas` | ≥ 1.5 | Data loading, cleaning, aggregation |
| `numpy` | ≥ 1.23 | Numerical operations |
| `matplotlib` | ≥ 3.6 | Base visualisation |
| `seaborn` | ≥ 0.12 | Statistical plotting |
| `scipy` | ≥ 1.9 | Skewness & kurtosis calculations |

---

## ▶️ How to Run

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/uber-eda.git
cd uber-eda

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scipy jupyter

# 3. Launch the notebook
jupyter notebook uber_eda.ipynb
```

Make sure `Uber_Data_Analytics.csv` is in the same directory as the notebook before running.

---

## 📌 Notes

- All monetary values are in **Indian Rupees (₹)**
- Distance is measured in **kilometres (km)**
- Time columns (`Avg VTAT`, `Avg CTAT`) are in **minutes**
- The `Hour` column used in the demand analysis must be extracted from the `Time` column prior to plotting

---

*Dataset: Uber Ride Operations 2024 | 148,770 bookings | 21 features | Delhi, India*

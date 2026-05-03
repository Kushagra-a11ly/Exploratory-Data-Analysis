![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/b52a7331206a874e8f8bb10172f92bb58d71e0c7/Uber%20Data%20Analytics/dataset-cover.png)


# 🚗 Uber Data Analytics — EDA Report

A comprehensive Exploratory Data Analysis (EDA) of Uber ride data, covering booking behaviour, revenue patterns, cancellation trends, driver/customer ratings, and operational insights.

---

## 📁 Project Structure

```
uber-data-analytics/
│
├── Uber_Data_Analytics.csv       # Raw dataset
├── uber_eda.ipynb                # Main analysis notebook
└── README.md                     # Project overview (this file)
```

---

## 📌 Objectives

- Understand the distribution of booking statuses (completed vs cancelled)
- Identify top revenue-generating vehicle types
- Analyse cancellation patterns by driver and vehicle type
- Explore payment method preferences
- Uncover peak demand hours and high-traffic pickup locations
- Examine relationships between ride distance, booking value, and ratings

---

## 🧹 Data Cleaning & Preprocessing

The following steps were applied before analysis:

- Standardised column names (lowercase, underscores)
- Filled missing cancellation flags with `0` and reasons with `'Not Cancelled'`
- Filled missing ride completion reasons with `'Completed'`
- Imputed `Driver Ratings` and `Customer Rating` with their respective **means**
- Filled `Booking Value` and `Ride Distance` nulls with `0`
- Used **median** imputation for `Avg CTAT` and `Avg VTAT`
- Filled missing `Payment Method` with `'Not Applicable'`

---

## 📊 Analyses Performed

### 1. Booking Status Distribution
> *What % of rides are completed vs cancelled?*

- ~93K completed rides dominate, but ~27K driver cancellations signal a supply/incentive issue.
- ~11K "No Driver Found" cases point to a structural supply gap.
- Customer cancellations (~11K) likely overlap with driver unavailability frustration.

---

### 2. Revenue by Vehicle Type
> *Which vehicle type earns most?*

| Vehicle Type | Revenue (approx.) |
|---|---|
| Auto | ₹1.29 Cr |
| Go Mini | ₹1.04 Cr |
| Go Sedan | ₹93 L |
| Premier Sedan | ₹79 L |
| Bike | ₹63 L |
| eBike / Uber XL | < ₹40 L |

Auto dominates revenue; eBike and Uber XL remain niche.

---

### 3. Pair Plot — Key Numerical Features
> *How do ride metrics relate to each other?*

- `Booking Value` and `Ride Distance` have a moderate positive relationship.
- Wait times (`VTAT`, `CTAT`) cluster near zero with long outlier tails.
- Ratings are compressed in the 4.0–5.0 band — rating inflation is evident.

---

### 4. Driver Cancellation Reasons
> *Why do drivers cancel?*

All reasons (Personal/Car issues, Customer-related, Overcrowding, Sick customer) are roughly equal at ~6–8K each — indicating broad, unresolved operational issues rather than a single dominant cause.

---

### 5. Booking Value Distribution
> *How are ride prices distributed?*

- Heavily right-skewed — most rides cost under ₹500.
- High-value rides (₹1000+) exist but are rare.
- Business model is **volume-driven, not value-driven**.

---

### 6. Ride Distance vs Booking Value
> *Do longer rides generate more money?*

- Moderate correlation (0.42), but wide scatter confirms pricing is **not purely distance-based**.
- Short rides show the highest price variance — premium vehicles on short trips are common.

---

### 7. Driver Ratings Distribution
> *Are drivers rated well?*

- 84.7% rated between 4–5 (High)
- 15.3% rated between 2–4 (Medium)
- 0% rated below 2 — likely reflects rating inflation, not absence of poor experiences.

---

### 8. Bookings by Hour
> *When is demand highest?*

- **Peak:** 6 PM (~12,500 rides) — evening commute dominates.
- **Secondary peak:** 9–10 AM (~9,500 rides).
- **Dead zone:** 12–2 PM — good window for driver incentives.
- Late-night demand (10 PM–midnight) remains significant at ~5,500–8,000 rides/hour.

---

### 9. Top Pickup Locations
> *Where do people go most?*

Key locations include Khandsa, Barakhamba Road, AIIMS, and Dwarka Sector 21. Demand is geographically **decentralised across Delhi** — no single dominant zone.

---

### 10. Payment Method Distribution
> *Which payment method is most used?*

- **UPI** leads at ~46K transactions (dominant in the Indian market).
- **Cash** remains significant at ~26K.
- Cards are relatively rare — users have leapfrogged to UPI.
- **"Not Applicable"** (~48K) is a data quality concern requiring investigation.

---

### 11. Cancellation by Vehicle Type
> *Which vehicle type gets cancelled more?*

- Auto has the highest completions **and** the highest driver cancellations.
- "No Driver Found" appears consistently across **all** vehicle types — a platform-wide supply problem.

---

### 12. Correlation Heatmap
> *Which features impact revenue?*

| Feature Pair | Correlation |
|---|---|
| Booking Value ↔ Ride Distance | 0.42 |
| Ratings ↔ Anything | ~0.00 |

Ratings are independent of fare and distance — satisfaction drivers are outside this dataset.

---

### 13. Revenue by Day
> *Which days generate most revenue?*

- **Weekends:** ~₹9.6–9.7 Cr — ~50% above weekday revenue.
- **Weekdays:** Flat at ₹6.4–6.7 Cr — reliable commuter base.
- Friday underperforms expectations despite gateway-to-weekend positioning.

---

### 14. Ratings Distribution Comparison
> *How do driver and customer ratings compare?*

- Drivers peak sharply at **4.2**; customers peak at **4.35**.
- Both distributions ignore anything below 3.5 — rating inflation across the board.
- Customer ratings show multiple bumps, suggesting drivers anchor to round numbers.

---

## 🔬 Advanced Analysis

| Analysis | Method |
|---|---|
| Revenue by Vehicle × Payment | `groupby` + `agg` |
| Cancellation patterns | `groupby` + `size` |
| Revenue deep dive | `pivot_table` |
| Cancellation behaviour | `crosstab` with normalisation |
| Outlier detection | Boxplot + IQR method |
| Distribution shape | Skewness & Kurtosis (scipy.stats) |

---

## 🛠️ Tech Stack

- **Python 3.x**
- **pandas** — data manipulation
- **matplotlib** — visualisation
- **seaborn** — statistical plots
- **scipy** — statistical tests
- **numpy** — numerical operations

---

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/your-username/uber-data-analytics.git
cd uber-data-analytics

# 2. Install dependencies
pip install pandas matplotlib seaborn scipy numpy

# 3. Open the notebook
jupyter notebook uber_eda.ipynb
```

---

## 📌 Key Business Takeaways

1. **Fix driver cancellations** — ~27K is too high; incentives and ride-matching need work.
2. **Solve the supply gap** — "No Driver Found" is a platform-wide, not category-level, problem.
3. **Double down on UPI** — it's the dominant payment rail; optimise the experience around it.
4. **Leverage weekend demand** — 50% revenue premium on weekends warrants aggressive surge strategy.
5. **Don't ignore late nights** — consistent demand after 10 PM deserves dedicated driver supply.
6. **Rating inflation masks real issues** — treat a 4.0 driver rating as a warning, not a pass.

---

## 📄 License

This project is for educational and analytical purposes only. Uber data is used solely for demonstrative EDA practice.
















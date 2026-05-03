# 🚗 Uber Ride Analytics Dataset 2024

> A comprehensive ride-sharing operations dataset capturing **148,770 bookings** across vehicle types, payment methods, cancellation patterns, and satisfaction metrics for the full year 2024.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Key Statistics](#-key-statistics)
- [Data Schema](#-data-schema)
- [Vehicle Fleet Coverage](#-vehicle-fleet-coverage)
- [Revenue Distribution](#-revenue-distribution-by-payment-method)
- [Cancellation Patterns](#-cancellation-patterns)
- [Rating Analysis](#-rating-analysis)
- [Data Quality](#-data-quality)
- [Use Cases](#-use-cases)
- [Getting Started](#-getting-started)

---

## 📊 Overview

This dataset provides a granular, end-to-end view of Uber ride operations throughout 2024. It is designed for analysts and data scientists working on ride-sharing intelligence, supply-demand modelling, cancellation prediction, or customer experience research.

The data covers the full booking lifecycle — from initial request through completion or cancellation — including financial metrics, geographic context, timing data, and bilateral satisfaction ratings.

---

## 🔢 Key Statistics

| Metric | Value |
|---|---|
| **Total Bookings** | 148,770 rides |
| **Completed Rides** | ~93,000 (65.96%) |
| **Total Cancellations** | ~37,430 (25.00%) |
| **Customer Cancellations** | ~19.15% of total bookings |
| **Driver Cancellations** | ~7.45% of total bookings |
| **Temporal Coverage** | Full Year 2024 (daily granularity) |
| **Vehicle Types** | 6 categories |
| **Payment Methods** | 5 methods |

---

## 📋 Data Schema

The dataset contains **21 columns** covering booking metadata, operational metrics, financial data, and satisfaction ratings.

| Column | Type | Description |
|---|---|---|
| `Date` | Date | Date of the booking |
| `Time` | Time | Time of the booking |
| `Booking ID` | String | Unique identifier for each ride booking |
| `Booking Status` | Categorical | Completed / Cancelled by Customer / Cancelled by Driver / No Driver Found / Incomplete |
| `Customer ID` | String | Unique identifier for customers |
| `Vehicle Type` | Categorical | Go Mini, Go Sedan, Auto, eBike/Bike, UberXL, Premier Sedan |
| `Pickup Location` | String | Starting location of the ride |
| `Drop Location` | String | Destination location of the ride |
| `Avg VTAT` | Float | Average time for driver to reach pickup location (minutes) |
| `Avg CTAT` | Float | Average trip duration from pickup to destination (minutes) |
| `Cancelled Rides by Customer` | Boolean/Int | Customer-initiated cancellation flag |
| `Reason for cancelling by Customer` | Categorical | Root cause of customer cancellation |
| `Cancelled Rides by Driver` | Boolean/Int | Driver-initiated cancellation flag |
| `Driver Cancellation Reason` | Categorical | Root cause of driver cancellation |
| `Incomplete Rides` | Boolean/Int | Incomplete ride flag |
| `Incomplete Rides Reason` | Categorical | Reason for incomplete rides |
| `Booking Value` | Float | Total fare amount for the ride (₹) |
| `Ride Distance` | Float | Distance covered during the ride (km) |
| `Driver Ratings` | Float | Rating given to the driver (1–5 scale) |
| `Customer Rating` | Float | Rating given by the driver to the customer (1–5 scale) |
| `Payment Method` | Categorical | UPI / Cash / Credit Card / Uber Wallet / Debit Card |

---

## 🚗 Vehicle Fleet Coverage

| Vehicle Type | Total Bookings | Success Rate | Avg Distance | Total Distance |
|---|---|---|---|---|
| **Auto** | 12.88M | 91.1% | 25.99 km | 602K km |
| **eBike / Bike** | 11.46M | 91.1% | 26.11 km | 537K km |
| **Go Mini** | 10.34M | 91.0% | 25.99 km | 482K km |
| **Go Sedan** | 9.37M | 91.1% | 25.98 km | 433K km |
| **Premier Sedan** | 6.28M | 91.2% | 25.95 km | 292K km |
| **UberXL** | 1.53M | 92.2% | 25.72 km | 72K km |

> **Note:** UberXL shows the highest success rate (92.2%) despite the lowest booking volume, suggesting a more committed, intentional user segment.

---

## 💰 Revenue Distribution by Payment Method

| Payment Method | Revenue Share | Notes |
|---|---|---|
| **UPI** | ~40% | Dominant method; reflects India's digital payment maturity |
| **Cash** | ~25% | Significant and persistent; cannot be ignored |
| **Credit Card** | ~15% | Mid-tier adoption |
| **Uber Wallet** | ~12% | Loyalty signal; underutilised growth lever |
| **Debit Card** | ~8% | Lowest adoption among digital methods |

---

## 🚫 Cancellation Patterns

### Customer Cancellation Reasons

| Reason | Share |
|---|---|
| Wrong Address | 22.5% |
| Driver Issues | 22.4% |
| Driver Not Moving | 22.2% |
| Change of Plans | 21.9% |
| App Issues | 11.0% |

### Driver Cancellation Reasons

| Reason | Share |
|---|---|
| Customer Related Issues | 25.3% |
| Capacity Issues | 25.0% |
| Personal & Car Issues | 24.9% |
| Customer Behavior | 24.8% |

> **Key Insight:** Both customer and driver cancellation reasons are near-uniformly distributed — no single root cause dominates, suggesting systemic friction rather than isolated issues.

---

## ⭐ Rating Analysis

| Vehicle Type | Customer Rating | Driver Rating |
|---|---|---|
| Go Sedan | 4.41 ⭐ | 4.24 |
| Auto | 4.40 | 4.23 |
| Go Mini | 4.40 | 4.23 |
| eBike / Bike | 4.40 | 4.23 |
| Premier Sedan | 4.40 | 4.24 |
| UberXL | 4.40 | 4.24 ⭐ |

- **Customer ratings** are consistently high across all categories (4.40–4.41)
- **Driver ratings** are stable but slightly lower (4.23–4.24)
- **Highest-rated vehicle** for customers: Go Sedan (4.41)
- **Most satisfied drivers**: UberXL category (4.24)

> **Note:** The narrow rating bands across all categories suggest platform-wide rating compression — a 4.0 score likely represents a more significant quality signal than it appears.

---

## ✅ Data Quality

| Dimension | Status | Detail |
|---|---|---|
| **Completeness** | ✅ High | Comprehensive coverage; minimal missing values |
| **Consistency** | ✅ High | Standardised vehicle types and status categories |
| **Temporal Coverage** | ✅ Full Year | Daily granularity across all of 2024 |
| **Geographic Scope** | ✅ Multi-location | Multiple pickup and drop locations |
| **Class Balance** | ✅ Good | Representation across all vehicle types and time periods |

---

## 💡 Use Cases

This dataset is well-suited for the following analytical and machine learning tasks:

- **Cancellation Prediction** — Build classifiers to predict booking cancellation risk before a driver accepts
- **Revenue Forecasting** — Time-series modelling of daily/weekly booking value
- **Supply-Demand Modelling** — Identify underserved zones and hours by cross-referencing "No Driver Found" events with time and location
- **Driver Performance Analysis** — Cluster drivers by rating, cancellation rate, and earnings efficiency
- **Customer Segmentation** — Segment riders by vehicle preference, payment method, and frequency
- **Pricing Optimisation** — Analyse fare variance unexplained by distance to surface surge pricing patterns
- **Rating Inflation Research** — Study bilateral rating behaviour and its relationship to ride outcomes

---

## 🚀 Getting Started

```python
import pandas as pd

# Load the dataset
df = pd.read_csv('Uber_Data_Analytics.csv')

# Basic inspection
print(df.shape)       # (148770, 21)
print(df.dtypes)
print(df.isnull().sum())

# Normalise column names
df.columns = df.columns.str.strip().str.lower().str.replace(" ", "_")

# Filter completed rides only
completed = df[df['booking_status'] == 'Completed']

# Revenue by vehicle type
revenue = df.groupby('vehicle_type')['booking_value'].sum().sort_values(ascending=False)
print(revenue)
```

### Recommended Libraries

| Library | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, aggregation |
| `matplotlib` / `seaborn` | Visualisation |
| `scikit-learn` | Classification and regression models |
| `scipy` | Statistical analysis |
| `plotly` | Interactive dashboards |

---

## 📄 License

This dataset is provided for educational and analytical purposes. Please refer to the source terms before redistribution or commercial use.

---

*Dataset covers Uber ride operations — Year 2024 | 148,770 total bookings | 21 features*

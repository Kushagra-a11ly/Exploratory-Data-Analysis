![image alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/e1e8f6b4280c6039db20a2fc21d298099a29518a/Car%20%20Price%20Analysis/dataset-cover.jpeg)


# 🚗 Automobile Market Dataset

## Overview

This dataset provides a comprehensive collection of automobile records designed for use in data analysis, machine learning, and statistical modeling within the automotive domain. It captures a wide range of vehicle attributes — from technical specifications to market pricing — making it a versatile resource for researchers, data scientists, and analysts exploring the used and new car market.

---

## Dataset Summary

| Attribute        | Details                          |
|------------------|----------------------------------|
| **Total Records**    | 2,500 rows                   |
| **Total Features**   | 10 columns                   |
| **File Format**      | CSV                          |
| **Domain**           | Automotive / Market Analysis |
| **Use Case**         | Pricing Prediction, Trend Analysis, Vehicle Comparison |

---

## Features Description

| Column         | Type        | Description                                              |
|----------------|-------------|----------------------------------------------------------|
| `Brand`        | Categorical | Manufacturer of the vehicle (e.g., Toyota, BMW, Tesla)   |
| `Model`        | Categorical | Specific model name (e.g., Corolla, X5, Model S)         |
| `Year`         | Integer     | Year of manufacture (2000–2024)                          |
| `Engine_Size`  | Float       | Engine displacement in litres (1.0–6.0)                  |
| `Fuel_Type`    | Categorical | Type of fuel used (Petrol, Diesel, Electric, Hybrid)     |
| `Transmission` | Categorical | Gearbox type (Manual or Automatic)                       |
| `Mileage`      | Integer     | Total kilometres/miles driven by the vehicle             |
| `Condition`    | Categorical | Vehicle condition rating (New, Used, Like New)           |
| `Price`        | Integer     | Market price of the vehicle in local currency (₹)        |

---

## Potential Use Cases

- **Price Prediction** — Build regression models to estimate vehicle market value based on specs and condition
- **Market Trend Analysis** — Explore how pricing, fuel type preferences, and brand share evolve over time
- **Vehicle Segmentation** — Cluster vehicles by attributes to identify distinct market segments
- **Brand Benchmarking** — Compare brands across price, mileage, and inventory distribution
- **Transmission & Fuel Insights** — Analyze consumer preference patterns across vehicle categories

---

## Key Observations

- All seven brands (Tesla, BMW, Audi, Ford, Honda, Mercedes, Toyota) are nearly equally represented at ~14–15% market share each
- Average prices across brands fall within a narrow ₹51,000–₹54,000 range, indicating low price differentiation by brand alone
- No strong linear correlation exists between any two numerical features, making this dataset well-suited for non-linear and ensemble modeling approaches
- Manual transmission vehicles slightly outnumber Automatic across all brands

---

## Data Quality

- ✅ No missing values
- ✅ Consistent formatting across all columns
- ✅ Balanced class distribution across categorical variables
- ✅ Ready for use without additional preprocessing

---

## License & Usage

This dataset is intended for educational, research, and non-commercial analytical purposes. Please ensure appropriate attribution if used in published work or shared projects.

---

## Author Notes

> Each row in this dataset represents a single vehicle and its complete set of associated attributes. The data has been structured and cleaned to ensure immediate usability in statistical workflows, visualization pipelines, and machine learning experiments without requiring extensive preprocessing.





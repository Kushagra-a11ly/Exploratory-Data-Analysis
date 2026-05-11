![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/e65152d2b26f90536a2777d7efd25c5bdbe18163/CarDekho%20Used%20Car%20Dataset%20Analysis/dataset-cover.png)

# 🚗 CarDekho Used Car Dataset

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-4c72b0?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML%20Ready-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Domain](https://img.shields.io/badge/Domain-Automotive%20%7C%20India-orange?style=for-the-badge)
![Task](https://img.shields.io/badge/Task-Price%20Prediction-red?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)

---

## 📌 About the Dataset

The used car market in India is a **dynamic and ever-changing landscape**. Prices can fluctuate wildly based on a variety of factors including the make and model of the car, its mileage, its condition, and the current market conditions. As a result, it can be difficult for sellers to accurately price their cars.

This dataset contains detailed information about used cars listed for sale, and can be used for a wide range of purposes — most notably **Used Car Price Prediction** using various Machine Learning techniques.

---

## 🎯 Use Cases

- Used Car Price Prediction (Regression)
- Market Trend Analysis
- Brand & Fuel Type Segmentation
- Feature Importance & Correlation Studies
- Exploratory Data Analysis (EDA)

---

## 📁 Dataset Overview

| Property | Details |
|---|---|
| Domain | Automotive / Used Car Market (India) |
| Primary Task | Supervised Regression (Price Prediction) |
| Format | CSV |
| Total Features | 12 |
| Target Variable | `selling_price` |

---

## 🧾 Feature Information

| # | Feature | Type | Description |
|---|---|---|---|
| 1 | `car_name` | Categorical | Full name of the car including brand and specific model |
| 2 | `brand` | Categorical | Brand name of the particular car |
| 3 | `model` | Categorical | Exact model name of the car under a particular brand |
| 4 | `seller_type` | Categorical | Type of seller listing the used car (Individual / Dealer / Trustmark Dealer) |
| 5 | `fuel_type` | Categorical | Fuel type used in the car (Petrol / Diesel / CNG / LPG / Electric) |
| 6 | `transmission_type` | Categorical | Transmission type of the car (Manual / Automatic) |
| 7 | `vehicle_age` | Numerical | Number of years since the car was originally purchased |
| 8 | `mileage` | Numerical | Fuel efficiency — kilometers the car runs per litre (kmpl) |
| 9 | `engine` | Numerical | Engine displacement capacity in CC (cubic centimeters) |
| 10 | `max_power` | Numerical | Maximum power output of the engine in BHP |
| 11 | `seats` | Numerical | Total number of seating capacity in the car |
| 12 | `selling_price` | Numerical | 🎯 Target — the listed sale price on the platform (in INR) |

---

## 🔍 Key Highlights

- **Maruti** is the most listed brand, reflecting its dominance in India's mass-market used car segment.
- **Petrol and Diesel** together account for over 95% of all fuel types in the dataset.
- **Manual transmission** vehicles make up approximately 80% of listings.
- **Max Power** and **Engine Capacity** are the strongest numerical predictors of selling price.
- The dataset contains significant **price outliers** from ultra-luxury brands like Ferrari and Rolls-Royce.

---

## 🛠️ Recommended Preprocessing Steps

- Handle missing values in `mileage`, `engine`, `max_power`, and `seats`
- Apply **log transformation** on `selling_price` to handle right-skew
- **Label encode** or **one-hot encode** categorical features (`fuel_type`, `transmission_type`, `seller_type`)
- Remove or cap **outliers** using IQR or Z-score methods
- Drop `car_name` and `model` or use them for feature engineering (e.g., extract trim level)

---

## 📊 Suggested ML Models

| Model | Use Case |
|---|---|
| Linear Regression | Baseline model |
| Ridge / Lasso Regression | Regularized baseline with multicollinearity control |
| Random Forest Regressor | Non-linear relationships, feature importance |
| Gradient Boosting (XGBoost / LightGBM) | High accuracy, handles mixed feature types |
| Support Vector Regression | Robust to outliers |

---

## 📦 Libraries Required

```python
pip install pandas numpy matplotlib seaborn scikit-learn scipy xgboost lightgbm
```

---

## 🚀 Quick Start

```python
import pandas as pd

df = pd.read_csv('CarDekho Used Car Dataset.csv')

print(df.shape)
print(df.head())
print(df.info())
print(df.describe())
print(df.isnull().sum())
```

---

## 📜 License

This project is licensed under the **MIT License** — free to use for educational and research purposes.

---

> **Dataset:** CarDekho Used Car Dataset
> **Domain:** Indian Automotive Market
> **Tools:** Python · Pandas · Seaborn · Matplotlib · Scikit-Learn

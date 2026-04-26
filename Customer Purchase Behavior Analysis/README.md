🛍️ Customer Shopping Behavior Dataset

A structured, transaction-level dataset capturing retail and e-commerce customer behavior — built for exploratory analysis, segmentation, forecasting, and machine learning.

Table of Contents

Overview
Objectives
Dataset Structure
Feature Reference
Use Cases
Getting Started
Notes & Considerations


Overview
This dataset provides a comprehensive view of customer shopping behavior across retail and e-commerce channels. Each row represents a single customer transaction, combining demographic attributes with detailed purchase and behavioral data.
It is designed to support data-driven decision-making in areas such as:

Marketing optimization
Customer segmentation
Demand forecasting
Business intelligence


Objectives
#Goal1Understand customer purchasing behavior across demographics2Identify trends in age, gender, and geographic segments3Analyze the impact of discounts and promotional strategies4Evaluate seasonal effects on sales volume and spend5Study payment preferences and transaction patterns6Support predictive modeling and recommendation systems

Dataset Structure
Type        : Structured (Tabular)
Granularity : Transaction-level
Variables   : Mix of categorical and numerical features
Format      : CSV / Tabular
The dataset combines four categories of information:

Customer Demographics — Who is buying
Product Information — What is being bought
Transaction Details — How and when it was purchased
Behavioral Indicators — Purchase frequency, loyalty signals, and preferences


Feature Reference
ColumnTypeDescriptionCustomer IDCategoricalUnique identifier for each customerAgeNumericalCustomer age in yearsGenderCategoricalCustomer gender (Male / Female)Item PurchasedCategoricalName of the specific product purchasedCategoryCategoricalProduct category (e.g., Clothing, Accessories, Footwear)Purchase Amount (USD)NumericalTotal transaction value in US dollarsLocationCategoricalCustomer's geographic region or stateSizeCategoricalItem size (S, M, L, XL, etc.)ColorCategoricalColor of the purchased productSeasonCategoricalSeason of purchase (Spring, Summer, Fall, Winter)Review RatingNumericalCustomer product rating (1–5 scale)Subscription StatusCategoricalWhether the customer has an active subscription (Yes / No)Payment MethodCategoricalPayment method used in this transactionShipping TypeCategoricalDelivery option selected (Standard, Express, etc.)Discount AppliedCategoricalWhether a discount was applied (Yes / No)Promo Code UsedCategoricalWhether a promo code was used (Yes / No)Previous PurchasesNumericalTotal number of prior purchases by the customerPreferred Payment MethodCategoricalCustomer's habitual payment preferenceFrequency of PurchasesCategoricalPurchase cadence (Weekly, Monthly, Annually, etc.)

Note: Payment Method and Preferred Payment Method are distinct fields.
The former reflects what was used in a specific transaction; the latter reflects the customer's stated or historical preference.


Use Cases
Exploratory Data Analysis (EDA)

Visualize spending trends across age groups, genders, and regions
Identify seasonal purchase spikes and category performance
Analyze product popularity and review rating distributions

Customer Segmentation

Cluster customers by purchase frequency, spend, and loyalty indicators
Identify high-value customers and at-risk churners
Build targeted campaigns for distinct behavioral groups

Revenue & Sales Analysis

Measure the uplift from discounts and promo codes
Calculate average order value (AOV) across segments
Benchmark performance by location, category, or season

Predictive Modeling

Build churn prediction or lifetime value (LTV) models
Develop product recommendation systems
Forecast demand by category and season


Getting Started
1. Load the Dataset
Python
pythonimport pandas as pd

df = pd.read_csv("shopping_behavior.csv")
print(df.shape)
df.head()
R
rdf <- read.csv("shopping_behavior.csv")
head(df)
2. Initial Exploration
python# Summary statistics
df.describe(include="all")

# Missing value audit
df.isnull().sum()

# Distribution of key columns
df["Category"].value_counts()
df["Purchase Amount (USD)"].hist(bins=30)
3. Preprocessing Checklist

 Encode categorical variables (Label Encoding or One-Hot Encoding)
 Normalize/scale numerical features for ML pipelines
 Handle missing or inconsistent values
 Verify distinction between Payment Method and Preferred Payment Method
 Parse or bin Age and Frequency of Purchases as needed


Notes & Considerations

Categorical Encoding — Most columns are categorical and will require encoding before use in machine learning models.
Duplicate Detection — Verify that Customer ID entries are unique per transaction vs. per customer to avoid miscounting.
Feature Leakage — Take care when using behavioral fields (e.g., Previous Purchases) in predictive models to avoid data leakage.
Scalability — The dataset structure is designed to scale; performance-sensitive operations should account for dataset size.
Privacy — While the dataset does not contain PII beyond anonymized IDs, handle it in compliance with applicable data privacy regulations.


License
Specify the applicable license here (e.g., MIT, CC BY 4.0, or proprietary).

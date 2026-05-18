![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/82a79030d32cf98004f2bc0a11603c58ffac2ee9/Olympics%20Athletes%20Dataset%20(1896%E2%80%932024)/Dataset%20Cover.png)



# Olympic Athletes — Exploratory Data Analysis Report

**Dataset:** `olympics_athletes_dataset.csv`
**Prepared by:** EDA Pipeline · Python (pandas · seaborn · matplotlib · scipy)
**Scope:** 8,500 athletes · 30 features · Summer & Winter Games · 1896–2024

---

## 1. Executive Summary

This report presents a comprehensive exploratory data analysis of 8,500 Olympic athletes spanning 128 years of Summer and Winter Games. The dataset is structurally clean — no missing values, no duplicates — and gender-balanced to within 0.3%. However, systematic uniformity across age, sport frequency, coach assignments, and categorical flags strongly indicates a **synthetically generated dataset** rather than one drawn from official Olympic records. Findings should be treated as illustrative rather than empirically conclusive.

The most analytically credible signal resides in country-level medal and ranking data, the height-weight relationship (when conditioned on sport), and the gold-to-total-medals ratio. Three columns — `coach_name`, `is_record_holder`, and `total_olympics_attended` — carry no predictive signal and should be dropped before any modelling.

---

## 2. Dataset Overview

| Property | Value |
|---|---|
| Rows | 8,500 |
| Columns | 30 |
| Missing values | 0 |
| Duplicate rows | 0 |
| Time span | 1896 – 2024 |
| Sports (unique) | 33 |
| Games types | Summer, Winter |

### 2.1 Key Columns

| Column | Type | Description |
|---|---|---|
| `athlete_id` | object | Unique athlete identifier |
| `athlete_name` | object | Full name |
| `gender` | object | Male / Female |
| `age` | int64 | Age at competition |
| `sport` | object | Sport category (33 unique) |
| `games_type` | object | Summer or Winter |
| `medal` | object | Medal type won |
| `total_medals_won` | int64 | Cumulative medals per athlete |
| `gold_medals` | int64 | Gold medal count |
| `height_cm` | float64 | Athlete height |
| `weight_kg` | float64 | Athlete weight |
| `country_total_medals` | int64 | Country's all-time medal tally |
| `country_best_rank` | int64 | Best Olympic ranking achieved |

---

## 3. Data Quality Assessment

### 3.1 Completeness and Duplicates

```python
df.isnull().sum()      # → 0 missing values across all 30 columns
df.duplicated().sum()  # → 0 duplicate rows
```

The dataset passes both checks cleanly, requiring no imputation or deduplication.

### 3.2 Outlier Detection (IQR Method)

```python
Q1  = df['height_cm'].quantile(0.25)
Q3  = df['height_cm'].quantile(0.75)
IQR = Q3 - Q1
outliers = df[(df['height_cm'] < Q1 - 1.5*IQR) | (df['height_cm'] > Q3 + 1.5*IQR)]
# → 20 outliers detected
```

Twenty height outliers were identified (213–215 cm), all belonging to Basketball players. These are legitimate values consistent with the sport's physical demands and should be **retained**.

---

## 4. Distribution Analysis

### 4.1 Age

```python
from scipy.stats import skew
skew(df['age'])   # → -0.006  (near-perfectly symmetric)
df['age'].kurt()  # → -1.201  (platykurtic / flat distribution)
```

Ages 15–41 are almost uniformly distributed, with approximately 280–320 athletes per bin. This flat pattern is inconsistent with real Olympic data, which typically peaks sharply at ages 22–26. It strongly signals deliberate age-group balancing during dataset construction.

### 4.2 Physical Attributes

| Feature | Skewness | Interpretation |
|---|---|---|
| `height_cm` | 0.096 | Near-symmetric |
| `weight_kg` | 0.750 | Moderate right skew |

Weight's right skew is plausible — a small number of heavier athletes (weightlifters, wrestlers) pull the tail rightward. Height is more evenly spread across the population.

### 4.3 Gender Distribution

Female athletes: 4,263 (50.15%) · Male athletes: 4,237 (49.85%) — a difference of less than 0.3%. This near-perfect balance is ideal for binary classification tasks without any resampling strategy.

---

## 5. Medal Analysis

### 5.1 Medal Type Totals

| Medal | Count |
|---|---|
| Gold | ~17,200 |
| Silver | ~8,700 |
| Bronze | ~9,100 |

Gold medals outnumber silver and bronze by roughly 2:1. The most likely explanation is that **team sports credit every squad member** with a gold medal, inflating the gold count disproportionately. For per-athlete success metrics, `total_medals_won` is the more reliable target variable.

### 5.2 Gold Medals by Gender

Both genders share identical distributions: median 1 gold, IQR 0–3, upper whisker 7, with symmetric outliers at 8 golds. This is another marker of synthetic balancing — real data would show variance by sport and era.

### 5.3 Team vs. Individual Performance

Both team and individual athletes share identical medians (4 medals) and IQRs (2–6), suggesting medals were counted per event rather than inflated per squad member at the athlete level.

---

## 6. Sport and Event Analysis

### 6.1 Most Popular Sports

All top 10 sports hold between 265–285 athletes — a spread of less than 8%. Boxing and Luge share the top spot, an implausible pairing in unsampled data given their very different scales in real Games. This confirms uniform sport-level sampling across Summer and Winter Games.

### 6.2 Top Sports by Medal Yield

Luge leads total medal counts at approximately 1,250. In real Olympic data, Swimming and Athletics dominate by a large margin. Luge's top ranking implies per-athlete medal normalisation rather than raw event counting.

### 6.3 Height Distribution by Sport

| Sport | Median Height | Notes |
|---|---|---|
| Basketball | ~190 cm | Highest; max ~215 cm |
| Gymnastics (Artistic) | ~170 cm | Lowest; tight IQR |
| Boxing / Weightlifting / Wrestling | Mixed | Widest IQRs due to weight-class variation |

---

## 7. Country-Level Analysis

### 7.1 Total Medals — Top 10 Countries

Hungary and Australia lead with approximately 1,030 medals each. The entire top 10 falls within a 14% range — unusually compressed compared to real-world Olympic standings, where the USA typically dominates by a large margin. This reinforces the data-balancing hypothesis.

### 7.2 Gold Medals by Country

Hungary (~535) and Germany (~515) lead. The remaining eight nations cluster between 450–485 golds, a 7% spread.

### 7.3 Country Rank vs. Total Medals

This is the **most analytically credible chart** in the dataset. The rank–medals relationship follows a textbook power-law decay:

- Rank 1: ~2,650 medals
- Rank 2: ~1,100 medals (2.4× lower)
- Rank 20+: 50–200 medals (plateau)

This structural pattern mirrors real Olympic data and is suitable for country-level modelling.

### 7.4 Top Host Cities

Athens dominates at 20.3% of total medals (hosted 1896 + 2004). London accounts for 14.4% and Paris 13.7%, together totalling 28.1%. Modern single-edition Summer hosts (Tokyo, Atlanta, Rio) each contribute approximately 7% — a consistent volume reflective of Games size growth.

---

## 8. Temporal Analysis

### 8.1 Medals Over Time (1896–2024)

Key structural breaks in the time series:

- **1920–1932:** Sharp drop due to World War cancellations (1916, 1940, 1944 Games not held)
- **Post-1992:** Sawtooth oscillation caused by mixing Summer and Winter Games on a single time axis

**Recommendation:** Always split the series by `games_type` before any time-series modelling. The mixed axis creates artificial periodicity that would corrupt trend and forecasting models.

---

## 9. Correlation Analysis

### 9.1 Heatmap Summary

| Feature Pair | Correlation | Interpretation |
|---|---|---|
| `country_total_gold` ↔ `country_total_medals` | **0.99** | Near-perfect collinearity — use only one |
| `total_medals_won` ↔ `gold_medals` | **0.62** | Gold is the strongest individual predictor |
| `country_best_rank` ↔ `country_total_medals` | **−0.59** | Better rank correlates with more medals |
| `height_cm` ↔ `weight_kg` | **0.21** | Weak positive anthropometric link |
| `age` ↔ any medal column | **~0.00** | Age carries no predictive signal |

### 9.2 Weight vs. Medals

Medal counts form discrete horizontal bands (0–9) across all weight ranges with no gradient. Weight alone has zero predictive power for medal success in isolation.

---

## 10. Suspicious / Synthetic Columns

### 10.1 Coach Name

All top 10 coaches manage 308–328 athletes — only a 6% spread — despite vastly different sporting backgrounds. This distribution is almost certainly synthetically assigned. The `coach_name` column carries no analytical signal.

### 10.2 Record Holder Flag

All three `is_record_holder` groups (No / Olympic Record / World Record) share identical medians and IQRs for `total_medals_won`. In real data, record holders would be clear right-tail outliers. The flag appears randomly assigned.

### 10.3 Total Olympics Attended

All five violin distributions (1–5 Games attended) are nearly identical in shape, spread, and median. No career-lifecycle pattern is detectable — experienced multi-Games athletes show no medal advantage over one-time competitors.

---

## 11. Feature Audit & Modelling Recommendations

| Feature | Signal Quality | Recommendation |
|---|---|---|
| `gold_medals`, `total_medals_won` | ✅ Strong | Use as target or primary feature |
| `country_best_rank`, `country_total_medals` | ✅ Credible | Use for country-level modelling |
| `height_cm`, `weight_kg` | ✅ Moderate | Include with `sport` as control variable |
| `sport`, `gender`, `games_type` | ⚠️ Balanced | Control variables only — frequency carries no signal |
| `age` | ⚠️ Caution | Artificially uniform — treat carefully |
| `coach_name` | ❌ Synthetic | Drop entirely |
| `is_record_holder` | ❌ Random | Drop entirely |
| `total_olympics_attended` | ❌ No signal | Exclude from models |

---

## 12. Key Caveats

1. **Synthetic dataset.** Uniform distributions across most categorical features indicate this data was generated rather than sourced from official Olympic records. Insights are illustrative, not empirically conclusive.

2. **Summer and Winter Games are mixed.** Sport-level and time-series analyses must filter by `games_type` to avoid misleading comparisons.

3. **Gold medal inflation.** Team event credits inflate gold counts per athlete; treat `total_medals_won` as the primary success metric.

4. **Country-level collinearity.** `country_total_gold` and `country_total_medals` (r = 0.99) must not both appear in any regression or tree-based model.

5. **Outliers are valid.** The 20 height outliers (Basketball, 213–215 cm) are sport-appropriate and should not be removed.

---

## 13. Recommended Next Steps

1. **Filter before analysing.** Separate Summer and Winter Games as a preprocessing step for all downstream tasks.
2. **Drop zero-signal columns.** Remove `coach_name`, `is_record_holder`, and `total_olympics_attended` before feature selection.
3. **Use sport as a conditioning variable.** Height and weight relationships are only interpretable within sport categories.
4. **Choose one country medal metric.** Drop `country_total_gold` and retain `country_total_medals` (or vice versa) to eliminate collinearity.
5. **Treat this as a classification benchmark dataset.** The balanced gender split and clean structure make it well-suited for binary or multi-class medal prediction experiments.

---

*Analysis performed using Python · pandas · numpy · seaborn · matplotlib · scipy.stats*

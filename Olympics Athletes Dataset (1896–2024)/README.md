![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/82a79030d32cf98004f2bc0a11603c58ffac2ee9/Olympics%20Athletes%20Dataset%20(1896%E2%80%932024)/Dataset%20Cover.png)



# Olympic Athletes — Exploratory Data Analysis

A comprehensive EDA of 8,500 Olympic athletes spanning Summer and Winter Games from 1896 to 2024, uncovering patterns in performance, physical attributes, country dominance, and sport participation.

---

## Dataset Overview

| Property | Value |
|---|---|
| **File** | `olympics_athletes_dataset.csv` |
| **Rows** | 8,500 athletes |
| **Columns** | 30 features |
| **Missing Values** | None |
| **Duplicates** | None |
| **Time Span** | 1896 – 2024 |

### Key Columns

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

## Tech Stack

```
Python 3.x
├── pandas          — data loading, cleaning, grouping
├── numpy           — numerical operations
├── matplotlib      — base plotting
├── seaborn         — statistical visualisations
└── scipy.stats     — skewness, kurtosis
```

---

## EDA Workflow

### 1. Data Loading & Inspection

```python
df = pd.read_csv('olympics_athletes_dataset.csv')
df.shape        # (8500, 30)
df.info()       # dtypes, non-null counts
df.describe()   # statistical summary
```

### 2. Data Quality Checks

```python
df.isnull().sum()       # → 0 missing values across all columns
df.duplicated().sum()   # → 0 duplicate rows
```

### 3. Outlier Detection (IQR Method)

```python
Q1 = df['height_cm'].quantile(0.25)
Q3 = df['height_cm'].quantile(0.75)
IQR = Q3 - Q1
outliers = df[(df['height_cm'] < Q1 - 1.5*IQR) | (df['height_cm'] > Q3 + 1.5*IQR)]
# → 20 outliers detected, all Basketball players (213–215 cm)
```

### 4. Distribution Analysis

```python
skew(df['age'])         # → -0.006  (near-perfectly symmetric)
df['age'].kurt()        # → -1.201  (platykurtic / flat)
skew(df['height_cm'])   # →  0.096  (slight right skew)
skew(df['weight_kg'])   # →  0.750  (moderate right skew)
```

---

## Visualisations & Key Findings

### 1 · Gender Distribution
> `sns.countplot` — Female: 4,263 · Male: 4,237 (< 1% difference)

The dataset is near-perfectly balanced by gender — ideal for classification modelling without any resampling.

---

### 2 · Medal Type Distribution
> `df[['gold_medals','silver_medals','bronze_medals']].sum().plot(kind='bar')`

Gold medals (~17,200) outnumber Silver (~8,700) and Bronze (~9,100) by roughly 2:1. The likely cause is team sports crediting every squad member with a gold medal, inflating the gold count disproportionately.

---

### 3 · Age Distribution
> `sns.histplot` with KDE overlay

Ages 15–41 are almost uniformly distributed (~280–320 athletes per bin) — a flat pattern inconsistent with real Olympic data, which typically peaks at 22–26. This signals deliberate dataset balancing across age groups.

---

### 4 · Height vs. Weight (by Gender)
> `sns.scatterplot` coloured by gender

A clear positive correlation exists between height and weight. Female athletes cluster at 155–180 cm / 50–100 kg; males span 165–210 cm / 60–130 kg. The widest weight spread appears in the 170–190 cm band, reflecting the most diverse athletic profiles.

---

### 5 · Top 10 Countries by Total Medals
> `groupby('country_name')['total_medals_won'].sum()`

Hungary and Australia lead (~1,030 medals each), with the entire top 10 compressed into a 14% range — unusually tight compared to real-world Olympic tallies. Suggests normalised or sampled country-level data.

---

### 6 · Top Gold Medal Countries
> Bar chart coloured gold

Hungary (~535) and Germany (~515) lead by a clear margin. The remaining eight nations cluster between 450–485 golds — a 7% spread that reinforces the data-balancing hypothesis.

---

### 7 · Most Popular Sports
> `df['sport'].value_counts().head(10)`

All top 10 sports hold between 265–285 athletes (< 8% spread). Boxing and Luge share the top spot — an implausible pairing in unsampled data, confirming uniform sport-level sampling across Summer and Winter Games.

---

### 8 · Top Sports by Medal Yield
> `groupby('sport')['total_medals_won'].sum()`

Luge leads at ~1,250 total medals. In real Olympic data, Swimming and Athletics dominate — Luge's top ranking suggests per-athlete medal normalisation rather than raw counting.

---

### 9 · Team vs. Individual Performance
> `sns.boxplot` — `team_or_individual` vs `total_medals_won`

Both groups share identical medians (4 medals) and IQRs (2–6). No format advantage exists at the athlete level, suggesting medals were counted per event rather than per squad member.

---

### 10 · Height Distribution by Sport
> `sns.boxplot` — sport vs height

**Basketball** has the highest median (~190 cm, max ~215 cm). **Gymnastics (Artistic)** sits at the opposite extreme (~170 cm, tight IQR). **Boxing**, **Weightlifting**, and **Wrestling** show the widest IQRs, reflecting weight-class variation across divisions.

---

### 11 · Weight vs. Medals
> `sns.scatterplot`

Medal counts form discrete horizontal bands (0–9) across all weight ranges. No correlation exists — weight has zero predictive power for medal success in isolation.

---

### 12 · Top Coaches by Athlete Count
> `df['coach_name'].value_counts().head(10)`

All top 10 coaches manage 308–328 athletes (only 6% spread). Given the vastly different sporting backgrounds of these coaches, this distribution is almost certainly synthetically assigned — the coach column carries no analytical signal.

---

### 13 · Record Holders vs. Medals
> `sns.boxplot` — `is_record_holder` vs `total_medals_won`

All three groups (No / Olympic Record / World Record) share identical medians and IQRs. In real data, record holders should be clear outliers on the right. This strongly suggests `is_record_holder` was randomly assigned and should be dropped from any predictive model.

---

### 14 · Medals Over Time (1896–2024)
> `groupby('year')['total_medals_won'].sum().plot()`

Key structural breaks:
- **1920–1932**: sharp drop due to WWI/WWII Games cancellations
- **Post-1992**: sawtooth oscillation caused by mixing Summer and Winter Games on one axis

**Recommendation**: split Summer and Winter series before any time-series modelling.

---

### 15 · Top Host Cities
> Pie chart — percentage share of total medals

Athens dominates at 20.3% (hosted 1896 + 2004). London (14.4%) and Paris (13.7%) together account for 28.1%. Modern single-edition Summer cities (Tokyo, Atlanta, Rio) each hold ~7% — remarkably consistent volumes.

---

### 16 · Experience vs. Medals
> `sns.violinplot` — `total_olympics_attended` vs `total_medals_won`

All five violins (1–5 Games attended) are nearly identical in shape and median. No career-lifecycle pattern is detectable — `total_olympics_attended` carries no predictive signal and should be excluded from models.

---

### 17 · Country Rank vs. Total Medals
> `sns.scatterplot`

The most analytically credible chart in the dataset. A textbook power-law decay: the rank-1 country holds ~2,650 medals — nearly 2.4× the rank-2 country (~1,100). The curve flattens after rank 20 at 50–200 medals, reflecting structural ceilings for mid-tier nations.

---

### 18 · Top Events by Athlete Count
> `df['event'].value_counts().head(10)`

Men's Singles leads (~185 athletes), followed by Women's Singles (~165) and Mixed Team (~158). The co-presence of Football and Ice Hockey in the same top 10 confirms Summer and Winter athlete pools are not separated in this dataset.

---

### 19 · Gold Medals by Gender
> `sns.boxplot`

Identical medians (1 gold), IQRs (0–3), and upper whiskers (7) for both genders. Outliers at 8 golds appear symmetrically — another marker of synthetic balancing.

---

### 20 · Correlation Heatmap
> `sns.heatmap` on all numeric columns

| Feature Pair | Correlation | Interpretation |
|---|---|---|
| `country_total_gold` ↔ `country_total_medals` | **0.99** | Near-perfect collinearity — use one only |
| `total_medals_won` ↔ `gold_medals` | **0.62** | Gold is the strongest individual predictor |
| `country_best_rank` ↔ `country_total_medals` | **-0.59** | Better rank ↔ more medals |
| `height_cm` ↔ `weight_kg` | **0.21** | Weak positive anthropometric link |
| `age` ↔ any medal column | ~0.00 | Age is not a performance predictor here |

---

## Dataset Audit Summary

| Feature | Signal Quality | Recommendation |
|---|---|---|
| `gold_medals`, `total_medals_won` | ✅ Strong | Use as target or feature |
| `country_best_rank`, `country_total_medals` | ✅ Credible | Use for country-level modelling |
| `height_cm`, `weight_kg` | ✅ Moderate | Use with sport as control variable |
| `sport`, `gender`, `games_type` | ⚠️ Balanced | Control variable only — frequency carries no signal |
| `coach_name` | ❌ Synthetic | Drop entirely |
| `is_record_holder` | ❌ Random | Drop entirely |
| `total_olympics_attended` | ❌ No signal | Exclude from models |
| `age` | ❌ Uniform | Treat with caution — artificially balanced |

---

## Key Caveats

1. **Synthetic dataset** — uniform distributions across most categorical features indicate this data was generated rather than sourced from official Olympic records. Insights are illustrative, not empirically conclusive.
2. **Summer + Winter Games are mixed** — sport-level and time-series analyses must filter by `games_type` to avoid misleading comparisons.
3. **Gold medal inflation** — team event credits inflate gold counts; treat `total_medals_won` as the primary success metric.
4. **Country-level collinearity** — `country_total_gold` and `country_total_medals` (r = 0.99) should not both appear in any model.

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/your-username/olympics-eda.git
cd olympics-eda

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scipy

# 3. Launch the notebook
jupyter notebook olympics_eda.ipynb
```

Ensure `olympics_athletes_dataset.csv` is in the same directory as the notebook.

---

## Project Structure

```
olympics-eda/
│
├── olympics_athletes_dataset.csv   # Source dataset
├── olympics_eda.ipynb              # Main analysis notebook
├── README.md                       # This file
└── plots/                          # Exported chart images (optional)
```

---

*Analysis performed using Python · pandas · seaborn · matplotlib · scipy*

*Analysis performed using Python · pandas · numpy · seaborn · matplotlib · scipy.stats*

# 🏅 Olympics Athletes EDA (1896–2024)

> A structured, visual-first Exploratory Data Analysis of 8,500+ Olympic athletes across 128 years of Summer and Winter Games — uncovering medal patterns, country dominance, athlete body profiles, and key modelling insights.

---

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=python&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-FA0F00?style=for-the-badge&logo=jupyter&logoColor=white)

---

## 📌 Project Overview

This notebook performs a full EDA on the Olympics Athletes Dataset — covering data loading, cleaning, univariate and bivariate analysis, outlier detection, and advanced grouping. Every visualization is paired with professional analyst-grade insights to surface patterns, flag data quality issues, and guide downstream modelling decisions.

| Property | Details |
|---|---|
| **Dataset** | `olympics_athletes_dataset.csv` |
| **Rows** | 8,500+ |
| **Columns** | 30 |
| **Games Covered** | Summer (1896–2024) · Winter (1924–2022) |
| **Analysis Questions** | 19 |
| **Notebook** | `eda.ipynb` |

---

## 📂 Repository Structure

```
├── olympics_athletes_dataset.csv   # Raw dataset
├── eda.ipynb                       # Main EDA notebook
├── visuals/                        # Exported chart images
└── README.md
```

---

## 🔧 Setup & Installation

```bash
# Clone the repository
git clone https://github.com/your-username/olympics-eda.git
cd olympics-eda

# Install dependencies
pip install pandas numpy matplotlib seaborn scipy

# Launch notebook
jupyter notebook eda.ipynb
```

---

## 🧹 Data Loading & Cleaning

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

df = pd.read_csv('olympics_athletes_dataset.csv')

# Inspection
df.shape         # (8500+, 30)
df.info()        # Data types and non-null counts
df.describe()    # Statistical summary

# Cleaning
df.isnull().sum()           # Missing value check
df.duplicated().sum()       # Duplicate check
df.drop_duplicates(inplace=True)
```

---

## 📊 EDA Questions & Insights

---

### Q1 — Who participates more?
**Gender Distribution of Athletes**

```python
sns.countplot(x='gender', data=df, hue='gender', palette='Set2', legend=False)
```

- The dataset is remarkably balanced — Female (~4,250) and Male (~4,200) athletes are nearly equal, with less than a **1% difference** between the two groups.
- Near-perfect parity suggests a deliberately balanced sampling strategy or mirrored male/female event categories across sports.
- Binary gender classification is a dataset limitation worth noting for inclusive analyses.
- From a modelling perspective this is ideal — no class imbalance corrections (SMOTE, class weights) will be needed for gender as a feature.

---

### Q2 — Which medal is most common?
**Total Medal Distribution**

```python
df[['gold_medals','silver_medals','bronze_medals']].sum().plot(
    kind='bar', color=['#FFD700','#C0C0C0','#CD7F32']
)
```

- Gold medals (~17,200) outnumber Silver (~8,700) and Bronze (~9,100) by nearly **2:1** — striking given that gold, silver, and bronze should theoretically be equal per event.
- Silver and Bronze differ by less than 5% — the real anomaly is gold's disproportionate dominance, likely from team sports crediting every squad member.
- Treating total medals as a single success metric may be more reliable than weighting by type for modelling purposes.

---

### Q3 — What is the peak athlete age?
**Age Distribution**

```python
sns.histplot(df['age'], kde=True, color='skyblue', bins=30)
```

- Remarkably uniform between ages 15–41, holding steady at 280–320 athletes per bin — an unusually flat pattern vs. real data which peaks mid-20s.
- Two visible dips around 23–24 and 28–30 may reflect career transition points or data gaps.
- Athletes as young as 15 confirm inclusion of youth-eligible sports (gymnastics, swimming, figure skating).
- Flat distribution is a strong signal of **deliberate age-group balancing** — factor this in before drawing population-level conclusions.

---

### Q4 — Is there a relation between height and weight?
**Height vs Weight by Gender**

```python
sns.scatterplot(data=df, x='height_cm', y='weight_kg', hue='gender', palette='Spectral')
```

- Clear positive correlation between height and weight across both genders — taller athletes trend heavier as expected.
- Female athletes cluster between 155–180 cm / 50–100 kg; Males span 165–210 cm / 60–130 kg.
- Significant overlap in the 165–185 cm / 60–100 kg zone — sport diversity drives body type variation more than gender alone.
- High-weight outliers (120–150 kg) likely represent weightlifters, shot putters, or wrestlers.
- Widest weight spread occurs between 170–190 cm — the most diverse athletic height range.

---

### Q5 — Which countries dominate?
**Top 10 Countries by Medals**

```python
df.groupby('country_name')['total_medals_won'].sum().sort_values(ascending=False).head(10).plot(kind='bar')
```

- Top 10 compressed into a narrow ~14% range (Hungary/Australia ~1,030 → India ~890) — no single dominant nation, flagging possible normalization artifacts.
- Hungary and Australia are statistically tied at the top — an unexpected pairing given differences in population and sports infrastructure.
- India's top-10 appearance likely reflects hockey dominance across multiple cycles rather than broad multi-sport strength.
- Near-uniform bar heights are a **data quality red flag** — real Olympic tallies show far greater disparity.

---

### Q6 — Who wins the most gold?
**Top Gold Medal Countries**

```python
df.groupby('country_name')['gold_medals'].sum().sort_values(ascending=False).head(10).plot(kind='bar', color='gold')
```

- Hungary leads at ~535 gold, followed by Germany at ~515 — a clear two-tier hierarchy above a tightly clustered remaining eight (450–485).
- Germany's strong finish reflects combined East/West German historical tallies — inflating its standing vs. split analyses.
- Greece at fifth (~475) reflects host-nation advantages at the 1896 and 2004 Athens Games rather than sustained dominance.
- India and Bulgaria rank high in total medals but drop from the gold top 10 — signalling silver/bronze-heavy performance profiles.

---

### Q7 — Which sports have the most athletes?
**Most Popular Sports**

```python
df['sport'].value_counts().head(10).plot(kind='bar', colormap='coolwarm')
```

- All ten sports fall within a narrow 265–285 athlete band (< 8% spread) — almost certainly deliberate balancing, not real-world participation.
- Boxing and Luge tied at the top is analytically implausible — a global contact sport and a niche Winter discipline should not be equal.
- Summer and Winter sports mixed in one chart confirms the dataset pools both Games — control for this in sport-specific analysis.
- `sport` should be treated as a **categorical control variable**, not a popularity signal, in any predictive model.

---

### Q8 — Which sports generate the most medals?
**Top Sports by Total Medals**

```python
df.groupby('sport')['total_medals_won'].sum().sort_values(ascending=False).head(10).plot(kind='bar')
```

- Luge leads at ~1,250 medals ahead of Boxing and Biathlon (~1,200 each) — in real Olympic history, Swimming and Athletics far outpace all other sports.
- Luge's dominance suggests medal counts are normalized or weighted per athlete rather than counted raw.
- Rowing's inclusion (~1,115) is the most credible entry — legitimately high medal volumes due to its broad weight/boat-class event structure.

---

### Q9 — Which performs better — Team or Individual?
**Team vs Individual Performance**

```python
sns.boxplot(x='team_or_individual', y='total_medals_won', data=df, palette='Pastel1')
```

- Both groups share an identical median of **4 medals** with IQRs of 2–6 — sport format alone confers no medal advantage.
- Identical whiskers (0–9) across both groups means no format produces extreme outliers beyond the other.
- If team medals were credited per athlete, team athletes should theoretically accumulate faster — equality here suggests per-event counting or normalization.

---

### Q10 — Do different sports have different height profiles?
**Height Distribution by Sport**

```python
sns.boxplot(x='sport', y='height_cm', data=df, palette='Set3')
```

- Basketball records the highest median height (~190 cm) with upper whiskers reaching ~215 cm — height is a direct competitive advantage.
- Gymnastics (Artistic) sits at the opposite extreme (~170 cm median) with a compressed IQR — smaller builds optimized for rotational power.
- Volleyball and Rowing follow Basketball with medians ~188–190 cm — reach and leverage matter across net and water sports.
- Boxing, Weightlifting, and Wrestling show the widest IQRs — weight-class structure creates significant within-sport height variation.

---

### Q11 — Does weight influence success?
**Weight vs Total Medals**

```python
sns.scatterplot(x='weight_kg', y='total_medals_won', data=df, color='teal')
```

- No meaningful correlation — athletes across 40–150 kg appear at every medal level with near-equal density.
- Grid-like pattern (horizontal medal bands, vertical weight density) is the visual signature of a **discretized target variable** — consider binning medals (0, 1–3, 4–6, 7+) for classification modelling.

---

### Q12 — Do some coaches produce more winners?
**Top Coaches by Athlete Count**

```python
df['coach_name'].value_counts().head(10).plot(kind='bar')
```

- All ten coaches manage 308–328 athletes (6% spread) — the flattest distribution in the entire EDA.
- Coaches from completely different sporting backgrounds (equestrian, sprinting) showing equal rosters is statistically impossible in real data.
- `coach_name` is **almost certainly synthetically assigned** — drop this feature entirely from any predictive model.

---

### Q13 — Are record holders better performers?
**Record Holders vs Medals**

```python
sns.boxplot(x='is_record_holder', y='total_medals_won', data=df, palette='cool')
```

- All three groups (No / Olympic Record / World Record) share identical medians of 4 and IQRs of 2–6.
- World record holders should show a significantly right-shifted distribution — their absence of any advantage is the clearest indicator yet that `is_record_holder` is **randomly assigned**.
- Exclude this feature from any predictive pipeline — it will only introduce noise.

---

### Q14 — Are medals increasing over the years?
**Medals Over Time**

```python
df.groupby('year')['total_medals_won'].sum().plot(color='red', marker='o')
```

- Structural break between 1920–1932: medals plummet from ~1,500 to ~500 — reflects WWI/WWII cancellations and reduced post-war programmes.
- Post-1992 sawtooth pattern (alternating ~450 and ~1,500) is not medal growth — it's **Summer and Winter Games plotted on the same axis**.
- Critical action: split Summer and Winter into separate time series before any longitudinal analysis.

---

### Q15 — Does host city influence results?
**Top Host Cities — Pie Chart**

```python
plt.pie(percentages, labels=cities, autopct='%1.1f%%')
```

- Athens commands **20.3%** — directly attributable to two hosting editions (1896, 2004) and inflated early Games event counts.
- London (14.4%) and Paris (13.7%) together account for **28.1%** — both multi-time hosts.
- Modern single-edition Summer cities (Tokyo, Atlanta, Rio) cluster at ~7% each — contemporary Games produce consistent medal volumes regardless of host.

---

### Q16 — Do experienced athletes perform better?
**Experience vs Medals — Violin Plot**

```python
sns.violinplot(x='total_olympics_attended', y='total_medals_won', data=df, palette='viridis')
```

- All five violins (1–5 Games) share an identical median of 4 and near-identical shapes — **zero relationship** between experience and medal outcomes.
- Real data should show leftward skew at 1 Game shifting rightward by Games 3–4 (peak window) — none of this career lifecycle pattern appears.
- `total_olympics_attended` is synthetically uniform — **exclude from all models**.

---

### Q17 — Does ranking reflect performance?
**Country Rank vs Total Medals**

```python
sns.scatterplot(x='country_best_rank', y='country_total_medals', data=df, color='green')
```

- Textbook **power-law decay curve** — rank-1 country at ~2,650 medals, nearly 2.4× rank-2 (~1,100), then a steep drop into a long flat tail.
- Steepest drop in top 5 ranks (2,650 → 400) — elite Olympic success is extraordinarily concentrated at the very top.
- Curve flattens after rank 20 (~50–200 medals) — structural ceiling for mid-tier nations driven by funding and programme breadth.
- Most analytically credible chart in the dataset — power-law shape mirrors verified real-world Olympic all-time tables.

---

### Q18 — Which events are most competitive?
**Top Events by Athlete Count**

```python
df['event'].value_counts().head(10).plot(kind='bar')
```

- Men's Singles (~185) leads, followed by Women's Singles (~165) and Mixed Team (~158) — all racket/individual formats appearing across multiple sports.
- Co-existence of Football and Ice Hockey in the same top 10 is the clearest visual confirmation that **Summer and Winter Games are not separated** — a critical caveat for event-level analysis.

---

### Q19 — Gender vs Gold Medals
**Gold Medal Distribution by Gender**

```python
sns.boxplot(x='gender', y='gold_medals', data=df)
```

- Both genders share a median of **1 gold medal** with IQRs of 0–3 — gender has no bearing on gold medal accumulation.
- Median of 1 gold out of 4 total medals implies athletes win roughly **1 gold per 4 medals** — a silver/bronze-heavy ratio broadly aligned with real Olympic probability.
- Symmetric outliers at 8 golds for both genders signal synthetic balancing — real distributions are uneven across genders and sports.

---

## 🔬 Advanced Analysis

```python
# Correlation matrix
df.corr(numeric_only=True)

# Average age by sport
df.groupby('sport')['age'].mean()

# Gender participation by sport
pd.crosstab(df['sport'], df['gender'])

# Multi-level grouping
df.groupby(['country_name', 'sport'])['gold_medals'].sum()

# Distribution shape
from scipy.stats import skew, kurtosis
skew(df['age'])
kurtosis(df['age'])

# Outlier detection — IQR Method
Q1 = df['height_cm'].quantile(0.25)
Q3 = df['height_cm'].quantile(0.75)
IQR = Q3 - Q1
outliers = df[(df['height_cm'] < Q1 - 1.5*IQR) | (df['height_cm'] > Q3 + 1.5*IQR)]
```

---

## ⚠️ Dataset Audit Summary

| Feature | Status | Action |
|---|---|---|
| `coach_name` | Synthetically assigned | Drop from all models |
| `is_record_holder` | Randomly assigned | Drop from all models |
| `total_olympics_attended` | Uniformly distributed | Drop from all models |
| `country_best_rank` | Credible power-law | Safe to use |
| `country_total_medals` | Credible power-law | Safe to use |
| `height_cm` / `weight_kg` | Realistic distributions | Safe to use |
| `gold_medals` / `total_medals_won` | Plausible but compressed | Use with caution |
| `year` | Summer + Winter mixed | Split before time-series work |

---

## 💡 Key Modelling Takeaways

- **Best predictive features:** `height_cm`, `weight_kg`, `sport`, `country_best_rank`, `country_total_medals`, `gender`
- **Drop entirely:** `coach_name`, `is_record_holder`, `total_olympics_attended`
- **Engineer before use:** `year` (split Summer/Winter), `total_medals_won` (bin into categories for classification)
- **Watch for multicollinearity:** `engine_cc` and `max_power` equivalents — country-level medal features are highly correlated

---

*Olympics EDA · 8,500+ athletes · 19 analysis questions · 128 years of Games*

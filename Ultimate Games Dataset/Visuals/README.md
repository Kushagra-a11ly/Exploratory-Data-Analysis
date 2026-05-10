# 🎮 Ultimate Games EDA — Visual Storytelling

<div align="center">

![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-11557c?logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13-4C72B0?logo=python&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-5.x-3F4F75?logo=plotly&logoColor=white)
![Visuals](https://img.shields.io/badge/Charts-15-orange)
![Dataset](https://img.shields.io/badge/Dataset-15%2C000%20Games-purple)
![License](https://img.shields.io/badge/License-MIT-brightgreen)

**15 charts. 15,000 games. Nearly five decades of gaming history — told through data.**

</div>

---

## 📌 Chart Index

| # | Title | Chart Type | Variables |
|---|---|---|---|
| 01 | [Genre Dominance](#-01--genre-dominance) | Horizontal Bar | `all_genres` |
| 02 | [Game Releases Over Time](#-02--game-releases-over-time) | Line | `release_year` |
| 03 | [User Rating Distribution](#-03--user-rating-distribution) | Histogram + KDE | `user_rating` |
| 04 | [Critic vs User Ratings](#-04--critic-vs-user-ratings) | Scatter | `metacritic` · `user_rating` · `is_multiplayer` |
| 05 | [Multiplayer Effect on Ratings](#-05--multiplayer-effect-on-ratings) | Box Plot | `is_multiplayer` · `user_rating` |
| 06 | [Platform Reach vs Popularity](#-06--platform-reach-vs-popularity) | Regression Plot | `platform_count` · `popularity_score` |
| 07 | [ESRB Rating Distribution](#-07--esrb-rating-distribution) | Count Plot | `esrb_rating` |
| 08 | [Engagement Score Density](#-08--engagement-score-density) | KDE | `engagement_score` |
| 09 | [Correlation Heatmap](#-09--correlation-heatmap) | Heatmap | 7 numerical features |
| 10 | [Publisher Market Share](#-10--publisher-market-share) | Horizontal Bar | `publishers` |
| 11 | [Game Production by Decade](#-11--game-production-by-decade) | Bar | `decade` |
| 12 | [Playtime Outlier Analysis](#-12--playtime-outlier-analysis) | Box Plot | `avg_playtime_hours` |
| 13 | [Popularity Across Game Modes](#-13--popularity-across-game-modes) | Violin | `game_mode` · `popularity_score` |
| 14 | [Achievements vs Engagement](#-14--achievements-vs-engagement) | Scatter | `achievements_count` · `engagement_score` |
| 15 | [Univariate Distributions](#-15--univariate-distributions) | Histogram Grid | `popularity_score` · `engagement_score` · `release_year` |

---

## 📊 01 · Genre Dominance

> **What genres dominate the gaming landscape?**

```python
plt.figure(figsize=(12, 6))
g = df['all_genres'].value_counts().head(10)
sns.barplot(x=g.values, y=g.index, hue=g.index,
            palette='viridis', legend=False, edgecolor='black')
plt.title("Top 10 Game Genres")
plt.xlabel("Game Count")
plt.ylabel("Genres")
plt.grid(axis='x', linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![Genre Dominance](./visuals/01_genre_dominance.png) -->

**Insights**

- 🥇 **Adventure|Indie** is the single most dominant genre combination — strong demand for creative, exploration-based experiences drives the top spot
- 🥈 **Casual|Indie** closely follows, confirming that accessible, low-pressure gameplay has a wide and loyal audience
- 🔀 **Hybrid genres outperform standalone categories** across the board — players demonstrably prefer layered, multi-genre experiences
- 📉 Standalone **Casual** ranks lowest among the top 10 — genre pairing is a measurable performance differentiator
- 🎯 **Action|Shooter** holds steady volume but consistently trails broader action-oriented hybrid combinations

---

## 📊 02 · Game Releases Over Time

> **How has game production volume evolved from 1979 to 2026?**

```python
plt.figure(figsize=(13, 5))
y = df['release_year'].value_counts().sort_index()
sns.lineplot(x=y.index, y=y.values, color='crimson', linewidth=3)
plt.title("Game Releases Over Time")
plt.xlabel("Release Year")
plt.ylabel("Games Released")
plt.grid(True, linestyle='--', alpha=0.5)
plt.show()
```

<!-- Add chart image here: ![Releases Over Time](./visuals/02_releases_over_time.png) -->

**Insights**

- 💤 **Dormant Era (1978–1999):** Near-zero release volume — high entry barriers, hardware-controlled distribution, and a small publisher oligopoly suppressed output for two decades
- 📈 **Growth Phase (2000–2012):** Steady climb as digital storefronts demolished retail gatekeeping and enabled smaller studios to self-publish globally
- 🚀 **Peak (2015–2016):** ~1,600 annual releases — Steam Greenlight's low-barrier model temporarily flooded the market with indie titles, overwhelming curation mechanisms
- 🔄 **Secondary Surge (2017–2022):** Post-peak consolidation followed by a rise to ~1,050 releases, driven by pandemic-era consumer demand and a boom in remote development
- ⚠️ **Post-2022 drop is a data artifact** — recent entries remain incompletely catalogued, not a real indicator of market contraction

---

## 📊 03 · User Rating Distribution

> **How do users rate the games they play?**

```python
plt.figure(figsize=(10, 5))
sns.histplot(df['user_rating'], bins=30, kde=True,
             color='darkorange', edgecolor='black')
plt.title("User Rating Distribution")
plt.xlabel("User Rating")
plt.ylabel("Frequency")
plt.grid(axis='y', linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![User Rating Distribution](./visuals/03_user_rating_distribution.png) -->

**Insights**

- ↩️ **Left-skewed distribution** — users are generous raters; the majority of scores cluster between 3.5–4.0
- 🎯 **Modal peak at 3.75** — the most commonly assigned score across all 15,000 games, with ~1,750 occurrences
- 🪶 **Thin lower tail (1.0–2.0)** — low ratings are rare, pointing to either a genuine lack of poor titles or a positivity bias where dissatisfied users simply don't rate
- 📊 Gradual frequency build-up across 2.5–3.5 reflects a broad base of average-to-good titles without extreme polarization
- ✂️ **Sharp drop after 4.0** — near-perfect scores are reserved and rare, lending credibility and weight to highly-rated titles

---

## 📊 04 · Critic vs User Ratings

> **Do critics and players agree — and does multiplayer status change the picture?**

```python
plt.figure(figsize=(9, 6))
sns.scatterplot(data=df, x='metacritic', y='user_rating',
                hue='is_multiplayer', palette='Set2', edgecolor='black')
plt.title("Metacritic vs User Rating")
plt.xlabel("Metacritic Score")
plt.ylabel("User Rating")
plt.grid(True, linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![Critic vs User Ratings](./visuals/04_critic_vs_user.png) -->

**Insights**

- 📈 **Positive but weak-to-moderate correlation** — higher Metacritic scores align with better user ratings, but wide vertical spread confirms frequent individual-level divergence
- 🔥 **Highest disagreement in the 50–75 Metacritic band** — the densest, most scattered region where subjective player experience departs most from professional critique
- 🎮 **Single-player titles dominate the scatter** — the dataset is heavily weighted toward solo experiences, which may bias overall rating distributions
- 🌐 **Multiplayer games cluster at 60–90 Metacritic** — less likely to receive extremely low or extremely high critical assessments
- 🏆 **Critical acclaim does not guarantee player satisfaction** — even games scoring 90+ on Metacritic show considerable user rating spread

---

## 📊 05 · Multiplayer Effect on Ratings

> **Does multiplayer support help or hurt user ratings?**

```python
plt.figure(figsize=(8, 5))
sns.boxplot(data=df, x='is_multiplayer', y='user_rating',
            hue='is_multiplayer', palette='coolwarm',
            linewidth=2, legend=False)
plt.title("Multiplayer Effect on Ratings")
plt.xlabel("Is Multiplayer (0 = No, 1 = Yes)")
plt.ylabel("User Rating")
plt.grid(axis='y', linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![Multiplayer Effect](./visuals/05_multiplayer_effect.png) -->

**Insights**

- 🏅 **Single-player median (~3.5) consistently exceeds multiplayer (~3.2)** — users reward solo experiences with measurably higher satisfaction scores
- 📦 **Multiplayer IQR is wider (~2.7–3.75)** — greater rating volatility driven by server quality, matchmaking experience, and community behavior beyond core gameplay
- ⬇️ Multiple outliers below 1.5 appear in the single-player group — a small cohort of critically poor titles that don't move the median
- 🔝 **Upper whiskers are comparable across both groups (~4.75–5.0)** — exceptional experiences are achievable regardless of format
- ⚖️ The multiplayer median sits at or below single-player Q1 — most multiplayer titles score where single-player games are considered below average

---

## 📊 06 · Platform Reach vs Popularity

> **Does releasing on more platforms drive higher popularity?**

```python
plt.figure(figsize=(10, 6))
sns.regplot(data=df, x='platform_count', y='popularity_score',
            scatter_kws={'alpha': 0.5}, color='green')
plt.title("Platform Reach vs Popularity")
plt.xlabel("Platform Count")
plt.ylabel("Popularity Score")
plt.grid(True, linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![Platform vs Popularity](./visuals/06_platform_vs_popularity.png) -->

**Insights**

- 📐 **Clear positive linear trend** — broader platform availability is a statistically meaningful driver of popularity and audience reach
- 🗜️ **Severe data concentration at 1–6 platforms** — the vast majority of studios operate within a limited distribution footprint due to financial and technical constraints
- ↕️ **High variance at every platform count level** — availability alone cannot guarantee popularity; content quality, marketing, and timing remain decisive variables
- 🎯 **Highest scores appear at mid-range platform counts (5–8), not the maximum** — quality titles on key platforms outperform broadly distributed mediocre ones
- 📉 Titles exceeding 15 platforms show moderate, not exceptional, popularity — extreme multi-platform releases are legacy/franchise titles sustained by brand recognition

---

## 📊 07 · ESRB Rating Distribution

> **What content rating profile does the dataset carry?**

```python
plt.figure(figsize=(11, 6))
order = df['esrb_rating'].value_counts().index
ax = sns.countplot(data=df, x='esrb_rating', order=order,
                   hue='esrb_rating', palette='cubehelix',
                   edgecolor='black', legend=False)
plt.title("ESRB Rating Distribution")
plt.xlabel("ESRB Category")
plt.ylabel("Number of Games")
plt.xticks(rotation=25, ha='right')
plt.grid(axis='y', linestyle='--', alpha=0.4)
[ax.bar_label(c, fontsize=9) for c in ax.containers]
plt.tight_layout()
plt.show()
```

<!-- Add chart image here: ![ESRB Distribution](./visuals/07_esrb_distribution.png) -->

**Insights**

| ESRB Rating | Count | Insight |
|---|---|---|
| Not Rated | **10,205** | Majority of the dataset — most indie/digital titles skip ESRB due to cost and voluntariness |
| Teen (T) | **1,575** | Largest formally rated segment — targets mass-market appeal with permissible mature themes |
| Mature (M) | **1,258** | Narrows the gap on Teen — adult-oriented content is a substantial commercial segment |
| Everyone (E + E10+) | **1,524** | Combined total still falls well below Teen + Mature, revealing an under-prioritized all-ages market |
| Adults Only (AO) | **412** | Commercially marginal — severe retail and platform restrictions disincentivize publishers |

---

## 📊 08 · Engagement Score Density

> **How is player engagement distributed across all games?**

```python
plt.figure(figsize=(10, 5))
sns.kdeplot(df['engagement_score'], fill=True, color='purple')
plt.title("Engagement Score Density")
plt.xlabel("Engagement Score")
plt.ylabel("Density")
plt.grid(True, linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![Engagement Density](./visuals/08_engagement_density.png) -->

**Insights**

- 📉 **Severely right-skewed** — the vast majority of games generate near-zero sustained engagement post-launch, a classic long-tail phenomenon
- 🏔️ **Modal density peaks near zero (~0.21)** — most releases fail to achieve meaningful player interaction regardless of quality or platform availability
- 🚧 **Rapid decay between scores 1–10** — crossing even a modest engagement threshold is a significant competitive differentiator
- 🔍 **Micro-peaks at 12–15 and 20–22** — faint bumps hint at a distinct sub-segment of niche-community titles sustaining above-baseline engagement
- 🌠 **Long tail extends beyond 45** — a statistically rare but commercially dominant cohort whose engagement accounts for a disproportionate share of total player hours

---

## 📊 09 · Correlation Heatmap

> **Which metrics move together — and which are truly independent?**

```python
plt.figure(figsize=(12, 8))
num = df[['user_rating', 'metacritic', 'ratings_count', 'reviews_count',
          'library_count', 'avg_playtime_hours', 'popularity_score']]
sns.heatmap(num.corr(), annot=True, cmap='Spectral',
            linewidths=1, linecolor='black')
plt.title("Correlation Heatmap")
plt.show()
```

<!-- Add chart image here: ![Correlation Heatmap](./visuals/09_correlation_heatmap.png) -->

**Insights**

| Variable Pair | `r` | What It Means |
|---|---|---|
| `ratings_count` ↔ `reviews_count` | **0.99** | Near-perfect redundancy — one variable is statistically sufficient |
| `library_count` ↔ `ratings_count` | **0.91** | Strong engagement funnel — library additions reliably predict rating activity |
| `user_rating` ↔ `metacritic` | **0.66** | Moderately correlated — critics and players share a perspective but diverge at the individual level |
| `popularity_score` ↔ `metacritic` | **0.60** | Popularity leans on critical visibility more than on organic user sentiment |
| `avg_playtime_hours` ↔ all others | **0.12–0.19** | Playtime is genre-driven and nearly independent of popularity, rating, or engagement |

---

## 📊 10 · Publisher Market Share

> **Which publishers release the most games?**

```python
plt.figure(figsize=(12, 6))
p = df['publishers'].value_counts().head(10)
sns.barplot(x=p.values, y=p.index, hue=p.index,
            palette='flare', edgecolor='black', legend=False)
plt.title("Top Publishers by Game Volume")
plt.xlabel("Published Games")
plt.ylabel("Publishers")
plt.grid(axis='x', linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![Publisher Market Share](./visuals/10_publisher_share.png) -->

**Insights**

- ⚠️ **"Not Specified" leads at ~1,500 games** — the largest bar is unattributed metadata, a significant data quality gap that limits publisher-level analysis
- 🥇 **EA (~200) and Ubisoft (~175) top named publishers** — decades of high-volume franchise strategy across multiple genres and platforms
- 🎯 **Nintendo (~160 games) punches above its volume weight** — widely recognized for disproportionately high quality-per-title relative to output volume
- 📦 **Mid-tier publishers cluster tightly at 100–130 games** — SEGA, Square Enix, Capcom, and Microsoft Studios form a natural equilibrium band
- 🔞 **EroticGamesClub's top-10 presence** reflects the expanding scope of game databases to encompass adult-oriented digital storefronts

---

## 📊 11 · Game Production by Decade

> **How dramatically has the industry's output grown?**

```python
plt.figure(figsize=(10, 5))
d = df['decade'].value_counts().sort_index()
ax = sns.barplot(x=d.index, y=d.values, hue=d.index,
                 palette='Set2', edgecolor='black', legend=False)
plt.title("Game Production by Decade")
plt.xlabel("Decade")
plt.ylabel("Number of Games")
plt.grid(axis='y', linestyle='--', alpha=0.4)
for c in ax.containers:
    ax.bar_label(c, fontsize=11, weight='bold')
plt.tight_layout()
plt.show()
```

<!-- Add chart image here: ![Decade Production](./visuals/11_decade_production.png) -->

**Insights**

| Decade | Games Released | Growth vs Prior Decade |
|---|---|---|
| 1970s | 2 | — |
| 1980s | 69 | ×34.5 |
| 1990s | 468 | ×6.8 |
| 2000s | 1,437 | ×3.1 |
| 2010s | **8,571** | ×5.9 — **All-time peak** |
| 2020s | 4,453 | On pace to rival 2010s |

> **4,285× total growth** from the 1970s to the 2010s — a trajectory that outpaces virtually every other entertainment medium in recorded history.

---

## 📊 12 · Playtime Outlier Analysis

> **How is average playtime distributed — and how extreme are the outliers?**

```python
plt.figure(figsize=(11, 5))
sns.boxplot(x=df['avg_playtime_hours'], color='skyblue', linewidth=2)
plt.title("Average Playtime Outlier Analysis")
plt.xlabel("Playtime Hours")
plt.grid(axis='x', linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![Playtime Outliers](./visuals/12_playtime_outliers.png) -->

**Insights**

- 🗜️ **IQR is nearly invisible at the left edge** — the vast majority of games fall in the 0–10 hour range, consistent with short-form session-based gameplay norms
- 🚧 **Outlier threshold begins at ~130–150 hours** — the statistical fence separating standard games from deep-engagement titles (open-world RPGs, survival sandboxes, live-service games)
- 🌌 **Sparse outliers extend to ~370 hours** — likely titles with procedural content, competitive multiplayer loops, or active modding communities
- 🎲 **No clustering beyond 150 hours** — post-fence points are isolated anomalies, not a defined market segment; treat as individual outliers in any model
- ⚠️ **Near-zero median is a data integrity flag** — may reflect playtime records defaulting to zero for unplayed library titles rather than true gameplay data

---

## 📊 13 · Popularity Across Game Modes

> **Which game mode structure produces the most popular games?**

```python
plt.figure(figsize=(10, 5))
sns.violinplot(data=df, x='game_mode', y='popularity_score',
               hue='game_mode', palette='pastel', legend=False)
plt.title("Popularity Across Game Modes")
plt.xlabel("Game Mode")
plt.ylabel("Popularity Score")
plt.xticks(rotation=15)
plt.grid(axis='y', linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![Popularity by Game Mode](./visuals/13_popularity_by_mode.png) -->

**Insights**

- 🏆 **Hybrid (Single + Multiplayer) achieves the highest median popularity (~30)** — mode flexibility maximizes addressable audience and is a commercially superior structural choice
- 🎭 **Single-player shows a bimodal distribution** — a large low-popularity cluster alongside a smaller high-performing cohort; the high-risk, high-reward nature of narrative-driven development confirmed
- 📉 **Multiplayer-only caps lower (~75 max)** — pure multiplayer titles live or die by concurrent player counts, making sustained popularity harder to maintain
- 🔴 **"Not Specified" extends into negative popularity** — a direct composite scoring artifact penalizing incomplete metadata; these records warrant preprocessing exclusion
- 📊 **All modes converge at 20–35 popularity** — this band represents the baseline floor of visibility for any adequately distributed commercial title, regardless of format

---

## 📊 14 · Achievements vs Engagement

> **Does a larger achievement list actually drive more player engagement?**

```python
plt.figure(figsize=(9, 6))
sns.scatterplot(data=df, x='achievements_count', y='engagement_score',
                color='teal', edgecolor='black')
plt.title("Achievements vs Engagement")
plt.xlabel("Achievement Count")
plt.ylabel("Engagement Score")
plt.grid(True, linestyle='--', alpha=0.4)
plt.show()
```

<!-- Add chart image here: ![Achievements vs Engagement](./visuals/14_achievements_vs_engagement.png) -->

**Insights**

- 🔁 **The relationship is inverse, not positive** — peak engagement (scores of 35–42) is concentrated in games with **fewer than 100 achievements**, directly contradicting the assumption that more achievements drive more engagement
- 📦 **Overwhelming data density below 500 achievements** — the vast majority of titles operate within a standard achievement design framework
- 📉 **Engagement flattens and stabilizes beyond 1,000 achievements** — scores plateau at 5–17 with no upward trend; diminishing returns on achievement inflation are empirically confirmed
- 🏅 **Ultra-high achievement titles (5,000–7,200) sustain moderate scores (14–22)** — maintained by dedicated achievement-hunting communities, not mainstream audiences
- 💡 **Critical design insight:** Studios deploying achievement inflation as a retention strategy may be misallocating resources that would yield higher returns invested in core gameplay depth

---

## 📊 15 · Univariate Distributions

> **What do the core metric distributions reveal about the overall market structure?**

```python
num_cols = ['popularity_score', 'engagement_score', 'release_year']
df[num_cols].hist(figsize=(12, 6), bins=20)
plt.tight_layout()
plt.show()
```

<!-- Add chart image here: ![Univariate Distributions](./visuals/15_univariate_distributions.png) -->

**Insights**

| Variable | Shape | Key Observation |
|---|---|---|
| `popularity_score` | Bell-shaped, bimodal tendency | Peaks at 25–35 — blockbuster-level popularity (60+) is a minority privilege |
| `engagement_score` | Severely zero-concentrated | ~8,000 games score 0–1 — meaningful engagement is a top-percentile outcome, not a baseline |
| `release_year` | Exponential ramp post-2010 | Mirrors the Releases Over Time chart — confirms internal dataset consistency |

> **All three distributions are right-skewed.** Together they confirm that the gaming market operates as a **winner-takes-most ecosystem** — a small number of titles, years, and publishers capture a disproportionate share of all measurable outcomes.

---

<div align="center">

---

*15 charts. One dataset. The full story of gaming — in data.* 🕹️

</div>


# 🎮 Ultimate Games Dataset — 15,000 Games | 43 Features

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Rows](https://img.shields.io/badge/Rows-15%2C000-blue)
![Columns](https://img.shields.io/badge/Columns-43-blue)
![Year Range](https://img.shields.io/badge/Years-1979–2026-purple)
![Format](https://img.shields.io/badge/Format-CSV-orange)
![Purpose](https://img.shields.io/badge/Purpose-EDA%20Only-red)
![Maintenance](https://img.shields.io/badge/Maintained-Yes-brightgreen)

A comprehensive, clean dataset of **15,000 video games** spanning nearly five decades — from 1979 to 2026. Covering everything from ratings and playtime to platforms, genres, art styles, and store availability, this dataset is purpose-built for **Exploratory Data Analysis (EDA)** on the gaming industry.

> ⚠️ **Intended Use:** This dataset is released strictly for **EDA purposes**. It is not intended for commercial use, production systems, or as a primary data source for applications.

---

## 📌 Table of Contents

- [Dataset Overview](#-dataset-overview)
- [Column Reference](#-column-reference)
- [Notes on Null Values](#-notes-on-null-values)
- [Potential EDA Directions](#-potential-eda-directions)
- [Sample Questions to Explore](#-sample-questions-to-explore)
- [Getting Started](#-getting-started)
- [License](#-license)

---

## 📊 Dataset Overview

| Property | Value |
|---|---|
| **Rows** | 15,000 |
| **Columns** | 43 |
| **Year Range** | 1979 – 2026 |
| **File Format** | CSV |
| **License** | MIT |

---

## 🗂 Column Reference

### 🪪 Identity
| Column | Description |
|---|---|
| `serial_no` | Sequential row identifier |
| `game_id` | Unique game identifier |
| `title` | Game title |
| `url_slug` | URL-safe version of the title |
| `cover_image_url` | Link to the game's cover art |
| `official_website` | Official game or developer website |

---

### 📅 Release Info
| Column | Description |
|---|---|
| `release_date` | Full release date |
| `release_year` | Year of release (integer) |
| `decade` | Decade of release (e.g., 1990s, 2000s) |

---

### 🕹️ Game Characteristics
| Column | Description |
|---|---|
| `all_genres` | Pipe-separated list of genres |
| `theme` | Primary thematic setting (e.g., fantasy, sci-fi) |
| `art_style` | Visual style (e.g., pixel art, 3D realistic) |
| `view_dimension` | Perspective type (e.g., 2D, 3D, isometric) |
| `game_mode` | Play modes supported (e.g., single-player, co-op) |
| `is_multiplayer` | Boolean — supports multiplayer |
| `is_multi_platform` | Boolean — available on multiple platforms |
| `controls` | Primary control scheme (e.g., gamepad, keyboard) |

---

### 🏢 Developers & Publishers
| Column | Description |
|---|---|
| `developers` | Studio(s) that developed the game |
| `publishers` | Publisher(s) who released the game |

---

### 🖥️ Platforms & Stores
| Column | Description |
|---|---|
| `all_platforms` | All platforms the game is available on |
| `platform_count` | Number of platforms |
| `available_stores` | Digital storefronts (e.g., Steam, GOG, Epic) |

---

### ⭐ Ratings & Reviews
| Column | Description |
|---|---|
| `user_rating` | Community user rating (may be null — see notes) |
| `rating_tier` | Categorical rating tier (e.g., great, good, unrated) |
| `metacritic` | Metacritic critic score (may be null — see notes) |
| `metacritic_tier` | Categorical Metacritic tier |
| `ratings_count` | Number of user ratings submitted |
| `reviews_count` | Number of written reviews |
| `esrb_rating` | ESRB content rating (e.g., E, T, M) |

---

### 🔥 Engagement & Popularity
| Column | Description |
|---|---|
| `popularity_score` | Derived popularity metric |
| `engagement_score` | Derived engagement metric |
| `library_count` | Number of users with this game in their library |
| `avg_playtime_hours` | Average hours played per user |
| `achievements_count` | Number of in-game achievements |
| `game_series_count` | Number of games in the same series |

---

### 📋 Player Status Tracking
| Column | Description |
|---|---|
| `status_owned` | Count of users who own the game |
| `status_beaten` | Count of users who have beaten it |
| `status_playing` | Count of users currently playing |
| `status_dropped` | Count of users who dropped it |
| `status_toplay` | Count of users planning to play |
| `status_yet` | Count of users yet to start |

---

### 🏷️ Tags & Description
| Column | Description |
|---|---|
| `all_tags` | Community and editorial tags |
| `description_clean` | Cleaned plain-text description |

---

## ⚠️ Notes on Null Values

Some columns contain nulls or zeros that carry semantic meaning — they are **not data entry errors**.

| Column | Null / Zero % | Reason |
|---|---|---|
| `user_rating` | 2.58% null | Games with no user reviews — `rating_tier` is set to `'unrated'` |
| `metacritic` | 5.91% null | Games not listed on Metacritic — `metacritic_tier` is set to `'no_score'` |
| `avg_playtime_hours` | ~7.1% zero (1,063 games) | No playtime tracking data available, **not** literal zero hours played |
| `ratings_count` | ~14.4% zero (2,161 games) | No community rating data recorded |

> When filtering for analysis, consider excluding or separately handling these cases rather than imputing them blindly.

---

## 🔍 Potential EDA Directions

This dataset is rich enough to support a wide range of exploratory investigations:

- **Trends over time** — How have genres, art styles, and platforms evolved across decades?
- **Platform ecosystems** — Comparing game libraries across PC, console, and multi-platform titles
- **Ratings analysis** — Relationship between user ratings, Metacritic scores, and community engagement
- **Genre popularity** — Which genres dominate in which eras or on which platforms?
- **Playtime patterns** — How does average playtime vary by genre, art style, or rating tier?
- **Publisher landscape** — Major publishers over time and their output volume vs. quality
- **ESRB distribution** — Content rating trends across years and platforms
- **Engagement vs. popularity** — Do highly-owned games get played and completed?
- **Series vs. standalone** — How do sequels perform compared to original titles?
- **Tag and NLP analysis** — Clustering games by description text or tag combinations

---

## ❓ Sample Questions to Explore

```
- Which decade produced the most highly-rated games?
- Are multiplayer games rated higher or lower than single-player games?
- What is the distribution of art styles across decades?
- Which publishers have the highest average Metacritic score?
- How does platform count correlate with engagement score?
- What genres have the longest average playtimes?
- Is there a relationship between achievements count and library count?
```

---

## 🚀 Getting Started

```python
import pandas as pd

df = pd.read_csv("ultimate_games_dataset.csv")

print(df.shape)         # (15000, 43)
print(df.dtypes)
print(df.isnull().sum())
```

### Suggested first steps

```python
# Distribution of games by decade
df['decade'].value_counts().sort_index()

# Top genres
df['all_genres'].str.split('|').explode().value_counts().head(20)

# Rating tier breakdown
df['rating_tier'].value_counts(normalize=True)

# Correlation between engagement and popularity
df[['engagement_score', 'popularity_score', 'avg_playtime_hours']].corr()
```

---

## 📄 License

This dataset is released under the **MIT License**. You are free to use, share, and adapt it for personal or academic purposes with attribution.

> **Reminder:** This dataset is intended for **EDA only** and should not be used as a production data source or in commercial applications without independent verification of data accuracy.

---

<p align="center">
  Made for explorers, analysts, and anyone curious about the history of video games. 🕹️
</p>

# 🏅 Olympics Athletes Dataset (1896–2024)

> A comprehensive, analysis-ready dataset of Olympic athletes spanning 128 years of Summer and Winter Games — covering demographics, performance results, career statistics, and country-level records.

## Tech Stack

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)
![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)

---

## Overview

| Property | Details |
|---|---|
| **Rows** | 8,500+ |
| **Columns** | 30 |
| **Games Covered** | Summer (1896–2024) · Winter (1924–2022) |
| **Editions Included** | 31 Summer · 24 Winter |
| **Sports Covered** | 33 across Summer & Winter |
| **Countries** | 60+ |
| **File Format** | CSV (UTF-8) |
| **File Name** | `olympics_athletes_dataset.csv` |
| **Generated** | 2026-02-20 |

---

## Context

This dataset spans the full modern Olympic era — from the inaugural 1896 Athens Games through Paris 2024. It combines athlete-level demographic and performance data with career-level medal tallies and country-level historical records, making it suitable for a wide range of analytical and machine learning tasks including medal prediction, athlete performance modelling, country dominance analysis, and sport participation trends.

> **Analyst Note:** Several columns (`total_olympics_attended`, `is_record_holder`, `coach_name`) show uniform distributions consistent with synthetic generation. These should be treated as illustrative rather than analytically conclusive. See the EDA notebook for a full feature audit.

---

## Column Reference

| # | Column | Type | Description |
|---|---|---|---|
| 1 | `athlete_id` | String | Unique ID — format `ATH-00001` through `ATH-08500` |
| 2 | `athlete_name` | String | Full name (First + Last) |
| 3 | `gender` | String | `Male` / `Female` |
| 4 | `age` | Integer | Age at time of event (15–42) |
| 5 | `date_of_birth` | Date | Format: `YYYY-MM-DD` |
| 6 | `nationality` | String | 3-letter IOC country code (e.g. `USA`, `CHN`, `GBR`) |
| 7 | `country_name` | String | Full country name |
| 8 | `sport` | String | Sport discipline (e.g. Athletics, Swimming, Alpine Skiing) |
| 9 | `event` | String | Specific event within the sport (e.g. 100m Sprint) |
| 10 | `games_type` | String | `Summer` / `Winter` |
| 11 | `year` | Integer | Olympic year (1896–2024) |
| 12 | `host_city` | String | City where the Games were held |
| 13 | `team_or_individual` | String | `Team` / `Individual` |
| 14 | `medal` | String | `Gold` / `Silver` / `Bronze` / `None` |
| 15 | `result_value` | Float | Numeric performance result (time, distance, score, etc.) |
| 16 | `result_unit` | String | Unit for `result_value` (seconds, metres, points, kg, etc.) |
| 17 | `total_olympics_attended` | Integer | Career Games attended (1–5)  |
| 18 | `total_medals_won` | Integer | Total career medals (Gold + Silver + Bronze) |
| 19 | `gold_medals` | Integer | Career gold medals |
| 20 | `silver_medals` | Integer | Career silver medals |
| 21 | `bronze_medals` | Integer | Career bronze medals |
| 22 | `country_total_gold` | Integer | Country's all-time Olympic gold medals (as of 2024) |
| 23 | `country_total_medals` | Integer | Country's all-time total Olympic medals (as of 2024) |
| 24 | `country_first_participation` | Integer | Year the country first participated in the Olympics |
| 25 | `country_best_rank` | Integer | Country's best all-time medal-table rank |
| 26 | `is_record_holder` | String | `World Record` / `Olympic Record` / `No`  |
| 27 | `coach_name` | String | Athlete's coach name  |
| 28 | `height_cm` | Float | Height in centimetres |
| 29 | `weight_kg` | Float | Weight in kilograms |
| 30 | `notes` | String | Extra context (e.g. `Personal Best`, `Disqualified`) |

---

## Sports Coverage

###  Summer Olympics

| Sport | Example Events |
|---|---|
| Athletics | 100m Sprint, Marathon, High Jump, Decathlon |
| Swimming | 100m Freestyle, 200m Butterfly, 4×100m Relay |
| Gymnastics (Artistic) | Floor Exercise, Vault, Balance Beam |
| Cycling | Road Race, Sprint, Keirin, BMX Racing |
| Weightlifting | 61kg, 81kg, +109kg |
| Wrestling | Freestyle & Greco-Roman weight classes |
| Boxing | Flyweight through Super Heavyweight |
| Rowing | Single Sculls, Eight, Pair |
| Football (Soccer) | Men's & Women's |
| Basketball | 5-a-side & 3×3 |
| Volleyball | Indoor & Beach |
| Judo | All weight classes + Mixed Team |
| Tennis | Singles, Doubles, Mixed |
| Shooting | Air Pistol, Rifle, Trap, Skeet |
| Archery | Individual & Team |
| Diving | Springboard & Platform (Synchro) |
| Canoe/Kayak | Sprint & Slalom |
| Triathlon | Individual & Mixed Relay |
| Taekwondo | All weight classes |
| Fencing | Foil, Sabre, Épée |

###  Winter Olympics

| Sport | Example Events |
|---|---|
| Alpine Skiing | Downhill, Slalom, Super-G, Giant Slalom |
| Biathlon | Sprint, Pursuit, Mass Start, Relay |
| Cross-Country Skiing | Sprint, 15km, 50km, Relay, Skiathlon |
| Speed Skating | 500m–10000m, Team Pursuit, Mass Start |
| Figure Skating | Singles, Pairs, Ice Dance, Team |
| Ice Hockey | Men's & Women's |
| Ski Jumping | Normal Hill & Large Hill (Individual/Team) |
| Luge | Singles & Doubles |
| Bobsled | 2-man, 4-man, Women's |
| Curling | Men's, Women's, Mixed Doubles |
| Skeleton | Men's & Women's |
| Freestyle Skiing | Moguls, Aerials, Halfpipe, Slopestyle |
| Short Track Speed Skating | 500m, 1000m, 1500m, Relay |

---

## Countries Included (60+)

| IOC Code | Country | All-Time Golds |
|---|---|---|
| USA | United States | 1,061 |
| URS | Soviet Union | 473 |
| GBR | Great Britain | 285 |
| GER | Germany | 275 |
| CHN | China | 263 |
| FRA | France | 248 |
| ITA | Italy | 247 |
| SWE | Sweden | 200 |
| RUS | Russia | 194 |
| HUN | Hungary | 182 |
| FIN | Finland | 161 |
| AUS | Australia | 170 |
| JPN | Japan | 170 |
| NED | Netherlands | 121 |
| CAN | Canada | 118 |
| KOR | South Korea | 99 |
| NOR | Norway | 148 |
| KEN | Kenya | 38 |
| BRA | Brazil | 37 |
| ETH | Ethiopia | 25 |
| JAM | Jamaica | 28 |
| IND | India | 10 |
| *40+ more* | | |

---

## Olympic Games Included

### Summer Games — 31 Editions
`1896 Athens` · `1900 Paris` · `1904 St. Louis` · `1908 London` · `1912 Stockholm` · `1920 Antwerp` · `1924 Paris` · `1928 Amsterdam` · `1932 Los Angeles` · `1936 Berlin` · `1948 London` · `1952 Helsinki` · `1956 Melbourne` · `1960 Rome` · `1964 Tokyo` · `1968 Mexico City` · `1972 Munich` · `1976 Montreal` · `1980 Moscow` · `1984 Los Angeles` · `1988 Seoul` · `1992 Barcelona` · `1996 Atlanta` · `2000 Sydney` · `2004 Athens` · `2008 Beijing` · `2012 London` · `2016 Rio de Janeiro` · `2020 Tokyo` · `2024 Paris`

### Winter Games — 24 Editions
`1924 Chamonix` · `1928 St. Moritz` · `1932 Lake Placid` · `1936 Garmisch-Partenkirchen` · `1948 St. Moritz` · `1952 Oslo` · `1956 Cortina d'Ampezzo` · `1960 Squaw Valley` · `1964 Innsbruck` · `1968 Grenoble` · `1972 Sapporo` · `1976 Innsbruck` · `1980 Lake Placid` · `1984 Sarajevo` · `1988 Calgary` · `1992 Albertville` · `1994 Lillehammer` · `1998 Nagano` · `2002 Salt Lake City` · `2006 Turin` · `2010 Vancouver` · `2014 Sochi` · `2018 PyeongChang` · `2022 Beijing`

---

## Suggested Use Cases

- **Medal Prediction** — classify or regress `total_medals_won` using athlete demographics and country-level features
- **Country Dominance Analysis** — explore how `country_best_rank` and `country_total_medals` relate to historical participation
- **Sport & Body Type Profiling** — analyse `height_cm` and `weight_kg` distributions across sports and events
- **Gender Equity Analysis** — compare medal distributions, sport participation, and performance across genders
- **Olympic Era Trends** — track medal volume, sport growth, and country emergence across 128 years of Games

---

## Quick Start

```python
import pandas as pd

df = pd.read_csv('olympics_athletes_dataset.csv')

print(df.shape)          # (8500+, 30)
print(df.dtypes)         # column types
print(df.isnull().sum()) # missing value check
print(df.head())
```

---

## Repository Structure

```
├── olympics_athletes_dataset.csv   # Main dataset
├── notebooks/
│   ├── eda.ipynb                   # Exploratory Data Analysis
│   └── modelling.ipynb             # Medal prediction model
├── visuals/                        # EDA chart exports
└── README.md
```

---

---

*Dataset generated 2026-02-20 · Covers Olympic Games 1896–2024 · 8,500+ athletes · 30 features*

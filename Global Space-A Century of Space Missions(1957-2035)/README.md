![image_alt](https://github.com/Kushagra-a11ly/Exploratory-Data-Analysis/blob/b1aaba4d4b2e952f1daa57828250bfc2b53e5d14/Global%20Space-A%20Century%20of%20Space%20Missions(1957-2035)/Dataset%20Cover.jpg)

# Global Space Missions Dataset

![Records](https://img.shields.io/badge/Records-10%2C500%2B-blue?style=for-the-badge&logo=databricks&logoColor=white)
![Columns](https://img.shields.io/badge/Columns-26_Features-6C3483?style=for-the-badge)
![Coverage](https://img.shields.io/badge/Coverage-1957–2035%2B-orange?style=for-the-badge&logo=rocket&logoColor=white)
![Agencies](https://img.shields.io/badge/Agencies-12%2B_Organizations-2ECC71?style=for-the-badge)
![Format](https://img.shields.io/badge/Format-CSV_UTF--8-lightgrey?style=for-the-badge&logo=files&logoColor=white)
![Version](https://img.shields.io/badge/Version-1.0-informational?style=for-the-badge)
![Updated](https://img.shields.io/badge/Updated-May_2026-success?style=for-the-badge)

---

## Overview

The **Global Space Missions Dataset** is a structured, research-grade collection of over 10,500 space mission records covering the complete arc of human spaceflight and robotic exploration — from Sputnik 1 in 1957 through active missions in 2026 and planned programs extending to 2035 and beyond.

Each record represents a unique mission or launch event enriched across 26 attributes, spanning operational, scientific, technical, and financial dimensions. The dataset encompasses 12 leading space agencies and private operators across government and commercial sectors, plus joint multi-agency missions.

Designed for data analysts, machine learning practitioners, academic researchers, and space enthusiasts, this dataset supports a wide range of applications from visualisation and predictive modelling to space policy analysis and STEM education.

---

## Dataset at a Glance

| Property | Value |
|----------|-------|
| Total Records | 10,500+ |
| Features per Record | 26 |
| Time Span | 1957 – 2035+ |
| Agencies / Organisations | 12 + Joint Missions |
| File | `Space_Missions_Dataset.csv` |
| Format | CSV (UTF-8, comma-delimited) |
| Missing Values | Represented as `N/A` |
| Date Format | `YYYY-MM-DD` |

### Mission Phase Breakdown

| Phase | Count | Period |
|-------|-------|--------|
| ✅ Past | ~6,835 | 1957 – 2023 |
| 🔄 Ongoing | ~2,105 | 2020 – 2026 |
| 🔜 Future / Upcoming | ~1,560 | 2026 – 2035+ |

---

## Organisations Covered

| # | Code | Full Name | Country / Region | Type |
|---|------|-----------|-----------------|------|
| 1 | NASA | National Aeronautics and Space Administration | USA | Government |
| 2 | ROSCOSMOS | State Space Corporation | Russia | Government |
| 3 | CNSA | China National Space Administration | China | Government |
| 4 | ESA | European Space Agency | Europe (22 Nations) | Government |
| 5 | ISRO | Indian Space Research Organisation | India | Government |
| 6 | JAXA | Japan Aerospace Exploration Agency | Japan | Government |
| 7 | SpaceX | Space Exploration Technologies Corp. | USA | Private |
| 8 | CNES | Centre National d'Études Spatiales | France | Government |
| 9 | DLR | German Aerospace Center | Germany | Government |
| 10 | ASI | Agenzia Spaziale Italiana | Italy | Government |
| 11 | CSA | Canadian Space Agency | Canada | Government |
| 12 | Blue Origin | Blue Origin LLC | USA | Private |
| + | Joint | Multi-agency collaborative missions | Various | Mixed |

---

## Schema — Column Reference

| # | Column | Type | Description |
|---|--------|------|-------------|
| 1 | `Mission_ID` | String | Unique identifier (e.g., `NA-00001`, `IS-00042`) |
| 2 | `Mission_Name` | String | Official mission name |
| 3 | `Agency` | String | Responsible space agency or company |
| 4 | `Country_Region` | String | Country or region of the agency |
| 5 | `Agency_Type` | String | `Government` or `Private` |
| 6 | `Program_Type` | String | Program category (Robotic, Human Spaceflight, Satellite, etc.) |
| 7 | `Mission_Category` | String | Primary destination or focus (Moon, Mars, Earth Orbit, etc.) |
| 8 | `Sub_Category` | String | Specific mission type (Orbiter, Lander, Rover, CubeSat, etc.) |
| 9 | `Launch_Date` | Date | Actual or planned launch date (`YYYY-MM-DD`) |
| 10 | `End_Date` | Date / N/A | Mission end date; `N/A` if ongoing or future |
| 11 | `Duration` | String | Mission duration in days or years |
| 12 | `Launch_Vehicle` | String | Rocket used for launch |
| 13 | `Launch_Site` | String | Launch facility or spaceport |
| 14 | `Status` | String | `Success` / `Failed` / `Partial Success` / `Ongoing` / `Upcoming` |
| 15 | `Mission_Phase` | String | `Past` / `Ongoing` / `Future` |
| 16 | `Crew_Type` | String | `Crewed` or `Uncrewed` |
| 17 | `Crew_Members` | String | Crew role designations if crewed; `N/A` otherwise |
| 18 | `Destination` | String | Target destination of the mission |
| 19 | `Objective` | String | Primary scientific or operational goal |
| 20 | `Key_Achievement` | String | Notable result, discovery, or milestone |
| 21 | `Cost_USD_Million` | Float | Estimated mission cost (millions USD) |
| 22 | `Partner_Agencies` | String | Collaborating agencies, if any |
| 23 | `Data_Returned` | String | `Yes` / `No` / `Partial` / `N/A` |
| 24 | `Failure_Reason` | String | Cause of failure where applicable; `N/A` otherwise |
| 25 | `Mission_Outcome_Detail` | String | Extended description of mission result |
| 26 | `Reference_URL` | String | Official agency reference link |

---

## Mission Categories

| Category | Description |
|----------|-------------|
| Moon | Lunar orbiters, landers, rovers, sample return |
| Mars | Orbiters, landers, rovers, helicopter missions |
| Deep Space | Outer solar system probes, interstellar missions |
| Earth Orbit | LEO / MEO / GEO satellites, ISS missions |
| Sun / Solar | Solar observers, coronagraphs, L1 missions |
| Asteroid | Flyby, rendezvous, sample return, deflection |
| Venus / Mercury | Atmospheric probes, orbiters, flyby missions |
| Jupiter / Saturn | Outer planet orbiters, probes, moon studies |
| Earth Observation | Climate, weather, ocean, agriculture satellites |
| Telescope | Space-based observatories (optical, X-ray, IR, radio) |
| CubeSat / SmallSat | Small satellite technology and science missions |
| Technology Demo | Propulsion tests, AI demonstrations, in-orbit servicing |
| Communication Satellite | Broadband, GEO comsat, military communication |
| Crewed Spaceflight | Human missions to LEO, Moon, and space stations |
| Sounding Rocket | Suborbital atmospheric and ionosphere studies |

---

## Notable Missions by Agency

**NASA** — Apollo 1–17, Space Shuttle STS-1 to STS-135, Voyager 1 & 2, Hubble Space Telescope, James Webb Space Telescope, Curiosity & Perseverance Rovers, Ingenuity Helicopter, Artemis I–IV, Europa Clipper, DART

**ROSCOSMOS** — Sputnik 1, Vostok 1, Mir Space Station, Soyuz / Progress ISS missions, Luna 25–27, Spektr-RG, Venera-D

**CNSA** — Shenzhou 5–20, Tiangong Space Station, Chang'e 1–7, Yutu / Yutu-2 Rovers, Tianwen-1 & Zhurong (Mars), BeiDou Navigation System

**ESA** — Rosetta / Philae, Mars Express, BepiColombo, JUICE, Solar Orbiter, Gaia, Planck, Euclid, Ariane 5 / 6 / Vega

**ISRO** — Chandrayaan 1–3, Pragyan Rover, Mangalyaan (Asia's first Mars mission), Aditya-L1, Gaganyaan, NISAR (joint with NASA)

**SpaceX** — Falcon 1 / 9 / Heavy, Starship, Crew Dragon, CRS ISS Resupply, Starlink V1–V2, Starship IFT-1 to IFT-7+

---

## Suggested Use Cases

| Domain | Application |
|--------|-------------|
| Data Visualisation | Timeline charts, agency comparison dashboards, mission success rate plots |
| Machine Learning | Success/failure prediction, cost estimation models, NLP on mission objectives |
| Academic Research | Space policy analysis, history of spaceflight, commercial space growth studies |
| Business Intelligence | Budget trend analysis, partner agency network graphs |
| Education | Interactive STEM teaching tool for space history programs |
| Journalism | Fact-based infographics and space exploration storytelling |

---

## Important Notes

1. **Historical missions** (pre-2000) use approximate dates and costs based on publicly available records.
2. **Future missions** (2026–2035) reflect programs announced by agencies as of May 2026; launch dates are subject to change.
3. **Cost estimates** are approximate for some missions and represent best available public figures.
4. **Joint missions** are listed under the lead agency; collaborators appear in `Partner_Agencies`.
5. **Crew member names** use role designations (Commander, Pilot, MS1, etc.) as placeholders rather than personal names.

---

## Official Sources

| Agency | URL |
|--------|-----|
| NASA | https://www.nasa.gov |
| ISRO | https://www.isro.gov.in |
| CNSA | http://www.cnsa.gov.cn |
| ESA | https://www.esa.int |
| ROSCOSMOS | https://www.roscosmos.ru |
| JAXA | https://www.jaxa.jp |
| SpaceX | https://www.spacex.com |
| CNES | https://cnes.fr |
| DLR | https://www.dlr.de |
| ASI | https://www.asi.it |
| CSA | https://www.asc-csa.gc.ca |
| Blue Origin | https://www.blueorigin.com |

---

## Version History

| Version | Date | Notes |
|---------|------|-------|
| 1.0 | May 2026 | Initial release — 10,500+ records, 1957–2035+ coverage |

---

*Compiled for educational, research, and analytical purposes. All mission names, agency identifiers, and historical data are derived from publicly available information.*

# Global Space Missions Dataset

![Records](https://img.shields.io/badge/Records-10%2C500%2B-blue?style=for-the-badge&logo=databricks&logoColor=white)
![Columns](https://img.shields.io/badge/Columns-26_Features-6C3483?style=for-the-badge)
![Coverage](https://img.shields.io/badge/Coverage-1957–2035%2B-orange?style=for-the-badge&logo=rocket&logoColor=white)
![Agencies](https://img.shields.io/badge/Agencies-12%2B_Organizations-2ECC71?style=for-the-badge)
![Format](https://img.shields.io/badge/Format-CSV_UTF--8-lightgrey?style=for-the-badge&logo=files&logoColor=white)
![Version](https://img.shields.io/badge/Version-1.0-informational?style=for-the-badge)
![Updated](https://img.shields.io/badge/Updated-May_2026-success?style=for-the-badge)

---

## Overview

The **Global Space Missions Dataset** is a structured, research-grade collection of over 10,500 space mission records covering the complete arc of human spaceflight and robotic exploration — from Sputnik 1 in 1957 through active missions in 2026 and planned programs extending to 2035 and beyond.

Each record represents a unique mission or launch event enriched across 26 attributes, spanning operational, scientific, technical, and financial dimensions. The dataset encompasses 12 leading space agencies and private operators across government and commercial sectors, plus joint multi-agency missions.

Designed for data analysts, machine learning practitioners, academic researchers, and space enthusiasts, this dataset supports a wide range of applications from visualisation and predictive modelling to space policy analysis and STEM education.

---

## Dataset at a Glance

| Property | Value |
|----------|-------|
| Total Records | 10,500+ |
| Features per Record | 26 |
| Time Span | 1957 – 2035+ |
| Agencies / Organisations | 12 + Joint Missions |
| File | `Space_Missions_Dataset.csv` |
| Format | CSV (UTF-8, comma-delimited) |
| Missing Values | Represented as `N/A` |
| Date Format | `YYYY-MM-DD` |

### Mission Phase Breakdown

| Phase | Count | Period |
|-------|-------|--------|
| ✅ Past | ~6,835 | 1957 – 2023 |
| 🔄 Ongoing | ~2,105 | 2020 – 2026 |
| 🔜 Future / Upcoming | ~1,560 | 2026 – 2035+ |

---

## Organisations Covered

| # | Code | Full Name | Country / Region | Type |
|---|------|-----------|-----------------|------|
| 1 | NASA | National Aeronautics and Space Administration | USA | Government |
| 2 | ROSCOSMOS | State Space Corporation | Russia | Government |
| 3 | CNSA | China National Space Administration | China | Government |
| 4 | ESA | European Space Agency | Europe (22 Nations) | Government |
| 5 | ISRO | Indian Space Research Organisation | India | Government |
| 6 | JAXA | Japan Aerospace Exploration Agency | Japan | Government |
| 7 | SpaceX | Space Exploration Technologies Corp. | USA | Private |
| 8 | CNES | Centre National d'Études Spatiales | France | Government |
| 9 | DLR | German Aerospace Center | Germany | Government |
| 10 | ASI | Agenzia Spaziale Italiana | Italy | Government |
| 11 | CSA | Canadian Space Agency | Canada | Government |
| 12 | Blue Origin | Blue Origin LLC | USA | Private |
| + | Joint | Multi-agency collaborative missions | Various | Mixed |

---

## Schema — Column Reference

| # | Column | Type | Description |
|---|--------|------|-------------|
| 1 | `Mission_ID` | String | Unique identifier (e.g., `NA-00001`, `IS-00042`) |
| 2 | `Mission_Name` | String | Official mission name |
| 3 | `Agency` | String | Responsible space agency or company |
| 4 | `Country_Region` | String | Country or region of the agency |
| 5 | `Agency_Type` | String | `Government` or `Private` |
| 6 | `Program_Type` | String | Program category (Robotic, Human Spaceflight, Satellite, etc.) |
| 7 | `Mission_Category` | String | Primary destination or focus (Moon, Mars, Earth Orbit, etc.) |
| 8 | `Sub_Category` | String | Specific mission type (Orbiter, Lander, Rover, CubeSat, etc.) |
| 9 | `Launch_Date` | Date | Actual or planned launch date (`YYYY-MM-DD`) |
| 10 | `End_Date` | Date / N/A | Mission end date; `N/A` if ongoing or future |
| 11 | `Duration` | String | Mission duration in days or years |
| 12 | `Launch_Vehicle` | String | Rocket used for launch |
| 13 | `Launch_Site` | String | Launch facility or spaceport |
| 14 | `Status` | String | `Success` / `Failed` / `Partial Success` / `Ongoing` / `Upcoming` |
| 15 | `Mission_Phase` | String | `Past` / `Ongoing` / `Future` |
| 16 | `Crew_Type` | String | `Crewed` or `Uncrewed` |
| 17 | `Crew_Members` | String | Crew role designations if crewed; `N/A` otherwise |
| 18 | `Destination` | String | Target destination of the mission |
| 19 | `Objective` | String | Primary scientific or operational goal |
| 20 | `Key_Achievement` | String | Notable result, discovery, or milestone |
| 21 | `Cost_USD_Million` | Float | Estimated mission cost (millions USD) |
| 22 | `Partner_Agencies` | String | Collaborating agencies, if any |
| 23 | `Data_Returned` | String | `Yes` / `No` / `Partial` / `N/A` |
| 24 | `Failure_Reason` | String | Cause of failure where applicable; `N/A` otherwise |
| 25 | `Mission_Outcome_Detail` | String | Extended description of mission result |
| 26 | `Reference_URL` | String | Official agency reference link |

---

## Mission Categories

| Category | Description |
|----------|-------------|
| Moon | Lunar orbiters, landers, rovers, sample return |
| Mars | Orbiters, landers, rovers, helicopter missions |
| Deep Space | Outer solar system probes, interstellar missions |
| Earth Orbit | LEO / MEO / GEO satellites, ISS missions |
| Sun / Solar | Solar observers, coronagraphs, L1 missions |
| Asteroid | Flyby, rendezvous, sample return, deflection |
| Venus / Mercury | Atmospheric probes, orbiters, flyby missions |
| Jupiter / Saturn | Outer planet orbiters, probes, moon studies |
| Earth Observation | Climate, weather, ocean, agriculture satellites |
| Telescope | Space-based observatories (optical, X-ray, IR, radio) |
| CubeSat / SmallSat | Small satellite technology and science missions |
| Technology Demo | Propulsion tests, AI demonstrations, in-orbit servicing |
| Communication Satellite | Broadband, GEO comsat, military communication |
| Crewed Spaceflight | Human missions to LEO, Moon, and space stations |
| Sounding Rocket | Suborbital atmospheric and ionosphere studies |

---

## Notable Missions by Agency

**NASA** — Apollo 1–17, Space Shuttle STS-1 to STS-135, Voyager 1 & 2, Hubble Space Telescope, James Webb Space Telescope, Curiosity & Perseverance Rovers, Ingenuity Helicopter, Artemis I–IV, Europa Clipper, DART

**ROSCOSMOS** — Sputnik 1, Vostok 1, Mir Space Station, Soyuz / Progress ISS missions, Luna 25–27, Spektr-RG, Venera-D

**CNSA** — Shenzhou 5–20, Tiangong Space Station, Chang'e 1–7, Yutu / Yutu-2 Rovers, Tianwen-1 & Zhurong (Mars), BeiDou Navigation System

**ESA** — Rosetta / Philae, Mars Express, BepiColombo, JUICE, Solar Orbiter, Gaia, Planck, Euclid, Ariane 5 / 6 / Vega

**ISRO** — Chandrayaan 1–3, Pragyan Rover, Mangalyaan (Asia's first Mars mission), Aditya-L1, Gaganyaan, NISAR (joint with NASA)

**SpaceX** — Falcon 1 / 9 / Heavy, Starship, Crew Dragon, CRS ISS Resupply, Starlink V1–V2, Starship IFT-1 to IFT-7+

---

## Suggested Use Cases

| Domain | Application |
|--------|-------------|
| Data Visualisation | Timeline charts, agency comparison dashboards, mission success rate plots |
| Machine Learning | Success/failure prediction, cost estimation models, NLP on mission objectives |
| Academic Research | Space policy analysis, history of spaceflight, commercial space growth studies |
| Business Intelligence | Budget trend analysis, partner agency network graphs |
| Education | Interactive STEM teaching tool for space history programs |
| Journalism | Fact-based infographics and space exploration storytelling |

---

## Important Notes

1. **Historical missions** (pre-2000) use approximate dates and costs based on publicly available records.
2. **Future missions** (2026–2035) reflect programs announced by agencies as of May 2026; launch dates are subject to change.
3. **Cost estimates** are approximate for some missions and represent best available public figures.
4. **Joint missions** are listed under the lead agency; collaborators appear in `Partner_Agencies`.
5. **Crew member names** use role designations (Commander, Pilot, MS1, etc.) as placeholders rather than personal names.

---

## Official Sources

| Agency | URL |
|--------|-----|
| NASA | https://www.nasa.gov |
| ISRO | https://www.isro.gov.in |
| CNSA | http://www.cnsa.gov.cn |
| ESA | https://www.esa.int |
| ROSCOSMOS | https://www.roscosmos.ru |
| JAXA | https://www.jaxa.jp |
| SpaceX | https://www.spacex.com |
| CNES | https://cnes.fr |
| DLR | https://www.dlr.de |
| ASI | https://www.asi.it |
| CSA | https://www.asc-csa.gc.ca |
| Blue Origin | https://www.blueorigin.com |

---

## Version History

| Version | Date | Notes |
|---------|------|-------|
| 1.0 | May 2026 | Initial release — 10,500+ records, 1957–2035+ coverage |

---

*Compiled for educational, research, and analytical purposes. All mission names, agency identifiers, and historical data are derived from publicly available information.*

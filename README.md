<div align="center">

# 🏏 IPL Analytics Dashboard

**An interactive, dark-themed analytics dashboard covering 18 years (2008–2026) of Indian Premier League data — built entirely in Python with Plotly Dash.**

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Plotly Dash](https://img.shields.io/badge/Plotly_Dash-2.14+-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)](https://dash.plotly.com)
[![Plotly](https://img.shields.io/badge/Plotly-5.17+-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com)
[![Pandas](https://img.shields.io/badge/pandas-2.0+-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

> *1,201 real matches · 19 franchises · 6 interactive tabs · animated charts · zero JavaScript required*

</div>

---

## What Is This?

This is a standalone Python analytics dashboard that lets you explore every IPL match ever played — from the inaugural 2008 season through mid-2026. You get animated visualizations, interactive cross-filters, a geo map of India, and a head-to-head rivalry matrix — all running from a single Python file.

**No React. No Node.js. No JavaScript. Just Python.**

---

## Quick Start

```bash
# 1. Clone the repo
git clone https://github.com/OzSpidey/ipl-analytics-dashboard.git
cd ipl-analytics-dashboard

# 2. Create a virtual environment
python -m venv venv
source venv/bin/activate        # Mac/Linux
# or: venv\Scripts\activate     # Windows

# 3. Install dependencies (only 5 packages)
pip install -r requirements.txt

# 4. Launch the dashboard
python dashboard.py
```

Open **http://localhost:8050** in your browser. That's it.

---

## Six Interactive Tabs

### 📊 Overview

The landing tab gives you the full picture at a glance.

- **KPI tiles** — Total matches played, number of seasons, total franchises, unique venues, and the all-time most successful team
- **Overall Win Rate** — Horizontal bar chart for every franchise, coloured in their official brand colours, sorted by dominance
- **Matches per Season** — Bar chart showing how the league has grown from 58 games in 2008 to 74+ in modern seasons
- **Home vs Away Win Rate** — Grouped bars showing every team's win rate at their home ground vs on the road. Reveals which teams are fortress-builders (CSK at Chepauk: 67%) and which actually perform better away
- **Most Wins as IPL Captain** — Horizontal leaderboard of all-time match wins as captain. MS Dhoni leads with 153, followed by Rohit Sharma (95) and Virat Kohli (85)

---

### 🏆 Season Race

Watch the IPL title race unfold in real time.

- **Animated Bar Chart Race** — Press ▶ Play and watch cumulative wins pile up season by season, from 2008 to 2026. Each bar is coloured in the team's official IPL colours. Use the season slider to jump to any year, or pause mid-animation
- **Season Win Rate Line Chart** — Multi-team line chart showing win rate trajectory across all seasons. Select any combination of teams from the dropdown to compare dynasties, declines, and comeback stories

---

### 📈 Team Analysis

Deep-dive into any franchise's complete history.

- **Team Selector** — Choose any of the 10+ franchises from the dropdown
- **Performance Radar** — A 5-axis spider chart covering: Win Rate, Recent Form, Consistency (inverse std-dev of season win rates), Experience (relative match count), and Titles (seasons where the team had the highest win count). Changes instantly when you switch teams
- **Season Wins & Losses** — Stacked bar showing wins (team colour) and losses (muted) for every season the team participated in
- **Home vs Away Breakdown** — Bar chart comparing the selected team's home and away win rates, with a "Home advantage: +X%" annotation so you know at a glance whether they rely on crowd support

---

### ⚔️ Head-to-Head

The full rivalry matrix and drill-down.

- **Win Rate Heatmap Matrix** — A 12×12 grid where every cell shows Team A's win rate against Team B. Deeper purple = Team A dominates. Hover any cell to see the exact record (e.g. "MI vs CSK — 17/32")
- **Rivalry Detail** — Choose any two teams from the dropdowns below the heatmap to see:
  - Overall win count bar chart for both teams
  - Season-by-season wins grouped bar so you can see when momentum shifted

---

### 🗺 Venue Map

Where cricket is played across India — and who wins where.

- **India Geo Map** — Every IPL venue plotted on an interactive map of India. Bubble **size** encodes how many matches were hosted there; bubble **colour** runs from blue → red showing whether the team batting first or chasing wins more often at that ground
- **Bat-First Win % Bar Chart** — Every venue with 10+ matches ranked by batting-first win percentage. A dashed line marks 50% so you can instantly see which grounds heavily favour the chasing team (dew-heavy venues like Eden Gardens) vs which favour setting a target

---

### 🎲 Toss Analysis

How much does the coin flip actually matter?

- **KPI tiles** — Overall rate at which the toss winner goes on to win the match, percentage of teams who choose to field first, and total matches analysed
- **Toss-to-Win Rate by Team** — Some teams convert toss wins into match wins at 55%+ while others barely benefit. This bar chart ranks every franchise
- **Toss Decision Trend** — Line chart showing how the split between "bat first" and "field first" has evolved across all 18 seasons. The shift toward chasing (accelerated after 2016 with bigger T20 scores and dew) is clearly visible

---

## Tech Stack

| Layer | Library | Purpose |
|:---|:---|:---|
| Dashboard framework | [Plotly Dash](https://dash.plotly.com) | Web app, callbacks, component tree |
| Charts | [Plotly](https://plotly.com/python) | All visualizations incl. animated race |
| Data | [pandas](https://pandas.pydata.org) + [NumPy](https://numpy.org) | All aggregations and feature computation |
| Styling | [dash-bootstrap-components](https://dash-bootstrap-components.opensource.faculty.ai) | CYBORG base theme |
| Custom CSS | `assets/dashboard.css` | Dark glassmorphism, dropdown theming |
| Data source | [CricSheet](https://cricsheet.org) | 1,201 real IPL matches (2008–2026) |

---

## Project Structure

```
ipl-analytics-dashboard/
│
├── dashboard.py          # The entire application — layout, charts, callbacks
│
├── assets/
│   └── dashboard.css     # Dark theme: dropdowns, scrollbar, animation controls
│
├── data/
│   └── matches.csv       # 1,201 IPL matches (2008–2026), sourced from CricSheet
│
├── requirements.txt      # 5 dependencies only
└── README.md
```

---

## Data Coverage

The dataset is sourced from **[CricSheet.org](https://cricsheet.org/downloads/ipl_json.zip)** — the gold-standard open-source cricket dataset providing ball-by-ball JSON for every IPL match since the inaugural 2008 season.

| Seasons | Franchises | Matches |
|:---|:---|:---|
| 2008–2012 | 8–10 teams (incl. Deccan Chargers, Kochi, Pune Warriors) | ~75/season |
| 2013–2015 | 8 teams (SRH replace Deccan Chargers) | ~60/season |
| 2016–2017 | Rising Pune Supergiant & Gujarat Lions replace banned CSK & RR | ~60/season |
| 2018–2021 | 8 teams (CSK & RR return) | ~60/season |
| 2022–2026 | 10 teams (Lucknow Super Giants & Gujarat Titans added) | ~74/season |

**Total: 1,201 matches across 19 franchises**

---

## Highlights & Findings

A few things the dashboard reveals that might surprise you:

- **MS Dhoni has 153 wins as captain** — more than Rohit Sharma (95) and Virat Kohli (85) combined nearly
- **CSK's home advantage is the strongest in the league** at 67% home win rate vs 52% away — no other team has that 15-point gap
- **Gujarat Titans actually win more away (65%) than at home (59%)** — a statistical quirk from the Narendra Modi Stadium being used as a neutral venue for multiple teams
- **The league shifted from ~40% fielding-first in 2008 to 70%+ by 2016** — the toss decision trend chart shows the exact inflection point
- **David Warner has 58 wins as SRH captain** — more than all but four captains in IPL history, despite only captaining for ~7 seasons

---

## Running on a Different Port

```bash
# Change the port in the last line of dashboard.py, or pass via env:
python dashboard.py  # default: 8050
```

To run alongside the [IPL Match Predictor](https://github.com/OzSpidey/ipl-match-predictor) (which runs on port 8000/3000), just leave the default port — they won't conflict.

---

## Related Project

This dashboard is a companion to the **[IPL Match Winner Predictor](https://github.com/OzSpidey/ipl-match-predictor)** — a full-stack ML application (FastAPI + React) that predicts IPL match outcomes using a calibrated ensemble of Logistic Regression, Random Forest, XGBoost, and LightGBM trained on the same CricSheet dataset.

---

## Data Attribution

Match data sourced from **[CricSheet.org](https://cricsheet.org)** — maintained by Stephen Rushe. Used for educational and non-commercial purposes under the [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) licence.

---

<div align="center">

Built with Python, Plotly Dash, and 18 years of cricket data.

**[IPL Match Predictor](https://github.com/OzSpidey/ipl-match-predictor)** · **[CricSheet Data](https://cricsheet.org)**

</div>

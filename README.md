# Polycrisis Survivability Atlas

An interactive world-map dashboard of **national survivability risk this century** from the compounding stresses of the polycrisis: climate hazard, pollution, conflict & violence, inequality & poverty, food & water insecurity, and the adaptive-capacity deficit. It projects these from 2025 to 2100 under four IPCC Shared Socioeconomic Pathways (SSP1-2.6, SSP2-4.5, SSP3-7.0, SSP5-8.5).

**Live site:** https://hunterhghs.github.io/global-survivability-risk-due-to-polycrisis---pollution-climate-conflict-inequality-etc-this-century/ (after GitHub Pages is enabled)

## Features
- Choropleth world map (composite score or any single dimension), zoom/pan, hover tooltips, click to inspect
- Scenario switcher, year slider (2025–2100) with play animation
- Country panel: six stress dimensions against their 2025 baseline, plus the trajectory under all four scenarios
- Global KPIs: population-weighted risk index, people living in High-or-worse-risk countries, Severe/Critical country count, warming level
- Population by risk tier, and the global trajectory by scenario
- Adjustable index weights and a polycrisis amplification toggle (compounding risk)
- Sortable, searchable country table for every value; shareable URL state (`#s=ssp370&y=2100&c=BRA`)
- Light/dark themes, responsive down to phone width

## Deploy (GitHub Pages)
Settings → Pages → *Deploy from a branch* → `main` / `(root)`. It's a static site with no build step. D3, topojson-client and the Natural Earth 1:110m world-atlas load from jsDelivr.

Run locally:
```bash
python3 -m http.server 8000
```

## Files
| File | Purpose |
|---|---|
| `index.html` | Layout and methodology text |
| `css/styles.css` | Theme tokens (light/dark), layout |
| `js/data.js` | 2025 baseline scores (0–100) for 173 countries and territories, sensitivity factor, population 2025/2100 |
| `js/model.js` | Scenario warming paths and projection equations |
| `js/app.js` | Map, charts, table, interactions |

## Method (summary)
- **Baseline (c. 2025):** rounded composite estimates informed by ND-GAIN, INFORM Risk, WHO/AQLI PM2.5, IHME GBD, UCDP/ACLED/Global Peace Index, World Bank PIP, FAO SOFI/IPC, WRI Aqueduct and the Fragile States Index. Population figures approximate UN WPP 2024 (medium variant).
- **Warming:** IPCC AR6 median global surface temperature per SSP.
- **Dynamics:** climate hazard saturates toward 100 with warming × country sensitivity. Adaptive capacity, pollution and inequality follow each SSP narrative. Food & water stress rises with warming and is damped by capacity. Conflict relaxes toward a structural level driven by the other stresses.
- **Composite:** weighted mean of the six dimensions, amplified by up to 15% when several stresses are ≥ 60 at once.

## Caveats
This is an exploratory scenario tool with deliberately simple, transparent dynamics. The scores are indicative. They are not official statistics or forecasts. Tipping points, migration, pandemics, sub-national hot spots and technological or policy surprises are not modelled. Edit `js/data.js` to plug in your own indicator values.

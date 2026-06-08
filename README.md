
# 🌡️ Climate Burden Index

### A composite equity score measuring cumulative climate vulnerability

### for every U.S. Census tract — open, reproducible, and built to be used.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Data: Federal Public Domain](https://img.shields.io/badge/Data-Federal%20Public%20Domain-green.svg)](DATA-SOURCES.md)
[![Methodology: Open](https://img.shields.io/badge/Methodology-Fully%20Documented-orange.svg)](methodology/METHODOLOGY.md)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](notebooks/)
[![GitHub Pages](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blueviolet)](https://meyeringn.github.io/climate-burden-index)

**[Live Lookup Tool](https://meyeringn.github.io/climate-burden-index) · [Methodology](methodology/METHODOLOGY.md) · [Policy Uses](POLICY-USES.md) · [Data Sources](DATA-SOURCES.md)**

</div>

-----

## What is the Climate Burden Index?

A neighborhood’s climate risk is never just about weather.

It’s about who lives there, what resources they have, whether they can evacuate, whether their building will flood, what the air is like on a bad day, and whether they’ll be able to recover when something goes wrong.

The **Climate Burden Index (CBI)** is an open-source composite score that makes this compounded reality legible. It combines five federally-sourced datasets into a single 0–100 score for every U.S. Census tract — where 100 means highest cumulative climate burden.

**This is not a dashboard. It’s a methodology. Fork it, weight it for your city, and use it.**

-----

## The Five Variables

|Variable              |Weight |Source           |Why It’s Here                                                      |
|----------------------|-------|-----------------|-------------------------------------------------------------------|
|🏘️ Social Vulnerability|**25%**|CDC/ATSDR SVI    |Adaptive capacity determines outcomes more than exposure alone     |
|🌡️ Heat Exposure       |**22%**|CDC PLACES + NOAA|Deadliest U.S. climate hazard; Disabled and elderly most at risk   |
|🌊 Flood Risk          |**20%**|FEMA NFHL        |Rapidly worsening; FEMA maps underestimate risk in low-income areas|
|💨 Air Quality         |**18%**|EPA EJScreen     |Industrial siting discrimination is most documented here           |
|🏠 Housing Instability |**15%**|HUD CHAS         |Determines whether communities can recover, not just survive       |

All variables are nationally normalized to percentile scores before weighting. Weights sum to 100%.

-----

## Score Interpretation

|Score |Tier          |Meaning                                        |
|------|--------------|-----------------------------------------------|
|80–100|🔴 **Critical**|Top quintile national climate burden           |
|60–79 |🟠 **High**    |Significantly above-average cumulative burden  |
|40–59 |🟡 **Elevated**|Moderate burden with multiple risk factors     |
|20–39 |🟢 **Moderate**|Below-average burden, some risk factors present|
|0–19  |⚪ **Lower**   |Lowest quintile national climate burden        |

**Plain-language example:** A CBI score of 78 means: *“This neighborhood carries more cumulative climate burden than 78% of U.S. Census tracts — driven primarily by flood risk and housing instability.”*

-----

## Equity Framework

This index is not politically neutral.

It is built on the documented reality that communities of color, low-income communities, Disabled communities, and communities with limited English proficiency bear disproportionate climate burdens they did not create. Every weight decision, variable selection, and validation step reflects that baseline.

The Social Vulnerability Index — weighted highest at 25% — explicitly includes **Disability status** as a component variable. This index treats Disabled communities as a primary equity concern, not a footnote. See [METHODOLOGY.md](methodology/METHODOLOGY.md) for the full rationale.

**Equity Validation:** Notebook 03 runs three formal audits confirming that high-CBI tracts show higher burden in majority-minority, low-income, and high-Disability communities — consistent with documented real-world disparities, not methodological artifacts.

-----

## Repository Structure

```
climate-burden-index/
│
├── 📋 README.md                    ← You are here
├── 📄 METHODOLOGY.md (→ methodology/)  ← The intellectual core. Read this.
├── 📄 POLICY-USES.md               ← How advocates, planners, journalists can use this
├── 📄 DATA-SOURCES.md              ← Every source, download link, and known limitation
├── 📄 CONTRIBUTING.md              ← How to challenge, improve, or extend this work
├── 📄 ABOUT-THE-AUTHOR.md          ← The personal stakes behind the methodology
│
├── 📓 notebooks/
│   ├── 01_data_pipeline.ipynb      ← Download and merge all five federal datasets
│   ├── 02_score_calculation.ipynb  ← Apply weights, compute CBI, assign tiers
│   └── 03_equity_validation.ipynb  ← Racial, income, and disability disparity audits
│
├── 📊 methodology/
│   └── METHODOLOGY.md             ← Full variable rationale, weighting, validation approach
│
├── 📁 data/
│   ├── raw/                        ← Downloaded source files (not tracked in git; see DATA-SOURCES.md)
│   └── processed/
│       ├── cbi_scores_national.csv ← Final scored dataset (all U.S. Census tracts)
│       └── cbi_state_summary.csv   ← State-level aggregations
│
├── 📁 findings/
│   └── equity_audit_*.png          ← Validation charts from Notebook 03
│
└── 🌐 docs/
    └── index.html                  ← GitHub Pages live lookup tool
```

-----

## Quick Start

```bash
# Clone the repo
git clone https://github.com/meyeringn/climate-burden-index.git
cd climate-burden-index

# Install dependencies
pip install pandas geopandas requests tqdm openpyxl matplotlib

# Run the full pipeline
jupyter notebook notebooks/01_data_pipeline.ipynb
# Then: 02_score_calculation.ipynb → 03_equity_validation.ipynb
```

**Or: skip the pipeline entirely.** The final scored national dataset is available in `data/processed/cbi_scores_national.csv`. Join it to any geographic data using the 11-digit Census tract FIPS code.

-----

## Live Lookup Tool

The [GitHub Pages site](https://meyeringn.github.io/climate-burden-index) lets you:

- Enter any U.S. ZIP code to retrieve CBI scores for tracts in that area
- See a component breakdown (which variable is driving the score)
- Download the data for your neighborhood as a CSV
- Embed a score badge for use in community presentations or grant applications

-----

## How to Cite

```
Meyering, N. (2026). Climate Burden Index: A Composite Equity Score for U.S. Census Tracts (v1.0).
GitHub. https://github.com/meyeringn/climate-burden-index
```

-----

## Contributing

We want:

- **Methodology challenges** — If you think a weight is wrong, say so with evidence
- **City additions** — Run the pipeline for your city and submit a PR
- **Community review** — Frontline advocates who know their neighborhood’s climate burden from lived experience
- **Disability expertise** — Emergency management, accessible housing, and infrastructure domains where this index may miss important variables

See <CONTRIBUTING.md>.

-----

## Part of the “Vibe Coding for Climate Action” Portfolio

|Tool                           |Description                                                    |
|-------------------------------|---------------------------------------------------------------|
|🌡️ **Climate Burden Index**     |This repo — composite equity score for U.S. Census tracts      |
|🌿 **CanopyWatch**              |Tree canopy equity dashboard for 36 Philadelphia neighborhoods |
|⚡ **VitalGrid**                |Power outage vulnerability mapping for Philadelphia            |
|🌊 **FloodRisk Philly**         |Flood risk lookup for Philadelphia renters                     |
|🚌 **Transit Carbon Calculator**|Emissions comparison across 11 PA transit agencies             |
|🤖 **SustAInable**              |XGBoost heat illness risk prediction by ZIP code               |
|♿ **UpLift**                   |Predictive maintenance for transit accessibility infrastructure|

-----

<div align="center">

*Built in Philadelphia. Built for everywhere.*  
*[github.com/meyeringn](https://github.com/meyeringn) · [LinkedIn](https://linkedin.com/in/nickmeyering)*

</div>
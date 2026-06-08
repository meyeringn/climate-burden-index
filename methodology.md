# Climate Burden Index: Methodology

**Version:** 1.0  
**Last Updated:** June 2026  
**Author:** Nick Meyering  
**Repository:** [github.com/meyeringn/climate-burden-index](https://github.com/meyeringn/climate-burden-index)

-----

## Overview

The **Climate Burden Index (CBI)** is an open, reproducible composite score measuring cumulative climate vulnerability at the U.S. Census tract level. It combines five federal data sources into a single 0–100 score that captures not just physical climate exposure, but the social and structural conditions that determine whether a community can survive and recover from climate impacts.

A neighborhood’s climate risk is never just about weather. It is about who lives there, what resources they have, what the built environment looks like, and how much political power they can access. The CBI is designed to make that compounded reality legible — to advocates, planners, journalists, and policymakers who need to make the case for investment in the places that need it most.

-----

## Guiding Principles

### 1. Cumulative Burden, Not Single-Factor Risk

Most climate risk indexes measure one thing: flood exposure, heat vulnerability, or air quality. Real communities experience all of these simultaneously. The CBI follows the **cumulative burden** framework pioneered by CalEnviroScreen and adopted in the EPA’s EJScreen: the places most at risk are those where multiple climate stressors stack on top of each other, compounded by poverty, poor housing, and limited healthcare access.

### 2. Equity-Weighted by Design

This index is not politically neutral. It is built on the documented reality that communities of color, low-income communities, Disabled communities, and communities with limited English proficiency bear disproportionate climate burdens — burdens they did not create. The variable selection, weighting decisions, and validation steps are all designed with this reality as the baseline assumption, not an afterthought.

### 3. Reproducibility Over Precision

Every data source used in the CBI is publicly available, federally maintained, and free to access. Every processing step is documented in the `/notebooks` directory. No proprietary data, no black-box models. Any researcher, journalist, or community organization can replicate this score for their city or challenge our methodology decisions. That is the point.

### 4. Designed for Use, Not Just Publication

The CBI is built to be *used* — in public comments, legislative testimony, grant applications, and community organizing. The score is therefore designed to be explainable in plain language: a score of 78 means “this neighborhood is in the top quarter of climate burden in the country, driven primarily by flood exposure and housing instability.” No PhD required.

-----

## Data Sources and Variable Selection

The CBI draws from five federal datasets. Each was selected for national coverage, Census-tract-level granularity, public accessibility, and documented relevance to climate vulnerability in the peer-reviewed literature.

### Variable 1: Heat Exposure Index

**Source:** CDC/ATSDR Social Vulnerability Index (SVI) + NOAA Heat Watch data  
**What it measures:** The frequency and intensity of extreme heat days, combined with the percentage of residents lacking air conditioning or living in housing with poor thermal performance.  
**Why it matters:** Heat is the deadliest weather-related hazard in the United States, killing more people annually than floods, hurricanes, and tornadoes combined. Heat mortality is not evenly distributed — it clusters in neighborhoods with urban heat island effects, poor tree canopy, aging housing stock, and high rates of poverty. Disabled people and elderly residents face dramatically elevated risk.  
**Equity note:** Redlined neighborhoods have, on average, 5–12°F higher summer surface temperatures than surrounding areas due to decades of disinvestment in green infrastructure. This variable partially captures that legacy without requiring a separate redlining overlay.  
**Weight in CBI:** 22%

### Variable 2: Flood Risk Score

**Source:** FEMA National Flood Hazard Layer (NFHL) + First Street Foundation Flood Factor (public API)  
**What it measures:** Percentage of Census tract land area in FEMA Special Flood Hazard Areas (100-year floodplain), combined with First Street’s 30-year cumulative flood probability at the parcel level, aggregated to tract.  
**Why it matters:** Flood risk is rapidly changing due to climate change, and FEMA’s static flood maps systematically underestimate risk in low-income communities where infrastructure maintenance has been deferred. First Street data captures this more dynamic picture.  
**Equity note:** Flood insurance enrollment rates are significantly lower in low-income tracts, meaning that even when residents carry equivalent physical flood risk to wealthier neighbors, their capacity to recover is much lower. This is a compound vulnerability that the score partially captures through the housing variable.  
**Weight in CBI:** 20%

### Variable 3: Air Quality Burden

**Source:** EPA EJScreen — PM2.5 and Ozone percentiles  
**What it measures:** Ambient concentration of fine particulate matter (PM2.5) and ground-level ozone, expressed as a percentile relative to the national distribution.  
**Why it matters:** Air pollution causes approximately 100,000 premature deaths annually in the U.S. and is strongly associated with cardiovascular disease, asthma, and reduced lung development in children. Industrial facilities, freight corridors, and highways — which are disproportionately sited in low-income communities of color — are primary contributors.  
**Equity note:** EPA EJScreen was specifically designed to surface environmental justice concerns. We use their percentile scores directly rather than raw concentration values, which preserves the national comparability they have built into the tool.  
**Weight in CBI:** 18%

### Variable 4: Social Vulnerability Index (SVI)

**Source:** CDC/ATSDR Social Vulnerability Index — Overall SVI Percentile  
**What it measures:** A composite of 16 census variables organized into four themes: socioeconomic status, household composition (including disability and age), minority status and language, and housing type and transportation.  
**Why it matters:** Physical climate exposure alone does not determine outcomes. A community’s capacity to prepare for, respond to, and recover from climate events is shaped by income, housing stability, access to transportation, presence of caregiving networks, and political power. The SVI is the most widely-used federal measure of this adaptive capacity.  
**Equity note:** The SVI’s “household composition” theme explicitly includes disability status. Communities with higher rates of Disability are systematically less able to evacuate during emergencies, are more dependent on infrastructure (transit, power, accessible facilities) that frequently fails first during climate events, and are more likely to be overlooked in emergency planning. This index treats Disabled communities as a primary equity concern, not a footnote.  
**Weight in CBI:** 25%

### Variable 5: Housing Instability Score

**Source:** HUD Comprehensive Housing Affordability Strategy (CHAS) data + ACS housing variables  
**What it measures:** Percentage of renter households spending more than 50% of income on housing (“severely cost-burdened”), combined with housing age (pre-1970 stock as a proxy for energy inefficiency and deferred maintenance) and overcrowding rates.  
**Why it matters:** Housing is the climate adaptation unit that matters most. Renters cannot make energy efficiency improvements, have no control over HVAC systems, and are one missed paycheck away from displacement — displacement that climate events can trigger. Older housing stock is less energy-efficient, more prone to flood damage, and more likely to have deferred maintenance that amplifies climate impacts (e.g., roof failures during storms, basement flooding).  
**Equity note:** Renters are disproportionately low-income residents of color. Renter-heavy tracts are also systematically underrepresented in climate adaptation planning processes that center homeowner concerns (property values, flood insurance) over renter concerns (habitability, displacement, lease protections).  
**Weight in CBI:** 15%

-----

## Score Calculation

### Step 1: National Percentile Normalization

Each variable is converted to a national percentile rank (0–100) across all Census tracts in the dataset. This allows comparison across different units of measurement and ensures that a tract’s score reflects its position relative to the full national distribution, not just its region.

### Step 2: Equity-Adjusted Weighting

Variables are multiplied by their assigned weights (which sum to 100%) and aggregated into a raw composite score. Weights were assigned based on:

- **Mortality and morbidity impact** in the peer-reviewed climate health literature
- **Disproportionate burden evidence** — variables where disparities across race and income are most documented receive higher weights
- **Policy tractability** — we weight variables where public investment can demonstrably reduce burden

### Step 3: Final Percentile Rescaling

The raw composite score is rescaled to a final 0–100 percentile within the national tract distribution. This final rescaling means the CBI score represents a tract’s overall climate burden rank relative to every other Census tract in the United States.

### Step 4: Tier Assignment

|Score |Tier      |Description                                    |
|------|----------|-----------------------------------------------|
|80–100|🔴 Critical|Top quintile national climate burden           |
|60–79 |🟠 High    |Significantly above-average cumulative burden  |
|40–59 |🟡 Elevated|Moderate burden with multiple risk factors     |
|20–39 |🟢 Moderate|Below-average burden, some risk factors present|
|0–19  |⚪ Lower   |Lowest quintile national climate burden        |

-----

## Validation Approach

### Consistency Check

CBI scores are compared against established indexes (CalEnviroScreen, EPA EJScreen Environmental Justice Index, CDC SVI) for overlapping geographies. High-scoring CBI tracts should correlate strongly with high scores on these validated tools.

### Racial and Income Disparity Audit

We calculate mean CBI scores disaggregated by majority racial composition and median income quintile. If the index is functioning correctly, majority-minority tracts and low-income tracts should score systematically higher — reflecting documented real-world disparities, not a methodological artifact. The validation notebooks in `/notebooks/03_equity_validation.ipynb` document these results.

### Disability Disparity Audit

Mean CBI scores are also calculated for tracts with above-average rates of Disability (using ACS disability prevalence data). Disabled communities should score higher on climate burden — not because Disability causes climate vulnerability, but because ableist systems of housing, infrastructure, and emergency management have created compounded exposure.

### Expert Review

The methodology was developed in consultation with the climate justice and civic tech literature. Community review by frontline advocates is an ongoing process — see `CONTRIBUTING.md` for how to provide input.

-----

## Known Limitations

**1. Tract-Level Aggregation Masks Within-Tract Variation**  
Census tracts average 4,000 residents. Within a single tract, climate burden can vary enormously by block or building. The CBI is a triage tool, not a parcel-level risk assessment. Use it to identify priority geographies, not to make individual decisions.

**2. Static Snapshot**  
Data sources are updated at different frequencies (annual, decennial, or irregular). The CBI represents a moment in time. Climate risk is changing faster than the underlying federal datasets can track, particularly for flood risk and heat exposure.

**3. Missing Variables**  
Several important climate burden dimensions are not yet captured due to data availability constraints: wildfire smoke transport, drinking water quality, tree canopy at the tract level (parcel data is not nationally standardized), and proximity to climate-vulnerable industrial facilities (beyond what EJScreen captures). Future versions will incorporate these as reliable tract-level federal data become available.

**4. Insurance and Recovery Capacity Gaps**  
The index does not directly measure insurance coverage rates, savings rates, or social network strength — all of which affect recovery capacity. These are captured only partially through the SVI and housing variables.

**5. Political Representation Not Included**  
Communities with less political representation face worse climate adaptation outcomes, but this is difficult to operationalize at the tract level. It is a real gap.

-----

## How to Cite This Work

> Meyering, N. (2026). *Climate Burden Index: A Composite Equity Score for U.S. Census Tracts* (v1.0). GitHub. <https://github.com/meyeringn/climate-burden-index>

-----

## Version History

|Version|Date     |Changes                                                |
|-------|---------|-------------------------------------------------------|
|1.0    |June 2026|Initial release — 5-variable composite, 20 pilot cities|

-----

*Questions about methodology? Open an issue or see `CONTRIBUTING.md`.*
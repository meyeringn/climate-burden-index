# Data Sources

All data used in the Climate Burden Index is publicly available, federally maintained, and free to access. No proprietary datasets. No paywalls.

-----

## Primary Datasets

### 1. CDC/ATSDR Social Vulnerability Index (SVI)

- **URL:** <https://www.atsdr.cdc.gov/placeandhealth/svi/data_documentation_download.html>
- **Version used:** SVI 2022 (released 2023)
- **Geographic level:** U.S. Census tract
- **Update frequency:** Every 2 years (aligned with ACS 5-year release)
- **Variable used:** `RPL_THEMES` (Overall SVI Percentile, 0–1 scale)
- **Equity audit variables:** `EP_DISABL` (% with disability), `EP_POC` (% people of color)
- **License:** Public domain (federal government data)
- **Notes:** -999 values indicate missing data; treated as NA in our pipeline.

-----

### 2. EPA EJScreen

- **URL:** <https://www.epa.gov/ejscreen/download-ejscreen-data>
- **Version used:** EJScreen 2.3 (2023 release)
- **Geographic level:** U.S. Census tract
- **Update frequency:** Annual
- **Variables used:** `P_PM25` (PM2.5 national percentile), `P_OZONE` (Ozone national percentile)
- **License:** Public domain
- **Notes:** EJScreen was designed specifically to surface environmental justice concerns. We use state percentile columns to avoid over-weighting regional air quality patterns.

-----

### 3. FEMA National Flood Hazard Layer (NFHL)

- **URL:** <https://msc.fema.gov/portal/advanceSearch>
- **Version used:** Current NFHL as of Q1 2026
- **Geographic level:** Parcel/polygon; aggregated to Census tract
- **Variable used:** % of tract land area in Special Flood Hazard Area (Zones A, AE, AH, AO, VE)
- **License:** Public domain
- **Known limitation:** FEMA maps are updated irregularly and systematically underestimate flood risk in lower-income communities where infrastructure maintenance has been deferred.

-----

### 4. HUD Comprehensive Housing Affordability Strategy (CHAS)

- **URL:** <https://www.huduser.gov/portal/datasets/cp.html>
- **Version used:** CHAS 2016–2020 (ACS 5-year base)
- **Geographic level:** U.S. Census tract
- **Variable used:** Table 7 — % renter households with severe cost burden (>50% income on housing)
- **License:** Public domain

-----

### 5. CDC PLACES

- **URL:** <https://chronicdata.cdc.gov/500-Cities-Places/PLACES-Local-Data-for-Better-Health-Census-Tract-D/cwsq-ngmh>
- **Version used:** PLACES 2023 (2021 ACS/BRFSS base)
- **Geographic level:** U.S. Census tract
- **Variables used:** BPHIGH, CHD, COPD, CASTHMA — combined as heat vulnerability proxy
- **License:** Public domain

-----

## Geographic Boundaries

### U.S. Census Tract Boundaries (2022)

- **URL:** <https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html>
- All data sources joined on 11-digit Census tract FIPS code.

-----

## Data Not Yet Incorporated (Future Versions)

|Variable                 |Source       |Reason Not Included                            |
|-------------------------|-------------|-----------------------------------------------|
|Wildfire smoke days      |USFS AirFire |No reliable national tract-level annual dataset|
|Tree canopy coverage     |USFS NLCD    |Parcel-level data not nationally standardized  |
|Extreme precipitation    |NOAA Atlas 14|Spatial processing not yet completed           |
|Drinking water violations|EPA SDWIS    |Facility-level; tract aggregation complex      |
|Insurance coverage rates |Census SAHIE |County-level only                              |

-----

All data is publicly available and free to access. The full pipeline from raw download to final CBI score can be reproduced with Python 3.8+ and the packages in `requirements.txt`. No API keys required.

For broken download links or methodology questions, please open a GitHub issue.

# Notebooks

Three Jupyter notebooks document the full Climate Burden Index pipeline — from raw federal data to final scored output. GitHub renders them as static previews; to run them locally, follow the setup steps below.

-----

## Notebook Overview

|Notebook                    |What It Does                                                       |
|----------------------------|-------------------------------------------------------------------|
|`01_data_pipeline.ipynb`    |Downloads and merges all five federal source datasets              |
|`02_score_calculation.ipynb`|Applies equity-adjusted weights, computes CBI scores, assigns tiers|
|`03_equity_validation.ipynb`|Runs racial, income, and Disability disparity audits               |

Run them in order. Each notebook saves output that the next one reads.

-----

## To Run Locally

### Step 1 — Install dependencies

```bash
pip install pandas geopandas requests tqdm openpyxl matplotlib jupyter
```

### Step 2 — Download source data

Download each dataset and place it in `data/raw/` with the exact filename listed. Full download links and instructions are in [DATA-SOURCES.md](../DATA-SOURCES.md).

|File to place in `data/raw/`|Source                                                                                                                                  |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
|`SVI2022_US.csv`            |CDC/ATSDR SVI — [download here](https://www.atsdr.cdc.gov/placeandhealth/svi/data_documentation_download.html)                          |
|`EJSCREEN_2023_Tracts.csv`  |EPA EJScreen — [download here](https://www.epa.gov/ejscreen/download-ejscreen-data)                                                     |
|`fema_flood_tract_pct.csv`  |Pre-computed from FEMA NFHL — see note below                                                                                            |
|`CHAS_tract_2016_2020.csv`  |HUD CHAS — [download here](https://www.huduser.gov/portal/datasets/cp.html)                                                             |
|`PLACES_tract_2023.csv`     |CDC PLACES — [download here](https://chronicdata.cdc.gov/500-Cities-Places/PLACES-Local-Data-for-Better-Health-Census-Tract-D/cwsq-ngmh)|

**Note on the FEMA file:** The `fema_flood_tract_pct.csv` file is a pre-computed spatial join of FEMA flood zones to Census tract boundaries. It is not a direct federal download — it requires a GIS intersection step documented in `notebooks/spatial/fema_tract_intersection.py` (coming in v1.1). In the meantime, open an issue and we can share the pre-computed file directly.

### Step 3 — Launch Jupyter and run in order

```bash
jupyter notebook
```

Open `01_data_pipeline.ipynb` → run all cells → then `02` → then `03`.

-----

## Just browsing the code?

No setup needed. GitHub renders all three notebooks as formatted, readable documents — code, markdown cells, and equity annotations included. That’s intentional: the methodology should be legible to anyone, not just people with a Python environment ready to go.

-----

*Questions or errors? Open an issue.*
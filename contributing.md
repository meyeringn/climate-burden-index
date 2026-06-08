# Contributing to the Climate Burden Index

The CBI is a community tool, not a finished product. We welcome contributions from data scientists, community advocates, planners, journalists, and anyone who has encountered climate burden firsthand.

-----

## Ways to Contribute

### 1. Challenge the Methodology

If you believe the variable selection, weights, or validation approach are flawed — say so. Open a GitHub issue with the title format: `[METHODOLOGY] Your concern here`. Explain your reasoning and, if possible, propose an alternative. We take these seriously.

### 2. Add a City

The pilot release covers 20 U.S. cities. Adding a new city requires:

- Downloading the five source datasets for that city’s Census tracts
- Running notebooks 01–03
- Submitting a pull request with the new scored data and a brief city-specific note in `data/cities/`

See `ADDING_A_CITY.md` (coming in v1.1) for step-by-step instructions.

### 3. Fix a Bug

If you find an error in the pipeline notebooks, open an issue and/or submit a pull request. Please include:

- Which notebook and cell the error occurs in
- What the error is
- Your proposed fix

### 4. Improve Documentation

Clear documentation makes this tool accessible to non-data-scientists. If something in the methodology, policy uses guide, or data sources document is unclear, fix it and submit a PR.

### 5. Translate

If you can translate the methodology document, README, or POLICY-USES into another language, please do. Climate burden is a global problem.

-----

## Community Review Process

We particularly want feedback from:

- **Frontline communities** who know their neighborhoods’ climate burdens from lived experience and can tell us where the index gets it right or wrong
- **Disability advocates** with expertise in emergency management, accessible housing, and infrastructure — domains where the current index may miss important variables
- **Environmental justice organizations** with methodological expertise in cumulative burden assessments

To provide community review feedback, open an issue labeled `[COMMUNITY REVIEW]`.

-----

## What We Won’t Merge

- Contributions that remove equity-related variables or reduce weights on social vulnerability factors without strong methodological justification
- Proprietary data dependencies that would make the pipeline inaccessible to community organizations
- Changes that reduce documentation transparency

-----

## Code of Conduct

This project operates under a simple standard: engage in good faith, assume good faith, and center the communities most affected by climate burden in every decision. Detailed Code of Conduct forthcoming in v1.1.

-----

*First-time contributor? Start by opening an issue. No PR required.*
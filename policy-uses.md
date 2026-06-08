# How to Use the Climate Burden Index

The CBI is built to be *used* — not just cited. This document is for advocates, planners, journalists, and policymakers who want to put this data to work.

-----

## For Community Advocates and Organizers

**In public comment and testimony:**
The CBI gives you a number that connects your neighborhood’s lived experience to national context. A CBI score of 82 means: *“This neighborhood is in the top fifth of climate burden in the entire United States — and we’re here to explain what that means on the ground.”*

Pair the CBI score with personal testimony. The number opens the door; your community’s story walks through it.

**In grant applications:**
Many climate resilience and environmental justice grants require documentation of need. The CBI and its component scores provide objective, federally-sourced evidence of cumulative burden that grant reviewers recognize.

**In coalition building:**
Use the CBI to show *which neighborhoods* face the highest cumulative burden and should be centered in planning processes — not as tokens, but as decision-makers.

-----

## For Local Government and Planners

**Recommended policy triggers:**

|CBI Score        |Recommended Policy Response                                                                      |
|-----------------|-------------------------------------------------------------------------------------------------|
|80–100 (Critical)|Mandatory inclusion in climate adaptation planning; priority for federal/state resilience funding|
|60–79 (High)     |Enhanced environmental review for new industrial siting; green infrastructure priority           |
|40–59 (Elevated) |Include in regional climate vulnerability mapping; flag for future monitoring                    |
|Below 40         |Standard review process                                                                          |

**In budget prioritization:**
When resources are constrained (and they always are), the CBI provides a defensible, methodology-transparent basis for prioritizing investments in heat mitigation, flood infrastructure, green space, and emergency preparedness.

-----

## For Journalists and Researchers

**The CBI is explainable in a single paragraph:**

> “The Climate Burden Index scores every U.S. neighborhood on a 0–100 scale based on five federally-sourced measures: social vulnerability, heat exposure, flood risk, air quality, and housing instability. A score of 75 means that neighborhood carries more cumulative climate burden than 75% of neighborhoods in the country. The index reflects the reality that climate risk is not just about weather — it’s about who has the resources to prepare for and recover from it.”

All source data and processing notebooks are in this repository. The final scored dataset (`data/processed/cbi_scores_national.csv`) joins to any geographic dataset via the 11-digit Census tract FIPS code.

-----

## For Other Developers: Fork and Adapt

The CBI is explicitly designed to be forked and adapted:

- **Re-weight variables** for your city’s climate context (hurricane-prone cities may weight flood risk higher)
- **Add local variables** not available nationally (tree canopy, cooling center proximity, accessible transit routes)
- **Translate the methodology** to countries where equivalent national datasets exist

If you fork and adapt, please document your changes, cite the original repository, and open an issue to let us know — we track adaptations.

-----

## What the CBI Is Not

- **Not a parcel-level risk assessment.** Census tracts average 4,000 residents. Do not use for individual address decisions.
- **Not a replacement for community input.** Data identifies where to look. Community members define what to do.
- **Not politically neutral.** No methodology that honestly measures cumulative climate burden is neutral. Our equity framework is explicit. Reviewers who disagree are encouraged to propose alternative weighting in a GitHub issue.

-----

*Questions? Open an issue. Want to present this data in your community? See `CONTRIBUTING.md`.*
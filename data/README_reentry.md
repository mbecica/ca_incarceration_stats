# Re-Entry Funding Data — California Criminal Justice

This file documents statewide state-funded re-entry programming streams from FY 2000–01 to 2025–26.

**Note: This dataset is a work in progress** with significant gaps, particularly for years before 2016 and for several funding streams where only partial data has been collected. See the Known Gaps section below.

---

## ca_statewide_reentry_funding.csv

26 rows, one per fiscal year (FY 2000–01 to 2025–26).

### Columns

| Column | Description |
|--------|-------------|
| `fiscal_year` | Fiscal year label (e.g., "2022-23") |
| `bscc_adult_reentry_grant` | BSCC Adult Reentry Grant (ARG) appropriation for that fiscal year |
| `bscc_arg_cohort` | ARG cohort number |
| `returning_home_well` | Returning Home Well program state funding |
| `bscc_prop47_grants` | BSCC Prop 47 grant cohort total for that fiscal year |
| `bscc_prop47_cohort` | Prop 47 cohort number |
| `dapo_reentry_contracts` | DAPO baseline reentry service contracts |
| `sco_prcs_county_allocations` | State Controller's Office PRCS county allocation payments (statewide total) |
| `cdcr_rehabilitative_programs` | CDCR Division of Rehabilitative Programs budget |
| `total_state_reentry_funding` | Sum of all state reentry funding streams (not yet calculated — too many gaps) |
| `notes` | Context for that fiscal year |
| `source` | Citation |

---

## Funding Streams

### BSCC Adult Reentry Grant (ARG)

Established by the Budget Act of 2018 (SB 840). Provides competitive grants to community-based organizations for rental assistance and warm handoff reentry services for people released from state prison.

Four cohorts awarded to date:
- Cohort 1: $65.7M (FY 2018–19)
- Cohort 2: $37M (FY 2020–21)
- Cohort 3: $67M (FY 2021–22)
- Cohort 4: $114M split across FY 2023–24 and 2024–25

### Returning Home Well (RHW)

Established in 2020 as a COVID-19 emergency response, led by Amity Foundation in partnership with CDCR. Initial $15M state commitment in FY 2020–21. The 2022 Budget Act appropriated $10.6M/year for three years (FY 2022–23 through 2024–25). The 2025–26 Governor's Budget proposes $12.9M one-time for two additional years.

### BSCC Proposition 47 Grants

Prop 47 (2014) reclassified certain felonies as misdemeanors, generating state prison savings deposited into the Safe Neighborhoods and Schools Fund. 65% of those savings flow to BSCC as competitive grants to public agencies for mental health services, substance-use disorder treatment, and diversion programs for people in the criminal justice system. The BSCC awards funding in multi-year cohorts:

- Cohort 1: $103M (FY 2016–17, grant cycle 2017–~2020)
- Cohort 2: $96M (FY 2019–20, grant cycle August 2019 – May 2023)
- Cohort 3: $124,907,667 funded of $143,436,700 available (FY 2022–23, grant cycle September 2022 – June 2026)
- Cohort 4: $167,044,387 (FY 2024–25, grant cycle October 2024 – June 2028)
- Cohort 5: $128M (FY 2025–26, grant cycle October 2025 – June 2029; RFP approved April 2025)

Source: BSCC Prop 47 Grant Program page (https://www.bscc.ca.gov/s_bsccprop47/).

### DAPO Reentry Contracts

CDCR's Division of Adult Parole Operations contracts with community providers for reentry services. The 2025–26 Governor's Budget proposes $32M (growing to $42.9M by 2029–30) to increase rates for 14 parole reentry contracts. Baseline amounts for prior years have not yet been researched.

### SCO PRCS County Allocations

State Controller's Office payments to county probation departments for Post-Release Community Supervision, authorized under Budget Act Item 5227-106-0001. These allocations fund the limited-term increase of offenders on PRCS resulting from the Public Safety and Rehabilitation Act of 2016 (Proposition 57). Coverage: FY 2017–18 through 2023–24. Statewide totals range from $9.3M (FY 2023–24) to $28.2M (FY 2018–19). FY 2019–20 includes an additional $2.97M COVID-19 early-release supplement (Non Budget Item 5227-604-0001) to reimburse counties for supervising individuals released up to 60 days early.

Source data extracted from 8 SCO xlsx files. County-level breakdowns are in `ca_county_prcs_allocations.csv`.

### CDCR Rehabilitative Programs

CDCR Division of Rehabilitative Programs budget. Merged from `ca_statewide_corrections_budget.csv` (`rehabilitative_programs_expenditures` column, available FY 2011–12 onward).

---

## Known Gaps

- DAPO reentry contract baseline for all years prior to 2025–26
- No data for FY 2000–01 through 2015–16 (no dedicated state reentry funding streams identified before Prop 47)
- Does not include county Realignment allocations, federal grants (Second Chance Act), or private philanthropy
- `total_state_reentry_funding` column not yet calculated due to the number of gaps

---

## What This File Does Not Include

- County Realignment allocations (AB 109 base allocations to county probation)
- Federal funding (Second Chance Act grants, DOJ programs)
- Private philanthropy
- CDCR Division of Rehabilitative Programs grant programs paid directly to participants
- Prop 57 credits program costs

---

## References

Amity Foundation. (n.d.). *Returning Home Well Initiative*. https://www.amityfdn.org/featured-partnerships/returning-home-well-initiative

Board of State and Community Corrections. (2018–2025). *Adult Reentry Grant Program*. https://www.bscc.ca.gov/s_argrant/

Board of State and Community Corrections. (n.d.). *Proposition 47 Grant Program*. https://www.bscc.ca.gov/s_bsccprop47/

California State Controller's Office. (2017–2024). *Post Release Community Supervision payments* [xlsx files]. https://www.sco.ca.gov/ard_payments_postreleasecommunitysupervision.html

California Department of Corrections and Rehabilitation. (2025). *Governor's Budget 2025–26, chapter 5210: Criminal Justice and Judicial Branch*. https://ebudget.ca.gov/

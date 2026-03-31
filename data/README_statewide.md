# Statewide Data — California Criminal Justice

This directory contains two statewide CSV files covering California prison population (1920–2025) and the CDCR corrections budget (FY 1980–81 to 2025–26).

---

## ca_statewide_prison_population.csv

106 rows (1920–2025), one row per calendar year.

### Columns

| Column | Description |
|--------|-------------|
| `year` | Calendar year |
| `prison_population` | California state prison population: Institution/Camps + Department of State Hospitals (DSH) beds. Excludes in-state contract beds, out-of-state contract beds, and CRPP placements (tracked separately). |
| `ca_state_population` | California resident population |
| `incarceration_rate_per_100k` | `prison_population / ca_state_population × 100,000` |
| `parole_population` | Total active parolees statewide |
| `crpp_supervision` | Community Reentry Program Participants (CRPP) supervision count, December snapshot. Includes Alternative Custody Program, Female/Male Community Reentry Programs, Medical Reprieve Program, and Community Participant Mother Program. Program began mid-2016; data available December 2016–2018 (from CDCR Offender Data Points PDFs) and 2024–2025 (from Tpop1d PDFs). 2019–2023 not yet collected. |
| `total_cdcr_population` | Total CDCR population (in-custody + parole + CRPP) |
| `felony_probation` | Statewide felony probation caseload (Dec ending) |
| `misdemeanor_probation` | Statewide misdemeanor probation caseload (Dec ending) |
| `total_probation` | Sum of felony + misdemeanor probation |
| `prcs_population` | Post-Release Community Supervision population |
| `mandatory_supervision` | Mandatory supervision population |
| `jail_population` | Statewide total county jail population (2000–2024), summed across all reporting counties from `ca_county_incarceration.csv`. Sourced from the California Board of State and Community Corrections (BSCC) Jail Profile Survey. 57 counties report through 2015; 56 counties from 2016–2023; 54 counties in 2024. The 2024 figure is a slight undercount due to missing counties. |
| `jail_population_source` | Source citation for the jail population figure. |

### Sources by column

**Prison population (1920–2025):**

Definition: Institution/Camps + Department of State Hospitals (DSH). Excludes in-state and out-of-state contract beds and CRPP placements. Prior to this correction, years 2015–2024 used the full Section A in-custody total (which included contract beds and CRPP), overstating prison population by roughly 6,000–10,000 depending on year.

- 1920–2014: CDCR historical records as compiled in Zimring and Hawkins. Measurement timing shifts from June (end of fiscal year) for early decades to December (end of calendar year) for modern data. No correction needed; contract/CRPP beds were not separately tracked in this period.
- 2015–2018: CDCR Offender Data Points PDFs (semi-annual reports). December values extracted from "In-Custody Population (Total Population) Breakout" table: Institution Population + Fire Camp Population + DSH Beds. (2015 data from Dec 2017 report p.74; 2016 from Dec 2017 report p.78; 2017 from Dec 2018 report p.80; 2018 from Dec 2018 report p.123.)
- 2019–2023: CDCR Monthly Report of Population (Tpop1d series), December 31 snapshots. Institution/Camps + DSH line items.
- 2024–2025: CDCR Monthly Report of Population (Tpop1d series), December 31 snapshots. Institution/Camps + DSH line items.

**California state population (1920–2025):**
- Federal Reserve Economic Data (FRED) CAPOP series, sourced from U.S. Census Bureau resident population estimates.

**Incarceration rate:**
- Calculated as state prison population per 100,000 California residents. Does not include county jail populations, federal prisoners, or community supervision populations in the numerator.

**Parole (2000–2025):**
- 2000–2009: Bureau of Justice Statistics, Annual Parole Survey, published in the *Probation and Parole in the United States* bulletin series. December 31 yearend parole counts extracted from nine BJS reports (NCJ 184735, 195669, 201135, 205336, 210676, 215091, 220218, 224707, 231674). Parole data appears in Table 5 (2001–2003), Table 1 (2004–2005), Table 3 (2006–2007), or Appendix Table 12 (2008–2009).
- 2010–2013, 2020–2022: Read from LAO "State and County Correctional Populations" stacked bar chart visualization. Confirmed to correct order of magnitude by visual inspection.
- 2014–2019: Extracted from CDCR *Data Points* PDF reports (semi-annual publications), December values for "Total Active Parolee Population."
- 2023: CDCR Population Dashboard CSV export, December statewide total.
- 2024–2025: CDCR Monthly Report of Population (Tpop1d PDFs), December 31 snapshots.

**CRPP supervision (2024–2025):**
- CDCR Tpop1d PDFs, December 31 snapshots. CRPP includes Alternative Custody Program, Female/Male Community Reentry Programs, Medical Reprieve Program, and Community Participant Mother Program. Pre-2024 values not collected.

**Probation (2003–2024):**
- California Department of Justice, Criminal Justice Statistics Center (CJSC), Adult Probation Caseload Actions dataset, downloaded from OpenJustice (openjustice.doj.ca.gov). Statewide totals are the sum of all 58 counties' December ending caseloads for felony and misdemeanor probation. Covers traditional probation only — not PRCS or mandatory supervision.

**PRCS (2011–2025):**
- 2013–2015: Chief Probation Officers of California (CPOC), *2015 California Probation Summary*, June 30 snapshots. Values: 2013 = 39,057; 2014 = 40,778; 2015 = 39,905.
- 2016: CPOC *2016 California Probation Summary*, June 30 snapshot. Value: 40,120.
- 2017–2018: CPOC *2018 California Probation Summary*, June 30 snapshots. Values: 2017 = 40,017; 2018 = 43,038.
- 2019–2023: Read from LAO Figure 1, "Total PRCS Population Has Declined to Pre-Proposition 57 Level" (average quarterly population bar chart). Values are approximate readings from the chart's y-axis. Note: the LAO chart reports average quarterly population rather than a point-in-time snapshot, so values may differ from the June 30 snapshots used in CPOC reports.

**Mandatory supervision (2012–2025):**
- 2013–2015: CPOC *2015 California Probation Summary*, June 30 snapshots. Values: 2013 = 8,196; 2014 = 11,557; 2015 = 11,780.
- 2016: CPOC *2016 California Probation Summary*, June 30 snapshot. Value: 12,019.
- 2017–2018: CPOC *2018 California Probation Summary*, June 30 snapshots. Values: 2017 = 12,519; 2018 = 12,178.
- 2019–2023: Read from LAO visualizations.

---

## ca_statewide_corrections_budget.csv

46 rows, one per fiscal year (FY 1980–81 to 2025–26).

### Columns

| Column | Description |
|--------|-------------|
| `fiscal_year` | Fiscal year label (e.g., "2023-24") |
| `corrections_budget_nominal_dollars` | CDCR total budget in nominal dollars |
| `total_state_budget_all_funds_nominal_dollars` | Total state budget, all funds |
| `total_general_fund_expenditures` | Total General Fund expenditures |
| `corrections_pct_of_general_fund` | `corrections_budget / total_general_fund × 100` |
| `data_quality` | "reported", "interpolated", or "derived" |
| `source_notes` | Citation for each row |
| `adult_operations_expenditures` | Adult Corrections and Rehabilitation Operations (all funds). Sum of: Security (4530), Security Overtime (4535, retired ~2019), Inmate Support (4540), Contracted Facilities (4545, retired ~2019), Institution Administration (4550). |
| `parole_operations_expenditures` | Parole Operations / DAPO (all funds). Sum of: Adult Supervision (4555), Adult Community Based Programs (4560), Adult Administration (4565), Sex Offender Management Board and SARATSO (4570). |
| `board_parole_hearings_expenditures` | Board of Parole Hearings (all funds). Sum of: Adult Hearings (4575), Administration (4580). |
| `total_parole_expenditures` | Sum of `parole_operations_expenditures` + `board_parole_hearings_expenditures`. |
| `rehabilitative_programs_expenditures` | Rehabilitative Programs (all funds). Sum of: Adult Education (4585), Cognitive Behavioral Therapy and Reentry Services (4590), Adult Inmate Activities (4595), Adult Administration (4600). |
| `budget_program_source` | PDF year and column type used as source (e.g., "2025-26 (prior_actual)"). |
| `cpi_u` | U.S. CPI-U annual average for the fiscal year (average of start and end calendar year values, 1982–84 = 100). Source: BLS CPIAUCSL series. The 2025 value is estimated. |
| `corrections_budget_2024_dollars` | `corrections_budget_nominal_dollars` adjusted to 2024 dollars using `cpi_u`. |
| `total_state_budget_all_funds_2024_dollars` | `total_state_budget_all_funds_nominal_dollars` adjusted to 2024 dollars. |
| `total_general_fund_2024_dollars` | `total_general_fund_expenditures` adjusted to 2024 dollars. |
| `adult_operations_2024_dollars` | `adult_operations_expenditures` adjusted to 2024 dollars. |
| `parole_operations_2024_dollars` | `parole_operations_expenditures` adjusted to 2024 dollars. |
| `board_parole_hearings_2024_dollars` | `board_parole_hearings_expenditures` adjusted to 2024 dollars. |
| `total_parole_2024_dollars` | `total_parole_expenditures` adjusted to 2024 dollars. |
| `rehabilitative_programs_2024_dollars` | `rehabilitative_programs_expenditures` adjusted to 2024 dollars. |

Inflation adjustment formula: `real_value = nominal_value × (CPI_2024 / cpi_u)`, where CPI_2024 = 314.2. The `corrections_pct_of_general_fund` column and its component-level equivalents do not require inflation adjustment since both numerator and denominator are in the same year's dollars.

### Sources

Budget data compiled from multiple primary sources:
- Governor's Budget Summary (various years)
- Legislative Analyst's Office (LAO) annual Budget Analyses
- California Budget & Policy Center, *Steady Climb* issue briefs
- Bureau of Justice Statistics (BJS), *State Corrections Expenditures* reports (FY 1982–2010)
- CDCR budget documents and Governor's Budget detail pages (2010–2026)
- Department of Finance (DOF) Chart A historical series and LAO *Cal Facts* for General Fund totals (1980–2009)

41 of 46 years use figures reported directly from primary sources. Five years (FY 1984–85 through 1986–87, 1989–90, and 1990–91) use linear interpolation between known anchor points and are flagged `data_quality = "interpolated"`. FY 1982–83 is flagged `data_quality = "derived"`: the LAO 1982–83 Budget Analysis states Department of Corrections expenditures were proposed to increase $48M over 1981–82, giving a derived figure of $511.1M.

**`total_general_fund_expenditures` for FY 2010–11 through 2025–26** was not collected from primary sources and is back-calculated as `corrections_budget_nominal_dollars / (corrections_pct_of_general_fund / 100)`. Because `corrections_pct_of_general_fund` is stored to one decimal place, these derived GF totals carry a rounding error of roughly ±$400–700M. Rows with derived GF values are noted in `source_notes`. Users needing precise GF totals for this period should source them from DOF Chart A or LAO *Cal Facts*.

### Program-level expenditure columns (FY 2011–12 to 2025–26)

The five program-level columns are extracted from Governor's Budget chapter 5210 PDFs from ebudget.ca.gov. All values are all-funds expenditures. When multiple PDFs report the same fiscal year, values are taken from the most recent PDF where that year appears as a prior-year actual. FY 2024–25 uses current-year estimated and FY 2025–26 uses budget proposal figures.

PDFs from 2015–16 onward use 4-digit codes (4530–4600); PDFs from 2013–14 and 2014–15 used 2-digit codes (25–48). Both sets map to the same program groups.

---

## Key Definitional Notes

**AB 109 (Public Safety Realignment, 2011):** Shifted responsibility for lower-level offenders from state to county. Created Post-Release Community Supervision (PRCS) for people released from state prison for non-serious/non-violent/non-sex offenses, and mandatory supervision (MS) for the community supervision portion of split sentences. Both went into effect October 1, 2011.

**Measurement timing varies across columns:**
- Prison and parole: December 31 snapshots (modern data); June 30 for pre-1990s.
- Probation: December ending caseloads.
- PRCS/MS from CPOC: June 30 snapshots.
- PRCS/MS from LAO: Quarterly averages.
- Corrections budgets: Fiscal year (July–June).

### PRCS and mandatory supervision: data source comparison

Three independent sources report PRCS and mandatory supervision populations for California, producing substantially different counts due to methodological differences:

**CPOC published reports (2013–2018):** Annual *California Probation Summary* reports based on the CPOC Annual Probation Survey. June 30 point-in-time snapshots, includes all individuals regardless of warrant status.

**BJS Annual Parole Survey (2019–2021):** California reported combined PRCS+MS totals. For 2019: combined = 55,216 (PRCS = 43,038, MS = 12,178). 2020 and 2021 figures are near-identical (55,216–55,220), suggesting California may have submitted estimated or carried-forward data. From 2022, California changed its reporting to BJS and separated PRCS/MS from parole entirely.

**CPOC Power BI dashboard (2018–2024):** Based on the same Annual Probation Survey but explicitly excludes adults on warrant status. For 2019, the dashboard shows combined PRCS+MS = 37,213 — substantially lower than the BJS figure of 55,216 for the same year. The ~33% gap is primarily attributable to the warrant-status exclusion.

**Comparison for 2019 (the only year with all three sources):**

| Source | PRCS | MS | Combined | Includes warrant status? |
|--------|------|----|----------|------------------------|
| BJS (Dec 31) | 43,038 | 12,178 | 55,216 | Yes |
| CPOC dashboard (June 30) | 28,931 | 8,282 | 37,213 | No |
| LAO visualization (quarterly avg) | 38,300 | 7,500 | 45,800 | Unknown |

**Decision:** The statewide CSV uses CPOC published report figures for 2013–2018 and LAO visualization estimates for 2019–2023. Users should be aware these two sources may not be directly comparable.

---

## References

Bureau of Justice Statistics. (2001–2010). *Probation and parole in the United States* [Annual bulletin series, NCJ 184735, 195669, 201135, 205336, 210676, 215091, 220218, 224707, 228230, 231674]. U.S. Department of Justice.

California Department of Corrections and Rehabilitation. (2014–2019). *CDCR data points* [Semi-annual PDF reports]. CDCR Office of Research.

California Department of Corrections and Rehabilitation. (2024–2025). *Monthly report of population* (Tpop1d series). CDCR.

California Department of Justice, Criminal Justice Statistics Center. (2003–2024). *Adult probation caseload actions* [Dataset]. OpenJustice. https://openjustice.doj.ca.gov/data

Chief Probation Officers of California. (2015). *2015 California probation summary*. CPOC.

Chief Probation Officers of California. (2016). *2016 California probation summary*. CPOC.

Chief Probation Officers of California. (2019). *2018 California probation summary*. CPOC.

Federal Reserve Bank of St. Louis. (n.d.). *Resident population in California* (CAPOP). FRED Economic Data. https://fred.stlouisfed.org/series/CAPOP

Legislative Analyst's Office. (1982). *Analysis of the budget bill of the State of California, FY 1982–83*. LAO.

Legislative Analyst's Office. (Various years). *Analysis of the budget bill*. https://www.lao.ca.gov/

Legislative Analyst's Office. (n.d.). *State and county correctional populations have declined* [Data visualization]. https://www.lao.ca.gov/PolicyAreas/CJ/5_cj_inmates

Legislative Analyst's Office. (2024). *Total PRCS population has declined to pre-Proposition 57 level* (Figure 1). https://lao.ca.gov/Publications/Report/4849

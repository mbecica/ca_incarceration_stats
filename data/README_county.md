# County-Level Data — California Criminal Justice

This directory contains two county-level CSV files: one with incarceration and probation data from Vera and DOJ, and one with county budget data from the State Controller's Office.

---

## ca_county_incarceration.csv

1,446 rows (58 counties × 25 years, 2000–2024), one row per county per calendar year.

### Sources

**Jail and prison populations:**
Vera Institute of Justice, *Incarceration Trends* dataset. Vera data is quarterly; values are annualized averages across available quarters for each county-year. Coverage: jail populations for 56–57 counties per year (Alpine and Sierra lack county jails); prison populations by county of commitment available 2000–2019. Vera stopped reporting county-level prison data after 2019.

**Probation by county:**
California Department of Justice, CJSC Adult Probation Caseload Actions dataset (openjustice.doj.ca.gov). December ending caseloads for all 58 counties, 2003–2024.

**Budget by county:**
Merged from `ca_county_totals.csv` (see below). Available for all 58 counties, FY 2002–03 through FY 2023–24. Includes total governmental expenditures, total public protection expenditures, and probation-only expenditures (see `ca_county_totals.csv` section for sourcing details).

### Known gaps

- Budget data unavailable for 2000–2002 (SCO open data begins FY 2002–03).
- Vera jail data for 2024 covers Q1 only (54 of 58 counties).
- County-level prison data stops after 2019 (Vera discontinued).
- PRCS by county: not included. Data exists in CPOC dashboards but is not available as bulk downloads.
- Parole by county: not included. CDCR Population Dashboard CSV has monthly county data for 2023–2025 but has not been merged in.
- Mandatory supervision by county: not included. Data is fragmented across individual county BSCC survey PDFs and CPOC dashboards without bulk download capability.

---

## ca_county_totals.csv

1,276 rows (58 counties × 22 years, FY 2002–03 to 2023–24), one row per county per fiscal year.

### Columns

| Column | Description |
|--------|-------------|
| `fiscal_year` | Fiscal year ending calendar year (e.g., `2024` = FY 2023–24) |
| `entity_name` | County name (or "San Francisco" via cities API) |
| `total_governmental_expenditures` | Sum of governmental fund expenditures (see Categories below) |
| `public_protection_expenditures` | Total Public Protection category (police, jails/detention, courts, fire, probation, protective inspection, flood control, other protection) |
| `public_protection_pct` | `public_protection_expenditures / total_governmental_expenditures × 100` |
| `probation_expenditures` | County probation-only expenditures, all funds. See "Probation extraction" below. |

### Source

California State Controller's Office (SCO), via the ByTheNumbers open data portal (SODA API, dataset ID `uctr-c2j8`), derived from the annual *Counties Financial Transactions Report*. Coverage: all 57 reporting counties (excluding San Francisco) FY 2002–03 through FY 2023–24.

San Francisco, as a consolidated city-county, reports to the Controller as a city. Its data is fetched separately from the SCO Cities API (dataset ID `ju3w-4gxp`) and merged in.

### Probation extraction

The SCO dataset breaks Public Protection into subcategories including a dedicated probation line, but the schema changed at FY 2017. The `probation_expenditures` column in this file is built from two API paths joined together:

**Counties (57 counties, all funds):**
- FY 2003 – 2016: `form_table='EXP_PUBLIC_PROTECTION'` with `subcategory_2` in `Probation_Operating Expenditures` and `Probation_Capital Outlay`. Two lines per county-year, summed.
- FY 2017 – 2024: `form_table` in `GEN_PROBATION`, `SR_PROBATION`, `DEBT_PROBATION`, `CAPPROJ_PROBATION`, `PERM_PROBATION` (the five fund types: General, Special Revenue, Debt Service, Capital Projects, Permanent). Five lines per county-year, summed.

**San Francisco (cities API, dataset `ju3w-4gxp`):**
- FY 2003 – 2016: `form_table='EXP_PROBATION_PUB'`, line `Probation_Total Expenditures`.
- FY 2017 – 2024: `form_table='CURR_EXP_PROBATION_PUB'`, line `Probation_Current Expenditures`.

All 58 counties × 22 fiscal years = 1,276 county-year cells are populated. Statewide totals range from $0.91B (FY 2002–03) to $2.33B (FY 2023–24) in nominal dollars.

**Caveats:**
- SF post-2017 reports `Current Expenditures` (operating) only; capital is bundled elsewhere in the cities schema, so SF's post-2017 figure is slightly narrower in scope than other counties' all-funds totals. Pre-2017 SF reports `Total Expenditures`, which is comparable.
- Pre-2017 county figures are operating + capital outlay only. Special revenue, debt service, and permanent fund probation activity (rare for probation departments) is captured in the post-2017 schema but not the pre-2017 schema. For most counties this is a negligible difference.

### Why governmental funds, not all funds

The Controller's data includes both governmental fund expenditures and enterprise/proprietary fund expenditures. Enterprise funds cover self-sustaining operations (airports, hospitals, water utilities, sewer, transit) funded by user fees rather than tax revenue. Including them would inflate the denominator and artificially shrink the public protection share. The denominator for `public_protection_pct` is the sum of governmental fund categories only.

### Categories included in the governmental fund total

- General / General Government
- Public Protection
- Public Assistance
- Health
- Education / Education and Recreation and Cultural Services
- Recreation and Cultural Services
- Public Ways and Facilities / Public Ways and Facilities, Health, and Sanitation
- Sanitation
- Debt Service / Debt Service and Capital Outlay
- Conduit Financing

Note: some category names changed over the 22-year reporting period (e.g., "General" became "General Government"). Both variants are included.

### Categories excluded (enterprise / proprietary funds)

Airport, Electric, Gas, Harbor/Port, Hospital, Internal Service, Other Enterprise, Refuse, Sewer, Solid Waste, Transit, and Water enterprise funds.

### Public Protection subcategories

Within Public Protection, the Controller's data breaks out: Police Protection, Detention and Correction, Fire Protection, Judicial, Protective Inspection, Flood Control / Soil and Water Conservation, and Other Protection.

### Calculation

```
public_protection_pct = public_protection_expenditures / total_governmental_expenditures × 100
```

### San Francisco notes

Total governmental expenditures are available for all 22 years. However, public protection expenditures are only available for FY 2002–03 through 2016–17. Starting in FY 2017–18, SF's Cities API combined categories (e.g., "General Government and Public Safety") making it impossible to isolate public safety spending. For FY 2017–18 onward, public protection columns are blank. The pre-2018 SF percentages (~14–15%) are not directly comparable to other counties (~25–35%), since the Cities API category "Public Safety" may not map exactly to the Counties API category "Public Protection."

### Fiscal year to calendar year alignment

The Controller's data labels each fiscal year by its ending calendar year (e.g., "2024" means FY 2023–24). In the merged county CSV, budget columns are joined to incarceration rows by matching calendar year to fiscal year ending year. This is approximate — jail population is an annual average and fiscal years span two calendar years.

---

## County PRCS Allocations

County-level PRCS allocation payments from the State Controller's Office are documented separately in `ca_county_prcs_allocations.csv` (59 rows: 58 counties + statewide total). This file covers FY 2017–18 through 2023–24 and is sourced from SCO Post Release Community Supervision payment xlsx files (https://www.sco.ca.gov/ard_payments_postreleasecommunitysupervision.html). Allocations fund county probation departments for supervising individuals on PRCS under Proposition 57 (2016). FY 2018–19 was the peak year statewide ($28.2M); FY 2023–24 was the lowest ($9.3M), reflecting declining PRCS caseloads.

---

## References

California Department of Justice, Criminal Justice Statistics Center. (2003–2024). *Adult probation caseload actions* [Dataset]. OpenJustice. https://openjustice.doj.ca.gov/data

California State Controller's Office. (2003–2024). *County expenditures* [Dataset]. ByTheNumbers. https://bythenumbers.sco.ca.gov/Finance-Application/County-Expenditures/uctr-c2j8

California State Controller's Office. (2003–2024). *City expenditures* [Dataset]. ByTheNumbers. https://bythenumbers.sco.ca.gov/Finance-Application/City-Expenditures/mxbq-rk3r

California State Controller's Office. (2017–2024). *Post Release Community Supervision payments* [xlsx files]. https://www.sco.ca.gov/ard_payments_postreleasecommunitysupervision.html

Vera Institute of Justice. (2000–2024). *Incarceration trends* [Dataset]. https://www.vera.org/incarceration-trends

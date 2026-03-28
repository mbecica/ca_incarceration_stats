# ca_incarceration_stats

Structured CSV datasets documenting California's criminal justice system from 1920 to 2025, compiled from primary government sources. Covers statewide prison population, parole and community supervision, corrections budgets, county-level incarceration and spending, and state re-entry funding.

---

## Data

All published datasets are in the `data/` directory. See the README files there for full methodology, column definitions, sources, and known gaps.

| File | Coverage | Documentation |
|------|----------|---------------|
| `ca_statewide_prison_population.csv` | 1920–2025, statewide | [README_statewide.md](data/README_statewide.md) |
| `ca_statewide_corrections_budget.csv` | FY 1980–81 to 2025–26 | [README_statewide.md](data/README_statewide.md) |
| `ca_county_incarceration.csv` | 58 counties, 2000–2024 | [README_county.md](data/README_county.md) |
| `ca_county_totals.csv` | 58 counties, FY 2002–03 to 2023–24 | [README_county.md](data/README_county.md) |
| `ca_statewide_reentry_funding.csv` | FY 2000–01 to 2025–26 | [README_reentry.md](data/README_reentry.md) |

The re-entry funding dataset is a work in progress with significant gaps for years before FY 2016–17.

---

## Data Sources

Primary sources include:
- California Department of Corrections and Rehabilitation (CDCR)
- California Department of Justice, Criminal Justice Statistics Center
- California State Controller's Office (SCO) ByTheNumbers portal
- Bureau of Justice Statistics (BJS) Annual Parole Survey
- Chief Probation Officers of California (CPOC)
- Vera Institute of Justice, Incarceration Trends dataset
- Legislative Analyst's Office (LAO)
- Board of State and Community Corrections (BSCC)
- Federal Reserve Economic Data (FRED)

Full citations are in each dataset's README.

---

## Repository Structure

```
data/
  ca_statewide_prison_population.csv
  ca_statewide_corrections_budget.csv
  ca_county_incarceration.csv
  ca_county_totals.csv
  ca_statewide_reentry_funding.csv
  README_statewide.md
  README_county.md
  README_reentry.md
data_sources/        # raw source files (not tracked in git)
```

# Fatal Police Shootings by Race (2015–2024)

## Research Question

Are Black, white, and Hispanic Americans killed by police at the same rate —
and has that pattern changed over time?

## Data

**Source:** Washington Post Fatal Force Database (Version 2)  
Link: https://github.com/washingtonpost/data-police-shootings

The Washington Post has recorded every fatal police shooting in the United States
since 2015, producing one of the most complete public datasets on this issue.
Version 2 is used because it tracks multi-racial and multi-ethnic identities more
accurately than Version 1. Because the federal government does not mandate
reporting of police-caused deaths, this database likely undercounts actual fatalities.

**Key variables used:**

| Variable | Description |
|---|---|
| `date` | Date of the shooting |
| `race` | Race of the person killed (B = Black, W = White, H = Hispanic) |

**Population denominators:**

| Race | Population (Millions) | Source |
|---|---|---|
| Black | 46.9 | U.S. Census Bureau, 2020 |
| White | 204.3 | U.S. Census Bureau, 2020 |
| Hispanic | 62.1 | U.S. Census Bureau, 2020 |

Census source: https://www.census.gov/library/stories/2021/08/improved-race-ethnicity-measures-reveal-united-states-population-much-more-multiracial.html

**Scope of analysis:**

- Years: 2015–2024 (full coverage of the database at time of analysis)
- Racial groups: Black, white, and Hispanic Americans — the three groups with
  the most consistent coding across all years of the database. Other racial
  groups excluded due to inconsistent coding in earlier years.
- Population denominators are fixed at 2020 Census estimates across all years,
  meaning rates reflect changes in shooting frequency, not shifts in population
  composition.

## Approach

The analysis addresses the research question in two steps:

1. **Normalize by population** — Raw death counts are divided by each group's
   population (in millions) to produce a deaths-per-million rate. Without this
   step, white Americans would dominate counts simply due to population size,
   making cross-race comparison misleading.

2. **Track trends over time** — Rates are plotted annually from 2015 to 2024,
   with a vertical annotation marking 2020 to capture whether the George Floyd
   murder and the Black Lives Matter protests that followed produced any
   measurable change in the data.

The analysis is compiled as a Quarto HTML report with embedded ggplot2
visualizations and a written narrative.

## Key Findings

- Every year from 2015 to 2024, Black Americans are killed at more than twice
  the rate of white Americans — this holds without exception across the full decade
- Hispanic Americans fall between the two groups in every year
- The 2020 George Floyd murder and BLM protests produced no measurable change
  in the rate of fatal police shootings for any racial group
- The gap between racial groups has not narrowed, widened, or shifted — it
  has simply persisted across ten years, different administrations, and one
  of the largest social movements in modern American history
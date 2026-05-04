# A World in Motion: Global Forced Displacement Flows (2000–2025)

## Research Question

Where do forcibly displaced people come from, and where do they go?

## Data

**Source:** UNHCR Forced Displacement Flow Dataset  
Link: [https://www.unhcr.org/refugee-statistics/insights/explainers/forcibly-displaced-flow-data.html](https://www.unhcr.org/refugee-statistics/insights/explainers/forcibly-displaced-flow-data.html)

The full dataset covers 1962–2025 and records annual flows of forcibly displaced
people between origin and asylum countries. Each row represents a unique
origin–asylum–year–population type combination.

**Key variables used:**

| Variable | Description |
|---|---|
| `OriginName` | Country people fled *from* |
| `AsylumName` | Country people fled *to* |
| `Count` | Number of people in that flow |
| `Year` | Year of the flow |
| `PT` | Population type (REF = Refugee, ASY = Asylum-seeker) |

**Scope of analysis:**

- Years: 2000–2025 (pre-2000 excluded due to sparse and inconsistent country coverage)
- Population types: Refugees (REF) and Asylum-seekers (ASY) - the two largest
  and most consistently reported UNHCR categories. Other types (IDPs, stateless
  persons) excluded to maintain comparability across years.
- Observations after filtering: 86,275 rows

## Approach

The analysis addresses the research question in three steps:

1. **Trend over time** - Total annual flows are aggregated and plotted from 2000
   to 2025, with crisis annotations marking the Syria conflict (2013), the Rohingya
   exodus from Myanmar (2017), and the Ukraine war (2022).

2. **Top origin and asylum countries** - Cumulative flows are summed by country
   across the full period to identify which countries generate the most outflows
   and which absorb the most inflows. Results are broken down by population type
   (REF vs. ASY) to distinguish refugee and asylum-seeker flows.

3. **Displacement corridors** - Origin–asylum country pairs are ranked by
   cumulative total to reveal which bilateral corridors dominate global
   displacement - and to test whether proximity or policy drives where
   people go.

The analysis is compiled as a Quarto Beamer slide deck (PDF), designed for
a presentation audience rather than a long-form report.

## Key Findings

- Global displacement flows have grown sharply since 2000 and have never
  returned to pre-crisis baselines after major spikes
- Syria and Ukraine together account for nearly half of all cumulative
  outflows since 2000
- The countries absorbing the most displaced people are neighboring
  low- and middle-income countries - Türkiye, Uganda, Pakistan, Bangladesh
- High-income countries like the US and Germany rank in the top 10 as
  high-volume asylum-processing destinations, not purely resettlement ones
- Every top bilateral corridor connects countries that share a border -
  displacement follows geography, not burden-sharing agreements
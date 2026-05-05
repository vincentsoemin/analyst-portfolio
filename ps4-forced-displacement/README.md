# A World in Motion: Global Forced Displacement Flows (2000–2025)

## Research Question

Where do forcibly displaced people come from, and where do they go?

## Data

**Source:** UNHCR Forced Displacement Flow Dataset  
Link: <https://www.unhcr.org/refugee-statistics/insights/explainers/forcibly-displaced-flow-data.html>

The UNHCR records annual movements of forcibly displaced people between countries.
Each record captures how many people moved from a specific country of origin to a
specific country of refuge in a given year, broken down by whether they were
formally recognized as refugees or registered as asylum-seekers.

**Key information recorded for each flow:**

| Field | Description |
|---|---|
| Country of origin | Country people fled *from* |
| Country of refuge | Country people fled *to* |
| Number of people | Size of the flow in that year |
| Year | Year the movement was recorded |
| Status | Whether classified as a refugee or asylum-seeker |

**Scope of analysis:**

- Years: 2000–2025 (the full dataset spans 1962–2025; pre-2000 data excluded
  due to sparse and inconsistent country coverage in many regions)
- Population types: Refugees and asylum-seekers — the two largest and most
  consistently reported categories across all years. Other displaced groups
  such as internally displaced persons and stateless people are excluded to
  maintain comparability over time.
- Observations after filtering: 86,275 records

## Approach

The analysis addresses the research question in three steps:

1. **Trend over time** — Annual totals are aggregated and plotted from 2000
   to 2025, with annotations marking the Syria conflict (2013), the Rohingya
   exodus from Myanmar (2017), and the Ukraine war (2022) to connect spikes
   to identifiable causes.

2. **Top origin and receiving countries** — Cumulative totals are summed by
   country across the full period to identify which countries generate the most
   outflows and which absorb the most people. Results distinguish between
   refugees and asylum-seekers to reveal how the composition of displacement
   differs by country.

3. **Displacement corridors** — Country pairs are ranked by cumulative total
   to reveal which bilateral flows dominate global displacement — and to test
   whether proximity or policy determines where people go.

The analysis is compiled as a Quarto Reveal.js slide deck, designed for a
presentation audience.

## Key Findings

- Global displacement flows have grown sharply since 2000 and have never
  returned to pre-crisis baselines after major spikes
- Syria and Ukraine together account for nearly half of all cumulative
  outflows since 2000
- The countries absorbing the most displaced people are neighboring
  low- and middle-income countries — Türkiye, Uganda, Pakistan, Bangladesh
- High-income countries like the US and Germany rank in the top 10 as
  high-volume asylum-processing destinations, not purely resettlement ones
- Every top bilateral corridor connects countries that share a border —
  displacement follows geography, not burden-sharing agreements

# analyst-portfolio
R-based data analysis portfolio: fatal police shootings by race (2015–2024) and global forced displacement flows (2000–2025). Visualizations built with ggplot2, compiled with Quarto.

# Analyst Portfolio by Soe Min Thein (Vincent)

This repository contains original data analysis work produced for
SIS-750 Data Analysis at American University.

## Projects

### [Fatal Police Shootings by Race (2015–2024)](./ps2-police-shootings/)
An analysis of racial disparities in fatal police shootings in the United States,
using the Washington Post Fatal Force database. Deaths are normalized per million
people by race to enable fair comparison across groups.

**Tools:** R, ggplot2, tidyverse, Quarto

### [A World in Motion: Global Forced Displacement Flows (2000–2025)](./ps4-forced-displacement/)
A slide deck examining where forcibly displaced people come from and where they go,
using UNHCR flow data. Finds that displacement follows borders, not burden-sharing agreements.

**Tools:** R, ggplot2, tidyverse, Quarto Beamer

### [Exemplary Code: Reusable Flow Summarizer](./exemplary-code/)
A general-purpose function for extracting ranked displacement corridors from
UNHCR flow data - demonstrating functional programming and tidy principles.

## Skills Demonstrated
- Data wrangling with `tidyverse` (joins, grouped summaries, `across()`)
- Data visualization with `ggplot2` (annotations, normalized rates, multi-panel layouts)
- Literate programming with `Quarto` (HTML reports, Beamer slide decks)
- Working with real-world datasets (CSV, XLSX, Stata `.dta`)
- Functional R programming
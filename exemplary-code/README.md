# Exemplary Code: A Reusable Country Rankings Extractor

## What It Does

When analyzing forced displacement data, the same analytical question arises
repeatedly: which countries account for the most displacement? The answer differs
depending on whether you are looking at where people are fleeing from or where
they are going – but the underlying logic is identical each time: group by
country, sum the totals, rank, and return the top results for filtering.

In an earlier version of this project, that pipeline was written twice – once
for the top countries of origin, once for the top countries of refuge. The code
worked, but repeating the same logic in two places violates the DRY principle
(Don't Repeat Yourself) and creates a maintenance problem: any change to the
ranking logic would need to be made in two places. The function below abstracts
that repeated pattern into a single, general-purpose tool. By accepting the
grouping dimension as an argument, it handles both use cases with one definition.
The result is cleaner code, easier maintenance, and a function that's genuinely
reusable across any similar UNHCR flow analysis.

## The Code

```r
# ── Helper: get top-N country names for filtering ───────────────────────────
#
# get_top_countries() identifies the highest-volume countries in UNHCR
# displacement flow data and returns their names as a character vector,
# ready to use as a filter in downstream analysis.
#
# Arguments:
#   data      - a data frame of UNHCR flow records, already filtered by
#               year and population type
#   group_var - which dimension to rank by: country of origin or country
#               of refuge (passed as a column name string)
#   n         - number of top countries to return (default: 10)
#
# Returns: a character vector of the top n country names

get_top_countries <- function(data, group_var, n = 10) {
  data |>
    group_by(across(all_of(group_var))) |>
    summarize(Total = sum(Count, na.rm = TRUE), .groups = "drop") |>
    arrange(desc(Total)) |>
    slice_head(n = n) |>
    pull(group_var)
}
```

## Usage

```r
# Top 10 countries people fled from
top_origins <- get_top_countries(filtered_data, "OriginName")

# Top 10 countries people fled to
top_asylum  <- get_top_countries(filtered_data, "AsylumName")

# Use results to filter for visualization
filtered_data |>
  filter(OriginName %in% top_origins) |>
  group_by(OriginName, PT) |>
  summarize(Total = sum(Count, na.rm = TRUE), .groups = "drop")
```

## Sample Output

```r
get_top_countries(filtered_data, "OriginName", n = 5)
#> [1] "Syrian Arab Rep."  "Ukraine"  "South Sudan"  "Sudan"  "Afghanistan"

get_top_countries(filtered_data, "AsylumName", n = 5)
#> [1] "United States of America"  "Türkiye"  "Germany"  "Uganda"  "France"
```

## Key Tidyverse Features Used

| Feature | Purpose |
|---|---|
| `across(all_of(group_var))` | Accepts the grouping column as a string argument, making the function flexible without knowing the column name in advance |
| `slice_head(n = n)` | Clean top-N selection after sorting, safer than `head()` in grouped contexts |
| `pull(group_var)` | Extracts the ranked country names as a plain character vector, ready for use in `filter()` |

## Why This Design

The key design choice is `across(all_of(group_var))` – it allows the function
to group by any column name passed as a string, without hardcoding either
"country of origin" or "country of refuge" into the function body. Passing
`"OriginName"` ranks by origin; passing `"AsylumName"` ranks by destination.
The logic is identical – only the grouping dimension changes. This is the kind
of abstraction that keeps analytical code maintainable as a project grows, and
avoids the silent errors that come from maintaining duplicate pipelines that
gradually drift apart.

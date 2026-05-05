# Exemplary Code: A Reusable Country Rankings Extractor

## What It Does

This function identifies the top-N countries by displacement volume and returns
their names for use as a filter in downstream analysis. The same ranking logic
appeared twice in an earlier version of this project — once for countries of
origin, once for countries of refuge. Abstracting it into a function eliminates
the duplication, reduces the risk of the two pipelines drifting apart, and makes
the intent of each call immediately clear.

## The Code

```r
# Helper: get top-N country names for filtering ---------------------------

# Arguments:
#   data      - UNHCR flow records, pre-filtered by year and population type
#   group_var - column to rank by (country of origin or country of refuge)
#   n         - number of countries to return (default: 10)
#
# Returns: character vector of top-n country names

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

## Key Design Choices

| Feature | Purpose |
|---|---|
| `across(all_of(group_var))` | Groups by any column passed as a string — no hardcoding required |
| `slice_head(n = n)` | Top-N selection after sorting; safer than `head()` in pipelines |
| `pull(group_var)` | Returns a plain character vector ready for use in `filter()` |

Passing the grouping dimension as an argument means one function handles both
use cases — origin countries and receiving countries — with identical logic.
Only the input changes; the pipeline does not.
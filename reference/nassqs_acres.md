# Get NASS Area given a set of parameters.

Get NASS Area given a set of parameters.

## Usage

``` r
nassqs_acres(
  ...,
  area = c("AREA", "AREA PLANTED", "AREA BEARING", "AREA BEARING & NON-BEARING",
    "AREA GROWN", "AREA HARVESTED", "AREA IRRIGATED", "AREA NON-BEARING", "AREA PLANTED",
    "AREA PLANTED, NET")
)
```

## Arguments

- ...:

  either a named list of parameters or a series of parameters to form
  the query

- area:

  the type of area to return. Default is all types.

## Value

a data.frame of acres data

## Examples

``` r
if (FALSE) { # \dontrun{
  # Get Area bearing for Apples in Washington, 2012.
  params <- list(
    commodity_desc = "APPLES",
    year = "2012",
    state_name = "WASHINGTON",
    agg_level_desc = "STATE"
  )
  area <- nassqs_acres(params, area = "AREA BEARING")
  head(area)
} # }
```

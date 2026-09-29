# Get yield records for a specified crop.

Returns yields for other specified parameters. This function is intended
to simplify common requests.

## Usage

``` r
nassqs_yields(...)
```

## Arguments

- ...:

  either a named list of parameters or a series of parameters to form
  the query

## Value

a data.frame of yields data

## Examples

``` r
if (FALSE) { # \dontrun{
  # Get yields for wheat in 2012, all geographies
  params <- list(
    commodity_desc = "WHEAT", 
    year = "2012", 
    agg_level_desc = "STATE",
    state_alpha = "WA")
    
  yields <- nassqs_yields(params)
  head(yields)
} # }
```

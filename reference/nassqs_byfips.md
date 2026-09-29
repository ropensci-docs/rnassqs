# Allow querying for a given set of counties based on FIPS.

This wrapper allows specifying a list of counties by FIPS code. It
iterates over each state in the list of FIPS, downloading for each
separately and then concatenating.

## Usage

``` r
nassqs_byfips(fips, ...)
```

## Arguments

- fips:

  a list of 5-digit fips codes

- ...:

  either a named list of parameters or a series of parameters to form
  the query

## Value

a data.frame of data for each fips code

## Examples

``` r
if (FALSE) { # \dontrun{
nassqs_byfips(
  fips = c("19001", "17005", "17001"),
  commodity_desc = "CORN",
  year = 2019,
  statisticcat_desc = "YIELD")
} # }
```

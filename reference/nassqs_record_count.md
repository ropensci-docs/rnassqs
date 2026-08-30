# Get a count of number of records for given parameters.

Returns the number of records that fit a set of parameters. Useful if
your current parameter set returns more than the 50,000 record limit.

## Usage

``` r
nassqs_record_count(...)
```

## Arguments

- ...:

  either a named list of parameters or a series of parameters to form
  the query

## Value

integer that is the number of records that are returned from the API in
response to the query

## Examples

``` r
if (FALSE) { # \dontrun{
  # Check the number of records returned for corn in 1995, Washington state
  params <- list(
    commodity_desc = "CORN",
    year = "2005",
    agg_level_desc = "STATE",
    state_name = "WASHINGTON"
  )
  
  records <- nassqs_record_count(params) 
  records  # returns 17
} # }
```

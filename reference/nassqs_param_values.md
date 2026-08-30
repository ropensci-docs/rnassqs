# Get all values for a specific parameter.

Returns a list of all possible values for a given parameter. Including
additional parameters will restrict the list of valid values to those
for data meeting the additional parameter restrictions. However, this is
only possible by requesting the entire dataset and then filtering for
unique values. It is recommended to make the query as small as possible
if including additional parameters

## Usage

``` r
nassqs_param_values(param, ...)
```

## Arguments

- param:

  the name of a NASS quickstats parameter

- ...:

  additional parameters for which to filter the valid responses.

## Value

a list containing all valid values for that parameter

## Examples

``` r
if (FALSE) { # \dontrun{
  # See all values available for the statisticcat_desc field. Values may not
  # be available in the context of other parameters you set, for example
  # a given state may not have any 'YIELD' in blueberries if they don't grow
  # blueberries in that state.
  # Requires an API key:
  
  nassqs_param_values("source_desc")

  # Valid values for a parameter given a specific set of additional
  # parameters
  nassqs_param_values("commodity_desc", state_fips_code = "53", 
                      county_code = "077", year = 2017, 
                      group_desc = "EXPENSES")
} # }
```

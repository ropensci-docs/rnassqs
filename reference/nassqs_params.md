# Return list of NASS QS parameters.

Contains a simple hard-coded list of all available parameters. If no
parameter name is provided, returns a list of all parameters. More
information can be found in the API documentation on parameters found at
<https://quickstats.nass.usda.gov/api/#param_define>.

## Usage

``` r
nassqs_params(...)
```

## Arguments

- ...:

  a parameter, series of parameters, or a list of parameters that you
  would like a description of. If missing, a list of all available
  parameters is returned.

## Value

a list of all available parameters or a description of a subset

## Examples

``` r
# Get a list of all available parameters
nassqs_params()
#>  [1] "agg_level_desc"        "asd_code"              "asd_desc"             
#>  [4] "begin_code"            "class_desc"            "commodity_desc"       
#>  [7] "congr_district_code"   "country_code"          "country_name"         
#> [10] "county_ansi"           "county_code"           "county_name"          
#> [13] "domaincat_desc"        "domain_desc"           "end_code"             
#> [16] "freq_desc"             "group_desc"            "load_time"            
#> [19] "location_desc"         "prodn_practice_desc"   "reference_period_desc"
#> [22] "region_desc"           "sector_desc"           "short_desc"           
#> [25] "state_alpha"           "state_ansi"            "state_name"           
#> [28] "state_fips_code"       "statisticcat_desc"     "source_desc"          
#> [31] "unit_desc"             "util_practice_desc"    "watershed_code"       
#> [34] "watershed_desc"        "week_ending"           "year"                 
#> [37] "zip_5"                

# Get information about specific parameters
nassqs_params("source_desc", "group_desc")
#> [1] "source_desc: Data source. Either 'CENSUS' or 'SURVEY'"       
#> [2] "group_desc: Commodity group category. A subset of the sector"
```

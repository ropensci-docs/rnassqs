# Issue a GET request to the NASS 'Quick Stats' API

This is the workhorse of the package that provides the core request
functionality to the NASS 'Quick Stats' API:
<https://quickstats.nass.usda.gov/api/>. In most cases
[`nassqs()`](https://docs.ropensci.org/rnassqs/reference/nassqs.md) or
other high-level functions should be used. `nassqs_GET()` uses
[`httr::GET()`](https://httr.r-lib.org/reference/GET.html) to make a
HTTP GET request, which returns a request object which must then be
parsed to a data.frame, list, or other `R` object. Higher-level
functions will do that parsing automatically. However, if you need
access to the request object directly, `nassqs_GET()` provides that.

## Usage

``` r
nassqs_GET(
  ...,
  api_path = c("api_GET", "get_param_values", "get_counts"),
  progress_bar = TRUE,
  max_retries = 2,
  format = c("csv", "json", "xml")
)
```

## Arguments

- ...:

  either a named list of parameters or a series of parameters to use in
  the query

- api_path:

  the API path that determines the type of request being made.

- progress_bar:

  whether to display the project bar or not.

- max_retries:

  maximum number of retries if a 429 error occurs

- format:

  The format to return the query in. Only useful if as = "text".

## Value

a [`httr::GET()`](https://httr.r-lib.org/reference/GET.html) response
object

## Examples

``` r
if (FALSE) { # \dontrun{
  # Yields for corn in 2012 in Washington
  params <- list(commodity_desc = "CORN",
                 year = 2012,
                 agg_level_desc = "STATE",
                 state_alpha = "WA",
                 statisticcat_desc = "YIELD")

  # Returns a request object that must be parsed either manually or
  # by using nassqs_parse()
  response <- nassqs_GET(params)
  yields <- nassqs_parse(response)
  head(yields)

  # Get the number of records that would be returned for a given request
  # Equivalent to 'nassqs_record_count(params)'
  response <- nassqs_GET(params, api_path = "get_counts")
  records <- nassqs_parse(response)
  records

  # Get the list of allowable values for the parameters 'statisticcat_desc'
  # Equivalent to 'nassqs_param_values("statisticcat_desc")'
  req <- nassqs_GET(list(param = "statisticcat_desc"),
                    api_path = "get_param_values")
  statisticcat_desc_values <- nassqs_parse(req, as = "list")
  head(statisticcat_desc_values)
} # }
```

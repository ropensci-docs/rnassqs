# Parse a response object from `nassqs_GET()`.

Returns a data frame, list, or text string. If a data.frame, all columns
except `year` strings because the 'Quick Stats' data returns suppressed
data as '(D)', '(Z)', or other character indicators which mean different
things. Converting the value to a numerical results in NA, which loses
that information.

## Usage

``` r
nassqs_parse(req, as_numeric = TRUE, as = c("data.frame", "list", "text"), ...)
```

## Arguments

- req:

  the GET response from
  [`nassqs_GET()`](https://docs.ropensci.org/rnassqs/reference/nassqs_GET.md)

- as_numeric:

  whether to convert values to numeric format.

- as:

  whether to return a data.frame, list, or text string

- ...:

  additional parameters passed to
  [`jsonlite::fromJSON()`](https://jeroen.r-universe.dev/jsonlite/reference/fromJSON.html)
  or [`utils::read.csv()`](https://rdrr.io/r/utils/read.table.html)

## Value

a data frame, list, or text string of the content from the response.

## Examples

``` r
if (FALSE) { # \dontrun{
  # Set parameters and make the request
  params <- list(commodity_desc = "CORN",
                 year = 2012,
                 agg_level_desc = "STATE",
                 state_alpha = "WA",
                 statisticcat_desc = "YIELD")
  response <- nassqs_GET(params)

  # Parse the response to a data frame
  corn <- nassqs_parse(response, as = "data.frame")
  head(corn)

  # Parse the response into a raw character string.
  corn_text<- nassqs_parse(response, as = "text")
  head(corn_text)

  # Get a list of parameter values and parse as a list
  response <- nassqs_GET(list(param = "statisticcat_desc"),
                    api_path = "get_param_values")
  statisticcat_desc_values <- nassqs_parse(response, as = "list")
  head(statisticcat_desc_values)
} # }
```

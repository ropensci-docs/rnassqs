# Check the response.

Check that the response is valid, i.e. that it doesn't exceed 50,000
records and that all the parameter values are valid. This is used to
ensure that the query is valid before querying to reduce wait times
before receiving an error.

## Usage

``` r
nassqs_check(response)
```

## Arguments

- response:

  a [`httr::GET()`](https://httr.r-lib.org/reference/GET.html) request
  result returned from the API.

## Value

nothing if check is passed, or an informative error if not passed.

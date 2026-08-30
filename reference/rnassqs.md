# rnassqs: Access the NASS 'Quick Stats' API

rnassqs is a wrapper for the United States Department of Agriculture's
National Agricultural Statistical Service (NASS) 'Quick Stats' API to
enable getting NASS 'Quick Stats' data directly from R. Based on the
httr API package guide.

## Details

The functions in this package facilitate getting data from NASS 'Quick
Stats'. It handles the API key checking and storage, authorization, rate
limiting, and fetching of data.

To avoid 429 ("Too Many Requests") errors from the API, this package
implements rate limiting that ensures API calls are made at a reasonable
pace (default: 1 call every 3 seconds). Rate limiting can be configured
using the
[`nassqs_rate_limit()`](https://docs.ropensci.org/rnassqs/reference/nassqs_rate_limit.md)
function.

## References

<https://quickstats.nass.usda.gov>

## See also

<https://quickstats.nass.usda.gov/api/>

## Author

Nicholas Potter

# Manage adaptive API rate limiting

The NASS Quick Stats API has rate limits to prevent abuse. This function
helps manage those rate limits by tracking the time between requests and
sleeping as needed to avoid exceeding the rate limit. It uses an
adaptive approach that starts with faster requests and slows down if
rate limits are encountered.

## Usage

``` r
rate_limit(
  rate_seconds = getOption("nassqs.rate_seconds", 0.2),
  throttled_rate_seconds = getOption("nassqs.throttled_rate_seconds", 3),
  override = getOption("nassqs.override_rate_limit", FALSE)
)
```

## Arguments

- rate_seconds:

  The minimum time in seconds between API requests. Default is 0.2
  seconds (5 requests per second).

- throttled_rate_seconds:

  The time to wait between requests when throttled. Default is 3
  seconds.

- override:

  Whether to override the rate limiting. Default is FALSE. Set to TRUE
  to bypass rate limiting (not recommended for normal use).

## Value

Invisibly returns the time waited in seconds.

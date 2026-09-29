# Changelog

## rnassqs 0.6.4

- incorporate PR from austinwpearce that auto-adjusts call time to meet
  QuickStats rate limiters

## rnassqs 0.6.3

CRAN release: 2024-08-30

- Update to work with R 4.4.0

## rnassqs 0.6.2

- Add more testing for http errors, explicit handling of error messages
  other than 413 and 429.
- Add querying by fips code with `nassqs_fips()` \[Issue
  [\#30](https://github.com/ropensci/rnassqs/issues/30)\]
- Depends on R(\>= 3.5.0) since some test objects are saved in RDS
  format.

## rnassqs 0.6.1

CRAN release: 2022-03-11

- Explicit handling for error code 429 has been added.

## rnassqs 0.6.0

CRAN release: 2022-03-10

- The default download is CSV format instead of JSON to reduce download
  sizes.
- Additional tests have been added.
- Parameters have been clarified so that only the parameters usable in a
  query are returned by
  [`nassqs_params()`](https://docs.ropensci.org/rnassqs/reference/nassqs_params.md)
  and `format` is a specific argument to
  [`nassqs()`](https://docs.ropensci.org/rnassqs/reference/nassqs.md).
  Although `CV` and `Value` are returned columns from Quick Stats, they
  are not queriable parameters.
- By default,
  [`nassqs()`](https://docs.ropensci.org/rnassqs/reference/nassqs.md)
  now converts the character `Value` to numeric. Raw character `Value`
  can be obtained by `as_numeric = FALSE`.
- Documentation for query parameters has been improved and available
  query parameters are explicit in
  [`nassqs()`](https://docs.ropensci.org/rnassqs/reference/nassqs.md)
  now. Functionality is unchanged but parameter names are listed and
  available in help. Thanks to Robert Dinterman for the initial
  contribution.
- An option to see valid parameter values given a query of other values
  in
  [`nassqs_param_values()`](https://docs.ropensci.org/rnassqs/reference/nassqs_param_values.md)
  has been added.
- [`nassqs_record_count()`](https://docs.ropensci.org/rnassqs/reference/nassqs_record_count.md)
  now validates parameters.

## rnassqs 0.5.0

CRAN release: 2019-08-19

- Approval for rOpensci inclusion!
- Additional testing to improve code coveral by
  [@nealrichardson](https://github.com/nealrichardson)
- Small changes for rOpensci review process
- Switch to rOpensci repository
- Change in syntax to allow for lower case query parameter values
- Change in syntax to allow for specifying each parameter as a separate
  function argument rather than as a single list (in addition to
  specifying a single list)
- Create package website with pkgdown
- Standardize code style in package code, examples, and vignette
- Simplify authentication
- Expanded test coverage with use of httptest::with_mock_api()
- Better clarification in documentation and documentation examples
- Improved README and vignette

## rnassqs 0.4.0.9000

- Development version

## rnassqs 0.4.0

CRAN release: 2019-05-03

- Add automated unit tests that work locally and others that work on
  CRAN.
- Improve documentation for core functions.
- Add parsing for CSV formatted data.
- Improve authentication.
- Simplify function calls to eliminate redundant calls.
- Add working examples and tests.
- fix name error in the function `nassqs_params_values` to
  `nassqs_param_values`

## rnassqs 0.3.0

- Prepare package for CRAN submission.
- Vignettes and README.md are up to date with respect to current
  functions.
- Fix tests.
- Minor spelling fixes contributed by Julia Piaskowski \<@jpiaskowski\>
- Remove test code that couldn’t be run due to API needing
  authentication.

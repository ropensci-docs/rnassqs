# Get data and return a data frame

The primary function in the `rnassqs` package, `nassqs` makes a HTTP GET
request to the USDA-NASS Quick Stats API and returns the data parsed as
a data.frame, plain text, or list. Various other functions make use of
`nassqs` to make specific queries. For a data request the Quick Stats
API returns JSON that when parsed to a data.frame contains 39 columns
and a varying number of rows depending on the query. Unfortunately there
is not a way to restrict the number of columns.

## Usage

``` r
nassqs(
  ...,
  agg_level_desc = NULL,
  asd_code = NULL,
  asd_desc = NULL,
  begin_code = NULL,
  class_desc = NULL,
  commodity_desc = NULL,
  congr_district_code = NULL,
  country_code = NULL,
  country_name = NULL,
  county_ansi = NULL,
  county_code = NULL,
  county_name = NULL,
  domaincat_desc = NULL,
  domain_desc = NULL,
  end_code = NULL,
  freq_desc = NULL,
  group_desc = NULL,
  load_time = NULL,
  location_desc = NULL,
  prodn_practice_desc = NULL,
  reference_period_desc = NULL,
  region_desc = NULL,
  sector_desc = NULL,
  short_desc = NULL,
  source_desc = NULL,
  state_alpha = NULL,
  state_ansi = NULL,
  state_fips_code = NULL,
  state_name = NULL,
  statisticcat_desc = NULL,
  unit_desc = NULL,
  util_practice_desc = NULL,
  watershed_code = NULL,
  watershed_desc = NULL,
  week_ending = NULL,
  year = NULL,
  zip_5 = NULL,
  as_numeric = TRUE,
  progress_bar = TRUE,
  format = "csv",
  as = "data.frame"
)
```

## Arguments

- ...:

  either a named list of parameters or a series of additional parameters
  that include operations, e.g. `year__GE = 2010` for all records in
  2010 and later. See `details` for information on available operators.

- agg_level_desc:

  Geographic level ("AGRICULTURAL DISTRICT", "COUNTY", "INTERNATIONAL",
  "NATIONAL", "REGION : MULTI-STATE", "REGION : SUB-STATE", "STATE",
  "WATERSHED", or "ZIP CODE").

- asd_code:

  Agriculture statistical district code.

- asd_desc:

  Agriculture statistical district name / description.

- begin_code:

  Week number indicating when the data series begins.

- class_desc:

  Commodity class.

- commodity_desc:

  Commodity, the primary subject of interest (e.g., "CORN", "CATTLE",
  "LABOR", "TRACTORS", "OPERATORS").

- congr_district_code:

  Congressional District codes.

- country_code:

  Country code.

- country_name:

  Country name.

- county_ansi:

  County ANSI code.

- county_code:

  County FIPS code.

- county_name:

  County name.

- domaincat_desc:

  Domain category within a domain (e.g., under domain_desc = "SALES",
  domain categories include \$1,000 TO \$9,999, \$10,000 TO \$19,999,
  etc).

- domain_desc:

  Domain, a characteristic of operations that produce a particular
  commodity (e.g., "ECONOMIC CLASS", "AREA OPERATED", "NAICS
  CLASSIFICATION", "SALES"). For chemical usage data, the domain
  describes the type of chemical applied to the commodity. The
  domain_desc: = "TOTAL" will have no further breakouts; i.e., the data
  value pertains completely to the short_desc.

- end_code:

  = Week number that the data series ends.

- freq_desc:

  Time period type covered by the data ("ANNUAL", "SEASON", "MONTHLY",
  "WEEKLY", "POINT IN TIME"). "MONTHLY" often covers more than one
  month. "POINT IN TIME" is for a particular day.

- group_desc:

  Commodity group within a sector (e.g., under sector_desc = "CROPS",
  the groups are "FIELD CROPS", "FRUIT & TREE NUTS", "HORTICULTURE", and
  "VEGETABLES").

- load_time:

  Date and time of the data load, e.g. "2015-02-17 16:05:20".

- location_desc:

  Location code, e.g. 5-digit fips code for counties.

- prodn_practice_desc:

  Production practice, (e.g. "UNDER PROTECTION", "OWNED, RIGHTS,
  LEASED", "ORGANIC, TRANSITIONING", "HIRED MANAGER").

- reference_period_desc:

  Reference period of the data (e.g. "JUN", "MID SEP", "WEEK \#32").

- region_desc:

  Region name (e.g. "TEXAS", "WA & OR", "WEST COAST", "UMATILLA").

- sector_desc:

  Sector, the five high level, broad categories useful to narrow down
  choices. ("ANIMALS & PRODUCTS", "CROPS", "DEMOGRAPHICS", "ECONOMICS",
  or "ENVIRONMENTAL").

- short_desc:

  A concatenation of six columns: `commodity_desc`, `class_desc`,
  `prodn_practice_desc`, `util_practice_desc`, `statisticcat_desc`, and
  `unit_desc`.

- source_desc:

  Source of data ("CENSUS" or "SURVEY"). Census program includes the
  Census of Ag as well as follow up projects. Survey program includes
  national, state, and county surveys.

- state_alpha:

  2-character state abbreviation, e.g. "NM".

- state_ansi:

  State ANSI code.

- state_fips_code:

  State FIPS code.

- state_name:

  Full name of the state, e.g. "ALABAMA".

- statisticcat_desc:

  Statistical category of the data (e.g., "AREA HARVESTED", "PRICE
  RECEIVED", "INVENTORY", "SALES").

- unit_desc:

  The units of the data (e.g. "TONS / ACRE", "TREES", "OPERATIONS",
  "NUMBER", "LB / ACRE", "BU / PLANTED ACRE").

- util_practice_desc:

  Utilization practice (e.g. "WIND", "SUGAR", "SILAGE", "ONCE REFINED",
  "FEED", "ANIMAL FEED").

- watershed_code:

  Watershed code as 8-digit HUC (e.g. "13020100").

- watershed_desc:

  Watershed/HUC name (e.g. "UPPER COLORADO").

- week_ending:

  Date of ending week (e.g. "1975-11-22").

- year:

  Year of the data. Conditional values are possible by appending an
  operation to the parameter, e.g. "year\_\_GE = 2020" will return all
  records with year \>= 2020. See `details` for more on operations.

- zip_5:

  5-digit zip code.

- as_numeric:

  Whether to convert data to numeric format. Conversion will replace
  missing notation such as "(D)" or "(Z)" with NA, but removes the need
  to convert to numeric format after querying.

- progress_bar:

  Whether or not to display the progress bar.

- format:

  The format to return the query in. Only useful if as = "text".

- as:

  whether to return a data.frame, list, or text string. See
  [`nassqs_parse()`](https://docs.ropensci.org/rnassqs/reference/nassqs_parse.md).

## Value

a data frame, list, or text string of requested data.

## Details

`nassqs()` accepts all parameters that are accepted by the USDA-NASS
Quick Stats. These parameters are listed in
[`nassqs_params()`](https://docs.ropensci.org/rnassqs/reference/nassqs_params.md),
and are used to form the data query.

Parameters can be modified by operations, which are appended to the
parameter name. For example, "year\_\_GE = 2020" will fetch data in 2020
and after. Operations can take the following form:

- \_\_LE: less than or equal (\<=)

- \_\_LT: less than (\<)

- \_\_GT: greater than (\>)

- \_\_GE: = \>=

- \_\_LIKE = like

- \_\_NOT_LIKE = not like

- \_\_NE = not equal

## See also

[`nassqs_GET()`](https://docs.ropensci.org/rnassqs/reference/nassqs_GET.md),
[`nassqs_parse()`](https://docs.ropensci.org/rnassqs/reference/nassqs_parse.md),
[`nassqs_yields()`](https://docs.ropensci.org/rnassqs/reference/nassqs_yields.md),
[`nassqs_acres()`](https://docs.ropensci.org/rnassqs/reference/nassqs_acres.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Get corn yields in Virginia in 2012
  params <- list(commodity_desc = "CORN",
                 year = 2012,
                 agg_level_desc = "COUNTY",
                 state_alpha = "VA",
                 statisticcat_desc = "YIELD")
  yields <- nassqs(params)
  head(yields)
} # }
```

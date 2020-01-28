01\_debugging\_spartan.R
================
lucas
2020-01-27

``` r
library(tidyverse)
```

    ## ── Attaching packages ──────────────────────────────────────────────────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.2.1     ✔ purrr   0.3.2
    ## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
    ## ✔ tidyr   1.0.0     ✔ stringr 1.4.0
    ## ✔ readr   1.3.1     ✔ forcats 0.4.0

    ## ── Conflicts ─────────────────────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
# Separate, flatten, and trim values in the vector
clean <- function(vec) {
  # browser()
  # recover()
  values <- strsplit(as.character(vec), ",")
  flat_values <- unlist(values)
  trimmed_values <- str_trim(flat_values)
  trimmed_values
}

# Clean vector and get the unique values
uniquify <- function(vec) {
  clean_values <- clean(vec)
  unique_values <- unique(clean_values)
  unique_values
}

# Read data and get unique climate values
get_climates <- function() {
  planets <- read.csv2(here::here("planets.csv"),stringsAsFactors = F)
  unique_climate <- uniquify(planets$climate)
  unique_climate
}

# This example originally used in Amanda Gadrow's excellent debugging talk at rstudio::conf 2018,
# https://github.com/ajmcoqui/debuggingRStudio/blob/b70a3575a3ff5e7867b05fb5e84568abba426c4b/error_example.R

# New comments
```

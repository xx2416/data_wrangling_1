Data Import
================

I’m an R Markdown document!

# Section 1

Import data using the `readr` package

``` r
library(readr)
FAS_litters <- read_csv("data_import_examples/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
FAS_litters <- janitor::clean_names(FAS_litters)
```

look at the data

``` r
View(FAS_litters)
skimr::skim(FAS_litters)
```

`read_csv` options

``` r
read_csv("data_import_examples/FAS_litters.csv", na=c("","NA",999,888),skip = 2)
```

    ## Rows: 47 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Con7, #1/2/95/2
    ## dbl (6): 27, 42, 19, 8, 0, 7
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

    ## # A tibble: 47 × 8
    ##    Con7  `#1/2/95/2`      `27`  `42`  `19`   `8`   `0`   `7`
    ##    <chr> <chr>           <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
    ##  1 Con7  #5/5/3/83/3-3    26    41.4    19     6     0     5
    ##  2 Con7  #5/4/2/95/2      28.5  44.1    19     5     1     4
    ##  3 Con7  #4/2/95/3-3      NA    NA      20     6     0     6
    ##  4 Con7  #2/2/95/3-2      NA    NA      20     6     0     4
    ##  5 Con7  #1/5/3/83/3-3/2  NA    NA      20     9     0     9
    ##  6 Con8  #3/83/3-3        NA    NA      20     9     1     8
    ##  7 Con8  #2/95/3          NA    NA      20     8     0     8
    ##  8 Con8  #3/5/2/2/95      28.5  NA      20     8     0     8
    ##  9 Con8  #5/4/3/83/3      28    NA      19     9     0     8
    ## 10 Con8  #1/6/2/2/95-2    NA    NA      20     7     0     6
    ## # … with 37 more rows

## import other file formats

we need to

``` r
library(readxl)
mlb_df=read_excel("data_import_examples/mlb11.xlsx")
```

``` r
View(mlb_df)
```

``` r
lotr_words_df=read_excel("data_import_examples/LotR_Words.xlsx")
```

    ## New names:
    ## • `` -> `...2`
    ## • `` -> `...3`
    ## • `` -> `...4`
    ## • `` -> `...6`
    ## • `` -> `...7`
    ## • `` -> `...8`
    ## • `` -> `...10`
    ## • `` -> `...11`

read in a SAS dataset

``` r
library(haven)
pulse_df<-read_sas("data_import_examples/public_pulse_data.sas7bdat")
```

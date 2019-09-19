data\_wrangling\_i
================
Xin He
9/17/2019

\#\#load in the litters
dataset

``` r
litters_data = read_csv(file = "./FAS_litters.csv",skip = 10, col_names = FALSE)
```

    ## Parsed with column specification:
    ## cols(
    ##   X1 = col_character(),
    ##   X2 = col_character(),
    ##   X3 = col_double(),
    ##   X4 = col_double(),
    ##   X5 = col_double(),
    ##   X6 = col_double(),
    ##   X7 = col_double(),
    ##   X8 = col_double()
    ## )

``` r
litters_data = janitor::clean_names(litters_data)
names(litters_data)
```

    ## [1] "x1" "x2" "x3" "x4" "x5" "x6" "x7" "x8"

``` r
litters_data
```

    ## # A tibble: 40 x 8
    ##    x1    x2                 x3    x4    x5    x6    x7    x8
    ##    <chr> <chr>           <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
    ##  1 Con8  #3/5/2/2/95      28.5  NA      20     8     0     8
    ##  2 Con8  #5/4/3/83/3      28    NA      19     9     0     8
    ##  3 Con8  #1/6/2/2/95-2    NA    NA      20     7     0     6
    ##  4 Con8  #3/5/3/83/3-3-2  NA    NA      20     8     0     8
    ##  5 Con8  #2/2/95/2        NA    NA      19     5     0     4
    ##  6 Con8  #3/6/2/2/95-3    NA    NA      20     7     0     7
    ##  7 Mod7  #59              17    33.4    19     8     0     5
    ##  8 Mod7  #103             21.4  42.1    19     9     1     9
    ##  9 Mod7  #1/82/3-2        NA    NA      19     6     0     6
    ## 10 Mod7  #3/83/3-2        NA    NA      19     8     0     8
    ## # … with 30 more rows

\#\#load in the pups data

``` r
pups_data = read_csv(file = "./FAS_pups.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   `Litter Number` = col_character(),
    ##   Sex = col_double(),
    ##   `PD ears` = col_double(),
    ##   `PD eyes` = col_double(),
    ##   `PD pivot` = col_double(),
    ##   `PD walk` = col_double()
    ## )

``` r
pups_data = janitor::clean_names(pups_data)
pups_data
```

    ## # A tibble: 313 x 6
    ##    litter_number   sex pd_ears pd_eyes pd_pivot pd_walk
    ##    <chr>         <dbl>   <dbl>   <dbl>    <dbl>   <dbl>
    ##  1 #85               1       4      13        7      11
    ##  2 #85               1       4      13        7      12
    ##  3 #1/2/95/2         1       5      13        7       9
    ##  4 #1/2/95/2         1       5      13        8      10
    ##  5 #5/5/3/83/3-3     1       5      13        8      10
    ##  6 #5/5/3/83/3-3     1       5      14        6       9
    ##  7 #5/4/2/95/2       1      NA      14        5       9
    ##  8 #4/2/95/3-3       1       4      13        6       8
    ##  9 #4/2/95/3-3       1       4      13        7       9
    ## 10 #2/2/95/3-2       1       4      NA        8      10
    ## # … with 303 more rows

\#\#Parsing columns

``` r
litters_data = read_csv(file = "./FAS_litters.csv",
  col_types = cols(
    Group = col_character(),
    `Litter Number` = col_character(),
    `GD0 weight` = col_double(),
    `GD18 weight` = col_double(),
    `GD of Birth` = col_integer(),
    `Pups born alive` = col_integer(),
    `Pups dead @ birth` = col_integer(),
    `Pups survive` = col_integer()
  )
)
```

the use of’’ is because of the exist of space\!

\#\#reading in an excel file…

``` r
mlb11_data = read_excel(path = "./mlb11.xlsx")
```

mlb11\_data = read\_excel(path = “./mlb11.xlsx”, sheet = , range =
“A1:D7”)

\#\#read in SAS

``` r
pulse_data = haven::read_sas("./public_pulse_data.sas7bdat")
```

## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax
for authoring HTML, PDF, and MS Word documents. For more details on
using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that
includes both content as well as the output of any embedded R code
chunks within the document. You can embed an R code chunk like this:

``` r
summary(cars)
```

    ##      speed           dist       
    ##  Min.   : 4.0   Min.   :  2.00  
    ##  1st Qu.:12.0   1st Qu.: 26.00  
    ##  Median :15.0   Median : 36.00  
    ##  Mean   :15.4   Mean   : 42.98  
    ##  3rd Qu.:19.0   3rd Qu.: 56.00  
    ##  Max.   :25.0   Max.   :120.00

## Including Plots

You can also embed plots, for example:

![](data_wrangling_i_files/figure-gfm/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.

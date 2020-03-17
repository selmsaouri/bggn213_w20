COVID-19
================

Coronavirus
-----------

Here we analyze infection data for the 2019 novel Coronavirus COVID-19 (2019-nCoV) epidemic. The raw data is pulled from the Johns Hopkins University Center for Systems Science and Engineering (JHU CCSE) Coronavirus repository.

A CSV file is available here <https://github.com/RamiKrispin/coronavirus-csv>

``` r
url <- "https://tinyurl.com/COVID-2019"
virus <- read.csv(url)

tail(virus)
```

    ##       Province.State Country.Region     Lat     Long       date cases      type
    ## 42115       Zhejiang          China 29.1832 120.0934 2020-03-10    15 recovered
    ## 42116       Zhejiang          China 29.1832 120.0934 2020-03-11     4 recovered
    ## 42117       Zhejiang          China 29.1832 120.0934 2020-03-12     2 recovered
    ## 42118       Zhejiang          China 29.1832 120.0934 2020-03-13     0 recovered
    ## 42119       Zhejiang          China 29.1832 120.0934 2020-03-14    14 recovered
    ## 42120       Zhejiang          China 29.1832 120.0934 2020-03-15     0 recovered

> Q1. How many total infected cases are there around the world?

``` r
total_cases <- sum(virus$cases)
total_cases
```

    ## [1] 249923

Lets have a look at the *$type* column

``` r
table(virus$type)
```

    ## 
    ## confirmed     death recovered 
    ##     14040     14040     14040

> Q2. How many deaths linked to infected cases have there been?

``` r
inds <- virus$type =="death"
death_cases <- sum(virus[inds,"cases"])
death_cases
```

    ## [1] 6440

> Q3. What is the overall death rate?

Percent death

``` r
round(death_cases/total_cases * 100, 2)
```

    ## [1] 2.58

> Q4. What is the death rate in "Mainland China"?

``` r
china <- virus[,2] == "Mainland China"
china_virus <- virus[china,]
```

``` r
total_china_cases <- sum(china_virus$cases)
total_china_cases
```

    ## [1] 0

``` r
death <- china_virus$type == "death"
death_china_cases <- sum(china_virus[death, "cases"])
death_china_cases
```

    ## [1] 0

``` r
round(death_china_cases/total_china_cases * 100, 2)
```

    ## [1] NaN

> Q5. What is the death rate in Italy, Iran and the US?

Italy
=====

``` r
italy <- virus[,2] == "Italy"
italy_virus <- virus[italy,]
```

``` r
total_italy_cases <- sum(italy_virus$cases)
total_italy_cases
```

    ## [1] 28891

``` r
death_italy <- italy_virus$type == "death"
death_italy_cases <- sum(italy_virus[death_italy, "cases"])
death_italy_cases
```

    ## [1] 1809

``` r
round(death_italy_cases/total_italy_cases * 100, 2)
```

    ## [1] 6.26

Iran
====

``` r
iran <- virus[,2] == "Iran"
iran_virus <- virus[iran,]
```

``` r
total_iran_cases <- sum(iran_virus$cases)
total_iran_cases
```

    ## [1] 19252

``` r
death_iran <- iran_virus$type == "death"
death_iran_cases <- sum(iran_virus[death_iran, "cases"])
death_iran_cases
```

    ## [1] 724

``` r
round(death_iran_cases/total_iran_cases * 100, 2)
```

    ## [1] 3.76

US
==

``` r
us <- virus[,2] == "US"
us_virus <- virus[us,]
```

``` r
total_us_cases <- sum(us_virus$cases)
total_us_cases
```

    ## [1] 3574

``` r
death_us <- us_virus$type == "death"
death_us_cases <- sum(us_virus[death_us, "cases"])
death_us_cases
```

    ## [1] 63

``` r
round(death_us_cases/total_us_cases * 100, 2)
```

    ## [1] 1.76

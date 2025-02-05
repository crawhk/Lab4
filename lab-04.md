Lab 04 - La Quinta is Spanish for next to Denny’s, Pt. 1
================
Insert your name here
Insert date here

### Load packages and data

``` r
library(tidyverse) 
library(dsbox) 
```

``` r
states <- read_csv("data/states.csv")
```

### Exercise 1

> What are the dimensions of the Denny’s dataset? (Hint: Use inline R
> code and functions like nrow and ncol to compose your answer.) What
> does each row in the dataset represent? What are the variables?

Denny’s Data: 1,643 Rows - observations (i.e., dennys locations)

6 columns - variables (address, city, state, zip, longitude, latitude)

``` r
glimpse(dennys)
```

    ## Rows: 1,643
    ## Columns: 6
    ## $ address   <chr> "2900 Denali", "3850 Debarr Road", "1929 Airport Way", "230 …
    ## $ city      <chr> "Anchorage", "Anchorage", "Fairbanks", "Auburn", "Birmingham…
    ## $ state     <chr> "AK", "AK", "AK", "AL", "AL", "AL", "AL", "AL", "AL", "AL", …
    ## $ zip       <chr> "99503", "99508", "99701", "36849", "35207", "35294", "35056…
    ## $ longitude <dbl> -149.8767, -149.8090, -147.7600, -85.4681, -86.8317, -86.803…
    ## $ latitude  <dbl> 61.1953, 61.2097, 64.8366, 32.6033, 33.5615, 33.5007, 34.206…

### Exercise 2

> What are the dimensions of the La Quinta’s dataset? What does each row
> in the dataset represent? What are the variables?

LaQuinta Data 909 Rows - observations (i.e., la qunitas locations)

6 columns - varaibles (address, city, state, zip, longitude, latitude)

``` r
glimpse(laquinta)
```

    ## Rows: 909
    ## Columns: 6
    ## $ address   <chr> "793 W. Bel Air Avenue", "3018 CatClaw Dr", "3501 West Lake …
    ## $ city      <chr> "\nAberdeen", "\nAbilene", "\nAbilene", "\nAcworth", "\nAda"…
    ## $ state     <chr> "MD", "TX", "TX", "GA", "OK", "TX", "AG", "TX", "NM", "NM", …
    ## $ zip       <chr> "21001", "79606", "79601", "30102", "74820", "75254", "20345…
    ## $ longitude <dbl> -76.18846, -99.77877, -99.72269, -84.65609, -96.63652, -96.8…
    ## $ latitude  <dbl> 39.52322, 32.41349, 32.49136, 34.08204, 34.78180, 32.95164, …

### Exercise 3

> Take a look at the websites that the data come from (linked above).
> Are there any La Quinta’s locations outside of the US? If so, which
> countries? What about Denny’s?

Yes, there are La Quinta’s locations outside of the US –\> Canada,
Mexico, China, New Zealand, Turkey, United Arab Emirates, Chile,
Colombia, and Ecuador

The current Dennys data set only includes US states, although Google
says Denny’s has now expanded globally.

``` r
select(states)
```

    ## # A tibble: 51 × 0

…

### Exercise 4

…

### Exercise 5

…

### Exercise 6

…

Add exercise headings as needed.

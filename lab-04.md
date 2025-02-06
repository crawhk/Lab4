Lab 04 - La Quinta is Spanish for next to Denny’s, Pt. 1
================
Hannah Crawley
2/6/25

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

``` r
laquinta %>% 
  count(state) %>% 
  arrange(n)
```

    ## # A tibble: 59 × 2
    ##    state     n
    ##    <chr> <int>
    ##  1 AG        1
    ##  2 ANT       1
    ##  3 BC        1
    ##  4 CH        1
    ##  5 FM        1
    ##  6 ME        1
    ##  7 ON        1
    ##  8 QR        1
    ##  9 SL        1
    ## 10 VE        1
    ## # ℹ 49 more rows

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

### Exercise 4

> Now take a look at the data. What would be some ways of determining
> whether or not either establishment has any locations outside the US
> using just the data (and not the websites). Don’t worry about whether
> you know how to implement this, just brainstorm some ideas. Write down
> at least one as your answer, but you’re welcomed to write down a few
> options too. - looking at number of states and longitude/latitude

### Exercise 5

> Find the Denny’s locations that are outside the US, if any. To do so,
> filter the Denny’s locations for observations where state is not in
> “states\$abbreviation.”

> The code for this is given below. Note that the “%in%” operator
> matches the states listed in the state variable to those listed in
> “states\$abbreviation”. The ! operator means not. Are there any
> Denny’s locations outside the US?

``` r
dennys %>%
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 0 × 6
    ## # ℹ 6 variables: address <chr>, city <chr>, state <chr>, zip <chr>,
    ## #   longitude <dbl>, latitude <dbl>

### Exercise 6

> Add a country variable to the Denny’s dataset and set all observations
> equal to “United States”. Remember, you can use the mutate function
> for adding a variable. Make sure to save the result of this as dn
> again so that the stored data frame contains the new variable going
> forward.

``` r
dennysus <- dennys %>%
  mutate(country = "United States")
```

### Exercise 7

> Find the La Quinta locations that are outside the US, and figure out
> which country they are in. This might require some googling. Take
> notes, you will need to use this information in the next exercise.

- Canada, Mexico, China, New Zealand, Turkey, United Arab Emirates,
  Chile, Colombia, and Ecuador, Honduras

### Exercise 8

> Add a country variable to the La Quinta dataset. Use the case_when
> function to populate this variable. You’ll need to refer to your notes
> from Exercise 7 about which country the non-US locations are in. Here
> is some starter code to get you going:

``` r
laquinta %>%
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 14 × 6
    ##    address                                  city  state zip   longitude latitude
    ##    <chr>                                    <chr> <chr> <chr>     <dbl>    <dbl>
    ##  1 Carretera Panamericana Sur KM 12         "\nA… AG    20345    -102.     21.8 
    ##  2 Av. Tulum Mza. 14 S.M. 4 Lote 2          "\nC… QR    77500     -86.8    21.2 
    ##  3 Ejercito Nacional 8211                   "Col… CH    32528    -106.     31.7 
    ##  4 Blvd. Aeropuerto 4001                    "Par… NL    66600    -100.     25.8 
    ##  5 Carrera 38 # 26-13 Avenida las Palmas c… "\nM… ANT   0500…     -75.6     6.22
    ##  6 AV. PINO SUAREZ No. 1001                 "Col… NL    64000    -100.     25.7 
    ##  7 Av. Fidel Velazquez #3000 Col. Central   "\nM… NL    64190    -100.     25.7 
    ##  8 63 King Street East                      "\nO… ON    L1H1…     -78.9    43.9 
    ##  9 Calle Las Torres-1 Colonia Reforma       "\nP… VE    93210     -97.4    20.6 
    ## 10 Blvd. Audi N. 3 Ciudad Modelo            "\nS… PU    75010     -97.8    19.2 
    ## 11 Ave. Zeta del Cochero No 407             "Col… PU    72810     -98.2    19.0 
    ## 12 Av. Benito Juarez 1230 B (Carretera 57)… "\nS… SL    78399    -101.     22.1 
    ## 13 Blvd. Fuerza Armadas                     "con… FM    11101     -87.2    14.1 
    ## 14 8640 Alexandra Rd                        "\nR… BC    V6X1…    -123.     49.2

Mexico (AG, QR, CH, NL, VE, PU, SL), Columbia (ANT), Canada (ON, BC),
Honduras (FM)

``` r
laquintacountry <- laquinta %>% 
  mutate(country = case_when(
    state %in% state.abb ~ "United States",
    state %in% c("ON", "BC") ~ "Canada",
    state == "ANT" ~ "Colombia",
    state %in% c("AG", "QR", "CH", "NL", "VE", "PU", "SL") ~ "Mexico",
    state == "FM" ~ "Honduras"))
```

``` r
laquinta_us <- laquintacountry %>%
  filter(country == "United States")
```

### Exercise 9

> Which states have the most and fewest Denny’s locations? What about La
> Quinta? Is this surprising? Why or why not?

- most Dennys: California

- fewest Dennys: Deleware

- most La Quintas: Texas

- fewest La Quintas: Maine

Not surprised by results

``` r
dennys %>%
  count(state) %>%
  inner_join(states, by = c("state" = "abbreviation")) %>%  
  arrange(n)
```

    ## # A tibble: 51 × 4
    ##    state     n name                     area
    ##    <chr> <int> <chr>                   <dbl>
    ##  1 DE        1 Delaware               2489. 
    ##  2 DC        2 District of Columbia     68.3
    ##  3 VT        2 Vermont                9616. 
    ##  4 AK        3 Alaska               665384. 
    ##  5 IA        3 Iowa                  56273. 
    ##  6 NH        3 New Hampshire          9349. 
    ##  7 SD        3 South Dakota          77116. 
    ##  8 WV        3 West Virginia         24230. 
    ##  9 LA        4 Louisiana             52378. 
    ## 10 MT        4 Montana              147040. 
    ## # ℹ 41 more rows

``` r
laquinta_us %>% 
  count(state) %>% 
  arrange(n)
```

    ## # A tibble: 48 × 2
    ##    state     n
    ##    <chr> <int>
    ##  1 ME        1
    ##  2 AK        2
    ##  3 NH        2
    ##  4 RI        2
    ##  5 SD        2
    ##  6 VT        2
    ##  7 WV        3
    ##  8 WY        3
    ##  9 IA        4
    ## 10 MI        4
    ## # ℹ 38 more rows

### Exercise 10

> Which states have the most Denny’s locations per thousand square
> miles? What about La Quinta?

### Exercise 11

> Filter the data for observations in North Carolina only, and recreate
> the plot. You should also adjust the transparency of the points, by
> setting the alpha level, so that it’s easier to see the overplotted
> ones. Visually, does Mitch Hedberg’s joke appear to hold here?

### Exercise 12

> Now filter the data for observations in Texas only, and recreate the
> plot, with an appropriate alpha level. Visually, does Mitch Hedberg’s
> joke appear to hold here?

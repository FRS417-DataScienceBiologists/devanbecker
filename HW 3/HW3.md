---
title: "HW3"
author: "Devan Becker"
date: "2/7/2019"
output: 
  html_document: 
    keep_md: yes
---


```r
library(tidyverse)
```

```
## ── Attaching packages ──────────────────────────────────────────────────────────────────────────────── tidyverse 1.2.1 ──
```

```
## ✔ ggplot2 3.1.0     ✔ purrr   0.2.5
## ✔ tibble  2.0.0     ✔ dplyr   0.7.8
## ✔ tidyr   0.8.2     ✔ stringr 1.3.1
## ✔ readr   1.3.1     ✔ forcats 0.3.0
```

```
## ── Conflicts ─────────────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```


```r
fisheries <- readr::read_csv(file = "FAO_1950to2012_111914.csv")
```

```
## Warning: Duplicated column names deduplicated: 'Species (ISSCAAP group)'
## => 'Species (ISSCAAP group)_1' [4], 'Species (ASFIS species)' => 'Species
## (ASFIS species)_1' [5], 'Species (ASFIS species)' => 'Species (ASFIS
## species)_2' [6]
```

```
## Parsed with column specification:
## cols(
##   .default = col_character(),
##   `Species (ISSCAAP group)` = col_double(),
##   `Fishing area (FAO major fishing area)` = col_double()
## )
```

```
## See spec(...) for full column specifications.
```


```r
names(fisheries) = make.names(names(fisheries), unique = T)
names(fisheries)
```

```
##  [1] "Country..Country."                    
##  [2] "Species..ASFIS.species."              
##  [3] "Species..ISSCAAP.group."              
##  [4] "Species..ISSCAAP.group._1"            
##  [5] "Species..ASFIS.species._1"            
##  [6] "Species..ASFIS.species._2"            
##  [7] "Fishing.area..FAO.major.fishing.area."
##  [8] "Measure..Measure."                    
##  [9] "X1950"                                
## [10] "X1951"                                
## [11] "X1952"                                
## [12] "X1953"                                
## [13] "X1954"                                
## [14] "X1955"                                
## [15] "X1956"                                
## [16] "X1957"                                
## [17] "X1958"                                
## [18] "X1959"                                
## [19] "X1960"                                
## [20] "X1961"                                
## [21] "X1962"                                
## [22] "X1963"                                
## [23] "X1964"                                
## [24] "X1965"                                
## [25] "X1966"                                
## [26] "X1967"                                
## [27] "X1968"                                
## [28] "X1969"                                
## [29] "X1970"                                
## [30] "X1971"                                
## [31] "X1972"                                
## [32] "X1973"                                
## [33] "X1974"                                
## [34] "X1975"                                
## [35] "X1976"                                
## [36] "X1977"                                
## [37] "X1978"                                
## [38] "X1979"                                
## [39] "X1980"                                
## [40] "X1981"                                
## [41] "X1982"                                
## [42] "X1983"                                
## [43] "X1984"                                
## [44] "X1985"                                
## [45] "X1986"                                
## [46] "X1987"                                
## [47] "X1988"                                
## [48] "X1989"                                
## [49] "X1990"                                
## [50] "X1991"                                
## [51] "X1992"                                
## [52] "X1993"                                
## [53] "X1994"                                
## [54] "X1995"                                
## [55] "X1996"                                
## [56] "X1997"                                
## [57] "X1998"                                
## [58] "X1999"                                
## [59] "X2000"                                
## [60] "X2001"                                
## [61] "X2002"                                
## [62] "X2003"                                
## [63] "X2004"                                
## [64] "X2005"                                
## [65] "X2006"                                
## [66] "X2007"                                
## [67] "X2008"                                
## [68] "X2009"                                
## [69] "X2010"                                
## [70] "X2011"                                
## [71] "X2012"
```

```r
fisheries
```

```
## # A tibble: 17,692 x 71
##    Country..Countr… Species..ASFIS.… Species..ISSCAA… Species..ISSCAA…
##    <chr>            <chr>                       <dbl> <chr>           
##  1 Albania          Angelsharks, sa…               38 Sharks, rays, c…
##  2 Albania          Atlantic bonito                36 Tunas, bonitos,…
##  3 Albania          Barracudas nei                 37 Miscellaneous p…
##  4 Albania          Blue and red sh…               45 Shrimps, prawns 
##  5 Albania          Blue whiting(=P…               32 Cods, hakes, ha…
##  6 Albania          Bluefish                       37 Miscellaneous p…
##  7 Albania          Bogue                          33 Miscellaneous c…
##  8 Albania          Caramote prawn                 45 Shrimps, prawns 
##  9 Albania          Catsharks, nurs…               38 Sharks, rays, c…
## 10 Albania          Common cuttlefi…               57 Squids, cuttlef…
## # … with 17,682 more rows, and 67 more variables:
## #   Species..ASFIS.species._1 <chr>, Species..ASFIS.species._2 <chr>,
## #   Fishing.area..FAO.major.fishing.area. <dbl>, Measure..Measure. <chr>,
## #   X1950 <chr>, X1951 <chr>, X1952 <chr>, X1953 <chr>, X1954 <chr>,
## #   X1955 <chr>, X1956 <chr>, X1957 <chr>, X1958 <chr>, X1959 <chr>,
## #   X1960 <chr>, X1961 <chr>, X1962 <chr>, X1963 <chr>, X1964 <chr>,
## #   X1965 <chr>, X1966 <chr>, X1967 <chr>, X1968 <chr>, X1969 <chr>,
## #   X1970 <chr>, X1971 <chr>, X1972 <chr>, X1973 <chr>, X1974 <chr>,
## #   X1975 <chr>, X1976 <chr>, X1977 <chr>, X1978 <chr>, X1979 <chr>,
## #   X1980 <chr>, X1981 <chr>, X1982 <chr>, X1983 <chr>, X1984 <chr>,
## #   X1985 <chr>, X1986 <chr>, X1987 <chr>, X1988 <chr>, X1989 <chr>,
## #   X1990 <chr>, X1991 <chr>, X1992 <chr>, X1993 <chr>, X1994 <chr>,
## #   X1995 <chr>, X1996 <chr>, X1997 <chr>, X1998 <chr>, X1999 <chr>,
## #   X2000 <chr>, X2001 <chr>, X2002 <chr>, X2003 <chr>, X2004 <chr>,
## #   X2005 <chr>, X2006 <chr>, X2007 <chr>, X2008 <chr>, X2009 <chr>,
## #   X2010 <chr>, X2011 <chr>, X2012 <chr>
```


```r
fisheries <- fisheries %>% 
  rename(country = Country..Country.,
         commname = Species..ASFIS.species.,
         sciname = Species..ASFIS.species._2,
         spcode = Species..ASFIS.species._1,
         spgroup = Species..ISSCAAP.group., 
         spgroupname = Species..ISSCAAP.group._1, 
         region = Fishing.area..FAO.major.fishing.area., 
         unit = Measure..Measure.)
fisheries
```

```
## # A tibble: 17,692 x 71
##    country commname spgroup spgroupname spcode sciname region unit  X1950
##    <chr>   <chr>      <dbl> <chr>       <chr>  <chr>    <dbl> <chr> <chr>
##  1 Albania Angelsh…      38 Sharks, ra… 10903… Squati…     37 Quan… ...  
##  2 Albania Atlanti…      36 Tunas, bon… 17501… Sarda …     37 Quan… ...  
##  3 Albania Barracu…      37 Miscellane… 17710… Sphyra…     37 Quan… ...  
##  4 Albania Blue an…      45 Shrimps, p… 22802… Ariste…     37 Quan… ...  
##  5 Albania Blue wh…      32 Cods, hake… 14804… Microm…     37 Quan… ...  
##  6 Albania Bluefish      37 Miscellane… 17020… Pomato…     37 Quan… ...  
##  7 Albania Bogue         33 Miscellane… 17039… Boops …     37 Quan… ...  
##  8 Albania Caramot…      45 Shrimps, p… 22801… Penaeu…     37 Quan… ...  
##  9 Albania Catshar…      38 Sharks, ra… 10801… Scylio…     37 Quan… ...  
## 10 Albania Common …      57 Squids, cu… 32102… Sepia …     37 Quan… ...  
## # … with 17,682 more rows, and 62 more variables: X1951 <chr>,
## #   X1952 <chr>, X1953 <chr>, X1954 <chr>, X1955 <chr>, X1956 <chr>,
## #   X1957 <chr>, X1958 <chr>, X1959 <chr>, X1960 <chr>, X1961 <chr>,
## #   X1962 <chr>, X1963 <chr>, X1964 <chr>, X1965 <chr>, X1966 <chr>,
## #   X1967 <chr>, X1968 <chr>, X1969 <chr>, X1970 <chr>, X1971 <chr>,
## #   X1972 <chr>, X1973 <chr>, X1974 <chr>, X1975 <chr>, X1976 <chr>,
## #   X1977 <chr>, X1978 <chr>, X1979 <chr>, X1980 <chr>, X1981 <chr>,
## #   X1982 <chr>, X1983 <chr>, X1984 <chr>, X1985 <chr>, X1986 <chr>,
## #   X1987 <chr>, X1988 <chr>, X1989 <chr>, X1990 <chr>, X1991 <chr>,
## #   X1992 <chr>, X1993 <chr>, X1994 <chr>, X1995 <chr>, X1996 <chr>,
## #   X1997 <chr>, X1998 <chr>, X1999 <chr>, X2000 <chr>, X2001 <chr>,
## #   X2002 <chr>, X2003 <chr>, X2004 <chr>, X2005 <chr>, X2006 <chr>,
## #   X2007 <chr>, X2008 <chr>, X2009 <chr>, X2010 <chr>, X2011 <chr>,
## #   X2012 <chr>
```

```r
fisheries_tidy <- fisheries %>% 
  gather(num_range("X",1950:2012), key="year", value="catch")
```


```r
glimpse(fisheries_tidy)
```

```
## Observations: 1,114,596
## Variables: 10
## $ country     <chr> "Albania", "Albania", "Albania", "Albania", "Albania…
## $ commname    <chr> "Angelsharks, sand devils nei", "Atlantic bonito", "…
## $ spgroup     <dbl> 38, 36, 37, 45, 32, 37, 33, 45, 38, 57, 33, 57, 31, …
## $ spgroupname <chr> "Sharks, rays, chimaeras", "Tunas, bonitos, billfish…
## $ spcode      <chr> "10903XXXXX", "1750100101", "17710001XX", "228020310…
## $ sciname     <chr> "Squatinidae", "Sarda sarda", "Sphyraena spp", "Aris…
## $ region      <dbl> 37, 37, 37, 37, 37, 37, 37, 37, 37, 37, 37, 37, 37, …
## $ unit        <chr> "Quantity (tonnes)", "Quantity (tonnes)", "Quantity …
## $ year        <chr> "X1950", "X1950", "X1950", "X1950", "X1950", "X1950"…
## $ catch       <chr> "...", "...", "...", "...", "...", "...", "...", "..…
```


```r
fisheries_tidy <- fisheries_tidy %>% 
  mutate(year = as.numeric(str_replace(year, "X", "")), 
         catch = as.numeric(str_replace(catch, c("F", "...", "-"), replacement = "")))
```

```
## Warning in evalq(as.numeric(str_replace(catch, c("F", "...", "-"),
## replacement = "")), : NAs introduced by coercion
```


```r
fisheries_tidy
```

```
## # A tibble: 1,114,596 x 10
##    country commname spgroup spgroupname spcode sciname region unit   year
##    <chr>   <chr>      <dbl> <chr>       <chr>  <chr>    <dbl> <chr> <dbl>
##  1 Albania Angelsh…      38 Sharks, ra… 10903… Squati…     37 Quan…  1950
##  2 Albania Atlanti…      36 Tunas, bon… 17501… Sarda …     37 Quan…  1950
##  3 Albania Barracu…      37 Miscellane… 17710… Sphyra…     37 Quan…  1950
##  4 Albania Blue an…      45 Shrimps, p… 22802… Ariste…     37 Quan…  1950
##  5 Albania Blue wh…      32 Cods, hake… 14804… Microm…     37 Quan…  1950
##  6 Albania Bluefish      37 Miscellane… 17020… Pomato…     37 Quan…  1950
##  7 Albania Bogue         33 Miscellane… 17039… Boops …     37 Quan…  1950
##  8 Albania Caramot…      45 Shrimps, p… 22801… Penaeu…     37 Quan…  1950
##  9 Albania Catshar…      38 Sharks, ra… 10801… Scylio…     37 Quan…  1950
## 10 Albania Common …      57 Squids, cu… 32102… Sepia …     37 Quan…  1950
## # … with 1,114,586 more rows, and 1 more variable: catch <dbl>
```


```r
fisheries_tidy %>% 
  select(country, spgroupname, year, catch) %>% 
  filter(year==2012, spgroupname=="Squids, cuttlefishes, octopuses") %>% 
  arrange(desc(catch))
```

```
## # A tibble: 745 x 4
##    country                  spgroupname                      year  catch
##    <chr>                    <chr>                           <dbl>  <dbl>
##  1 China                    Squids, cuttlefishes, octopuses  2012 434845
##  2 China                    Squids, cuttlefishes, octopuses  2012 261000
##  3 Korea, Republic of       Squids, cuttlefishes, octopuses  2012 181408
##  4 Japan                    Squids, cuttlefishes, octopuses  2012 169055
##  5 China                    Squids, cuttlefishes, octopuses  2012 127126
##  6 Indonesia                Squids, cuttlefishes, octopuses  2012 116991
##  7 United States of America Squids, cuttlefishes, octopuses  2012  97036
##  8 Argentina                Squids, cuttlefishes, octopuses  2012  94984
##  9 India                    Squids, cuttlefishes, octopuses  2012  82456
## 10 China                    Squids, cuttlefishes, octopuses  2012  78000
## # … with 735 more rows
```

```r
cuttlefish <- 
  fisheries_tidy %>% 
  select(country, commname, sciname, year, catch) %>% 
  filter(year==2012, commname=="Common cuttlefish") %>%
  arrange(desc(catch))
cuttlefish
```

```
## # A tibble: 21 x 5
##    country commname          sciname            year catch
##    <chr>   <chr>             <chr>             <dbl> <dbl>
##  1 France  Common cuttlefish Sepia officinalis  2012 13217
##  2 Tunisia Common cuttlefish Sepia officinalis  2012  7717
##  3 Spain   Common cuttlefish Sepia officinalis  2012  1685
##  4 Turkey  Common cuttlefish Sepia officinalis  2012  1396
##  5 Belgium Common cuttlefish Sepia officinalis  2012   836
##  6 Croatia Common cuttlefish Sepia officinalis  2012   169
##  7 Albania Common cuttlefish Sepia officinalis  2012   125
##  8 France  Common cuttlefish Sepia officinalis  2012    94
##  9 Cyprus  Common cuttlefish Sepia officinalis  2012    24
## 10 Malta   Common cuttlefish Sepia officinalis  2012    24
## # … with 11 more rows
```



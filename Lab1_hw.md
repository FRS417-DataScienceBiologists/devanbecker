---
title: "Lab1_hw"
output: 
  html_document: 
    keep_md: yes
---


```r
library("tidyverse")
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
getwd()
```

```
## [1] "/Users/devanbecker/Desktop/FRS417"
```


```r
5 - 3 * 2
```

```
## [1] -1
```


```r
8 / 2 ** 2
```

```
## [1] 2
```


```r
(5-3)*2
```

```
## [1] 4
```


```r
(8/2)*2*2
```

```
## [1] 16
```


```r
blackjack <- c(140, -20, 70, -120, 240)
roulette <- c(60, 50, 120, -300, 10)
days <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
```


```r
names(blackjack) <- days
names(roulette) <- days
```


```r
total_blackjack <- sum(blackjack)
total_blackjack
```

```
## [1] 310
```

```r
total_roulette <- sum(roulette)
total_roulette
```

```
## [1] -60
```


```r
total_week <- c(blackjack+roulette)
total_week
```

```
##    Monday   Tuesday Wednesday  Thursday    Friday 
##       200        30       190      -420       250
```


```r
if(total_week > 0) {print("play blackjack")}
```

```
## Warning in if (total_week > 0) {: the condition has length > 1 and only the
## first element will be used
```

```
## [1] "play blackjack"
```

```r
if(total_week < 0) {print("play roulette")}
```

```
## Warning in if (total_week < 0) {: the condition has length > 1 and only the
## first element will be used
```





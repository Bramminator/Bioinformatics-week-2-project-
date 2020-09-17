R Notebook for beetle data
================

  - [The data set](#the-data-set)
      - [The source of the dataset](#the-source-of-the-dataset)
      - [Flour beetle](#flour-beetle)
  - [Variables](#variables)

This is an [R Markdown](http://rmarkdown.rstudio.com) Notebook. When you
execute code within the notebook, the results appear beneath the code.

# The data set

This data set illustrates the acute mortality of flour beetles
(Tribolium confusum) following 5 hour exposure to carbon disulfide gas.

### The source of the dataset

Burnham, K. P., Anderson, D. R. (2002) Model Selection and Multimodel
Inference: a practical information-theoretic approach. Second edition.
Springer: New York.

Young, L. J., Young, J. H. (1998) Statistical Ecology. Kluwer Academic
Publishers: London.

## Flour beetle

![Flour Beetle](Graphics/Red-flour-beetle.jpg)

Source:
<https://plunketts.net/pest-identification/other-pests/red-flour-beetles-confused-flour-beetles>

# Variables

We have chosen to use the following naming convention: lower case words
seperated by dots in the case of variables, and first word lowercase and
any additional words in upper case for functions. An example of a
variable structured via this naming convention might be weight.kg, and
an example of a properly named function would be computeAverage.

``` r
beetle.data <- read.csv("Data/beetle.csv")
str(beetle.data)
```

    ## 'data.frame':    8 obs. of  4 variables:
    ##  $ dose.mg       : num  49.1 53 56.9 60.8 64.8 ...
    ##  $ number.tested : int  49 60 62 56 63 59 62 60
    ##  $ number.killed : int  6 13 18 28 52 53 61 60
    ##  $ mortality.rate: num  0.122 0.217 0.29 0.5 0.825 ...

``` r
library(ggplot2)
library(tidyverse)
```

    ## -- Attaching packages ------------------------------------------- tidyverse 1.3.0 --

    ## v tibble  3.0.3     v dplyr   1.0.2
    ## v tidyr   1.1.2     v stringr 1.4.0
    ## v readr   1.3.1     v forcats 0.5.0
    ## v purrr   0.3.4

    ## -- Conflicts ---------------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
beetle.data %>%
  ggplot(aes(x = dose.mg, y = mortality.rate)) +
    geom_point() +
    geom_smooth(method = 'lm')
```

    ## `geom_smooth()` using formula 'y ~ x'

![](README_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

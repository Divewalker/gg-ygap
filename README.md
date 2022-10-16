
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ggygap

<!-- badges: start -->
<!-- badges: end -->

ggygap allows to easily add a gap in y-the axis of ggplots.

## Installation

You can install the development version of ggygap like so:

``` r
# FILL THIS IN! HOW CAN PEOPLE INSTALL YOUR DEV PACKAGE?
```

## Example

1.  First create and edit your graph like you would normally do and
    assign it to a variable.
2.  Use gg.y_gap() to add your gap in the y axis. gg.y_gap() returns
    your plot; simply assign it to a variable and you can continue
    refining it.

``` r
library(ggplot2)
library(scales)
library(ggygap)
# Example Data
set.seed(1)
x <- rep(0:9, 2)
y <- rnorm(20, mean=100, sd=5)
z <- c(rep("a", 10), rep("b", 10))
i <- rep(c("c", "d"), 10)
dat <- data.frame(x, y, z, i)
dat$i <- factor(dat$i)
# 1. Create Plot
p <- ggplot(dat, aes(x=x, y=y, color=z, group=z)) +
  geom_point() +
  geom_line() 
p
```

<img src="man/figures/README-example-1.png" width="100%" />

``` r
# 2. Add Gap (Continuous x Example)
gg.y_gap(p, y_segment_start = 85, y_segment_end = 110, break_step = 5)
```

<img src="man/figures/README-example-2.png" width="100%" />

``` r

# 2. Add Gap (Categorical x Example + additional params)
p1 <- ggplot(dat, aes(x=i, y=y, fill=z, group=z)) +
  geom_bar(stat="identity", position="dodge")
p
```

<img src="man/figures/README-example-3.png" width="100%" />

``` r
gg.y_gap(p1, y_segment_start = 85, y_segment_end = 110, break_step = 5,
         gap_lines = "r", gap_line_length = 0.05, gap_width = 0.03) +
  theme(
    panel.background = element_blank(),
    axis.line = element_line(colour = "black")
  )
```

<img src="man/figures/README-example-4.png" width="100%" />
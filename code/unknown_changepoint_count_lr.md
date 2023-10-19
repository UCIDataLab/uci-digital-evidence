Sample Code for Likelihood Ratios for Categorical Event Data with an Unknown Changepoint
================

## LR under the proposed model

Recall that the formula for the likelihood ratio under the proposed
model is

<p align="center">
<img src="unknown_changepoint_formula.png" width="500">
</p>

where $B(.)$ denotes the multivariate beta function. The multivariate
beta function is defined as

<p align="center">
<img src="mv_beta.png" width="250">
</p>

## Functions for computing the LR

`calc_ln_mv_beta` calculates the natural log transformed multivariate
beta function for a given set of inputs.

``` r
# Calculate ln(multivariate beta function)
# rho: vector of inputs to the multivariate beta function
#
calc_ln_mv_beta <- function(rho) {
  sum(lgamma(rho)) - lgamma(sum(rho))
}
```

`get_lnlr_from_seq` calculates natural log transformed likelihood ratios
for a given set of prior parameters and sequence of events.

``` r
# Calculate the ln(LR) for a given sequence of events
#
# event_seq: vector containing a sequence of events
# cp_window_start: the start of the window of possible times for the changepoint
# cp_window_end: the end of the window of possible times for the changepoint
# categories: vector of length K specifying the LR categories
#   - if not specified, defaults to the event types in event_seq
#   - note that if specified, events in event_seq not in these categories will 
#     be ignored
# alpha: vector of length K containing the Dirichlet prior parameters
#   - if not specified, defaults to uniform Dirichlet
# p_z: vector specifying the distribution on the location of the changepoint
#   - if not specified, defaults to discrete uniform
#
get_lnlr_from_seq <- function(event_seq,
                              cp_window_start,
                              cp_window_end,
                              categories = NA,
                              alpha = NA,
                              p_z = NA) {
  
  # treat event sequence as categorical
  if (sum(is.na(categories)) == 0){
    # with specified categories, others treated as NA
    event_seq <- factor(event_seq, levels = categories)
    
  } else {
    # categories inferred from unique values in sequence
    event_seq <- factor(event_seq)
  }
  
  # ignore empty events
  event_seq <- event_seq[!is.na(event_seq)]
  
  # get number of categories
  K <- length(levels(event_seq))
  # get number of events
  N <- length(event_seq)
  # get possible changepoints
  cps <- cp_window_start:cp_window_end
  n_cp <- length(cps)
  
  # error check inputs
  if (sum(is.na(alpha)) == 0) {
    
    if (length(alpha) != K) {
      stop("The number of prior parameters is not equal to the number of categories.")
    }
    
    if (sum(alpha <= 0) > 0) {
      stop("All prior parameters need to be greater than 0.")
    }
    
  } else {
    alpha <- rep(1, K)
  }
  
  if (cp_window_start > cp_window_end) {stop("Incompatible window start/end indices.")}
  if (cp_window_start < 2) {stop("Window start must be at least 2.")}
  if (cp_window_end > N - 1) {stop("Window end must be before last event index.")}
  
  if (sum(is.na(p_z)) == 0) {
    
    if (length(p_z) != n_cp) {
      stop("Changepoint distribution is incompatible with time window.")
    }
    
    if (sum(p_z > 0) != n_cp) {
      stop("All values in the changepoint distribution must be larger than 0.")
    }
    
    if (sum(p_z <= 1) != n_cp) {
      stop("All values in the changepoint distribution be less than or equal to 1.")
    }
    
  } else {
    p_z <- rep(1/n_cp, n_cp)
  }
  
  # calculate numerator
  x <- as.vector(table(event_seq))
  ln_num <- calc_ln_mv_beta(alpha + x) + calc_ln_mv_beta(alpha)
  
  # calculate denominator
  ln_den_vals <- rep(NA, n_cp)
  
  for (i in 1:n_cp) {
    x1 <- table(event_seq[1:cps[i]])
    x2 <- table(event_seq[(cps[i] + 1):length(event_seq)])
    ln_den_vals[i] <- calc_ln_mv_beta(alpha + x1) + 
      calc_ln_mv_beta(alpha + x2) +
      log(p_z[i])
  }
  
  ln_den <- matrixStats::logSumExp(ln_den_vals)
  
  # calculate ln(LR)
  ln_num - ln_den
  
}
```

## Toy examples

``` r
set.seed(NULL)
set.seed(5678)
```

Let’s consider three event types of interest, “A”, “B”, and “C”.

``` r
toy_categories <- c("A", "B", "C")
```

Suppose we compose a sequence with the same distribution of events
throughout and then calculate the likelihood ratio.

``` r
event_seq <- toy_categories[sample(seq(3), size = 30, prob = c(0.8, 0.1, 0.1), replace = T)]
exp(get_lnlr_from_seq(event_seq, 
                      cp_window_start = 10, 
                      cp_window_end = 20, 
                      categories = toy_categories))
```

    ## [1] 9.655598

If generate more data, there is more evidence with which to calculate
our likelihood ratio, so we see more extreme values.

``` r
event_seq <- toy_categories[sample(seq(3), size = 300, prob = c(0.8, 0.1, 0.1), replace = T)]
exp(get_lnlr_from_seq(event_seq, 
                      cp_window_start = 125, 
                      cp_window_end = 175,
                      categories = toy_categories))
```

    ## [1] 33.66436

We can also generate dual source data which comes from two
distributions, i.e., there is a changepoint in the middle of the events.

``` r
event_seq <- c(toy_categories[sample(seq(3), size = 15, prob = c(0.8, 0.1, 0.1), replace = T)],
               toy_categories[sample(seq(3), size = 15, prob = c(0.4, 0.1, 0.5), replace = T)])
exp(get_lnlr_from_seq(event_seq, 
                      cp_window_start = 10, 
                      cp_window_end = 20,
                      categories = toy_categories))
```

    ## [1] 0.1097021

And now when we have more data, we get a smaller value of the likelihood
ratio.

``` r
event_seq <- c(toy_categories[sample(seq(3), size = 50, prob = c(0.8, 0.1, 0.1), replace = T)],
               toy_categories[sample(seq(3), size = 50, prob = c(0.4, 0.1, 0.5), replace = T)])
exp(get_lnlr_from_seq(event_seq, 
                      cp_window_start = 30, 
                      cp_window_end = 75,
                      categories = toy_categories))
```

    ## [1] 0.0001065497

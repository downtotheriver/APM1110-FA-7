APM1110 - FA 7 - Dacanay
================
Jordan Dacanay

### 1) In Example 16.3 with 𝜆 = 4 per minute, use R to obtain:

### (a) P(T ≤ 0.25) = P(time between submissions is at most 15 seconds);

#### Let us define the rate parameter as e1_lambda

``` r
e1_lambda <- 4
```

``` r
p_025 <- pexp(0.25, rate = e1_lambda)
p_025_rounded <- round(p_025, 4)
```

#### ANSWER

``` r
print(paste0("The probability that the time between submissions is at most 15 seconds is ", p_025_rounded, " or ", p_025_rounded * 100, "%."))
```

    ## [1] "The probability that the time between submissions is at most 15 seconds is 0.6321 or 63.21%."

### (b) P(T \> 0.5) = P(time between submissions is greater than 30 seconds)

``` r
p_05 <- 1 - pexp(0.5, rate = e1_lambda)
p_05_rounded <- round(p_05, 4)
```

#### ANSWER

``` r
print(paste0("The probability that the time between submissions is greater than 30 seconds is ", p_05_rounded, " or ", p_05_rounded * 100, "%."))
```

    ## [1] "The probability that the time between submissions is greater than 30 seconds is 0.1353 or 13.53%."

### (c) P(0.25 \< T \< 1) = P(time between submissions is between 15 seconds and 1 minute)

#### To get the probability that the time between submissions is between 15 seconds (0.25 minutes) and 60 seconds (1 minute), we can use the difference between the cumulative distribution function (CDF) values at these two points.

``` r
# Calculate P(T <= 1)
p_1 <- pexp(1, rate = e1_lambda)
# Calculate P(T <= 0.25)
p_025 <- pexp(0.25, rate = e1_lambda)

# Calculate the difference
p_025_1 <- p_1 - p_025

p_025_1_rounded <- round(p_025_1, 4)
```

#### ANSWER

``` r
print(paste0("The probability that the time between submissions is between 15 seconds and 60 seconds is ", p_025_1_rounded, " or ", p_025_1_rounded * 100, "%."))
```

    ## [1] "The probability that the time between submissions is between 15 seconds and 60 seconds is 0.3496 or 34.96%."

### 3) The average rate of job submissions in a computer center is 2 per minute. If it can be assumed that the number of submissions per minute has a Poisson distribution, calculate the probability that:

### (a) more than two jobs will arrive in a minute

#### Let us define the rate parameter as e3_lambda

``` r
e3_lambda <- 2
```

#### To get the probability that more than two jobs will arrive in a minute when the average rate is 2 per minute, we can use the complementary approach (assuming a Poisson distribution).

``` r
p_2j <- 1 - ppois(2, lambda = e3_lambda)
p_2j_rounded <- round(p_2j, 4)
```

#### ASNWER

``` r
print(paste0("The probability that more than two jobs will arrive in a minute is ", p_2j_rounded, " or ", p_2j_rounded * 100, "%."))
```

    ## [1] "The probability that more than two jobs will arrive in a minute is 0.3233 or 32.33%."

### (b) at least 30 seconds will elapse between any two jobs

``` r
p_least_30s <- exp(-e3_lambda * 0.5)
p_least_30s_rounded <- round(p_least_30s, 4)
```

#### ANSWER

``` r
print(paste0("The probability that at least 30 seconds will elapse between any two jobs is ", p_least_30s_rounded, " or ", p_least_30s_rounded * 100, "%."))
```

    ## [1] "The probability that at least 30 seconds will elapse between any two jobs is 0.3679 or 36.79%."

### (c) less than 30 seconds will elapse between jobs

``` r
p_less_30_s<- 1 - exp(-e3_lambda * 0.5)
p_less_30_s_rounded <- round(p_less_30_s, 4)
```

#### ANsWER

``` r
print(paste0("The probability that less than 30 seconds will elapse between jobs is ", p_less_30_s_rounded, " or ", p_less_30_s_rounded * 100, "%."))
```

    ## [1] "The probability that less than 30 seconds will elapse between jobs is 0.6321 or 63.21%."

### (d) a job will arrive in the next 30 seconds, if no jobs have arrived in the last 30 seconds

``` r
p_next_30s <- pexp(0.5, rate = e3_lambda)
p_next_30s_rounded <- round(p_next_30s, 4)
```

#### ANSWER

``` r
print(paste0("The probability that a job will arrive in the next 30 seconds, if no jobs have arrived in the last 30 seconds is ", p_next_30s_rounded, " or ", p_next_30s_rounded * 100, "%."))
```

    ## [1] "The probability that a job will arrive in the next 30 seconds, if no jobs have arrived in the last 30 seconds is 0.6321 or 63.21%."

### 7) A website receives an average of 15 visits per hour, which arrive following a Poisson distribution.

### (a) Calculate the probability that at least 10 minutes will elapse without a visit.

#### Let us define the rate of visits per hour as per_hour_lambda and and the visits per minute as per_minute_lambda

``` r
per_hour_lambda <- 15
per_minute_lambda <- per_hour_lambda/60
```

#### To get the probability, we can use the properties of the exponential distribution since the time between visits in a Poisson process follows an exponential distribution.

``` r
time_interval <- 10
p_least_10m <- exp(-per_minute_lambda * time_interval)

p_least_10m_rounded <- round(p_least_10m, 4)
```

#### ASNWER

``` r
print(paste0("The probability that at least 10 minutes will elapse without a visit is ", p_least_10m_rounded, " or ", p_least_10m_rounded * 100, "%."))
```

    ## [1] "The probability that at least 10 minutes will elapse without a visit is 0.0821 or 8.21%."

### (b) What is the probability that in any hour, there will be less than eight visits?

``` r
p_less_8v <- ppois(7, lambda = per_hour_lambda)
p_less_8v_rounded <- round(p_less_8v, 4)
```

#### ANSWER

``` r
print(paste0("The probability that in any hour, there will be less than eight visits is ", p_less_8v_rounded, " or ", p_less_8v_rounded * 100, "%."))
```

    ## [1] "The probability that in any hour, there will be less than eight visits is 0.018 or 1.8%."

### (c) Suppose that 15 minutes have elapsed since the last visit, what is the probability that a visit will occur in the next 15 minutes.

``` r
t_interval <- 15
p_next_15m <- pexp(t_interval, rate = per_minute_lambda)

p_next_15m_rounded <- round(p_next_15m, 4)
```

#### ANSWER

``` r
print(paste0("The probability that a visit will occur in the next 15 minutes, given that 15 minutes have elapsed since the last visit, is ", p_next_15m_rounded, " or ", p_next_15m_rounded * 100, "%."))
```

    ## [1] "The probability that a visit will occur in the next 15 minutes, given that 15 minutes have elapsed since the last visit, is 0.9765 or 97.65%."

### (d) Calculate the top quartile, and explain what it means

``` r
top_quartile <- qexp(0.75, rate = per_minute_lambda)
top_quartile_rounded <- round(top_quartile, 2)
```

#### ANSWER

``` r
print(paste0("The top quartile is ", top_quartile_rounded, ". This means that 75% of the time, a visit will occur within approximately ", top_quartile_rounded ," minutes or less since the last visit."))
```

    ## [1] "The top quartile is 5.55. This means that 75% of the time, a visit will occur within approximately 5.55 minutes or less since the last visit."

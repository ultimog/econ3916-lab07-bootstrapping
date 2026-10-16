# econ3916-lab07-bootstrapping
Lab 07 submission
# Estimation & Bootstrapping — Quantifying Uncertainty Without a Formula

## Objective
I measured how uncertain different estimates are, using formulas where they exist and the bootstrap where they don't, on the UCI Adult Census Income data.

## Methodology
- I loaded the UCI Adult Census Income data (32,561 respondents).
- I separated the standard deviation of the data from the standard error of an estimate, and checked the s/sqrt(n) relationship across four sample sizes.
- I built parametric confidence intervals from the CLT and showed that the CLT converges quickly for age and slowly for capital gains.
- I ran the bootstrap by hand, then with scipy.stats.bootstrap.
- I compared percentile and BCa intervals on a heavily skewed variable.
- I bootstrapped a two-sample difference in mean weekly hours.
- I asked an AI to write a bootstrap-interval function, revised my prompt once, and checked the function against my own intervals.
- I ran a coverage simulation on lognormal data at n=50 to check whether nominal 95% intervals actually cover 95% of the time.

## Key Findings
- I found a degenerate case: the bootstrap SE of the median of 32,561 whole-number ages is exactly 0.0000. Every resample returns the same median, because with that many ties the median is pinned. The bootstrap is reporting a real property of the data, not failing.
- For the mean, the nominal 95% parametric interval covered 92.5% and the percentile bootstrap 91.5%. The gap is inside the Monte Carlo standard error of about 1.3 points, so the two methods are indistinguishable here, and both under-cover slightly.
- For the median, the mean-centred parametric interval covered only about 66.8%, while the bootstrap held near its nominal level.
- The bootstrap is most useful for statistics that have no usable standard-error formula, like the median.

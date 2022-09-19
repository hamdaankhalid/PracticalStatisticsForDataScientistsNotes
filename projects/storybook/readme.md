# Storybook

- A cpp based library that lets you do non visual exploratory data analysis on a given csv file with non categorical variables.

## Features
Given a dataset give a summary of the following:
- Location Estimates
  - Mean/AVG (Sum of vals divided by number of vals).
  - Median/50th percentile (The value such that one half od the data lies below it)
  - Percentile/Quantile (The value such that P percent of the data lies below it)
  - Trimmed Mean/Truncated mean (Mean after dropping a fixed number of extreme values)
  
- Variability
  - Deviations/errors/residuals: The difference between observed values and the estimate of location.
  - Variance/mean-squared-error: Sum of squared deviations from the mean divided by n - 1 where n is the number of data values.
  - Standard Deviation: Square root of variance.
  - Mean Absolute Deviation/L1 Norm/Manhattan Norm: Mean of absolute values of the deviations from the mean.
  - Range: Difference between largest and smallest value in a dataset.
  - Order Statistics / Rank: Metrics based on the data values sorted from largest ti smallest.
  - Percentile: Percentile/Quantile (The value such that P percent of the data lies below it).
  - Interquartile Range/IQR: Difference between 75th percentile and 25th percentile.

- Correlation
  - Pearson's correlation coefficient amongst the numerical columns.

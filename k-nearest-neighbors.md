# K Nearest Neighbors:

## Algorithm:
For each record to be classified or predicted:
1. Find "K" records that have similar featuers (i.e. similar predictor values).
2. For classification, find out the what majority class is among those similar records, and assign that class to the new record.
3. For prediction also called (KNN Regression), find the average among those similar records, and predict that average for the new record.

## Terms:
- Neighbor: A record that has similar predictor values to another record
- Distance metrics: Measures that sum up in a single number how far one record is from another.
- Standardization: Subtract the mean and divide bu the standard deviation.
- Z-score: The value that results after standardization.
- K: The number of neighbors considered in the nearest enighbor calculation.

## Distance Metrics:
Similarity (nearness) between two records is calculated using the distance metric. The most popular distance metric between two vectors is Euclidean distance of the two vectors (where each vector is a record). Another common distance metric for numeric data is Manhattan distance. ***Note: Euclidean Distance == Crows distance vs Manhattan distance is like travelling along rectangular city blocks***.
Manhattan distance is useful approx if similarity is defined as point to point travel time. In order to prevent larger variables/features from domintating the measurement, we stadardixe the data.

## One Hot Encoding:
Transforming the representation of categorical data into numerical dummy variables.

## Standardization/Normalization:
In Measurement we are often not so much interested in "how much" but in "how different from the average". Standardiazation puts all the variabls on similar scales by subtracting the mean and dividing by the standard deviation. This ensures that a variable fors not overly influence a model simply due to the scale of its original measurement. The result of this standardization is ofen known as z-score. Measurements are then states in terms of "standard deviations aaway from the mean".

## Choosing K
- If the K is too low we may be overfitting, if the K is too high we may oversmooth the data and miss out on KNN's ability to capture the local structure in the data, one of its main advantages.
- The K that best balances between overfitting and oversmoothing is typically determined by the accuracy metrics, and in particular, accuracy with holdout or validation data. Typically values of K generally fall in range of 1-20. Often, an odd number is chosen to avoid ties.

## KNN as a Feature Engine
- KNN performance by itself is not competetive with more sophisticated classification techniques. In practical model fitting, however, KNN can be used to add "local knowledge" in a staged process with other classification techniques:
  1. KNN is run on the data, and for each record, a classification (or quasi-probability of a class) is derived.
  2. That result is added as a new feature to the record, and anotehr classificatoin method is then run on the data. The original predictor variables are thus used twice.
   - This technique does not cause issues with multicollinearity (you may think we have duplicated our data, and used predictors twice). Since the information being incorporated into the second stage model is highly local, derived only from a few nearby records, and is therefore additional information and not redundant.

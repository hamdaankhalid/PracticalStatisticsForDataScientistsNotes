# Classification

- Classifiaciton problems., a form of supervised learning in which we first train a model on data where the outcome is known and then apply the model on data where the outcome is not known.

## Bayesian Classifications
- Naive Bayes uses the probability of obseving the predictor values, given an outcome, to estimate what is really of interest: the probability of observing outcome Y = i, given a set of predictor values.

### Complete/Exact Bayes Classification:
- Algorithm for each record to be classified.
1. Find all the other records with the same predictor profiles (i.e. where the predictor values are the same).
2. Determine what classes those records belong to and which class is most prevalent (i.e. probable).
3. Assign that class to the new record.
- This approach amounts to find all the records in the sample that are exactly like the new record to be classified in the sense that all predictors values are exactly like the new record to be classified in the sense that all th predictor values are identical.
- This is an impractical approach to real world problems because in a real dataset many of the records will be without exact matches

### The Naive Solution
- Algorithm for each record's probability to be of classification. P (Y = i | X1....Xp)
1. For a binary response Y = i (i = 0 || i = 1, estimate the individual conditional probabilities for each predictor P(Xj | Y = i); these are the probabilities that the predictor value is in the record when we observe Y = i. This probability is estimated by the proportion of Xj values among the Y = i records in the training set.
2. Multiply these probabilities by each other, and then the proportion of records belonging to Y = i.
3. Repeat steps 1 and 2 for all classes.
4. Estimate the probability outcodome i by taking the value calculated by step 2 for class i and dividing it by the sum of such values for all classes.
5. Assign the record to the class with the highest probability for this set of predictor variables.
- Naive because we assume each predictor is independent of other.
- Naive Bayes is known to produce biased estimates. However twhere the goal is to rank records according to probabilities Y = 1, unbiased estimates of probability are not needed, and naive bayes produces good result.

**Bayesian classification on works for categorical variables. Numerical variables must be converted to categorical variables by bin and convert or using a probability model to estimate the conditional probability.**

## Linear Discriminant Analysis Classification
- Earliest statistical classifier.

### Prereq 
-  Covariance Matrix: The covariance measures the relationship between two variables x and z. Denote the mean for each variable by Xbar and Zbar. The covariance Sx,z between x and z is given by:
  ```Sx,z = Summation(i=1 to n)[(Xi -  Xbar)(Zi = Zbar)] / (n - 1)```
- As with correlation coefficient positive values indiciate a poistive relationship and negative values indicate a negative relationship. Correlation, however is constrained to be between -1 and 1, whereas covariance scale depends on the scale of the variables x and z. The covariance matrix Summation for x and z consists of the individual variable variances s^2x and s^2z on the diagonal and the covariance variable pairs on the off diagnoals.

#### LDA
- For simplicity imagine a classification problem in which we want to predict a binary outcome y using two continunous numeric variables (x, z). Technically, discriminant analysis assumes the predictor variables are normally distributed continuous variables, but, in practice, the method works well even for non-extreme departures from normality, and for binary predictors.
-  Fisher's linear discriminant distinguishes variation between groups on the one hand, from variation within groups on the other. Specifically, seeking to divide the records into two groups, linear discriminant analysis focuses on maximizing the "between" sum of squares (measuring variation between 2 groups) relative to the the "within" sum of squares (variation with group). In this case, the two groups correspond to the records (x0, z0) for which y = 0 and the records (x1, z1) for which y = 1. The method finds the linear combination ```wx*x + wz*z``` that maximizes the sum of square ratio: ```SSbetween / SSwithin```
- The between sum of squares is the squared distance between the two group means, and the within sum of squares is the spread around the means within each group, weighted by the covariance matrix, Intuitively by maximizing the between sum of squares and minimizing the within  sum of squares, this method yields the greatest separation between the two groups.

## Logistic Regression
# TODO
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
# TODO
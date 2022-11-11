# Classification

- Classifiaciton problems., a form of supervised learning in which we first train a model on data where the outcome is known and then apply the model on data where the outcome is not known.

## Naive Bayes
- Naive Bayes uses the probability of obseving the predictor values, given an outcome, to estimate what is really of interest: the probability of observing outcome Y = i, given a set of predictor values.

### Complete/Exact Bayes Classification:
- Algorithm for each record to be classified.
1. Find all the other records with the same predictor profiles (i.e. where the predictor values are the same).
2. Determine what classes those records belong to and which class is most prevalent (i.e. probable).
3. Assign that class to the new record.
- This approach amounts to find all the records in the sample that are exactly like the new record to be classified in the sense that all predictors values are exactly like the new record to be classified in the sense that all th predictor values are identical.
- This is an impractical approach to real world problems because in a real dataset many of the records will be without exact matches

## The Naive Solution

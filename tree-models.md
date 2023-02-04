# Tree Models
- Synonyms: Classification and Regression Trees, decision trees, or just trees.
- Set of "if-then-else" riles that are easy to understand to implement. In contrast to linear regression, trees have the ability to discover hidden patterns corresponding to complex interactions in the data. However, unlike KNN or Naive bayes, simple tree models can be expressed in terms of predictor relationships that are easily interpretable.

## Recursive Partitioning Algorithm
- The data is repeatedly partitioned using predictor values that do the best job of separating the data into relatively homogeneous partitions.
- Suppose we hvae a response variable Y and a set of P predictor variables Xj for j = 1,..,P. For a partition A of records, recursive partitionnig will find the best way to partition A into two subpartitions.
  
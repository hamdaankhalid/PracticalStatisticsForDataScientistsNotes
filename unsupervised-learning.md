# Unsupervised Learning

- Statistical methods that extract meanning from data without training a model on labeled data. 
- Unsupervised learning can be used to create predictive rule in absence of a labled respone. The goal may be to reduce the dimension of the data to a more manageable set of variables. This reduced set can then be used as an input into a predictve model, such as regression or classification. unsupervided learning can also be viewed as an extension of the exploratary data analysis. The aim is to gain insight into a set of data and how the different variables relate to each other.
-  Unsupervised techniques allow you to sift through and analyze these variables and discover relationships.

## Principal Component Analysis
- Technique to discover the way in which numeric variables covary (some of the variation in one variable is duplicated in another variable).
- PCA idea is to combine multiple numeric predictor variables into a smaller set of variables, which are weighted linear combinations of the original set. The smaller set explains the variability of the full set of variables, the principal components. The weights reveal the contributions of the original variables to the new principal components.
- Scree Plots give you a visual on the importance of variables. We will have N principal components if we have n predictor variables.
[https://www.youtube.com/watch?v=FgakZw6K1QQ](https://www.youtube.com/watch?v=FgakZw6K1QQ)

## K-Means Clustering
- Clustering is a technique to divide data into different groups, where the records in each group are similar to one another. The goal is to identify signinficant and meaningful groups of data. K-mean was the first clustering method developed.

### Terminology:
- Cluster: A group of records that are similar.
- Cluster mean: The vecto of variable means for the records in a cluster.
- K: The nu,ber of clusters.

- K means divides the data into K clusters by minimizing the sum of squared distances of each record to the mean of its assigned cluster.This is referred to as the within-cluster sum fof squares of within-cluster SS.
- Imbalanced cluster can result from distant outliers, or from groups of records very distinct from the rest of the data-both may warrant further inspection.

### Selecting the number of clusters (K)
- In the absence of a cluster number dictated by practical or managerial considerations a statistical approach like "elbow method" can be taken.
- Elbow method -> Graph Y axis %variance explained, and X axis (number of clusters). The elbow is the point where the cumulative variance explained falttens out after rising steeply.

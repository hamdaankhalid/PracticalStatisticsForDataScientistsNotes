# Tree Models
- Synonyms: Classification and Regression Trees, decision trees, or just trees.
- Set of "if-then-else" riles that are easy to understand to implement. In contrast to linear regression, trees have the ability to discover hidden patterns corresponding to complex interactions in the data. However, unlike KNN or Naive bayes, simple tree models can be expressed in terms of predictor relationships that are easily interpretable.

## Recursive Partitioning Algorithm
- The data is repeatedly partitioned using predictor values that do the best job of separating the data into relatively homogeneous partitions.
- Suppose we have a response variable Y and a set of P predictor variables Xj for j = 1,..,P. For a partition A of records, recursive partitionnig will find the best way to partition A into two subpartitions.
1. For each predictor variabel Xj:
    a. For each value sj of Xj:
      i. Split the records in A wiht Xj values < sj as one partitino, amd the remaining records where Xj >= sj as another partition.
      ii. Measure the homogenity of classes within each partition of A.
    b. Select the value of sj that produces maximum within-partition homogenity of class.
2. Select the variable Xj and split value sj that produces maximum within partition homogenity of class.
***Now comes the recursive part***
1. Initialize A with the entire data set.
2. Apply the parititoning algorithm to split A into two subparittionsm A1 and A2.
3. Repeat step 2 on subparititons A1 and A2.
4. The algorithm terminates when no further partition can be made that sufficiently improves the homogenity of the partitions.

The end result is a paritioning of the data in P-dimensions, with each partition predicting an outcome of 0 or 1 depending on the majority vote of the response in that partition.

## Measuring Homogeneity or Impurity
Let p be the proportion of misclassified records within a partition.
- Gini impurity: Gini impurtiy for a set of records A = I(A) = p(1-p)
- Entropy of information: Entropy measure for a set of records A = I(A) = -plogb2(p) - (1-p)logb2(1-p)

## Stopping the Tree from Growing:
As the tree grows bigger, the splitting rules become more detailed, and the tree gradaully shifts from identifying "big" rules that identify real and reliable relationships in the data to "tiny" rules that reflect only noise. A fully grown tree results in completely pure leaves and, hence, 100% accuracy in classifying the data that it is trained on. This accuracy is false, since we have basically completely overfit our model to the noise, and we will not have good performance when crossvalidating or testing our model.
The following ways an be used to avoid this situation:
1. Avoid splitting the paritions if a resulting subpartition is too small, or if a terminal leaf is too small.
2. Don't split a partition if the new partition does not "significantly" reduce the impurity.
- These methods can feel somewhat arbitrary, but we can't determine optimum values without cross validation by changing model parameters, or by modifying the tree through pruning.

## Predicting a Continuous Value:
Predicting a continuous value (also termed regression) with a tree follows the same logic and procedure, except impurity within a subpartition is measure by squared deviations from the mean (squared errors), and predictive performance is measured using the square root of the mean squared error (RMSE) in each partition.

## Appeal for using tree models
Many predictive models provide a black box nature, tree models are not like that.
1. The tree models provide a visual tool for exploring the data, to gain an idea of what variables are important and how they relate to one another. Trees can capture nonlienar relationship among predictor variables.
2. Tree models provide a set of rules that can be effectively communicated to non-specialists, either for implementation or to "sell" a data mining project.

When it comes to prediction, however, harnessign the results from multiple trees is typically more powerful than using just a single tree.

## Bagging and the Random Forest
Principle is that averaging (or taking majority votes) of multiple models - an ensemble of models - turns out to  be more accurate than just selecting one model. The simplest version of ensembles is as follows:
1. Develop a predictive model and record the prediction for a given data set.
2. Repeat for multiple models with the same data
3. For each record to be predicted, take an average (or a weighted average, or a majority vote) of the predictions.

Bagging and boosting are two main variants of ensemble models.

## Bagging (Bootstrap Aggregating)
- Suppose we have a response Y and P predictor variables X = X1,...Xp with N records. Bagging the basic algorithm for ensembles, except that, instead of fitting various models to the same data, each new model is fitted to a bootstrap resample of the dataset.

## Random Forest
- The random forest is based on applying bagging to decision trees, with one important extenstion: in addition to sampling the records, the algorithm also samples the variables. In traditional decision trees, to determine how to create a subpartition of a partition A, the algorithm makes the choice of variable and split point by minimizing a criterion such as gini impurity. With random forests, at each stage of the algorithm, the choice of variable is limited to a random subset of variables. Compared to the basic tree algorithm , the random forest algorithm adds two more steps: the bagging discussed earlier and the bootstrap sampling variables at each split.
- How many variables to sample at each step? A rule of thumb is to choose square root p where p is the number of predictor variables.
- The random forest method is a "black box" method. It produces more accurate predictions than a simple tree, but the simple tree's intuitive decision rules are lost. The random forest predictions are also somewhat noisy. This is a result of unusual records in the data and demonstrates the danger of overfitting by the random forest.
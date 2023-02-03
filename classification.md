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

### Linear Discriminant Analysis
- For simplicity imagine a classification problem in which we want to predict a binary outcome y using two continunous numeric variables (x, z). Technically, discriminant analysis assumes the predictor variables are normally distributed continuous variables, but, in practice, the method works well even for non-extreme departures from normality, and for binary predictors.
-  Fisher's linear discriminant distinguishes variation between groups on the one hand, from variation within groups on the other. Specifically, seeking to divide the records into two groups, linear discriminant analysis focuses on maximizing the "between" sum of squares (measuring variation between 2 groups) relative to the the "within" sum of squares (variation with group). In this case, the two groups correspond to the records (x0, z0) for which y = 0 and the records (x1, z1) for which y = 1. The method finds the linear combination ```wx*x + wz*z``` that maximizes the sum of square ratio: ```SSbetween / SSwithin```
- The between sum of squares is the squared distance between the two group means, and the within sum of squares is the spread around the means within each group, weighted by the covariance matrix, Intuitively by maximizing the between sum of squares and minimizing the within  sum of squares, this method yields the greatest separation between the two groups.
- ***Intuition**: LDA creates a new axis -> like a line in a 2d graph, and then projects the data on the line such that it maximizes the separation of the two categories. The new axis created according to two criteria. The first criteria is that once the data is projected on the axis we want to maximize the distance between means of the categories. The second criteria is to minimize the variation (scatter) within each category.


## Logistic Regression
- Logistic regression is analogous to multiple linear regression except the outcome is binary. Like LDA, and unlike K-Nearest neighbor and Naive Bayes, logistic regression is a structured model approach rather than data centric approach. Due to its fast computational speed and its output of a model that lends itseld to rapid scoring of new data, it is a popular method.

### Logistic Response Function and Logit
The key ingredients for logistic regression are the logistic response function and the logit, in which we map a probability (which is on a 0-1 scale) to a more expansive scale suitable for linear modeling.
The first step is to think of the outcome variable not as a binary label but as the probability "p" that the label is a "1". Naively, we might be tempted to model p as a linear function of the predictor variables. 
```
p = B0 + B1*x1 + B2*x2 +... + Bq*xq
```

- However, fitting this model does not ensure that p will end up between 0 and 1, as a probability must. Instead, we model p by applying a logistic response or inverse logit function to the predictors.
```
 p = 1 / ( 1 + e^-(B0 + B1*x1 +...+Bq*xq) )
```
this transform ensures that the p stays betweeen 0 and 1.

We the use a special function called logodds function or logit fuction to map from probability p to -> -inf to +inf. By applying a cutoff we can now map to a binary outcome. The response in the logistic regression formula is the log odds of a binary outcome of the result being "1". We observe only the binary outcode, not the log odds, so special methods are needed to fit the equation.


- Logistic Regression is calculated using the Maximum Likelihood Estimation (MLE) method, which estimates the parameters of the logistic regression model that maximize the likelihood of observing the sample data. The logistic regression model involves using an equation of the form:

logit(p) = β0 + β1X1 + β2X2 + ... + βkXk

where logit(p) is the log-odds of the binary outcome, p is the probability of the binary outcome, β0, β1, ..., βk are the coefficients or parameters of the model that represent the relationship between each independent variable (X1, X2, ..., Xk) and the binary outcome, and X1, X2, ..., Xk are the values of the independent variables.

To calculate the logistic regression model, the software will iteratively adjust the values of the coefficients until the maximum likelihood is achieved, that is, until the predicted probabilities for the binary outcome are as close as possible to the observed outcomes in the sample data.

Once the coefficients have been estimated, the logistic regression equation can be used to predict the binary outcome for new data by plugging in the values of the independent variables and calculating the predicted probability of the binary outcome. The predicted probability can then be thresholded to make binary predictions (e.g., if the predicted probability is greater than 0.5, the prediction is 1, otherwise it is 0).

### Evaluating Classification Models
- Confusion Matrix: This is a table that summarizes the number of true positive, true negative, false positive, and false negative predictions made by the model. The ratios of these numbers can be used to calculate various metrics such as accuracy, precision, recall, and F1-score.
- Accuracy = True positives + true negaitves / total

- Rare class problems: In many cases there is an imbalance in the classes to be predicted, with one class much more prevalent thatn other. E.g. legit insurance claims versus fraudulent ones, or browsers versus purchasers at a website. The rare class is usually the class of more interest and is typically designated 2, in contrast to more prevalent 0s. In the typical scenario, the 1s are the more important case, in the sense that miclassifying them as 0s is costlier than misclassifying 0s as 1s. For example, correctly identifying a fraudulent insurance claim may save thousands of dollars. On the other hand, correctly identifying a non fraudulent claim merely saves you the cost and effort of going through the claim bu hand with a more careful review (which is what you would do if the claim is tagged as fraudulent).

```
Precision = sum of true positives/(sum of true positives + sum of false positives)
```

```
Recall or sensitivity = sum of true positives / sum of true positives + sum of false negatives
```

```
Speciicity = sum of true negatives/sum of true negatives + sum of false positives
```

- ROC Curve: You can see that there is a tradeoff betweeen recall and specificity. Capturing more 1s generally means misclassifying more 0s than 1s. The ideal classifier would do an excellent job classifying the 1s, without misclassifying more 0s as 1s.
The metric that captures this trade off is the "Receiver Operating Characteristics" curve, usually referre to as the ROC curve. The ROC curve plots recall(sensitivity) on the y-axis against specificity on the x-axis. The ROC curve shows the tradeoff between recall and specificity as you change the cutoff to determine how to classify a record.

- AUC: The Area Under Curve Metric is simply the total area under the ROC curve. The larger the value of AUC, the more effective the clasifier. An AUC of 1 indicates a perfect classifier. A completely ineffective classifier - The diagonal line - will have an AUC of 0.5.

- Using the AUC metric to evaluate a  model is an improvement over simple accuracy, as it can assess how well a classifier handles the tradeoff between overall accuracy and the need to identify the more important 1s. But it does not completely address the rare case proble, where you need to lower the model's probability cutoff below 0.5 to avoid having all records classified as 1s, it might be sufficient to have a probability of 0.4, 0.4, or lower.

- Lift: Lift is a metric used to evaluate the performance of a classification model, especially in marketing and customer relationship management (CRM) applications. It measures the ratio of the positive responses generated by the model to the positive responses that would have been generated if the model were not used. In other words, it measures the amount by which the model "lifts" the response rate above the response rate that would be achieved by simply using a random or naive approach.

Lift is typically calculated by dividing the cumulative gains obtained by the model by the cumulative gains that would have been obtained by a random or naive approach. The cumulative gains are the sum of the positive responses over the total number of instances, and the lift is expressed as a ratio or as a percentage.

For example, if the model's cumulative gain is 1.5 and the cumulative gain of the random or naive approach is 1, then the lift of the model is 1.5. This means that the model is generating 50% more positive responses than the random or naive approach.

Lift is an important metric because it helps to determine the effectiveness of a model in real-world applications. It provides a way to compare the performance of the model to a baseline and to determine the amount by which the model is improving the response rate. Additionally, lift can be used to determine the optimal cutoff for the predicted probabilities, and to identify the most profitable segment of the population for targeted marketing efforts.

### Strategies For Imbalanced Data
- Undersample: Use fewer of prevalevnt class records in the classification model.
- Oversample: Use more of the rare class records in the classification model, bootstrapping if necessary.
- Upweight or down weight: Attach more or less weight to the rare class in the model.
- Data Generation: Like bootstrapping, except each new bootstrapped record is slightly different from its source.
- Cost Based Classification: In practice, accuracy and AUC are a poor man's way to choose a classification rule. Often, an estimated cost can be assigned to false positives versus false negatives, and it is more appropriate to incorporate these costs to determine the best cutoff when classifying 1s and 0s. For example, suppose the expected cost of a default of a new loan is C and the expected return from a paid-off loan is R. Then the expected return for that loan is:
```
expected return = P(Y = 0)*R + P(Y=1)*C
```
Instead of simply labeling a loan as default or paid off, or determining the probability of default, it makes more sense to determine if the load has a positive expected return. Predicted probability of default is an intermediate step, and it must be combined with the loan's total value to determine the expected profit, which is the ultimate planning metric of business.


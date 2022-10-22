# Regression and Prediction

### Simple Linear Regression
- Model of the relationship between the magnitude of one variable and that of a second.
- Correlation is another way to measure how two variables are related. Correlation measures the strength of an association between two variables.
- Regression quatinfies the nature of the relationship.

### Key terms:
- Response: The variable we are trying to predict.
- Independent Variables: The variable used to predict the response.
- Record: The vector of predictor and outcome values for a specific indvidual or case.
- Intercept: The intercept of the regression line-that is, the predicted value when X=0.
- Regression Coefficient: The slope of the regression line.
- Fitted values: The estimates ÿ obtained from the regression line.
- Residuals: The difference between the observes values and the fitted values.
- Least squares: The method of fitting  regression by minimizing the sum of squared residuals.

### The Regression Equation:
Simple linear regression estimates how much Y changes when X changes by a certain amount. We try to represent it as a linear relationship. Y = b0 + b1*X. b1 is our regression coefficient and b0 is our intercept. In machine learning Y is often called the target and X is called a feature vector.

### Fitted Values and Residuals
- Fitted Values: Predictions
- Residuals: Prediction errors.
- In general the the data doesn't fall exactly on a line so the regression equation should include an explicit error term ei:
    Yi = b0 + b1*Xi + ei
- Fitted values aka predicted values, are typically denoted by y-hat ÿ: 
    Ÿi = (b0-hat)i + (b1-hat)i*Xi
- b0-hat and and b1-hat indicate the coefficients are estimates versus known.
- Residuals ê = Yi - Ÿi

### Least Squares
- Regression line is the estimate that minimizes sum of squared residuals values, also called the residual sum of squares or RSS:
- RSS = Summation(i = 1 to n)(Yi - Ÿi)^2 = Summation(i = 1 to n)(Yi - (b0-hat)i + (b1-hat)i*Xi)^2
- b0-hat and b1-hat minimize RSS
- The method of minimizing RSS is termed least squares regression, or ordinary least squares regression.

By itself the regression does not prove the direction of causation. Conclusions about causation must come from a broader understanding about the relationship. Example: A regression equation might show a definite relaationship between number of clicks on a web ad and number of conversions. It is our knowledge of the marketing process and not the regression equation that, that leads us to that conclusion that click on ad lead to sales and not vice versa.

### Multiple Linear Regression
When there are multiple predictors we extend simple linear regression equation to accomodate them:
```Y = b0 + b1*X1 + b2*X2 +...+bn*Xn (where X1 to Xn are n predictors for target variable Y)```
Instead of a line we now have a linear model.

### Assessing a Linear Regression Model
- Root mean squared error (RMSE) is one of the most important performance metrics. 
  ```RMSE = Square Root ( summation 1 to n((yi - ÿi)^2) / n)```
  RMSE measures the overall accuracy of the model and is basis for comparing it to other models.
- Residual Standard Error (RSE) is similar to RMSE except it is adjusted with degrees of freedom
  ```RSE = Square Root ( summation 1 to n((yi - ÿi)^2) / (n - p - 1) )```
  The difference b/w RSE and RMSE is usually very small.
- R-squared statistic or Coefficient of determination is a value that ranges from 0 to 1 and measures the proportion of variation on the data that is accounted for in the model. It is useful mainly in explanatory uses of regression where you want to assess how well the model fits the data.
  ```R^2 = 1 -  ( summation 1 to n((yi - ÿi)^2) /  summation 1 to n((yi - mean of y)^2) )```
An "adjusted r-squared" adjusts for degrees of freedom, effectively penalizing the addition of more predictors to a model. It is rarely different r-squared.
- Every predictor may also carry with a t-statistic and a p-value which measures to the extent to which a coefficent is statistically significant. Higher the t-statistic the more significant the predictor.

### Cross-validation
- All the above metrics are called "in-sample" metrics-they are applied to the same data that was used to fit the model. Normally we use majority of the data to train the model and set aside a smaller portion to test the trained model. This is how we get to "out-of-sample" metrics. Using a holdout sample leaves you subject to some uncertainity that arises simply from variability in the smalll holdout sample. 
- Cross-Validation extends the idea of a holdout sample to mulitple sequential holdout samples. The algorithm for basic k-fold Cross-Validation is as follows.
    1. Set aside 1/k of the data as a holdout sample
    2. Train the model on remaining data
    3. Apply (score) the model to the 1/K of the holdout, and record needed model asessment metrics.
    4. Restore the first 1/k of the data, and set aside the next 1/k (excluding any records that got picked the first time).
    5. Repeat the steps 2 and 3.
    6. Repeat until each record has been used in the holdout portion.
    7. Average or otherwise combine the model assessment metric.
The division of the data into the training sample and the holdout sample is also called a fold.

### Model Selection and Stepwise Regression
- Adding more variables, however, does not necessarily mean we have a better model. Statisticians use the principle of Occam's razor to guide the choice of a model: all things being equal, a simple model should be used in preference to a more complicated model.
- Including additional variables always reduces the RMSE and increases R^2 for the training data. Hence, these are not appropriate to help guide the model choice. One approach to including model complexity is to use the adjusted R^2:
    ```R^2(adjusted) = 1 - (1 - R^2) * (n-1)/(n-P-1) where n is the number of records, and P is the number of variables in the model.```
    ```Akaike's Information Criteria (AIC) = 2P + nlog(RSS/n) where RSS is residual sum of squares.```
- AIC penalizes adding terms to a  model.

### How do we find a model that minimizes AIC or Adjusted R^2
- One way is to search through all possible models. This is called "all subset regression". This is computationally expensive and is not feasible for problems with large data and many variables.
- An alternative is the "stepwise regression". It could start with a full model and successively drop variables that don't contribute meaningfully. This is called "backward elimination". Altr=ernatively you could start with a constant model and add variables (forward selection). As a third option you could also successively add and drop predictors to find a model that lowers AIC or adjusted R^2. 
- In forward selection we add predictors one by one, at each step the predictor that has the largest contribution to R^2 is added, and stopping when the contribution is no longer statistically significant. With backwards you invert the process.
- Penalized regression: Instead of searching through a discrete set of models,the model fitting equation incorporates a constraint that penalizes the model for too many variables(predictors or parameters). Rather than completely removing or adding variable like forward selction or backward elimination penalized regression reduces the coefficients (penalizes) for the variable. Ridge and lasso regressions are common penalized regression methods.
- The above are all in-sample methods (no holdout). So it is possible they may not apply as well to new data. One common approach is to use cross validation to validate the models.

### Weighted Regression
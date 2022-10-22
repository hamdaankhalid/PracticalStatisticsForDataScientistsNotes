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
  
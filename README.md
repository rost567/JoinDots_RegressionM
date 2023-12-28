# Unlocking the Dynamics of Online Article Sharing: A Multivariate Regression Exploration"
This proyect is mainly predicting a future response given historical data.  
**GOAL**  
We are trying to predict the "shares" variable, it has a very wide distribution.  
By conducting a multivariate regression analysis, this analysis seeks to provide insights into the factors that contribute significantly to the variation in the number of shares an article receives. This can help content creators, marketers, or publishers understand what aspects of an article are associated with higher or lower levels of engagement.
So to understand and predict the number of shares for online articles. This is achieved through a multivariate regression analysis that considers various features or independent variables associated with each article. The project aims to uncover insights into the factors influencing the popularity of online articles and to develop a predictive model that can effectively estimate the number of shares based on these features. The analysis may also involve evaluating the performance of the regression model and exploring the relationships between the dependent variable ('shares') and multiple independent variables. 

**INTRODUCTION**
1. What is the likelihood that a customer will buy a second product from your website if they bought their first more than 6 months ago?
2. Trend line is a common feature of many business analyses.
3. How much do purchases increase when ads are shown more often on a homepage?
<br>

These sort of questions can be answered by drawing a line, **termed Regression**, representing the average change in our response as we vary the input **based in historical data and using this to extrapolate the response for future data**.<br>
That means where we only know the input but no the output yet.
<br>
Calculating the regression based on: 
- the hypothesis that our observations are scatterred around the true relationship between the 2 variables.
- And on average future observations will regress (approach) the trend line between input and output.
<br>

**Complexitites in the analysis:**   
1. The relationship we fit usually involve not one, but several inputs. So two dimensional line is not an option, instead, to represent the multi-variate relationship, we need more advanced methos to calculate the line trend in a hight-dimensional space.  
2. The line trend could be a line, a curve, a wave, or even complex patterns. 
3. SOmetimes we need to decide which variables we are going to use, which ones are relevant for the problem at hand.
4. Determine carefully not just the trend that best fits the data we have, but also, generalizes best to new data.


**MODEL FITTING AND EVALUATION**
From data to decissions - The goal of modelling can be either:  
First scenario: To predict a future response given historical data.
Second scenario: Infer the statistical significance and effect of a given variable on an outcome.

a) The first scenario, we will choose a subset of data to train our model, --- and then evaluate the goodness of fit of the linear model on an independent data set not used to derive the model parameters --- we want to validate that the trends represented by the model generalise beyond a particular set of data points. (queremos validar que las tendencias representadas por el modelo generalizan más allá de un conjunto concreto de puntos de datos) --- While the coefficient output of the linear model are interpretable, we are still more concerned in this scenario about whether we can accurately predict future responses rather than the meaning of the coefficients.

Let's continue under the first assumption, that is we are trying to predict future data.  
To obtain **test** and **validation data**, we will split the response and predictor data into 60% training and 40% test splits.
According to the distribution of the columns these have maximum values in the hundreds, thousands, cero and one.
And even the value we are trying to predict, shares, has a very wide distribution.

**RESULTS**
In this example, it seems reasonable to assume that the residuals of the model we fit for popularity as a function of new item characteristics are independent. In other cases, we might make multiple observations on the same set of entries (as when a given customer appears more than once in a dataset), and these data might be correlated over time (as when records for the same customer are more likely to be correlated when they appear closer together in time). Both situations violate the assumptions of independence between the residuals of a model. In the following sections we will present three methods to deal with these cases.

According to the OLS regression results.
- R-squared: The R-squared value is 0.123, indicating that approximately 12.3% of the variance in the dependent variable (shares) is explained by the independent variables in the model.

- Adjusted R-squared: The adjusted R-squared, which takes into account the number of predictors in the model, is 0.121.

- F-statistic: The F-statistic is 98.80, and the associated p-value (Prob (F-statistic)) is very close to zero (0.00). This suggests that the overall model is statistically significant.

- Coefficients: The table provides coefficients for each independent variable along with standard errors, t-values, and p-values. The coefficients represent the estimated effect of each variable on the dependent variable (shares). The p-values (P>|t|) indicate whether each coefficient is significantly different from zero.

- Intercept: The intercept is 2.1756, representing the estimated value of the dependent variable when all independent variables are zero.

- Variable significance: Some variables have p-values less than 0.05 (e.g., timedelta, n_tokens_title, n_tokens_content), suggesting that they are statistically significant predictors of the dependent variable.

- Multicollinearity warning: The notes section mentions the possibility of strong multicollinearity problems or a singular design matrix. This issue may affect the reliability of individual coefficient estimates.

- Omnibus, Durbin-Watson, Jarque-Bera, Skew, Kurtosis: These are diagnostic statistics to assess the regression model's assumptions and properties. For example, Jarque-Bera tests the normality of the residuals, and the Durbin-Watson statistic checks for autocorrelation in the residuals.

- Number of Observations and Variables: The model is based on 39,644 observations with 56 variables.

**TO SUM IT UP ACCORDING TO THE GOAL**
"We are trying to predict the 'shares' variable, it has a very wide distribution"
- Model Fit Considerations: The wide distribution of the 'shares' variable may indicate heteroscedasticity, where the variance of the errors is not constant across all levels of the independent variables. This can impact the efficiency and reliability of the regression estimates.

- Outliers and Skewness: The wide distribution could be indicative of outliers or a skewed distribution of the 'shares' variable. Outliers can disproportionately influence the regression model, and skewed distributions may violate the assumption of normality in the residuals.

- Transformation Possibilities: Depending on the nature of the distribution, it might be beneficial to explore data transformations (e.g., logarithmic or power transformations) to stabilize variance or address skewness.

- Model Interpretation: In the presence of a wide distribution, interpreting the coefficients becomes more nuanced. The effect of an independent variable may vary across different levels of the 'shares' variable, and the linear model may not capture these nuances adequately.

- Consideration of Model Assumptions: The assumptions of linear regression, such as homoscedasticity, normality of residuals, and linearity, should be carefully assessed. Residual analysis and diagnostic tests can provide insights into the model's performance.

- Potential Influential Observations: The wide distribution might indicate the presence of influential observations that disproportionately affect the model. Investigating influential data points and their impact on the results is crucial.

- Predictive Challenges: Predicting a variable with a wide distribution may pose challenges, as the model needs to account for the variability in the outcome variable. This emphasizes the importance of model evaluation metrics and the need for alternative modeling approaches if linear regression proves insufficient.


This is based in the curiosity of how to join dots or clustering with Regression Models, it is a first version, currently working on it. Taking notes based on the book  "Python: Advanced Predictive Analytics" by Ashish Kumar, Joseph Babcock.

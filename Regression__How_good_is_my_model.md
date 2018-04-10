<!--
Marco Amato

-->
# Regression: How good is my model?
___
 By Marco. 
 Thanks to [@ranaq](https://github.com/ranaq) for her precious feedback
___


* P-value (indicates which features are useful)
* RMSD  (How is my model performing)
* Does it overfit training data? (Is RMSD valid for all the data I will use?
* Z-Statistic / T-Statistic / F-Statistic


#### P-value
The regression model provides a P-value for every prediction. This value gives us information about how useful the feature is (check out the 'Null Hypothesis' video for a better understanding)

* the null hypothesis is rejected when p < .05
* the null hypothesis is not rejected when p > .05. 

**Intuition:** When *p-value* > 0.5 for a feature, check if the feature makes sense 

[video](https://www.khanacademy.org/math/statistics-probability/significance-tests-one-sample/more-significance-testing-videos/v/hypothesis-testing-and-p-values)

**Note** Sklearn does not implement p-value, however statsmodels does (code example 1)

#### Root mean square deviation :

<!--$$ r = \sum_{\substack{n}} P(y -  \hat{y}\ \ ) $$
**Intuition:** Sums all errors but don't consider the sign; better to use mean squared error 

$$ MSE = r^2 = \sum_{\substack{n}} P(y -  \hat{y}\ \ )^2 $$

**Intuition:** 0 is a perfect prediction
-->
$$ RMSD = \sqrt{\sum_{\substack{n}} P(y -  \hat{y}\ \ )^2} $$

$$ \hat{y}\ = predicted\ value \ \ \ \ \ \ \ \ \   y = target\ value $$ 


**Intuition:** 0 is a perfect prediction
[video](https://www.khanacademy.org/math/ap-statistics/bivariate-data-ap/assessing-fit-least-squares-regression/v/residual-plots)


To dig deeper into these concepts check out these links:
[video](https://www.khanacademy.org/math/ap-statistics/bivariate-data-ap/assessing-fit-least-squares-regression/v/standard-deviation-of-residuals-or-root-mean-square-error-rmsd)
[wikipedia](https://en.wikipedia.org/wiki/Mean_squared_errorsquares-regression/v/standard-deviation-of-residuals-or-root-mean-square-error-rmsd)

#### Is my model overfit to my training data?
Why: If the model performs well on training data but poorly on new data (test data) I have probably overfit the model to the training data.

* Use more data to train
* Kfold and Crossvalidation

#### Z-Statistic / T-Statistic
[TK-Work in progress]
* T-Statistic if I have less than 30 values
* Z-Statistic if I have more than 30 values

__________
Code examples

[Statsmodels Website](http://www.statsmodels.org/dev/examples/notebooks/generated/ols.html)

```python
import pandas as pd
from sklearn import datasets
import statsmodels.api as sm

diabetes = datasets.load_diabetes()
X = diabetes.data
y = diabetes.target

X2 = sm.add_constant(X)
est = sm.OLS(y, X2)
est2 = est.fit()
print(est2.summary())
```

Result will look like:

```python
                           OLS Regression Results                            
==============================================================================
Dep. Variable:                      y   R-squared:                       0.518
Model:                            OLS   Adj. R-squared:                  0.507
Method:                 Least Squares   F-statistic:                     46.27
Date:                Wed, 28 Mar 2018   Prob (F-statistic):           3.83e-62
Time:                        14:05:31   Log-Likelihood:                -2386.0
No. Observations:                 442   AIC:                             4794.
Df Residuals:                     431   BIC:                             4839.
Df Model:                          10                                         
Covariance Type:            nonrobust                                         
==============================================================================
                 coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------
const        152.1335      2.576     59.061      0.000     147.071     157.196
x1           -10.0122     59.749     -0.168      0.867    -127.448     107.424
x2          -239.8191     61.222     -3.917      0.000    -360.151    -119.488
x3           519.8398     66.534      7.813      0.000     389.069     650.610
x4           324.3904     65.422      4.958      0.000     195.805     452.976
x5          -792.1842    416.684     -1.901      0.058   -1611.169      26.801
x6           476.7458    339.035      1.406      0.160    -189.621    1143.113
x7           101.0446    212.533      0.475      0.635    -316.685     518.774
x8           177.0642    161.476      1.097      0.273    -140.313     494.442
x9           751.2793    171.902      4.370      0.000     413.409    1089.150
x10           67.6254     65.984      1.025      0.306     -62.065     197.316
==============================================================================
Omnibus:                        1.506   Durbin-Watson:                   2.029
Prob(Omnibus):                  0.471   Jarque-Bera (JB):                1.404
Skew:                           0.017   Prob(JB):                        0.496
Kurtosis:                       2.726   Cond. No.                         227.
==============================================================================

Warnings:
[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
```

##### Regression code example

```python
from sklearn import metrics  
metrics.mean_squared_error(y, model.predict(X))
```
<!--

The probability of get a results away from the standard deviation

For dig deep in this concept check there links:
[video](https://www.khanacademy.org/math/statistics-probability/significance-tests-one-sample/more-significance-testing-videos/v/z-statistics-vs-t-statistics)

standard deviation = standardeviantion / sqr sample

X - mean /stanadard deviation


### Error Type I and Type II

A Type I error ( false positive )
When we preditc 
A Type II error, also called a false negative, is when we reject a hypothesis that is actually true; that is, we attribute an effect to chance when it was actually real.






- Introduction to Type I and Type II errors

- EDA
- Check for coorelation
- Scale


Reference:
http://scikit-learn.org/stable/modules/classes.html#sklearn-metrics-metrics



#### Classification metrics :

##### Binary classification

<div style="float:left;">
<img src="Precisionrecall.png" width="80%" />
</div>ciao


https://en.wikipedia.org/wiki/F1_score

-->

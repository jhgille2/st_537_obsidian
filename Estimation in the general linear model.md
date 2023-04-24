[[General_Linear_model.pdf|Lecture notes]]

## Previous steps
![[Introduction notes#Objectives| The overall goals for modeling longitudinal data]]

## Estimation of parameters
Specifying the model is just the first, albeit importat, step. Once the models for the fixed and random components of the total model have been decided on, we nees some technique for estimating the values of the parameters. 

#### Maximum likelihood - Regression parameters
Maximum likelihood estimation involves finding the parameters of the model that make the data most likely to have occurred. [[General_Linear_model.pdf#page=3|It involves some fancy math]]. This estimator $\hat{\beta}$, is an unbiased estimator of $\beta$, even if the covariance structure is not specified correctly. As long as the error distribution is MVN, the sampling distribution of $\hat{\beta}$ will be MVN as well.

#### REML - Variance components
Estimation of the variance components through pure maximum likelihood produces biased estimated of the parameters so restricted maximum likelihood (REML) is used instead. [[General_Linear_model.pdf#page=4|This also involves some fancy math]].

### Estimation and extraction of parameters in R
In R, (and in the nlme package), the correlation argument to the [gls](https://www.rdocumentation.org/packages/nlme/versions/3.1-162/topics/gls) function specifies what correlation structure you want to use. [There are many of these available for use](https://www.rdocumentation.org/packages/nlme/versions/3.1-162/topics/corClasses). The weights argument tot he function specifies the within unit variance structure. By default, the same variance for all units is assumed. 

Once fit, [[General_Linear_model.pdf#page=11|other functions can be used to extract components, and other summary information from the model]]. 

Different variances for each time point can also be fit with the *weights* argument to the gls function. In the results, the estimates of the variance for each time point are then given relative to the variance of the first time point through [[General_Linear_model.pdf#page=14|inflation factors]].

### Robust estimation of $\hat{\beta}$
If the covariance model is not correct (it often isn't), then the standard errors on the regression parameters ($\hat{\beta}$) will be incorrest as well, along with anything that uses the standard errors in their calculation. [[General_Linear_model.pdf#page=18|Again, this uses some fancy math]]. This is important because these standard errors are required for doing things like contrasts or computing confidence intervals or hypothesis testing.

## Inference

### Confidence intervals
The parameters $\hat\beta$ of the model are approximately $N(\beta, \hat{V})$ where $\hat V$ is the correlation matrix of $\beta$. The confidence interbals can then be constructed with [[General_Linear_model.pdf#page=20|a rather long formula]] that is very similar to that used in normal linear regression with come caveats placed on the degrees of freedom that relate to the number of parameters in the mean formula of the model.  See an example of the calculation [[General_Linear_model.pdf#page=21|here]].

### Hypothesis testing
Testing that $\hat \beta$ is equal to some value is [[General_Linear_model.pdf#page=22|also very similar]] to normal linear regression, again under the assumptions that $\hat \beta \sim N(\beta, \hat{V})$.  

For simultaneously testing more than one parameter in this way, a [[General_Linear_model.pdf#page=23|wald or an F-test]] is used.

### Information criteria
Informal information criteria techniques are used to compare models that are not nested. This is especially useful for comparing models that have different correlation or variance structures.  The two main information criteria metrics are AIC and BIC and [[General_Linear_model.pdf#page=25| and they are calculated like this]]. When comparing a sequence of models, the one with the lowest AIC or BIC is considered to be "best".

### Small sample size considerations
If there are not many observations, special tests have to be used to get accurate results. One popular approach is the [[General_Linear_model.pdf#page=26|Kenward-Roger approximation]].
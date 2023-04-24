[[Models_for_mean_and_covariance.pdf|Lecture handout]]

From the [[Introduction notes#Objectives|goals of longtidunial analysis]] we know that at a most basic level, we want to characterize the population mean and variance, as well as the within-subject correlation patterns through time for some response variable in a data set.

### Conceptual model of the mean
The mean trend is thought of in longitudinal data as a function of time:
$$Y_{ij} = \mu(t_j) + e_{ij}$$
Or in other words: *How does my response change on average over time?*  This conceptual model has two components: the mean response and the residual. These two components along with the distribution of the resonse variable, are what need to be modeled in longitudinal analysis.

## Working with group data
Often in longitudinal analysis, you want to compare the parameters of interest between groups in the data to ask questions like:
> Does the mean trend (slope) differ between my groups?
> Do I have different correlation patterns between my groups?
> Do my groups have different responses to come covariate?

### Formulation 1: Estimate group parameters directly
Instead of fitting a model for each group, you can instead come up with one general model and repeat it for each group, and insert an indicator variable for each repeated model to control which is relevant based on the value of your grouping variable. A model with this formulation on data with two groups will look like this: 
$$Y_{ij} = G_i(\beta_0 + \beta_1t_j) + (1-G_i)(\beta_2 + \beta_3t_j) + e_{ij}$$
### Formulation 2: Estimate differences between group parameters
The same model can instead be reformulated to directly let you look at the differences in the parameters between groups. The model in that formulation looks like this: 
$$Y_{ij} = \eta_0 + t_j\eta_1 + G_i\eta_2 + G_it_j\eta_3 + e_{ij}$$
This formulation sets one group as the reference, and the other(s) as then interpreted as deviation(s) from the reference parameters. In the formulation above, $G$ is an indicator variable again like it was in the first formulation.  You'll need one less indicator variables than groups in the data as one group will always be a reference and wont need to be indicated as all the groups are measured relative to the reference. 

### Polynomial model
The mean response does not have to be linear, the polynomial model can be used to add in a quadratic mean trend:
$$E(Y_{ij}) = \beta_0 + \beta_1t_{ij}+\beta_2t^2_{ij}$$
Accounting for groups in the mean model works the same way, just repeat the model but preface it with an indicator variable.

## Modeling covariance
The covariance part of the model has to do with the $e_{ij}$ term.  Here, what you're looking to describe is a covariance structure among the residuals of the model. This structure takes the form of a matrix, or put mathematically:
$$cov(e_i) = \Sigma_{i.}$$
This part is neceaary to specify in longitudinal models because there are repeated measures for each subject that will be correlated with each other in some way. 

### Unstructered covariance model
The unstructured covariance matrix has a parameter for each pair of time points that a subject has measurements in. If a subject does not have a measurement at a particular time point, then its correlation matrix excludes any parameters that would otherwise have the subscript for that time point.
### Compound symmetric
The compound symmetric model assumes that the correlation between the measurements of any two time points is the same, and all the time points have the same variance. 
### AR-1
This correlation structure assumes that time points that are further apart are less correlated with oneanother. Specifically, it assumes that time points separated by a certain uniform unit are proportionally correlated with one anoter by some coefficient, $\rho$. For example, time points separated by one unit are correlated by $\rho$, and time points separated by two units are correlated by $\rho^2$.
### Exponential
This is just a genaralization of the [[Mean and covariance modeling#AR-1|AR-1]] model to account for time points that are not evenly spaced. Instead of havind coefficients raised to integer powers, they are raised to powers directly proportional to the difference in units between the two time points. For example, two time points one taken at $t=1.7$ and one taken at $t=3.2$ would have a correlation of $\rho^{3.2-1.7}$.

> All three of these previous models assumed that variance was constant through time.



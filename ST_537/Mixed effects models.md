[[Linear_mixed_effects_models.pdf|lecture notes]] 

## The big picture
Mixed effects models let you estimate components of variation, and are mure robust to unbalanced conditions than their [[Estimation in the general linear model|GLS counterparts]]. At the most general level, defining a mixed effects model consists of defining a trend for each subject, and then describing how this trend changes from subject to subject. These steps are called the *subject-level stage* and the *population stage*, respectively and are directly related to characterizing the within unit, and between unit variation in the data.

## The LME Model

#### Subject level
The subject-level *linear mean trend* model is specified first. This has a familiar form: 
$$Y_i(t_{ij}) = \beta_{0i} + \beta_{1i}t_{ij} + e_{ij}$$
And describes the trend for **one** subject. What you are saying with this model is that you think each subject has its own unique slope and intercept.

#### Population level
The subject-level parameters can be thought of as a random population in themselves, randomly fluctuating around a population trend which itself has a set of parameters. The exact formulation for how they deviate [[Linear_mixed_effects_models.pdf#page=5|is shown here]]. 

### Putting it together
In general though, the model consists of **fixed** parameters for the intercept and slope ($\beta_0, \beta_1$), and **random** deviations from these fixed effects that can be predicted ($b_{0i}, b_{1i}$). This combination of different effects is why these models are called *mixed effects models*. The full formulation of this model is:

$$Y_{ij} = (\beta_0 + \beta_1t_{ij}) + (b_{0i} + b_{1i}t_{ij}) + e_{ij}$$
Where the parameters in the first set of parentheses model the fixed effects and the terms in the second set model the random effects.

### Within unit variation
The error component is specified in a similar way to how it is in the GLS model. By default, most software assumes independent errors with equal variance, but this can be adjusted by the user to account for biological deviation from this assumption. Following this, the within-unit variation can be explicitely segmented to estimate variation due to biological deviations, and variation due to measurement error.

With this last component, the model is fully specified. The notation for the formulation of the model is [[Linear_mixed_effects_models.pdf#page=7|shown here]].

### Including covariates
The model can be [[Linear_mixed_effects_models.pdf#page=8|further extended to include covariates]]. There's nothing special about this process relative to adding a covariate to a GLS model. Factor variables are added as indicator dummy variables which effectively copy the model formulation for each level of the factor.

In words, what you are saying by including these covariates in the random effects is *the subject-specific variation is influenced on the value of this covariate (in this way)*.

### Estimation and inference
Estimation and inference can proceed in the same way that was done with GLS. ![[Estimation in the general linear model#Inference]]


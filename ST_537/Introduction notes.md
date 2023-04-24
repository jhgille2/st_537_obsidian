---
DOI:
Date: 
Summary: The first lecture of the longitudinal data analysis section. This just introduces the general concept of the analysis and sets the goals and notation that are used in later lectures/the analysis in general.
Title: Introduction to longitudinal data analysis
annotation-target: pdf_path
---

#### [[Introduction_Longitudinal_Data_Analysis.pdf|Introduction to longitudinal data analysis]]

Longitudinal data is data that is collected for some variable for some subject at multiple sequential time points. The time points are not always evenly spaced, and not every subject will always have the same number of observations taken for every variable. 

## Objectives
[[Introduction_Longitudinal_Data_Analysis.pdf#page=4|The goal of longitudinal data analysis]] is to characterize different aspects of the longitudinal nature of the data (duh). Specifically, these are the mean response of the population, and how it changes through time. The population standard deviation, and how it changes through time. How are observations for each subject correlated with one another, and does this correlation change through time? If the within-subject correlation does change, then specifically how does it change mathematically? What are the effects of any covariates on any of the previous variables?

## Design terminology
A design is **balanced** if the same number of observations are taken for each subject, and all the observations for every subject are taken at the same time. Otherwise, a design is called **unbalanced**.  An **equally spaced** design has the same duration of time between each consecutive measurement.  

## Inferences

#### Population mean
The population mean is not a single value anymore because time is an element in the data, instead the mean is a *function of time* that has a value for each time point in the data. The mean of the population can be constant over time, can have a trend over time, or be affected by other covariates over time. 

#### Population variance
The population variance/standard deviation can be thought of in the same way. The population mean and variance are estimated at each time point my taking the sample mean and variance of all the observations at that particular time point. 

#### Subject-level covariance
Each subject has measurements taken on it multiple times. These measurements may have some correlation structure. The correlation and covariance for each subject is estimated with the [[Introduction_Longitudinal_Data_Analysis.pdf#page=7|sample sovariance and correlation]].

#### Missing data considerations
Somethimes it is impossible to estimate a parameter at a time point because there is not enough data. One approach is to instead pool observations in time windows instead to make a smoother profile with more data.
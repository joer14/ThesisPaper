# Literature Review

<!--
After the introductory chapter, it seems fairly common to 
include a chapter that reviews the literature and 
introduces methodology used throughout the thesis.
-->

## Traditional Dosing

Explain what heparin is, how heparin is traditional prescribed.  
reference dosage guidelines which are in the appendix. 

## High Level

At a high level explain what we want to do - remove doctors manual process/guessing heuristics.  
we want to predict the amount of heparin needed to get a therapeutic aptt. explain aptt is our marker for success. explain that there is a lot of data that can be used for predictions - explain how they selected their features.  

## Prediction 

explain different techniques that could be used (svm, logistic regression, others listed in their paper)  
then explain that mohammad et al chose to use logistic regression because it had a natural relationship with this...  

### Logistic Regression 

explain what logistic regression is and how they used the multiparameter model.  
explain how they choose features for the model.  
explain assumption of proportional odds-  
> Ordinal logistic regression is a special form of multinomial logistic regression which is commonly used to model categorical outcomes with some meaningful order. Besides the assumption that outcomes can be ordered in a meaningful way, ordinal regression also makes the assumption of proportional odds. This assumption leads to regression coefficients that are maintained across classes, with only the intercept terms of the models changing. That is, it assumes that explanatory features maintain identical effects across varying ranges of the outcome. seem that modeling therapeutic aPTT categories would lend itself nicely to this kind of approach. However, we did not feel that the assumption of proportional odds was a valid one. Specifically, the constant nature of the regression coefficients enforces zero skew on the P(therapeutic) function, and  thereby limits the flexibility of the approach.  
thereby limits the flexibility of the approach.
explain equation 1.

(@ref_for_eqn1) $P(thera) = P(sub) + P(supra)$

## Summary of their results 

Summary of the results from their paper.  It is better than weight based system alone.  
They weren't able to test if it was better than an actual doctor because you'd need to have the system in place to do that. That is where this system/survey comes into play.  

<!-- Insert an unordered list -->

<!-- - first item in the list
- second item in the list
- third item in the list

 -->


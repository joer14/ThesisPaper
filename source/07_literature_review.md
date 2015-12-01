# Background

## Traditional Dosing of Heparin 

Heparin is an anticoagulant medication administered intravenously to patients with blood clots. Specifically it is often used for strokes, pulmonary embolism (blockage in an artery in the lung), acute coronary syndrome (e.g. heart attack), and many other conditions. The general protocol for dosing heparin is to initially order baseline lab results for the patient. These values combined with context of the patients condition allow a doctor to determine the infusion rate and if a bolus (a single large initial dose) is required. The primary metric used for monitoring patient progress is activated partial thromboplastin time (APTT). After the infusion is started the patient is monitored and the dose is adjust periodically. Most often new labs are ordered every 6 hours [citation to UW and Beth Israel].

<!--
After the introductory chapter, it seems fairly common to 
include a chapter that reviews the literature and 
introduces methodology used throughout the thesis.
-->



<!-- Explain what heparin is, how heparin is traditional prescribed.   -->
<!-- reference dosage guidelines which are in the appendix.  -->

<!-- ## High Level -->

<!-- At a high level explain what we want to do - remove doctors manual process/guessing heuristics.   -->
<!-- we want to predict the amount of heparin needed to get a therapeutic aptt. explain aptt is our marker for success. explain that there is a lot of data that can be used for predictions - explain how they selected their features.   -->

## Predicting Therapeutic Outcome

The objective of the dosing tool is determine an ideal initial infusion rate, such that patient has the highest probability of reaching a therapeutic state in 6 hours time. A therapeutic state is defined as an APTT value of between 60 seconds and 100 second. To predict an optimal dose Ghassemi et al. employed the use of multi-variant logistic regression. 


### Logistic Regression Approach 

<!-- Logistic regression  -->
The objective of the model was to determine the probability that patient would end in one of three categories: sub-therapeutic, therapeutic, or supra-therapeutic. A patient can by definition only be in one category at a time. This lead Ghassemi et al. to the following equation:  
(1) $1 = P(sub-therapeutic) + P(therapeutic) + P(supra-therapeutic)$  

The challenge of using logistic regression to predict therapeutic outcomes is that the probability of a therapeutic outcome is not a strictly monotonic function. So using logistic regression directly to predict P(therapeutic) will not work. That being said, the probability of sub-therapeutic and supra-therapeutic outcomes are monotonically decreasing and increasing functions respectively. Given these properties, we can use multinomial logistic regression to determine functions for sub-therapeutic and supra-therapeutic aPTT. Using equation 1 we can then determine the probability of a therapeutic outcome.  
Although at this point a case been has made that multinomial logistic regression may be an appropriate tool, there are a few considerations the Ghassemi et al. took with regards to the form of regression. There are many forms of multinomial logistic regression with subtle but important differences. There is a natural order to the classifications (sub-therapeutic, therapeutic, supra-therapeutic), so ordinal logistic regression could be considered. The challenge with ordinal logistic regression, however, is that it makes the assumption of proportional odds, so regression intercept terms vary across classes while regression coefficients are shared across classes. In the words of the original authors *"it assumes that explanatory features maintain identical effects across varying ranges of the outcome"*[citation appendix]. Instead the ordinal regression they instead used a modified version of standard multinomial logistic regression, which utilized a flexible reference category. That is instead of using a single class to predict the outcome that is not being modeled, they used all classes. So when modeling supra-therapeutic aPTT, standard multinomial logistic regression would reference either therapeutic or sub-therapeutic aPTT classes, while their approach referenced both classes. This choice was demonstrated to have significant effects on the validity of their models [citation to appendix, section 2].   


<!-- To predict the probability of a therapeutic outcome  -->

<!-- explain different techniques that could be used (svm, logistic regression, others listed in their paper)   -->
<!-- then explain that mohammad et al chose to use logistic regression because it had a natural relationship with this...   -->


<!-- explain what logistic regression is and how they used the multiparameter model.   -->
<!-- explain how they choose features for the model.   -->
<!-- explain assumption of proportional odds-   -->


### Feature Selection 
There are innumerable potential features one could consider as predictors of patient outcome. In their paper, Ghassemi et al. determined the salient features as follows: age, SOFA score, Elixhauser, Heparin dose, Measurement time, Creatinine, Ethnicity, Gender, ICU type, presence of pulmonary embolism, obesity, presence of end stage renal failure. 


## Summary of Their Results

The original paper and associated appendix document the efforts taken to validate the models. To summarize, they partitioned their dataset, dedicating 70% to training and 30% for validation. They then compared the calculated the predicted classification for each patient using both a full featured model and a weight-only model. The full featured model was more accurate than the weight-only approach as measured by Volume Under the Receiver Operating Characteristic Surface (the multiple class version of Area Under Receiver Operating Characteristic Curve), with values of 0.48 vs 0.42 [citation].  
In closing, they noted that a randomized controlled trial would be necessary to determine if this mechanism is more effective for dosing. This thesis project represents the initial steps towards this trial. 

<!-- Summary of the results from their paper.  It is better than weight based system alone.   -->
<!-- They weren't able to test if it was better than an actual doctor because you'd need to have the system in place to do that. That is where this system/survey comes into play.   -->

<!-- Insert an unordered list -->

<!-- - first item in the list
- second item in the list
- third item in the list

 -->



# Introduction

<!-- ## Background -->
<!-- 
Explain how I reimplemented a research paper into a real world web application and then tested it. 

- keep it relatively high level  
- current dosing practices 
- how retrospective data comes into play, potential improvements it offers. Increasing patient care outcomes. Cost/length of stay outcomes. Could revolutionize the ways in which drug trails occur. Drug trails traditionally use a rather homogeneous group of people, and test them to with doses to see if there are any adverse effects. After we test with the homogeneous group, the guidelines developed are used for patients that do not fit in with the testing cohort, so no guidelines for proper dosing exist for these patients. 
- purpose of thesis, demonstrate a potential interface for an actual model that has been peered reviewed gather insights on potential issues with dosing. Also create a sample web application that works for this use case, so that the technique can be more easily generalized to other drugs such as ....???? 
- 
The intention of this study was to determine the feasibility of using statistical drug dosing tools in a mock clinical setting. We wanted to learn about both the technical implementation and user experience challenges involved with creating and using computer aided dosing tools. First a web application was developed using existing models for dosing heparin in ICU patients. This application was next developed into an interactive user survey. We found that Doctors were generally more confidant and faster when dosing using the tools. [[add other results here too. It's good to avoid numbers in abstracts from what I recall]] In closing we recommend some best practices for future development of statistical drug dosing tools.

 -->
<!-- 

intro
talk about what I did
-- implemented exisiting tool
-- implemented a survey
-- collected responses




 -->

The primary goal of this study was to determine the technical implementation challenges and user experience challenges involved with a statistical dosing tool. Specifically, we implemented a heparin dosing tool that was first introduced in the paper *A data-driven approach to optimized medication dosing: a focus on heparin* [@ghassemi2014data]. In the paper a statistical model is generated for predicting an optimal infusion rate for heparin for patients in intensive care units (ICUs). In this study, we reimplemented their existing models into an interactive web application, which allows the user to generate dosage guidelines based on a patient's features. Next a user study application was created, which presents the doctors with a patient case. The doctor initially provides their own suggestion for the infusion rate and is then presented with the model's prediction for an optimal infusion rate. After the doctor views the model, they have the opportunity to adjust their initial dose and provide a reasoning for their dose adjustments. Their interaction with the tool yields many metrics, including number of dose adjustments, speed of dosing, number of times guidelines were viewed. 

<!-- One serious disadvantage of heparin risk factor analyses based on clinical trials alone is that they exclude patients who exhibit a high propensity for bleeding or severe complications caused by bleeding [2]. Retrospec- tive analyses like ours are able to overcome this issue by utilizing clinical data that is reflective of the entire pop- ulation actually receiving treatment.  -->
<!-- Their final multiple feature model improved outcome classification over a weight-only with a volume under the surface (VUS) of 0.48 vs. 0.42. -->

<!-- Statistical dosing tools offer an alternative to traditional dosing methodologies, which by nature cannot be tuned to a specific patient's every condition every time. Additionally, traditional dosing often is backed by heuristics, knowledge accumulated overtime by more experienced doctors. This knowledge is not peer reviewed and cannot be easily transfered to other new doctors. The promise of statistical dosing is that it   -->

<!-- 
To include a reference, add the citation key shown in the references.bib file. 
[@Cousteau1963].
-->

<!-- 
This is a brief outline of what went into each chapter. **Chapter 1** gives a background on duis tempus justo quis arcu consectetur sollicitudin.  **Chapter 2** discusses morbi sollicitudin gravida tellus in maximus.  **Chapter 3** discusses vestibulum eleifend turpis id turpis sollicitudin aliquet.  **Chapter 4** shows how phasellus gravida non ex id aliquet. Proin faucibus nibh sit amet augue blandit varius. -->


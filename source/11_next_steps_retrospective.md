# Retrospective and Next Steps 

<!--
After the introductory chapter, it seems fairly common to 
include a chapter that reviews the literature and 
introduces methodology used throughout the thesis.
-->
## User Concerns 

Although most participants expressed that the dosing tool gave them greater confidence, the majority also had reservations with adopting the tool in their practice. Their common concern involved their understanding of how the tool worked. This concern is appropriate, as it reflects a conservative approach to experimenting on best practices in patient care. One reason for their lack of understanding can be attributed to the nature of this study, in that participants completed the survey on their own time and were given no incentives for completing the survey. As such, many users may have read the system explanation quickly.  
Additionally, the technique used for dosing, although not terribly complex, is not trivial to understand. Physicians in general cannot be asked to learn how a logistic regression works or how these models are built. Simply speaking, their time is very valuable and limited. Thus, experimental techniques need to be validated in formal clinical setting with physicians who are invested in understanding and participating in a trial of the new tools. Then once the techniques are validated others can adopt them with greater confidence.  
Another concern expressed was that the tool did not consider other potential features when dosing patients. Although these features can be added overtime, as the data becomes available and coded appropriately, this concern speaks to the greater issue of user interaction with the model. In its current state, the standalone calculator allows physicians to view the weight-only model and the all-features model (age, SOFA score, creatinine level, ethnicity, gender, etc.) This gives them a better understanding of how these features change the therapeutic curve. Future versions of this tool should allow the user to enable and disable a given feature, so they can have a better understanding of the effects of the feature on the model outcome. This understanding could potentially come in the form of additional visualizations like the original graph or arguably better in the form of written descriptions, e.g. "The SOFA score causes a deviation of 3% from normal dosing." An initial version of this project included a crude nearest-neighbor visualization, but that feature was not incorporated in the final version due to time limitations. Increasing user interaction with the tool will hopefully address some knowledge and trust issues with the current system. 

## Shortcomings in the Survey

This study has no shortage of problems. The problems generally come from a lack of resources, in terms of time and money. A funded study would allow for a greater number of participants with specific ICU expertise. Additionally, the participant selection process would not be limited to friends of the researchers, which may have skewed the results. Funding would also allow for time for researchers to work with participants to better understand the model. Given the problems with the survey, and limited number of participants, the results are still very valuable as they clearly reveal areas for future improvement in the system.  
One place for future research would be creating a similar survey that periodically provides sub-par dosage estimates for doctors. Then one could measure how frequently doctors correct the estimate. If doctors do not consistently catch dosing errors, that would indicate that increased dose validation software should be implemented.  


<!-- ## Places for Future Research -->

<!-- how did the doses differ in part 1 and part 2 of the survey.  -->

## Future Implementations

The experimental nature of this project has lead to a software implementation that is limited in several ways. The codebase served its purpose as a tool for a research study fairly well, but it is not "real world" ready in its current form. In future versions we'd like to see improved logging, system documentation, automated unit testing on builds, and better scaling performance. Additionally, the overall design should be more modular, such that it is easier to try out and compare different candidate models (e.g. Ensemble Learning, Neural Networks, SVMs, etc.) on different drugs. Automated testing could even run trial comparisons and compute statistics on models. From a data processing perspective, an entire subsystem should be designed and built for selecting data from the medical records database and translating it into a suitable form for models. There should also be tools for validating the cohort selection. This is not a trivial task when working with a specific medical record database, and becomes much more challenging when attempting to interface with other databases. Defining the generic interface used for selecting the cohort from the database will be challenging. Finally, the data will also need to be validated and then translated (coded) to appropriate values for a given model.  
On the front-end, user analytics could be improved, as it would be ideal to know more about the user's device and how they interact on a per-click basis. One final improvement on the client would be modifying the data model, such that instead of requesting an estimate for a specific patient, the client requests a static model that has been precomputed on the server using the latest dataset. Then the user can manually modify features and the estimated probability curves are computed client side. This should allow for a much more responsive experience for the user, providing them instantaneous feedback for each feature change made, instead requiring a request to the server for each change. The dosage curves could be computed in a separate thread using web workers. Additionally, by implementing the predictions client side, patient data does not need to be transfered to an external server (easing HIPAA compliance), and the client can be fully functional offline which is ideal for low resource environments such as developing countries. 

<!-- documented, tested, scalable, maintainable/easy to modify models, design well though out -->


<!-- better build system -->
<!-- better analytics/guidelines -->
<!-- - transfer model to device so it can do queries more quickly -->
<!-- - instead of static data source have real medical database -->
<!-- - easily interchangeable models -->
<!-- - better analytics  -->

<!-- blank lines at end -necessary for template -->


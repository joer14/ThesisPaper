# Heparin Survey

<!--
After the introductory chapter, it seems fairly common to 
include a chapter that reviews the literature and 
introduces methodology used throughout the thesis.
-->

## Survey Design

The primary objective of the survey was to learn about the user experience challenges involved with data-driven dosage techniques. To do this a test interface was developed and several medical doctors of varying disciplines attempted to use it. The survey consisted of 5 patient cases developed by domain experts to cover multiple different use cases for heparin. A doctor would first agree to a research disclosure, then fill out a short questionnaire about their background and relevant experience. Next an instruction page was displayed explaining the survey. Once the doctor read over the instructions and guidelines, they were presented with their first case which consists of some lab results and a short admission note. It was their task to determine a potential infusion rate based on traditional heparin dosing guidelines that were available to them. After choosing an infusion rate, the model showing the suggested optimal dose was displayed, along with the location of the users dose. The doctor then had the option of either adjusting the dose or sticking with their initial dose. Whenever dosing the doctor was able to leave notes to explain their reasoning. This task then was repeated for the remaining four patients. After completing the test, there is a short follow-up questionnaire consisting of a few questions to gauge receptiveness to the tool and measure any change in confidence in the tool. Additionally, we asked for other places they thought the tool could be used. 
<!-- Additionally, we wanted to learn about any advantages and disadvantages the technique brings to doctors. To do thi -->
<!-- what the goals of the survey were. - what did we want to learn? hypothesis      -->
<!-- how the survey was conducted.  -->
<!-- how we decided what information to ask about.  -->
<!-- what information that was logged.   -->

## Architecture and Implementation

The survey was implemented using the same technological stack as the calculator. By utilizing a SPA (single page application) methodology we were able to quickly iterate and make many changes over time. There were several candidate versions of the survey developed over time, but the final iteration allows for the most direct input of comments from doctors, instead of relying on proxy metrics such as time to complete cases that are similar with and without the heparin calculator. 

<!-- talk about the stack, tools used etc. how it was implemented. user experience.   -->
<!-- blank lines at end -necessary for template -->


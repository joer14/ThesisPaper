# Heparin Survey

<!--
After the introductory chapter, it seems fairly common to 
include a chapter that reviews the literature and 
introduces methodology used throughout the thesis.
-->

## Survey Design

\begin{figure}[H]
\centering
\includegraphics[width=0.7\textwidth]{source/figures/part3_iii.png}
\caption{\label{fig:part3_iii}Dosage curves with doctors initial dose plotted in black on the therapeutic curve.}
\end{figure}

The primary objective of the survey was to learn about the user experience challenges involved with data-driven dosage techniques. To do this a test interface was developed and several medical doctors of varying disciplines attempted to use it. You can view the interface [online](https://hepstack-stage.herokuapp.com/) or in [Appendix 2](#appendix-2-application-user-interface). The survey consisted of five patient cases developed by domain experts to cover multiple different use cases for heparin. A doctor would first agree to a research disclosure, then fill out a short questionnaire about their background and relevant experience (figure \ref{fig:presurvey}). Next an instruction page was displayed explaining the survey (figure \ref{fig:part3info1}, \ref{fig:part3info2}). Once the doctor read over the instructions and guidelines, they were presented with their first case which consists of some lab results and a short admission note (figure \ref{fig:part3_i}). It was their task to determine a potential infusion rate based on traditional heparin dosing guidelines that were available to them. After choosing an infusion rate, the optimal dose model was displayed (figure \ref{fig:part3_ii}). Unlike the standalone calculator, with the survey version of the graph does not present the weight-only model. It does however plot the user's initial infusion rate on the estimated therapeutic curve in black, so they can visualize the estimated dose versus their own dose (figure \ref{fig:part3_iii}). The doctor then had the option of either adjusting the dose or sticking with their initial dose. Whenever dosing the doctor was able to leave notes to explain their reasoning. This task then was repeated for the remaining four patients. After completing the test, there was a short follow-up questionnaire consisting of a few questions to gauge receptiveness to the tool and measure any change in confidence in the tool. Additionally, participants were asked for other places they thought the tool could be used(figure \ref{fig:postsurvey}).
Due to financial and scope limitations, we could not compensate participants for their time taking the survey. As a result all volunteers were acquaintances or friend's of friends of the author.

<!-- Additionally, we wanted to learn about any advantages and disadvantages the technique brings to doctors. To do thi -->
<!-- what the goals of the survey were. - what did we want to learn? hypothesis      -->
<!-- how the survey was conducted.  -->
<!-- how we decided what information to ask about.  -->
<!-- what information that was logged.   -->

## Architecture and Implementation

The survey was implemented using the same technological stack as the calculator (Angular.js and Bootstrap on the frontend). By utilizing a SPA (single page application) methodology we were able to quickly iterate and make many changes over time. There were several candidate versions of the survey developed over time, and tested with domain experts for feedback. The final iteration allows for the most direct input of comments from doctors, instead of relying on proxy metrics such as time to complete cases that are similar with and without the heparin calculator. 

<!-- talk about the stack, tools used etc. how it was implemented. user experience.   -->
<!-- blank lines at end -necessary for template -->


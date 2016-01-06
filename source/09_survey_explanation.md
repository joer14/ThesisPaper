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

The primary objective of the survey was to learn about the user experience challenges involved with data-driven dosage techniques. To do this, a test interface was developed and several medical doctors of varying disciplines attempted to use it. You can view the interface [online](https://hepstack-stage.herokuapp.com/) or in [Appendix 2](#appendix-2-application-user-interface). The survey consisted of five patient cases developed by domain experts to cover multiple different use cases for heparin. A doctor would first agree to a research disclosure, then fill out a short questionnaire about their background and relevant experience (Figure \ref{fig:presurvey}). Next an instruction page was displayed explaining the survey (Figure \ref{fig:part3info1}, \ref{fig:part3info2}). Once the doctor read over the instructions and guidelines, they were presented with their first case which consists of some lab results and a short admission note (Figure \ref{fig:part3_i}). It was their task to determine a potential infusion rate based on traditional heparin dosing guidelines that were available to them. After choosing an infusion rate, the optimal dose model was displayed (Figure \ref{fig:part3_ii}). Unlike the standalone calculator, the survey version of the graph does not present the weight-only model. It does, however, plot the user's initial infusion rate on the estimated therapeutic curve as a black dot, so they can visualize the estimated dose versus their own dose (Figure \ref{fig:part3_iii}). The doctor then had the option of either adjusting the dose or sticking with their initial dose. Whenever dosing the doctor was able to leave notes to explain their reasoning. This task then was repeated for the remaining four patients. After completing the test, there was a short follow-up questionnaire consisting of a few questions to gauge receptiveness to the tool and measure any change in confidence when using the tool. Additionally, participants were asked for other places they thought the tool could be used (Figure \ref{fig:postsurvey}).
Due to financial and scope limitations, we could not compensate participants for their time taking the survey. As a result all volunteers were acquaintances or friend's of friends of the author.

<!-- Additionally, we wanted to learn about any advantages and disadvantages the technique brings to doctors. To do thi -->
<!-- what the goals of the survey were. - what did we want to learn? hypothesis      -->
<!-- how the survey was conducted.  -->
<!-- how we decided what information to ask about.  -->
<!-- what information that was logged.   -->

## Architecture and Implementation

The survey was implemented using the same technological stack as the calculator (Angular.js and Bootstrap on the front-end, Python and Flask on the back-end). By utilizing a SPA (single page application) methodology we were able to quickly iterate and make many revisions. There were several candidate versions of the survey developed and tested with domain experts for feedback. One initial version had the user adjusting the heparin infusion rate over time, to more accurately simulate a patient's care (Figure \ref{fig:old}). This technique was not used in the final version because we did not want to introduce the challenge of generating lab results dynamically overtime as a function of heparin infusion rate, and the patient's current and past conditions. The final iteration does not require the simulation of patient lab results and allows for the most direct input of comments from doctors, instead of relying on proxy metrics such as time to complete cases that are similar too each other. 

<!-- talk about the stack, tools used etc. how it was implemented. user experience.   -->
<!-- blank lines at end -necessary for template -->


# Heparin Dosage Calculator


<!-- ## Introduction -->

This project is composed of two key components. The first is a "dose calculator" which contains all the functionality required to determine the optimal dose for a given patient. The second component is a survey that incorporates the calculator and is used to study how doctors interact with the dosing tool. We now describe the calculator.

<!-- explain what it is - a standalone calculator, to familiar doctors with the technique.  -->
<!-- Goals of System   -->
<!-- - mobile ready...  -->
<!-- talk about user experience/ui design. -->

## Functional Requirements 
The purpose of the calculator is to determine the probability functions for sub-therapeutic, therapeutic, supra-therapeutic aPTT for a range of infusion amounts for a given patient. The calculator can be broken into three steps:  
1. Access and refine Dataset  
2. Calculate static models  
3. Make a prediction based on a given patient's features. 

### Data Processing

The data source for the original study was the MIMIC II database [citation]. MIMIC is an open access database consisting of over 40,000 deidentified patient encounters from Beth Israel Deaconess Hospital's ICUs. It is hosted at MIT's Lab for Computational Physiology. The majority of patients in an ICU do not receive heparin, so filtering by medication was needed. This was accomplished by a series of SQL queries on a local machine. Furthermore, we worked to maintain an identical dataset as was used in the original dataset. This required filtering out all transfer patients and all patients missing required features. Additionally some features viz. Elixhauser comorbidity index, mean Sequential Organ Failure Assessment (SOFA), required manual calculation on a per patient basis, as they were not available directly from MIMIC. This yielded a dataset of approximately 1,600 patients. This number varies depending on the features supplied for a given prediction.  

This data munging was primarily done in Python using the Pandas library, but also required PostgreSQL for hosting the database. SQL queries were composed by hand. To prepare the data for model generation we needed to code several variables. Specifically, we needed to add binary classifiers for sub-therapeutic and supra-therapeutic to each patients dataset. Additionally a binary classifier was needed for ethnicity, and we followed the original coding used in the paper (white and non-white). 

<!-- 
talk about mimic ii / iii - was it, wheres it from etc. 
what is needed to get a cohort
what else you need to look up to get a full dataset
that i ended up getting dataset from Mohammad
that i needed to filter... started with 4,000, got down to x patients by filtering 
out transfers etc. 

then talk about tech I used to do this
- python, numphy, sql, etc... 
  -->

### Model Generation

Once the dataset was prepared, generating the models was fairly simple. We used the Python library Scikit-learn's implementation of multinomial Logistic Regression to compute the two logistic regressions. Once the two logistic regressions for sub-therapeutic and supra-therapeutic aPTT are generated they can be stored for later use as long as the dataset is static. We avoided doing this to simulate a real world scenario where data is constantly being added overtime. 
<!-- 
need to generate the 2 models using the features in python and x function calls.

 -->
  
### Model Prediction

To generate the final dose curves for a specific patient we use scikit-learn's logistic regression predict_proba function. A function was created to output the probability of sub-therapeutic, sup-therapeutic aPTT given a patients features and a dose. For graphical purposes we call this function repeatedly for varying infusion rates in the range of 0 to 34 units/Kg/HR in steps of 0.5 units/Kg/HR. Predicting the specific infusion rate which maximizes the probability of a therapeutic outcome can also be thought of as finding the point which minimizes the sum of the probabilities of sub-therapeutic and supra-therapeutic (see equation 1). Using this fact we used the python library scipy's minimize_scalar function which implements Brent's Method and let it solve for the highest probability with a tolerance of .01%. The infusion rate curves and the optimal dose are then cached in Postgres for future queries that match the same patient features, given that the initial dataset has not changed.    


<!-- from scipy.optimize import minimize_scalar -->

<!-- from sklearn.linear_model import LogisticRegression -->
<!-- 
talk about how I used a loop to create the dose curve
talk about how I used the maximization function to maximize the probability of therapeutic 
 -->

## Architecture 
<!-- maybe include a diagram -->

<!-- Figure \ref{ref_a_figure} shows how to add a figure. Donec ut lacinia nibh. Nam tincidunt augue et tristique cursus. Vestibulum sagittis odio nisl, a malesuada turpis blandit quis. Cras ultrices metus tempor laoreet sodales. Nam molestie ipsum ac imperdiet laoreet. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. -->

### Frontend 


\begin{figure}
\centering
\includegraphics[width=0.7\textwidth]{source/figures/calc_graph.png}
\caption{\label{fig:calc_graph}Graph generated by the client software displaying an all features model vs. a weight-only model.}
\end{figure}

The frontend for the application was built in Angular.js. Angular.js is client-side MVC (Model View Controller) framework that was chosen for it's strengths in quick prototyping. The user interface was built on Twitter Bootstrap, as it was familiar to the authors, is relatively easy to use and offers built in responsive design. Additionally, it has many CSS components such as nice forms and progress bars that are useful for the design.  
For graphing the D3.js, NV-D3 and Angular-nvd3 libraries were used which enables inserting graphs using simple directives. Figure \ref{fig:calc_graph} shows an example output of the standalone calculator as seen in [Appendix 2](#appendix-2-application-user-interface) or 
[online](https://hepstack-stage.herokuapp.com/#/calc). The two prominent dots represent the optimal doses for each model. Note that in this example, the weight-only model predicts that the probability that the patient will reach therapeutic state is higher than the all features model.

<!-- explain this is a standalone version
include screen shot maybe? 
explain how user interacts with this on the frontend 
explain how frontend was built 
	angular, bootstrap, nvd3, etc...
 -->

### Backend  


\begin{figure}[H]
\noindent
\includegraphics[width=1.05\textwidth]{source/figures/arch1.png}
\caption{\label{fig:flow1}Example of a typical client server interaction.}
\end{figure}

The backend for the application utilizes Python's Flask webframe work. Data is stored in postgreSQL and accessed through the sqlalchemy object relational mapping library. The frontend interfaces with the server via a stateless RESTful API which enables the exchange of json data. Figure \ref{fig:flow1} shows an example of how a client interacts with the backend server currently. 

<!-- 

explain how frontend and backend connect
what calls are made, idk. 

 -->






<!-- architecture here... include a figure.F igure \ref{ref_a_figure} shows how to add a figure. Donec ut lacinia nibh. Nam tincidunt augue et tristique cursus. Vestibulum sagittis odio nisl, a malesuada turpis blandit quis. Cras ultrices metus tempor laoreet sodales. Nam molestie ipsum ac imperdiet laoreet. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. -->

<!-- ![RV Calypso is a former British Royal Navy minesweeper converted into a research vessel for the oceanographic researcher Jacques-Yves Cousteau. It was equipped with a mobile laboratory for underwater field research. \label{ref_a_figure}](source/figures/example_figure.pdf) -->

<!-- ## Implementation  -->

<!-- talk about the stack, tools used etc.  -->
<!-- talk about how the tools used helped ensure rapid prototyping and good ui.  -->

<!-- blank lines at end -necessary for template -->


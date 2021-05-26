# FRAUD DETECTION MODELS
- Notebook 1: Application Fraud Detection
- Notebook 2: Property Tax Fraud Detection

## Application Fraud Detection :female_detective:
### Overview
Application Fraud is a form of identity fraud that involves a fraudster applying for a new account in a service or product using stolen or synthetic identities. The targets are often bank accounts, credit or debit cards, public administration, e-commerce, and loans, to name a few. This type of fraud is often the consequence of previously accomplished data breaches that provide the fraudster with massive personal information data sets. These are used to forge synthetic identities or to impersonate somebody else.

While it is impossible for a human being to quickly and accurately evaluate each application that arrives at a banking institution for fraud, machine learning models made much progress in detecting application fraud over the past few decades. 

## Executive Summary
The objective of this project is to build a real time Application Fraud algorithm. As this is an identity fraud problem, we were provided with a dataset of applications containing the identity fields of the applicants and a label indicating Fraud/Non-Fraud. 

> The model developed in this project will be able to predict in real-time, the probability of a new application in the system being fraudulent with 99.1% accuracy and 80% precision.

![alt text](https://github.com/sneha-raj/Fraud-detection-models/blob/master/Summary.png)

### Process Overview
- Data Pre-processing
  - The dataset contained one million records and ten fields. 
  - A data quality check revealed four variables with frivolous values which were replaced to avoid bias in modelling. 

- Feature Engineering
  - First, we carefully separated out the out-of-time (OOT) data from the training and testing data to ensure the model would only look at past data.
  - Second, we created variables to uniquely identify applicants, features to identify entities like SSN and built entity combination groups.
  - Then we built a few hundred expert variables from the above features using the velocity, relative velocity and frequencies of these variables, taking care to ensure no variable was being built on future data.

- Feature Selection
  - In the first stage, we utilized a univariate filter by calculating the KS(Kolmogorov-Smirnov) and Fraud Detection Rate (FDR) to rank the features and selected the top 80 candidate features. 
  - In the next stage, we ran a Recursive Feature Elimination (RFE) wrapper model to first select the top 50 variables and then again to identify the top 30 most important variables in predicting the fraud label. 
  
- Model-building
  - A number of linear and non-linear predictive models were built using the 30 features produced by the wrapper. 
  - Specifically, the models built were logistic regression, neural networks, boosted trees, and random forest models with a number of varying hyperparameters. 
  - Each of these models were evaluated depending on the FDR (fraud detection rate) at 3% on the training, testing, and out of time datasets. 

- Identifying the best model
  - The best model with the highest training FDR was chosen and further tuned on different hyperparameter combinations and minority oversampling techniques.
  - The best model was a Random Forest model with 50 trees and a node size of 300 and was able to achieve a 55.7% FDR on the test dataset by selecting 20 features. 

### Summary
In summary,a supervised model to predict application fraud in real-time was built. The model utilizes the most relevant 30 candidate variables determined by a multi-step feature selection process that was implemented after creating an in-depth data quality report, cleaning the data by replacing frivolous values, and creating entities and combination groups that allowed us to engineer 601 candidate variables. After testing various models with these top 30 candidate variables, a Random Forest Model was determined to be best able to predict fraud. This model was fine-tuned by varying a number of parameters to select the best Random Forest model. The final Random Forest model selected had a fraud detection rate of 56% in the test dataset using 20 out of the 30 features input to it.


## New York Property Tax Fraud Detection


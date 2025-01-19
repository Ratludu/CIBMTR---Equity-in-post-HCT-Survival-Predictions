# CIBMTR - Equity in post HCT Survival Predictions

Current submission gives a CV score of 68 and a LB score of 68.5.

## Overview

[CIBMTR - Equity in post HCT Survival Predictions](https://www.kaggle.com/competitions/equity-post-HCT-survival-predictions/overview) is aimed at developing models to improve the prediction of transplant survival rates for patients undergoing allogeneic Hematopoietic Cell Transplant (HCT) - an important step in ensuring that every patient has a fair chance at a successful outcome, regardless of their background.

## Description

(Summarising the description from Kaggle) 
Improving survival predictions for allogeneic HCT patients is a vital healthcare challenge. Current models do not fully address the disparities related to socioeconomic status, race and geography. Addressing these gaps is crucial.

The goal is to address disparities by bridging diverse data sources, refining algorithms and reducing biases to ensure equitable outcomes for patients across diverse race groups.

## Evaluation Criteria

The evaluation used is a specialised metric called the Stratified Concordance Index (C-index), adpated to consider different racial groupd independently. This method allows us to gauge the predictive performance of models in a way that emphasises equitability across diverse patient populations, particularly focusing on racial disparities in transplant outcomes.

### Concordance Index

It represents the global assessment of the model discrimination power: this is the models ability to correctly provide a reliable ranking of th esurvival times based on the individual risk scores. 

$$\text{C-index} = \frac{\sum_{i,j}1_{T_j< T_i}\cdot 1_{\eta_j>\eta_i}\cdot \delta_j}{\sum_{i,j}1_{T_j < T_i}\cdot \delta_j}$$

with:

- $\eta_i,$ the risk score of a unit $i$
- $1_{T_j<T_i}=1$ if $T_j < T_i$ else $0$
- $1_{\eta_j<\eta_i}=1$ if $\eta_j < \eta_i$ else $0$

C-index = 1 corresponds to the best model prediction and 0.5 represents a random prediction.

## Stratified Concordance Index

We adjust the standard C-index to account for racial stratification, thus ensuring that each racial groups outcomes are weighed equally in the model evaluation. The stratified c-index is calculated as teh mean minus the standard deviation of the c-index scores calculated within the recipients race categories, i.e. the score will be better if the mean c-index over the different race categories is large and the standard deviation of the c-indicies of the race category is small.


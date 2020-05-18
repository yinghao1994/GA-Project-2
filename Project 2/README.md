# Project 2: Ames Housing Price Prediction - README.md
#### Don Chng, General Assembly SG-DSI-14
#### 4th May, 2020

## Problem Statement

In this project, we wantidentify the key factors which affect the housing prices in Ames, Iowa. Furthermore, using these factors as inputs, we aim to create a model that can give good predictions on subsequent housing price. Hence, the goal is to **predict the housing prices with the lowest possible error**. 

## Executive Summary

Both the train and test dataset had to be cleaned for numerous null values. Ordinal datatypes had to be switched into numbers and nominal datatypes encoded into dummy variables. 

Exploratory Data Analysis was first done to identify the relationships between the 80 variables. It was important to use a heatmap and correlation plots to identify correlations between the variables. 

An initial model was first created using linear regression, using variables that had high correlations to sale prices. In order to make sure that there was no stone left unturned, regularization models such as Ridge, Lasso and ElasticNet were used to comb through all the variables and minimize or eliminate those that are irrelevant. The aim was to identify which variables are most price sensitive, as well as to create a model that minimizes error.

## Data Dictionary  
  
Refer to http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

## Conclusion

We notice certain commonalities between key variables in models that have displayed a high sensitivity in prices, which are:

- Above Grade Living Area 
- Overall Quality 
- Neighbourhoods
- Year Built 
- Garage
- 1st Floor Area
- Basement Area

The Lasso and Ridge Regression Model have certainly shown some oddities in non-essential features have high coefficients. In Ridge Regression, these oddities maybe a result of multicollinearity, in which one seemingly unrelated model with high coefficient may also affect other models. However, when comparing the lasso model against the ridge model, the lasso model seems to produce variables with high coefficients that are more sensible as opposed to the ridge model. It is still unclear why roof material ('roof_matl') tops the ridge model coefficient charts. 

The Lasso Model may have been more effective in this determining housing prices from the datasets, given that alot of the variables given have high correlation with each other (as demonstrated in the heatmap above). The Lasso Model does well in eliminating variables that have multicollinearity, as opposed to the Ridge Model which only seeks to minimize it. This is supported by the fact that the ElasticNet Model optimized in a way where only the Lasso Model portion remains.

To sum up, the initial linear regression model fared worse off in R-Squared score and RMSE when modelled against the trained dataset compared to Ridge and Lasso. However, when predicting values for the kaggle test dataset, it managed to obtain RMSE scores similar to that of the Ridge and Lasso, even faring slighly better. This may suggest that regularization should not be used in its entirety when it comes to predicting models. Regularization should be used to assist us in feature engineering and ultimately, expertise and intrisic human knowledge is still needed to identify which factors are the most important. 


## Further Research

The datasets given only cover attributes pertaining to the features of the house. In order to accurately valuate the price of a house, other external factors must also be taken into consideration, such as:
- Population and demographics of people within the neighbourhood 
- Surrounding amenities and facilities in the neighbourhood 
- Transport Accessibility 
- Economic Indicators (e.g. GDP, YoY-Growth)
- Interest Rates 

All these other factors contribute to the supply and demand of the housing market, the main forces that drive housing price. Simply put, if there is more demand than supply, prices will rise and vice versa. 
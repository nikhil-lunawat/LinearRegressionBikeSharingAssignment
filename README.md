# Bike Sharing Case Study
> Build a multiple linear regression model for the prediction of demand for shared bikes. A bike-sharing system is a service in which bikes are made available for shared use to individuals on a short term basis for a price or free.

> Objective is to understand the demand for shared bikes to cater people's need and stay ahead of competition to make huge profit.

> Perform EDA analysis, build regression model and predict output on the driving factors (or features) behind bike rentals. This knowledge can be utilised by management to understand how demands vary with different features to manipulate business strategies and meet the demand levels.

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)

## General Information
- Import required libs and load data set
- Data cleanup, manipulation, filtering and conversion to correct data types
- Perform Exploratory Data Analysis (EDA)
- Pre-processing before building model
    - Creation of dummy variables
    - Splitting data set in training and test data
    - Feature scaling
- Build Linear regression model
    - Use RFE to select significant features in automated way
    - Select fetures manually based on p-value and VIF score
- Check model assumptions
- Predict output on test data
- Model evaluation

## Technologies Used
Project is executed on Ubuntu 22.04

- Jupiter notebook
- Python 3.10.x

#### Libraries used and their versions
Please install below libs before executing notebook

- matplotlib 3.9.x
- seaborn 0.13.x
- scipy 1.14.x
- statsmodels 0.14.4
- scikit-learn 1.5.2

## Conclusions
The above analysis and model on bike renting gives below data points-

### EDA Summary
- 'temp', 'atemp' looks like having linear relationship with output variable count from pairplots
- 2019 year have higher number of bike rentals than 2018 and for every other combined category
- In case of holiday, bike rentals is lower than non holiday. Possible that people might prefer spending time with family or choosing other options for outings.
- Fall season having highest while spring season having lowest bike rentals
- Clear weather having highest while light rain having lowest bike rentals
- September month having highest bike rentals
- Day of week doesn't seem to have any effect on bike rentals

### Model Evaluation summary
- Train data set R2          : 0.83
- Train data set Adjusted R2 : 0.83 
- Test data set R2           : 0.80
- Test data set Adjusted R2  : 0.79
- R2 and Adjusted R2 scores more than 0.8, hence 80% variance can be explained by the model, which is pretty good
- On test data, R2 and Adj R2 is ~0.8 which is very close to actual model, which explains that model is not over fit.
- Prob (F-statistic) is very low, which shows that overall significance level of model is high
- Error term mean is 0 on both training and test data
- Error term is having normal distribution on both training and test data
- Error terms are independent of each other from the pattern on both training and test data
- Homoscedacity is checked against temperature and windspeed continuous variables. Variance of error terms doesn’t seem to be changing with change in predictor variable
- In final model, we were able to select 10 features which is not very high and not so complex as seen by Adjusted R2 score. Removed high p value features and high VIF score features one by one. Hence multicollinearity doesn't exist in last model
- All p values of features are less than 0.05 (5%), hence individual features are also significant. Feature like "Sat" day of the week is removed based on p-value.
- VIF score is less than 5, hence multicollinearity doesn't exist in final model
- Bike renting equation can be created like
  - count = 0.2 + 0.233 * year - 0.098 * holiday + 0.491 * temp - 0.148 * windspeed - 0.067 * spring season + 0.045 * summer season + 0.083 * winter season - 0.285 * light_rain weathersit - 0.082 * misty weathersit + 0.077 * Sep month
  - Which means temperature, year, (light rain, misty) weather conditions, (spring, summer, winter) season, wind speed, holiday and Sep month can impact bike renting significantly. Some features are impacting output positively while some impacting negatively.
  - Year shows that bike renting has increased YoY basis.
  - Temperature is the most impacting feature for bike renting.

## Acknowledgements
Project is done by

- Nikhil Lunawat

## Contact
Created by [@nikhil-lunawat] - feel free to contact me!

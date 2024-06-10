---
title: "Project - Phase IV"
date: 2024-06-09
draft: false
description: "Phase Four of our Dialouge Project "
slug: "phase4post"
tags: ["authors", "config", "docs"]
authors:
  - "carson_hunter"
  - "dylan_sacks"
  - "ivy_jordan"
showAuthorsBadges : false
---

{{< katex >}}

# Model 1
We, as a team initiated this project by searching for the most detailed datasets we could find and brainstorm how they could be used. After working together to come up with applications for the extensive UNHCR dataset about immigration, we began with data visualizations to view possible trends as inspiration for our ML model. We viewed the correlates of features included in the dataset such as year, gender, and country of asylum which fit to a linear regression model. 

This shortly evolved to an exponential regression model due to the seemingly exponential trend over time in some of the data visualizations that were used as a proof of concept for the regression model.
<img src = "https://i.imgur.com/hOvzYWt.png"/>

The model outputs outputs the predicted number of applicants expected to seek asylum given the country of asylum (where they're migrating to), gender, year and their age group[(0-4), (5-11), (12-17), (18-59), (60+)]. The overall intention was to create this product to be used by migration officials such as Tanya Brakcer from our initial user archetype to better understand and predict the age group demographic immigrating to new countries in order to effectively allocate school budgets. 

After the demographics dataset was loaded and cleaned by removing unnecessary or repeated columns, the pandas function df.melt was used to change the dataframe from a long to wide format. This essentially created a row for each instance of the counts in the multiple age group columns, combining those separate columns into one age group column. Each row now had a unique combination of year, country of asylum, age group, gender and number of people who fit that exact demographic. Because we decided this should be an exponential model, the log of that number was taken after adding 0.0001 to include the rows that had a number of 0 given the zeroes (No 0-4 females applied for asylum to Afghanistan in 2010). 

The pandas function get_dummies() was used to assign the rows dummy variables. This changed countries column to give each unique country a column (increasing the number of columns by about 200). Every country in the row has a 0 other than a 1 for the country that the row is referencing:

<img src = "https://i.imgur.com/dF61YfU.png"/>

This was done to use the resulting matrix (that now only had integers but retained all the desired information) could be used to manually train the model. The X-values(predictors) and y(number of applicants) were assigned and a bias column was added to the predictors. The coefficients were then calculated using the normal equation \\( b = (X^T X)^{-1} X^T y \\) , and predications were calculated by multiplying the coefficients matrix by the X matrix, and residuals were calculated by subtracting the difference in predicted versus actual values.  

The model was firther checked by calculating r2, mse. A Q-Q and residuals vs predicted values was completed to view the model success. Unfortunately, the rows with zeroes greatly affected the model as outliers, and brought the slope down greatly. This can be seen in the following graph by the outlier line below 0:

<img src = "https://i.imgur.com/tk1XOsZ.png">

This function was then written to be able to make and call the unique X matrix of 1 and 0 containing information for year, country (array of all zeroes other than a 1 for desired country in the same order as the final dataframe the model was trained on), gender (1 for male, 0 for female), and age (array of zeroes other than the specific age group in the same order model was trained on)to be used for future predicitons. This is called one-hot encoding, and is very common for training ML models:
<img src = "https://i.imgur.com/laPBZcS.png">

The fucntion can then be used to output the following:

<img src = "https://i.imgur.com/LRCaVgL.png">

A bias column was then added to this resulting matrix, accomodating for the y-intercept, of which the dot product with the coefficient matrix was taken. The resulting output was then bakctransformed by applying the exponential function due to the log-transformed data from the beginning of the data manipulation. 


# Model 2
The pipeline leading to the implementation of the second model began similarly to the first by deciding on a linear regression model to predict the acceptance rates for countries of asylum given the year, country of origin, and total applications based on extensive data visualizations that occured after manipulating the dataframes:

<img src = "https://i.imgur.com/P9gbnJY.png">
This was one of the correlation matrices used to come up with some of the idea behind the second model. 

Cleaning the data and adding a column for acceptance rate by dividing number of acceptances by total applications resulted in the following:

<img src = "https://i.imgur.com/PsnXH0N.png">

The country id's were used instead of country names because the randomforests regression model produced an error when countries were strings. The dataset used had each country both as a string and indexed so making this change was extremely easy, the columns of strings simply were swapped with the column of indexed countries. 

After importing randomforests regression libraries, defining the X features as year, country of origin, country of asylum, and total applications, and dependent variable as acceptance rate, the data were split into training and testing sets.

The model was then trained and fit by calling the randomforestsregressor() .fit() functions. Predictions were made using the .predict() function. An advantige to this model was that randomforests does not calculate predictions the same way model 1 did manually. Instead of using matrices, it builds many decision trees with slight variations based on the unique subset of data it's trained on. Outputted predictions are then given by taking the average from all the trees from the training data. This has advantages and disadvantages, such as fewer assumptions regarding the data (doesn't have to be linear), while also having less troubleshooting capabilities if an output looks incorrect.

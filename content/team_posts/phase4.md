---
title: "Project - Phase IIII"
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
# Model 1
We, as a team initiated this project by searching for the most detailed datasets we could find and brainstorm how they could be used. After working together to come up with applications for the extensive UNHCR dataset about immigration, we began with data visualizations to view possible trends as inspiration for our ML model. We viewed the correlates of features included in the dataset such as year, gender, and country of asylum which fit to a linear regression model. 

This shortly evolved to an exponential regression model due to the seemingly exponential trend over time in some of the data visualizations that were used as a proof of concept for the regression model.
<img src = "https://i.imgur.com/hOvzYWt.png"/>

The model outputs outputs the predicted number of applicants expected to seek asylum given the country of asylum (where they're migrating to), gender, year and their age group[(0-4), (5-11), (12-17), (18-59), (60+)]. The overall intention was to create this product to be used by migration officials such as Tanya Brakcer from our initial user archetype to better understand and predict the age group demographic immigrating to new countries in order to effectively allocate school budgets. 

After the demographics dataset was loaded and cleaned by removing unnecessary or repeated columns, the pandas function df.melt was used to change the dataframe from a long to wide format. This essentially created a row for each instance of the counts in the multiple age group columns, combining those separate columns into one age group column. Each row now had a unique combination of year, country of asylum, age group, gender and number of people who fit that exact demographic. Because we decided this should be an exponential model, the log of that number was taken after adding 0.0001 to include the rows that had a number of 0 given the zeroes (No 0-4 females applied for asylum to Afghanistan in 2010). 

The pandas function get_dummies() was used to assign the rows dummy variables. This changed countries column to give each unique country a column (increasing the number of columns by about 200). Every country in the row has a 0 other than a 1 for the country that the row is referencing:
<img src = "https://i.imgur.com/dF61YfU.png"/>

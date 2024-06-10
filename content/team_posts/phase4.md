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

## Software Architecture

After our team generated both machine learning models, we began to implement them into the software as described by our user stories. After making decisions feasability, ease of use, and availability of data, we decided to make final edits to our personas and their resulting stories: 

# User Stories 
Jackson retains his position as a senior immigration official for a government entity. His user stories change as follows: 

a) "As an immigration official, I want to be able to view the general population for  various countries so I can determine if there are adequate resources to accept asylum applications and compare other country populations to my own."

b) "As an immigration official, I want to be able predict the number of applicants for a given age group, gender, country of asylum, and year.

c) "As an immigration official, I want to be able to predict a country's asylum application rate based on a given country of origin, year, and total number of applications. 

Hugo retains his identity as a migrant in a new city looking to access community resources. His user stories also remain from phase 2. 

Tanya also keeps her position as the head of refugee affairs for her city council looking to manage and coordinate refugee resources. Her user stories change as follows: 

a)"As an urban development planner, I want to organize community events to support the refugee population so that we can build better relationships between refugees and citizens of the city." 

b)"As an urban development planner, I want to coordinate appointments with refugee population representatives to address their needs and concerns so that we can better improve refugees’ quality of life during their time in my city."

c)"As an urban development planner, I want to oversee a community bulletin board, with the ability to moderate and delete comments. 

# Data Model

Based on our user stories we generated a final data model: 

This data model ensures all users will be able to achieve their desired goals. 

# Landing
 
Upon entrance to the page, the user has the option to select one of the personas as outlined above. 

# Jackson Davies 

When the user logs in to the Jackson Davies archetype, they are greeted and given a list of tasks to do. These tasks do not actually interact with the database, but instead are just front in features. 

The first thing the user can do is predict the number of applications to a given country of asylum based on a given year, gender, and age group. When the user submits, their inputs are stored as arrays and the api calls the beta values for the regression model from the database. The two values are multiplied an expected number of applcations is outputted. 

In the next page, the user can predict asylum application acceptance rate for a given country of origin, country of asylum, year, and number of total decisons. When the user submits, a random forest classifier runs via an api call and returns an ecpected acceptance rate. In the front end, the acceptance rate is rounded and converted to a percent. 

The user can also access a table of population statistics for a given country through an api call to the values stored in the database. 

# Hugo Diallo

When the user enters the Hugo Diallo session state, they are greated by a list of areas to navigate to. 

"Appointment Book" Returns a list of all the appointments for the given user (their id has been authenticated upon login). 

The user can also select a weekday and view appointments which fall during that weekday. These appointments are similar to a "DMV" style appointment system, where a certain number of users can reserve a spot and the actual appointments come "first come first serve" style. They can also cancel appointments they are signed up for. 

The user can also view a list of community events through a GET call to the database. 

Finally the user can add posts to a bulletin style message board where they set a display name and content of their post. The user does not have the ability to edit or delete their posts. 

# Tanya Bracker
When the user logs in as Tanya Bracker, they land on a page of upcoming events. 

"Manage Community Events" takes the user to a page where they get a more detailed view of the events, showing things like duration, venue capacity. The user can create new events where they specify the name, duration in hours, date, and venue capacity. They can also edit and cancel events, which is reflected application wide. 

The user can also delete and edit posts that the migrants make as a moderator/administrator of the bulletin board. 

Finally, the user can scheudle, cancel, and delete appointment slots, which is also reflected application wide. 
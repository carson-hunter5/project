---
title: "Project - Phase III"
date: 2024-06-05
draft: false
description: "Phase Three of our Dialouge Project "
slug: "phase3post"
tags: ["authors", "config", "docs"]
authors:
  - "carson_hunter"
  - "dylan_sacks"
  - "ivy_jordan"
showAuthorsBadges : false
---

# Data Model Modifications and Updates
The ML model from phase 1 was completely scrapped for a variety of reasons, including a lack of impact the output would have on the user. The new model uses exponential regression (reasoning discussed below) to output the predicted number of immigrants expected to apply for asylum to a given country in a given year. This was used on a different dataset from the same API. 

Below is the list of tables that we have currently and whether or not this data will be sourced or generated via mockaroo: 

## Appointments

  Source: Generated via Mockaroo

  Description: Contains appointment details for users and volunteers.

## AttendeeEvents

  Source: Generated via Mockaroo

  Description: Records of events attended by users and volunteers.

## CommunityEvents

  Source: Generated via Mockaroo

  Description: Information about various community events organized for or involving users and volunteers.

## Countries

  Source: Sourced

  Description: List of countries and their details.

## CountryStats

  Source: Sourced

  Description: Statistical data related to countries, including population and asylum application statistics.

## Dependents

  Source: Generated via Mockaroo

  Description: Information about dependents of users

## ## Posts

  Source: Generated via Mockaroo

  Description: User-generated posts and related information.

## RefugeeCohort

  Source: Sourced

  Description: Details and statistics about refugee cohorts.

## Users

  Source: Generated via Mockaroo

  Description: User profiles including personal information and relevant attributes.

## Volunteers

  Source: Generated via Mockaroo
  
  Description: Profiles of volunteers.



# Dataset
<img src = "https://i.imgur.com/HOojKct.png">
This is the dataset used to train the exponential regression model, taken from <a href="https://icr.ethz.ch/data/epr/er/" target="_blank" >the same API</a> used in phase 2. This dataset, however, gives information regarding the age and gender demographics of asylum seekers from 2010-2022 as opposed to the varying types of immigration applications used in phase 2. The advantage to this change in dataset was that the user archetypes discussed in phase 2 would likely have greater affinity to the predictive output generated to this dataset. For example, Tanya Bracker could use the information about the demographics surrounding asylum seekers to better allocate funds for schools (just one of many real world examples). Because these data are from a <a href="https://en.wikipedia.org/wiki/Open_API" target="_blank" >public API</a>, they are sourced, and not generated.

<img src = "https://i.imgur.com/tk1XOsZ.png">
This graph depicts the residuals of the exponential regression. There is clearly heteroscedasticity, exemplified by the lack of residuals randomly scattered around zero, an indicator of homoscedasticity. A future improvement for this model which will be investigated shortly is a box-cox transformation. This was ultimately hypothesized as a possible solution for the relatively poor model outcomes after viewing a Q-Q plot to investigate the distribution of residuals.

<img src = "https://i.imgur.com/eCMxirt.png">
This plot is detailing that the residuals appear to be non-normally distributed. Because this is an indicator of poor model fitting, a box-cox transformation will be performed as an attempt to normalize the distribution of residuals.

# Features used for ML and reasoning
Country of Asylum (coa): Demographic patterns can differ significantly between countries. Including this variable enables the model to give more accurate information which is subjective to a specific country.

Year : Demographic patterns can change over time due to factors like economic conditions, political instability, conflicts, and policy changes. The model should capture these temporal changes to make accurate future predictions.

Age: Age is a critical demographic factor that influences health care needs, educational requirements, and economic participation. Breaking down the population into age groups allows the model to capture differences in demographic profiles and needs across various age brackets.

Gender: Gender is a fundamental demographic factor that can affect migration patterns, health needs, and social vulnerabilities. Including gender allows the model to differentiate demographic patterns between males and females.

# API Routes and Explanations

## City Council API Routes

GET /city_council
    Purpose: Retrieve all community events from the database.

POST /council_add_event
    Purpose: Create a new community event.

PUT /city_council/communityEvent
    Purpose: Update an existing community event.

DELETE /city_council/communityEvent/<eventID>
    Purpose: Delete a specific community event based on its event ID.

GET /city_council
    Purpose: Retrieve all appointments from the database.

GET /city_council/<cohortID>
    Purpose: Get demographics for a specific cohort of refugees.


DELETE /city_council/delete_bulletin/<post_id>
    Purpose: Delete a specific bulletin post based on its post ID.

GET /city_council/bulletin
    Purpose: Retrieve all bulletin posts. 

## Migrant API Routes 
GET /migrant/appointments/<migrantID>
    Purpose: Retrieve all appointments from the database for a specific migrant.

GET /migrant/show_appt/<apptID>
    Purpose: Retrieve a specific appointment based on its appointment ID.

POST /migrant
    Purpose: Create a new appointment for a migrant.

PUT /migrant/appointment
    Purpose: Update the appointment details for a specific migrant.

DELETE /migrant/appointment_delete/<appointmentID>
    Purpose: Delete a specific appointment based on its appointment ID.

GET /migrant/posts
    Purpose: Retrieve all posts from the database.

GET /migrant/<migrantID>
    Purpose: Retrieve a specific migrant's posts based on their migrant ID.

POST /migrant/add_post
    Purpose: Create a new post for a migrant.

PUT /migrant/post
    Purpose: Update a specific post for a migrant.

DELETE /migrant/post/<postID>
    Purpose: Delete a specific post based on its post ID.

GET /migrant/events
    Purpose: Retrieve all community events from the database.


## Immigration Official API Routes 

  GET /immigration_official/population
    Purpose: Retrieve the population from the database based on countryID.

  GET /immigration_official/countryStats
      Purpose: Retrieve all country statistics from the database.

  POST /immigration_official/newStat
      Purpose: Create a new country statistic entry.

  PUT /immigration_official/editCountryStat
      Purpose: Update an existing country statistic.

  DELETE /immigration_official/deleteCountryStat
      Purpose: Delete a country statistic entry based on countryID.

  GET /immigration_official/numApplications
      Purpose: Retrieve the number of applications for a specific country in a given year.

  GET /immigration_official/applicationTrends
      Purpose: Retrieve the overall trend of applications for a specific country in a given year.

# Surprises/setbacks
The main difficulty when designing this model was that the linear regression model (to put it bluntly) was terrible. The r2 value was 0.02, and the mse was over 10,000,000. The idea of trying exponential regression came due to the intuition of Dr. Gerber after observing the appearance of an exponential slope in a comparable graph conducted as a proof of concept in the phase 2 blog post:
<img src = "https://i.imgur.com/hOvzYWt.png"/>

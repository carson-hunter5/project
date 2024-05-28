---
title: "Project - Phase II"
date: 2024-05-21
draft: false
description: "Phase Two of our Dialouge Project, in which we focused on developing our app’s data model and sourcing the ML-models data to perform some exploratory data analysis."
slug: "phase2post"
tags: ["authors", "config", "docs"]
authors:
  - "carson_hunter"
  - "dylan_sacks"
  - "ivy_jordan"
showAuthorsBadges : false
---

# Updates and Changes from Phase I

After our first initial round of feedback, we decided to implement a few changes from the original blogpost. The first change being the user stories to be properly formated: 

As a ____, I wnat to ___ so that _____ . 

## User Stories and Personas

**Immigration Focused Entities: Jackson Davies is a field officer with USCIS who has experience facing sudden surges in immigration applications, leading to delays and inefficient processing.**

a) As a field officer, I want to allocate resources needed populations within a targeted area of the United states so that I can correlate certain areas are more subject to more migration than others.

b) As a field officer, I want to efficinetly manage immigration applications and anticipate where an influx of groups may arise so that I can show the correlation during a time of crisis based on historical context. 

c) As a field officer, I want to be able to coordinate with other immigartion enities so that policies and regulations on immigration are based on the attributes and qualities of migration from certain countries. 

**Relief Groups: Kyle Medina is a data scientist for the UNHCR based in Geneva, Switzerland, who is tasked with overseeing NGO / Red Cross locations which are facing a shortage of supplies in developing countries in the Southern Hemisphere.**

a) As a data scientist, I want to predict migration patterns to nearby asylum seeking countries, so that we can account for the amount of necessary supplies needed for a duration of time.

b) As a data scientist, I want to know which regions that will be prone to an influx of refugees so that we can anticapte the amount of employees/volunteers needed during a given timeframe.  

c) As a data scientist, I want to enhance the efficiency of distribution flow of certain products needed by a certain group of refugees such as women vs men, and children vs elderly groups.

**Urban Development Planners: Tanya Bracker is a city council member from Utica, New York, a city with a large refugee population, based on the last few years population increase, there will be budget cuts and allocations for more city resources.**

a) As a city council executive, I want to identify the common age demographic levels of refugees so that I know if primary and secondary schools budget allocations will be most effective.

b) As a city council executive, I want to  anticipate and manage the housing needs for incoming refugees by predicting which regions are likely to send more refugees so that we can prevent housing shortages.

c) As a city council executive, I want to plan for and improve public transportation routes and schedules so that we can better serve areas with high refugee populations. 

**Data Visualizations**
[Asylum Applications to USA](https://imgur.com/a/e4bCMg3)
This graph is depicting the change in immigration application requests from around the world sent to the United States over time. The size of the mark is proportional to the number of immigration applications sent, and the different countries are designated by varying colors. This graph indicates that the number of asylum applications has been increasing since 2010, the beginning of our dataset. This applies to our larger interest in predicting the number of refugees travelling to a specific country over time, directly applying this question to the United States. According to these data, the quantity of applications sent to the US per year has been booming since 2022, with huge outliers as well. Jackson Davies would be able to use this visualization to better manage immigration applications and anticipate where an influx of groups may arise.

[Age Demographics](https://imgur.com/hOvzYWt)
This graph shows the age demographics of applicants seeking asylum per year. There is clearly an increase in the number of 18-59, and 5-11 year old males and females in the past 7 years. It is interesting that the second greatest increase in applications by age group appears to 5-11 year olds, as it would be expected to be either the age demographic immediately before 18-59 year olds. This graph could be used by someone such as Tanya Brakcer to understand and predict the age group demographic immigrating to new countries in order to effectively allocate school budgets. 

[ML Model POC](https://imgur.com/uHC5CB7)
This linear regression model is comparing the asylum applications sent to the United States over time from all countries over time. The challenge surrounding this preliminary model was mainly that the x-values being years are a disctrete value while the y-value representing applications is continuous. Although this is not ideal for an ML model, it is sufficient as a proof of concept that can be ratified by implementing other variables such as applications from specific global areas, which would reveal more information and contribute to the overall question of predicting future asylumn applications. The next step for this model is to use it to predict future values of applications sent to the U.S.

[Global Asylum Applications](https://imgur.com/undefined)
This graph depicts the global asylum applications by year for every country of origin. The data are interesting as they indicate global conflicts, such as a large outlier of asylum applications coming from Ukraine to Russia in 2014. This graph could be used by someone such as Kyle Medina to predict which regions might experience an influx of asylum seekers to efficiently allocate resources such as aid. This can be used to answer the major question whihc sparked this project of "Where are populations likely to move during major conflicts/crises?".

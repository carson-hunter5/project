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

As a ____, I want to ___ so that _____ . 

We also received feedback that we should focus much more heavily on the software application portion of the project. Though we generated many different ideas for data analysis, it was important to incorporate features into our application that didn’t exclusively rely on data analysis. We decided to incorporate different uses into the application that were focused in the area of assisting migrant populations. 

## User Stories and Personas

**Immigration Focused Entities: Jackson Davies is a senior official at his country’s immigration bureau who has experience facing sudden surges in immigration applications, leading to delays and inefficient processing.**

a) "As an immigration official, I want to be able to predict the general population for the country so I can determine if there are adequate resources to accept asylum applications."

b) "As an immigration official, I want to be able to view past trends in asylum applications so I can determine if numbers of applications are likely to rise or fall." 

c) "As an immigration official, accepting or denying an application for asylum can be very political. I also want to be able to view trends in asylum decisions so I can objectively show the state of immigration to the country."


**Refugees: Hugo is a refugee from Guinea, who has recently been displaced and moved to a new European city with a large refugee population. It’s been a few months and he is concerned as to how he is supposed to support his family and doesn’t know what he needs to do in order to get certain resources.**

a) "As a refugee, I want to schedule appointments with city service providers so that I can access necessary resources and support."

b) "As a refugee, I want to be able to post to a public bulletin that allows me to interact with other members of my community." 

c) "As a refugee, I want to view upcoming community events so that I can participate and integrate into the community."


**Urban Development Planners: Tanya Bracker is a city council member from Utica, New York, a city with a large refugee population, based on the last few years population increase, there will be budget cuts and allocations for more city resources.**

a)"As an urban development planner, I want to organize community events to support the refugee population so that we can build better relationships between refugees and citizens of the city." 

b)"As an urban development planner, I want to meet with refugee population representatives to address their needs and concerns so that we can better improve refugees’ quality of life during their time in my city."

c)"As an urban development planner, I want to analyze demographic data to enhance city infrastructure for refugees so that we can improve specific infrastructures most used and impacted by refugees."


**Data Visualizations**
<img src = "https://i.imgur.com/TDNNZUF.png"/>

**Asylum Applications to USA**

This graph is depicting the change in immigration application requests from around the world sent to the United States over time. The size of the mark is proportional to the number of immigration applications sent, and the different countries are designated by varying colors. This graph indicates that the number of asylum applications has been increasing since 2010, the beginning of our dataset. This applies to our larger interest in predicting the number of refugees travelling to a specific country over time, directly applying this question to the United States. According to these data, the quantity of applications sent to the US per year has been booming since 2022, with huge outliers as well. Jackson Davies would be able to use this visualization to better manage immigration applications and anticipate where an influx of groups may arise.


<img src = "https://i.imgur.com/hOvzYWt.png"/>

**Age Demographics**

This graph shows the age demographics of applicants seeking asylum per year. There is clearly an increase in the number of 18-59, and 5-11 year old males and females in the past 7 years. It is interesting that the second greatest increase in applications by age group appears to 5-11 year olds, as it would be expected to be either the age demographic immediately before 18-59 year olds. This graph could be used by someone such as Tanya Brakcer to understand and predict the age group demographic immigrating to new countries in order to effectively allocate school budgets. 

<img src = "https://i.imgur.com/4TdiS6U.png">

**ML Model POC** 

This linear regression model is comparing the asylum applications sent to the United States over time from all countries over time. The challenge surrounding this preliminary model was mainly that the x-values being years are a disctrete value while the y-value representing applications is continuous. Although this is not ideal for an ML model, it is sufficient as a proof of concept that can be ratified by implementing other variables such as applications from specific global areas, which would reveal more information and contribute to the overall question of predicting future asylumn applications. The next step for this model is to use it to predict future values of applications sent to the U.S. This model has a slope of 95.18, meaning that every year 95.18 more people apply for asylum than the previous year.

<img src = "https://i.imgur.com/NF08BZZ.png"/>

**Global Asylum Applications**

This graph depicts the global asylum applications by year for every country of origin. The data are interesting as they indicate global conflicts, such as a large outlier of asylum applications coming from Ukraine to Russia in 2014. This graph could be used by someone such as Kyle Medina to predict which regions might experience an influx of asylum seekers to efficiently allocate resources such as aid. This can be used to answer the major question whihc sparked this project of "Where are populations likely to move during major conflicts/crises?".

# Localized ER Diagrams for User Archetypes 

**Government Immigration Focused Entities**
<img src = "https://i.imgur.com/5lv14AN.png">


**Refugee Entities**
<img src = "https://i.imgur.com/0sxPRK2.png">


**Urban Development and Planning Entities**
<img src = "https://i.imgur.com/0SvOeaM.png">


**Global ER Diagram**
<img src = "https://i.imgur.com/LJgbUFF.png">


# SQL DDL for Global Data Model
**SQL Query**

<img src = "https://i.imgur.com/lIUu9yd.jpeg">

**SQL Pop-Up Diagram**

<img src = "https://i.imgur.com/zOUWTg6.png">


# Draft Wireframes of POC

<img src = "https://i.imgur.com/weeldsa.png">
<img src = "https://i.imgur.com/PM8JtmZ.png">
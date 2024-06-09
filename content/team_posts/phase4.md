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
We, as a team began this project by finding the most detailed datasets we could find and brainstorm how they could be used. After working together to come up with applications for the massive UNHCR dataset about immigration, I began with data visualizations to view possible trends as inspiration for our ML model. After viewing the correlates of features such as year, country of asylum, and country of origin, and discussing with the rest of the group, we settled on making a model using linear regression to predict the age group demographics of asylum applicants based on the year, their country of origin, country of asylum, and age group

Our first model is an exponential regression model which outputs the predicted number of applicants expected to seek asylum given the country of asylum (where they're migrating to) and their age group[(0-4), (5-11), (12-17), (18-59), (60+)]. The overall intention was to create this product to be used by migration officials such as Tanya Brakcer from our initial user archetype to better understand and predict the age group demographic immigrating to new countries in order to effectively allocate school budgets. 
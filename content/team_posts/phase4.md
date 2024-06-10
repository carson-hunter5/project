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
We, as a team initiated this project by searching for the most detailed datasets we could find and brainstorm how they could be used. After working together to come up with applications for the extensive UNHCR dataset about immigration, we began with data visualizations to view possible trends as inspiration for our ML model. We viewed the correlates of features included in the dataset such as year, country of asylum, and country of origin which fit to a linear regression model. This model predicted the age group demographics of asylum applicants based on year, their country of origin, country of asylum, and age group

Our first model is an exponential regression model which outputs the predicted number of applicants expected to seek asylum given the country of asylum (where they're migrating to) and their age group[(0-4), (5-11), (12-17), (18-59), (60+)]. The overall intention was to create this product to be used by migration officials such as Tanya Brakcer from our initial user archetype to better understand and predict the age group demographic immigrating to new countries in order to effectively allocate school budgets. 
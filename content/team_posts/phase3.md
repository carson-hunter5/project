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

# Data Model Modifications
The ML model from phase 1 was completely scrapped for a variety of reasons, including a lack of impact the output would have on the user. The new model implemented. The new model uses exponential regression (reasoning discussed below) to output the predicted number of immigrants expected to apply for asylum to a given country in a given year. This was used on a different dataset from the same API. 

# Dataset
<img src = "https://i.imgur.com/HOojKct.png">
This is the dataset used to train the exponential regression model, taken from <a href="https://icr.ethz.ch/data/epr/er/" target="_blank" >the same API</a> used in phase 2. This dataset, however, gives information regarding the age and gender demographics of asylum seekers from 2010-2022 as opposed to the varying types of immigration applications used in phase 2. The advantage to this change in dataset was that the user archetypes discussed in phase 2 would have a greater affinity to the predictive output generated to this dataset. For example, 


# Features used for ML 
# Surprises/setbacks
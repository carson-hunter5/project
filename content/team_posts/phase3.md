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
The ML model from phase 1 was completely scrapped for a variety of reasons, including a lack of impact the output would have on the user. The new model uses exponential regression (reasoning discussed below) to output the predicted number of immigrants expected to apply for asylum to a given country in a given year. This was used on a different dataset from the same API. 

# Dataset
<img src = "https://i.imgur.com/HOojKct.png">
This is the dataset used to train the exponential regression model, taken from <a href="https://icr.ethz.ch/data/epr/er/" target="_blank" >the same API</a> used in phase 2. This dataset, however, gives information regarding the age and gender demographics of asylum seekers from 2010-2022 as opposed to the varying types of immigration applications used in phase 2. The advantage to this change in dataset was that the user archetypes discussed in phase 2 would likely have greater affinity to the predictive output generated to this dataset. For example, Tanya Bracker could use the information about the demographics surrounding asylum seekers to better allocate funds for schools (just one of many real world examples). Because these data are from a <a href="https://en.wikipedia.org/wiki/Open_API" target="_blank" >public API</a>, they are sourced, and not generated.


<img src = "https://i.imgur.com/tk1XOsZ.png">
This graph depicts the residuals of the exponential regression. There is clearly heteroscedasticity, exemplified by the lack of residuals randomly scattered around zero, an indicator of homoscedasticity. A future improvement for this model which will be investigated shortly is a box-cox transformation. This was ultimately hypothesized as a possible solution for the relatively poor model outcomes after viewing a Q-Q plot to investigate the distribution of residuals.
<img src = "https://i.imgur.com/eCMxirt.png">
This plot is detailing that the residuals appear to be non-normally distributed. Because this is an indicator of poor model fitting, a box-cox transformation will be performed as an attempt to normalize the distribution of residuals.

# Features used for ML 

# Surprises/setbacks
The main difficulty when designing/fitting this model was that the linear regression model (to put it bluntly) was terrible. The r2 value was 0.02, and the mse was over 10,000,000. The idea of trying exponential regression came due to the intuition of Dr. Gerber after observing the appearance of an exponential slope in a comparable graph conducted as a proof of concept in the phase 2 blog post:
<img src = "https://i.imgur.com/hOvzYWt.png"/>

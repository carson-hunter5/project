---
title: "Individual Blog Post 4"
date: 2024-06-09
draft: false
description: "The last one"
slug: "phase4individualpost"
tags: ["authors", "config", "docs"]
authors:
  - "dylan_sacks"
showAuthorsBadges : false
---

# Final Blog Post
I'd like to start this final blog post by emphasizing just how impactful this final project has been to top off this amazing dialogue experience. There was something unique about the appreciation I gleaned with regards to data science/statistics after spending half my day nesarly everyday learning about data science. Being immersed in such an interactive classroom bred the ideal combination of attitude and confidence to handle my portion of this final project, which was the perfect way to apply everything I've worked on the past few weeks in DS 3000 and solidify that knowledge to an applicable topic that can have a tangible impact.

I thoroughly enjoyed the process of transcribing the skills that I aquired from class to a project of my own choosing. It felt analogous to switching from multiple choice to free response where anything was possible as oppsoed to simply answering the questions from classwork and homework. I would be lying to say I was never hesitant about how I would fare being the only DS 3000 student in my group. This brief lack in self-confidence was shrot lived, however. Once I got on a roll and saw my own successes I began to relax and focus more on what I was doing rather than how well I was doing it. 

I handled beginning this project with the data visualizations of the datasets that we found as a group surrounding immigration statistics. I created several different graphs and tables to inspect possible applications that could be gleaned from our manipulated data.

<img src = "https://i.imgur.com/bcOawml.png">

<img src = "https://i.imgur.com/YDswxAi.png">
This was my favorite part of the project. Using such a large dataset to view different trends felt like there were endless possibilities and applications we could use our data for given all the manipulations and interpretations that could be made from those manipulations.

Following these visualizations, I performed linear regression using matrix manipulation based on the mathematical reasoning behind regression to view the relationship between applications and the features previously mentioned. 

<img src = "https://i.imgur.com/TG2xFcD.png">

This model did not look promising. After discussing with Dr. Gerber, we decided to fit an exponential model as opposed to linear, given the appearance of the points in the first visualization graph (Asylun appplications to USA). After implementing this model, the predictions were not very accurate. I looked at implementing a box-cox transformation, however after correcting the mistake of adding a 1 to all the values before taking the log by changing it to a 0.001, the Q-Q plot no longer showed as severe of a deviation in the residuals line indicating skewed residual distribution. The most difficult part of this project was dealing with the possible changes to this model. There were about 5 changes made to this model before settling on one that in my opinion could use a lot of work before being as accurate and thus impactful as it could be. Not to say it is not succesful, it is certainly a proof of concept that 'works', but it shows a lot of promise in an area that needs insurmountable help that could help millions of people. Additionally, the constant changing of the model was time consuming, and frustrating. However, I'm glad that it went exactly as it did because it was a learning experience, and simply how model implementation works.

After finishing this model, I used randomforests classifier to make a model predicting country of origin given the year, country of asylum, age group demographic, and number of applications. 

<img src = "https://i.imgur.com/vHDgdFV.png">

This model had a lot of promise and would strongly support the user archetypes we created at the beginning of the project. However, this model was ultimately trashed due to low success rate and personal preference for a third model I created using randomforests linear regression to predict the acceptance rate of a country given the year, country of origin, country of asylum, and total applications.

<img src = "https://i.imgur.com/fyaTDZ2.png">

I also assisted the database team as best I could to implement the models, such as working in tandem to create functions that could be called from the user in order to calculate the predictions from the model. 

I would include this project on my resume in my extracurriculars section (as a non-cs major) by saying:

Designed and implemented machine learning models in custom app with ability to predict future migration patterns to help migration officials make efficient and better informed decisions.

The project title is "SUBLEVA"
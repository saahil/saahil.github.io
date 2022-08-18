---
layout:     post
title:      Data Quality Metrics for Everybody
date:       2022-08-17 07:00:00
summary:    To solve one of the biggest pains in ML projects, you need to start somewhere - here.  
categories: data technology ai
---
Training the first ML model in a business app is usually driven by extensive experimentation, exploration and, what is essentially, making a lot of reasonable assumptions about what a future user's characteristics are and how they will behave. At inference time, however, nobody should be surprised when these assumptions are violated by reality left, right and centre, and you're left with some pretty tricky scenarios to diagnose and debug. As a starting point for these investigations, which should, ideally, involve feature importances, explanations, and so on, should be a good grip on whether the latest training data, as well as inference-time input meets a basic set of quality measures. 

This article won't go into any business use-case specific assumptions, obviously, but the following are the bare minimum in terms of data quality metrics that you should put in place, and automate, at the end of your ETL pipelines and inference endpoints.  

1. _Null values_: Whether there are missing values in fields where there shouldn't be any. 
2. _Casting of values_: Whether the input data flows in in a format that your casting operations can't handle, e.g. string "1.0" can be cast into floating point, but "1 point something" cannot be. 
3. _Fill rates_: For sparse feature matrices, an overview of column fill rates is important, especially how it has evolved over the time since your model was last trained. 
4. _Timeliness_: If models are trained periodically upon availability of new ground-truth data, then a timeliness check is what allows data scientist to track whether *all the expected data* was updated, and to what degree, at the expected intervals. 
5. _Historical consistency_: As a final check, historical consistency should give an indication of whether any *qualitative* aspects of the data have changed over time, e.g. has a numerical field always been delivering integer values or have the sources been recently delivering floating point values instead - denoting certain new assumptions about the data. 
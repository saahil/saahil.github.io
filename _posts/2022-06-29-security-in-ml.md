---
layout:     post
title:      The AI of Your ML Products Can Also be an Attack Surface  
date:       2022-06-29 11:00:00
summary:    Time to think seriously about security in machine/deep learning
categories: technology ai machine-learning security deep-learning
---

Even though non-ML fields in computer science are swiftly turning into auxiliary and domain-specific machine learning research fields (e.g. look at the number of papers using or addressing machine learning in this year's [International Conference for Software Engineering](https://conf.researchr.org/program/icse-2022/program-icse-2022/Detailed-Table)), the core research in ML and deep learning moves so fast, that it's impossible these days for researchers from other fields to keep track of all the new developments.
Serious researchers, however, have [already](https://ieeexplore.ieee.org/abstract/document/9252851) [started](https://ieeexplore.ieee.org/abstract/document/8474192) [to look](https://ieeexplore.ieee.org/abstract/document/8617013) into an important, but often overlooked aspect due to the speed of new developments, in machine learning systems - _security_. 

Security, in this article, is probably a catch-all for a lot of related but, theoretically speaking, distinct concepts such as robustness, safety, and adversarial-proof machine learning systems. If we use the [artifact-based approach](https://arxiv.org/abs/1806.00098) to software engineering, security for machine learning systems should focus on these main artifacts -

1. Training data
2. Trained models
3. Inference endpoints or APIs

__Training data__, especially when sourced from ELT pipelines and automatically labeled, can be the first source of poisoning if, either meaningful data quality metrics are not set-up and visible (more on this in a later post), or if active-learning is set up where adversarial edge-case inputs are added to the training datasets without correcting the labels first. 

__Trained models__ can further add to the attack surface of an ML-system when it is not updated over the course of business use-case serving, and they _drift_ due to the initial assumptions about the independent variables or problem statements not being valid anymore. Moreover, it can be argued that deep models whose outputs cannot be sufficiently _explained_, can be hard to debug and are a compliance and security liability, in themselves.  

__Inference endpoints__, typically in the form of Rest or GraphQL APIs, may, in addition to being vulnerable to common software vulnerabilities, also be susceptible to being abused by, e.g. training proxy models by attackers or inferring on adversarial inputs.

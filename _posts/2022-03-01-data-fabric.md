---
layout:     post
title:      Most Data Fabrics are Made Of Lead, not Linen
date:       2022-03-01 07:37:00
summary:    Don't let AI-experts scare you out of implementing data integration in your org  
categories: data technology ai
---

Gartner defines Data Fabric as {Gartner definition}. 
It even seems like a sibling to the data virtualization {definition} idea - that proposes a "logical" data layer on top of disparate sources, where data resides in varying formats. 
While most data fabric providers promise the world at the click of a button, it remains the case that most businesses need to use a semantic engine on top of their original sources, in order to run meaningful data analytics. These semantic engines are what ultimately often plug into an org's Data Lake pipelines and feed into the data fabric, that is able to keep the data fresh for quick analytics. 

Creating a domain- or org-specific AI-driven data integration strategy from scratch (and it often _need to be_ from scratch) sounds frightening, especially given how prolific the development in vector-search space has been recently. For D&A teams, this often means top-down mandates and project charters talking about digital transformation, breaking of department-silos, machine learning capabilities, question-and-answer capabilities yada, yada, yada. 

But I'm here to tell you - you've got this. And the reason I say this is because, unlike what the hype tries to make you believe, most data integration layers are built using domain-specific, time-consuming and *heavy* transformations to even bring their original sources to a state that they can index it in a Lucene-based text search engine. And while that might not seem impressive if you're on data management LinkedIn too much, it is enormous when it comes to solving your organization's specific needs and maybe even create new business models. 

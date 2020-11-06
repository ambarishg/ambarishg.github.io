---
layout: post
tags:
- azure-machinelearning
- machinelearning
categories: Azure Machine Learning
title: Azure ML Pipelines
description: Azure ML Pipelines
---

Different types of **pipelines** are

<img src="/img/AzureML/pipelines.PNG">    

In Azure Machine Learning, a pipeline is a workflow of machine learning tasks in which each task is implemented as a step.

* Steps can be arranged `sequentially or in parallel`  
* Each step can be run on a `specific compute target`, making it possible to combine different types of processing as required to achieve an overall goal  
* A pipeline can be executed as a process by running the pipeline as an experiment  
* Each step in the pipeline runs on its `allocated compute` target as part of the overall experiment run.

We can `publish` a pipeline as a REST endpoint, enabling client applications to initiate a pipeline run.  
We can also define a `schedule` for a pipeline, and have it run automatically at periodic intervals.  


*References*  


* [Azure Machine Learning documentation](https://docs.microsoft.com/en-in/azure/machine-learning/)
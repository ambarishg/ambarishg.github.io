---
layout: post
tags:
- azure-machinelearning
- machinelearning
categories: Azure Machine Learning
title: Azure ML Experiments and Runs basics
description: Azure ML Experiments and Runs basics
---


>
An experiment is a grouping of many runs from a specified script. It always belongs to a workspace. When we submit a run, we provide an experiment name. Information for the run is stored under that experiment. If the name doesn't exist when we submit an experiment, a new experiment is automatically created.  

<img src="/img/AzureML/expts.PNG">

>  
A run is a single execution of a training script. An experiment will typically contain multiple runs.

<img src="/img/AzureML/runs.PNG">

A run has the following characteristics

* Metrics
* Child Runs  
* Outputs 
* Logs 

<img src="/img/AzureML/a-single-run.PNG">

A run also has metrics and parameters associated with it

<img src="/img/AzureML/a-single-run-metrics.PNG">   

A run also has outputs associated with it

<img src="/img/AzureML/a-single-run-outputs.PNG">

*References*   

* [Azure Machine Learning documentation](https://docs.microsoft.com/en-in/azure/machine-learning/)
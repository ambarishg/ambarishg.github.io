---
layout: post
tags:
- azure-machinelearning
- machinelearning
categories: Azure Machine Learning
title: Azure ML workspace basics
description: Azure ML workspace basics
---


Azure ML has a top level component which is the **Workspace**. The workspace contains all the components of the Azure Machine Learning space.  

<img src="/img/AzureML/workspace.png">

The workspace is associated with  

* Azure subscription  
* Azure Key Vault
* Azure Application Insights  

It is associated with the following **assets**  

* Datasets  
* Experiments  
* Pipelines
* Models
* EndPoints  

The workspace **manages** the following

* Datastores
* Compute  

The workspace can be used for authoring

* Notebooks  
* Automated ML
* Designer


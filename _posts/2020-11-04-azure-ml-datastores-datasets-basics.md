---
layout: post
tags:
- azure-machinelearning
- machinelearning
categories: Azure Machine Learning
title: Azure ML DataStores and Datasets
description: Azure ML DataStores and Datasets
---
<br/>

**DataStores**       

In Azure ML, datastores are references to storage locations, such as Azure Storage blob containers. Every workspace has a default datastore - usually the Azure storage blob container that was created with the workspace.  

<img src="/img/AzureML/datastores.PNG">

When data is uploaded into the datastore through the following code

```
default_ds.upload_files(files=['data/diabetes.csv', 'data/diabetes2.csv'], # Upload the diabetes csv files in /data
                       target_path='diabetes-data/', # Put it in a folder path in the datastore
                       overwrite=True, # Replace existing files of the same name
                       show_progress=True)

```

we can see the files in the Azure Storage Account > Containers > Blob Stores  

<img src="/img/AzureML/uploaded-data-datastores.PNG">

<br/>

**Datasets**  

> While we can read data directly from `datastores`, Azure Machine Learning provides a further abstraction for data in the form of `datasets`.   

A dataset is a versioned reference to a specific set of data that you may want to use in an experiment.   

Datasets can be tabular or file-based.

<img src="/img/AzureML/registered-datasets.PNG">

*References*   

* [Azure Machine Learning documentation](https://docs.microsoft.com/en-in/azure/machine-learning/)
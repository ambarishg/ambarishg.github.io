---
layout: post
tags:
- azure-machinelearning
- machinelearning
categories: Azure Machine Learning
title: Azure ML Environments
description: Azure ML Environments
---

>  
An environment is the encapsulation of the environment where training or scoring of the  machine learning model happens. The environment specifies  

* the Python packages,  
* environment variables,  
* and software settings around your training and scoring scripts.  

Environments are of three types
curated, user-managed, and system-managed.

**Curated environments** are provided by Azure Machine Learning and are available in the workspace by default.  

In **user-managed environments**, the person is  responsible for setting up the environment and installing every package that the training script needs on the compute target. Conda doesn't check the environment or install anything.  

```
from azureml.core import Environment

# Editing a run configuration property on-fly.
user_managed_env = Environment("user-managed-env")

user_managed_env.python.user_managed_dependencies = True  

```

We use **system-managed environments** when we want Conda to manage the Python environment and the script dependencies.A new conda environment is built based on the conda dependencies object. The Azure Machine Learning service assumes this type of environment by default, because of its usefulness on remote compute targets that aren't manually configurable.  

*References*   

* [Azure Machine Learning documentation](https://docs.microsoft.com/en-in/azure/machine-learning/)
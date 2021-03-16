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

# Code    


## Create the workspace   

```
from azureml.core import Workspace
from azureml.core import Workspace
from azureml.core.authentication import InteractiveLoginAuthentication

sid = 'a817a155-2099-4dcb-80ae-e5c2ea0e248e'
forced_interactive_auth = InteractiveLoginAuthentication(tenant_id="0f942ca0-ebef-4f26-80f8-f501d599ba90", force=True)

ws = Workspace.create(name='azureml_workspace',
            subscription_id= sid, 
            resource_group='rgazureml',
            create_resource_group = True,
            location='centralus'
            )
```

## Create an experiment and a run              

```
from azureml.core import Experiment

# create an experiment
exp = Experiment(workspace=ws, name='trial_exp')

# start a run
run = exp.start_logging()

# log a number
run.log('trial', 30)

# log a list (Fibonacci numbers)
run.log_list('my list', [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]) 

# finish the run
run.complete()

print('Finished logging')
```


## Create another run      

```
# start a run
run = exp.start_logging()

# log a number
run.log('trial2', 35)

# log a list 
run.log_list('my list2', [1, 1, 2, 2, 5, 5, 13, 13, 13, 13]) 

# finish the run
run.complete()
```

*References*   

* [Azure Machine Learning documentation](https://docs.microsoft.com/en-in/azure/machine-learning/)
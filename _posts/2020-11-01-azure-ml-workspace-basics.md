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

You can implement via **code** 

```
import azureml.core
print(azureml.core.VERSION)
```
```
from azureml.core import Workspace
from azureml.core.authentication import InteractiveLoginAuthentication

sid = <your-subscription-id>
forced_interactive_auth = InteractiveLoginAuthentication(tenant_id=<your-tenant-id>)
ws = Workspace.create(name='azureml_workspace',
            subscription_id= sid, 
            resource_group='rgazureml',
            create_resource_group = True,
            location='centralus'
            )
```

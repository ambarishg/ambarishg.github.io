---
layout: post
tags:
- azure-machinelearning
- machinelearning
categories: Azure Machine Learning
title: 2 Stories, Azure ML, Azure Kubernetes Service, Model deployment
description: 2 Stories, Azure ML, Azure Kubernetes Service, Model deployment
---

Let's start with 2 of my experiences with machine learning in data science competitions and writing a research paper. This will give us enough motivation to understand why platforms such as AzureML are required.

# Story 1 -  A data science competition 

> I participated in a data science competition that required predicting time series data. For this, I tried 5 different algorithms `Arima, ETS, Facebook Prophet, XGBoost, and Random Forest`. I also used several imputation techniques which also involved a number of hyperparameters. The competition ran for around 2 months and I worked on it continuously. It was very difficult and cumbersome to maintain the various metrics of the model runs and their hyperparameters.It would have been easier if I could log the metrics and the hyperparameters in a more systematic manner. This would have helped me ease the model management to a great extent. 

# Story 2 -  Writing a research paper            

> This involved classification of **breast cancer** images. I used 13 different models, which included deep learning architectures and classical computer vision models. The complexity here is more since the `experimentation` is with different architectures which also have different hyperparameters. This was an unbalanced dataset, therefore metrics such as `precision`, `recall`, `fscore` , `balanced accuracy` were used. The model management and hyperparameter management becomes very difficult if we do not have a very good platform for such quick experimentation and also for the analysis of the results.

These 2 stories illustrate that in Machine Learning, model development is important but there are many other factors such as model management, hyperparameter management, reproducibility are very important factors for the success of a machine learning project.

Azure ML provides a robust framework for deploying, maintaining models.  We are going to build a Machine Learning Model and deploy it to Azure ML. In the process, we not only make use of AzureML but also use various other services such as `AKS(Azure Kubernetes Service) and Azure Storage` to name a few. Through this blog, we are going to learn various Machine Learning concepts and how they are implemented in Azure ML. 

We divide into **2 major blocks**:
1. Building the Model in Azure ML   
2. Inference from the Model in Azure ML  

**Building the model in Azure ML** has the following steps:
1. Create the Azure ML workspace      
2. Upload data into the Azure ML Workspace  
3. Create the code folder      
4. Create the Compute Cluster      
5. Create the Model   
6. Create the Compute Environment 
7. Create the Estimator 
8. Create the Experiment and Run
9. Register the Model     

**Inferencing from the model** in Azure ML has the following steps:  
1. Create the Inference Script
2. Create the Inference Dependencies
3. Create the Inference Config
4. Create the Inference Clusters   
5. Deploy the Model in the Inference Cluster  
6. Get the predictions

> The post generously uses code from the MS Learn Data Scientist Associate Learning path. The post will help you in understanding the different Azure ML concepts from conceptualizing a problem to deployment in a production environment. You may have to change certain settings though. Moreover, if you are interested in the DP-100 Microsoft Data Scientist Associate Exam, you will find this post helpful.

**Let's begin our journey:**    

# Create the Azure ML workspace         
                  

We need to create an Azure ML workspace that contains the experiments, runs, models, and everything. It is a house for everything. Let's create one
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

What does this code segment actually do:
* Deployed an Azure ML workspace `azureml_workspace`
* Deployed an AppInsights
* Deployed KeyVault 
* Deployed StorageAccount 

in the resource group **rgazureml**. You can navigate to the resource group to view these features.

I have attached my screenshot. Please navigate to your workspace to see the results.

![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0ml6s7upgzwm1gvb469v.png)

# Upload data into the Azure ML Workspace          
                  

Machine Learning is about data. We need data to build our models. The data which we are going to use is the Red Wine Quality dataset. Let us store the data in the Azure ML workspace. 

```
# Upload data into the Azure ML Workspace

#upload data by using get_default_datastore()
ds = ws.get_default_datastore()
ds.upload(src_dir='./winedata', target_path='winedata', overwrite=True, show_progress=True)

print('Done')
```

We upload the data to the workspace default store. The default store is associated with the **storage account** we had created earlier.

The screenshot of my files in the datastore is attached here
![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hd7zcmzyy74bobz9b1xc.png)

# Create the code folder               
              

We store the code files in a directory

```
import os

# create the folder
folder_training_script = './winecode'
os.makedirs(folder_training_script, exist_ok=True)

print('Done')
```
Till this point, we have uploaded the data for machine learning. We need to identify the computing environment to process the machine learning models. Let's create a **compute cluster** using the Azure ML SDK.

# Create the Compute Cluster   
                   

```        
from azureml.core.compute import AmlCompute
from azureml.core.compute import ComputeTarget
import os

# Step 1: name the cluster and set the minimal and maximal number of nodes 
compute_name = os.environ.get("AML_COMPUTE_CLUSTER_NAME", "cpucluster")
min_nodes = os.environ.get("AML_COMPUTE_CLUSTER_MIN_NODES", 0)
max_nodes = os.environ.get("AML_COMPUTE_CLUSTER_MAX_NODES", 1)

# Step 2: choose environment variables 
vm_size = os.environ.get("AML_COMPUTE_CLUSTER_SKU", "STANDARD_D2_V2")

provisioning_config = AmlCompute.provisioning_configuration(
    vm_size = vm_size, min_nodes = min_nodes, max_nodes = max_nodes)

# create the cluster
compute_target = ComputeTarget.create(ws, compute_name, provisioning_config)

print('Compute target created')
```
![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0bojaz128y0hq504zc3m.png)

# Create the Model              
                

We now create the model and store it in a script. The model uses the following
* Decision Trees algorithm             
* Cross-validation             
* Logs the Decision Trees `max_depth` parameter and `rmse` parameter             

```
%%writefile $folder_training_script/train.py

import argparse
import os
import numpy as np
import pandas as pd
import glob

from azureml.core import Run
# from utils import load_data

import joblib

from sklearn.tree import DecisionTreeRegressor
from sklearn.model_selection import cross_val_score

# let user feed in 2 parameters, the dataset to mount or download, and the regularization rate of the logistic regression model
parser = argparse.ArgumentParser()
parser.add_argument('--data-folder', type=str, dest='data_folder', help='data folder mounting point')
parser.add_argument('--max-depth', type=float, dest='max_depth', default=5, help='max depth')
args = parser.parse_args()

###
data_folder = os.path.join(args.data_folder, 'winedata')
print('Data folder:', data_folder)

wine_data = pd.read_csv(os.path.join(data_folder, 'winequality_red.csv'))

                        
X = wine_data.drop(columns =["quality"])
y = wine_data["quality"]

clf = DecisionTreeRegressor(random_state=0,max_depth = args.max_depth)
rmse= np.mean(np.sqrt(-cross_val_score(clf, X, y, scoring="neg_mean_squared_error", cv = 5)))
print('RMSE is', rmse)

# Get the experiment run context
run = Run.get_context()

run.log('max depth', np.float(args.max_depth))
run.log('rmse', np.float(rmse))

os.makedirs('outputs', exist_ok=True)

clf.fit(X,y)
# note file saved in the outputs folder is automatically uploaded into experiment record
joblib.dump(value=clf, filename='outputs/wine_model.pkl')

run.complete()
```
# Create the Compute Environment                 
                

Till this point, we have done the following things
* Uploaded the data into Azure 
* Created the compute resources for the machine learning model
* Created the model in a file

We need certain packages so that we can perform machine learning. Usually, we would require packages such as `sklearn`. This is a small machine learning model, but ideally, we would require more packages. In the next step, we create an **Environment** which houses the packages for the machine learning model

```
from azureml.core import Environment
from azureml.core.conda_dependencies import CondaDependencies

# Create a Python environment for the experiment
wine_env = Environment("wine-experiment-env")
wine_env.python.user_managed_dependencies = False # Let Azure ML manage dependencies
wine_env.docker.enabled = False # Use a docker container

# Create a set of package dependencies (conda or pip as required)
wine_packages = CondaDependencies.create(conda_packages=['scikit-learn'])

# Add the dependencies to the environment
wine_env.python.conda_dependencies = wine_packages

print(wine_env.name, 'defined.')

# Register the environment
wine_env.register(workspace=ws)
```

# Create the Estimator               
             

Till this point, we have done the following things
* Uploaded the data into Azure 
* Created the compute resources for the machine learning model
* Created the model in a file
* Created the environment for the compute clusters

We need to bind all this together and we would create an **Estimator** which binds the source code, hyperparameters required for the model, compute clusters, and the compute environment together. To run the model, we would also pass the hyperparameters required for the model. 

```
from azureml.train.estimator import Estimator

script_params = {
    '--data-folder': ds.as_mount(),
    '--max-depth': 10
}

registered_env = Environment.get(ws, 'wine-experiment-env')

# Create an estimator
estimator = Estimator(source_directory=folder_training_script,
                      script_params=script_params,
                      compute_target = compute_target, # Run the experiment on the remote compute target
                      environment_definition = registered_env,
                      entry_script='train.py')
```
We are now ready for an AzureML **Experiment** which would house a number of **Runs**. The following code segment creates an experiment and also creates a **Run** with the created **Estimator**

```
# Create the Experiment and Run               

from azureml.core import Experiment

#Create an experiment
experiment = Experiment(workspace = ws, name = "wine_expt")

print('Experiment created')
run = experiment.submit(config=estimator)
run
```
A snapshot of the experiment and its associated run is provided below. The experiment is `wine_expt` and the Runs associated with it.

![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/crpzixx2hwutgu3lvlnu.png)
 
The latest completed Run snapshot is provided below
![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2f4e1lswpsm9k7tefyhp.png)
 
In the latest run, we see the metrics **rmse** and the hyperparameters **max_depth** being shown.
 
 We print the model metrics here using the following code segment

```
#get the result
print(run.get_metrics())
```
# Register the Model            

We register the model in the workspace using the following code segment

```
model = run.register_model(model_name='wine_model',
                           model_path='outputs/wine_model.pkl',
                           tags = {'area': "wine", 'type': "sklearn"},
                           description = "quality wine")

print(model.name, model.id, model.version, sep='\t')
```

You can see this in your workspace. I have attached my screenshot
![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5rli8x3uoq7bk270kj4m.png)
 
# Create the Inference Script        

Till this point , we have built the model and registered in our workspace. We will now use this model to predict on new data. The first step is to create an **inference script**.    

```
%%writefile $folder_training_script/score.py
import json
import joblib
import numpy as np
from azureml.core.model import Model

# Called when the service is loaded
def init():
    global model
    # Get the path to the registered model file and load it
    model_path = Model.get_model_path('wine_model')
    model = joblib.load(model_path)

# Called when a request is received
def run(raw_data):
    # Get the input data as a numpy array
    data = np.array(json.loads(raw_data)['data'])
    # Get a prediction from the model
    predictions = model.predict(data)
    # Return the predictions as any JSON serializable format
    return predictions.tolist()
```
We also create the environment for the `packages` which are required for the inference script through the script   

# Create the Inference Dependencies    

```
from azureml.core.conda_dependencies import CondaDependencies

# Add the dependencies for your model
myenv = CondaDependencies()
myenv.add_conda_package("scikit-learn")

# Save the environment config as a .yml file
env_file = './winecode/env.yml'
with open(env_file,"w") as f:
    f.write(myenv.serialize_to_string())
print("Saved dependency info in", env_file)
```
Till this point, we have the following 
* Inference script  
* Dependencies required for the inference script   

We need to combine this together and the **InferenceConfig** will help us to do this

# Create the Inference Config   

```
from azureml.core.model import InferenceConfig

classifier_inference_config = InferenceConfig(runtime= "python",
                                              source_directory = './winecode',
                                              entry_script="score.py",
                                              conda_file="env.yml")
```

# Create the Inference Clusters

We create the **Inference Clusters**, the AKS clusters required for the inference  

```
from azureml.core.compute import ComputeTarget, AksCompute

cluster_name = 'aks-cluster'
compute_config = AksCompute.provisioning_configuration(cluster_purpose = AksCompute.ClusterPurpose.DEV_TEST)
production_cluster = ComputeTarget.create(ws, cluster_name, compute_config)
production_cluster.wait_for_completion(show_output=True)
```

We can see the inference clusters in the workspace. I have attached my screenshot here
![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eyuvjj45l0tg99bjsx8p.png)

# Deploy the Model in the Inference Cluster  

We create the deployment config for the AKS Web Service    

```
from azureml.core.webservice import AksWebservice

classifier_deploy_config = AksWebservice.deploy_configuration(cpu_cores = 1,
                                                              memory_gb = 1)
```
The final step is to combine the 
* Inference config  
* Deployment config   
* Inference Cluster to create an endpoint which can be used for predicting new data    

```
from azureml.core.model import Model

model = ws.models['wine_model']
service = Model.deploy(workspace=ws,
                       name = 'wine-service',
                       models = [model],
                       inference_config = classifier_inference_config,
                       deployment_config = classifier_deploy_config,
                       deployment_target = production_cluster)
service.wait_for_deployment(show_output = True)
```
We print the endpoint for the model

```
endpoint = service.scoring_uri
print(endpoint)
```
You can see the endpoint of the model in your workspace. Here is my screenshot

![image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/j1ejillo1cunfk8ffiuw.png)

# Get the predictions 

We get the **Service Keys** which we would require for prediction

```
primary_key, secondary_key = service.get_keys()
```

The final step is creating predictions from the endpoint which is illustrated below

```
import requests
import json

# An array of new data cases
x_new = [[7.3,0.65,0,1.2,0.065,15,21,0.9946,3.39,0.47,10]]

# Convert the array to a serializable list in a JSON document
json_data = json.dumps({"data": x_new})

# Set the content type in the request headers
request_headers = { "Content-Type":"application/json",
                    "Authorization":"Bearer " + primary_key }

# Call the service
response = requests.post(url = endpoint,
                         data = json_data,
                         headers = request_headers)

print(response)
print(response.json)
```

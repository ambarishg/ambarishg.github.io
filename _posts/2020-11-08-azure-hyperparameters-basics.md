---
layout: post
tags:
- azure-machinelearning
- machinelearning
categories: Azure Machine Learning
title: Azure ML HyperParameters
description: Azure ML HyperParameters
---

<br/>

<hr/>

**Parameter**  

A variable of a model that the machine learning system trains on its own. For example, weights are `parameters` whose values the machine learning system gradually learns through successive training iterations.  

<hr/>

**Hyperparameter**  

The "knobs" that we tweak during successive runs of training a model. For example, learning rate is a hyperparameter.  

<hr/>

Hyperparameters have the following properties

* Search space - The set of hyperparameter values tried during hyperparameter tuning is known as the search space. The definition of the range of possible values that can be chosen depends on the type of hyperparameter. 

    The **Search Space** includes **Discrete** and **Continuos**  values  

* Sampling strategy - The specific values used in a hyperparameter tuning run depend on the type of sampling used.  

    **Grid sampling** can only be employed when all `hyperparameters are discrete`, and is used to try every possible combination of parameters in the search space.  

    **Random Sampling** is used to `randomly select a value for each hyperparameter`, which can be a mix of discrete and continuous values  

    **Bayesian sampling** chooses hyperparameter values based on the Bayesian optimization algorithm, which tries to select parameter combinations that will result in `improved performance from the previous selection`.  

* Early stopping strategy - With a sufficiently large hyperparameter search space, it could take many iterations (child runs) to try every possible combination. Typically, we set a maximum number of iterations, but this could still result in a large number of runs that don't result in a better model than a combination that has already been tried.

    **Bandit policy** to stop a run if the target performance metric underperforms the best run so far by a specified margin.  

    **Median stopping** policy abandons runs where the target performance metric is worse than the median of the running averages for all runs.  

    **Truncation selection** policy cancels the lowest performing X% of runs at each evaluation interval based on the truncation_percentage value you specify for X.

**HyperDriveConfig**  

Configuration that defines a HyperDrive run.

HyperDrive configuration includes information about hyperparameter space sampling, termination policy, primary metric, resume from configuration, estimator, and the compute target to execute the experiment runs on.

*References*  

* [Azure Machine Learning documentation](https://docs.microsoft.com/en-in/azure/machine-learning/)
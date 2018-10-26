---
layout: post
title: Azure Batch
categories: Cloud
date: 2018-08-12 03:00:00
tags:
- azure
- azure compute
description: Azure Batch 
---

Batch processing began with mainframe computers and punch cards. Today, it still plays a central role in business, engineering, science and other areas that require running lots of automated tasks—processing bills and payroll, calculating portfolio risk, designing new products, rendering animated films, testing software, searching for energy, predicting the weather and finding new cures for disease. Previously, few people had access to the computing power for these scenarios. With Azure Batch, that power is available to you when you need it, without any capital investment.               

A common scenario for Batch involves scaling out intrinsically parallel work, such as the rendering of images for 3D scenes, on a pool of compute nodes. This pool of compute nodes can be your "render farm" that provides tens, hundreds, or even thousands of cores to your rendering job.

The following diagram shows steps in a common Batch workflow, with a client application or hosted service using Batch to run a parallel workload.        

<br/>

![Azure](/img/AzureBatch/azure_batch.jpg){:class="img-responsive"} 

<br/>

Upload the data files that you want to process to an **Azure Storage account**. Batch includes built-in support for accessing Azure Blob storage, and your tasks can download these files to compute nodes when the tasks are run.                

Upload the application files that your tasks will run. These files can be binaries or scripts and their dependencies, and are executed by the tasks in your jobs. Your tasks can download these files from your Storage account, or you can use the application packages feature of Batch for application management and deployment.              

Create a **pool of compute nodes**. When you create a pool, you specify the number of compute nodes for the pool, their size, and the operating system. When each task in your job runs, it's assigned to execute on one of the nodes in your pool.
Create a job. A job manages a collection of tasks. You associate each job to a specific pool where that job's tasks will run.                  

Add **tasks to the job**. Each task runs the application or script that you uploaded to process the data files it downloads from your Storage account. As each task completes, it can upload its output to Azure Storage.                

Monitor **job progress** and retrieve the task output from Azure Storage.               



Details are found [here](https://azure.microsoft.com/en-in/services/batch/)




         

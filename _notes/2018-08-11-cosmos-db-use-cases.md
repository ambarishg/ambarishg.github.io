---
layout: post
title: Cosmos DB Use Cases
categories: Cloud
date: 2018-08-11 05:00:00
tags:
- azure
- azure no sql
description: Cosmos DB Use Cases 
---
<br/>

Cosmos DB use cases are found [here](https://docs.microsoft.com/en-in/azure/cosmos-db/use-cases/)

<br/>

Azure Cosmos DB is a fast and flexible globally replicated database, well-suited for IoT, gaming, retail, and operational logging applications. A common design pattern in these applications is to use **changes to the data to kick off additional actions**. These additional actions could be any of the following:

* Triggering a notification or a call to an API when a document is inserted or modified.                      
* Stream processing for IoT or performing analytics.                
* Additional data movement by synchronizing with a cache, search engine, or data warehouse, or archiving data to cold storage.              
* The change feed support in Azure Cosmos DB enables you to build efficient and scalable solutions for each of these patterns, as shown in the following image:           

![Azure](/img/CosmosDB/changefeedoverview.jpg){:class="img-responsive"} 


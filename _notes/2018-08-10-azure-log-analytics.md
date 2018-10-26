---
layout: post
title: Azure Log Analytics 
categories: Cloud
date: 2018-08-10 14:54:00
tags:
- azure
- azure security
- azure monitoring
description: Azure Log Analytics 
---

![Azure](/img/AzureSecurity/loganalytics.jpg){:class="img-responsive"}

Log Analytics plays a central role in Azure management by collecting telemetry and other data from a variety of sources and providing a query language and analytics engine that gives you insights into the operation of your applications and resources. You can either interact directly with Log Analytics data through log searches and views, or you may use analysis tools in other Azure services that store their data in Log Analytics such as Application Insights or Azure Security Center.              

Methods for collecting data into Log Analytics include the following:

* Configure **Azure Monitor** to copy metrics and logs that it collects from Azure resources.             

* Collect telemetry written to Azure Storage.        

* **Agents on Windows and Linux virtual machine** send telemetry from the guest operating system and applications to Log Analytics according to Data Sources that you configure. Agents can be directly connected, connect through an OMS Gateway when they don't have firewall access, or connect through a System Center Operations Manager management group.            

* Azure services such as **Application Insights and Azure Security Center** store their data directly in Log Analytics without any configuration.

*  Write data from **PowerShell command line or Azure Automation runbook** using Log Analytics cmdlets.         

* If you have custom requirements, then you can use the HTTP Data Collector API to write data to Log Analytics from any REST API client or an Azure Logic App to write data from a custom workflow.          

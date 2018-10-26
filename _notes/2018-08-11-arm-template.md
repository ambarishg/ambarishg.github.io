---
layout: post
title: ARM Template
categories: Cloud
date: 2018-08-12 02:00:00
tags:
- azure
- azure deployment
description: ARM Template 
---

An `ARM template` consists of `JSON` and expressions which you can use to construct values for your deployment. You must limit the size your template to 1 MB, and each parameter file to 64 KB. The 1 MB limit applies to the final state of the template after it has been expanded with iterative resource definitions, and values for variables and parameters.

		{
		   "$schema": "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
		   "contentVersion": "",
		   "parameters": {  },
		   "variables": {  },
		   "resources": [  ],
		   "outputs": {  }
		}                   

* $Schema: Location of the JSON schema file that describes the version of the template language.                

* contentVersion: Version of the template (such as 1.0.0.0).   
         
* parameters: Optional values that are provided when deployment is executed to customize resource deployment.              

* resources: A manageable item that is available through Azure. Some common resources are a virtual machine, storage account, web app, database, and virtual network, but there are many more.        

* outputs: Values that are returned after deployment             
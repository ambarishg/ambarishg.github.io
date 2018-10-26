---
layout: post
title: ARM linked and nested templates
categories: Cloud
date: 2018-08-15 01:00:00
tags:
- azure
- azure arm
description: ARM linked and nested templates
---
<br/>

**Link or nest a template**         

To link to another template, add a **deployments resource** to your main template.                

**Nested template**    

To nest the template within the main template, use the **template property** and specify the template syntax.             

**External template and external parameters**             

To link to an external template and parameter file, **use templateLink and parametersLink**. When linking to a template, the Resource Manager service must be able to access it. You cannot specify a local file or a file that is only available on your local network. You can only provide a URI value that includes either http or https. One option is to place your linked template in a storage account, and use the URI for that item.                       

Details are [here](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-linked-templates#link-or-nest-a-template)               

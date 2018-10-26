---
layout: post
title: Event Grid 
categories: Cloud
date: 2018-08-10 16:30:00
tags:
- azure
- azure messaging
description: Event Grid 
---

![Azure](/img/AzureMessaging/eventgrid.jpg){:class="img-responsive"}

Azure Event Grid allows you to easily build applications with event-based architectures. You select the Azure resource you would like to subscribe to, and give the event handler or WebHook endpoint to send the event to. Event Grid has built-in support for events coming from Azure services, like storage blobs and resource groups. Event Grid also has custom support for application and third-party events, using custom topics and custom  webhooks.           

**Serverless apps**     
Event Grid connects data sources and event handlers. For example, use Event Grid to instantly trigger a serverless function to run image analysis each time a new photo is added to a blob storage container.            

![Azure](/img/AzureMessaging/serverless_web_app.jpg){:class="img-responsive"}
 
 <br/>

**Ops automation** 
Event Grid allows you to speed automation and simplify policy enforcement. For example, Event Grid can notify Azure Automation when a virtual machine is created, or a SQL Database is spun up. These events can be used to automatically check that service configurations are compliant, put metadata into operations tools, tag virtual machines, or file work items.         

![Azure](/img/AzureMessaging/ops_automation.jpg){:class="img-responsive"}
 <br/>

**Application integration**

Event Grid connects your app with other services. For example, create a custom topic to send your app's event data to Event Grid, and take advantage of its reliable delivery, advanced routing, and direct integration with Azure. Alternatively, you can use Event Grid with Logic Apps to process data anywhere, without writing code.      

![Azure](/img/AzureMessaging/app_integration.jpg){:class="img-responsive"}
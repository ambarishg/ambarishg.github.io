---
layout: post
title: Service Bus
categories: Cloud
date: 2018-08-19 01:00:00
tags:
- azure
- azure messaging
description: Service Bus
---

Service Bus is intended for `traditional enterprise applications`. These enterprise applications require `transactions, ordering, duplicate detection, and instantaneous consistency`. Service Bus enables cloud-native applications to provide reliable state transition management for business processes. When handling high-value messages that cannot be lost or duplicated, use Azure Service Bus. Service Bus also facilitates highly secure communication across hybrid cloud solutions and can connect existing on-premises systems to cloud solutions.

Service Bus is a **brokered messaging system**. It stores messages in a "broker" (for example, a queue) until the consuming party is ready to receive the messages.                               

It has the following characteristics:           

* reliable asynchronous message delivery (enterprise messaging as a service) that requires polling                 
* advanced messaging features like FIFO, batching/sessions, transactions, dead-lettering, temporal control, routing and filtering, and duplicate detection             
* at least once delivery              
* optional in-order delivery                  
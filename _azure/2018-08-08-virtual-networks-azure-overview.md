---
layout: post
title: Virtual Networks in Azure Overview
categories: Cloud Computing
date: 2018-08-09 08:00:00
tags:
- azure
- virtual networks
description: Virtual Networks in Azure Overview 
---
<br/>

###  Virtual Networks in Azure Overview
                                
<br/>
![VNets](/img/VNets/vnetoverview.jpg){:class="img-responsive"}
<br/>

* In an Azure subscription, many **regions** may be associated.               

* A region may be associated with many **virtual networks**            

* A virtual network may be associated with many **subnets**             

* A subnet may be a **front-end subnet** consisting of a `Public Front End Load balancer` and the front-end VMS.             

* Another subnet may be a **backend-end subnet** consisting of a `Private Back End Load balancer` and the backend-end VMS.

* The front-end subnet may be associated with a **Network Security Group** which will have certain **InBound as well as Outbound rules** associated with it            

* The back-end subnet may be associated with a **Network Security Group** which will have certain **InBound as well as Outbound rules** associated with it            


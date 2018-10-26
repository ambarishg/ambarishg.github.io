---
layout: post
title: Azure Traffic Manager
categories: Cloud
date: 2018-08-11 01:20:00
tags:
- azure
- azure load balancer
description: Azure Traffic Manager 
---

Azure Traffic Manager is a **DNS-based traffic load balancer** that enables you to distribute traffic optimally to services across **global Azure regions**, while providing high availability and responsiveness.               

Traffic Manager uses DNS to direct client requests to the most appropriate service endpoint based on a traffic-routing method and the health of the endpoints. An endpoint is any Internet-facing service hosted inside or outside of Azure. Traffic Manager provides a range of traffic-routing methods and endpoint monitoring options to suit different application needs and automatic failover models. Traffic Manager is resilient to failure, including the failure of an entire Azure region.              

Azure provides a suite of fully managed load-balancing solutions for your scenarios. If you are looking for `Transport Layer Security (TLS) protocol termination ("SSL offload") or per-HTTP/HTTPS request`, application-layer processing, **review Application Gateway**. If you are looking for `regional balancing`, **review Load Balancer**. Your end-to-end scenarios might benefit from combining these solutions as needed.             
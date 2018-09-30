---
layout: post
title: aws ebs volume types
categories: aws
date: 2018-09-30 09:00:00 -0500
tags:
- ebs
- aws
description: We describe the <b>aws ebs volume types</b>  here...            
---        

**EBS Volume Types**                

`General Purpose SSD (gp2)`             
General purpose SSD volume that balances price and performance for a wide variety of workloads           

 * Recommended for most workloads          
 * System boot volumes            
 * Virtual desktops                   
 * Low-latency interactive apps        
 * Development and test environments                                  

`Provisioned IOPS SSD (io1)`             
Highest-performance SSD volume for mission-critical low-latency or high-throughput workloads                             

 * Critical business applications that require sustained IOPS performance, or more than 10,000 IOPS or 160 MiB/s of throughput per volume                  
 * Large database workloads, such as:MongoDB,Cassandra,Microsoft SQL Server,MySQL,PostgreSQL,Oracle              

`Throughput Optimized HDD (st1)`                 
Low cost HDD volume designed for frequently accessed, throughput-intensive workloads                                                

* Streaming workloads requiring consistent, fast throughput at a low price   
* Big data              
* Data warehouses             
* Log processing           
* Cannot be a boot volume     

`Cold HDD (sc1)`                 
Lowest cost HDD volume designed for less frequently accessed workloads                                                        
* Throughput-oriented storage for large volumes of data that is infrequently accessed                   
* Scenarios where the lowest storage cost                           
* Cannot be a boot volume 
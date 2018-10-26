---
layout: post
title: Forced Tunneling
categories: Cloud
date: 2018-08-09 09:00:00
tags:
- azure
- virtual networks
description: Forced Tunneling in Virtual Networks
---
<br/>

###  Forced Tunneling in Virtual Networks
                                
<br/>
![VNets](/img/VNets/forced-tunnel.jpg){:class="img-responsive"}
<br/>

In the diagram above, the Frontend subnet is not forced tunneled. The workloads in the Frontend subnet can continue to accept and respond to customer requests from the Internet directly. The Mid-tier and Backend subnets are forced tunneled. Any outbound connections from these two subnets to the Internet will be forced or redirected back to an on-premises site via one of the S2S VPN tunnels.                        

This allows you to restrict and inspect Internet access from your virtual machines or cloud services in Azure, while continuing to enable your multi-tier service architecture required. If there are no Internet-facing workloads in your virtual networks, you also can apply forced tunneling to the entire virtual networks                 


---
layout: post
title: confidence intervals of population proportion
categories: Statistics
date: 2018-01-11 11:00:00 -0700
tags:
- statistics
description: We describe the Business applications of <b>Confidence Intervals of Population proportion</b>  here...
---

### 95% Confidence Interval for **Proportion**   

A ( 1-  $$\alpha$$  ) confidence interval for the proportion $$\hat{p}$$ when population standard deviation $$\sigma$$ is known and a sampling is done from a normal population , or with a large sample is    

 $$\hat{p}$$  +/-  $$\mathbf{Z_\frac{\alpha}{2}}$$ $$\sqrt\frac{\hat{p}(1- \hat{p})}{n}$$ 
 

{% highlight R %}

qnorm(.025,0,1)
{% endhighlight %}

Therefore the equation for the **95% confidence interval** is    

$$\hat{p}$$  +/-  1.96 * $$\sqrt\frac{\hat{p}(1- \hat{p})}{n}$$ 

#### 6–41 

The makers of a medicated facial skin cream are interested in determining
the percentage of people in a given age group who may benefit from the ointment.
A random sample of 68 people results in 42 successful treatments. Give a 99%
confidence interval for the proportion of people in the given age group who may be
successfully treated with the facial cream.

{% highlight R %}

z_alpha_by_two = qnorm(.005,0,1)

z_alpha_by_two

p = 42/68

n = 68

p + z_alpha_by_two * sqrt( (p * (1-p))/n)

p - z_alpha_by_two * sqrt( (p * (1-p))/n)


{% endhighlight %}

#### 6-47 

A machine produces safety devices for use in helicopters. A quality-control
engineer regularly checks samples of the devices produced by the machine, and if too
many of the devices are defective, the production process is stopped and the machine
is readjusted. If a random sample of 52 devices yields 8 defectives, give a 98% confidence
interval for the proportion of defective devices made by this machine.

{% highlight R %}

z_alpha_by_two = qnorm(.010,0,1)

z_alpha_by_two

p = 8/52

n = 52

p + z_alpha_by_two * sqrt( (p * (1-p))/n)

p - z_alpha_by_two * sqrt( (p * (1-p))/n)


{% endhighlight %}


#### 6–49

An airline wants to estimate the proportion of business passengers on a new
route from New York to San Francisco. A random sample of 347 passengers on this
route is selected, and 201 are found to be business travelers. Give a 90% confidence
interval for the proportion of business travelers on the airline’s new route.


{% highlight R %}

z_alpha_by_two = qnorm(.05,0,1)

z_alpha_by_two

p = 201/347

n = 347

p + z_alpha_by_two * sqrt( (p * (1-p))/n)

p - z_alpha_by_two * sqrt( (p * (1-p))/n)


{% endhighlight %}


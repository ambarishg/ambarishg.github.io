---
layout: post
title: hypothesis Testing for population proportions
categories: Statistics
date: 2018-01-11 11:00:00 -0700
tags:
- statistics
description: We describe the Business applications of <b>hypothesis Testing for population proportions</b>  here...
---

### Introduction

We investigate the hypothesis testing for population proportions.         


### 7-29 

The manufacturer of electronic components needs to inform its buyers of the
proportion of defective components in its shipments. The company has been stating
that the percentage of defectives is 12%. The company wants to test whether the proportion
of all components that are defective is as claimed. A random sample of 100
items indicates 17 defectives. Use $$\alpha$$ =  0.05 to test the hypothesis that the percentage
of defective components is 12%.

The **Null Hypothesis** is population proportion is 12% or less

The **Alternative Hypothesis** is population proportion is greater          

{% highlight R %}

sample_prop = 0.17

population_prop = 0.12

n =100

z_statistic = (sample_prop - population_prop)/
sqrt(population_prop *(1-population_prop)/n)

z_statistic

{% endhighlight %}

**Rejection Region**

{% highlight R %}

qnorm(.05,mean=0,sd = 1)

{% endhighlight %}


The rejection region is less than **-1.644854**        
        

The zstatistic is outside the rejection region. Therefore we **CANNOT reject the NULL hypothesis**  that the percentage of defective components is 12.             

<hr/>






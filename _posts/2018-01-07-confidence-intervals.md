---
layout: post
title: Confidence Intervals
categories: Statistics
tags:
- statistics
description: We describe the <b>Confidence Intervals</b>  here...
---


### Introduction
<br/>
A confidence interval is a range of numbers believed to include an
unknown population parameter. Associated with the interval is a measure
of the confidence we have that the interval does indeed contain the parameter
of interest.

### 95% Confidence Interval for **Population Mean** when Population Standard Dev is Known    
<br/>
A ( 1-  $$\alpha$$  ) confidence interval for the population mean $$\mu$$ when population standard deviation $$\sigma$$ is known and a sampling is done from a normal population , or with a large sample is    

 $$\mathbf{\bar{X}}$$  +/-  $$\mathbf{Z_\frac{\alpha}{2}}$$ $$\mathbf{\frac{\sigma}{\sqrt(n)}}$$ 
  
 $$\mathbf{\alpha}$$ = .05 for the **95% Confidence Interval**    
 
 $$\mathbf{\frac{\alpha}{2}}$$ = .025            

 We follow a **Case Study** approach in explaining the concepts and use the problems in the book 
**Complete Business Statistics** by **Aczel and Sounderpandian**.The numbers in the headings are the problem numbers in the book.   
 

{% highlight R %}

qnorm(.025,0,1)
{% endhighlight %}

Therefore the equation for the **95% confidence interval** is    

$$\mathbf{\bar{X}}$$  +/-  1.96 * $$\mathbf{\frac{\sigma}{\sqrt(n)}}$$ 

####   6-5
<br/>
A real estate agent needs to estimate the average value of a residential property
of a given size in a certain area. The real estate agent believes that the standard deviation
of the property values is $5,500.00 and that property values are approximately
normally distributed. A random sample of 16 units gives a sample mean of
$89,673.12. Give a 95% confidence interval for the average value of all properties of
this kind.

{% highlight R %}

89673.12 + (1.96 * (5500/4))

89673.12 - ( 1.96 * (5500/4))
{% endhighlight %}


####  6–7 
<br/>
A car manufacturer wants to estimate the average miles-per-gallon highway
rating for a new model. From experience with similar models, the manufacturer
believes the miles-per-gallon standard deviation is 4.6. A random sample of 100 highway
runs of the new model yields a sample mean of 32 miles per gallon. Give a 95%
confidence interval for the population average miles-per-gallon highway rating.

{% highlight R %}

32 + (1.96 * (4.6/sqrt(100)))


32 - ( 1.96 * (4.6/sqrt(100)))

{% endhighlight %}

####  6–9
<br/>
A wine importer needs to report the average percentage of alcohol in bottles
of French wine. From experience with previous kinds of wine, the importer believes
the population standard deviation is 1.2%. The importer randomly samples 60 bottles
of the new wine and obtains a sample mean  9.3%. Give a 90% confidence interval
for the average percentage of alcohol in all bottles of the new wine.
 
 $$\mathbf{\alpha}$$ = .10
 
 $$\mathbf{\frac{\alpha}{2}}$$ = .05
 

{% highlight R %}

p = qnorm(.05,0,1)


{% endhighlight %}

{% highlight R %}
9.3 + (p * (1.2/sqrt(60)))

9.3 - (p * (1.2/sqrt(60)))

{% endhighlight %}


#### 6–15 
<br/>
“Small-fry” funds trade at an average of 20% discount to net asset value. If population standard deviation is 8% and n is 36, give the 95% confidence interval for average population percentage.

{% highlight R %}
20 + (1.96 * (8/sqrt(36)))

20 - (1.96 * (8/sqrt(36)))

{% endhighlight %}


#### 95% Confidence Interval for **Population Mean** when Population Standard Dev is NOT Known    <br/>

A ( 1-  $$\alpha$$  ) confidence interval for the population mean $$\mu$$ when population standard deviation $$\sigma$$ is known and a sampling is done from a normal population , or with a large sample is    

 $$\mathbf{\bar{X}}$$  +/-  $$\mathbf{T_\frac{\alpha}{2}}$$ $$\mathbf{\frac{\sigma}{\sqrt(n)}}$$ 
 
 $$\mathbf{\alpha}$$ = .05
 
 $$\mathbf{\frac{\alpha}{2}}$$ = .025
 
 
####  6–19
<br/>
An insurance company handling malpractice cases is interested in estimating
the average amount of claims against physicians of a certain specialty. The company
obtains a random sample of 165 claims and finds sample mean $$16,530 and s = $$5,542. Give
a 95% confidence interval and a 99% confidence interval for the average amount of a
claim.

We assume this follows a standard **t distribution**.        

{% highlight R %}

p = qt(.025,164)

p


16530 + (p * (5542/sqrt(165)))

16530 - (p * (5542/sqrt(165)))

{% endhighlight %}

**2nd method**      

We assume this follows a standard **z distribution**.        

{% highlight R %}

p = 1.96

16530 + (p * (5542/sqrt(165)))

16530 - (p * (5542/sqrt(165)))

{% endhighlight %}



####  6–21


A tire manufacturer wants to estimate the average number of miles that may
be driven on a tire of a certain type before the tire wears out. A random sample of
32 tires is chosen; the tires are driven on until they wear out, and the number of miles
driven on each tire is recorded. The data, in thousands of miles, are as follows:
32, 33, 28, 37, 29, 30, 25, 27, 39, 40, 26, 26, 27, 30, 25, 30, 31, 29, 24, 36, 25, 37, 37, 20, 22,
35, 23, 28, 30, 36, 40, 41

Give a 99% confidence interval for the average number of miles that may be driven
on a tire of this kind.

{% highlight R %}

mean = mean(c(32, 33, 28, 37, 29, 30, 25, 27, 39, 40, 26, 26, 27, 30, 25, 30, 31, 29, 24, 36, 25, 37, 37, 20, 22,35, 23, 28, 30, 36, 40, 41))

sd = sd(c(32, 33, 28, 37, 29, 30, 25, 27, 39, 40, 26, 26, 27, 30, 25, 30, 31, 29, 24, 36, 25, 37, 37, 20, 22,35, 23, 28, 30, 36, 40, 41))

mean

sd

n = length(c(32, 33, 28, 37, 29, 30, 25, 27, 39, 40, 26, 26, 27, 30, 25, 30, 31, 29, 24, 36, 25, 37, 37, 20, 22,35, 23, 28, 30, 36, 40, 41))

n

{% endhighlight %}

#### Considering the **t distribution**

{% highlight R %}
p = qt(.005,n-1)

mean + (p * (sd/sqrt(n)))

mean - (p * (sd/sqrt(n)))


{% endhighlight %}

####  Considering the **z distribution**

{% highlight R %}
p = qnorm(.005,0,1)

mean + (p * (sd/sqrt(n)))

mean - (p * (sd/sqrt(n)))


{% endhighlight %}



---
layout: post
title: hypothesis Testing for population means
categories: Statistics
date: 2018-01-11 11:00:00 -0700
tags:
- statistics
description: We describe the Business applications of <b>hypothesis Testing for population means</b>  here...
---

### Introduction
<br/>

Steps for performing Hypothesis Testing

Step 1 : Formulate Hypothesis

Step 2 : Calculate the t-statistic

Step 3 : Cutoff values for the t-statistic

Step 4 : Check whether t-statistic falls in the rejection region            

We do the **Case Studies** for Hypothesis Testing for the population means.        


### 7–17 

In controlling the quality of a new drug, a dose of medicine is supposed
to contain an average of 247 parts per million (ppm) of a certain chemical. If the
concentration is higher than 247 ppm, the drug may cause some side effects; and if
the concentration is below 247 ppm, the drug may be ineffective. The manufacturer
wants to check whether the average concentration in a large shipment is the required
247 ppm or not. A random sample of 60 portions is tested, and the sample mean is
found to be 250 ppm and the sample standard deviation 12 ppm. Test the null
hypothesis that the average concentration in the entire large shipment is 247 ppm
versus the alternative hypothesis that it is not 247 ppm using a level of significance
alpha = 0.05. Do the same using alpha = 0.01. What is your conclusion? What is your decision
about the shipment? If the shipment were guaranteed to contain an average concentration
of 247 ppm, what would your decision be, based on the statistical
hypothesis test? Explain.

<hr/>

For calculating the z-statistic we require the population standard deviation.But here we have the sample standard deviation. Approximating we use the sample standard deviation for the population standard deviation.       


The NULL Hypothesis is sample mean is 247 parts per million (ppm).            


{% highlight R %}

sample_mean = 250

sample_standard_dev = 12

population_mean = 247

n = 60

z_statistic = (sample_mean - population_mean)/ ((sample_standard_dev)/sqrt(n)) 


z_statistic

{% endhighlight %}


####  For alpha = .05  

{% highlight R %}

qnorm(.025,mean=0,sd = 1)
qnorm(.975,mean=0,sd = 1)

{% endhighlight %}


The zstatistic is **1.936492**            

The rejection region is less than **-1.959964** and greater than **1.959964**              

The zstatistic is outside the rejection region. Therefore we **CANNOT reject the NULL hypothesis**  that the sample mean 247 parts per million (ppm)       

####  For alpha = .01       

{% highlight R %}
qnorm(.005,mean=0,sd = 1)
qnorm(1-.005,mean=0,sd = 1)

{% endhighlight %}

The zstatistic is **1.936492**            

The rejection region is less than **-2.575829** and greater than **2.575829**              

The zstatistic is outside the rejection region. Therefore we **CANNOT reject the NULL hypothesis**  that the sample mean 247 parts per million (ppm)

### 7–19

Many recent changes have affected the real estate market. A study was undertaken
to determine customer satisfaction from real estate deals. Suppose that before
the changes, the average customer satisfaction rating, on a scale of 0 to 100, was **77**.
A survey questionnaire was sent to a random sample of 50 residents who bought new
plots after the changes in the market were instituted, and the average satisfaction rating
for this sample was found to be **84**; the sample standard deviation was found
to be **s = 28**. Use an $$\alpha$$ of your choice, and determine whether statistical evidence indicates
a change in customer satisfaction. If you determine that a change did occur, state
whether you believe customer satisfaction has improved or deteriorated.             


The **Null Hypothesis** is the average customer satisfaction rating is 77.

{% highlight R %}

sample_mean = 84

sample_standard_dev = 28

population_mean = 77

n = 350

z_statistic = (sample_mean - population_mean)/ ((sample_standard_dev)/sqrt(n)) 

z_statistic

{% endhighlight %}

**Rejection Region for $$\alpha$$ = 0.5**

{% highlight R %}

qnorm(.025,mean=0,sd=1)

{% endhighlight %}

The rejection region is less than -1.959964 and greater than 1.959964

The zstatistic is **4.677072**

The zstatistic is **inside** the rejection region. Therefore we **reject the NULL hypothesis**  that the population mean is the average customer satisfaction rating is 77.              




###  7–25

A new chemical process is introduced by Duracell in the production of
lithium-ion batteries. For batteries produced by the old process, the average life of a
battery is 102.5 hours. To determine whether the new process affects the average life
of the batteries, the manufacturer collects a random sample of 25 batteries produced
by the new process and uses them until they run out. The sample mean life is found
to be 107 hours, and the sample standard deviation is found to be 10 hours. Are these
results significant at the $$\alpha$$ =  0.05 level? Are they significant at the $$\alpha$$ =  0.01 level?
Explain. Draw your conclusion.   

The **Null Hypothesis** is population mean is 102.5 hours or less

{% highlight R %}

sample_mean = 107

sample_standard_dev = 10

population_mean = 102.5

n = 25

t_statistic = (sample_mean - population_mean)/ ((sample_standard_dev)/sqrt(n)) 


t_statistic


{% endhighlight %}

**Rejection Region for $$\alpha$$ = 0.5**

{% highlight R %}

qt(.05,n-1)

{% endhighlight %}

The rejection region is less than **-1.644854** and greater than **+1.644854**   

The zstatistic is **inside** the rejection region. Therefore we **CAN reject the NULL hypothesis**  that the population mean is 102.5 hours or less.    


**Rejection Region for $$\alpha$$ = 0.01**

{% highlight R %}

qt(.01,n-1)

{% endhighlight %}

The rejection region is less than **-2.492159** and greater than **2.492159**   


The zstatistic is **outside** the rejection region. Therefore we **CANNOT reject the NULL hypothesis**  that the population mean is 102.5 hours or less. 

### 5.7 Sleep habits of New Yorkers

This case study is from **OpenIntro Statistics**          


New York is known as “the city that never sleeps”.
A random sample of 25 New Yorkers were asked how much sleep they get per night. Statistical
summaries of these data are shown below. Do these data provide strong evidence that New Yorkers
sleep less than 8 hours a night on average?          

n   $$\bar{x}$$       s     min max               
25   7.73           0.77 6.17 9.78                     

(a) Write the hypotheses in symbols and in words.
(b) Check conditions, then calculate the test statistic, T, and the associated degrees of freedom.
(c) Find and interpret the p-value in this context. Drawing a picture may be helpful.
(d) What is the conclusion of the hypothesis test?
(e) If you were to construct a 90% confidence interval that corresponded to this hypothesis test,
would you expect 8 hours to be in the interval?               


The Null Hypothesis is that New Yorkers  sleep 8 hours or less a night on average          
The Alternative Hypothesis is that New Yorkers sleep more than 8 hours a night on average         


{% highlight R %}
sample_mean = 7.73

sample_standard_dev = 0.77

population_mean = 8

n = 25

t_statistic = (sample_mean - population_mean)/ ((sample_standard_dev)/sqrt(n)) 


t_statistic

{% endhighlight %}


**Rejection Region for $$\alpha$$ = 0.05**

{% highlight R %}

qt(.95,n-1)

{% endhighlight %}

The rejection region is more than 1.710882           

The t statistic is -1.753247. It does not fall within the rejection region.          

Therefore we cannot reject the NULL Hypothesis that New Yorkers  sleep 8 hours or less a night on average                 

#5.11 Play the piano

This case study is from **OpenIntro Statistics**       

Georgianna claims that in a small city renowned for its music school, the
average child takes at least 5 years of piano lessons. We have a random sample of 20 children from
the city, with a mean of 4.6 years of piano lessons and a standard deviation of 2.2 years.
(a) Evaluate Georgianna’s claim using a hypothesis test.
(b) Construct a 95% confidence interval for the number of years students in this city take piano
lessons, and interpret it in context of the data.
(c) Do your results from the hypothesis test and the confidence interval agree? Explain your
reasoning.             

The Null Hypothesis is that average child takes 5 years or more of piano lessons            
The Alternative Hypothesis is that average child takes less than 5 years of piano lessons              
{% highlight R %}
sample_mean = 4.6

sample_standard_dev = 2.2

population_mean = 5

n = 20

t_statistic = (sample_mean - population_mean)/ ((sample_standard_dev)/sqrt(n)) 


t_statistic

{% endhighlight %}

**Rejection Region for $$\alpha$$ = 0.05**

{% highlight R %}

qt(.05,n-1)

{% endhighlight %}

The rejection region is less than -1.729133         

The t statistic is -0.8131156        

The t statistic lies **outside the rejection region**. Therefore we cannot reject the NULL Hypothesis that average child takes 5 years or more of piano lessons

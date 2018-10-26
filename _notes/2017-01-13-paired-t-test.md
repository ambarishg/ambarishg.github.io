---
layout: post
title: paired t test
categories: Statistics
date: 2018-01-12 11:00:00 -0700
tags:
- statistics
description: We describe the Business applications of <b>paired t test</b>  here...
---

### Introduction

In this section, we describe a method for conducting a hypothesis test and constructing
a confidence interval when our observations come from two populations and are
**paired in some way**.                 


**What is the advantage of pairing observations?**         


Suppose that a taste test of two flavors is carried out. It seems intuitively plausible that if we let every person in our sample rate each one of the two flavors (with random choice of which
flavor is tasted first), the resulting paired responses will convey more information
about the taste difference than if we had used two different sets of people, each group
rating only one flavor. Statistically, when we use the same people for rating the two
products, we tend to remove much of the extraneous variation in taste ratings—the
variation in people, experimental conditions, and other extraneous factors—and concentrate
on the difference between the two flavors. When possible, pairing the observations
is often advisable, as this makes the experiment more precise

### 8–1


A market research study is undertaken to test which of two popular electric
shavers, a model made by Norelco or a model made by Remington, is preferred
by consumers. A random sample of **25** men who regularly use an electric shaver, but
not one of the two models to be tested, is chosen. Each man is then asked to shave
one morning with the Norelco and the next morning with the Remington, or vice
versa. The order, which model is used on which day, is randomly chosen for each
man. After every shave, each man is asked to complete a questionnaire rating his
satisfaction with the shaver. From the questionnaire, a total satisfaction score on a
scale of 0 to 100 is computed. Then, for each man, the difference between the satisfaction
score for Norelco and that for Remington is computed. The score differences
**(Norelco score - Remington score)** are 15, -8, 32, 57, 20, 10, -18, -12, 60, 72, 38,
-5, 16, 22, 34, 41, 12, -38, 16, -40, 75, 11, 2, 55, 10. Which model, if either, is statistically
preferred over the other? How confident are you of your finding? Explain.

The Null hypothesis is that there is No preference among the brands. Therefore the differences between the **(Norelco score - Remington score)** is zero.

We calculate the t-statistic as provided below.        

{% highlight R %}

sample_mean = mean(c(15, -8, 32, 57, 20, 10, -18, -12, 60, 72, 38,
-5, 16, 22, 34, 41, 12, -38, 16, -40, 75, 11, 2, 55, 10))

sample_standard_dev = sd(c(15, -8, 32, 57, 20, 10, -18, -12, 60, 72, 38,
-5, 16, 22, 34, 41, 12, -38, 16, -40, 75, 11, 2, 55, 10))

population_mean = 0

n = 25

t_statistic = (sample_mean - population_mean)/ ((sample_standard_dev)/sqrt(n)) 

t_statistic
{% endhighlight %}

**Rejection region of the t test**

{% highlight R %}

qt(.025,n-1)
qt(.975,n-1)

{% endhighlight %}


The tstatistic is inside the rejection region. Therefore we **reject the NULL hypothesis**  that the differences between the **(Norelco score - Remington score)** is zero.        


### 8–3

Recent advances in cell phone screen quality have enabled the showing of
movies and commercials on cell phone screens. But according to the New York Times,
advertising is not as successful as movie viewing. Suppose the following data are
numbers of viewers for a movie (M) and for a commercial aired with the movie (C).
Test for equality of movie and commercial viewing, on average, using a two-tailed test
at $\alpha$ = 0.05 (data in thousands):              
M: 15 17 25 17 14 18 17 16 14          
C: 10 9 21 16 11 12 13 15 13

The Null Hypothesis is that there is no difference in the numbers of viewers for a movie (M) and for a commercial aired with the movie (C).


{% highlight R %}

M =c(15, 17, 25 ,17 ,14, 18, 17, 16 ,14)

C =c(10, 9 ,21, 16 ,11 ,12 ,13 ,15, 13)

D = M - C

sample_mean = mean(D)

sample_standard_dev = sd(D)

population_mean = 0

n = length(D)

t_statistic = (sample_mean - population_mean)/ ((sample_standard_dev)/sqrt(n)) 

t_statistic

{% endhighlight %}

**Rejection region of the t test**

{% highlight R %}

qt(.025,n-1)
qt(.975,n-1)

{% endhighlight %}

The tstatistic is inside the rejection region. Therefore we **reject the NULL hypothesis**  there is no difference in the numbers of viewers for a movie (M) and for a commercial aired with the movie (C).    


### 8–5

A nationwide retailer wants to test whether new product shelf facings are effective
in increasing sales volume. New shelf facings for the **soft drink Country Time** are
tested at a random sample of 15 stores throughout the country. Data on total sales of
Country Time for each store, for the week before and the week after the new facings
are installed, are given below:           


Store : 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15            

Before: 57 61 12 38 12 69 5 39 88 9 92 26 14 70 22        

After : 60 54 20 35 21 70 1 65 79 10 90 32 19 77 29         

Using the 0.05 level of significance, do you believe that the new shelf facings increase
sales of Country Time?            

The Null Hypothesis is that there is no difference in the total sales of
**Country Time** for each store, for the week before and the week after the new facings
are installed

{% highlight R %}

BeforeInstallations =c(57, 61, 12 ,38, 12, 69, 5 ,39, 88, 9 ,92 ,26, 14, 70,22)

AfterInstallations =c(60, 54, 20, 35, 21, 70, 1, 65, 79 ,10, 90, 32, 19, 77, 29 )

n= 15

D = BeforeInstallations - AfterInstallations

sample_mean = mean(D)

sample_standard_dev = sd(D)

population_mean = 0

t_statistic = (sample_mean - population_mean)/ ((sample_standard_dev)/sqrt(n)) 

t_statistic

{% endhighlight %}

**Rejection region of the t test**

{% highlight R %}

qt(.025,n-1)
qt(.975,n-1)

{% endhighlight %}

The tstatistic is outside the rejection region. Therefore we **CANNOT reject the NULL hypothesis**      



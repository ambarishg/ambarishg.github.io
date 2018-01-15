---
layout: post
title: unpaired t test
categories: Statistics
date: 2018-01-13 11:00:00 -0700
tags:
- statistics
description: We describe the Business applications of <b>unpaired t test</b>  here...
---

### Introduction

We discuss the cases when the samples cannot be paired.             


**Cases in Which the Test Statistic Is Z**

* The sample sizes n1 and n2 are both at least 30 and the population
standard deviations $$\sigma_1$$ and $$\sigma_2$$ are known.            

* Both populations are normally distributed and the population standard
deviations $$\sigma_1$$ and $$\sigma_2$$ are known.             

The formula for the test statistic Z is

$$Z = \frac{(\bar{X_1} - \bar{X_2}) - (\bar\mu_1 - \bar\mu_2)}{\sqrt(\sigma_1^2/{n_1}+\sigma_2^2/{n_2})  }$$


**Cases in Which the Test Statistic Is t**                

Both populations are normally distributed; population standard deviations
$$\sigma_1$$ and $$\sigma_2$$ are unknown, but the sample standard deviations S1 and S2 are
known.

**Case 1** when the population standard deviations $$\sigma_1$$ and $$\sigma_2$$ are equal       

$$t = \frac{(\bar{X_1} - \bar{X_2}) - (\bar\mu_1 - \bar\mu_2)}{\sqrt(S_p^2/(1/{n_1}+1/{n_2})}$$     

$${S_p}$$ is the pooled variance of the two samples

The degrees of freedom are $${n_1 + n_2 -1}$$

**Case 2** when the population standard deviations $$\sigma_1$$ and $$\sigma_2$$ are unequal      

$$t = \frac{(\bar{X_1} - \bar{X_2}) - (\bar\mu_1 - \bar\mu_2)}{\sqrt(S_1^2/{n_1}+ S_2^2/{n_2})}$$      

The r function is         


{% highlight R %}

calculateTStatistic = function(sample_mean1,sample_mean2,s1,s2,n1,n2)
{
  return ((sample_mean1 - sample_mean2)/sqrt( (s1*s1)/n1 + (s2*s2)/n2 ))  
}

{% endhighlight %}


The degrees of freedom is given by


{% highlight R %}

calculateDegreesofFreedom = function(s1,s2,n1,n2)
{
  term1 = s1 * s1/n1

  term2 = s2*s2/n2

  df = ((term1 + term2)^2) /(term1^2/(n1-1) + term2^2/(n2-1))

  return(df)  
}

{% endhighlight %}

### 8-11
Marcus Robert Real Estate Company wants to test whether the average sale
price of residential properties in a certain size range in Bel Air, California, is approximately
equal to the average sale price of residential properties of the same size
range in Marin County, California. The company gathers data on a random sample
of 32 properties in Bel Air and finds the sample mean = dollars 345650 and s = dollar 48500. A random sample of 35 properties in Marin County gives sample mean = 289440 and s equals dollar 87090. Is the average sale price of all properties in both locations approximately equal or not? Explain.

The Null Hypothesis is that the average sale price of all properties in both locations approximately equal.           


{% highlight R %}

sample_mean1 = 345650

sample_mean2 = 289440

s1 = 48500

s2 = 87090

n1 = 32 

n2 = 35

calculateTStatistic(sample_mean1,sample_mean2,s1,s2,n1,n2)

{% endhighlight %}

**Calculate the degrees of freedom**

{% highlight R %}

df = calculateDegreesofFreedom(s1,s2,n1,n2)

df

{% endhighlight %}


**Calculate the t statistic for $$\alpha$$ = 0.5**

{% highlight R %}

qt(.025,df)

{% endhighlight %}

The t statistic is 3.299556

The rejection region is less than -2.004756 and more than 2.004756

The t statistic is in the rejection region. Therefore we will **Reject the NULL Hypothesis** that the average sale price of all properties in both locations approximately equal.     


### 8-13

Many companies that cater to teenagers have learned that young people
respond to commercials that provide dance-beat music, adventure, and a fast pace
rather than words. In one test, a group of 128 teenagers were shown commercials featuring
rock music, and their purchasing frequency of the advertised products over the
following month was recorded as a single score for each person in the group. Then a
group of 212 teenagers was shown commercials for the same products, but with the
music replaced by verbal persuasion. The purchase frequency scores of this group
were computed as well. The results for the music group were **sample mean = 23.5 and s = 12.2**;
and the results for the verbal group were **sample mean = 18.0 and s = 10.5**. Assume that the two
groups were randomly selected from the entire teenage consumer population. Using
the alpha equal to 0.01 level of significance, test the null hypothesis that both methods of advertising are equally effective versus the alternative hypothesis that they are not equally
effective. If you conclude that one method is better, state which one it is, and explain
how you reached your conclusion.  


The Null Hypothesis is that the both methods of advertising are equally effective      


{% highlight R %}
sample_mean1 = 23.5

sample_mean2 = 18

s1 = 12.2

s2 = 10.5

n1 = 128 

n2 = 212

calculateTStatistic(sample_mean1,sample_mean2,s1,s2,n1,n2)

{% endhighlight %}

**Calculate the degrees of freedom**

{% highlight R %}
df = calculateDegreesofFreedom(s1,s2,n1,n2)

df
{% endhighlight %}

**Calculate the t statistic for $$\alpha$$ = 0..01**

{% highlight R %}

qt(c(.005,.995),df)

{% endhighlight %}

The t statistic is 4.239735

The rejection region is less than -2.596695 and more than 2.596695

The t statistic is in the rejection region. Therefore we will **Reject the NULL Hypothesis** that the the both methods of advertising are equally effective.     


**State which one it is, and explain how you reached your conclusion.**

The Null hypothesis is that the non music groups is better than music groups score

{% highlight R %}
sample_mean2 = 23.5

sample_mean1 = 18

s2 = 12.2

s1 = 10.5

n2 = 128 

n1 = 212

calculateTStatistic(sample_mean1,sample_mean2,s1,s2,n1,n2)

{% endhighlight %}

**Calculate the degrees of freedom**

{% highlight R %}
df = calculateDegreesofFreedom(s1,s2,n1,n2)

df
{% endhighlight %}

**Calculate the t statistic for $$\alpha$$ = 0.01**

{% highlight R %}

qt(.01,df)

{% endhighlight %}


The t statistic is -4.239735

The rejection region is less than -2.342157.

The t statistic is in the rejection region. Therefore we will **Reject the NULL Hypothesis that the  non music groups is better than music groups score**             

### 8–15

A fashion industry analyst wants to prove that models featuring Liz Claiborne
clothing earn on average more than models featuring clothes designed by Calvin
Klein. For a given period of time, a random sample of 32 Liz Claiborne models
reveals average earnings of 4,238.00 and a standard deviation of 1,002.50. For the
same period, an independent random sample of 37 Calvin Klein models has mean
earnings of 3,888.72 and a sample standard deviation of 876.05.  

a. Is this a one-tailed or a two-tailed test? Explain.
b. Carry out the hypothesis test at the 0.05 level of significance.
c. State your conclusion.
d. What is the p-value? Explain its relevance.
e. Redo the problem, assuming the results are based on a random sample of
10 Liz Claiborne models and 11 Calvin Klein models           

<hr/>

This is a one tailed hypothesis test since the Null Hypothesis is that the models featuring Liz Claiborne clothing earn on average more than models featuring clothes designed by Calvin
Klein             


We revise the Null Hypothesis so that it has a equality sign.            

<hr/>
The Null Hypothesis is revised to     

Models featuring clothes designed by Calvin Klein clothes earn less than or equal to models featuring Liz Claiborne clothing           

<hr/>

{% highlight R %}

sample_mean1 = 3888.72

sample_mean2 = 4238.00

s1 = 876.05

s2 = 1002.50

n1 = 37 

n2 = 32

calculateTStatistic(sample_mean1,sample_mean2,s1,s2,n1,n2)

{% endhighlight %}

**Calculate the degrees of freedom**

{% highlight R %}
df = calculateDegreesofFreedom(s1,s2,n1,n2)

df
{% endhighlight %}

**Calculate the t statistic for $$\alpha$$ = 0.05**

{% highlight R %}

qt(.05,df)

{% endhighlight %}
The rejection region is less than -1.66975        

Since the TStatistic is outside the rejection region. therefore we cannot reject the NULL hypothesis that Models featuring clothes designed by Calvin Klein clothes earn less than or equal to models featuring Liz Claiborne clothing             

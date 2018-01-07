---
layout: post
title: Normal Distribution
categories: Statistics
tags:
- statistics
description: We describe the <b>Normal Distribution</b>  here...
---

# Introduction

A normal distribution, sometimes called the bell curve, is a distribution that occurs naturally in many situations.            

The percentage of data that falls within a certain number of standard deviations from the mean is       
* 68% of the data falls within one standard deviation of the mean.          
* 95% of the data falls within two standard deviations of the mean.             
* 99.7% of the data falls within three standard deviations of the mean   

**Properties of a normal distribution**        

* The mean, mode and median are all equal.            
* The curve is symmetric at the center (i.e. around the mean, μ).              
*  Exactly half of the values are to the left of center and exactly half the values are to the right.     
* The total area under the curve is 1.                     


#Cumulative Density Function

From **Wikipedia** ,       

>
In probability theory and statistics, the cumulative distribution function (CDF, also cumulative density function) of a real-valued random variable X, or just distribution function of X, evaluated at x, is the probability that X will take a value less than or equal to x.

**pnorm** function calculates the **CDF(Cumulative Density Function)**        

This can be represented as 

![Probality Less Than P](..\img\ProbablityLessThanp.jpg)


## 4-23

Let X be a normally distributed random variable with mean 410 and standard deviation 2.              

Find the probablity that X will be between 407 and 415.

{% highlight R %}

p1 = pnorm(407, mean=410, sd=2)
p2 = pnorm(415, mean=410, sd=2)

p2 -p1
{% endhighlight %}


## 4-29

The number of votes cast in favor of a controversial proposition is believed to be approximately **normally distributed** with **mean 8000** and **standard deviation 1000**. The proposition needs at least 9322 votes in order to pass. What is the probablity that the proposition will pass ? (Assume numbers to be of continous scale)

{% highlight R %}

pnorm(9322, mean=8000, sd=1000)

{% endhighlight %}

This is the probablity that the number of votes would be **Less than or Equal to**  9322. For getting votes which are more that 9322 will be

{% highlight R %}

1- pnorm(9322, mean=8000, sd=1000)

{% endhighlight %}

## 4-33

Daily fluctuations of the French CAC-40 stock index from March to June 1997
seem to follow a normal distribution with mean of 2,600 and standard deviation of 50.
Find the probability that the CAC-40 will be between 2,520 and 2,670 on a random
day in the period of study

{% highlight R %}

p1 = pnorm(2520, mean=2600, sd=50)
p2 = pnorm(2670, mean=2600, sd=50)

p2 -p1
{% endhighlight %}


## 4-37

The daily price of orange juice 30-day futures is normally distributed. In
March through April 2007, the mean was 145.5 cents per pound, and standard
deviation is  25.0 cents per pound. Assuming the price is independent from day to
day, find P (x is less than 100) on the next day.


{% highlight R %}

pnorm(100, mean=145.5, sd=25)

{% endhighlight %}


# Standard Normal Distribution

Standard Normal Distribution is a normal distribution with **mean of 0 and standard deviation of 1**    

**1 Standard Deviation Probablity**   

{% highlight R %}

pnorm(1,mean=0,sd=1) - pnorm(-1,mean=0,sd=1)

{% endhighlight %}

The probability that a normal random variable will be within a distance
of 1 standard deviation from its mean (on either side) is 0.6826, or
approximately 0.68.


**2 Standard Deviations Probablity**   

{% highlight R %}

pnorm(2,mean=0,sd=1) - pnorm(-2,mean=0,sd=1)

{% endhighlight %}

The probability that a normal random variable will be within a distance
of 2 standard deviation from its mean (on either side) is 0.9544997, or
approximately 0.95.


**3 Standard Deviations Probablity**   

{% highlight R %}

pnorm(3,mean=0,sd=1) - pnorm(-3,mean=0,sd=1)

{% endhighlight %}

The probability that a normal random variable will be within a distance
of 3 standard deviation from its mean (on either side) is 0.9973002, or
approximately 0.97.

# Six Sigma


**6 Standard Deviations Probablity**   

{% highlight R %}

p1 = pnorm(6,mean=0,sd=1) 
p2 = pnorm(-6,mean=0,sd=1)

p1

p2

{% endhighlight %}

The probability that a normal random variable will be within a distance of 6 standard deviation from its mean (on either side) is 0.999999999


# Case Studies

## 4-45

Let X be a normally distributed random variable with mean 600 and variance 10,000. Find two values x1 and x2 such that **P(X is more  than x1)** is equal to 0.01 and **P(X is less than x2)** is equal to 0.05

{% highlight R %}

qnorm(.99,mean=600,sd=100) 
qnorm(.05,mean=600,sd=100) 

{% endhighlight %}

## 4–47   

The demand for high-grade gasoline at a service station is normally distributed
with mean 27,009 gallons per day and standard deviation 4,530. Find two values
that will give a symmetric 0.95 probability interval for the amount of high-grade
gasoline demanded daily.

{% highlight R %}

qnorm(.025,mean=27009,sd=4530) 
qnorm(.975,mean=27009,sd=4530) 

{% endhighlight %}


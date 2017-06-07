---
layout: post
title: Simple Exponential Smoothing 
categories: Statistics
tags:
- timeseries
- statistics
---
Simple exponential smoothing forecast is a forecasting technique which provides more weight to the **RECENT** values and less weights are applied to the older values.   

$$ {Y_t} $$ =  Actual value of y  at time t   
$$ {F_t} $$ =  Forecast value of y  at time t    
$$ {F_{t+1}} $$ =  Forecast value of y  at time t +1   

The method takes the forecast at time t and adds the error between the forecast and the actual. $$ \alpha $$ is the smoothing constant.$$ \alpha $$ takes values between 0 and 1.

$$  {F_{t+1}}=  {F_t}  + \alpha({Y_t} - {F_t}) $$     

The above equation can be recalculated to the following equation

$$
\begin{align*}
  {F_{t+1}}=  \alpha{Y_t} + \alpha(1- \alpha){Y_{t-1}} + \alpha(1- \alpha)^2{Y_{t-2}} + \\
  & \alpha(1- \alpha)^3{Y_{t-3}}  +  .......\\
  & + \alpha(1- \alpha)^{t-1}{Y_{1}} + ( 1- \alpha)^t F_{t}
\end{align*}
$$  

From the equation , it is evident that more weight is provided to the RECENT values and less weights are applied to the older values.



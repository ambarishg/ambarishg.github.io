---
layout: post
title: Holts Linear method
categories: Statistics
tags:
- ets
- statistics
- timeseries
---
Holt extended the Simple Exponential smoothing to include **trend** through the following technique.The forecast using two constants $$ \alpha $$ and $$ \beta $$ with values between 0 and 1 using the following equations

$$ {Y_t} $$ =  Actual value of y  at time t   
$$ {F_t} $$ =  Forecast value of y  at time t    
$$ {F_{t+1}} $$ =  Forecast value of y  at time t +1   

$$ {L_t} $$ =  Estimate of the level of the series at time t    
$$ {b_t} $$ =  Estimate of the slope of the series at time t    

**Level equation** ::   $$ {L_t} =  \alpha{Y_t} + (1- \alpha)({L_{t-1}} + {b_{t-1}}) $$ 

**Trend equation** ::  $$ {b_t} =  \beta({L_{t-1}} - {L_{t}}) + (1- \beta){b_{t-1}} $$ 

**Forecast equation**::  $$ {F_{t+m}} = {L_{t}} + {b_{t}}m $$



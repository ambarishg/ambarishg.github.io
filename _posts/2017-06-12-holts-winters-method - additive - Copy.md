---
layout: post
title: Holts Winters method ( additive )
categories: Statistics
tags:
- ets
- statistics
- timeseries
---
Holt Winters additive differs from the additive version in the seasonal component being added and subtracted instead of taking products or ratios. The Level and the Seasonal equation is changed while the Trend and Forecast equation remains the same.       

$$ {Y_t} $$ =  Actual value of y  at time t   
$$ {F_t} $$ =  Forecast value of y  at time t    
$$ {F_{t+1}} $$ =  Forecast value of y  at time t +1   

$$ {L_t} $$ =  Estimate of the level of the series at time t    
$$ {b_t} $$ =  Estimate of the slope of the series at time t       

**s** is the length of the seasonality (e.g. number of months or number of quarters in a year )   
$$ {S_t} $$ =  Seasonal component at time t  

**Level equation** ::   $$ {L_t} =  \alpha({Y_{t}} - {S_{t-s}}) + (1- \alpha)({L_{t-1}} + {b_{t-1}}) $$ 

**Trend equation** ::  $$ {b_t} =  \beta({L_{t-1}} - {L_{t}}) + (1- \beta){b_{t-1}} $$ 

**Seasonal equation** ::  $$ {S_t} =  \gamma({Y_{t}} - {L_{t}}) + (1- \gamma){S_{t-s}} $$ 

**Forecast equation**::  $$ {F_{t+m}} = ({L_{t}} + {b_{t}}m){S_{t-s+m}} $$



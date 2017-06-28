---
layout: post
title: Holts Winters method ( multiplicative )
categories: Statistics
tags:
- ets
- statistics
- timeseries
---
Holt Winters extended the Holts method to include **seasonality** through the following technique.The forecast uses three equations for level, trend and seasonality.     

$$ {Y_t} $$ =  Actual value of y  at time t   
$$ {F_t} $$ =  Forecast value of y  at time t    
$$ {F_{t+1}} $$ =  Forecast value of y  at time t +1   

$$ {L_t} $$ =  Estimate of the level of the series at time t    
$$ {b_t} $$ =  Estimate of the slope of the series at time t       

**s** is the length of the seasonality (e.g. number of months or number of quarters in a year )   
$$ {S_t} $$ =  Seasonal component at time t  

**Level equation** ::   $$ {L_t} =  \alpha(\frac{Y_t}{S_{t-s}}) + (1- \alpha)({L_{t-1}} + {b_{t-1}}) $$ 

**Trend equation** ::  $$ {b_t} =  \beta({L_{t-1}} + {L_{t}}) + (1- \beta){b_{t-1}} $$ 

**Seasonal equation** ::  $$ {S_t} =  \gamma(\frac{Y_t}{L_{t}}) + (1- \gamma){S_{t-s}} $$ 

**Forecast equation**::  $$ {F_{t+m}} = ({L_{t}} + {b_{t}}m){S_{t-s+m}} $$



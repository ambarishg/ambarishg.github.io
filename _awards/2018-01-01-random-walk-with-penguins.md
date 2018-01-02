---
layout: post
title: Random walk with Penguins
description: Honoured to win the <b>1st prize</b> in a Data Science competition <b>Random Walk of Penguins</b> hosted by DrivenData. Sharing the winning approach here...
---

Honoured to win the 1st prize in a Data Science competition [Random Walk of Penguins](https://www.drivendata.org/competitions/47/penguins/) hosted by [DrivenData](https://www.drivendata.org/). Sharing the winning approach here.              


# Introduction           

Penguins are among the most charismatic animals in the world and have captured the imaginations of news-makers, scientists, film producers, and the general public. Beyond their general intrinsic value, they are considered important ecosystem indicators. In other words, monitoring these beautiful species can tell us a lot about the general health of the Antarctic because penguins are important krill and fish predators, and changes (natural or anthropogenic) that influence prey abundance and environmental conditions will ultimately be detected through changes in distribution or population size.

Data on penguin populations are limited because most monitored colonies are near permanent research stations and other sites are surveyed only sporadically. Because the data are so patchy, and time series relatively short, it has been difficult to build statistical models that can explain past dynamics or provide reliable future predictions. The goal is to create better models to estimate populations for hard-to-reach sites in the Antarctic, and thereby greatly improve our ability to use penguins to monitor the health of the Southern Ocean!

This project is a collaborative effort between **Oceanites, Inc., Black Bawks Data Science Ltd., and Dr. Heather Lynch's lab at Stony Brook University**. Prize generously provided by **NASA (Award NNX14AC32G)**.

# Details of the data provided             

The data was provided for three types of penguins namely adelie penguin, chinstrap penguin, and gentoo penguin for 548 different sites in Antarctica from the year 1875 to 2013.  Overall there were 648 combinations of penguin types and sites. There were a lot of missing values in the data. The challenge was to populate the penguin population from 2014 to 2017.

# Model Overview         

The solution is divided into 2 major parts

* Imputation of the data         
* Model Building     

# Imputation of the data           

Before running the model, imputation of the data was done for each of the site and penguin type combinations. The imputations were done in the following order

* Stine in case of R models and Linear in case of Python models
* Last Observation Carried Forward in case of R models only
* Next Observation Carried Backward in case of R and Python models
* Replace by Zero in case of R models and Python model

# Model Building           

Built 5 models for each of the site and penguin type combination. Therefore for each of the 648 combinations of site and penguin type, the following models were built

* XGBoost in Python
* RandomForest in Python
* ARIMA in R
* ETS in R
* Prophet in R

An **average** for all of these models was created for every 648 combinations.


Thanks reading. If you still like it, please visit an interesting blog post in [DrivenData blog]( http://blog.drivendata.org/2017/08/28/random-walk-of-the-penguins/)
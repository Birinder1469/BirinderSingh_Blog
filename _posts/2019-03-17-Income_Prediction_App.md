---
layout: post
title:  "Income Prediction using Machine Learning"
date:   2019-03-17
excerpt: "Machine Learning"
tag:
- sample post
- post
- images
comments: true
---

## Motivation

The motivation to do the analysis is to build an entire pipeline starting from the Exploratory Data Analysis to choice of Machine Learning model and then deployment on a microservice Heroku so that it can be used for analysis by anyone. The task is to is to determine whether a person makes over $50k a year.


## Dataset
The dataset is available on the UCI website under the name of Adult Data Set/Census Income data.  
Link to the Data Set : [AdultDataSet](https://archive.ics.uci.edu/ml/datasets/adult)

Characteristics of the data are as shown below : <br>

![](../imgs/DataDscription1.PNG)

Out of the total 48842 entries, Training dataset contains 32561 and the remaining 16281 are the Test dataset entries.

I loaded the data and since its a binary classification problem I converted the entries with income <=$50 as  `0` and income >$50k as  `1` The training data set head is shown below :

![](../imgs/Head_UCI_Adultdata.PNG)



## Exploratory Data Analysis


<br>

![Data_available](../imgs/Data_available.png)

<br>

![Data_available_1](../imgs/Data_available_1.png)

<br>

![Data_available_1](../imgs/Analysis_Income_prediction.png)

<br>

![Data_available_1](../imgs/Analysis_Income_prediction_1.png)

<br>


![Data_available_1](../imgs/Analysis_Income_prediction_work_profile.png)

<br>

<center>

![Data_available_1](../imgs/Analysis_Income_prediction_workhours.png)

</center>

<br>

![Data_available_1](../imgs/Analysis_Income_predictionAge.png)

<br>

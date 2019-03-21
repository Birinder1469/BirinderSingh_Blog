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

The motivation to do the analysis is to build an entire pipeline starting from the Exploratory Data Analysis to choice of Machine Learning model and then deployment on a microservice [Heroku](https://www.heroku.com/) so that it can be used for analysis by anyone. The task is to is to determine whether a person makes over `$50k` a year.


## Dataset
The dataset is available on the UCI website under the name of Adult Data Set/Census Income data.  
Link to the Data Set : [AdultDataSetUrl](https://archive.ics.uci.edu/ml/datasets/adult)

Characteristics of the data are as shown below : <br>

![](../imgs/DataDscription1.PNG)

Out of the total `48842` entries, Training dataset contains `32561` and the remaining `16281` are the Test dataset entries.

I loaded the data and since its a binary classification problem I converted the entries with income `<=$50` to  `0` and income `>$50k` to `1` as can be seen in the target column. The training data set head with 16 columns is shown below :

![](../imgs/Head_UCI_Adultdata.PNG)

## Exploratory Data Analysis

The categorical columns such as ``` 'Occupation','Workclass', 'Education_Label', 'Education_Number',
       'Relationship', 'Race', 'Income_class'  ``` contain the following unique categories : <br>

![](../imgs/categorical_varoables.PNG)

The level of education has been represented in words `Education` as well as corresponding numeric value `Education-Number` where Pre school is considered as basic level of education with numeric value 1 and the largest value for the highest level of education attained which is `Doctorate`.

Lets see how much data is available for each of the variable.

<br>

![Data_available](../imgs/Data_available.png)

<br>

Native country column has majority of the data from United States.

![Data_available_1](../imgs/Data_available_1.png)

<br>

I notice some '?' in workclass and native country and occupation level. After these entries with '?'
I lost around 2399 rows of which most of them were from occupation column.
The target variable/Income_Class contains around 22600 entries for the category of people earning <\$50k and around 7500 entries of people earning more than \$50k. This is important observation indicating that our dataset is biased towards people earning less than $50k.

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

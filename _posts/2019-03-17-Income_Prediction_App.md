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

### Motivation

The motivation to do the analysis is to build an entire pipeline starting from the Exploratory Data Analysis to choice of Machine Learning model and then deployment on a microservice [Heroku](https://www.heroku.com/) so that it can be used for analysis by anyone. The task is to is to determine whether a person makes over `$50k` a year.


### Dataset
The dataset is available on the UCI website under the name of Adult Data Set/Census Income data.  
Link to the Data Set : [AdultDataSetUrl](https://archive.ics.uci.edu/ml/datasets/adult)

Characteristics of the data are as shown below : <br>

![](../imgs/DataDscription1.PNG)

Out of the total `48842` entries, Training dataset contains `32561` and the remaining `16281` are the Test dataset entries.

I loaded the data and since its a binary classification problem I converted the entries with income `<=$50` to  `0` and income `>$50k` to `1` as can be seen in the target column. The training data set head with 16 columns is shown below :

![](../imgs/Head_UCI_Adultdata.PNG)

### Exploratory Data Analysis

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
The target variable/Income_Class contains around 22600 entries for the category of people earning <\$50k and around 7500 entries of people earning more than \$50k. This is important observation indicating that our dataset is biased towards people earning less than \$50k.

Now lets see what proportion of people in each category earn in which income bracket.

![Data_available_1](../imgs/Analysis_Income_prediction.png)

<br>



![Data_available_1](../imgs/Analysis_Income_prediction_1.png)

<br>


![Data_available_1](../imgs/Analysis_Income_prediction_work_profile.png)

<br>

`Education`
The wealthy people are generally highly educated. Professors, Doctorate and or masters education
level people earn well  Lets investigate who among low education levels are wealthy what they do how come they can earn so much at such young age. Most of the people with education level less than 12th standard work in Private jobs

`Work class`
The Self employed people have a higher proportion of being rich (>50k $) followed by people working in Federal jobs

`Marital Status`
The Married couple from Armed forces and Civilian spouse are in high income category but the dataset contains very few entries for Armed force category hence we wont consider them as much of a valid observation

`Occupation`
The Executive and Managerial roles are the most paid ones it seems followed by  Professors and Protective services Some of the job categories such as Clerical jobs, farming fishing and Cleaners and handlers are not that much paid.

`Relation ship`
 Its a little surprising for me to see Husbands having less proportion than Wives with high income,
 I notice that the data for wives is just ~1400  entries and for the husbands is ~ 12500
 because of which the proportion is a little misleading

`Gender`
 The proportion of males with high income is more than the females

`Native Country`
 As we saw above the data for United states natives is overwhelmingly higher than other countries.
 The proportion of people who got wealthy (>$50k) from different natives is very high for France, Taiwan, Iran. Again its worth noting  that the data for each of these countries is too less to make a sane judgement.

<center>

![Data_available_1](../imgs/Analysis_Income_prediction_workhours.png)

</center>

`Hours per week`
 The people in the higher income group work mostly between 35-60 hours a week.
 This goes up to 100 as well but there are less of such people.

 `Race`
 We notice that we have too little data for races other than White(Figure A). Still I tried to compare the  proportions of each race who were wealthy (>50k$). For the whites ~ 26% people are earning >50k while from the available  data ~28% Asian Pac Islander earn greater than $50k

<br>

![Data_available_1](../imgs/Analysis_Income_predictionAge.png)

<br>

 `Income vs Age`
 Generally people between the age group of 30-50 are wealthy. The youngsters up to the age of 27 are under  the low income category. This makes sense as this is the age when the students are studying or just getting in  to the employment

 ### Fitting the Machine Learning model

Before i can apply any machine learning model i need to transform my data in the form that my machine learning model understands

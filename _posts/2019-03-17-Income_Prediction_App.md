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
*Figure A*

<br>

Native country column has majority of the data from United States.

![Data_available_1](../imgs/Data_available_1.png)
*Figure B*
<br>

I notice some '?' in workclass and native country and occupation level. After these entries with '?'
I lost around 2399 rows of which most of them were from occupation column.
The target variable/Income_Class contains around 22600 entries for the category of people earning <\$50k and around 7500 entries of people earning more than \$50k. This is important observation indicating that our dataset is biased towards people earning less than \$50k.

Now lets see what proportion of people in each category earn in which income bracket.

![Data_available_1](../imgs/Analysis_Income_prediction.png)
*Figure C*
<br>



![Data_available_1](../imgs/Analysis_Income_prediction_1.png)
*Figure D*
<br>


![Data_available_1](../imgs/Analysis_Income_prediction_work_profile.png)
*Figure E*
<br>

`Education`
The wealthy people are generally highly educated. Professors, Doctorate and or masters education
level people earn well  Lets investigate who among low education levels are wealthy what they do how come they can earn so much at such young age. Most of the people with education level less than 12th standard work in Private jobs

`Work class`
The Self employed people have a higher proportion of being rich (>\$50k) followed by people working in Federal jobs

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

![Data_available_2](../imgs/Analysis_Income_prediction_workhours.png)
*Figure G*
`Hours per week`
 The people in the higher income group work mostly between 35-60 hours a week.
 This goes up to 100 as well but there are less of such people.

 `Race`
 We notice that we have too little data for races other than White(Figure A). Still I tried to compare the  proportions of each race who were wealthy (>\$50k). For the whites ~ 26% people are earning >\$50k while from the available  data ~28% Asian Pac Islander earn greater than \$50k

<br>

![Data_available_1](../imgs/Analysis_Income_predictionAge.png)
*Figure H*
<br>

 `Income vs Age`
 Generally people between the age group of 30-50 are wealthy. The youngsters up to the age of 27 are under  the low income category. This makes sense as this is the age when the students are studying or just getting in  to the employment

### Transforming input for ML Model

Before I can apply any machine learning model I need to transform my data in the form that my machine learning model understands. As already discussed in the data set section I have total `48842` entries out of which Training dataset contains `32561` and the remaining `16281` are the Test dataset entries. For the transformation I applied the following transformations on both the training and test dataset together. Before training my ML model I will split them again so that the test dataset remains unseen.  

I did the following assignments to make my data ready to be fed into the ML model.

`Sex`

- Males : `1` <br>
- Females : `0`

` Race `

- Whites : `1`<br>
- Non Whites : `0` <br>

This assignment is because data is skewed with entries mostly for White people.

`Education`

The income bracket looks distinct for students up to standard 12th level of education followed by Associates and then high income group which includes people with Bachelors degree or above, Hence I am dividing this category into 3 classes.

- Preschool ,$$1^{st}-4^{th}$$,$$5^{th} - 6^{th}$$ ,$$7^{th}-8^{th}$$, $$9^{th}$$, $$10^{th}$$,  $$11^{th}, 12^{th} $$   : `0` <br>

- HS-grad,  Some-college,  Assoc-acdm,  Assoc-voc : `1` <br>

- Bachelors,  Masters,  Doctorate, Prof-school : `2`<br>

`Native_Country`

- United_States : `1` <br>
- Rest : `0`<br>

This is because most of the data is available for the United States natives.<br>

`workclass`

- Private : `0`

- State-gov, Federal-gov, Local-gov : `1`

- Self-emp-not-inc, Self-emp-inc, Without-pay, Never-worked : `2`

The people working in private sector jobs were put together in category 0. People working in one way or the other with the government were put in another category 1. Remaining people who were either self employed or without income were put together into category 1.

`Occupation`

- ' Priv-house-serv', ' Farming-fishing',' Armed-Forces',' Machine-op-inspct',' Other-service',' Handlers-cleaners', ' Adm-clerical' : `0`

- Craft-repair', ' Sales', ' Transport-moving : `1`

- Exec-managerial', ' Prof-specialty',  ' Protective-serv',' Tech-support : `2`

Looking at the Figure D specifically the distribution of income some occupations are believed to be earning high such as Managerial roles so I assigned them high pay category `2`. Similarly Middle `1` for Sales etc. and Lower Pay categories `0` for professions like Farming etc.

Lastly for

`Marital Status`

- Never-married : `0`
- Married-civ-spouse, Married-AF-spouse : `1`
- Divorced, Married-spouse-absent, Separated, Widowed : `2`


For the marital status I have assigned three categories. The unmarried people. The people in marriage and another category for those who have separated due to some reason.

After assigning categories to our feature variables we have our dataset in correct form to be used for building the Machine Leaning model. I am left with 11 features `age`, `workclass`, `education`, `marital-status`, `occupation`, `race`,
       `sex`, `capital-gain`, `capital-loss`, `hours-per-week`,
       `native-country` and 1 target variable `Income-Class` which is a binary class of people earning  `>\$50k` or `<=\$50k`.

A quick look at the final DataFrame containing 11 features and 1 target variable :

![](../imgs/Model_BuildingRead.PNG)

*Figure H*

### Fitting the Machine Learning model

After the transformation of the data above I got the DataFrame containing the train and test dataset. I split them again so I have Training DataFrame with 32561 rows and test dataset with 16281 rows.

For the training the model I split the training dataset into training and validation dataset by allocating 20% of the data to the validation dataset.

The [sklearn.model_selection.train_test_split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html) module was used for doing this split.
Since its a binary classification problem I will use the following models the prediction.

 1 - Logistic regresion <br>
 2 - Decision Trees / Random Forest <br>
 3 - XGBoost <br>

##### RandomForestClassifier

```
model=RandomForestClassifier()

model.fit(X_train,y_train)
print('The train score is : ', "{00:.2f}%".format(round(model.score(X_train, y_train),4)*100))
print('The Validation score is : ',"{00:.2f}%".format(round(model.score(X_valid, y_valid),4)*100))
print('The Test score is : ',"{00:.2f}%".format(round(model.score(X_test, y_test),4)*100))

```
Training the Random Forest  Classifier without optimization gives me the following accuracies :

```
The train score is :  93.87%
The Validation score is :  84.40%
The Test score is :  83.94%

```

As you can notice the Accuracy on the training dataset is ~94% where as the validation and test accuracies are quite low compared to the training accuracy. This could most likely be the case of Overfitting. Since we have not defined any maximum depth of the tree it has the freedom to do quite well on the training dataset but the generalization is not expected to be that great on any unseen data. To correct this let me do the Random Search of the best parameters : `Max_features`, `Max_depth`. 

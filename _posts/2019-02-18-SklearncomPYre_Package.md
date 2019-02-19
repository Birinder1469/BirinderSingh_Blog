---
layout: post
title:  " The Machine Learning Package - SklearncomPYre"
date:   2019-02-18
excerpt: "Python Package"
tag:
- sample post
- post
- images
comments: true
---

## Motivation

As a part of Master of Data Science student at The University of British Columbia I had to try out different machine learning models on the different datasets almost every week. I would try out different models compare the test scores and give my judgement as to which model could be used for further analysis. After doing this for couple of months I realized it was high time to make a package out of it and make my life easy by removing the redundant task of splitting the data trying different models and making comparison plot of accuracies.
This package provides functions to help make the early stages of model selection and exploration easier to cycle through and meaningfully compare.


## About the Package

__SklearncomPYre__ harnesses the power of <a href="https://scikit-learn.org/">scikit-learn</a>, combining it with <a href="https://pandas.pydata.org/">pandas</a> dataframes and <a href="https://matplotlib.org/">matplotlib</a> plots for easy, breezy, and beautiful machine learning exploration.A Python package facilitating beautifully efficient comparisons of machine learning classifiers and regression models. The package comprises of 3 functions which together have the capabilities to split the X (predictors) and y (target) inputs in the Train, Test and Validation datasets based on the input proportions given by the user. The package takes the input dictionary of the models user wants to fit and score on the data and additionally saves the bar plot of the Accuracy and Time taken to fit and predict these models. The details of each of these functions is given below.

### Dependencies
- `sklearn`
- `numpy`
- `matplotlib`
- `pandas`


### Installation & Usage

Please use the following command to install the package : <br>
`pip install git+https://github.com/Birinder1469/SklearncomPYre`

#### <a href="https://github.com/Birinder1469/SklearncomPYre/blob/master/SklearncomPYre/train_test_acc_time.py">Function 1:</a>   `train_test_acc_time()`

The purpose of this function is to compare different sklearn regressors or classifiers in terms of training and test accuracies, and the time it takes to fit and predict. The function inputs are dictionary of models, input train samples `Xtrain`(input features), input test samples `Xtest`, target train values `ytrain` and target test values `ytest` (continuous or categorical).  

The function outputs a beautiful dataframe with training & test scores, model variance, and the time it takes to fit and predict using different models.  <br>

  __Inputs:__

   - Dictionary of ML classifiers or regressors.
   - X train set, type: `Array-like `
   - Y train set, type: `Array-like`
   - X test set, type: `Array-like `
   - Y test set, type: `Array-like`

  __Outputs:__

  - Dataframe with 7 columns: (1) regressor or classifier name, (2) training accuracy, (3) test accuracy, (4) model variance, (5) time it takes to fit, (6) time it takes to predict and (7) total time. The dataframe will be sorted by test score in descending order.


#### <a href="https://github.com/Birinder1469/SklearncomPYre/blob/master/SklearncomPYre/comparison_viz.py">Function 2:</a> `comparison_viz()`

The purpose of this function is to visualize the output of `train_test_acc_time()` for easy communication and interpretation. The user has the choice to visualize a comparison of accuracies or time. It takes in a dataframe with 7 attributes i.e. model name, training & test scores, model variance, and the time it takes to fit, predict and total time.

Outputs a beautiful <a href="https://matplotlib.org">matplotlib</a> bar chart comparison of different models' training and test scores or the time it takes to fit and predict.

  __Inputs:__   

  - Dataframe with 7 columns: (1) regressor or classifier name, (2) training accuracy, (3) test accuracy, (4) model variance, (5) time it takes to fit, (6) time it takes to predict and (7) total time. Type: `pandas.Dataframe`
  - Choice of `accuracy` or `time`. Type: `string`

  __Outputs:__

  - Bar chart of accuracies or time comparison by models saved to root directory. Type: `png`

#### <a href= "https://github.com/Birinder1469/SklearncomPYre/blob/master/SklearncomPYre/split.py">Function 3:</a> `split()`

The function splits the training input samples `X`, and target values `y` (class labels in classification, real numbers in regression) into train, test and validation sets according to specified proportions.

Outputs four array like training, validation, test, and combined training and validation sets and four y arrays. <br>

  __Inputs:__

  - X data set, type: `Array like `
  - Y data set, type: `Array like`
  - proportion of training data  , type: `float`
  - proportion of test data , type: `float`
  - proportion of validation data, type: `float`<br>

  __Outputs:__  

  - X train set, type: `Array like`
  - y train, type: `Array like`
  - X validation set, type: `Array like`
  - y validation, type: `Array like`
  - X train and validation set, type: `Array like`
  - y train and validation, type: `Array like`
  - X test set, type: `Array like`
  - y test, type: `Array like`


### Contributors :

For any clarification please feel free to contact the contributors:

| Contributor                  | Github              |
| --------------------- |-----------------------|
| Birinder Singh | [birinder1469](https://github.com/Birinder1469) |
| Jes Simkin | [jessimk](https://github.com/jessimk) |
| Talha Siddiqui | [talhaadnan100](https://github.com/talhaadnan100) |

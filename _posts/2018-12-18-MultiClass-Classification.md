---
layout: post
title:  "Multi Class Text Classification - Scikit Learn"
date:   2016-03-18
excerpt: "Consumer review data"
tag:
- sample post
- post
- images
- test
comments: true
---

**Introduction**

I had previously worked with the Spam and Not Spam problems which were mainly binary classifications. I recently came across an interesting article on Medium and thought of trying the Multi class classification. In fact in the real world there is a more chance of encountering Multi Class and Multi label classifications rather than the simple binary classifications. In the following analysis the assumption is that the review belongs to only one class. Had it been multi class then we would call it multi label classification. For now I am only considering Multi class classification.
The analysis has been carried out in Python and Jupyter notebook. The well known scikit learn has been used for the machine leaning analysis.

**Data**

The data is available at [Data](https://catalog.data.gov/dataset/consumer-complaint-database). It is a big dataset with 15 product categories and for each of them different customer complaint narratives. I have used only the subset of it this dataset. In actual the dataset is imbalanced with each class having different examples for training but for now I have chosen only 5 most commonly occurring classes and chose 1000 examples of each. In short the final dataset that I worked with is balanced with 1000 examples to train on for each of the 5 classes.

**Analysis**

- Data Cleaning
The first step was loading the data in proper format in the Jupyter Notebook. I used the pandas library to load the csv file.The below snapshot shows how the dataframe looks upon loading. The two columns of our interest are :

 > Product
 > Consumer complaint narrative

![Customer_Review_dataset](../imgs/Consumer_dataframe.PNG)
*Consumer review snippet*

Based on the customer complaint narrative we intend to categorize the data in different product categories. I noticed there are several Null values in the Consumer complaint narrative which will not add any value to our training, hence I removed these Null values.
I assigned numeric values to the product categories in a separate column names : Product_id since in fact the python also treats the categorical variables as Numeric in the memory and while conducting any analysis.

The 3 main columns look like below :

![Customer_Review](../imgs/Customer_narrative.PNG)
*Consumer review snippet*

Next I checked how many examples I have for each category and the plot below shows the imbalanced categories.

![Customer_Review_Categories](../imgs/Complaint_Counts_with_titles.PNG)

You can notice there is a big imbalance between the categories. I chose the top 5 of those categories listed below and converted my data in balanced dataset.

- Credit reporting, credit repair services, or other personal consumer reports
- Debt collection
- Mortgage
- Credit reporting
- Student loan

I chose 1000 examples of each of these classes and constructed a dataframe of 5000 rows.


- Machine Learning 

**References:**

I got the inspiration from the following article : [Medium_post](https://towardsdatascience.com/multi-class-text-classification-with-scikit-learn-12f1e60e0a9f)

---
layout: post
title:  "Big Data Processing with Apache Spark"
date:   2020-10-25
excerpt: "How Spark came to my rescue"
tag:
- sample post
- post
- images
comments: true
---

*In progress*

*Alert - this blog is going to be a little long. It will showcase all the research I had done to understand Spark as well.*

# Taking Data Processing to next level

## What led me to discover Apache Spark and its power of parallel computing?

I am an experienced Data Scientist and I have been at the forefront of managing the entire data science project life cycle including defining project scope, identifying data requirements and acquisition, data cleaning, feature engineering, Machine Learning model building, evaluating and deploying.

This time around in one of the projects we had to analyze the high frequency data and build a machine learning model pipeline. I started with a sample to understand the data structure.

But soon I realized it was not going to be possible scale what I was doing on the entire dataset. Talking to my peers I came across Dask, an open source library for parallel computing written in Python and Koalas, which is the pandas DataFrame API for handling Big Data. Very recently Koalas has been highlighted as a good alternative to PySpark as there is no learning curve for the user if you already know pandas. Check: [Koalas - pandas API on Apache Spark](https://github.com/databricks/koalas).

However in this blogpost I will share with you the working of PySpark and overview of the structure of the Spark architecture.


![](../imgs/apache_spark.png)


<img align="center" src="../imgs/apache_spark.png" width="500" height="300"  />


<p align="center">
  <img width="5" height="5" src="../imgs/apache_spark.png">
</p>

## Spark architecture


## Used Case - Data loading, wrangling, ML model building and deploying





## References

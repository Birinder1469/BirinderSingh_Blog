---
layout: post
title:  "Comparison of Distributions "
date:   2019-04-20
excerpt: "Population, Sample and Sampling distribution comparison"
tag:
- sample post
- post
- images
comments: true
---

<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Motivation</span>

<span style="color:black; font-family: Tahoma;font-size:1.1em;">
I have been in the state where I could not distinguish among the Population, Sample and Sampling distributions. In the following synthetic experiment I will try to differentiate between them.</span>

<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Population Distribution </span>

<span style="color:black; font-family: Tahoma;font-size:1.1em;">Let us create a synthetic dataset to investigate how much time on an average the people of a locality spend exercising. The below code creates a virtually simulated population data (exercise_data) where the response variable is the number of hours spent per week on exercising by each of the 1,000,000 residents. We also create a resident_id with a unique number for each person in the data set. The hours of exercising come from two separate normal distributions with different mean and standard deviations.</span>

``` python
n = 1000000;

y1 = rnorm(n, 4, 2) ;
y2 = rnorm(n, 10, 1)

w = rbinom(n, 1, .4)
X = w*y1 + (1-w)*y2

excercise_data <- tibble(resident_id = seq(from = 1, to = n, by = 1),
                                           hours = X) %>%
    filter(hours > 0) # Taking only postive entries as time has to be positive

print('The data looks like:')
head(excercise_data)

```

<span style="color:black; font-family: Tahoma;font-size:1.1em;">The distribution of hours spent exercising by 1,000,000 residents is the population distribution. Let us see how it looks.</span>

<br>
<p align="center">
  <img src="../imgs/population_distributions.PNG">
</p>
<br>


<span style="color:black; font-family: Tahoma;font-size:1.1em;"> We notice a bimodal distribution which is expected as we extracted the exercise hours from two separate normal distributions. The mean of the hours of exercise for the entire population is 7.67 hours. </span>

<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Sample Distribution </span>


<span style="color:black; font-family: Tahoma;font-size:1.1em;">From the population we take 1 sample of size 100 (randomly choose 100 residents). Now we can plot the hours of exercise for these 100 residents. This would be our Sample distribution.</span>



<br>
<p align="center">
  <img src="../imgs/sample_distributions.PNG">
</p>
<br>

<span style="color:black; font-family: Tahoma;font-size:1.1em;">This is a plot from just one sample chosen at random from the population. The mean can be different for different samples. For the sample displayed above the mean is 7.9 hours. We cannot conclude anything about the population mean just by looking at one sample distribution.</span>


<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Sampling Distribution </span>


<span style="color:black; font-family: Tahoma;font-size:1.1em;">We obtain 10,000 samples each comprising 100 residents which means our sample size is 100. We plot the mean of each of these 10,000 samples. This distribution of the means in our case would be called the sampling distribution.</span>

<br>
<p align="center">
  <img src="../imgs/sampling_distributions.PNG">
</p>
<br>

<span style="color:black; font-family: Tahoma;font-size:1.1em;">Above plot is a plot of the means of the 10,000 samples. We obtain the mean of the means and we notice it is quite close to the population mean which is 7.67 hours. This is because of the central limit theorem. The central limit theorem states that when an infinite number of successive random samples are taken from a population, the sampling distribution of the means of those samples will become approximately normally distributed with mean μ (same as the population mean) and standard deviation same as the population standard deviation as the sample size (N) becomes larger, irrespective of the shape of the population distribution.</span>

<span style="color:black; font-family: Tahoma;font-size:1.1em;">In our case the population distribution is bimodal but the sampling distribution still comes out to be Normal.</span>
<br>

<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Summary</span>
<br>

<p align="center">
  <img src="../imgs/distributions_comparisons.PNG">
</p>
<br>


- <span style="color:black; font-family: Tahoma;font-size:1.1em;">First is the population distribution, second plot is the sample of size 100 randomly chosen out of the population. Third is the plot of the means of the 10,000 samples collected out of the population where each sample is of size 100.</span>


- <span style="color:black; font-family: Tahoma;font-size:1.1em;">The population distribution is showing the hours spent exercising by 1,000,000 residents vs the count of the residents in different bins. The mean of the population distribution is 7.67 hours.</span>


- <span style="color:black; font-family: Tahoma;font-size:1.1em;">The Sample distribution comprises of 100 residents and we see the hours spent exercising by each of them. The mean for this case could vary a lot and it is 7.9 hours for the sample above.</span>


- <span style="color:black; font-family: Tahoma;font-size:1.1em;">The sampling distribution shows a normal distribution with its mean same as the mean of the population. In sampling distribution we have 10,000 samples of size 100 whose mean each has been computed and plotted on X axis.</span>

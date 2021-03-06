---
layout: post
title:  "What is a Monte Carlo Simulation"
date:   2019-10-15
excerpt: "Simulations"
tag:
- sample post
- post
- images
comments: true
---


*Draft Version, blog is still in progress*

## Monte Carlo Simulation

### Finding the Area
Based on my understanding, Monte Carlo Simulation is a technique to estimate the parameter of interest(otherwise difficult to compute) by carrying out computations on random numbers picked repeatedly from a distribution. Sounds complicated right. Let me make it a little more intuitive. Lets say if we want to find the area of a Square, what can do what we have been doing since high school which is to use the formula $$Side^2$$. Or alternately we can count and sum total number of points(many, many points) enclosed in the square. Ideally both of them will give us the same and correct answer. What if I now ask the area of the Circle enclosed within the Square. Again using our high school knowledge we can either use $$\pi r^2$$. Or if we already know the area of the square we can roughly find the proportion of randomly picked points lying within the circle and this proportion will give us of the area of the Circle given the area of Square.


In the figure given below we see the same happening. I have randomly picked 10,100,1000, 10000 points within the square from a uniform distribution meaning every point has equal probability of being picked. Now the proportion of points lying within the Circle will give me the area of the Circle given the area of the square.





| --  | --  |
| ![](../imgs/Circle_10.png)  | ![](../imgs/Circle_100.png)  |
| ![](../imgs/Circle_1000.png)  | ![](../imgs/Circle_10000.png) |

You may argue that this is not very useful. What is the big deal with estimating the area of Circle using this complicated approach you suggested. But what if I tell you to get me the area of the snowflake given below. Do you know the formula to estimate the area of a Snowflake. At least I do not. I have to get into complicated geometry and find a way to estimate the area of a Snowflake. However if you use the technique I suggested above we can easily estimate the area of the Snowflake.  

Another observation is that more the number of random numbers/points we pick, better will be our estimation of the area of the Snowflake. Isn't it cool.

|-- | -- |
| ![](../imgs/Snowflake_10.png)  | ![](../imgs/Snowflake_100.png) |
| ![](../imgs/Snowflake_1000.png)  | ![](../imgs/Snowflake_10000.png)  |


### Application in Coin Toss experiment
We have always believed that a fair coin toss has 50% probability of showing up `Heads` and 50% probability of showing up `Tails`. What that means is that if we carry out the experiment many times then half of the times I should get `Heads` and the other half of the times I should get `Tails`. Let us see if that is True.

In the below experiment we are going to flip the coin multiple times and initially assuming the coin is fair(probability of `Heads` showing up is 50%). After multiple flips we will see the proportion of `Head`.

```python

# number of trials, probability of each trial being 0.5
n_flips, probability_of_heads = 1, 0.5  
n_experiments= 10000

# we are using the binomial distribution, where the outcome will be either 0 or 1 with the probability of 50%.

s = np.random.binomial(n_flips, probability_of_heads, n_experiments)

# result of flipping a coin n=1 time, tested n_flips=10000 times.

experiment_outcome= np.where(s==1, 'Heads', 'Tails')
print(experiment_outcome)
```

```python
['Tails' 'Tails' 'Heads' ... 'Heads' 'Heads' 'Tails']
```

In the experiment above we used the Binomial distribution where the outcome would be either 0 or 1 with the probability defined as 50% in the above case. Of the outcome is 1 we hae defined it as `Heads` and `Tails` otherwise.

Now lets find out the proportion of times we got `Heads`.

```python

prop_heads=sum(experiment_outcome=='Heads')/len(experiment_outcome)
print(prop_heads)
```


```python
0.4
```

We obtain the proportion of `Heads` showing up is 0.4. But this experiment was only performed 10 times. Lets increase the number of experiments to 1,00,000.

Carrying out the experiment 1,00,000 times we get:


```python
n_flips, probability_of_heads = 1, 0.5  
n_experiments= 100000

# we are using the binomial distribution, where the outcome will be either 0 or 1 with the probability of 50%.
s = np.random.binomial(n_flips, probability_of_heads, n_experiments)

# result of flipping a coin n=1 time, tested n_flips=10000 times.
experiment_outcome= np.where(s==1, 'Heads', 'Tails')

prop_heads=sum(experiment_outcome=='Heads')/len(experiment_outcome)
print(prop_heads)
```


```python
0.5035
```


Now we get the proportion of `Heads` showing up as 0.5035 which is quite close to the 0.5 we had initially assigned.

Lets do another simulation, lets increase the probability of `Heads` showing up as 70% now. In case some one is trying to cheat us with an Unfair coin. Lets see what the proportion of `Heads` showing up in that case is.

```python
n_flips, probability_of_heads = 1, 0.7  
n_experiments= 100000

# we are using the binomial distribution, where the outcome will be either 0 or 1 with the probability of 50%.

s = np.random.binomial(n_flips, probability_of_heads, n_experiments)

# result of flipping a coin n=1 time, tested n_flips=10000 times.

experiment_outcome= np.where(s==1, 'Heads', 'Tails')

prop_heads=sum(experiment_outcome=='Heads')/len(experiment_outcome)
print(prop_heads)
```

```python
0.70073
```


That's amazing. Now out of 1,00,000 coin flips we got `Heads` 70% of the times.



### Bayesian Inference in Practice
If frequentist and Bayesian inference were programming functions, with inputs being statistical problems, then the two would be different in what they return to the user. The frequentist inference function would return a number, representing an estimate (typically a summary statistic like the sample average etc.), whereas the Bayesian function would return probabilities.

For example, in our debugging problem above, calling the frequentist function with the argument "My code passed all 𝑋 tests; is my code bug-free?" would return a YES. On the other hand, asking our Bayesian function "Often my code has bugs. My code passed all 𝑋 tests; is my code bug-free?" would return something very different: probabilities of YES and NO. The function might return:

```
YES, with probability 0.8; NO, with probability 0.2

```

This is very different from the answer the frequentist function returned. Notice that the Bayesian function accepted an additional argument: "Often my code has bugs". This parameter is the prior. By including the prior parameter, we are telling the Bayesian function to include our belief about the situation. Technically this parameter in the Bayesian function is optional, but we will see excluding it has its own consequences.




The Jupyter notebook with the above analysis is available on my GitHub at: [Monte_Carlo_Simulation_GitHub](https://github.com/Birinder1469/MonteCarlo_Simulation)

For feedback please contact me at birinder1469@gmail.com


## Reference:
1. https://towardsdatascience.com/a-zero-math-introduction-to-markov-chain-monte-carlo-methods-dcba889e0c50
2. https://matplotlib.org/3.1.1/gallery/lines_bars_and_markers/fill.html#sphx-glr-gallery-lines-bars-and-markers-fill-py

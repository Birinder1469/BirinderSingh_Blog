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

```
# number of trials, probability of each trial being 0.5

n, p = 1, 0.5  
n_flips= 10000

#
s = np.random.binomial(n, p, n_flips)

# result of flipping a coin n=1 time, tested n_flips=10000 times.

experiment_outcome= np.where(s==1, 'Heads', 'Tails')

print(experiment_outcome)

```

```

array(['Heads', 'Tails', 'Heads', ..., 'Tails', 'Heads', 'Heads'],
      dtype='<U5')

```



## Reference:
1. https://towardsdatascience.com/a-zero-math-introduction-to-markov-chain-monte-carlo-methods-dcba889e0c50
2. https://matplotlib.org/3.1.1/gallery/lines_bars_and_markers/fill.html#sphx-glr-gallery-lines-bars-and-markers-fill-py

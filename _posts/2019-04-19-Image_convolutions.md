---
layout: post
title:  "Image convolutions"
date:   2019-04-20
excerpt: "Convolutions"
tag:
- sample post
- post
- images
comments: true
---

<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Motivation</span>
I have always been fascinated by the concept of playing around with the images in python. I realized the images are nothing but an array of x height y width and 3 channels corresponding to each RGB Red Green and Blue colors. I tried playing around with my picture by applying some synthetic filters and got some funny results.


![](../imgs/image_conv_concept.PNG)

In the below images the pictures are of size 200 by 200.


<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Horizontal filter</span>

First I applied horizontal filter shown below on my image. The horizontal filter comprises of 0.1 value 10 times in horizontal direction. This way every pixel value is being being averaged by 0.1 times its
![](../imgs/horizontal_conv_filter.PNG)

![](../imgs/horizontal_conv.PNG)



<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Vertical filter</span>
![](../imgs/vertical_conv_filter.PNG)

![](../imgs/vertical_conv.PNG)

<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Identity filter</span>
![](../imgs/identity_conv_filter.PNG)

![](../imgs/identity_conv.PNG)



<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Averaging filter</span>
![](../imgs/average_conv_filter.PNG)

![](../imgs/average_conv.PNG)


<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Edge detection filter</span>
![](../imgs/edge_detection_filter.PNG)

![](../imgs/edge_detection.PNG)

<span style="color:black; font-family: Tahoma;font-size:1.1em;">The code is available on my GitHub repository: [GitHub Repository](https://github.com/Birinder1469/web_scraping_GOT)</span>
<br>
<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Reference</span>

<br>

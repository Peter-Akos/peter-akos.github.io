---
layout: post
title: Our Team has Qualified for the Finals of the Morgan Stanley Quant Challenge
---
I'm happy to announce that our team, Compacto has qualified for the finals of the Morgan Stanley Quant Challenge. Being part of the 8 best teams out of more than a hundred makes me so proud of the amazing people that I worked with in the last few weeks and I want to share what we've been working on.

## Let's start by introducing the team
1. **Ács Hunor**: Responsible for the data visualizations.

2. **Magyari-Sáska Attila**: Responsible for the model for soybeans.

3. **Gagyi Levente Lóránt**: Responsible for the model for oats.

4. **Péter Ákos**: I was responsible for the corn model and for managing the project.

## The problem

The task was to predict the yield for corn, soybeans and oats under multiple weather scenarios, based on historical data.

We were given coordinates to weather stations and the data recorded by them, in some cases going back more than a century. Also we received coordinates to counties and data about the yearly crop yield for oats, soybeans and corn.

We also received some example weather scenarios and our task was to predict the yield for corn, soybeans and oats.

----

## Our Solution

To tackle this challenge, we had to create a model that works like this:
weather scenario -> crop yield

We decided to go with 3 separate models for the 3 different types of crop: corn, soybeans and oats.

### 1. Using as much data as we can

Our first problem was matching the weather stations to the counties. The data at the stations contained a lot of missing values and since they weren't build at the same time, recorded data from different times. To use as much data as we can, we decided to do it the following way:
- get the closest 4-5 stations to each county
- for each year, check if data exists for the given station
- take the average of the stations that had data

This way we can use most of our data, while ensuring that the data that we use is relevant, since being close to the place the crop was harvested at.

<img src="/images/Counties and Stations.png" alt="Alt text" style="display:block; margin:auto;width:360px;" />

There exists a clear relation between the weather and the yield, higher temperatures and more precipitation leads to higher yield.


<div style="text-align:center">
  <img src="/images/Average Yearly Precipitation.png" alt="Alt text 1" style="width:340px;" />
  <img src="/images/AverageCornYieldMap.png" alt="Alt text 2" style="width:340px;" />
  <img src="/images/Average Yearly Temperature.png" alt="Alt text 2" style="width:340px;" />
</div>  

### 2. Cleaning the data of other biases

If we plot the yearly average yield, we can see that as it got better and better with time. This is due to better technology: seeds and fertilizers. When we train the models, we want the input data to only contain the variability of the weather, so that our model learns to predict based on the weather, not based on the year. 

To do this, we fit a linear regression on the yearly average yield for each of the crops and substract from each yield the slope times the years to 1950, since our data starts then.


<div style="text-align:center">
  <img src="/images/oats-regression.png" alt="Alt text 2" style="width:340px;" />
  <img src="/images/corn-regression.png" alt="Alt text 1" style="width:340px;" />
  <img src="/images/soybeans-regression.png" alt="Alt text 2" style="width:340px;" />
</div>  



### 3. Training the models

We trained a bunch of models:
- Linear Regression
- Perceptron
- Gradient Boosting
- Long-Short Term Memory

Here are the results for corn:

<table style="margin: 0 auto; border-collapse: collapse;">
  <tr>
    <th style="text-align:center;">Model name</th>
    <th style="text-align:center; padding-left: 10px; padding-right: 10px;">Mean-Squared Error</th>
    <th style="text-align:center; padding-left: 10px; padding-right: 10px;">R-squared</th>
  </tr>
  <tr>
    <td style="text-align:center;">Linear Regression</td>
    <td style="text-align:center; padding-left: 10px; padding-right: 10px;">2.24e+22</td>
    <td style="text-align:center; padding-left: 10px; padding-right: 10px;">-1.07e+19</td>
  </tr>
  <tr>
    <td style="text-align:center;">Perceptron</td>
    <td style="text-align:center; padding-left: 10px; padding-right: 10px;">219.222</td>
    <td style="text-align:center; padding-left: 10px; padding-right: 10px;">0.871</td>
  </tr>
  <tr>
    <td style="text-align:center;">HBGB</td>
    <td style="text-align:center; padding-left: 10px; padding-right: 10px;">248.969</td>
    <td style="text-align:center; padding-left: 10px; padding-right: 10px;">0.917</td>
  </tr>
  <tr>
    <td style="text-align:center;">LSTM</td>
    <td style="text-align:center; padding-left: 10px; padding-right: 10px;">25.57</td>
    <td style="text-align:center; padding-left: 10px; padding-right: 10px;">0.925</td>
  </tr>
</table>


And here are the losses for the LSTM:

<div style="text-align:center">
  <img src="/images/corn-loss.png" alt="Alt text 1" style="width:440px;" />
</div>  





In the end we ended up choosing the Long-Short Term Memory, since that was the most accurate.

If you want to learn more, please read the [paper](https://drive.google.com/file/d/1uYFck13EBt0yTMGcFjFRf3ExtCFT6LX8/view?usp=sharing){:target="_blank"} or check out the [repository](https://github.com/Peter-Akos/quant-challenge){:target="_blank"} on github.


If you have any comments or questions, feel free to write it to me.





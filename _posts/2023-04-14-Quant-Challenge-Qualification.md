---
layout: post
title: Our Team has Qualified for the Finals of the Morgan Stanley Quant Challenge
---

I'm happy to announce that our team, Compacto has qualified for the finals of the Morgan Stanley Quant Challenge. Being part of the 8 best teams out of more than a hundred makes me so proud of the amazing people that I worked with in the last few weeks and I want to share what we've been working on.

## Let's start by introducing the team
1. **Ács Hunor**: Data Visualization expert, he made the plots that you can see in the paper.

2. **Magyari-Sáska Attila**: Responsible for the model for soybeans.

3. **Gagyi Levente Lóránt**: Responsible for the model for oats.

4. **Péter Ákos**: I was responsible for the corn model and for managing the project.

## The problem

We were given coordinates to weather stations and the data recorded by them, in some cases going back more than a century. Also we received coordinates to counties and data about the yearly crop yield for oats, soybeans and corn.

We also received some example weather scenarios and our task was to predict the yield for corn, soybeans and oats.

To tackle this challenge, we had to create a model that works like this:
weather scenario -> crop yield

We decided to go with 3 separate models for the 3 different types of crop: corn, soybeans and oats.

Our first problem was matching the weather stations to the counties. The data at the stations was contained a lot of missing values and  
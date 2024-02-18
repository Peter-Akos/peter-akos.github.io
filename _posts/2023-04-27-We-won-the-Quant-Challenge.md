---
layout: post
title: We have won the Quant Challenge
---

As you can know from the last post, we have qualified for the finals of the [Morgan Stanley Quant Challenge](https://www.quantchallenge.hu/){:target="_blank"}. I'm very happy to announce, that after an eventful weekend at Budapest, we have managed to win the competition. 

I'd just like to say that I deeply appreciate the work of my fellow teammates, [Attila](https://www.linkedin.com/in/attila-magyari-s%C3%A1ska-a89380199/){:target="_blank"}, [Huni](https://www.linkedin.com/in/%C3%A1cs-hunor-0ab3a8246/){:target="_blank"} and [Lóri](https://www.linkedin.com/in/gagyi-lorant/){:target="_blank"} and also I would like to thank the organizers for the fantastic comptetition that they have put together for us: the subjects, the office, the prizes, the whole environment was just a great experience for me. I enjoyed how teams from different cities and universities have came to Budapest to put their data analyst skills to the test.

Also, our whole team is thankful to the people from [Mathias Corvinus Collegium](https://mcc.ro/en/){:target="_blank"} for encouraging us and for taking care of the costs of our trip, so we could really spend our time preparing for the competition.

I'll make this post a bit more personal than the last one and talk also about my experiences, not just our solution.

# The Place

The competition was held in the [Morgan Stanley Office at Budapest](https://www.morganstanley.com/about-us/global-offices/europe-middle-east-africa/hungary){:target="_blank"}, a building with a nice view across the Danube river.


<div style="text-align:center">
  <img src="/images/team-working.jpeg" alt="Description of the image" width="472px" />
  <img src="/images/office-danube.jpeg" alt="Description of the image" width="420px" />
  <p> Here you can see us concentrating and me with the Danube</p>
</div>  

# The Task

Our task was to find the optimal number of options to purchase, to hedge the risk of farmers to climate change. We had to do this for 3 different weather scenarios. Each time we had 7 put and 7 call options and we needed to somehow reduce the risk. What does reducing the risk mean? It means that somehow you still get paid, even in bad market conditions, in our case when the price of corn is low. To ensure this, our solution also had to comply with the lower limits on the 10th and 25th percentile of the income, ensuring that we are indeed reducing the risk.

# Our Solution

We figured out two things from the beginning: 
- it is not worth it to buy both put and call options, since that means that we are betting against ourself and all we do by this is pay for the options
- we should focus on [put options](https://www.investopedia.com/terms/p/putoption.asp), as we get paid good if the price is high so we should bet on the price being low

So our task is basically a **search problem**, we need to find the 7 values that **maximize the expected value of our income function**, while **conforming to the limits** on the 10th and 25th percentile of the income.

To do this, we randomly try to find some numbers that satisfy the requirements fot the percentiles and if we find one, we search the values around it, to see if it can get any better. Since we had 3 laptops, each of us had a scenario and we had to run this a lot of times. We have found some solutions in the first 2 hours so we just let it run and we were satisfied with the best results that we found, since it reduced the risk greatly and the expected income got smaller by just a bit. 

In a weather scenario there are 1000 possible outcomes for the yield and the price of the corn. If we plot the distribution of the income before and after buying options, we can clearly see their effect.

<div style="text-align:center">
  <img src="/images/expected-income.png" alt="Description of the image" />
  <p> Buying options greatly reduces our risk</p>
</div>  

Looking back, we could have improved the randomized finding of solutions that satisfy the percentile requirements, by searching the whole 7 dimensions, with bigger step size, for example 10, 20 or 30, depending on the speed. This way, we would have been more sure that we have found the optimal solution. Also, we didn't have the needed computing power, we could have used virtual machines from AWS or GC. 

# The Presentation

The contest had two parts: solving the problem and presenting the solution. We knew the presentation was going to be the tie-breaker, so we put great emphasis on making good slides and knowing what we want to say.

We started putting together the [slides](https://drive.google.com/file/d/1GYFjzHbPhA_7oMo9j-cAcr8FF68yC17O/view?usp=sharing){:target="_blank"} right after we had our first few good-enough solutions, and started from a template. We included a lot of charts, to get our point across, also the most convincing way to use data is to visualize it. One of my favourites is the histogram that you can see above, I think it greatly shows how options reduce the risk, making the low income parts disappear.

# Gallery

<div style="text-align:center">
  <img src="/images/presenting.jpeg" alt="Description of the image" />
  <p> Our team as we present the solution</p>
</div>  

<div style="text-align:center">
  <img src="/images/team.jpeg" alt="Description of the image" />
  <p> Happy faces </p>
</div>  

<div style="text-align:center">
  <img src="/images/keleti.jpeg" alt="Description of the image" />
  <p> Me at the Keleti Station, eating a well-deserved greasy bread</p>
</div>  

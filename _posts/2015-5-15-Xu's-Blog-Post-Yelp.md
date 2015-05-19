---
layout: post
title: Yelp Graph Critique
---

### Amazing Facts about Yelp:

Number of Yelp reviews (cumulative): 77.3 million reviews

Number of claimed local business on Yelp: 2.1 million

Number of countries that Yelp is available in: 27

Yelp has become the go-to place for many consumers looking for ratings and reviews of a wide variety of businesses. 

### How is rating distributed and what affects ratings in general?

![alt text](http://searchengineland.com/figz/wp-content/seloads/2014/02/Screen-Shot-2014-02-11-at-2.15.33-PM.png)

##### Critique of the Graph:

1. fails to mention which categories of businesses the 188 reviews belong to, leaving us guessing. 
2. no x-axis label
3. the bottom graph does not show which years these three months belong to. If the graph averages over all business categories per 30 days, then it does not give us much information

[Bad graph article](http://searchengineland.com/yelp-supersizes-profiles-makes-less-busy-184075)

##### My Improvement:

For this blog post I used Yelp restaurant reviews. The data were provided directly from Yelp as part of their [Dataset Challenge](http://www.yelp.com/dataset_challenge). The data was extremely large (over 1.6 million reviews, and 61,000 businesses), and the visualization was done using R and Shiny RStudio. My main question was how business-related metrics could be good measures of rating and price level prediction from a visual perspetive. 

After separating restaurants from the rest of the businesses, I decided to create a new dataset containing only those restaurants with actual price level and with more than 10 reviews. The rationale behind this was that the median number of reviews for all restaurants is 10.4 and I wanted to strike a balance between having enough restaurants and having enough information to work with. The new dataset consisted of 13,966 restaurants not only from the U.S, but also from countries such as Canada, the UK, and Germany. 

Here is the Yelp Restaurant Explorer that I created: 

![alt text](https://github.com/conan2014/conan2014.github.io/blob/master/images/Yelp_Explorer1.png)

The interactive Shiny graph allows users to tinker with different parameters in the dataset and hopefully gain some new insight. For instance, users could adjust number of reviews, star ratings, and price levels by moving the slider bar on the left-hand side. They could also select state and noise level to generate more detailed data. In addition, x and y axis can be adjusted to suit users' need. And more information would be displayed when the cursor hovers over one particular restaurant in the graph. 

In general, the graph demonstrates several pieces of conventional wisdom. For instance, plotting average star ratings against review counts shows a skewed normal distribution centered around star rating 4. This pattern is expected because restaurants with better reviews tend to have more customers and thereby more reviews, thus creating a positive cycle. And restaurants with consistent lower reviews get less and less traffic and eventually get weeded out, while restaurants with perfect reviews on average are very hard to come by because different reviewers might have different tastes and even a great restaurant cannot please everybody.

However, it goes without saying that there are several drawbacks with regard to the interactive graph. 1) Although each point representing a particular restaurant gives the corresponding average star rating and price level, there is no intuitive way to show the distribution of restaurants with different ratings or ratings across different states. Everything displayed are just lines populated by points and darker color indicates line segments in which more points are concentrated. 2) As both average rating and price level take on discreet values, points belong to the same set of ratings and price level are stacked on top of each other and the graph becomes uninterpretable as we select these two vairables as x and y axis (as shown below). These problems are the motivation that lead up to more informative graphs. 

![alt text](https://github.com/conan2014/conan2014.github.io/blob/master/images/Yelp_Explorer2.png)

##### How I generate Yelp Restaurant Explorer:

To generate the graph I leveraged Shiny's movie explorer's code on [github](https://github.com/rstudio/shiny-examples/tree/master/051-movie-explorer)

Here is [my source code](https://github.com/conan2014/conan2014.github.io/tree/master/Interactive-Graph)

![alt text](https://github.com/conan2014/conan2014.github.io/blob/master/images/Histogram1.png)

The top two histograms give us a rough idea of what the dataset looks like. The left one shows a skewed normal distribution centered between star ratings 3.5 and 4. The right one shows the distribution of numbers of restaurants reviewed across states. The top three states are Arizona, Nevada, and North Carolina where Phoenix, Las Vegas, and Charlotte reside. 

![alt text](https://github.com/conan2014/conan2014.github.io/blob/master/images/Boxplot2.png)

The boxplot on the left tells the story that ratings around 4 stars have lots of outliers that have more than 500 reviews. The most extreme outlier is a 4 star restaurant with 4,578 reviews. Thus if a restaurant is very popular and the number of reviews is just over the roof, the average rating is highly likely to be 4 stars, plus minus 0.5. 
The boxplot on the right clearly shows Nevada (NV) has every restaurant with more than 1,500 reviews, although Nevada does not have the most number of restaurants reviewed. 

![alt text](https://github.com/conan2014/conan2014.github.io/blob/master/images/Boxplot3.png)

We could trace an inverted parabola-shaped imaginary line connecting average price range (diamond-shaped) across star ratings from low to high. Between star rating 1 and 4, we see as ratings increase, price level generally goes up at a decreasing rate. But when star rating hit 4.5, we observe a dip in average price level that is on par with star rating 2.5. And when rating reaches 5, it is almost on par with rating 3. Such phenomenon suggests that there are other factors that might affect price level other than ratings. 

![alt text](https://github.com/conan2014/conan2014.github.io/blob/master/images/Boxplot4.png)

There are couple interesting trend observed from this boxplot. First, restaurants from outside of the U.S, such as Quebec (QC), Baden-Wurttemberg (BW) in Germany, and  Edinburgh (EDH), tend to have higher average price level, with the exception of Rhineland-Palatinate (RP) in Germany that has both the lowest mean and median price level. Secondly, in the U.S, East Coast states like Pennsylvania (PA) and South Carolina (SC) tend to have higher price level than their southwest peers. Lastly, price levels in the Mid-West are on par with their southwest counterparts, such as Wisconsin (WI) and Arizona (AZ). 

![alt text](https://github.com/conan2014/conan2014.github.io/blob/master/images/Boxplot5.png)

Some general trends:
1. States in the UK and Canada have higher median restaurant ratings than those in the U.S, while states in Germany have the same or lower median ratings than those in the U.S. All U.S states have the same median ratings (3.5 stars). 
2. Given its relatively fewer number of restaurants reviewed, Wisconsin still have extremely similar distribution to the top three states: Arizona, Nevada, and North Carolina (NC)
3. Baden-Wurttemberg and Pennsylvania have very similar distribution while Edinburgh and Quebec have very similar distribution. 



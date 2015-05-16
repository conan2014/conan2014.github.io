---
layout: post
title: Yelp Graph Critique
---

Amazing Facts about Yelp:

Number of Yelp reviews (cumulative): 77.3 million reviews
Number of claimed local business on Yelp: 2.1 million
Number of countries that Yelp is available in: 27

Yelp has become the go-to place for many consumers looking for ratings and reviews of a variety of businesses. 

How is rating distributed and what affect ratings in general?

![alt text](http://searchengineland.com/figz/wp-content/seloads/2014/02/Screen-Shot-2014-02-11-at-2.15.33-PM.png)

Critique of the Graph:
1. fail to mention 188 reviews of what category of business, leaving us guessing
2. no x-axis label
3. the bottom graph does not show which years these three months belong to. If it is averaging over all business categories per 30 days, then it does not give us much information

[Bad graph article](http://searchengineland.com/yelp-supersizes-profiles-makes-less-busy-184075)

My Improvement:

For this blog post I used Yelp restaurant reviews. The data were provided directly from Yelp as part of their [Dataset Challenge](http://www.yelp.com/dataset_challenge). The data was extremely large (over 1.6 million reviews, and 61,000 businesses), and the visualization was done using R and Shiny RStudio. My main question is how business-related metrics be good measures of rating and price level prediction from a visual perspetive. 

After separating restaurants from the rest of the businesses, I decided to create a new dataset containing only those restaurants with actual price level and with more than 10 reviews. The rationale behind this is that the median number of reviews for all restaurants is 10.4 and I wanted to strike a balance between having enough restaurants and enough information to work with. 

Here is the Yelp Restaurant Explorer that I created: 

![alt text](https://github.com/conan2014/conan2014.github.io/blob/master/images/Yelp_Explorer1.png)





![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.

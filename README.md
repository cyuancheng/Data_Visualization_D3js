###Project 6: Make Effective Data Visulization | Data Visualization and D3.js
- Author:  Chi-Yuan Cheng (cyuancheng AT gmail DOT com)
- Last updated: Oct 13, 2015

#### Summary

In this project, I used d3.js to create an explanatory data visualization from Airbnb dataset to analyze the price of accommodation places in San Francisco in 2015. This work includes a reflection of the theory and practice of data visualization, such as visual encodings, design principles and effective communication.

####Design

I took the 2015 Airbnb data in San Francisco from [Inside Airbnb](http://insideairbnb.com/san-francisco/), and combined data of SF area v.s. neighborhood from [sfarmis.com](http://www.sfarmls.com/docs/areamaps.htm) using R program. The subset of the data is listed below.
 
 ```
  room_type        Area       neighborhood    date    month  day  median_price median_aval reviews
1 Entire home/apt Central Castro/Upper Market  1/1/16     1   Fri        229.0    74.52055    1751
2 Entire home/apt Central Castro/Upper Market 1/10/16     1   Sun        207.5    74.10959    1976
3 Entire home/apt Central Castro/Upper Market 1/11/16     1   Mon        207.5    74.10959    1976
4 Entire home/apt Central Castro/Upper Market 1/12/16     1  Tues        207.5    74.10959    1976
5 Entire home/apt Central Castro/Upper Market 1/13/16     1   Wed        207.5    74.10959    1976
6 Entire home/apt Central Castro/Upper Market 1/14/16     1 Thurs        207.5    74.10959    1976
 ```
 
1. initial design.  (see [here])

The dataset contains lots of information. I chose to focus on the analysis of how the price varies with room type, location, and time. I used a pie chart to present room type data, since there are only three room types (Entire home/apt, Private room, and Shared room). I then used two row charts to present "price by day" and "price by month". To understand how the price varies with availability, location, and number of reviews, I decided to use a bubble chart to visualize these data, with the price on x-axis, availability on y-axis, and the total number of the reviews in specific location for the bubble area. I also used a bar chart to present the price distribution, and a line chart to present the price varies with time. Finally, I used a row chart on the right to show the price changes in each neighborhood. For this row chart, I sorted the price from high to low, so reader can immediately see the price ordering in the neighborhood under specific conditions. 

Because this project contains seven graphs, I used Bootstrap to develop and design the HTML, CSS, and JavaScript framework. I used [dc.js](https://dc-js.github.io/dc.js/) and [crossfilter](http://square.github.io/crossfilter/) to make interactive dashboard.

####Feedback


- What do you notice in the visualization?
- What questions do you have about the data?
- What relationships do you notice?
- What do you think is the main takeaway from this visualization?
- Is there something you don’t understand in the graphic?

####Resources



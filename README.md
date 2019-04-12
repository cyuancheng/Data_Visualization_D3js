## Project 6: Make Effective Data Visulization | Data Visualization and D3.js

- Author:  Chi-Yuan Cheng (cyuancheng AT gmail DOT com)
- Last updated: Nov 13, 2015
-  [Certificate](certificate-6.pdf)

### Summary

This project is to create an explanatory data visualization from Airbnb dataset to analyze the price of accommodation places in San Francisco in 2015. The purpose  is to demonstrate how the price of accommodations in San Francisco varies with room type, time, and/or location. 



### Final Version of Visualization
1. [Explanatory visualization of Airbnb data](http://cdn.rawgit.com/cyuancheng/Data_Visualization_D3js/master/index.html)
2. [Exploratory visualization of Airbnb data](http://cdn.rawgit.com/cyuancheng/Data_Visualization_D3js/master/index_re10.html)

### Design
#### 1. Data clean and manipulation

I took the 2015 Airbnb data in San Francisco from [Inside Airbnb](http://insideairbnb.com/san-francisco/), and data of SF neighborhood v.s. area from [sfarmis.com](http://www.sfarmls.com/docs/areamaps.htm). I first used R program to merge two data sets by neighborhood. The price outliners were then removed from the dataset by only including the price values within 95 % range. Finally, I grouped the data based on room type, area, neighborhood. The subset of the data is listed below.
 
 ```
  room_type        Area       neighborhood    date    month  day  median_price median_aval reviews
1 Entire home/apt Central Castro/Upper Market  1/1/16     1   Fri        229.0    74.52055    1751
2 Entire home/apt Central Castro/Upper Market 1/10/16     1   Sun        207.5    74.10959    1976
3 Entire home/apt Central Castro/Upper Market 1/11/16     1   Mon        207.5    74.10959    1976
4 Entire home/apt Central Castro/Upper Market 1/12/16     1  Tues        207.5    74.10959    1976
5 Entire home/apt Central Castro/Upper Market 1/13/16     1   Wed        207.5    74.10959    1976
6 Entire home/apt Central Castro/Upper Market 1/14/16     1 Thurs        207.5    74.10959    1976
 ```
 
#### 2. Design

**(1)  Initial visualization design (original [index.html] (http://cdn.rawgit.com/cyuancheng/Data_Visualization_D3js/master/index_re1.html))**
 
All the graphs are generated using [dc.js](https://dc-js.github.io/dc.js/), which is dimensional charting javascript library on top of D3.js. I used [crossfilter](http://square.github.io/crossfilter/) to quickly manipulate multi-dimensional data array, including filtering and grouping. These two unique tools allow me to make interactive dashboard very easily. Because this project contains seven graphs, I used [Bootstrap](http://getbootstrap.com) to design the HTML, CSS, and JavaScript framework. 

The data contains lots of information. I focus on the analysis of how the price varies with room type, location, and time. The reasons about why seven graphs are encoded are summarized below:

- **Bubble chart** (price vs. total number of review): It is the main figure in this visualization project. To understand how the price varies with location, number of review, and number of accommodation places, I decided to use a bubble chart to visualize these data, with the price per night on y-axis, number of review on x-axis, and the total number of accommodation places in specific location for the bubble radius.
- **Pie chart** (room type) : There are only three room types (Entire home/apt, Private room, and Shared room).  It would be easy to show the percentage of each room type by pie chart.
- **Row chart** (price by month): To show how the average price / night changes with month.
- **Row chart** (price by day): To show how the average price / night changes with day in a week.
- **Bar chart** (price distribution): To visualize the price distribution under selected conditions.
- **Line chart** (price varies with time): To monitor how the price changes with time under selected conditions.
- **Row chart** (price by neighborhood): To show how the price changes in each neighborhood. 

**(2) Revised visualization design based on feedback (revised [index.html] (http://cdn.rawgit.com/cyuancheng/Data_Visualization_D3js/master/index_re7.html))**

The discussion of which and why the changes were made are summarized below:

- I included how many room places are there in Airbnb above the pie chart, according to how selection goes, so that the reader can easily see how many rooms are available under selected conditions.
- For this row chart, I sorted the price from high to low, so reader can immediately see the price ordering in the neighborhood under specific conditions.
- Included year on the title (2015). This was missing in the original design.
- Added $ signs on every price axis, so reader can immediately realize which axis is price within multiple charts.
-  Turn off auto rescale function on x-axis and use identical x-axis scale for price-by-month and price-by-day charts, so that it would be easy to see how the price changes between two charts.
-  Modify the bubble chart. 
	- The original design for bubble chart was to compare price vs. number of review. But there seems to be no directly relevant between these two factors. therefore, in this revised design, I compare price vs. availability in this bubble chart.
	- To make the chart consistent among one another, I used price as x axis and availability as y axis. 
	- used square root of value to size the bubbles, so the bubble area represents the value (number of review). 
- Put pie chart, two row charts (price by month and price by day) on the top, and put bubble chart in the middle. That way, reader can first play with the value for room-type and month/date to see how the price changes on the bubble chart.
- Rounded all the values in the mouseovers. It is because availability, price, number of review should not have decimal.  
- Changed the gridlines weight to light dark, so the charts are consistent among one another.

**(3) Revised visualization design based on reviewer's comments, the 1st submission (revised [index.html](http://cdn.rawgit.com/cyuancheng/Data_Visualization_D3js/master/index_re8.html))**

- In order to tell stories from the visualization, I did more exploratory data analysis, and filtered out specific values to show explanatory charts. I then created link buttons that automatically adjust the plots.
- Turned off the BrushOn function and used the tooltip for line chart, so reader can see the specific values of price and date in the line chart.
- Mentioned the x-axis of bar chart can be extended by mouse.
- Used the same color of two row chart (price by month and price by day) to avoid confusing
- Changed the style for the text and title, so that reader can easily capture the message and story.

**(4) Revised visualization design based on reviewer's comments, the 2nd submission (revised [index.html](http://cdn.rawgit.com/cyuancheng/Data_Visualization_D3js/master/index_re9.html))**

- Draw noteworthy conclusions at the top of the visulization. The insights from the data are summarized below:
	- Renting entire home is more expensive than renting private room or shared room 
	- It is cheaper to visit SF during the off-peak season (Jan - Apr, Oct - Dec) or during the week (Mon - Thur) 
	- Renting private room in the most expensive area is about the same price as renting entire home in the least expensive area

**(5) Revised visualization design based on reviewer's comments, the 3rd submission (revised [index.html](http://cdn.rawgit.com/cyuancheng/Data_Visualization_D3js/master/index_re10.html) for original exploratory visualization,  [index.html](http://cdn.rawgit.com/cyuancheng/Data_Visualization_D3js/master/index_re11.html) for simple explanatory version)**

- Consistently used tabs in the codes to avoid "indentation wars"
- Deleted redundant comments in the code
- Fixed the bugs on the percentage of the pie chart, and change the pie chart to row chart for room-type data
- Added the reset to the filters in the "insight from the data" section 
- I revised the second insight, because it seems like that there is no strong seasonal trend in the data.
- I decided to use a simple explanatory visualization to present my story, as below:
	- Only present three graphs (a row chart for "room type", row chart for "price by month", and a row chart for "price by area" ). 
	-  The original exploratory visualization was provided as a link in the new html file.

**(6) Revised visualization design based on reviewer's comments, the 4th submission (revised [index.html](http://cdn.rawgit.com/cyuancheng/Data_Visualization_D3js/master/index.html) for explanatory version using dimple.js)**

- Constructed "explanatory graph" using [dimple.js](http://dimplejs.org), according reviewer's suggestion:
	- Dc.js is designed for exploratory dashboard visualization and might not be the best tool to make a explanatory visualization. Thus, I switched to dimple.js to make a new explanatory visualization. 
	- I showed the renting price at different area, room type and month using a **multi-category bar chart**.
	- In each bar chart, I showed area and room type on the x axis, and then sorted the x-axis from the least expensive area to the most expensive area. I presented each bar chart by month.
	- I found that renting the entire room in the least expensive area is equal or cheaper than renting the private room in the most expensive area ONLY during the off-peak season (I marked the months of off-peak season with red text). This is the main story I want to show in this visualization. I highlighted the text of this insight in yellow, so the reader can easily see this.
	- In each bar chart, I marked the price of the private room in the most expensive area by red circle, and the price of the entire room in the least expensive area by blue circle, so that the reader can compare these two values in each chart.
	- The reason I used the multi-category bar chart is because the reader can easily compare renting price at different area and room type in each chart. 
	- By comparing the price by month (between different bar chart), I found that the price pattern does not charge that much between each month, suggesting that the renting price does not have strong seasonality in SF. But as reviewer stated, a line chart (price v.s. month for different area) is a better way to show the time-series data, so I did not emphasize the seasonality in this visualization.
- I provided my original exploratory dashboard visualization as a link in the new html file, so the reader can access this visualization if they are interested.


### Feedback

I obtained lots of helpful feedback and comments from [Udacity discussion forum](https://discussions.udacity.com/t/project-feedback-visualization-of-airbnb-data-in-san-francisco/34570/4) and [Google+](https://plus.google.com/communities/116797052510270749486?gclid=Cj0KEQjwwIKxBRDKhOz7ytT30vkBEiQAT1NaPS05CAXdYdk1Yu7ymp6T8ZGMhTJ0lMeqMdwFyCpF2bsaAkHc8P8HAQ). The selected feedback and comments are below:


1. Andrew Lavers (Udacity discussion forum)
 
	- Top right bars - Price by Neighborhood. I suggest order from highest to lowest (if you want people to be surprised at the high prices) or lowest to highest if it is like airfares - we want the cheapest.
	- Perhaps add $ signs on every price axis (if this is simple)
	- price by month and price day
		- should have identical x axis (they are close but should be exactly the same) are these average prices?? 
		- the axis should stay same for all selections.

	- The bubble chart looks nice but I cant understand the story. 
		- The x axis label is "count" -- count of what?
		- When using bubbles it may be better to use square root of value to size the bubbles. Northeast looks huge but it actually is only about twice Central West
		- There must be some relationship between Total Number of reviews and count but I am not sure it is interesting. My guess is that count is number of properties available ... not number of stays. 
		- Central East has way more reviews -- there must be some reason which cannot be seen in the chart 
		- I think might try to replace the bubble chart with bars like Price by Neighborhood except summarized to "Region" and drop the "count" and "number of reviews" completely. you could consider boxplots to show price range by region instead of bars.
	- I would put the price by day and month and the room type (middle row) at the top. These tell the story that save about $20-30 per night, don't come in the summer, but it doesn't matter which weekday.
	- round all the values in the mouseovers (d3.format does percentages, numbers and money nicely)

	- The gridlines weight (light/dark) is inconsistent in the different charts. Try and get them the same by lightening the price charts. 
	- Try flipping the axis of the bubble chart so that price is horizontal and on the same scale as all the other charts - this is for consistency. (You may have to scale the bubble smaller to make it fit)

2. Jay Teguh (Google+)

	- How many room places are there in AirBnB? Perhaps a good idea to include this under Room Type chart.
	- What year was the data from?
	- Due to different sizes of the circles in price vs. availability, it is sometimes hard to compare price and availability between each data point. Maybe a button to disable sizes, in addition to a faster tooltip display would help.
	- Price varies with time could benefit from tooltips too. I use d3-tip in my project and it works really great (I did not use html default tip since it takes awhile to show them and users are impatient).
	- Remember that the rubric requires you to have a complete documentation of your functions. The functions in your projects seems to be sparsely commented as it is now. My reviewer suggested me to use jsdoc and that makes documentation really easy, but in your case you would need to put your js code into a separate file if you wish to do so.
	- As you get more feedback you'll notice several interesting findings readers have noticed. You can create stories from them, then later create quick-link buttons that will automatically adjust the plots to tell the story and pops up an explanation you wish to tell your readers (martini glass narrative structure).﻿

3. Piyush Agarwal (Google+)

	- The dashboard looks exhaustive, as there are so many charts. Maybe if you could arrange them in a better way and provide a detailed insight into each, that would be great.
	- I don't know the dataset but is it possible to figure out that what is the most busiest time for the bookings, i.e., at what time of the year there are max. number of people using these Airbnb locations.
	- Do people like staying in the shared rooms/private?
	- Number of reviews is higher in the Central East region as compared to any other region I have never been to SF, but from the visualizations, Presidio seems to be a very expensive and high-class neighborhood, as there are no shared/single rooms available there and also its very expensive.
	- There is a lot of variation in the Price/Night and it looks like you can find a place in San Francisco, starting from anywhere between $40 to about $400
	- Variation of price with time graph can be done better if we move the axis away from 0.
	- The colors are fading in Price by Month and Price by Day graphs. Not sure do they have some significance (like price is higher with darker colors)﻿


### Resources
1. [DC.JS GETTING STARTED AND HOW-TO GUIDE](https://dc-js.github.io/dc.js/docs/stock.html)
2. [Create Rich Interactive Visualisations](https://becomingadatascientist.wordpress.com/2013/05/21/create-rich-interactive-visualisations/)
3. [dimple.js](http://dimplejs.org)



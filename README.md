# Opentable_Forecasting
![opentable-logo](https://user-images.githubusercontent.com/100893109/178285523-d947d8c2-e970-497d-bc85-a449544bbc45.png)

# Overview
When Covid-19 hit the United States in March of 2020, everyone quarantined in their homes and the economy ground to a halt. One of the industries hit hardest by Covid was the food and restaurant industry. Restaurants operate on very small margins to begin with and to have to completely shut down for many months, was crushing, causing many to permanently close. 

# Business Problem
Opening a new restaurant takes a large amount of time and capital and maintaining a restaurant is extreamly difficult due to the long work hours and tight margins. Compounded with Covid, the restaurant industry has been crushed in the last 2 years. The entire country shutdown in March of 2020 and even onces cities started reopening, there were restrictions such as only essential businesses, mask mandates and the biggest restriction for restaurants, was that they could not operate at full capacity.

This analysis is going to use time series to determine how different city's politics, as it relates to Covid restrictions, has impacted how the city's food industry was affected during and post Covid. 

My stakeholder is the National Restaurant Association. They aim to represent and advocate for the more than 500,000 restaurant businesses they serve, by providing various resources such as Financial, Tax & Audit, Food Safety & Quality Assurance, HR and Sustainability. The National Restaurant Association can use this analysis to determine what resources are necessary and which cities most need them.  

My analysis will include 6 cities that are known to be "foodie cities", based off an article from June 2022: https://www.2foodtrippers.com/best-food-cities-in-the-us/.

The 6 cities analyzed include 3 Republican cities and 3 Democratic cities: Miami, Florida (R), Dallas, Texas (R), Phoenix, Arizon (R), New Orleans, Louisiana (D), Los Angeles, California (D), New York City, New York (D). 

![Cities_mapped](https://user-images.githubusercontent.com/100893109/178285593-21bb339f-7261-49b2-9486-92db6f435c0e.png)

# Data Understanding
In March of 2020, Opentable launched a "State of the Industry" project to illustrate how Covid has impacted restaurants. The data has been updated daily since early 2022 and my analysis includes data from 2/18/20 (when the project launched) through 7/7/22.

The data analyzed is a daily percent change, year-over-year comparison, with 2019 as the baseline. However, given that the day of the week is relevant for restaurant reservations, the same day of the same week is compared, not the same date. For example, Tuesday of week 11 in 2022 is being compared to to Tuesday of week 11 in 2019. If a restaurant had 100 reservations in 2019 and 40 on the same day of the same week in 2020, a -60% is listed.

Each city included has at least 50+ restaurants on the OpenTable network, however the data does not account for the changes in the number of restaurants on OpenTable per city. Many restaurants permanently closed during Covid, which could affect the number or resrvations in and of itself because there are less options. However with over 50+ restaurants on the network, it is unlikely this will have a big impact. The data also includes restaurants that have not gone out of business, but have still not reopened to customers, meaning that restaurant will have -100% listed.  

# Data Limitations
There are several limitations with this dataset.  
-First and most importantly is that there is only about 2.5 years of data. (February 2020-July 2022). This is not very much data to form an accurate model to predict future restaurant reservations.    
-Second, the restaurants used in the dataset are not necessarily the same for each year. A lot of restaurants went out of business during Covid and sometimes new ones went up in their place, which could affect the number of reservations overall.   
-Next, the type of cuisine was not analyzed, so certain types of restaurants could have done better or worse overall, or certain days of the week, based on promotions or special events.   
-Lastly, OpenTable did state that each city analyzed had at least 50+ restaurants in their network, however, the number of restaurants could have (and probably did) change dramatically from the baseline of 2019 to July 2022. This does not necessarily impact the number of reservations overall, because if there are 50+ restaurants in the city, people could have chosen one of the other restaurants with availability, but it is another limitation to take into account. 

# Covid Background/Restrictions

As stated above, the 6 cities I used in this analysis were Phoenix, Arizona; Miami, Florida; Dallas, Texas; New York City; Los Angeles, California; New Orleans, Louisiana.

![Health_vs_Economy_Scores](https://user-images.githubusercontent.com/100893109/178285761-9edffed2-acc9-452f-b8fe-299ee1293f31.png)

*The code for this graph is in the apendix

This graph is showing the health and economy scores for each of these states, reported by Politico. The health score is made up of # of deaths, hospital admissions, vaccinations and Covid testing. The economy score consists of State GDP (quarter-over-quarter change compared to 2019), unemployment and jobs (both as an average month-over-month change compared to 2019). 

The average scores across the entire United States is also plotted as a comparison.
As you can see in the graph, the three more conservative states, Arizona, Florida and Texas, have higher economy scores and lower health scores. Not suprisingly, these were also states that had fewer Covid restrictions and shorter shutdowns. The two more liberal states, New York and California had more Covid restrictions and therefore higher health scores but lower economy scores. The last state plotted was Louisiana, which is generally a conservative state, but New Orleans is a much more liberal city than the rest of the state and therefore had many more Covid restrictions than the rest of Louisiana. https://www.nola.com/news/coronavirus/article_fd14b8b2-934d-11eb-a45f-67ac65525d56.html

According to Politico, "What the scorecard shows is that the pandemic has played out in vastly different ways across America, and that those state decisions had real-life impacts. There was no optimal set of choices, no perfect path a governor or other state officials could have taken. Every choice came with negative consequences, some known ahead of time, some only discovered or appreciated months later...The answers weren’t obvious. State officials had limited information about the virus, and the trade-offs were difficult. Protect residents’ health and instruct them to stay home – but risk driving companies out of business and accelerating unemployment. Keep businesses open – but risk a rise in hospitalizations and deaths. Close schools to control spread – but risk damaging kids’ education."

What has become clear however is that cities with more restrictions (stay-at-home orders, limited dining capacity, mask requirements, etc) did experience lower rates of death and hospitalizations due to Covid, but they also tended to have worse economic outcomes.

"During the pandemic, Republican-led states tended to be more resistant to mask mandates and stay-at-home edicts while Democratic governors, by and large, embraced those public health precautions, even at the expense of the local economy." This is shown in my data, as restaurants in Republican cities had far more reservations than restaurants in Democratic cities. 

Also, not shockingly, cities that had fewer shutdowns and Covid restrictions in general, tended to have better economic outcomes than cities that imposed more public health restrictions. 

For more information on how  different cities and states responded to Covid and how that impacted their health, economy, education and social well-being, visit: https://www.politico.com/interactives/2021/covid-by-the-numbers-how-each-state-fared-on-our-pandemic-scorecard/# Covid Background/Restrictions

# EDA
![average_ _change](https://user-images.githubusercontent.com/100893109/178285999-c4ac46df-57aa-49af-b097-68d19af073a8.png)

This graph is showing the negative average change in reservations since 2019, with NYC having the largest decrease, 65% on average since 2019. As shown in this graph, the three more Democratic cities, New York, LA and New Orleans, have been hit signficantly harder, with many fewer reservations than the three conservative cities, Dallas, Phoenix and Miami.

![Number_of_Reservations](https://user-images.githubusercontent.com/100893109/178286229-d3df51f9-1391-4143-8c26-c2ff76df04cd.png)

All 6 cities are plotted on the same scale, with -1 to 0.6 on the X-Axis (the highest and lowest percent change) and 0-35 on the Y-Axis (the highest and lowest total # of weeks for each percent change). Cities that have histograms with values above 0 are cities that have (at any point since 2019) had more reservations week-over-week since 2019.  Phoenix (R) and Miami (R) have the highest values, with up to 50% more reservations at some points since 2019. New York City (D) does not have any data points above 0 and New Orleans (D), LA (D) and Dallas (R) have very few points above 0.

Reservations Per City

![Reservations_per_city](https://user-images.githubusercontent.com/100893109/178286558-c2948c1e-aac3-42cb-aa82-3dbb86e8b140.png)

While it is hard to differentiate between cities on this graph, it is helpful to see the general trends and the inital lockdown. Ths graph also shows when certain cities had steep drops at certain times. Further evaluation and research will need to be done to account for these drops.

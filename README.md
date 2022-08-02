# Opentable_Forecasting: Covid and Politics
![opentable-logo](https://user-images.githubusercontent.com/100893109/178285523-d947d8c2-e970-497d-bc85-a449544bbc45.png)

When Covid-19 hit the United States in March of 2020, everyone was quarantined in their homes, and the economy ground to a halt. One of the industries hit hardest by Covid was the food and restaurant industry, causing many restaurants to permanently close. 
This analysis will use data published by OpenTable, the popular restaurant reservation tool, to explore how Covid and a city's politics regarding Covid restrictions have impacted the restaurant industry during and post-Covid. Six cities were analyzed using a time-series model: 3 Democratic and 3 Republican cities.  

# Business Problem
The restaurant industry was one of the most heavily impacted by Covid. The entire country shut down for at least several months, which was crushing for restaurants that operate on small margins to begin with. Even once cities started reopening, many restrictions were put in place, such as only essential businesses, mask, and later vaccine mandates, and the most significant restriction for restaurants, was that they could not operate at full capacity. A city's politics played a prominent role in the Covid restrictions enforced, which in turn greatly impacted the outcome for the city's restaurant industry. The six cities used in this analysis were: Phoenix, Arizona (R); Miami, Florida (R); Dallas, Texas (R); New York City (D); Los Angeles, California (D); New Orleans, Louisiana (D).

The stakeholder for this analysis is the National Restaurant Association. They aim to represent and advocate for the more than 500,000 restaurant businesses they serve by providing various resources such as Financial, Tax & Audit, Food Safety & Quality Assurance, H.R., and Sustainability. The National Restaurant Association can use this analysis to determine what resources are necessary and which cities need them the most.  

Politico created "Covid scorecards," ranking each state's outcome since Covid with scores for health, the economy, social well-being, and education. Their data shows that states with more restrictions (such as stay-at-home orders, limited dining capacity, and mask requirements) experienced lower rates of death and hospitalizations due to Covid. However, they also tended to have worse economic outcomes, and there was a direct correlation between these scores and a state's politics. According to Politico, "During the pandemic, Republican-led states tended to be more resistant to mask mandates and stay-at-home edicts while Democratic governors, by and large, embraced those public health precautions, even at the expense of the local economy." 

![Health_vs_Economy_Scores](https://user-images.githubusercontent.com/100893109/178285761-9edffed2-acc9-452f-b8fe-299ee1293f31.png)

As shown in this graph, the three more conservative states, Arizona, Florida, and Texas, have higher economy scores and lower health scores. Not surprisingly, these were also states with fewer Covid restrictions and shorter shutdowns. The two more liberal states, New York and California had more Covid restrictions and therefore higher health scores but lower economic scores. The last state plotted was Louisiana, which is generally a conservative state, however, New Orleans is a much more liberal city than the rest of the state and therefore had many more Covid restrictions than the rest of Louisiana. The Politico scorecards were only created on a state-wide basis, and the entire United States was also plotted as a point of reference.

For more information on how different states responded to Covid and how that impacted their health, economy, education, and social well-being, visit https://www.politico.com/interactives/2021/covid-by-the-numbers-how-each-state-fared-on-our-pandemic-scorecard/.


# Data Understanding
In March 2020, OpenTable launched a "State of the Industry" project to illustrate how Covid has impacted the restaurant industry. The data has been updated daily since early 2022, and this analysis includes data from 2/18/20 (when the project launched) through 7/7/22.

The data is reported as a daily percent change, year-over-year, with 2019 as the baseline. However, given that the day of the week is relevant for restaurant reservations, the same day of the same week is compared, not the same date. For example, Tuesday of week 11 in 2019 is compared to Tuesday of week 11 in 2021. If a restaurant had 100 reservations in 2019 and 40 on the same day of the same week in 2021, a -60% is listed.

This analysis used data published by OpenTable to compare the number of restaurant reservations in 6 cities: Phoenix, Arizona (R); Miami, Florida (R); Dallas, Texas (R); New York City (D); Los Angeles, California (D); New Orleans, Louisiana (D).

### Negative Average % Change in Reservations Since 2019

![average_ _change](https://user-images.githubusercontent.com/100893109/178285999-c4ac46df-57aa-49af-b097-68d19af073a8.png)

As shown in this graph, the three Democratic cities, New York, Los Angeles, and New Orleans, have been hit significantly harder, with a 46%-65% average decrease in reservations from February 2020-July 2022, compared to the three Republican cities, Dallas, Phoenix, and Miami which only had a 7%-28% decrease. 

### Average % Change in Reservations in 2022

![2022_Average_ _Change](https://user-images.githubusercontent.com/100893109/178813553-3fa90ac4-6503-4301-a3c1-9e3f755dba6e.png)

Looking at just January-July of 2022, the six cities have the same order of average % change, with the most significant decrease in NYC. However, Miami and Phoenix have a positive difference in reservations in 2022, from the 2019 baseline, and Dallas has a much smaller average loss. The three Democratic cities still have a significant decrease in the number of reservations, however, throughout 2022, it is 19%-46% as opposed to 46%-65% over the entire 2.5 years since Covid began.

### Total Number of Reservations for Each Percent Change Since 2019:

![Number_of_Reservations](https://user-images.githubusercontent.com/100893109/178286229-d3df51f9-1391-4143-8c26-c2ff76df04cd.png)

These six histograms show the total number of reservations for each percent change. All six cities are plotted on the same scale, with -1 to 0.6 on the X-Axis (the highest and lowest percent change) and 0-35 on the Y-Axis (the highest and lowest total # of weeks for each percent change).

Cities that have histograms with values above 0 are cities that have (at any point since February 2020) had more reservations week-over-week than in 2019. Phoenix (R) and Miami (R) have the highest values, with up to 50% more reservations at some points since 2019. New York City (D) does not have any data points above 0%, and New Orleans (D), Los Angeles (D), and  Dallas (R) have very few points above 0%.

### Reservations Over Time per City:

![Reservations_per_city](https://user-images.githubusercontent.com/100893109/178286558-c2948c1e-aac3-42cb-aa82-3dbb86e8b140.png)

While it is hard to differentiate between cities on this graph, it is helpful to see the general trends and the initial lockdown. This graph also shows when certain cities had steep drops at certain times. Further evaluation and research is needed to account for these drops.


## Data Limitations
This dataset has several limitations.  
-First and most importantly is the lack of data: 2.5 years of data (February 2020-July 2022) is not enough to form an accurate model to predict future restaurant reservations.  
-Second, the restaurants used in the dataset are not necessarily the same for each year. Many restaurants went out of business during Covid, and sometimes new ones went up in their place, which could affect the number of reservations overall.  
-Next, the data did not include the type of cuisine, so certain kinds of restaurants could have done better or worse overall or on certain days of the week, based on promotions or special events.  
-Lastly, OpenTable stated that each city analyzed had at least 50+ restaurants in its network; however, the number of restaurants could have, and probably did, change dramatically from the baseline of 2019 to July 2022. This does not necessarily impact the number of reservations overall since there are 50+ restaurants in the city, which means customers could have chosen one of the other available restaurants, however, it is another limitation to consider. 

# Modeling and Evaluation
This analysis used time series to predict restaurant reservations. The baseline model used was a shift of 1, which means that the forecasting will be the data from the week before. Next, ARIMA and SARIMA models were created, with the SARIMA models performing significantly better than the baseline and ARIMA models. 

The mean absolute errors for the six models were between 5.65%-13.06%. However, because this analysis only included about 2.5 years of data, this is not enough to create a very accurate time-series model. This resulted in predictions very close to a 0% change from the 2019 baseline. Because the actual values were reasonably close to the 2019 baseline scores, this explains why the mean absolute error values were 5-13%.  

## Forecasted Values:

![Forecasting_mean_scores](https://user-images.githubusercontent.com/100893109/178802228-19547130-b273-4b5b-a943-9763b9e6a0b3.png)

With the exception of Miami, the Republican cities have higher forecasting means than the Democratic cities, meaning these cities have bounced back more since Covid, however, the predictions for all six cities are above the baseline. It is important to note from this graph that even the highest percent change (Dallas) is less than 3% above the 2019 baseline, so the predictions for all six cities are relatively close to the 2019 values.


# Conclusion
Although the model's predictions were not very strong, the other data analysis can be helpful for the National Restaurant Association. As we saw in the "Average % Change in 2022" graph, Miami and Phoenix are the only cities with positive average % changes in 2022, and Dallas, as well as the 3 Democratic cities, had negative average % changes, with NYC having the most significant % loss. 

Because the National Restaurant Association does not have the authority to impact Covid restrictions imposed on restaurants, they can instead use these findings to determine how to help restaurants in different cities overcome the restrictions. As these findings show, Democratic cities will need more help recovering from Covid because of the restrictions they endured. These resources could be in the form of financial assistance, marketing resources, consumer trends, and resources to help track inventory and cost of goods to optimize their profit.

# Future Steps
1) Because this forecast includes the shutdown in early 2020, another model could be made starting after the shutdown to see if that produces more accurate predictions.
2) Point intervention for the big dips
3) Python's "holidays" package to create an exogenous variable within the SARIMA models.
4) To avoid some of the limitations discussed above, collecting and analyzing the data at a more granular level would be helpful, such as comparing the same restaurants from 2019 through 2022 or the same types of cuisine.
5) Take into account the weather in each city. This analysis included five warm-weather cities and one colder city (N.Y.), however, NYC did have heated outdoor dining. If we compared only cities with similar weather, we might be able to create a more accurate comparison because of the availability of outdoor dining.
6) This data can also be graphed on Tableau to have a user interface that the National Restaurant Association or restaurants in these cities can use to see the forecasting.
7) Lastly, more data would be necessary to create an accurate model. Short of waiting for more data, if I had the data from before 2019, that could also help to predict the future. Another way to have more usable data would be to combine the reservation data for all the Democratic cities analyzed, and all the Republican cities analyzed to compare the two groups as a whole.

#### Final Notebook: https://github.com/julietday422/Covid_Politics_Opentable_Forecasting/blob/main/Project_notebook.ipynb
#### Presentation: https://github.com/julietday422/Covid_Politics_Opentable_Forecasting/blob/main/Presentation.pdf

## Disclaimer: 
I am not affiliated with OpenTable or the National Restaurant Association in any way and do not have any legal rights to the logo.

## Repository Navigation
```bash
├── Data  
│   └── Opentable_dataset.csv.csv 
├── Images  
│   └──Forecasts
│        └── DAL_forecast.png
│        └── LA_forecast.png
│        └── MIA_forecast.png
│        └── NOLA_forecast.png
│        └── NYC_forecast.png
│        └── PHO_forecast.png
├── └──Test_Preds
│        └── DAL_final_model_test_preds.png
│        └── LA_final_model_test_preds.png
│        └── MIA_final_model_test_preds.png
│        └── NOLA_final_model_test_preds.png
│        └── NYC_final_model_test_preds.png
│        └── PHO_final_model_test_preds.png
│   └──2022_Average_&_Change.png
│   └──Cities_mapped.png
│   └──Forecasting_mean_scores.png
│   └──Health_vs_Economy_Scores.png
│   └──Number_of_Reservations.png
│   └──Reservations_per_city.png
│   └──average_&_change.png
│   └──opentable-logo.png
├── Presentation.pdf 
├── Project_notebook.ipynb
├── README.md
├── environment.yml
```

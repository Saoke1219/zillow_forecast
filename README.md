# FORECASTING HIGH-VALUE ZIP CODES BY UTILIZING TIME SERIES ANALYSIS

![4-modern-doral-model-60-exterior](https://github.com/Saoke1219/zillow_forecast/assets/144773775/98f6ad7f-58cc-4f42-9e3b-46ee27b37bbe)

# OVERVIEW


In the dynamic world of real estate investments, strategic decision-making is crucial for achieving success and maximizing returns. With the advent of advanced data analytics techniques, such as time series modeling, investors now have powerful tools at their disposal to forecast market trends and identify lucrative opportunities. In this project, we delve into the domain of real estate investment by harnessing the wealth of information provided by the https://www.zillow.com/research/data/ to unlock actionable insights for prospective investors.

# BUSINESS UNDERSTANDING


Our client is an investor with a budget of 300,000 dollars who, after reading articles such as (https://www.worldbizmagazine.net/post/miami-dade-best-region-in-north-america-for-investment-2021-2022), believes that Miami-Dade County presents the most promising investment opportunities in North America. Inspired by these insights, they seek to leverage data science and real estate expertise to make informed investment decisions in the area.

# BUSINESS PROBLEM


The client aims to capitalize on the potential highlighted in the articles by identifying lucrative investment opportunities within Miami-Dade County. Specifically, they are interested in properties with high returns on investment (ROI) within a 3-year timeframe.

# WORKFLOW

## 1. Data Preparation

+ Imported the necessary libraries
+ Loading the dataset
+ Checked for the general data shape.
+ Checked the dataset info
+ Filtered the chosen zipcodes
+ Checking and handling missing values in our dataset.
+ Checked for duplicates

## 2. Data Pre-processing
Conducted some analysis and visualizations to find out how many cities are in Miami-Dade and how the Zip codes are distributed among the cities. The number of cities in Miami-Dade county are 33 with Miami having the highest number of Zip code distribution. Since our client has a budget of 300,000 dollars, we will further filter our dataframe and only consider Zip codes that fall under this budget.

## 3. EDA and Visualization

What is the price history of the Miami-Dade county since 1996?

**Q1.What are the historical trends in property values and ROI in Miami-Dade County, as highlighted in the articles?**

![download (1)](https://github.com/Saoke1219/zillow_forecast/assets/144773775/9db0dad5-5028-4f01-b26b-60af62e1b89c)

From the visualization above, it's evident that there was a peak in housing prices just before the recession hit in 2008. This recession led to a significant decline in housing prices, but since around 2011, we've observed a gradual recovery with prices steadily rising. However, it's noteworthy that as of the latest data, housing prices have yet to reach the peak levels observed in 2007 before the recession occurred.

**Q2.Which zip codes exhibits the most substantial growth post-2007 recession, aligning with our objective of identifying the best-growing zip codes while minimizing risks associated with economic downturns such as recessions?**

![download (2)](https://github.com/Saoke1219/zillow_forecast/assets/144773775/afb8247a-c508-48c6-b377-9f46b5157c68)

The above pie plot shows the zipcodes that had the highest steady growth after emerging from the 2007 recession. Here are the 5 best perfoming Zip codes;

1.zipcode 33055 had a percentage ROI of 7.7%

2.zipcode 33161 had a percentage ROI of 7.2%

3.zipcode 33177 had a percentage ROI of 6.9%

4.zipcode 33189 had a percentage ROI of 6.8%

5.zipcode 33162 had a percentage ROI of 6.7%

We went ahead to filter the data for the selected Zip codes and time period.





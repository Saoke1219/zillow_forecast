# FORECASTING HIGH-VALUE ZIP CODES BY UTILIZING TIME SERIES ANALYSIS

![4-modern-doral-model-60-exterior](https://github.com/Saoke1219/zillow_forecast/assets/144773775/98f6ad7f-58cc-4f42-9e3b-46ee27b37bbe)

# OVERVIEW


In the dynamic world of real estate investments, strategic decision-making is crucial for achieving success and maximizing returns. With the advent of advanced data analytics techniques, such as time series modeling, investors now have powerful tools at their disposal to forecast market trends and identify lucrative opportunities. In this project, we delve into the domain of real estate investment by harnessing the wealth of information provided by the [Zillow daset](https://www.zillow.com/research/data/ )to unlock actionable insights for prospective investors.

# BUSINESS UNDERSTANDING


Our client is an investor with a budget of 300,000 dollars who, after reading articles such as (https://www.worldbizmagazine.net/post/miami-dade-best-region-in-north-america-for-investment-2021-2022), believes that Miami-Dade County presents the most promising investment opportunities in North America. Inspired by these insights, they seek to leverage data science and real estate expertise to make informed investment decisions in the area.

# BUSINESS PROBLEM


The client aims to capitalize on the potential highlighted in the articles by identifying lucrative investment opportunities within Miami-Dade County. Specifically, they are interested in properties with high returns on investment (ROI) within a 3-year timeframe.

# WORKFLOW

## 1. Data Preparation

+ Imported the necessary libraries
+ Loaded the dataset
+ Checked for the general data shape.
+ Checked the dataset info
+ Filtered the chosen zipcodes
+ Checked and handled missing values in our dataset
+ Checked for duplicates


## 2. Data Preprocessing
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

## 4. Data preprocessing for the selected top 5 zipcodes.
Before fitting the a basic ARIMA model further data preprocessing needs to take place. When working with time series models, it's crucial to assume that the data is stationary. Stationary time series data is essential for efficient model development. Prior to modeling, a thorough assessment of data stationarity will be conducted using the following methods:

Dickey-Fuller Test: The Dickey-Fuller test will be employed to assess the stationarity of the data. This statistical test helps determine if a unit root is present in the series, which is indicative of non-stationarity.

Rolling Mean Analysis: Additionally, a rolling mean analysis will be performed. This involves calculating the mean over a sliding window of observations. Fluctuations in the rolling mean indicate non-stationarity.

In cases where the data is identified as non-stationary, a differencing technique will be applied. Differencing involves computing the difference between consecutive observations.

#### 4.1 create a new dataframe with the topfive zipcodes.
    Consolidate the filtered data into a single dataframe making it easier to work with and analyse.
#### 4.2 Drop unnecessary columns
    For one to perform a stationarity and seasonality test,we need to drop columns that are not relevant to the analysis or are redundant. We dropped RegionID because it likely represents some identifier and is not relevant for the analysis.
#### 4.3 Stationarity Test
    Before applying the ADF test, it's important to visually inspect the time series plots for any obvious trends, seasonality, or non-stationary behavior.
#### 4.1.1 Rolling Mean and Standard Deviation
For Zipcodes 33161, 33177, 33162, and 33189: The p-values are greater than 0.05, indicating that we fail to reject the null hypothesis at a 5% significance level. Therefore, we cannot conclude that these series are stationary.

For Zipcodes 33055: The p-value is very small (0.001), indicating strong evidence against the null hypothesis. However, a visual inspection is not accurate enough to just rely on it and proceed with fitting an ARIMA model. Therefore, it is necessary to perform an Augmented Dickey-Fuller test for stationarity.
#### 4.1.2 Augmented Dickey-Fuller Test
Null hypothesis(the series is stationary);
For Zipcode 33161: Test Statistic is -1.698, which is greater than the critical values at all significance levels (1%, 5%, and 10%). This suggests that we fail to reject the null hypothesis, indicating that the series is non-stationary.

For Zipcodes 33177, 33162, and 33189: Test Statistic is 0.242, -0.382, and -0.019 respectively. In each case, the test statistic is greater than the critical values, indicating non-stationarity.

For Zipcode 33055: Test Statistic is 1.924, which is less than the critical values at all significance levels. This suggests rejecting the null hypothesis, indicating that the series is stationary.

We need our series to be stationary for modeling. we now go a step further and perform differencing.
#### 4.1.3 Differencing
Is often applied to achieve stationarity by removing trends or seasonal components from the time series data. For zip codes 33161 33177, 33162, and 33189, differencing is necessary to make the series stationary before further analysis or modeling.

After differencing we note a marked improvement that all data is stationary.

##  5. Modelling
**5.1 Basic SARIMA Model.**

Using a baseline model first is a necessary approach in time series forecasting as it helps in gaining insights into the data, assessing model performance, and guiding subsequent modeling efforts.

**5.1.1 Plot (ACF) and (PACF)**

Autocorrelation function and Partial autocorrelation function is a method use to provide insight into the selection of ones (p,d,q) as well as (p,d,q,s) which are our seasonal orders for a SARIMA model. Hence why it's generally recommended to visually inspect the ACF and PACF plots to guide the selection process, especially when dealing with complex or ambiguous time series patterns.

# MODEL EVALUATION
*Zip Code 33055: The RMSE is 0.01. This indicates a very good fit between the forecasting model and the actual data for this zip code. A low RMSE value suggests that the model's predictions are generally close to the actual values.*

*Zip Code 33161: The RMSE is 0.00, which is exceptionally low. It suggests an almost perfect fit between the model's predictions and the actual data. In practice, such a low RMSE might be due to a very good model fit or potentially overfitting to the specific data used for training.*

*Zip Code 33162: The RMSE is also 0.00, similar to zip code 33161.*

*Zip Code 33177: The RMSE is 0.01, similar to zip code 33055. This indicates a good model fit, but there's slightly more error compared to zip codes 33161 and 33162.*

*Zip Code 33189: The RMSE is 0.00. Here, the interpretation is similar to zip codes 33161 and 33162.*

#### RMSE: 0.002172299659738043
    lower RMSE values indicates a good model performance, as they signify smaller deviations between predicted and actual values.

## 6. Three Year Forecast.
## Top five Zip Codes with the highest ROI forecast
![download (3)](https://github.com/Saoke1219/zillow_forecast/assets/144773775/f2cd8262-f94c-414f-96a8-d465b6a48055)



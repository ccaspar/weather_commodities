# Weather and Commodities

|Table of Contents |
|---|
| [Overview](#overview) |
| [Data](#data) |
| [Key Insights](#key-insights) |

## Overview
The goal of this study is to examine the effect of weather on agricultural commodity prices. The initial target is to see how what percentage of price variability is explained by weather, and the secondary target is to predict commodities price movement (directional/classification or actual price). Corn, cotton, and wheat are three of the US' biggest crops. I will use US spot prices and US weather data. This analysis will assume that the US market is the driver of US commodity prices; however, it is certainly possible that imports from other countries would affect prices too. I am currently in the early stages of this project. Stay tuned!


## Data
Two main datasets were used. Each dataset consists of daily values, but I will be grouping individual observations into longer time frames.
 - First is historical price data for corn, cotton, and wheat. This data is a daily price for every business day dating back to the 60s. Data was retreived from http://www.macrotrends.net/charts/commodities
 - Second is weather data from the National Oceanic and Atmospheric Administration(NOAA). The data set is the global summary of the day(GSOD). This provides data on a number of daily metrics such as temperature, humidity, and wind, for numerous locations across the globe. For this data set, I will only use data from the US, and given the time, only for crop growing regions.



## Key Insights
Time frames will be key in this study. Important decisions include: length of period over which to aggregate weather data (days/weeks/months), amount of weather data to use (one/two/three weeks etc), delay in predicting spot price (next month, three months, six months etc).



## Concepts and Skills used
Python <br>
Pandas <br>
SKLearn <br>
Feature engineering <br>
TensorFlow <br>
Keras <br>
Neural Networks <br>
Random Forest <br>
Logistic Regression <br>
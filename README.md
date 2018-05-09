# Weather and Commodities

|Table of Contents |
|---|
| [Overview](#overview) |
| [Data](#data) |
| [Key Insights](#key-insights) |

## Overview
I've been interested in the environment and our interactions with it my whole life. This study examines the relationship between weather and agricultural commodities prices. Specifically, can we use recent weather to predict prices in the near future? Corn, cotton, and wheat are three of the US' biggest crops. The hypothesis is that weather will affect the supply of these commodities when they hit the market in the near future. For example, a particularly dry spell, or wildfires, could reduce the supply of corn that is currently being harvested and will hit the market in a couple weeks. This reduced supply would then drive prices up. I will use US spot prices and US weather data. This analysis assumes that the US market is the driver of US commodity prices; as three of the US largest crops, they certainly have a large effect on domestic prices. However, it is certainly possible that imports from other countries would affect prices too.


## Data
Two main datasets were used.
 - First is historical price data for corn, cotton, and wheat. This data is a daily price for every business day dating back to the 60s. There are data points for every trading day (no weekends or holidays) which on average is 252 days per year. There was very little clearning required for this data. Data was retreived from http://www.macrotrends.net/charts/commodities
 - Second is weather data from the National Oceanic and Atmospheric Administration(NOAA). The data set is the global summary of the day(GSOD). This provides data on a number of daily metrics such as temperature, humidity, and wind, for numerous locations across the globe. Both acquiring and cleaning this data were lengthy processes. NOAA has an FTP for the GSOD data, provided you are using it for non-business purposes (that's me!). I used a bash script to access this server and download data from the 1960s to present (range of the commodities data). For each year, the data could be unzipped into a separate .op file for each station on record that year (around 12,000 stations at most). Each of these files would contain at most 365 days of data for that particular station. I am still unsure what .op stands for, but it is a fixed width text file. My next bash script unzipped these files, removed their headers, and concatenated them into one large file for the given year (repeated for each year). At this point, I had one large text file for each year. I created a schema for these files and read them into pandas. My first step was to filter to just US stations. The weather data didn't have any info on station location, so I retrieved another fixed width file with on station locations from NOAA, made a schema for it, and read it into pandas to make a list of US stations. Next, I filtered to the US stations that were present in every year. For each commodity, I filtered to stations in states where that crop is grown. There were some quirks to the data - for example, in different columns, n/a values could be represented by 99.9, 999.99, 9999.99, and more, without rhyme or reason (same number could have been used for all variables to avoid confusion). After all cleaning was done, I averaged each variable of all stations for each day.



## Key Insights
This project was an excellent exercise in time series decomposition and modeling. I used a SARIMAX model to predict prices three weeks into the future. To test the practical use of my model, I built a simple trading strategy: if you are not in the market, buy if the predicted price in three weeks is higher than present, and do nothing if it is lower. If you are already in the market, sell if the predicted price in three weeks is lower than present, and do nothing if it is higher. I applied this strategy from 2010-2018. Ultimately, my model and strategy proved better than holding the index for all three commodities. Corn performed the best with a 61% relative outperformance.
There were many learning opportunities throughout this project. The process of attaining and moving the data into a usable format proved much more complicated than I orginally predicted, and I learned some bash scripting along the way. Working with historical weather data can be very challenging, as collection methods have varied over the years. Frequency of reporting was certainly an issue too. While the majority of weather stations had over 340 days of observations per year, there were a number with only ~20 days of observations. Additionally, this study only used spot prices without consideration for futures prices, which should be incorporated for more accurate price analysis. Finally, trading costs should be incorporated into the cost-benefit analysis in the future.



## Concepts and Skills used
Bash <br>
Python <br>
Pandas <br>
SKLearn <br>
Feature engineering <br>
Time series decomposition <br>
Time series modeling <br>
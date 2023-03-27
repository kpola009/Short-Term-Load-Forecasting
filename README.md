# Short-Term-Load-Forecasting

**Problem Statement:** Accurate load forecasting is crucial for energy providers to ensure that there is an adequate energy supply to meet the demand. The traditional methods of load forecasting, such as time-series analysis, have limitations and are often unable to account for changes in energy consumption patterns.

**Project Goal:** The goal of this research project is to forecast load, using historical load consumption data to train Artificial Neural Network which capture’s non-linear relationships and changing consumer patterns.

Recently RNN’s have promised great results for forecasting problems but for this project I will try a different approach, The approach is defined more in detail in detailed report.

## Introduction

Load Forecasting the process of predicting future energy consumption for a customer or a region. For energy suppliers, load forecasting is an essential activity since it aids in planning and managing energy supply to meet demand. Energy suppliers may avoid overproduction or lack of energy, which can result in large financial losses and negatively affect consumers, with the help of accurate load forecasting. Despite its significance, load forecasting is still a difficult task because of extremely complicated and dynamic nature of energy consumption patterns.

The traditional techniques for load forecasting, such as time-series analysis, have limitations in capturing non-linear relationships and dynamic consumer patterns. Therefor there is need for more sophisticated approach to load forecasting, which can tackle limitations of tradition methods.

Artificial Neural Networks (ANNs) are becoming increasingly popular in load forecasting due to their ability to handle complex and non-linear relationships in data. In load forecasting using ANNs, the input variables can include historical load data, weather data, and socio-economic data, while the output is the predicted load. For this project only historical load data will be used.

## Dataset

The data was donated from Florida based utility company Florida Power and Light (fpl), to Energy Systems Research Laboratory. The dataset contains real load values of Miami for the year 1987, 1988, 1989, and 1990 in hourly timestamp.

## Approach

In this project, we have load data from year 1987, 1988, 1989, and 1990. From which year 1987, 1988, and 1989 were used to train ANN model, and year 1990 was used to test the model.

## Steps

- Segmenting each year into seasons of Summer (April- September), Transition (October and March), and Winter (November – February).
- Aggregating each season into one.
- Further, a different ANN (ANN1, ANN2, ANN3) is trained for each segment, where the architecture of the ANN remained same but different features were used for each season segment. Feature description can be seen below.
- Each ANN will forecast season segment for the year 1990. As shown in table below. 
- Compare the model predictions with real load values of the year 1990.

The whole approach can be seen in _Figure: 1_

![alt text](https://github.com/kpola009/Short-Term-Load-Forecasting/blob/main/Images/Drawing8.png "Figure 1")

![alt text](https://github.com/kpola009/Short-Term-Load-Forecasting/blob/main/Images/figure2.png "Figure 2")

**Feature List:**

- AvgL(k-1): Average Load of the previous day.
- sqr[MaxL(k-1)-AveL(k-1)]: Square of the difference between maximum Load of previous day and average load of previous day.
- sqr[aveL(k-1)-minL(k-1)]: Square of the difference between average load of previous day and min load of previous day.
- L(k-1,h): System load of previous day at hour.
- L(k-1,8): System load at 8 o’clock at previous day.
- Daytype: Daytype represents day of the week to capture patterns during the week.
- L(k-1,24): System load at 12 mid-night day earlier.
- Max L(k-1): Maximum load of the day earlier.
- Min L(k-1): Minimum load of the day earlier.
- L(k-7,h): load at hour h, one week ago.
- Hourtype: Hourtype represents hours during the day to capture patterns during the day.

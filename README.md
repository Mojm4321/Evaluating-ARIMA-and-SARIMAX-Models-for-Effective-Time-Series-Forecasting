# (Python) Evaluating ARIMA and SARIMAX Models for Effective Time Series Forecasting By Jolly Madamedon 

## Introduction
This report evaluates the forecasting performance of ARIMA and SARIMAX models in time series analysis. Leveraging historical data, the aim is to predict future trends while assessing the models using the Mean Squared Error (MSE) metric. Also, the SARIMAX model is applied to account for both non-seasonal and seasonal paterns within the dataset.

## Data Preparation and Visualisation
The process begins by importing the necessary libraries: pandas, numpy, and matplotlib. A sample time series dataset is generated, starting from January 1, 2019, spanning 200 days. The time series values are created with a linear trend, incorporating random noise to simulate real-world behaviour. Additionally, columns such as Category, Quantity and Random are included to represent other variables that may exist in the dataset but are irrelevant for forecasting purposes. 

The data is then stored in a pandas Data Frame, and the first five rows are displayed to check if the data looks correct (see Diagram 1).

![Diagram 1](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%201%20ARIMA.png)

Diagram 1

Next,the date and values columns are extracted from the data frame and set the Date column as the index. The data is now structured for time series analysis, linking each value directly to a specific date (Diagram 2).

![Diagram 2](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%202%20ARIMA.png)

Diagram 2

A line plot is created to visually represent the time series data. The plot includes labels for both axes, a title, a legend to identify the data, and a grid for readability, helping to visually analyse the trend in the data over time (see Diagram 3).

![Diagram 3](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%203%20ARIMA.png)

Diagram 3

## ARIMA Model Fitting and Summary

The ARIMA model is defined and fitted to the time series data, using the order (1,1,1), which specifies: 
 p: number of lag observations included (1), 
 d: Differencing to ensuring stationary (1) 
 q: Lagged forecast errors (1). 
 
The ARIMA model is then fitted and a summary report from the SARIMAX model is created to assess the model’s performance and its parameters, to see if there is any need to make any necessary adjustments to improve its forecasting accuracy. Presented in Diagram 4.

![Diagram 4](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%204%20ARIMA.png)

Diagram 4

### Interpretation of (ARIMA-1,1,1) SARIMAX results
The autoregressive coefficient is very low and insignificant, illustrating that the lagged values don’t contribute much to the overall predictions. Furthermore, the AIC, BIC and MSE values suggest that the model has a poor fit because a good model would minimise these values, the values in the diagram are high, which indicates the ARIMA (1,1,1) specification is struggling to capture any underlying patterns in the data, which can result in poor forecast accuracy. Also, the high signma2 (residual variance) illustrates that the model’s predictions deviate significantly from the actual values (Diagram 5).

![Diagram 5](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%205%20ARIMA.png)

Diagram 5

The ARIMA (1,1,1) model is used to forecast 90 days into the future. Predictions are generated starting from the end of the time series for these 90 days. Another date range is created, beginning from the day immediately following the last observed date and extending for the forecast period (Diagram 6).

![Diagram 6](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%206%20ARIMA.png) 

Diagram 6

The results are then visualised by plotting both the original time series data and the forecasted values. The plot is customised with a title, axis labels, a legend a grid to enhance readability and interpretation (Diagram 7).

![Diagram 7](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%207%20ARIMA.png) 

Diagram 7

## Forecasting with ARIMA Model
The decision to change the ARIMA model from (1,1,1) to (2,1,4) significantly improved the accuracy and realism of the forecast. In the original ARIMA (1,1,1) model, the forecast quickly flattened into a straight line, indicating that it couldn’t capture the complexity of the data beyond short-term fluctuations. This occurred because the model used only one past observation and one past error term, limiting its ability to reflect complex time series patterns (Diagram 8 and 9).

![Diagram 8](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%208%20ARIMA.png)

Diagram 8

![Diagram 9](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%209%20ARIMA.png)

Diagram 9

By using ARIMA (2,1,4), the model considered more past values (p = 2) and adjusted for errors over a longer period (q=4), leading to a more reliable forecast. The new configuration allowed the model to better capture the underlying trends and cycles in the data, resulting in a smoother and more accurate projection (Diagram 10).

![Diagram 10](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%2010%20ARIMA.png)

Diagram 10

## Model Evaluation: ARIMA with Different Orders
The evaluation of different ARIMA model configurations was completed by fitting each model to the time series data and calculating the mean squared error (MSE) of their predictions. Lower MSE values indicate a better fit to the data. The ARIMA model with parameters (2,1,4) achieved the lowest MSE of 457.88, making it the most accurate model for this dataset. Models with parameters (1,1,2) and (2,1,2) also performed well, with MSE values of 487.85 and 459.29, respectively. In contrast, the model with parameters (1,2,1) had the highest MSE, indicating the poorest fit. To summarise, the (2,1,4) model provided the best performance in terms of predictive accuracy among the configurations tested (Diagram 11 and 12).

![Diagram 11](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%2011%20ARIMA.png)

Diagram 11

![Diagram 12](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%2012%20ARIMA.png)

Diagram 12

## Seasonal ARIMA (SARIMAX) Model

### Model Configuration
To account for seasonality, the SARIMAX model is introduced. The process begins by importing the statsmodels library, which provides statistical tools for time series analysis. 

The order parameter (1,1,1) specifies the non-seasonal elements of the model: 1 autoregressive term (AR), 1st order differencing to ensure stationarity, and 1 moving average term. The seasonal order (1,1,1,12) addresses yearly seasonality, where data is differenced once for seasonality, with one AR term, one seasonal MA term, and the seasonality repeats every 12 periods (one year of monthly data). The SARIMAX model is then fitted to the values column of the dataset, which represents the time series.  The summary function provides a statistical overview of the model, highlighting key metrics that inform the model’s fit and predictive accuracy. Shown in (Diagram 13 and 14).

![Diagram 13](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%2013%20ARIMA.png)

Diagram 13

### SARIMAX Model Performance and Interpretation
While the residual anaylsis shows that errors are normally distributed and uncorrelated, the SARIMAX model's high AIC (1724.271) and BIC(1740.27) values indicate a poor fit. Furthermore, the Log Likelihood of -857.136 also suggest the model struggles to capture meaningful patterns int the data. Only the moving average term (MA.L1) is statistically significant as the other terms – AR and seasonal parts don’t seem to add any value, which suggests that the model is not optimal. Diagram 14 illustrates the poor fit.

![Diagram 14](https://github.com/Mojm4321/Evaluating-ARIMA-and-SARIMAX-Models-for-Effective-Time-Series-Forecasting/blob/main/Diagram%2014%20ARIMA.png)

Diagram 14

## Conclusion
The report demonstrates the process the applying ARIMA and SARIMAX models for time series forecasting. The ARIMA model particularly the (2,1,4) configuration provided the most accurate results based on the MSE evaluation. Eventhough, the SARIMAX model aimed to capture seasonal trends, it did not yield a better fit than ARIMA, as shown by its statistical performance.

## Recommendation
Additional optimisation and parameter tuning are recommended to enhance model performance, particularly in capturing both short term and seasonal trends.
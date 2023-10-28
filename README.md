# Cryptocurrencies-Analysis--Forecasting
This notebook is devoted to **system analysis and forecasting of the given cryptocurrency** (for example, "BTC" = Bitcoin, but it is easy to replace in the variable "cryptocurrency"): 
* Exploratory Data Analysis (EDA)
* Feature Engineering (FE) - synthesis and research of new features (internal and external factors)
* Data preprocessing and get target
* Building and tuning of many models of Machine Learning (ML) and choosing the optimal among them 
* Data forecasting 
* Analysis of forecasting accuracy and the importance of features

This notebook section provides examples of identifying the following **ML models** (but the list goes on):
* Facebook Prophet 
* ARIMA (and AutoARIMA)
* Linear Regression
* KNeighbors Regressor
* Support Vector Machines
* Linear SVR
* Random Forest Regressor
* Bagging Regressor
* XGB Regressor
* MLP Regressor
* ## Acknowledgements:
* data download and ML models training from the notebook [Crypto - BTC : 7 prediction models](https://www.kaggle.com/code/vbmokin/crypto-btc-7-prediction-models)
* FE - from the notebooks: 
    - [BTC Growth Forecasting with Advanced FE for OHLC](https://www.kaggle.com/code/vbmokin/btc-growth-forecasting-with-advanced-fe-for-ohlc)
    - [G-Research Crypto Forecasting - baseline & FE](https://www.kaggle.com/code/vbmokin/g-research-crypto-forecasting-baseline-fe)
    - [GResearch Simple LGB Starter](https://www.kaggle.com/code1110/gresearch-simple-lgb-starter)
    - [COVID in UA: Prophet with 4, Nd seasonality](https://www.kaggle.com/code/vbmokin/crypto-btc-advanced-analysis-forecasting-d)
    - [COVID-19 in 70 countries: daily Prophet forecast](https://www.kaggle.com/code/vbmokin/covid-19-in-70-countries-daily-prophet-forecast)
* Stationarity check from the notebook [Time Series: Interpreting ACF and PACF](https://www.kaggle.com/code/iamleonie/time-series-interpreting-acf-and-pacf)
* [How to Check if Time Series Data is Stationary with Python](https://machinelearningmastery.com/time-series-data-stationary-python/)
* candle OHLC-chart from the notebook [Cryptocurrency Data Visualization + ARIMA 💰](https://www.kaggle.com/code/fangya/cryptocurrency-data-visualization-arima)
* about cryptocurrencies - dataset [Forecasting Top Cryptocurrencies](https://www.kaggle.com/datasets/vbmokin/forecasting-top-cryptocurrencies)
* data about cryptocurrency source via API: https://finance.yahoo.com/cryptocurrencies/
* data about COVID-19 via API: https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series
<a class="anchor" id="0.1"></a>

## Table of Contents

1. [Import libraries and set parameters](#1)
1. [Download data](#2)
1. [EDA](#3)
   - [3.1 Market Cap](#3.1)
   - [3.2 Cryptocurrency data](#3.2)
   - [3.3 Cryptocurrency features data](#3.3)
   - [3.4 Stationarity check](#3.4)
   - [3.5 Identification of seasonality](#3.5)
   - [3.6 EDA with Pandas Profiling Report](#3.6)   
1. [FE](#4)
   - [4.1 FE with TSFRESH](#4.1)
   - [4.2 FE from technical features (Finance knowledge and Data Science)](#4.2)
   - [4.3 Analysis of anomalies](#4.3)
       - [4.3.1 Analysis of anomalies for "Close"](#4.3.1)
       - [4.3.2 Analysis of anomalies for the first data difference "Close_diff"](#4.3.2)
   - [4.4 Analysis of the impact of COVID-19 on the cryptocurrency rate](#4.4)
   - [4.5 Get target, training, validation and test datasets for ML models](#4.5)
1. [Model training and forecasting](#5)
    - [5.1 Facebook Prophet](#5.1)
    - [5.2 ARIMA](#5.2)
        - [5.2.1 How to find the order of differencing (d) in ARIMA model](#5.2.1)
        - [5.2.2 How to find the order of the AR term (p)](#5.2.2)
        - [5.2.3 How to find the order of the MA term (q)](#5.2.3)
        - [5.2.4 How to build the ARIMA Model with manually defined parameters](#5.2.4)
        - [5.2.5 How to build the ARIMA automatically](#5.2.5)
    - [5.3 Other ML models (Multi-factors models)](#5.3)
        - [5.3.1 Set parameters for many models](#5.3.1)
        - [5.3.2 Models training and forecasting](#5.3.2)
    - [5.4 Choosing the main optimal model and forecasting](#5.4)
    - [5.5 Feature importance study](#5.5)    

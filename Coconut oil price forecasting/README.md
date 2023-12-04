# Coconut oil price forecasting

In this [project](https://github.com/privet1mir/Econometrics-Data-Analysis-School-at-HSE/blob/main/Coconut%20oil%20price%20forecasting/Coconut_oil_forecasting.ipynb) you can see cocunut oil price forecasting using both econometrics & ML models. 

I took the data from the World Bank website, and decided to work with coconut oil prices because they have a good distribution (they even pass the DickeyFuller-test!) and I like coconut oil.

First of all I need to mention that we are working with monthly prices and we have data starting from 1960. 
Our target, which we will predict, is expressed as $ / mt, which means ($ per metric ton).

Let's look at historic data plot: 

<img src="https://github.com/privet1mir/Econometrics-Data-Analysis-School-at-HSE/blob/main/Coconut%20oil%20price%20forecasting/coconut_oil_historic_prices.png" width="800">

First of all, using cross-validation for the last 20 points I built forecasts for the day ahead for three models: Naive, AutoARIMA and AutoETS (season_length=3).
The results are the following:

| Model | MAE | RMSE | MAPE |
| ------- | --- | --- | --- |
| Naive | 82.08 |  106.23 | 5.89 |
| Observation Shape | 82.08 |  106.23 | 5.89 |
| AutoETS | 78.94 |  103.47 | 5.63 |
| AutoARIMA | 72.75 |  93.29 | 5.13 |

It is clear that autoARIMA is the leader among our models. 
Predictive curves of each of the model you can see below:

<img src="https://github.com/privet1mir/Econometrics-Data-Analysis-School-at-HSE/blob/main/Coconut%20oil%20price%20forecasting/arima_garch_predcitions.png" width="800">

Then, I tuned ARIMA by hands. Conducted the Dickey-Fuller test for the presence of a unit root,
examined autocorrelation graphs and selected the hyperparameters of the model. 

As a result, we managed to slightly reduce errors (pivot table below).

Also at the end I trained some ML models (out of the box). 
I used linear regression & XGBoost and hybrid models for cross-validation. 

As predictions of the hybrid model, I used the predictions of the tuned ARIMA and boosting (XGBRegressor) with different weights. 

<img src="https://github.com/privet1mir/Econometrics-Data-Analysis-School-at-HSE/blob/main/Coconut%20oil%20price%20forecasting/all_models_predictions.png" width="800">

Results:

| Model | MAE | RMSE | MAPE |
| ------- | --- | --- | --- |
| Naive | 82.08 |  106.23 | 5.89 |
| Observation Shape | 82.08 |  106.23 | 5.89 |
| AutoETS | 78.94 |  103.47 | 5.63 |
| AutoARIMA | 72.75 |  93.29 | 5.13 |
| tuned ARIMA | 69.40 |  87.54 | 5.02 |
| LinearRegression | 79.02 |  100.17 | 5.71 |
| Hybrid (ARIMA + XGBoost) | 66.34 |  85.77 | 4.93 |

It can be seen that the hybrid model performs better. It is also clear that these results are not ideal, since the ML models, as I wrote above, were used out of the box, I almost didn't tuned the boosting. At the same time, the result, in comparison with the Naive approach, improved quite well.

# Coconut oil price forecasting

In this project you can see cocunut oil price forecasting using both econometrics & ML models. 

I took the data from the World Bank website, and decided to work with coconut oil prices because they have a good distribution (they even pass the DickeyFuller-test!) and I like coconut oil.

First of all I need to mention that we are working with monthly prices and we have data starting from 1960. 
Our target, which we will predict, is expressed as $ / mt, which means ($ per metric ton).

Let's look at historic data plot: 

First of all, using cross-validation for the last 20 points I built forecasts for the day ahead for three models: Naive, AutoARIMA and AutoETS (season_length=3).
The results are the following:

It is clear that autoARIMA is the leader among our models. 
Predictive curves of each of the model you can see below:

Then, I tuned ARIMA by hands. Conducted the Dickey-Fuller test for the presence of a unit root,
examined autocorrelation graphs and selected the hyperparameters of the model. 

As a result, we managed to slightly reduce errors (pivot table below).


Also at the end I trained some ML models (out of the box). 
I used linear regression & XGBoost and hybrid models for cross-validation. 

As predictions of the hybrid model, I used the predictions of the tuned ARIMA and boosting (XGBRegressor) with different weights. Results:


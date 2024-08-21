# Short-Term Electricity Load Forecasting Using Machine Learning Techniques
## Project Overview
### This project, part of the MSc Data Science at the University of Hertfordshire, involves predicting short-term electricity load using different machine learning models. The goal is to explore how well ARIMA, Prophet, and XGBoost were a forecasting model for daily energy consumption based on a Low Carbon London (LCL) application data set. The LCL dataset contains over 5500 households in London, over half of hourly energy consumption data from November 2011 to February 2014.
Motivation
Reliable short-term electricity load forecasting plays a vital role in efficient energy management, especially due to the higher degrees of freedom within modern energy systems, which include additional renewable contributing factors. This project aims to build models that can work with real-time data and changing consumption patterns to provide useful information for energy providers who need to forecast future demand peaks and guarantee an adequate energy offer at the cheapest expense possible.
Dataset
We have utilized a dataset from the Low Carbon London (LCL) project, which contains:
•	DateTime: The date and time the half-hourly energy consumption was recorded.
•	KWH/hh (per half hour): The amount of electricity consumed in kilowatt-hours during each half-hour period.
•	LCLid: A unique identifier for each household.
•	stdorToU: Tariff type, indicating whether the household was under dynamic pricing or a flat rate.
Preprocessing Steps
•	Data Cleaning: Combined multiple CSV files into a single DataFrame, handled missing values, and converted relevant columns to appropriate data types.
•	Feature Engineering: Applied rolling averages, lag features, and rolling standard deviations to capture consumption trends. Integrated weather data and created a holiday indicator to account for external factors influencing energy use.
•	Resampling: Aggregated the half-hourly data into daily consumption values to facilitate model training and evaluation.
Models Developed
1. ARIMA (AutoRegressive Integrated Moving Average)
•	Purpose: Captures linear trends and relationships in time series data.
•	Parameters: The best model was found with parameters p=9, d=3, q=6 through grid search.
•	Performance: Achieved an R² value of 0.056, indicating limited explanatory power with significant prediction errors (MAE: 1843.28, RMSE: 3236.09).
2. Prophet
•	Purpose: Designed to handle time series data with strong seasonality and missing data, developed by Facebook.
•	Parameters: Tuned using changepoint_prior_scale and seasonality_prior_scale, with the best results obtained for a changepoint_prior_scale of 0.1 and seasonality_prior_scale of 1e-05.
•	Performance: Showed poor performance with a negative R² value (-1.00), indicating that the model's predictions were worse than a simple mean forecast (MAE: 2769.75, RMSE: 4542.43).
3. XGBoost (Extreme Gradient Boosting)
•	Purpose: An ensemble learning method that is highly effective for capturing complex non-linear relationships in large datasets.
•	Parameters: Optimized using grid search for n_estimators and learning_rate, with the best model using 2000 trees and a learning rate of 0.1.
•	Performance: Demonstrated superior predictive accuracy with an R² value of 0.9985, significantly outperforming the other models (MAE: 256.84, RMSE: 382.09).
Results and Discussion
The XGBoost model outperformed both ARIMA and Prophet in all evaluation metrics, showing its strength in handling complex, non-linear relationships in the energy consumption data. The ARIMA and Prophet models struggled to capture the intricate patterns in the data, with Prophet performing particularly poorly in this context.
Model Performance Comparison
Model	MAE	RMSE	R²
ARIMA	1843.28	3236.09	0.056
Prophet	2769.75	4542.43	-1.00
XGBoost	256.84	382.09	0.9985
Future Work
•	Hyperparameter Tuning: Further tuning of model parameters using advanced techniques like Bayesian optimization to improve performance.
•	Exploring Advanced Models: Investigate other state-of-the-art models, such as Long Short-Term Memory (LSTM) networks or Transformer-based models, for potentially better results.
•	Ensemble Methods: Combine different models or apply stacking techniques to balance their strengths and achieve better predictive accuracy.

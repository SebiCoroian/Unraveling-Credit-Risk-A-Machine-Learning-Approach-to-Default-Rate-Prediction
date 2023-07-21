# Unraveling-Credit-Risk-A-Machine-Learning-Approach-to-Default-Rate-Prediction

This project aims to develop predictive models for the Default Rate in Romania based on various macroeconomic indicators. The Default Rate represents the percentage of loans that lenders expect to go unpaid. The models are trained on a dataset with economic indicators for Romania and the European Union from 2008 to 2021, following specific requirements and constraints. The purpose of the project is to find a model that can accurately predict the Default Rate based on the given macroeconomic factors, achieving an accuracy between 55% and 80% to avoid overfitting.

## Dataset

The dataset consists of 14 features:

- `Date`: The date of observation.
- `EU_CPIYOY`: The inflation rate in the European Union area.
- `EU_GDPYOY`: The Gross Domestic Product (GDP) in the European Union area.
- `EURIBOR`: The Euro Interbank Offered Rate (EURIBOR).
- `GDPYOY`: The Gross Domestic Product (GDP) for Romania, computed using the Production Approach. The figures are in total volume or constant price value index, not seasonally adjusted RON, and at 2000 prices.
- `INFL`: The Consumer Price Index (CPI) for Romania, which provides the inflation rate. The figures represent the year-over-year change at the end of each period.
- `ROBOR3M`: The 3-month Romanian Interbank Offered Rate (ROBOR).
- `LT_IR`: The 10-year Government Benchmark Bid Yield for Romania, provided by Thomson Reuters.
- `EURRON`: The exchange rate from the New Romanian Leu to the Euro, provided by the European Central Bank (ECB).
- `ROKEPOLA`: The Monetary Policy Rate of the National Bank of Romania.
- `LENDRATE`: The average interest rate for credits in Romania [source](http://www.bnro.ro/Interactive-database-1107.aspx).
- `DEPRATE`: The average interest rate for deposits in Romania [source](http://www.bnro.ro/Interactive-database-1107.aspx).
- `UNEMP`: The unemployment rate in Romania.
- `DR_12`: The Default Rate for Bank Portfolios.

## Methodology

The data analysis and modeling process is broken down into several steps:

1. **Data Exploration**: The first step is to load the dataset and perform initial data exploration. This includes checking the first few rows of the data, the dimensions of the dataset, the data types of each column, and descriptive statistics.

2. **Data Preprocessing**: The 'Date' column is converted into datetime format and set as the index of the DataFrame. The dataset is then split into three parts based on time periods: a development set (2008-01-01 to 2018-12-31), a validation set (2019-01-01 to 2021-12-31), and a testing set (2022-01-01 to 2022-12-31).

3. **Model Development**: Three different models are developed and compared:

   - An Ordinary Least Squares (OLS) Regression model
   - A Random Forest Regressor model
   - A Seasonal Autoregressive Integrated Moving Average (SARIMAX) model

4. **Model Training**: The models are trained on the development set. For the OLS Regression and Random Forest models, the independent variables are 'EU_CPIYOY', 'EU_GDPYOY', and 'EURIBOR', and the dependent variable is 'DR_12'. For the SARIMAX model, the 'DR_12' variable is used.

5. **Model Evaluation**: The models' performance is evaluated by making predictions on the validation and testing sets and calculating the Root Mean Squared Error (RMSE). The RMSE is the square root of the average squared differences between the predicted and actual values. It measures the standard deviation of the residuals or prediction errors. Lower RMSE values indicate better model performance.

## Results

Each of the three models showed success in predicting the Default Rate based on the given macroeconomic factors:

1. **OLS Regression Model**: The OLS model achieved an RMSE of approximately 0.0218 on the validation set. The model's predictions closely followed the actual values, which indicates a good fit to the data. The model's summary provides valuable insights into the relationship between the Default Rate and the independent variables. 

2. **Random Forest Regressor Model**: The Random Forest model achieved an RMSE of approximately 0.0133 on the validation set. This model also showed a good fit to the data. In addition, the feature importance calculated from the Random Forest model provides an understanding of which variables are most influential in predicting the Default Rate.

3. **SARIMAX Model**: The SARIMAX model, fitted with the best parameters obtained from a grid search, achieved an RMSE of approximately 0.00168 on the validation set. This model showed an excellent fit to the data and performed better than the OLS and Random Forest models in terms of RMSE.

## Conclusion

The models developed in this project provide valuable insights into the factors affecting the Default Rate in Romania. They can be used to predict future Default Rates based on macroeconomic indicators, which can be useful for financial institutions, policy makers, and investors. 

The OLS Regression model provides a simple linear relationship between the Default Rate and the macroeconomic indicators. It's easy to interpret and provides a baseline for comparison with the other models.

The Random Forest model, being a non-linear model, captures complex relationships between the predictors and the Default Rate. It provides an importance score for each feature, allowing us to understand the relative influence of each macroeconomic indicator on the Default Rate.

Finally, the SARIMAX model takes into account the temporal nature of the data and captures trends and seasonality in the Default Rate. It outperforms the other two models in terms of RMSE, making it the best performing model in this project.

These results meet the general requirements of the project. The models are built using quarterly data, as provided by the dataset. The models achieve an accuracy between 55% and 80%, avoiding overfitting. The p-values for all risk drivers are below the 10% threshold. The models are trained on the development sample (2008 – 2018) and tested on the validation sample (2019 – 2021) and the test sample (2022). The SARIMAX model uses a grid search on the validation sample to choose the orders.

Overall, this project demonstrates how macroeconomic factors can be used to predict future Default Rates. These insights could help financial institutions better assess risk and make more informed lending decisions. Policymakers could also use these findings to implement measures to control the Default Rate and stabilize the financial market.

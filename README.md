# Real_Estate_Price_Prediction_Website
This repository houses a machine learning model, now deployed as a web application, to predict property prices in Bangalore. The model leverages real estate data and various features to provide accurate estimates.

Problem Statement

Real-world Problem
The real estate market, especially in metropolitan cities like Bangalore, is highly dynamic and complex. Traditional methods of property valuation often rely on expert opinions and historical data, which can be subjective and time-consuming. This can lead to inaccurate valuations, hindering informed decision-making for both buyers and sellers.

Significance

Informed Decision Making: Accurate property price predictions empower buyers and sellers to make informed decisions.
Market Transparency: By providing reliable price estimates, the model can contribute to a more transparent and efficient real estate market.
Risk Mitigation: Accurate valuations can help mitigate financial risks associated with real estate investments.
Investment Strategies: Investors can leverage the model to identify potential investment opportunities and optimise their portfolios.
Policy Making: Urban planners and policymakers can use the model to analyze market trends and inform urban development strategies.

Source: Kaggle

Key Features:

area_type: Indicates the type of area (e.g., Super built-up Area, Carpet Area).
availability: Specifies the availability status of the property (e.g., Ready To Move, 18-Dec).
location: The location of the property.
size: The size of the property in square feet.
society: The name of the society or residential complex.
total_sqft: The total square footage of the property.
bath: The number of bathrooms.
balcony: The number of balconies.

Target Variable:
price: The price of the property.

Data Preprocessing:
Outlier Removal:A custom function remove_bhk_outliers was used to identify and remove outliers based on the price per square foot for each BHK category within a specific location.
This step ensured that the model is trained on realistic and reliable data.

Feature Engineering:
Price per Square Foot: This feature was calculated by dividing the price by the total square footage to normalize the price across different property sizes.
Location One-Hot Encoding: The categorical location feature was one-hot encoded to create binary features for each unique location.

Model Architecture Overview

The provided code snippet utilises a technique called GridSearchCV to find the best performing model among three different regression algorithms:
Linear Regression
Lasso Regression
Decision Tree Regression

The code defines a dictionary named algos that stores information about each model. This includes:
model: An instance of the specific scikit-learn model class (e.g., LinearRegression()).
params: A dictionary containing hyperparameters to be tuned during GridSearchCV. These hyperparameters control the behaviour of the model.


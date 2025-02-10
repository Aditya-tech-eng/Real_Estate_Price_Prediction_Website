# Bengaluru House Prices Prediction Model - Stage 1

## Overview

This project aims to predict house prices in Bengaluru using machine learning. The model considers factors such as square footage, number of bedrooms, bathrooms, and location.

## Dataset

The dataset used for training is `bengaluru_house_prices.csv`, which contains real estate data from Bengaluru, including property attributes and prices.

## Dependencies

Before running the code, install the necessary Python libraries:

```sh
pip install numpy pandas matplotlib scikit-learn flask
```

## Data Preprocessing

- Missing and incorrect values are handled using helper functions.
- The `total_sqft` column is cleaned and converted to numerical values.
- Locations with fewer occurrences are grouped into an "other" category.
- Outliers in `price_per_sqft` and `bhk` categories are removed to improve model accuracy.

## Exploratory Data Analysis (EDA)

- The dataset is analyzed using `matplotlib` to visualize patterns.
- Scatter plots are used to compare property prices based on BHK and square footage.

## Model Training

- The dataset is split into training and testing sets using `train_test_split`.
- Various models are evaluated using `GridSearchCV`:
  - **Linear Regression**
  - **Lasso Regression**
  - **Decision Tree Regressor**

## Model Evaluation

- `cross_val_score` is used for model validation.
- The best model is selected based on `GridSearchCV` results.
- The model achieves an accuracy of approximately 84.5%.

## Price Prediction Function

A function `predict_price()` is implemented to estimate house prices based on user input.

## Saving the Model

The trained model is saved as a pickle file (`bangalore_home_prices_model.pickle`) for future use.

---

# Stage 2 - Web Integration

## Web Application Development

To deploy the model as a web application, a front-end interface is developed using:

- **HTML** for structure
- **CSS** for styling
- **JavaScript (jQuery)** for interaction

A **Flask** backend (`server.py`) is implemented to:

- Serve the model predictions via API endpoints.
- Fetch available location names dynamically.

### Code Breakdown

#### **Front-End (HTML, CSS, JavaScript)**

- The UI consists of input fields for square footage, BHK, bathrooms, and location selection.
- A button triggers the price estimation function via JavaScript.
- jQuery is used to send data to the Flask API and display the estimated price dynamically.

#### **Back-End (Flask API - server.py)**

- Two main API endpoints:
  - `/get_location_names`: Returns available location names for the drop-down menu.
  - `/predict_home_price`: Accepts user input and returns the estimated price using the trained model.
- The `util.py` script is used to load saved artifacts and make predictions.

### Running the Web Application

1. Start the Flask server:
   ```sh
   python server.py
   ```
2. Open `index.html` in a web browser.
3. Enter property details and get an estimated price.

---

# Stage 3 - Deployment on AWS EC2

## Deployment Process

The web application is deployed on an Amazon EC2 instance to make it accessible online.

### Steps:

1. Launch an **EC2 Instance** (Ubuntu/Linux-based recommended).
2. Install required dependencies:
   ```sh
   sudo apt update
   sudo apt install python3-pip
   pip install flask numpy pandas scikit-learn gunicorn
   ```
3. Transfer project files to the EC2 instance via **SCP** or **Git**.
4. Run the Flask application using **Gunicorn**:
   ```sh
   gunicorn --bind 0.0.0.0:5000 server:app
   ```
5. Configure **Nginx** as a reverse proxy for better scalability and security.
6. Obtain a public **Elastic IP** to access the application online.

---

# Stage 4 - Transforming into a Startup

## Vision: AI-Powered Real Estate Advisory Platform

This project has the potential to be developed into a **real estate tech startup**, offering AI-driven property valuation services. The goal is to provide accurate, real-time property price predictions to home buyers, sellers, and real estate agencies.

### Key Features for a Startup Model:

1. **Expanding Beyond Bengaluru**
   - Scale the model to include real estate data from other major Indian cities and international markets.

2. **User Profiles & Personalized Insights**
   - Implement authentication so users can save searches and track market trends.

3. **Real Estate Partner Integration**
   - Provide an API service that integrates with real estate platforms like **99acres** and **MagicBricks** to offer instant property valuations.

4. **AI-Driven Market Insights**
   - Incorporate external data sources such as **economic trends, infrastructure projects, and mortgage rates** to enhance pricing predictions.

5. **Monetization Strategies**
   - Offer **premium subscriptions** for advanced analytics.
   - Partner with **real estate agencies** for lead generation.
   - Provide **customized reports** for investors and property developers.

By implementing these enhancements, this project can evolve into a fully operational **AI-driven real estate advisory platform**, disrupting the traditional property market and offering valuable insights to buyers, sellers, and investors.


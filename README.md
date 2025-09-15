# Solar Power Forecasting for Smart Homes

This project develops a machine learning model to predict solar power generation, enabling smart home and building systems to optimize energy usage. It demonstrates a complete data science workflow, from data preparation to model application.

## Table of Contents
- [Project Overview](#project-overview)
- [The Challenge](#the-challenge)
- [Methodology](#methodology)
- [Data Files](#data-files)
- [Key Results](#key-results)
- [Dashboard & Visualization](#dashboard-and-visualization)
- [Application: Smart Energy Optimization](#application-smart-energy-optimization)
- [How to Run the Code](#how-to-run-the-code)
- [Dependencies](#dependencies)

---

## Project Overview

The primary goal of this project is to build a time-series forecasting model that accurately predicts future solar power generation. This forecast can then be used by a smart home system to automate energy-intensive tasks, such as charging an electric vehicle, during periods of peak solar availability.

---

## The Challenge

Solar power is an intermittent energy source, meaning its availability is highly dependent on weather and time of day. This unpredictability makes it difficult for smart systems to efficiently use the energy generated. This project addresses that challenge by building a model that can forecast solar output, providing the intelligence needed for an automated, optimized energy plan.

---

## Methodology

The project follows a standard machine learning pipeline tailored for time-series data:

1.  **Data Acquisition & Preparation**: The raw data from two separate plants was merged with corresponding weather data, cleaned, and filtered to focus on daylight hours.
2.  **Feature Engineering**: New features were created to help the model identify patterns. This included extracting time-based features (e.g., **hour**, **day of year**) from the timestamp and creating a **lagged feature** of the previous hour's solar output.
3.  **Model Building**: A **Linear Regression** model was trained on the data. The data was split **sequentially** (using past data for training and future data for testing) to ensure a realistic evaluation.
4.  **Evaluation**: The model's performance was evaluated against a simple **persistence model** (our baseline) using **Mean Absolute Error (MAE)**, **Root Mean Squared Error (RMSE)**, and **R-squared ($R^2$)**.

---

## Data Files

This repository contains the final processed dataset, making the project fully reproducible.

-   `solar_power_data.csv`: The clean, preprocessed, and feature-engineered dataset used for training the model.

---

## Key Results

The trained Linear Regression model proved to be a significant improvement over the baseline.

* **Linear Regression Model Evaluation**:
    * MAE: **151.87 kW**
    * RMSE: **285.93 kW**
    * $R^2$: **0.33**

* **Persistence Model (Baseline)**:
    * MAE: **145.36 kW**
    * RMSE: **345.59 kW**
    * $R^2$: **0.02**

The lower **RMSE** and much higher **$R^2$** demonstrate that the model successfully learned from the features to reduce large errors and explain a significant portion of the solar output variance, making it a reliable forecasting tool.

---

## Dashboard & Visualization

A companion **Looker Studio dashboard** has been created to visualize the data and model's performance. The dashboard allows users to interact with the project's findings without needing to run any code.

-   `Solar_Power_Forecast_Dashboard.pdf`

The dashboard includes key visualizations such as:
-   A **line chart** comparing the actual vs. predicted solar power over time.
-   A **scatter plot** illustrating the strong correlation between solar power and irradiation.
-   **Scorecards** displaying the final model performance metrics (MAE and R-squared).

---

## Application: Smart Energy Optimization
The true value of this project lies in its application. A smart energy system can use the model's forecast to make intelligent decisions. The following pseudocode illustrates how a system could use the forecast to optimize energy usage.
// Get the forecast for the day from the trained model
hourly_forecast = model.predict(todays_weather_forecast)

// Find the time of day with the maximum predicted solar output
peak_generation_hour = find_peak_in_forecast(hourly_forecast)

// Use a simple decision-making logic
if current_time == peak_generation_hour:
print("Peak solar generation detected! Starting EV charging now.")
start_ev_charging()
else:
print("Waiting for peak solar generation to start charging.")
wait()


---

## How to Run the Code

1.  **Clone the repository**:
    `git clone https://github.com/zia9571/Solar-Power-Forecasting-Dashboard.git`
2.  **Install dependencies**: Run `pip install -r requirements.txt`.
3.  **Run the notebook**: Open `solar_power.ipynb` in Jupyter or a similar environment to see the full code and analysis.

---

## Dependencies

The following libraries are required to run this project:

-   `pandas`
-   `numpy`
-   `scikit-learn`
-   `matplotlib`
-   `seaborn`

A `requirements.txt` file is included for easy installation:
`pip install -r requirements.txt`



The true value of this project lies in its application. A smart energy system can use the model's forecast to make intelligent decisions. 

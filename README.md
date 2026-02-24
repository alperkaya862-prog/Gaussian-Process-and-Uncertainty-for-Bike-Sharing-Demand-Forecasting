# Gaussian Process and Uncertainty for Bike Sharing Demand Forecasting

## Project Title and Purpose
This project applies Gaussian Process regression to forecast daytime bike rental demand using a time series dataset. The primary goal is to predict hourly bike sharing demand while quantifying weather dependent uncertainty and rental volatility. It utilizes the UCI Bike Sharing dataset from Washington D.C.

## Tech Stack
* **Language:** Python
* **Data Processing:** Pandas, NumPy
* **Machine Learning:** Scikit learn
* **Visualization:** Matplotlib, Seaborn

## Technical Decisions
* **Data Filtering:** The dataset was filtered to include only daytime hours (7 AM to 7 PM) to capture peak rental times and lower the computational load.
* **Feature Engineering:** A binary weather condition indicator (clear vs wet) was created. Cyclic hour features were generated using sine and cosine transformations to accurately represent the time of day.
* **Multicollinearity Handling:** Highly correlated variables, such as feel like temperature and season, were dropped.
* **Target Transformation:** The target variable was logarithmically transformed to stabilize variance and improve model performance.
* **Model Selection:** Gaussian Process regression was selected because it offers a Bayesian framework that provides both predictions and calibrated uncertainty estimates.
* **Kernel Composition:** A composite kernel was designed using a Constant Kernel for overall variance, a Radial Basis Function kernel for smooth patterns, and a White Kernel for observation noise.
* **Data Splitting:** The data was split temporally by year, training on 2011 data and testing on 2012 data, to reflect real forecasting scenarios.

## Key Findings and Challenges
* The model achieved a Training RMSE of 40.83 and an R squared of 0.908.
* The Test RMSE was 169.96 with an R squared of 0.284.
* A significant finding was the model's ability to quantify uncertainty; the mean prediction uncertainty was 12.5 percent higher during wet weather compared to clear weather. This successfully captured the increased unpredictability of rentals during bad weather.
* A challenge encountered was the overall increase in demand from 2011 to 2012, which caused the test target mean to fall outside the expected range of the training data.

## Installation Instructions
1. Clone the repository: `git clone https://github.com/alperkaya862-prog/Gaussian-Process-and-Uncertainty-for-Bike-Sharing-Demand-Forecasting.git`
2. Install the required dependencies: `pip install pandas numpy scikit-learn matplotlib seaborn`
3. Run the Jupyter Notebook to view the analysis and model evaluation.

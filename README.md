# Next-Day PM2.5 Prediction Using Machine Learning

A machine learning project to predict the next PM2.5 concentration using historical air-quality data from multiple Indian cities and monitoring locations.

## 📌 Project Overview

This project uses air-quality data to predict future PM2.5 levels. It includes data preprocessing, EDA, feature engineering, model training, evaluation, and feature-importance analysis.

Two models were compared:

- Linear Regression — Baseline
- Random Forest Regressor — Improved Model

## 📊 Dataset

**India Multi-City Air Quality Dataset (100K+ Rows)**

The dataset contains **96,755 records** and includes:

- City
- Monitoring location
- Date
- PM2.5
- PM10
- O3
- NO2
- SO2
- CO

### Dataset Source

https://www.kaggle.com/datasets/riteshswami08/india-multi-city-air-quality-dataset-100k-rows

## 🎯 Problem Statement

The objective is to predict the **next-day PM2.5 concentration** using current pollutant levels, historical PM2.5 values, location, and time-based features.

## ⚙️ Feature Engineering

The following features were created:

- `pm25_lag1`
- `pm25_lag2`
- `pm25_lag3`
- `pm25_rolling3`
- `pm25_rolling7`
- `month`
- `day_of_week`

Historical PM2.5 features help capture recent pollution trends.

## 🔍 Exploratory Data Analysis

The project includes:

- Pollutant distribution analysis
- Correlation heatmap
- PM2.5 time-series analysis
- Missing-value analysis
- IQR-based outlier analysis
- Boxplots

Missing pollutant values were handled using median imputation based on city and monitoring location.

High pollution values were not automatically removed because they may represent genuine pollution events.

## 🤖 Models Used

### Linear Regression

Used as the baseline model to establish a simple performance reference.

### Random Forest Regressor

Used as the improved model because it can capture nonlinear relationships between pollutant levels and historical PM2.5 patterns.

Parameters:

- `n_estimators = 200`
- `max_depth = 20`
- `min_samples_leaf = 2`
- `random_state = 42`

## 📅 Train-Test Split

An **80:20 chronological split** was used.

The data was sorted by date before splitting to ensure that the model learns from earlier observations and is tested on later observations.

## 📈 Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 20.082 | 35.827 | 0.741 |
| **Random Forest** | **18.404** | **35.260** | **0.749** |

Random Forest performed better than the Linear Regression baseline, with approximately **8.36% improvement in MAE**.

## ⭐ Feature Importance

The most important features included:

1. Current PM2.5
2. PM10
3. 7-day PM2.5 rolling average
4. Historical PM2.5 features
5. Other pollutant measurements

Current PM2.5 was the strongest predictor in the Random Forest model.

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## 📁 Project Structure

```text
Next-Day-PM25-Prediction/
│
├── AIMLInternship_code.ipynb
├── Technical_Report.pdf
├── README.md
└── images/


##▶️ How to Run
1. Clone the repository
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd Next-Day-PM25-Prediction
2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
3. Download the dataset

Download the dataset from Kaggle:

https://www.kaggle.com/datasets/riteshswami08/india-multi-city-air-quality-dataset-100k-rows

Place the CSV file in the project directory.

4. Run the notebook
jupyter notebook

Open .ipynb and run the cells sequentially.

##⚠️ Limitations
Weather variables were not included.
Some pollutant values required missing-value handling.
Pollution patterns can vary across cities and locations.
The target represents the next available observation in a city/location sequence and may not always be exactly 24 hours later when dates are missing.

##🚀 Future Improvements
Add weather information such as temperature, humidity and wind speed
Try XGBoost or Gradient Boosting
Perform hyperparameter tuning
Explore advanced time-series models
Build a Streamlit dashboard
Add SHAP-based model explainability
#👩‍💻 Author

Siddhi Kakade

Computer Engineering | AI/ML | Data Science


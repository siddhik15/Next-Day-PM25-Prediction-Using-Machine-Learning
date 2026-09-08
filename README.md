# 🌍 Next-Day PM2.5 Prediction Using Machine Learning

A machine learning project for predicting **next-day PM2.5 concentration** using historical air pollution data from multiple Indian cities and monitoring locations.

The project focuses on understanding pollution patterns, engineering time-based features, and comparing a baseline Linear Regression model with a customized Random Forest model.

---

## 📌 Project Overview

Air pollution is a major environmental and public health concern. Accurate prediction of pollutant concentrations can help in monitoring pollution levels and supporting early planning and decision-making.

This project predicts the **next available PM2.5 observation** using:

- Current pollutant concentrations
- Historical PM2.5 values
- Rolling averages
- Temporal features
- City and monitoring-location information

The project follows a complete machine learning workflow:

**Data Collection → Data Cleaning → EDA → Feature Engineering → Model Training → Evaluation → Comparison**

---

## 🎯 Problem Statement

The objective of this project is to predict the **next-day PM2.5 concentration** for different cities and monitoring locations across India.

### Purpose

To use historical air-quality patterns and pollutant concentrations to estimate upcoming PM2.5 levels.

### Real-World Relevance

PM2.5 forecasting can support:

- Air-quality monitoring
- Pollution alerts
- Environmental planning
- Public awareness
- Data-driven pollution management

---

## 📊 Dataset

### Dataset Used

**India Multi-City Air Quality Dataset – 100K Rows**

The dataset contains approximately **96,755 records** and includes air-quality measurements from different Indian cities and monitoring locations.

### Pollutants

- PM2.5
- PM10
- O3
- NO2
- SO2
- CO

### Other Information

- City
- Monitoring Location
- Date

### Dataset Source

Kaggle:

https://www.kaggle.com/datasets/riteshswami08/india-multi-city-air-quality-dataset-100k-rows

---

## 📁 Project Structure

```text
Next-Day-PM25-Prediction/
│
├── AIMLInternship_code.ipynb
├── Technical_Report.pdf
├── README.md
└── images/
```

---

## 🔍 Exploratory Data Analysis

The dataset was analyzed to understand pollutant distributions, relationships, temporal patterns, missing values, and outliers.

### EDA Performed

- Dataset structure and information
- Statistical summary
- Missing-value analysis
- Pollutant distributions
- Correlation analysis
- PM2.5 time-series trend
- Outlier detection using IQR
- Boxplot analysis

### Important Observations

PM2.5 showed strong temporal behavior and was the most important variable for predicting future PM2.5 values.

PM10 also showed a meaningful relationship with PM2.5.

High pollutant values were retained because they may represent genuine pollution events rather than data errors.

---

## 🧹 Data Preprocessing

The following preprocessing steps were performed:

1. Converted pollutant columns to numeric values.
2. Identified missing values.
3. Filled missing pollutant values using city/location-level median values.
4. Applied overall median filling where required.
5. Converted the date column to datetime format.
6. Sorted observations by city, location, and date.

---

## ⚙️ Feature Engineering

Time-series features were created to capture historical pollution behavior.

### Historical PM2.5 Features

- `pm25_lag1` – Previous PM2.5 value
- `pm25_lag2` – PM2.5 value from two observations earlier
- `pm25_lag3` – PM2.5 value from three observations earlier
- `pm25_rolling3` – Previous 3-observation average
- `pm25_rolling7` – Previous 7-observation average

### Temporal Features

- `month`
- `day_of_week`

### Spatial Features

- `city`
- `location`

### Target

`next_day_pm25`

The target was created by shifting PM2.5 values within each city and monitoring location sequence.

---

## 🤖 Machine Learning Models

Two models were implemented and compared.

### 1. Linear Regression — Baseline

Linear Regression was selected as the baseline model because it is simple, interpretable, and provides a reference point for evaluating a more complex model.

### 2. Random Forest Regressor — Customized Model

Random Forest was selected as the customized model because it can capture nonlinear relationships between pollutant concentrations, historical PM2.5 values, temporal features, and location information.

### Random Forest Configuration

- `n_estimators = 200`
- `max_depth = 20`
- `min_samples_leaf = 2`
- `random_state = 42`

---

## 📅 Train-Test Strategy

A **chronological 80/20 split** was used instead of a random split.

This approach is more appropriate for forecasting because the model is trained on earlier observations and evaluated on later observations.

### Dataset Split

- Training samples: **77,175**
- Testing samples: **19,276**
- Split point: **26 April 2024**

---

## 📈 Model Evaluation

The following regression metrics were used:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

### Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 20.082 | 35.827 | 0.741 |
| Random Forest | **18.404** | **35.260** | **0.749** |

### Improvement

Random Forest achieved:

- Approximately **8.36% lower MAE**
- Approximately **1.58% lower RMSE**
- Higher R² score compared with Linear Regression

This indicates that Random Forest captured nonlinear relationships in the data more effectively than the baseline model.

---

## ⭐ Feature Importance

Feature importance analysis was performed using the trained Random Forest model.

The most influential features included:

1. **Current PM2.5**
2. **PM10**
3. **7-observation rolling PM2.5 average**
4. Other pollutant, temporal, and location features

Current PM2.5 was the dominant feature, showing that recent pollution concentration is highly useful for predicting future PM2.5 levels.

---

## 📊 Key Findings

- Historical PM2.5 values are highly useful for forecasting future PM2.5.
- PM10 provides additional predictive information.
- Rolling averages help capture recent pollution trends.
- Random Forest performed better than the Linear Regression baseline.
- Pollution extremes were retained because they may represent genuine pollution events.
- Pollution patterns can differ across cities and monitoring locations.

---

## ⚠️ Limitations

- Weather variables were not included.
- Some pollutant values required missing-value handling.
- Pollution patterns can vary significantly across cities and locations.
- The target represents the next available observation in a city/location sequence and may not always correspond to exactly 24 hours later.
- The model may perform differently for different cities and monitoring locations.

---

## 🚀 Future Improvements

Possible improvements include:

- Add weather variables such as temperature, humidity, and wind speed.
- Experiment with XGBoost and Gradient Boosting models.
- Perform hyperparameter tuning.
- Explore advanced time-series models.
- Build an interactive Streamlit dashboard.
- Add SHAP-based model explainability.
- Evaluate model performance separately for individual cities and locations.

---

## ▶️ How to Run

### 1. Clone the Repository

`git clone <YOUR_GITHUB_REPOSITORY_URL>`

`cd Next-Day-PM25-Prediction`

### 2. Install Dependencies

`pip install pandas numpy matplotlib seaborn scikit-learn jupyter`

### 3. Download the Dataset

Download the dataset from Kaggle:

https://www.kaggle.com/datasets/riteshswami08/india-multi-city-air-quality-dataset-100k-rows

Place the dataset CSV file in the project directory.

### 4. Run the Jupyter Notebook

`jupyter notebook`

Open:

`.ipynb`

Run the notebook cells sequentially.

---

## 📦 Dependencies

- Python 3.x
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook


---

## 👩‍💻 Author

**Siddhi Kakade**

Computer Engineering | AI/ML | Data Science

---

⭐ If you find this project useful, feel free to explore the repository.

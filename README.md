# Parafield Rainfall Prediction

## Project Overview

This project investigates whether daily weather observations from Parafield Airport, South Australia can be used to predict whether rainfall will occur during the following observation period.

The project follows a complete machine learning workflow including data cleaning, exploratory data analysis, feature engineering, time-series cross-validation, model selection, hyperparameter tuning, and final model evaluation.

A key focus of the project was ensuring realistic model evaluation by implementing leakage-aware time-series cross-validation with a forecast-horizon gap between training and validation periods.

---

## Dataset

The dataset consists of daily weather observations collected at Parafield Airport by the Australian Bureau of Meteorology (BoM) and is included in the `data/` directory of this repository.

Variables include:

* Temperature measurements
* Atmospheric pressure
* Humidity
* Wind speed
* Wind direction
* Rainfall observations
* Seasonal and calendar-based features

Variables with substantial missingness were excluded from modelling, while categorical weather variables were appropriately encoded for machine learning.

---

## Project Workflow

1. Data cleaning and preprocessing
2. Exploratory data analysis (EDA)
3. Feature engineering
4. Time-series train/test splitting
5. Time-series cross-validation
6. Hyperparameter tuning
7. Final model evaluation
8. Model interpretation

---

## Models Evaluated

The following classification models were compared:

* Logistic Regression
* Lasso Logistic Regression
* Ridge Logistic Regression
* Random Forest
* XGBoost

Model performance was assessed using time-series cross-validation and evaluated using:

* Accuracy
* Balanced Accuracy
* Precision
* Recall
* F1 Score
* Matthews Correlation Coefficient (MCC)
* ROC-AUC

---

## Final Model

After model comparison and hyperparameter tuning, the final selected model was a **Lasso Logistic Regression** classifier.

The model achieved the strongest overall performance during model comparison while maintaining a high level of interpretability.

---

## Key Findings

* 3pm humidity was the strongest positive predictor of rainfall occurrence.
* 3pm temperature was the strongest negative predictor of rainfall occurrence.
* Fine-grained seasonal timing (day of year) provided more predictive value than broad seasonal categories.
* Most morning weather variables were removed through Lasso regularisation, suggesting afternoon conditions carried substantially greater predictive information.
* Introducing a forecast-horizon gap during time-series cross-validation altered performance estimates and prevented target leakage.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* XGBoost

---

## Repository Contents

* `parafield_rainfall_prediction.ipynb` — Complete analysis, modelling workflow, and results.
* `README.md` — Project summary and key findings.

---

## Future Improvements

Potential future extensions include:

* Extend the dataset to include multiple years of weather observations to improve seasonal coverage and model robustness.
* Incorporate cloud cover measurements if a more complete historical record becomes available.
* Integrate observations from nearby weather stations to capture broader regional weather patterns.
* Explore additional lagged weather and rainfall variables to better capture temporal dependencies.
* Further investigate probability threshold selection for different forecasting objectives, such as maximising rainfall detection or minimising false rainfall forecasts.
* Evaluate model performance using alternative forecast horizons beyond the next observation period.

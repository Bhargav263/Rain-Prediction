# Rain-Prediction

📌 Project Overview

This project focuses on predicting whether it will rain tomorrow based on historical weather observations using machine learning. The objective is to build a leakage-free, end-to-end ML pipeline that reflects real-world modeling practices.

🎯 Problem Statement

Given daily weather attributes such as temperature, humidity, pressure, wind direction, and cloud cover, predict whether it will rain the next day (RainTomorrow).

This is a binary classification problem.

📊 Dataset Description

Dataset: Australian Weather Dataset

Records: ~142,000

Features: Mix of numerical and categorical weather attributes

Target Variable: RainTomorrow (Yes / No)

Class Distribution: Imbalanced (fewer rain days)

⚠️ Important:
The feature RISK_MM was removed as it directly leaks future rainfall information and causes data leakage.

🔍 Exploratory Data Analysis (EDA)

EDA was performed only on the training data to avoid data leakage.

Key observations:

Target variable is imbalanced

Several features contain missing values

Correlation analysis performed on numerical features

Categorical features analyzed separately using grouped statistics

EDA guided preprocessing and modeling decisions.

🧹 Data Preprocessing

All preprocessing steps were implemented using scikit-learn Pipelines to ensure consistency and prevent data leakage.

Steps include:

Train–test split performed before preprocessing

Missing value imputation using Iterative Imputer (MICE)

One-hot encoding for categorical features

Feature scaling using StandardScaler

Unified preprocessing using ColumnTransformer

⚖️ Handling Class Imbalance

The dataset is imbalanced.

Instead of oversampling:

Model-specific imbalance handling was applied

For XGBoost, scale_pos_weight was used

This avoids synthetic data generation and reduces overfitting risk

🧠 Models Trained

The following models were trained and compared:

Logistic Regression

Decision Tree

Random Forest

XGBoost (Final Model)

All models were evaluated on the same untouched test set.

🚀 Final Model & Results

Final Model: XGBoost Classifier

Metric	Score
Accuracy	85.76%
ROC-AUC	~0.88–0.92

The performance is realistic and confirms a leakage-free pipeline.

🔎 Feature Importance

Feature importance analysis showed that the most influential predictors of rainfall include:

Humidity (especially afternoon humidity)

Cloud cover

Sunshine duration

Atmospheric pressure

Rain persistence indicators

These features align well with real meteorological intuition.

🧠 Key Learnings

Importance of identifying and removing data leakage

Correct placement of EDA in the ML workflow

Building preprocessing using pipelines to avoid leakage

Handling class imbalance without oversampling

Interpreting model outputs meaningfully

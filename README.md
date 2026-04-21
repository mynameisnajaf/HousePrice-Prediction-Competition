# 🏠 House Price Prediction Project

This project focuses on predicting residential property sale prices using advanced data preprocessing, feature engineering, and an ensemble modeling approach. The solution is inspired by a Kaggle-style machine learning competition.

---

## 📊 Dataset Overview

The project uses the following datasets:

- **`train.csv`** – Training data including the target variable `SalePrice`
- **`test.csv`** – Test data for which predictions are generated
- **`data_description.txt`** – Detailed explanation of all features

---

## 🛠️ Key Processing Steps

### 1. Feature Engineering

To improve model performance, several new features are created:

- **`TotalSF`** – Total square footage (basement + 1st + 2nd floor)
- **`HouseAge`** – Age of the house at the time of sale
- **`RemodAge`** – Time since last remodeling
- **`TotalBath`** – Combined number of bathrooms (full + half)

---

### 2. Data Preprocessing

- **Log Transformation**  
  The target variable `SalePrice` is transformed using `log1p` to reduce skewness.

- **Handling Missing Values**  
  - Categorical features → filled with `"None"`  
  - Numerical features → filled with median values  

- **Encoding**  
  Categorical variables are converted using **One-Hot Encoding**

- **Scaling**  
  Numerical features are standardized using `StandardScaler` (mainly for linear models)

---

## 🤖 Modeling Approach

An **ensemble model** is used to balance bias and variance by combining two different algorithms:

### Models Used

| Model            | Configuration                          | MAE    |
|------------------|----------------------------------------|--------|
| Ridge Regression | `alpha = 10.0`                         | 0.0913 |
| LightGBM         | `n_estimators = 2000`, `learning_rate = 0.01` | 0.0870 |

---

## 🔗 Ensemble Strategy

Final predictions are computed as a weighted average:

Final Prediction = (0.4 × Ridge) + (0.6 × LightGBM)

---

## 🚀 Usage

### Requirements

Install the required libraries:

```bash
pip install numpy pandas scikit-learn lightgbm

unning the Project
Place the dataset files (train.csv, test.csv) in the working directory
Run the notebook or script
The output will be generated as:
submission.csv

📤 Output
submission.csv
Contains:
Id
Predicted SalePrice (inverse log-transformed)

📌 Notes
Feature engineering significantly improves prediction accuracy
Ensemble learning combines strengths of different models
Log transformation helps stabilize variance and handle skewed data

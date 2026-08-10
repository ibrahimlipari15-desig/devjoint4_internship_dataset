# 🏠 House Price Prediction — Machine Learning

## 📌 Project Overview

This project develops a **Machine Learning regression solution for predicting house prices** based on property characteristics.

The main objective is to help real estate businesses estimate property prices more efficiently and support data-driven pricing decisions.

The project covers the complete Machine Learning workflow, including:

* Problem definition
* Exploratory Data Analysis (EDA)
* Data cleaning
* Feature engineering
* Data preprocessing
* Model comparison
* Cross-validation
* Hyperparameter tuning
* Final model evaluation
* Model serialization

---

## 🎯 Business Problem

Determining an appropriate selling price for a property can be challenging because prices depend on multiple factors such as:

* Property area
* Number of rooms
* Location
* Floor
* Total number of floors
* Land area
* Property characteristics

The goal of this project is to build a model that can estimate the **expected house price** from these features.

### Target Variable

**Target:** `price`

This is a **Supervised Learning — Regression** problem because the target variable is continuous and numerical.

---

## 📊 Dataset

The original dataset contains:

* **100,775 records**
* **51 features**

The dataset contains information related to residential properties and their characteristics.

Examples of available information include:

* Property price
* Area
* Number of rooms
* City
* Floor
* Total floors
* Land area
* Location coordinates
* Views
* Repair status
* Other property attributes

---

## 🔎 Exploratory Data Analysis

A comprehensive EDA was performed to understand the structure and quality of the dataset.

The following analyses were performed:

* Dataset dimensions
* Data types
* Descriptive statistics
* Missing-value analysis
* Duplicate detection
* Target variable distribution
* Categorical variable analysis
* Numerical variable analysis
* Correlation analysis
* Outlier analysis
* Relationship between property area and price
* Relationship between number of rooms and price

### Example insights

The analysis showed that property characteristics such as **area, number of rooms and location-related variables** can have an important relationship with property prices.

The target variable was also analyzed for its distribution and potential outliers.

---

## 🧹 Data Cleaning

Several preprocessing and cleaning operations were performed.

### Missing Values

Missing numerical values were handled using the **median**, while missing categorical values were replaced with `"Naməlum"` / an appropriate categorical placeholder.

### Duplicate Values

Duplicate records were checked and removed/handled where necessary.

### Data Type Conversion

Some variables originally stored as text were converted into numerical features.

For example:

* `Sahə` → `area_m2`
* `Mərtəbə` → `floor`
* `Mərtəbə` → `total_floors`
* `Torpaq sahəsi` → `land_area_sot`

### Data Leakage Prevention

Variables such as `total_price` and `unit_price` were excluded from the modeling features because they contain information directly related to the target price and could cause **data leakage**.

ID, URL and unnecessary text-based columns were also removed from the initial modeling dataset.

---

## ⚙️ Machine Learning Pipeline

The project uses a preprocessing pipeline to ensure that the same transformations are consistently applied to the data.

### Numerical Features

* Missing values → Median imputation
* Scaling → StandardScaler

### Categorical Features

* Missing values → Most frequent value
* Encoding → OneHotEncoder

---

## 🤖 Model Comparison

Three regression algorithms were evaluated:

### 1. Linear Regression

Used as a baseline regression model.

### 2. Random Forest Regressor

An ensemble tree-based model capable of capturing nonlinear relationships between property characteristics and price.

### 3. Gradient Boosting Regressor

A boosting-based ensemble model designed to improve prediction performance by combining multiple weak learners.

---

## 📈 Model Evaluation

All models were evaluated using the **same 5-Fold Cross-Validation strategy**.

### Cross-Validation

```text
KFold
n_splits = 5
shuffle = True
random_state = 42
```

### Evaluation Metrics

#### MAE — Mean Absolute Error

Measures the average absolute difference between predicted and actual prices.

**Lower is better.**

#### RMSE — Root Mean Squared Error

Penalizes larger prediction errors more strongly.

**Lower is better.**

#### R² Score

Measures how well the model explains the variation in house prices.

**Higher is better.**

---

## 🔧 Hyperparameter Tuning

After comparing the three models, the best-performing model was selected based on the validation results.

Hyperparameter optimization was then performed using:

**GridSearchCV**

The same cross-validation methodology was maintained during tuning.

The objective was to find the parameter combination that minimized the model's **Mean Absolute Error (MAE)**.

---

## 🧪 Final Test Evaluation

After model selection and hyperparameter tuning, the final model was evaluated on a **separate test set**.

The test set was kept isolated from the model selection and hyperparameter tuning process and was used only for the final evaluation.

Final evaluation metrics:

```text
MAE  : [add final value]
RMSE : [add final value]
R²   : [add final value]
```

---

## 💾 Model Saving

The final trained model was saved using **Joblib**.

```python
import joblib

joblib.dump(final_model, "house_price_model.pkl")
```

The saved model can later be loaded and used for predictions without retraining the model.

```python
loaded_model = joblib.load("house_price_model.pkl")
```

---

## 💼 Business Value

The developed solution can support real estate businesses by:

* Providing initial property price estimates
* Supporting pricing decisions
* Identifying properties with unusual prices
* Reducing manual valuation effort
* Processing large numbers of properties automatically
* Supporting data-driven decision making

The model should be considered a **decision-support tool**, rather than a replacement for professional property valuation.

---

## 📁 Project Structure

```text
House-Price-Prediction/
│
├── house_sale (2).csv
├── house_price_prediction.ipynb
├── house_price_model.pkl
├── README.md
└── requirements.txt
```

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Joblib
* Jupyter Notebook

---

## 🚀 Machine Learning Workflow

```text
Business Problem
       ↓
Data Collection
       ↓
EDA
       ↓
Data Cleaning
       ↓
Feature Engineering
       ↓
Preprocessing
       ↓
Train/Test Split
       ↓
Model Comparison
       ↓
5-Fold Cross-Validation
       ↓
Hyperparameter Tuning
       ↓
Final Model
       ↓
Test Set Evaluation
       ↓
Model Saving
```

---

## 👩‍💻 Author

**Pəri Ibrahimova**

Machine Learning & Data Analytics Project

---

## 📌 Conclusion

This project demonstrates an end-to-end Machine Learning workflow for **house price prediction**.

Multiple regression algorithms were compared using a consistent evaluation methodology. The best-performing model was then optimized using hyperparameter tuning and evaluated once on an isolated test set.

The resulting model provides a foundation for developing a real-world automated property price estimation system.

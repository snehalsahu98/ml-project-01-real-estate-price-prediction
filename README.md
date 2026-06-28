# Real Estate Price Prediction

## Table of Contents

- [Project Overview](#project-overview)
- [Project Workflow](#project-workflow)
- [Data Source](#data-source)
- [Technologies Used](#technologies-used)
- [Data Cleaning](#data-cleaning)
- [Feature Engineering](#feature-engineering)
- [Outlier Treatment](#outlier-treatment)
- [Missing Value Imputation](#missing-value-imputation)
- [Feature Selection](#feature-selection)
- [Model Building](#model-building)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Results](#results)
- [Future Improvements](#future-improvements)
- [Project Structure](#project-structure)
- [How to Run](#how-to-run)
- [References](#references)

---

# Project Overview

> **📷 Insert Project Screenshot Here**

This project focuses on building a complete end-to-end machine learning pipeline to predict residential property prices using data collected through web scraping. It walks through every stage of the data science lifecycle, starting from gathering raw data and transforming it into a usable format, all the way to building, evaluating, and deploying a predictive model.

The main goal of the project is to estimate the market value of a property based on various characteristics such as location, built-up area, furnishing level, property age, amenities, and several engineered features derived from the raw data. By combining domain knowledge with machine learning techniques, the model aims to capture patterns that influence property pricing.

To make the solution practical and user-friendly, the final model was deployed as an interactive web application using Streamlit. This allows users to input property details and receive real-time price predictions, making the project not just analytical but also usable in real-world scenarios.

---

# Project Workflow

The project follows a structured workflow that mirrors a typical data science pipeline. It begins with web scraping to collect raw property listings, followed by extensive data cleaning to ensure consistency and reliability. Feature engineering is then applied to extract meaningful information from the data, which is further explored through exploratory data analysis to uncover patterns and trends.

After understanding the data, the next steps involve handling outliers and imputing missing values to improve data quality. Feature selection techniques are then used to identify the most relevant variables for prediction. Finally, multiple machine learning models are trained and evaluated, and the best-performing model is deployed using Streamlit for real-time predictions.

---

# Data Source

> **📷 Insert Dataset Workflow Image Here**

The dataset used in this project was created by scraping property listings from a real estate website. Two separate datasets were initially collected, one for flats and another for independent houses. Each dataset was cleaned individually to address inconsistencies specific to that property type before being merged into a unified dataset for analysis and modeling.

The combined dataset includes a wide range of attributes such as:

- Property Price
- Area Measurements
- Bedrooms
- Bathrooms
- Balconies
- Floor Details
- Furnishing Status
- Amenities
- Property Age
- Sector
- Property Type
- Luxury Features

---

# Technologies Used

This project was developed using Python and a range of popular data science libraries.

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Streamlit
- Jupyter Notebook
- Pickle

---

# Data Cleaning

The raw dataset contained several inconsistencies, missing values, duplicate entries, and text-based attributes that required careful preprocessing.

The cleaning process included:

- Removing duplicate records
- Removing irrelevant columns
- Standardizing price formats
- Converting text-based numerical values into numeric format
- Extracting floor numbers
- Extracting sector information
- Standardizing furnishing categories
- Cleaning balcony information
- Cleaning flats and houses separately before merging
- Manually correcting inconsistent sector names

---

# Feature Engineering

Feature engineering played a crucial role in improving the predictive performance of the model.

New features created include:

- Built-up Area
- Property Type
- Sector
- Property Age Category
- Furnishing Category
- Luxury Category
- Floor Category
- Number of Additional Rooms

Additional feature engineering involved:

- Extracting built-up area from multiple area measurements
- Creating a luxury score based on available amenities
- Categorizing furnishing levels using clustering
- Categorizing floor numbers into Low Rise, Mid Rise, and High Rise
- Extracting individual additional rooms such as:
  - Study Room
  - Servant Room
  - Pooja Room
  - Store Room

---

# Outlier Treatment

Outlier treatment was performed carefully to ensure that genuine high-value properties were not removed.

The process included:

- Correcting incorrect area calculations
- Updating Price per Sq.ft after correcting area values
- Removing physically impossible records
- Treating extreme values in:
  - Price
  - Area
  - Price per Sq.ft
  - Built-up Area
  - Carpet Area
- Using the Area-to-Bedroom ratio to identify unrealistic listings

Rather than blindly removing outliers, domain knowledge was used to distinguish genuine luxury properties from incorrect records.

---

# Missing Value Imputation

Missing values were handled using a combination of statistical techniques and domain knowledge.

Different strategies included:

- Median Imputation
- Correlation-based Imputation
- Property Type-based Imputation
- Sector-based Imputation

Important features imputed include:

- Built-up Area
- Property Age
- Floor Number

Features containing excessive missing values with limited predictive importance were removed from the final dataset.

---

# Feature Selection

To identify the most relevant variables, multiple feature selection techniques were evaluated.

Methods used include:

- Correlation Analysis
- Random Forest Feature Importance
- Gradient Boosting Feature Importance
- Permutation Importance
- Recursive Feature Elimination
- Lasso Regression
- Linear Regression Coefficients
- SHAP Values

The importance scores from all techniques were compared to identify consistently important features. Less important features were removed only after verifying that model performance remained largely unchanged.

---

# Model Building

Before training, the target variable was transformed using a logarithmic transformation to reduce right skewness.

A complete machine learning pipeline was constructed consisting of:

- Data Preprocessing
- Column Transformer
- Feature Encoding
- Feature Scaling
- Target Encoding
- Machine Learning Model
- K-Fold Cross Validation

The following regression models were evaluated:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Support Vector Regression
- Decision Tree
- Random Forest
- Extra Trees
- Gradient Boosting
- AdaBoost
- XGBoost
- Multi-layer Perceptron Regressor

The final model used:

- Numerical Feature Scaling
- Ordinal Encoding
- One-Hot Encoding
- Target Encoding
- Random Forest Regressor

The complete pipeline was exported as a Pickle file for deployment.

---

# Exploratory Data Analysis

Exploratory Data Analysis helped uncover several important trends within the real estate market.

Some key observations include:

- Property prices are heavily right-skewed.
- Most listings fall between **₹1–2 Crore**.
- Very few properties are priced above **₹5 Crore**.
- Flats generally offer better amenities than houses.
- Houses usually have larger built-up areas.
- Newer sectors contain more apartment projects.
- Older sectors primarily consist of independent houses.
- Premium sectors command significantly higher property prices.
- Around **75 societies account for more than 50%** of all available listings.
- Luxury apartment projects are concentrated near major IT hubs.

---

# Results

The final machine learning pipeline achieved:

- **Model Accuracy:** ~90%
- **Mean Absolute Error (MAE):** ~₹45 Lakhs

Project achievements:

- Built a complete end-to-end machine learning pipeline.
- Compared multiple regression algorithms.
- Applied extensive feature engineering.
- Evaluated eight feature selection techniques.
- Developed a deployable prediction pipeline.
- Built an interactive Streamlit web application for real-time property price prediction.

---

# Future Improvements

Potential enhancements include:

- Expanding the dataset with additional property listings.
- Periodically retraining the model using recent market data.
- Incorporating geospatial features such as proximity to schools, metro stations, and commercial hubs.
- Experimenting with advanced ensemble and deep learning models.
- Integrating SHAP-based model explainability into the Streamlit application.

---

# Project Structure

```text
Real-Estate-Price-Prediction/
│
├── notebooks/
├── datasets/
├── docs/
├── streamlit_project/
├── models/
├── README.md
└── requirements.txt
```

---

# How to Run

Clone the repository:

```bash
git clone https://github.com/snehalsahu98/ml-project-01-real-estate-price-prediction.git
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Run the Streamlit application:

```bash
streamlit run Home.py
```

---

# References

This project makes use of the following open-source libraries and frameworks:

- Scikit-learn
- Pandas
- NumPy
- Streamlit
- XGBoost
- Matplotlib
- Seaborn

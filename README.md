# Real Estate Price Prediction

## Table of Contents

- [Project Overview](#project-overview)
- [Project Workflow](#project-workflow)
- [Data Source](#data-source)
- [Data Cleaning](#data-cleaning)
- [Feature Engineering](#feature-engineering)
- [Outlier Treatment](#outlier-treatment)
- [Missing Value Imputation](#missing-value-imputation)
- [Feature Selection](#feature-selection)
- [Model Building](#model-building)

---

# Project Overview

> **📷 Insert Project Screenshot Here**

This project focuses on building a complete end-to-end machine learning pipeline to predict residential property prices using data collected through web scraping. It walks through every stage of the data science lifecycle, starting from gathering raw data and transforming it into a usable format, all the way to building, evaluating, and deploying a predictive model.

The main goal of the project is to estimate the market value of a property based on various characteristics such as location, built-up area, furnishing level, property age, amenities, and several engineered features derived from the raw data. By combining domain knowledge with machine learning techniques, the model aims to capture patterns that influence property pricing.

To make the solution practical and user-friendly, the final model was deployed as an interactive web application using Streamlit. This allows users to input property details and receive real-time price predictions, making the project not just analytical but also usable in real-world scenarios.

**Website:** https://bit.ly/snehalsahu98_real_estate_price_predictor


---

# Project Workflow

The project was completed in the following stages:

1. Web Scraping
2. Data Cleaning
3. Feature Engineering
4. Exploratory Data Analysis
5. Outlier Treatment
6. Missing Value Imputation
7. Feature Selection
8. Model Building & Evaluation
9. Recommender System
10. Streamlit Deployment

---

# Data Source

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

# Data Cleaning

The raw dataset contained several inconsistencies, missing values, duplicate entries, and text-based attributes that required careful preprocessing.

The cleaning process included:

- Removing duplicate records
- Removing irrelevant columns
- Standardizing price formats
- Converting text-based numerical values into numeric format
- Extracting sector information
- Standardizing furnishing categories
- Cleaning balcony information
- Cleaning flats and houses separately before merging
- Manually correcting inconsistent sector names

---

# Feature Engineering

Feature engineering played a crucial role in improving the predictive performance of the model.

Important features created include:

- Built-up Area
- Sector
- Luxury Score

Furnishing details were converted into numerical counts based on the number of available furnishing items in a property. The K-Means clustering algorithm, along with the Elbow Method, was then used to determine the optimal number of clusters, resulting in three furnishing categories: Unfurnished, Semi-Furnished, and Fully Furnished. Society amenities were assigned weighted scores, which were aggregated to compute a Luxury Score for each property. Additional features such as Additional Rooms, Floor Number and Property Age were created to better capture property characteristics.

---

# Outlier Treatment

Outlier treatment was performed carefully to improve data quality while preserving genuine high-value properties. Instead of removing all extreme observations, each potential outlier was investigated individually to distinguish legitimate luxury properties from data entry errors and inconsistencies.

The process began by correcting incorrect area calculations, which also required updating the corresponding Price per Square Foot values since they are directly dependent on the property's area. Several records contained unrealistic area measurements caused by conversion errors, and these were manually corrected wherever possible. Properties with physically impossible configurations, such as extremely small homes containing an unusually large number of bedrooms, were identified using the **Area-to-Bedroom ratio** and removed from the dataset.

Extreme values across important numerical features in Price, Area, Price per Square Foot, Built-up Area, and Carpet Area were corrected, capped, or removed based on their validity, ensuring a cleaner and more reliable dataset for model training.

---

# Missing Value Imputation

Missing values were handled using a combination of statistical techniques and domain knowledge to preserve the quality of the dataset. Different imputation strategies were applied based on the nature of each feature rather than using a single approach for all missing values.

Highly correlated features were used to estimate missing Built-up Area, while Property Age was imputed using the median value of properties belonging to the same sector and property type. Missing Floor Number values were filled using median imputation. Features containing excessive missing values with limited predictive importance were removed from the final dataset.

---

# Feature Selection

To identify the most relevant variables, multiple feature selection techniques were evaluated.

8 techniques used include:

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

# Climate Vulnerability Prediction using Random Forest

## Project Overview

This project uses a **Random Forest** model to predict the **vulnerability level** of different regions based on various environmental, social, and economic features. The dataset includes features such as temperature, precipitation, GDP, social vulnerability scores, population density, and more. The goal is to build a multi-class classification model that predicts vulnerability levels, helping stakeholders identify areas that require more attention for climate adaptation.

## Key Features

- **Multi-class classification**: Predicting vulnerability level as one of three categories (0, 1, or 2).
- **Random Forest Model**: Ensemble learning method that reduces overfitting and improves accuracy by combining multiple decision trees.
- **Exploratory Data Analysis (EDA)**: Analyzing the dataset to understand data distribution, check for missing values, and identify important features.

## Table of Contents

- [Dataset](#dataset)
- [Data Preprocessing](#data-preprocessing)
- [Model Building](#model-building)
- [Model Evaluation](#model-evaluation)
- [Next Steps](#next-steps)
- [License](#license)

---

## Dataset

The dataset used in this project is a **climate vulnerability dataset**, which contains the following key features:

- **environmental_quality_index**: Environmental quality score.
- **social_vulnerability_score**: Social vulnerability index.
- **population_affected_by_hazards**: Number of people affected by environmental hazards.
- **avg_temp_celsius**: Average temperature in Celsius.
- **precipitation_mm**: Precipitation in millimeters.
- **vegetation_index**: Index representing the vegetation cover.
- **num_extreme_weather_events**: Number of extreme weather events.
- **sea_level_rise_mm**: Sea level rise in millimeters.
- **avg_humidity_percent**: Average humidity percentage.
- **access_to_clean_water_percent**: Percentage of population with access to clean water.
- **literacy_rate**: Literacy rate (with missing values).
- **gender_equality_index**: Gender equality index (with missing values).
- **population_density**: Population density (people per square kilometer).
- **gdp_per_capita**: GDP per capita (USD).
- **poverty_rate**: Poverty rate as a percentage.
- **urban_population_percent**: Percentage of urban population.
- **env_soc_interaction**: Environmental-social interaction index.
- **pop_density_deviation_from_mean**: Deviation from the mean population density.
- **geographic_zone_Coastal**, **geographic_zone_Inland**, **geographic_zone_Mountain**: Geographic zone dummies.
- **vulnerability_level**: Target variable (0, 1, or 2), representing different levels of vulnerability.

## Data Preprocessing

To prepare the data for model training, the following steps were performed:

### Handling Missing Values:
- Columns `literacy_rate` and `gender_equality_index` had excessive missing values and were dropped.
- Sentinel values (`-9999`) were replaced with `NaN` and imputed with the median for the remaining missing values.

### Feature Engineering:
- Categorical features (`geographic_zone_*`) were one-hot encoded.
- Numerical features were scaled using `StandardScaler`.

### Data Splitting:
- The dataset was split into **80% training** and **20% testing** sets.

## Model Building

A **Random Forest Classifier** was used to build the model:

- **Random Forest Classifier**: This ensemble method builds multiple decision trees and combines their predictions to reduce overfitting and improve accuracy.
- The model was trained on the preprocessed training data.

```python
from sklearn.ensemble import RandomForestClassifier

# Instantiate and train the model
model = RandomForestClassifier(random_state=42)
model.fit(X_train_processed, y_train)

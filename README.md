# Airbnb Price Prediction
This project is part of Data Science Bootcamp at [Rakamin](https://www.rakamin.com/) 

## Table of Contents
1. [Introduction](#introduction)  
2. [Problem Statement](#problem-statement)  
3. [Goals and Objectives](#goals-and-objectives)  
4. [Dataset](#dataset)  
5. [Methodology](#methodology)
6. [Results](#Results)
7. [Acknowledgements](#Acknowledgements)

## Introduction
Predicting the price of Airbnb listings can help hosts set competitive and optimized rates. This project explores how data science is implemented to analyze and predict Airbnb room prices based on various features.

## Problem Statement
Setting the right price for an Airbnb listing is crucial for maximizing revenue and attracting customers. However, hosts often face challenges due to the wide range of factors influencing prices, such as location, amenities, and reviews. This project aims to develop a predictive model to address this issue.

## Goals and Objectives
- Analyze the factors affecting Airbnb room prices.  
- Build a machine learning model to predict room prices.  
- Provide actionable insights for Airbnb hosts.

## Dataset
- **Source:** [Airbnb Prices in European Cities](https://www.kaggle.com/datasets/thedevastator/airbnb-prices-in-european-cities) on Kaggle.
- **Features**:
#### Categorical Features
| **Feature Name**   | **Feature Description**                                     |
|---------------------|-------------------------------------------------------------|
| `city`             | The city where the listing is located.                      |
| `room_type`        | The type of room offered (Entire home/apt, Private room, Shared room).      |
| `room_shared`    | Indicates if the room is shared (True for shared, False for not shared).      |
| `room_private`    | Indicates if the room is private (True for private, False otherwise).      |
| `host_is_superhost`    | Whether the host is a superhost (True for superhost, False otherwise).      |
| `multi`    | Indicates if the listing is part of a multi-property setup (1 for yes, 0 for no).      |
| `biz`    | Indicates if the property is suitable for business stays (1 for yes, 0 for no).      |
| `bedrooms`    | The number of bedrooms available in the listing.      |
| `is_weekend`    | Indicates if the booking falls on a weekend (1 for yes, 0 for no).      |

#### Numerical Features
| **Feature Name**      | **Feature Description**                                     |
|------------------------|------------------------------------------------------------|
| `cleanliness_rating`     | The cleanliness rating of the listing, as rated by guests (scale from 0 to 10).                  |
| `guest_satisfaction_overall`  | Overall guest satisfaction rating (scale from 0 to 100).           |
| `dist`  | Distance of the listing from the city center (in kilometers).               |
| `metro_dist`   | Distance of the listing from the nearest metro station (in kilometers).          |
| `attr_index`           | An index indicating proximity to tourist attractions (higher values = closer).                      |
| `attr_index_norm`          | Normalized attraction index for easier comparison across listings.                     |
| `rest_index`          | An index indicating proximity to restaurants (higher values = closer).                     |
| `rest_index_norm`          | Normalized restaurant index for easier comparison across listings.                     |
| `lng`          | Longitude of the listing’s location.                     |
| `lat`          | Latitude of the listing’s location.                     |

#### Target Variable
| **Feature Name**   | **Feature Description**                                     |
|---------------------|-------------------------------------------------------------|
| `realSum`             | The target variable indicating the room price (in Euros).   |

### Data Preprocessing
- Missing values were handled.  
- Numerical columns were normalized.  
- Categorical features were encoded using [e.g., One-Hot Encoding, Label Encoding].  

## Methodology
1. **Exploratory Data Analysis (EDA):**  
   - **Univariate Analysis:**  
     - Examined individual features to understand their distribution and characteristics.  
     - Key actions:  
       - Plotted histograms, bar charts, and boxplots for numerical and categorical features.  
       - Identified skewness, outliers, and missing values.  

   - **Multivariate Analysis:**  
     - Explored relationships between multiple features to identify patterns and correlations.  
     - Key actions:  
       - Created pair plots and correlation heatmaps to evaluate dependencies among numerical features.  
       - Visualized relationships between categorical and numerical variables using boxplots and violin plots.  
       - Analyzed interaction effects, such as the influence of `room_type` and `city` on price.

2. **Data Preprocessing:**  
   -   Handle missing values and duplicates.
   - Handle outliers
      - Detect using IQR methods.
      - Standardization
         - Log transformation for Right-skewed features.
         - Square-root transformation for Left-skewed features.
         - Cube-root transformation for moderate left-skewed features.
      - Remove outliers by winsorization with percentile [0.05, 0.95].
      - Feature Encoding
         - Binary label encoding for features with two categories.
         - One-hot encoding for features with more than two categories.
      - Feature scaling
         - Apply Min-Max scaling for numerical features.
      - Data splitting
         - Train:Test = 8:2

   - Feature Selection
      - Dropped features: 
         `guest_satisfaction_overall`, `cleanliness_rating`, `attr_index`, `rest_index`
      - Selected features:
            `room_shared`,`room_private`, `person_capacity`, `host_is_superhost`, `multi`, `biz`, `bedrooms`, `dist`, `metro_dist`, `attr_index_norm`, `rest_index_norm`, `lng`, `lat`, `is_weekend`, `room_type_Private room`, `room_type_Shared room`, `city_Athens`, `city_Barcelona`, `city_Berlin`, `city_Budapest`, `city_Lisbon`, `city_London`, `city_Paris`,`city_Rome`, `city_Vienna`

3. **Model Selection:**  
   - Trained multiple models, including: Linear Regression, Ridge, Lasso, Random Forest, Gradient Boosting with default parameters. The results are as follow:

      📊 LinearRegression

         🟢 Train - MAE: 101.5335, R2: 0.2220
         🔵 Test  - MAE: 102.4646, R2: 0.2241

      📊 Ridge

         🟢 Train - MAE: 101.9560, R2: 0.2201
         🔵 Test  - MAE: 102.6475, R2: 0.2230

      📊 Lasso
         
         🟢 Train - MAE: 102.1718, R2: 0.2104
         🔵 Test  - MAE: 103.0278, R2: 0.2118

      📊 RandomForest

         🟢 Train - MAE: 21.7303, R2: 0.9263
         🔵 Test  - MAE: 56.4752, R2: 0.6656

      📊 GradientBoosting
         
         🟢 Train - MAE: 79.4672, R2: 0.4532
         🔵 Test  - MAE: 81.7521, R2: 0.3022

   - Fine-tuned hyperparameters of Random Forest using grid search, with following hyperparameters:
   ```
   param_grid = {
    'n_estimators': [100, 200, 300, 500],
    'max_depth': [None, 10, 20, 30, 40, 50],
    'min_samples_split': [2, 5, 10, 15],
    'min_samples_leaf': [1, 2, 5, 10],
    'max_features': ['auto', 'sqrt', 'log2'],
    'bootstrap': [True, False]
   }

4. **Model Evaluation:**  
   - Evaluated models using metrics MAE and R² and metrics. 
   - Compared predictions with actual values to validate model accuracy.

## Results
- Best model: Random Forest.  
The best model is Random Forest with following hyperparameter:
   ```
   {
      'bootstrap': False, 'max_depth': 30, 'max_features': 'sqrt' 'min_samples_leaf': 1, 'min_samples_split': 2, 'n_estimators': 200
   }

- Performance metrics:
   The selected model has following performance.
   ```
      🟢 Train - MAE:  0.31714266633045585
      🔵 Test - MAE:  51.80982348914899
      🟢 Train - R2:  0.9999946550793409
      🔵 Test - R2:  0.717864899828761
- Actual values vs Predicted values
![performance](/imgs/res_2.png)

## Acknowledgements
- Rakamin Bootcamp for guidance and resources.
- Airbnb Prices in European Cities dataset provider.
- Mentors and peers for support throughout the project.

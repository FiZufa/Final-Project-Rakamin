# Airbnb Price Prediction
This project is part of Data Science Bootcamp at [Rakamin](https://www.rakamin.com/) 
 
<img src="logo.png" width="150" />
*Image Source: [logodix.com](https://logodix.com)*

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

---

## Problem Statement
Setting the right price for an Airbnb listing is crucial for maximizing revenue and attracting customers. However, hosts often face challenges due to the wide range of factors influencing prices, such as location, amenities, and reviews. This project aims to develop a predictive model to address this issue.

---

## Goals and Objectives
- Analyze the factors affecting Airbnb room prices.  
- Build a machine learning model to predict room prices.  
- Provide actionable insights for Airbnb hosts.

--

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

--- 

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

2. **Feature Engineering:**  
   - Extracted new features (e.g., `price per person`, `distance to city center in miles`).  
   - Normalized and encoded features for modeling.  

3. **Model Selection:**  
   - Tested multiple models, including [e.g., Linear Regression, Random Forest, Gradient Boosting].  
   - Fine-tuned hyperparameters using grid search or random search.  

4. **Model Evaluation:**  
   - Evaluated models using metrics like RMSE, MAE, and R².  
   - Compared predictions with actual values to validate model accuracy.  

---

## Results
- Best model: [Model name].  
- Performance metrics:
  - **RMSE:** [Value].  
  - **MAE:** [Value].  
  - **R²:** [Value].  

### Key Insights

---

## Acknowledgements
- Rakamin Bootcamp for guidance and resources.
- Airbnb Prices in European Cities dataset provider.
- Mentors and peers for support throughout the project.

# Airbnb Price Prediction

## Table of Contents
1. [Introduction](#introduction)  
2. [Problem Statement](#problem-statement)  
3. [Goals and Objectives](#goals-and-objectives)  
4. [Dataset](#dataset)  
5. [Methodology](#methodology)

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
| `room_type`        | Type of room offered (e.g., Entire home, Private room).      |
| `room_shared`    | The specific neighborhood where the listing is located.      |
| `room_private`    | The specific neighborhood where the listing is located.      |
| `host_is_superhost`    | The specific neighborhood where the listing is located.      |
| `multi`    | The specific neighborhood where the listing is located.      |
| `biz`    | The specific neighborhood where the listing is located.      |
| `bedrooms`    | The specific neighborhood where the listing is located.      |
| `is_weekend`    | The specific neighborhood where the listing is located.      |

#### Numerical Features
| **Feature Name**      | **Feature Description**                                     |
|------------------------|------------------------------------------------------------|
| `cleanliness_rating`     | Minimum number of nights required to book.                  |
| `guest_satisfaction_overall`  | Total number of reviews received for the listing.           |
| `dist`  | Average number of reviews received per month.               |
| `metro_dist`   | Number of days the listing is available in a year.          |
| `attr_index`           | Geographical latitude of the listing.                      |
| `attr_index_norm`          | Geographical longitude of the listing.                     |
| `rest_index`          | Geographical longitude of the listing.                     |
| `rest_index`          | Geographical longitude of the listing.                     |
| `rest_index_norm`          | Geographical longitude of the listing.                     |
| `lng`          | Geographical longitude of the listing.                     |
| `lat`          | Geographical longitude of the listing.                     |


#### Target Variable
| **Feature Name**   | **Feature Description**                                     |
|---------------------|-------------------------------------------------------------|
| `realSum`             | The target variable indicating the room price (in Euros).   |


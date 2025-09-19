# What drives the price of a car?

Jupyter Notebook : https://github.com/sajitha-03/Used_Car_Price/

## Overview

The goal of the project is to understand what factors make a car more or less expensive. As a result of the analysis, provide clear recommendations to a used car dealership as to what consumers value in a used car.  

## Problem Statement

Given a dataset of used car attributes such as year, model, manufacturer, condition, title_status and other key features, predict the price of a used car. Addtionally, analyze and recommend what features influence the car price.

## Data Understanding

Explore the dataset to find the key features and the target variable included. Try to eyeball relationship of target variable with each of the key features. Identify missing and invalid values and the outliers from the dataset. Identify the columns that can be dropped from a modeling perspective.

- Find how big the dataset is
- Identify and drop duplicates
- Identify columns to be dropped - id, VIN
- Visualize the relationionship of price with other features
- Identify unique values in categorical features and drop columns with large number of unique values
- Drop outliers from price column
- Keep recent data up to 4 decades

Original dataset - (426880, 18)

## Data Preparation

- Dropped duplicates, columns not relevant to current analysis - id,vin,region,state,paint_color,size
- Dropped model column becasue of large number of unique values
- Kept data in the 500-150000 price range to remove outliers
- Kept more recent data from year 1980 onwards
- Filled null numerical features with median values
- Filled null categorical features with unknown values
- Applied StandardScaler to scale and PolynomialFeatures to reduce overfittng on numerical features
- Applied OneHotEncoding on catergorical features
- Split train and test data for simple cross validation

After data preprocessing - (355979, 9)

Used: 83% of rows

Key features kept for modeling used car price and analysis:
> ['year', 'odometer', 'manufacturer', 'condition', 'cylinders', 'title_status', 'transmission', 'drive', 'type']

## Modeling

Considered different models such as LinearRegression, Lasso, Ridge Regression. PCA was done for certain models to handle the dimensionality from PolynomialFeatures and OHE . 

## Findings

Comparing RMSE and R2 score between models, Ridge Regression without using PCA results in lower RMSE and better R2 score.

<img width="348" height="145" alt="Screenshot 2025-09-18 at 3 20 03 AM" src="https://github.com/user-attachments/assets/15f99890-32a2-4e19-bd82-2a0ebfdc9a51" />


<img width="805" height="478" alt="Screenshot 2025-09-18 at 3 18 32 AM" src="https://github.com/user-attachments/assets/8e85f6bc-5371-4476-98d4-f75226932505" />


<img width="805" height="478" alt="Screenshot 2025-09-18 at 3 19 29 AM" src="https://github.com/user-attachments/assets/29704b2d-d9f2-4f82-aae9-76bd847ce346" />

### Feature Importance

Visualizing importance of features from Ridge regression model - year(age), manufacturer, type, drive and odometer are the top five features that influence the car price.

<img width="881" height="550" alt="Screenshot 2025-09-18 at 6 53 58 PM" src="https://github.com/user-attachments/assets/f951de64-9885-4515-820f-6c4d160cafb0" />

Visualizing correlation between price vs other features and the feature importance, these are the findings:

- Price of older cars with high mileage is much depreciated
- Pickup/SUV/coupe/convertible type vehicles have high resale value

## Recommendations

**Recommendations to used car dealership are to increase the inventory of newer 4wd Japanese brand pickup/SUV with low miles for better sales. Limited stock of expensive cars from Mercedes-Benz/Porsche/Ferrari in good condition will also boost overall car sales**


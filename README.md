# Retail-Business-Sales-Data-Analysis

## Overview
Python-based data analysis project focusing on retail sales data. The data set used contains transaction records for a period of two years from an international retail store. The project covers data cleaning, exploration, and deriving valuable insights about sales trends and popular products.

## Business Task
To help the retail business find helpful insights that can positively impact sales.

## Data Source
The data was provided on Kaggle and can be found [here](https://www.kaggle.com/datasets/umerkk12/online-retail-business)

## Tools
Python

## Process
### Initial Data Exploration & Preprocessing
- The data analysis process for this project started with the importation of useful libraries which included pandas, numpy, and matplotlib.
- Next, I loaded the CSV file from my local storage into a data frame on python using the pd.DataFrame() class constructor.
- Then I performed an initial exploration of the data set to get an idea of what I will be working with. During this initial exploration process, I noticed the data column in the data set was loaded as an object data type, so I converted it to a datetime data type to make the data uniform and understandable.
- Lastly, I checked for null values and discovered there were 55 null values all coming from the 'CustomerNo' i.e. customer number table.
- Usually, one should drop null values to ensure data integrity, especially when I'm not provided enough information to fill in NaN values with the right data. But I decided to take a different route when I noticed a pattern with the null values.
- First, every NaN value in the 'CustomerNo' column had a corresponding negative numeric value in the 'Quantity' column. 

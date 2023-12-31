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
- Usually, one should drop null values to ensure data integrity, especially when I'm not provided enough information to fill in NaN values with the right data. But I decided to keep these values as they disproportionately affected only one country in the dataset - the United Kingdom. And since I'm not particularly doing any analysis with the CustomerNo as a main point of focus, then I didn't think it necessary to drop the null values. If, perhaps, we wanted to find the top regular or highest paying customer for that period (maybe to do a promo?) then we could consider dropping the NaN values in the CutomerNo column as it will affect aggregation.

### Data Cleaning
- After doing the initial exploration, the next thing is to clean out the data to ensure integrity. I noticed a couple of patterns while I was exploring the data that needed investigation:
- First, every NaN value in the 'CustomerNo' column had a corresponding negative numeric value in the 'Quantity' column. This is unusual of course since quantity of items bought can only be a positive integer.
- Secondly, all NaN values in the 'CustomerNo' column had corresponding alpha-numeric 'TransactionNo' values, which was quite strange as the transaction number is supposed to be numeric. But I first thought probably it was the naming convention of the retail business' transaction numbers, but I discovered that only 1.6% of the data set had this alpha-numeric convention. Plus, all alpha-numeric TransactionNo corresponded to negative quantity values.
- My assumption was that there was probably an issue with the device that logged transactions at the point of sale that recorded alpha-numeric Transaction numbers (instead of numeric only) and negative quantity values (instead of positive integers only). Either way, I proceeded to clean these out.
-  First thing I did was to create a copy of the dataframe. Just to ensure I always have a copy of the original data as it is. Next, I defined a function to iterate on a given column in the dataframe to replace the negative instance of the value with its positive. I then applied this function to the Quantity column.
-  To clean the TransactionNo column, I simply stripped the values to recover only the numeric part.
-  I then checked for duplicates and dropped these duplicates after checking to see whether the duplication was intentional or not.
-  Looking at the dataset further I noticed a similar pattern in the ProductNo column to the one I noticed in the TransactionNo column; where there was a mixture of numeric and alpha-numeric values. Only this time, there was a legitimate reason for this pattern - Upon investigation, I noticed that two different products in the dataset had the same numeric ProductNo component but a different ProductNo alphabet component. If I had proceeded to strip these alphabets from the product numbers, as I did with the transaction numbers, I would have had a huge problem of mismatch, confusion, and pseudo-duplication. 

### Feature Engineering
- For the purpose of our analysis, we needed to extract some interactive features from the dataset. One of which was TotalAmt, which is the multiplication of the Price and Quantity columns.
- Another feature I was interested in looking at was the month in which each transaction took place. To do this, I extracted the month name from our Date column.

### Data Exploration & Visualization
- Once the cleaning and feature engineering process had been settled, I proceeded to query the data to get some business insights that can arm stakeholders with the necessary data-backed knowledge to make positive decisions that would impact the growth of the business.

#### Top-Selling Products
- First, I analyzed the top 10 grossing products out of 3,768 products sold within the time period of the dataset (01/12/2018 - 09/12/2019)

![total_amt_sold_per_product](https://github.com/txs7n/Retail-Business-Sales-Data-Analysis/assets/118135226/1ddc4ddf-fccc-44fc-9812-b9b1fa0bb0b8)

#### Frequently Sold Products
- The top-selling products do not tell the full story, because while the above graph represents the top-grossing products for our store, it could mean this was as a result of huge one-time purchases. Which was investigated and found to be true. So, I decided to also analyze the most frequently sold products as well.

![most_freq_sold_products](https://github.com/txs7n/Retail-Business-Sales-Data-Analysis/assets/118135226/294571b6-0081-4102-880a-0121b08da474)

- So even though 'Medium ceramic top storage jar' is the most sold by total amount, 'Cream Hanging Heart T-Light Holder' is the most frequently sold.

#### Top Sales Month 
- I also analyzed the top sales month and as expected, the holiday months ranked high

![total_amt_sold_per_month](https://github.com/txs7n/Retail-Business-Sales-Data-Analysis/assets/118135226/29186bb0-7c5f-45a8-9918-1abdb6fb2f35)

#### Top Sales by Country
- From our analysis, we see that most of the company's sales came from them United Kingdom.

![total_amt_sold_per_country](https://github.com/txs7n/Retail-Business-Sales-Data-Analysis/assets/118135226/82bdb1af-cbca-42b7-895b-ae51e1ba64ae)


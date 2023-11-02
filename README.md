# Sales Prediction Model
This project repository contains the data analysis and model training using the data that came from all food items sold at various stores from 1985 to 2009

## Data Definition

**Link to the data:**
[HERE](https://docs.google.com/spreadsheets/d/e/2PACX-1vTB8dpLqxYs1II-ubJFUnfFu2jO8TEVnDPjAJ2rl3Yup02v-UzBapk3tE_Vft51jvAkwftMpsWBCJpn/pub?output=csv)

The data used for this project is from the sales of food items at various stores between 1985 to 2009. The dataset contains information about food items and the outlet where it is sold.

### Dictionary
| Column Name               | Description                                                                                         |
| ------------------------- | --------------------------------------------------------------------------------------------------- |
| Item_Identifier           | Unique product ID                                                                                   |
| Item_Weight               | Weight of product                                                                                   |
| Item_Fat_Content          | Whether the product is low fat or regular                                                           |
| Item_Visibility           | The percentage of the total display area of all products in a store allocated to the particular product |
| Item_Type                 | The category to which the product belongs                                                           |
| Item_MRP                  | Maximum Retail Price (list price) of the product                                                    |
| Outlet_Identifier         | Unique store ID                                                                                     |
| Outlet_Establishment_Year | The year in which the store was established                                                             |
| Outlet_Size               | The size of the store in terms of ground area covered                                               |
| Outlet_Location_Type      | The type of area in which the store is located                                                      |
| Outlet_Type               | Whether the outlet is a grocery store or some sort of supermarket                                   |
| Item_Outlet_Sales         | Sales of the product in the particular store. This is the target variable to be predicted.          |

## Data Analysis

View the EDA [here](https://colab.research.google.com/drive/1-vru7kb2L66F5kNqojhkHTzv6Bz9EM6I?usp=sharing)

### Exploratory Data Analysis (EDA)
- Dataset has 7 categorical columns and 5 numerical columns
- `Item_Outlet_Sales` and `Item_Visibility` are positively skewed and not normally distributed
- `Item_Weight` is normally distributed with no appreciable skewness
- From the box plots on the categorical data related to the `Item_Outlet_Sales`, most of the data have outliers that are dispersed
- There is only 1 pair of columns that have a significant correlation across the dataset

### Explanatory Data Analysis

![Top 10 Highest Total Average Sales per Outlet]('/images/top10_high_and_average_sales.png')

- Based on the graph above, OUT027 has the highest sales all time with around 3.45 million sales, averaging 3694.04 of sales all time
- Based on the graph above, OUT019 has the lowest sales all time with around 179,694 sales, averaging 340.33 of sales all time

![Outlet Sales Trend per Location Type ]('/images/sales_per_loctype.png')
- Tier 1 has an uptrend that spans from 1985 up to 2000.
- Tier 2 has an uptrend that spans from around 2002 up to 2007.
- Tier 3 had a downtrend from 1985 to 1997, but had an uptrend from 1997 until 2010


## Model Design

### Comparision of implemented models
|    Metrics           | Linear Regression | Decision Trees Regression[^1] |
| ------------------------ | ----------------- | --------------------------- |
| RMSE @ Train             | 1,208             | **1,082**                    |
| RMSE @ Test              | 1,165             | **1,057**                       |
| Confidence Score @ Train | 51%               | **60%**                         |
| Confidence Score @ Test  | 51%               | **59%**                         |
[^1] Decision Trees Regression is tuned by using `max_depth` only

## Summary and Recommendation
After analyzing the data and fitting the data to models, I recommend using the Decision Trees Regressor as the main model for predicting this data. Since the recommended model is not yet fully tuned, there is still room for improvement in the model's performance.

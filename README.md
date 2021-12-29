# Price analysis of first hand residential sales
*This project extracts and combines information from several pdfs, to analyse and predict residential sales data of a newly launched pre-sale project (One Victoria in Kai Tak, Hong Kong).*

## 1. Data
The data is published by the developer on their pre-sale website at the following links:
- [Register of Transactions:] (https://www.onevictoria.com.hk/en/register/)
- [Price List:] (https://www.onevictoria.com.hk/en/housing/price_list/)
- [Sales Brochure:] (https://www.onevictoria.com.hk/en/housing/brochure/)
- [Sales Arrangement:] (https://www.onevictoria.com.hk/en/sales_arrangement/)

## 2. Method
The source files are in pdf format which are first cleaned and combined into a master summary of the development for further analysis.

The key steps consist of: 
a) Extract price details from "Price List". The units are sold in batches, so there are multiple price lists. The price list tables are updated when a new batch of pre-sale units are launched.
b) Merge information with the "Sales Arrangement". This contains the first launch date. 
c) Merge "Registration of Transaction". This includes the ASP, P-ASP and Cancelled Transactions.

## 3. Data Cleaning
Tabula is used to read from pdf and convert into csv file (tabula.convert_into), because direct import into a dataframe (tabula.read_pdf) was slow. 
A function was defined and used to extract and clean data from price lists which had the same regular patterns after reading from tabula.
Some price lists requried further cleaning as the extracted data was shifted and did not match correctly. 

## 4. EDA
![heatmap](https://user-images.githubusercontent.com/85296113/147647921-d494f1e4-c347-499a-8e21-e1aaa98a27f4.png)

A heatmap of the non-categorical numeric columns show that there are redundant features (i.e. price, price/SA, transaction price).

![pricesa_floor_plno](https://user-images.githubusercontent.com/85296113/147648145-a9bf67c4-ab2d-462f-a0a7-52d0b0181610.png)

Of the launched units, the price per saleable area increases in subsequent price lists. Developers tend to factor in price increases in later launches, the units also tend to be more desirable than the first launch units, in terms of view and higher floors etc.

![dvptsum](https://user-images.githubusercontent.com/85296113/147651249-29fff7f5-9ff8-4570-8113-3cd994adf03e.png)

A development summary table is created to gain a quick overview of key development parameters, e.g. average flat size and average price per saleable area. 

## 5. Machine Learning Algorithms and Prediction
The data was split into train-test sets to build a regression model for predicting prices of future launches. OLS, linear, ridge and lasso regression were used. Hyperparameter tuning was performed with Grid Search for linear regression to identify the key features. The scores for various alpha values are tested for the Ridge and Lasso models. The Ridge model performs best, with the highest coefficient of determination for the predictions at 0.96. An alpha of 0.01 was selected. There are few data samples and many features (after encoding categorical features), so the Ridge model is suitable. 
![ridge_alpha](https://user-images.githubusercontent.com/85296113/147672618-5da52872-41b8-488a-9077-bef782f5e10d.png)
![ridge_fit](https://user-images.githubusercontent.com/85296113/147672642-de34cc31-1aff-49f7-93df-d2086045999c.png)

## 6. Future Improvements
The analysis can be repeated for the new developments in Kai Tak to get an analysis of the area. The flat type summary currently requires manual analysis of floor plans, the project can be extended to include image analysis to extract this data for faster analysis. 

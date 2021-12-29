# Capstone_Two_Data_Wrangling
*This project extracts and combines information from several pdfs, to analyse and predict residential sales data of a newly launched pre-sale project (One Victoria).*

## Data
The data is published by the developer on their pre-sale website at the following links:
- [Register of Transactions:] (https://www.onevictoria.com.hk/en/register/)
- [Price List:] (https://www.onevictoria.com.hk/en/housing/price_list/)
- [Sales Brochure:] (https://www.onevictoria.com.hk/en/housing/brochure/)
- [Sales Arrangement:] (https://www.onevictoria.com.hk/en/sales_arrangement/)

## Method
The source files are in pdf format which is first cleaned and combined into a master summary of the development for further analysis.

The key steps consist of: 
a) Extract price details from "Price List". The units are sold in batches, so there are multiple price lists. The price list tables are updated when a new batch of pre-sale units are launched.
b) Merge information with the "Sales Arrangement". This contains the first launch date. 
c) Merge "Registration of Transaction". This includes the ASP, P-ASP and Cancelled Transactions.

## Data Cleaning

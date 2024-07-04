# Customer-Purchase-Analysis-Project
Objective:
To analyze customer purchase data to uncover insights about purchasing behavior, identify sales trends, and visualize key metrics.

Dataset:
Assuming we have a CSV file named customer_purchases.csv with the following columns:

CustomerID
PurchaseDate
ProductID
ProductCategory
Quantity
UnitPrice
Libraries Import:

Import the necessary libraries for data analysis (pandas) and visualization (matplotlib, seaborn).
Load the Dataset:

Load the customer purchase data from a CSV file into a DataFrame.
Data Cleaning:

Check for missing values and drop rows with missing CustomerID or ProductID.
Convert the PurchaseDate column to a datetime format.
Add a column for the total purchase amount (TotalAmount).
Data Analysis:

Calculate total sales by product category and sort the results to identify the most popular categories.
Calculate monthly sales by extracting the month from the PurchaseDate column and grouping by month.
Identify the top 10 customers by total purchase amount.
Data Visualization:

Create a bar plot for total sales by product category.
Create a line plot to visualize the monthly sales trend.
Create a bar plot for the top 10 customers by total purchase amount.

# Customer-Purchase-Analysis-Project
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
df = pd.read_csv('customer_purchases.csv')

# Display the first few rows of the dataset
print(df.head())

# Data Cleaning
# Check for missing values
print(df.isnull().sum())

# Drop rows with missing CustomerID or ProductID as they are crucial for analysis
df = df.dropna(subset=['CustomerID', 'ProductID'])

# Convert 'PurchaseDate' column to datetime format
df['PurchaseDate'] = pd.to_datetime(df['PurchaseDate'])

# Add a column for total purchase amount
df['TotalAmount'] = df['Quantity'] * df['UnitPrice']

# Data Analysis
# Calculate total sales by product category
total_sales_by_category = df.groupby('ProductCategory')['TotalAmount'].sum().reset_index().sort_values(by='TotalAmount', ascending=False)
print(total_sales_by_category)

# Calculate total sales by month
df['Month'] = df['PurchaseDate'].dt.to_period('M')
monthly_sales = df.groupby('Month')['TotalAmount'].sum().reset_index()
print(monthly_sales)

# Identify top customers by total purchase amount
top_customers = df.groupby('CustomerID')['TotalAmount'].sum().reset_index().sort_values(by='TotalAmount', ascending=False).head(10)
print(top_customers)

# Data Visualization
# Total Sales by Product Category
plt.figure(figsize=(10, 6))
sns.barplot(x='TotalAmount', y='ProductCategory', data=total_sales_by_category)
plt.title('Total Sales by Product Category')
plt.xlabel('Total Sales Amount')
plt.ylabel('Product Category')
plt.show()

# Monthly Sales Trend
plt.figure(figsize=(12, 6))
sns.lineplot(x='Month', y='TotalAmount', data=monthly_sales)
plt.title('Monthly Sales Trend')
plt.xlabel('Month')
plt.ylabel('Total Sales Amount')
plt.xticks(rotation=45)
plt.show()

# Top Customers by Total Purchase Amount
plt.figure(figsize=(10, 6))
sns.barplot(x='TotalAmount', y='CustomerID', data=top_customers)
plt.title('Top 10 Customers by Total Purchase Amount')
plt.xlabel('Total Purchase Amount')
plt.ylabel('Customer ID')
plt.show()



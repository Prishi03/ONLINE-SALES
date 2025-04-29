# 🛒 Sales Data Analysis using SQL

This project focuses on analyzing sales order data using SQL queries. The dataset includes details such as `Order_ID`, `Product_ID`, `Order_Date`, `Total_Amount`, etc. The analysis uncovers trends in monthly revenue and ordering behavior, helping stakeholders make data-driven decisions.

---

## 📌 Dataset Overview

The dataset used in this project contains the following key columns:

- `Order_ID`: Unique identifier for each order  
- `Product_ID`: Unique identifier for each product  
- `Order_Date`: Date the order was placed  
- `Quantity`: Number of items purchased  
- `Unit_Price`: Price per item  
- `Total_Amount`: Total revenue for each order

---

## 🔧 Data Preparation (Excel)

Before importing the dataset into MySQL:

- Removed **duplicates**, **blank rows**, and **null values**
- Renamed columns and **standardized headers**
- Ensured all **data types** were appropriate
- Converted date fields to proper `datetime` format

---

## 🧠 Key SQL Concepts Used

- `GROUP BY`, `ORDER BY`, `LIMIT`  
- Aggregates: `SUM()`, `COUNT()`, `AVG()`  
- Date functions: `MONTH()`, `YEAR()`, `EXTRACT()`  
- `HAVING` clause for filtering aggregated data  
- Filtering using `WHERE` and combining with `HAVING`  

---

## 📊 Key Insights & Queries

- **Monthly Revenue Trends**: Identified months with highest and lowest revenue  
- **Top Ordering Months**: Found top 3 months with most orders placed  
- **Order Frequency**: Counted distinct orders per month  
- **Average Revenue**: Tracked average monthly revenue  
- **Revenue Thresholds**: Filtered months where revenue exceeded ₹50,000

### Sample Query:
```sql
SELECT 
  MONTH(Order_Date) AS Month,
  SUM(Total_Amount) AS Total_Revenue,
  COUNT(DISTINCT Order_ID) AS Number_of_Orders
FROM `order table`
WHERE YEAR(Order_Date) = 2023
GROUP BY MONTH(Order_Date)
HAVING SUM(Total_Amount) > 50000
ORDER BY Month;

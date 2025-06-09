# E-commerce-Data-Analysis-Report
This project analyzes e-commerce transaction data to uncover customer buying behavior, top-selling products, and sales by country. Using SQL queries on a real dataset, it demonstrates data aggregation, filtering, and insights extraction to support data-driven marketing and business decisions in e-commerce.
E-commerce Data Analysis Report
This report presents an analysis of an online retail dataset sourced from Kaggle, which contains detailed transactional data from a UK-based online store. The dataset includes information such as invoice numbers, product descriptions, quantities sold, invoice dates, unit prices, customer IDs, and countries of purchase. The transactions span multiple years and provide a comprehensive view of customer purchasing behavior, product popularity, and sales distribution across different regions.
The purpose of this report is to leverage SQL queries to extract actionable insights relevant to e-commerce operations. The analyses focus on identifying best-selling products, understanding customer purchase patterns, and evaluating sales performance by country. These insights can help businesses optimize inventory management, marketing strategies, and geographic focus to drive growth and improve customer satisfaction.


# Objective:Identify the top 10 products based on total quantity sold to determine which items are the most popular among customers.

**SQL Query:**
```sql
SELECT Description, SUM(Quantity) AS TotalQuantitySold
FROM data
GROUP BY Description
ORDER BY TotalQuantitySold DESC
LIMIT 10;
# Insights: This query highlights the products with the highest sales volume. Knowing which products sell the most can inform inventory management and marketing priorities.

 
**# Objective: Find the top 10 customers who bought the largest number of items, showing the most engaged or high-value buyers.
****SQL Query:**
```sql
SELECT CustomerID, SUM(Quantity) AS TotalItemsBought
FROM data
WHERE CustomerID IS NOT NULL
GROUP BY CustomerID
ORDER BY TotalItemsBought DESC
LIMIT 10;

![image](https://github.com/user-attachments/assets/e616202b-c625-4dda-9fb6-c7b1948286e4)

#Insights: Identifying top customers helps tailor loyalty programs and personalized marketing.This analysis reveals buyer concentration and potential key accounts.

 


#Objective: Calculate total sales revenue for each country to understand geographic revenue distribution.
**SQL Query:**
```sql
SELECT Country, SUM(Quantity * UnitPrice) AS TotalSales
FROM data
GROUP BY Country
ORDER BY TotalSales DESC;

![image](https://github.com/user-attachments/assets/820097f7-7279-4386-b1d8-b549066e0952)


# Insights:This query shows which countries generate the most revenueEnables strategic decisions regarding market focus and resource allocation
# Summary: These analyses provide a foundational understanding of product performance, customer engagement, and geographic sales distribution in an e-commerce setting. Such insights are essential for data-driven decision making in marketing, sales, and inventory planning.
 


# Project 3: December 2011 Sales Analysis
# Objective: Analyze customer purchase behavior in December 2011 to identify the top-selling products by total revenue and average quantity sold per transaction.
# Data Source: Online Retail Dataset (Kaggle) — includes sales transactions with product details, quantity, unit price, invoice date, and customer information.
 #SQL Analysis:
We filtered sales records for December 2011 and grouped data by product code and description. For each product, we calculated: The average quantity sold per transaction (avg_quantity). The total revenue generated (total_revenue).

**SQL Query:**
```sql

SELECT 
  StockCode,
  Description,
  AVG(Quantity) AS avg_quantity,
  SUM(Quantity * UnitPrice) AS total_revenue
FROM data
WHERE InvoiceDate LIKE '12/%/2011%'
GROUP BY StockCode, Description
ORDER BY total_revenue DESC
LIMIT 10;
 
![image](https://github.com/user-attachments/assets/4696b799-765f-4dc0-84be-69bd323c2d39)

# Findings: The top 10 products contributed the highest sales revenue during December 2011.Average quantity sold per transaction varies, reflecting product demand and purchase patterns. This analysis can help marketing and sales teams focus on high-performing products during peak seasons.
# Next Steps:
•	Extend analysis to compare monthly sales trends.
•	Perform customer segmentation based on purchase behavior.
•	Integrate with inventory data to optimize stock management.
We are going to explore customer segmentation based on customer behaviour

**SQL Query:**
```sql

SELECT 
  CustomerID,
  COUNT(DISTINCT InvoiceNo) AS PurchaseFrequency,  -- Cuántas compras únicas hizo
  SUM(Quantity) AS TotalItemsBought,                -- Total de ítems comprados
  SUM(Quantity * UnitPrice) AS TotalSpent           -- Monto total gastado
FROM data
WHERE CustomerID IS NOT NULL
GROUP BY CustomerID;

#![image](https://github.com/user-attachments/assets/89197744-7f68-4ea6-ad65-459bb129e497)

 

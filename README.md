# Capstone-Project (Sales Performance Analysis)

## Project Overview: Analyzing Sales Data

**Objective**:  
To analyze sales data to uncover insights that support data-driven decision-making, enhance sales strategies, and optimize inventory management.

### Expected Outcomes:
- Clear understanding of sales performance.
- Informed decisions on marketing and inventory.
- Enhanced profitability through targeted strategies.

### Tools:
- Excel
- SQL
- Power BI

---

### Data Understanding and Observations:

Before starting this project, I took some time to understand the data and the key questions I needed to answer. Here are my observations:

1. **Data Cleaning**:  
   I started by using **Excel** to clean the data. The first task was to **remove duplicates**, using all columns as criteria to ensure the data was accurate and consistent.

2. **Calculating Total Sales**:  
   After cleaning the data, I proceeded to calculate the **total sales** for each transaction by multiplying the **quantity** by the **unit price**. This step provided a more comprehensive view of total revenue.

3. **Sales Analysis with Pivot Table**:  
   Next, I created a **Pivot Table** in Excel to analyze the sales performance. This allowed me to group sales data by:
   - **Category**
   - **Product**
   - **Region**
   - **Month** (I grouped the dates into monthly intervals for better analysis)

The Pivot Table was essential for uncovering trends and gaining insights into sales patterns across different dimensions.


![image](https://github.com/user-attachments/assets/494b80dc-2f2a-48e7-8155-cdfa12656995)

#### A. Total Sales by Product Report

This report provides a summary of total sales for each product. It allows us to identify which products are performing well and where to invest more capital based on sales performance. If a product is selling quickly, consider increasing inventory or boosting marketing efforts for that item.

#### B. Total Sales by Region Report

This report summarizes total sales across different regions. It helps us understand which areas are driving sales and where there may be opportunities for growth. By analyzing regional performance, we can make informed decisions about resource allocation, marketing strategies, and expansion efforts.

#### C. Total Sales by Month Report

This report provides a summary of total sales broken down by month. It enables us to track sales trends over time, identify seasonal patterns, and evaluate the effectiveness of marketing initiatives. By understanding monthly sales performance, we can make data-driven decisions for future strategies and budget allocations. This report shows the same as the **E** (top selling region report)

#### D. Average Sales and Quantity by Product Report

This report presents the average sales and average quantity sold for each product. It allows us to assess overall product performance and understand customer demand. By analyzing average sales and average quantity, we can identify which products are consistently popular and determine where to focus inventory and marketing efforts.


##### 4. I futher analyse the data using Excel formula formulas to calculate the metrics

Using the formula to calculate average sales yields the same result as the pivot table analysis. This demonstrates an alternative method for calculating averages. 

### Formula Used
`=AVERAGEIF(SalesData!C2:C10426, "jacket", SalesData!H2:H10426)`

In this formula, "jacket" is the specific product for which the average sales are calculated from the sales data.

![image](https://github.com/user-attachments/assets/eb663f5f-f231-40ef-9e28-0a52bb980579)

I also used a formula to calculate the total sales for each region.

### Formula Used
`=SUMIF(SalesData!D2:D10426, "RegionName", SalesData!H2:H10426)`

In this formula, "RegionName" is replaced with the specific name of the region we want to analyze. This will sum all sales in the specified region from the sales data.

![image](https://github.com/user-attachments/assets/800e66cf-0d6a-4e18-821a-a54676df455c)


# SQL Analysis on Sales Data

## Overview
This queries provides an analysis of sales data using SQL, Each query addresses a specific aspect of the sales performance.
```sql
-- Total sales for each product category --
SELECT product, SUM(Total_sale) AS Total_sale
FROM SalesData
GROUP BY product;

-- Number of sales transactions in each region --
SELECT region, COUNT(*) AS transaction_count
FROM SalesData
GROUP BY region;

-- Highest-selling product by total sales value --
SELECT TOP 1 product, SUM(Total_sale) AS total_sales
FROM SalesData
GROUP BY product
ORDER BY total_sales DESC;

-- Total revenue per product --
SELECT product, SUM(Total_sale) AS total_revenue
FROM SalesData
GROUP BY product;

-- Monthly sales totals for the current year --
SELECT MONTH(Orderdate) AS month,
       SUM(Total_sale) AS total_sales
FROM SalesData
WHERE YEAR(Orderdate) = 2024
GROUP BY MONTH(Orderdate)
ORDER BY MONTH(Orderdate);

-- Top 5 customers by total purchase amount --
SELECT TOP 5 customer_id, SUM(Total_sale) AS total_purchase
FROM SalesData
GROUP BY customer_id
ORDER BY total_purchase DESC;

-- Percentage of total sales contributed by each region --
SELECT region,
       SUM(Total_sale) AS total_sales,
       (SUM(Total_sale) / (SELECT SUM(Total_sale) FROM SalesData) * 100) AS percentage_of_total_sales
FROM SalesData
GROUP BY region;

-- Products with no sales in the last quarter --
SELECT product
FROM SalesData
GROUP BY product
HAVING SUM(CASE WHEN Orderdate BETWEEN '2024-06-01' AND '2024-08-31' THEN 1 ELSE 0 END) = 0;

-- ==========================
-- End of SQL Analysis
-- ==========================

# Capstone-Project 

[Expected Outcomes](#expected-outcomes)

[Tools](#tools)

[Data Understanding and Observations](#data-understanding-and-observations)

[SQL Analysis on Sales Data](#sql-analysis-on-sales-data)

[Visualising Sales Data with Power BI](#visualising-sales-data-with-power-bi)

## Capstone Project 2

[Objective](#objective)

[Tools Used](#tools-used)

[Expected Outcomes](#expected-outcomes)

[pivot Presentation](#pivot-presentation)
 
[Visualising customer Data with Power BI](#visualising-customer-data-with-power-bi)

# Sales Performance Analysis

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



### Total sales for each product category
```sql
SELECT product, SUM(Total_sale) AS Total_sale
FROM SalesData
GROUP BY product;
```

### Number of sales transactions in each region 
```sql
SELECT region, COUNT(*) AS transaction_count
FROM SalesData
GROUP BY region;
```

### Highest-selling product by total sales value
```sql
SELECT TOP 1 product, SUM(Total_sale) AS total_sales
FROM SalesData
GROUP BY product
ORDER BY total_sales DESC;
```

### Total revenue per product
```sql
SELECT product, SUM(Total_sale) AS total_revenue
FROM SalesData
GROUP BY product;
```

### Monthly sales totals for the current year
```sql
SELECT MONTH(Orderdate) AS month,
SUM(Total_sale) AS total_sales
FROM SalesData
WHERE YEAR(Orderdate) = 2024
GROUP BY MONTH(Orderdate)
ORDER BY MONTH(Orderdate);
```

 ### Top 5 customers by total purchase amount
```sql
SELECT TOP 5 customer_id, SUM(Total_sale) AS total_purchase
FROM SalesData
GROUP BY customer_id
ORDER BY total_purchase DESC;
```

### Percentage of total sales contributed by each region 
```sql
SELECT region,
SUM(Total_sale) AS total_sales,
(SUM(Total_sale) / (SELECT SUM(Total_sale) FROM SalesData) * 100) AS percentage_of_total_sales
FROM SalesData
GROUP BY region;
```

### Products with no sales in the last quarter 
```sql
SELECT product 
FROM SalesData
GROUP BY product
HAVING SUM(CASE WHEN Orderdate BETWEEN '2024-06-01' AND '2024-08-31' THEN 1 ELSE 0 END) = 0;
```

-- ==========================
-- End of SQL Analysis
-- ==========================

# Visualising Sales Data with Power BI
### Power BI Data Preparation

1. Imported the dataset into Power BI.
2. Corrected the data types for accuracy.
3. Cleaned the data by rearranging the dates to fit the date data type correctly.
4. Grouped the dates into months for better analysis.
5. Created a measure to calculate total revenue.

![image](https://github.com/user-attachments/assets/392bfd13-c07f-43c4-a5e7-50b0147a7f45)


## Sales Total Revenue & Total Quantity of Products Sold

These metrics offer a high-level overview of the overall sales performance. The **Total Revenue** ($2,101,090) reflects the financial success, while the **Total Quantity of Products Sold** (68,461) indicates the volume of products moved. Together, these figures summarize the business’s achievements in terms of revenue generation and product demand.

## Sales Distribution by Region (Pie Chart)

This pie chart illustrates the distribution of sales across different regions. The **East region** leads with 44.16% of total sales, followed by the **North region** at 23.13%, with other regions contributing smaller shares. This breakdown helps identify regional strengths, allowing the business to focus on high-performing areas or to develop targeted strategies for regions with lower sales.

## Top Selling Products (Bar Chart)

This bar chart highlights the best-selling products, with **Shoes** being the highest-selling item, followed by **Shirts** and **Hats**. This insight helps identify the most popular products that drive significant revenue, guiding inventory management and marketing efforts toward these high-demand items.

## Quantity Sold by Region (Donut Chart)

The donut chart shows the distribution of product quantities sold by region. It reveals a fairly even distribution, with each region contributing approximately the same share. This balance suggests that demand for products is relatively uniform across all regions.

## Quantity of Product Sold by Month (Stacked Bar Chart)

This chart shows the monthly sales breakdown of products, highlighting seasonal demand variations. 

- **Hats** peak in sales in **March**.
- **Shoes** and **shirts** have consistent demand year-round.

This data aids in inventory and marketing strategy planning.


## Conclusion

The sales data analysis showed that:

1. **Top Products**: Gloves clear best-sellers.
2. **Regional Strengths**: East perform better than others.










# Capstone Project 2: Customer Segmentation for a Subscription Service

## Objective:
Segment customers based on their **subscription behavior**, **region**, and **purchase patterns** to:
- Improve **customer retention**.
- Create **targeted marketing** strategies.
- Optimize **subscription plans** to boost revenue and **customer retention value**.

## Tools Used:
- **Excel** for data cleaning and analysis.
- **SQL** for querying and data manipulation.
- **Power BI** for visualization and reporting.

## Expected Outcomes:
- Enhanced **customer retention** with personalized marketing.
- Optimized **subscription offerings** to drive revenue.
- Insights into the most **profitable customer segments** and regions.

### Tools:
- Excel
- SQL
- Power BI
---
## pivot Presentation
---

### Subscription Type Report

This report provides the total number of customers for each subscription type. It highlights customer distribution across different subscription plans, offering insights into popular subscription tiers and customer preferences.

![image](https://github.com/user-attachments/assets/dd2e27d6-a1ec-4c4d-a6ce-542055accc3b)

### Customer Subscription Analysis

## Table 1: Active vs. Canceled Customers
This table presents the count of active customers compared to those who have canceled their subscriptions. This data provides an overview of customer retention and cancellation rates.

## Table 2: Retention Analysis for 2022 and 2023
The second table dives deeper into customer retention trends by showing:
- The number of customers who canceled their subscriptions in 2022 and 2023.
- The number of customers who remained active across both years.

These insights help assess the effectiveness of retention efforts and identify patterns in customer loyalty over time.


![image](https://github.com/user-attachments/assets/4716728d-5968-4f37-b232-3f2e5c3c786b)


## Table 1: Subscription Start Date by Quarter
The first table compares the subscription start date with each quarter of the year. This analysis helps identify trends in customer sign-ups by quarter, revealing any seasonal patterns in subscription activity.

## Table 2: Subscription Start Date by Type and Year
The second table provides a comparison of the subscription start date by both subscription type and year. This breakdown offers insights into how different subscription types have trended over time, helping to assess long-term customer preferences.


![image](https://github.com/user-attachments/assets/b4b22a7a-4107-4701-b778-e9292c208077)

# SQL Queries for CUSOMER SEGMENATION FOR A SUBSCRIPTION SERVICE

```sql
 Select * from [dbo].[CustomerData]
 ```

 ### retrieve the total number of customers from each region.
```sql
Select region, count(CustomerID) as Total_number
 from [dbo].[CustomerData]
 group by region
```


 ### the most popular subscription type by the number of customers
 ```sql
select subscriptionType, count(customerid) as most_Popular
 from [dbo].[CustomerData]
 group by SubscriptionType
```

 ### customers who canceled their subscription within 6 months
```sql
 select customerid from [dbo].[CustomerData]
 where DATEDIFF(month,subscriptionStart,subscriptionend) <=6
```

 ### the average subscription duration for all customers.
 ```sql
select avg(datediff(day,subscriptionStart,subscriptionend)) as AverageSubscripionDuration
 from [dbo].[CustomerData]
 ```

 ### customers with subscriptions longer than 12 months.
```sql
 select customerid, subscription_length
 from [dbo].[CustomerData]
 where DATEDIFF(month,subscriptionStart,subscriptionend) > 12
```

 ### Total revenue by subscription type
```sql select subscriptiontype, sum(revenue) as total_revenue
from [dbo].[CustomerData]
group by subscriptiontype;
```

### Top 3 regions by subscription cancellations.
```sqlselect top 3 region,count(*) as cancellation 
from [dbo].[CustomerData]
where canceled = '0'
group by region
order by cancellation desc;
```

### The total number of active and canceled subscriptions
 ```sqlselect sum(case when canceled= '1' then 1 else 0 end) as active,
sum(case when canceled= '0' then 1 else 0 end) as cancelled
from [dbo].[CustomerData];
```


# Visualising customer Data with Power BI
### Power BI Data Preparation

1. I_ Imported the dataset into Power BI.
2. I Corrected the data types for accuracy.
3. I Cleaned the data by rearranging the dates to fit the date data type correctly.

![image](https://github.com/user-attachments/assets/6e956cd5-6a00-4bc9-b5c0-f92284a5c631)









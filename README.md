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
## pivot represenaaton
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


# Visualising Sales Data with Power BI
### Power BI Data Preparation

1. I_ Imported the dataset into Power BI.
2. I Corrected the data types for accuracy.
3. I Cleaned the data by rearranging the dates to fit the date data type correctly.

![image](https://github.com/user-attachments/assets/6e956cd5-6a00-4bc9-b5c0-f92284a5c631)



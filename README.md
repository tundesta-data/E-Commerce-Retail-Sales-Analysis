# E-Commerce Retail Sales Analysis | Revenue, Trends, and Insights
Excel + SQL + Power BI Project | E-Commerce Retail Sales Datat | From Raw Data to Buniness Insights

## Table Of Contents
* [Project Overview](#project-overview)
* [Tools & Technologie](#tools--technologie)
* [Dataset Overview](#dataset-overview)
* [Data Cleaning](#data-cleaning)
* [Exploratory Analysis](#exploratory-analysis)
* [Power BI Dashboard](#power-bi-dashboard)
* [Key Metrics](#key-metrics)
* [Key Insights](#key-insights)
* [Recommendations](#recommendations)

### Project Overview
This project provides a comprehensive view of sales performance, profitability, customer purchasing behavior, and regional trends. 
The goal was to transform raw transactional data into actionable insights that can support better business decision-making.

### Tools & Technologies
* Excel
* MySQL → Data cleaning, transformation, and querying
* Power BI → Data visualization and dashboard development

### Dataset Overview
Column
OrderID, OrderDate, Region, Category, Subcategory, CustomerSegment, Sales, Quantity, Discount, Profit

Sample Preview
| OrderID | OrderDate | Region | Category | Subcategory | CustomerSegment | Sales | Quantity | Discount | Profit |
|---------|-----------|--------|----------|-------------|-----------------|-------|----------|----------|--------|
| ORD100000 | 2021-05-02 | East | Office Supplies | Blinders | Home Office | 383.2 | 8 | 0.2 | -0.3 |
| ORD100001 | 2023-02-09 | West | Office Supplies | Art Supplies | Coeprate | 1735.03 | 4 | 0.1 | -77.82 |

### Data Cleaning
- Removed missing or invalid values
- Created new calculated fields
- Revenue = Units_Sold * Unit_Price
- Profit_Margin = Profit / revenue

### Exploratory Analysis
- Total Revenue and Profit
```sql
SELECT SUM(Sales) AS total_sales,
		SUM(Profit) AS total_profit
FROM datasta.retail_sales;
```
- Total Sale by Region
```sql
SELECT 
    Region,
    SUM(Sales) AS total_sales
FROM datasta.retail_sales
GROUP BY Region
ORDER BY total_sales DESC;
```
- Sales by Category
```sql
SELECT category,
		SUM(Sales) AS total_sales,
		SUM(Profit) AS total_profit
FROM datasta.retail_sales
GROUP BY category
ORDER BY total_sales;;
```
- Sales Trend Per Month
```sql
SELECT 
	DATE_FORMAT(orderdate, '%Y-%m') AS month,
    SUM(Sales)
    FROM datasta.retail_sales
 GROUP BY date_format(orderdate, '%Y-%m')
 ORDER BY month;
```
- Top 5 Profitable Products
```sql
SELECT 
    SubCategory,
    SUM(Profit) AS total_profit
FROM datasta.retail_sales
GROUP BY SubCategory
ORDER BY total_profit DESC
LIMIT 5;
```
- Discount Impact on Profit
```sql
SELECT 
    Discount,
    AVG(Profit) AS avg_profit
FROM datasta.retail_sales
GROUP BY Discount
ORDER BY Discount;
```
- Revenue and Profit
```sql
SELECT 
    DATE_FORMAT(OrderDate, '%Y-%m') AS month,
    SUM(Sales) AS sales,
    SUM(Profit) AS profit
FROM datasta.retail_sales
GROUP BY month
ORDER BY month;ER BY Discount;
```
- Sales and Profit by Category
```sql
SELECT 
    DATE_FORMAT(OrderDate, '%Y-%m') AS month,
    SUM(Sales) AS sales,
    SUM(Profit) AS profit
FROM datasta.retail_sales
GROUP BY month
ORDER BY month;ER BY Discount;
```

### Power BI Dashboard
The Power BI  dashboard includes the following visuals:
* KPIs
* Top Product Sales
* Category Sales
* Monthly Revenue
* Category Profit
* Regional Sales
* Discount Distribution
* Interactive filters for date, product and region comparison
<img width="1256" height="681" alt="E-Commerce Retail Dashbaord" src="https://github.com/user-attachments/assets/5d5c936c-9b7e-423e-b7d9-89c70aa175f6" />

### Key Metrics
- Total Sales: £60.7M
- Total Profit: £4.56M
- Profit Margin: 7.5%
- Total Orders: 60,000
- Average Order Value: £1,013

### Key Insights
1. Sales are relatively evenly distributed across categories, with Furniture slightly leading.
2. Profit margins remain moderate, indicating potential opportunities for cost optimization.
3. Monthly revenue shows noticeable fluctuations, suggesting seasonality in customer demand.
4. Top-performing products such as
 > Storage, Tables, and Chairs consistently drive revenue.
5. Regional sales distribution is balanced, meaning no single region dominates the market.
6. Higher discounts do not always correlate with higher sales, indicating inefficiencies in discount strategies.

###  Recommendations
* Optimize discount strategies to improve profitability.
* Focus marketing efforts during peak-performing months to maximize revenue.
* Increase investment in top-performing product categories.
* Investigate cost structures to improve overall profit margin.

Dataset Source
<img width="1584" height="818" alt="Data Preview" src="https://github.com/user-attachments/assets/6ee2b418-00c7-4244-a749-2704bedc52cb" />


[Download Here](https://drive.google.com/file/d/15bWJj_wltCqsd-BDSzHba9jRDvQVHXOw/view?usp=sharing) 



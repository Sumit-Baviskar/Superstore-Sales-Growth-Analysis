# Superstore-Sales-Dataset (SQL+Power BI)


# Dataset Overview

The dataset provided originates from a survey conducted in 2014 within the technology sector, aiming to assess attitudes towards mental health and the prevalence of mental health disorders in the workplace. It offers a valuable insight into the mental health landscape within the tech industry, shedding light on perceptions, experiences, and responses related to mental well-being among employees



# Tools Used

SQL (Data expolration and manipulation)
Power BI (Data visualization)

# Business Problem Statement:

**1.Overview of Superstore Sales Dataset:**

A) Total number of orders


B) Total sales


C) Average profit

**2.Sales Performance Analysis:**

Identify top-selling products and categories.


Analyze sales trends and highlight significant patterns over the years

**3.Customer Segmentation:**


Segment customers based on purchasing behavior.


Understand which segments contribute most to sales

**4.Shipping and Order Management:**


Evaluate efficiency of different shipping modes.


Analyze shipping costs and their impact on overall profitability.


Assess order processing times and identify areas for improvement

**5.Profitability and Cost Analysis:**


Analyze profit margins for different product categories and sub-categories.


Evaluate the impact of discounts on overall profitability.


Identify products or regions requiring cost optimization.



**6.Global Sales/Product Quantity Overview:**


Analyze distribution of sales across different countries.


**7.State-Level Category Exploration:**


Understand most-used product categories in different states.



**8.Regional Sub-Category Analysis:**


Analyze popularity of sub-categories in different regions.



# Dataset Columns:

**order_id:** IDs of all orders


**order_date:** Dates for all orders


**ship_date:** Shipping date of all orders


**ship_mode:** Shipping mode of all orders


**customer_name:** Customer names of all order IDs


**segment:** Segment of all orders


**state:** State of the order ID


**country:** Country of the order ID


**market:** Market of the order ID


**region:** Region of the order ID


**product_id:** Product ID of all orders


**category:** Category of the orders


**sub_category:** Sub-category of the orders


**product_name:** Product name of the orders


**sales:** Sales of the orders


**quantity:** Quantity of the orders


**discount:** Discount of the orders


**profit:** Profit of the orders


**shipping_cost:** Shipping cost of the orders


**order_priority:** Order priority of the orders


**year:** Year of the orders


-- Overall view of superstore sales dataset --
SELECT
COUNT(order_id) AS Total_oreders,
COUNT(DISTINCT country) AS Total_countries,
COUNT(DISTINCT product_name) AS Total_products,
COUNT(DISTINCT category) AS Total_categories,
COUNT(DISTINCT sub_category) AS Total_subcategories,
COUNT(DISTINCT year) AS Total_years,
SUM(sales) AS Total_sales,
SUM(quantity) AS Total_quantity_sold,
AVG(profit) AS Avg_profit,
AVG(discount) AS Total_discount
FROM store;

-- sales performance analysis --
SELECT product_name,SUM(sales) AS Toatl_sales,SUM(quantity) AS Total_quantity_sold 
FROM store
GROUP BY product_name,category
ORDER BY SUM(sales) DESC
LIMIT 10;

-- total sales per year  --
SELECT  year, SUM(sales) AS Total_sales FROM Store
GROUP BY year
ORDER BY SUM(sales) DESC;

-- customer segmentation --
SELECT segment, COUNT(DISTINCT customer_name) AS Toatl_customers,SUM(sales) AS Total_sales
FROM store
GROUP BY segment
ORDER BY SUM(sales) DESC;

-- RECENT Shipping and order management --
SELECT ship_mode, AVG(shipping_cost) AS Avg_shipping_cost, AVG(profit) AS Avg_profit
FROM store
GROUP BY ship_mode
ORDER BY AVG(profit) DESC;

-- time analysis for order orderes and order received --
SELECT ship_mode, AVG(DATEDIFF(DAY, CAST(order_date AS DATE),CAST(ship_date AS DATE))) AS Avg_time_gape
FROM store
GROUP BY ship_mode;

-- profitability and cost analysis --
SELECT product_name,category,sub_category,AVG(profit) AS Avg_profit,AVG(discount) AS Avg_dicount
FROM store
GROUP BY product_name,category,sub_category
ORDER BY AVG(profit) DESC;

-- Global values for sales and quantity product  --
SELECT country,SUM(sales) AS Total_sales,SUM(quantity)  AS Total_quantity
FROM store
GROUP BY country
ORDER BY SUM(sales) DESC;


-- state level category exploration --
SELECT  product_name,category,SUM(quantity) AS Total_quantity_sold
FROM store
GROUP BY product_name,category
ORDER BY SUM(quantity) DESC;

-- Regional subcategory analysis --
SELECT region,sub_category,SUM(quantity) AS Total_quantity_sold
FROM store
GROUP BY region,sub_category
ORDER BY SUM(quantity) DESC



# Dashboard

![Super_store](https://github.com/Sumit-Baviskar/Mental-Health-Power-BI-/assets/153518735/95dadd55-7962-42a7-88e7-afb86e52abea)


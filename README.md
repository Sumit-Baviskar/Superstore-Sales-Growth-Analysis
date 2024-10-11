# :chart_with_upwards_trend: **Superstore-Sales-Dataset (SQL + Power BI)** :chart_with_upwards_trend:


# :green_book: **Dataset Overview :** :green_book:

The dataset provided originates from a survey conducted in 2014 within the technology sector, aiming to assess attitudes towards mental health and the prevalence of mental health disorders in the workplace. It offers a valuable insight into the mental health landscape within the tech industry, shedding light on perceptions, experiences, and responses related to mental well-being among employees



# :green_book:  **Tools Used :** :green_book:

 - **SQL (Data expolration and manipulation)**

 - **Power BI (Data visualization)**


# :green_book:  Business Problem Statement:  :green_book:


**1. Overview of Superstore Sales Dataset :**

 -  A) Total number of orders


 - B) Total sales


 - C) Average profit


**2. Sales Performance Analysis :**

 - Analyze sales trends and highlight significant patterns over the years


**3. Customer Segmentation :**

 - Segment customers based on purchasing behavior.


 - Understand which segments contribute most to sales


**4. Shipping and Order Management :**


 - Evaluate efficiency of different shipping modes.


 - Analyze shipping costs and their impact on overall profitability.


 - Assess order processing times and identify areas for improvement


**5.Profitability and Cost Analysis :**


 - Analyze profit margins for different product categories and sub-categories.


 - Evaluate the impact of discounts on overall profitability.


 - Identify products or regions requiring cost optimization.



**6. Global Sales/Product Quantity Overview :**


 - Analyze distribution of sales across different countries.



**7. Orders And Time Analysis Overview :**


 -  time analysis for order  and order received 


**8. State-Level Category Exploration :**


 - Understand most-used product categories in different states.



**9.Regional Sub-Category Analysis :**


 - Analyze popularity of sub-categories in different regions.



**10. One Month Prediction of Sales and Profit :** (Only in Power BI)

  - Segment customers based on purchasing behavior.


# :green_book: Dataset Columns: :green_book:


 - **order_id:** IDs of all orders


 - **order_date:** Dates for all orders


 - **ship_date:** Shipping date of all orders


 - **ship_mode:** Shipping mode of all orders


 - **customer_name:** Customer names of all order IDs


 - **segment:** Segment of all orders


 - **state:** State of the order ID


 - **country:** Country of the order ID


 - **market:** Market of the order ID


 - **region:** Region of the order ID


 - **product_id:** Product ID of all orders


 - **category:** Category of the orders


 - **sub_category:** Sub-category of the orders


 - **product_name:** Product name of the orders


 - **sales:** Sales of the orders


 - **quantity:** Quantity of the orders


 - **discount:** Discount of the orders


 - **profit:** Profit of the orders


 - **shipping_cost:** Shipping cost of the orders


 - **order_priority:** Order priority of the orders


 - **year:** Year of the orders



# :green_book:  **Business Solution :**  :green_book:



**1. Overview of Superstore Sales Dataset :**

 -  A) Total number of orders


 - B) Total sales


 - C) Average profit


**Solution :**


**SQL Code :**

    SELECT product_name,SUM(sales) AS Total_sales, AVERAGE(profit) AS Average_profit , COUNT(DISTINCT Order ID) AS Total_Orders
    FROM store
    GROUP BY product_name,category
    ORDER BY SUM(sales) DESC;

---------------------------------------------------------------------------------------------------------------------------------

**2. Sales Performance Analysis :**


 - Analyze sales trends and highlight significant patterns over the years



**Solution :**



**SQL Code :**

    SELECT  year, SUM(sales) AS Total_sales FROM Store
    GROUP BY year
    ORDER BY SUM(sales) DESC;


---------------------------------------------------------------------------------------------------------------------------------


**3. Customer Segmentation :**

 - Segment customers based on purchasing behavior.

 - Understand which segments contribute most to sales



**Solution :**



**SQL Code :**

    SELECT segment, COUNT(DISTINCT customer_name) AS Total_customers,SUM(sales) AS Total_sales
    FROM store
    GROUP BY segment
    ORDER BY SUM(sales) DESC;


---------------------------------------------------------------------------------------------------------------------------------


**4. Shipping and Order Management :**


 - Evaluate efficiency of different shipping modes.


 - Analyze shipping costs and their impact on overall profitability.



**Solution :**

   

**SQL Code :**

    SELECT ship_mode, AVG(shipping_cost) AS Avg_shipping_cost, AVG(profit) AS Avg_profit
    FROM store
    GROUP BY ship_mode
    ORDER BY AVG(profit) DESC;


---------------------------------------------------------------------------------------------------------------------------------


**5.Profitability and Cost Analysis :**


 - Analyze profit margins for different product categories and sub-categories.


 - Evaluate the impact of discounts on overall profitability.


 - Identify products or regions requiring cost optimization.



**Solution :**



**SQL Code :**   

    SELECT product_name,category,sub_category,AVG(profit) AS Avg_profit,AVG(discount) AS Avg_dicount
    FROM store
    GROUP BY product_name,category,sub_category
    ORDER BY AVG(profit) DESC;


---------------------------------------------------------------------------------------------------------------------------------


**6. Global Sales/Product Quantity Overview :**


 - Analyze distribution of sales across different countries.

 - Global values for sales and quantity product


**Solution :**



**SQL Code :**   

    SELECT country,SUM(sales) AS Total_sales,SUM(quantity)  AS Total_quantity
    FROM store
    GROUP BY country
    ORDER BY SUM(sales) DESC;


---------------------------------------------------------------------------------------------------------------------------------


**7. Orders And Time Analysis Overview :**

 -  time analysis for order  and order received



**Solution :**



**SQL Code :**   

    SELECT ship_mode, AVG(DATEDIFF(DAY, CAST(order_date AS DATE),CAST(ship_date AS DATE))) AS Avg_time_gap
    FROM store
    GROUP BY ship_mode;

---------------------------------------------------------------------------------------------------------------------------------


**8. State-Level Category Exploration :**


 - Understand most-used product categories in different states.



**Solution :**



**SQL Code :**   

    SELECT  product_name,category,SUM(quantity) AS Total_quantity_sold
    FROM store
    GROUP BY state,category
    ORDER BY SUM(quantity) DESC;

---------------------------------------------------------------------------------------------------------------------------------


**9.Regional Sub-Category Analysis :**


 - Analyze popularity of sub-categories in different regions.



**Solution :**



**SQL Code :**   

    SELECT region,sub_category,SUM(quantity) AS Total_quantity_sold
    FROM store
    GROUP BY region,sub_category
    ORDER BY SUM(quantity) DESC



---------------------------------------------------------------------------------------------------------------------------------


**10. One Month Prediction of Sales and Profit :** (Only in Power BI)



**Solution :**







---------------------------------------------------------------------------------------------------------------------------------






# :key: **Dashboard :**

![superstore ](https://github.com/Sumit-Baviskar/SQl-Amazon-sales/assets/153518735/f560e20d-659f-435f-ae0d-c098e7dc84eb)



# :key: **Recommendation :**



# :key: **Conclusion :**



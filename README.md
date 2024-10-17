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


- **A) Total Number of Orders: 51K**

  - **Insight :** High volume of orders indicates strong market activity and customer engagement.
    
  - **Recommendation :** Continue expanding product lines to capitalize on customer demand and further increase order volume.

- **B) Total Sales: $13M**

  - **Insight :** Impressive total sales; however, it’s important to ensure profit margins are maintained despite large sales figures.

  - **Recommendation :** Focus on increasing sales from high-margin products, especially in top-performing countries and segments.

- **C) Average Profit: $28.64 per order**

  - **Insight :** Reasonable profit per order, but there’s room for improvement by optimizing costs (especially shipping and discounts).

  - **Recommendation :** Reduce costs by renegotiating supplier contracts or adjusting discount strategies to enhance profitability
---------------------------------------------------------------------------------------------------------------------------------

**2. Sales Performance Analysis :**


 - Analyze sales trends and highlight significant patterns over the years



**Solution :**



**SQL Code :**

    SELECT  year, SUM(sales) AS Total_sales FROM Store
    GROUP BY year
    ORDER BY SUM(sales) DESC;

**Sales Performance Analysis**

- **Insight :** Sales have grown consistently, with a significant spike in 2014 reaching $4.3M. This shows that the business is scaling well.

- **Recommendation :**


  - Invest more in marketing during peak sales periods to maximize growth opportunities.


  - Analyze the factors that contributed to the sales increase in 2014 and replicate successful strategies in future years


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

**Customer Segmentation**

- **Insight :** The Consumer segment dominates the market, contributing 27K customers, followed by Corporate (15K) and Home Office (9K).

- **Recommendation :**

  - Implement targeted promotions for the Consumer segment to sustain their loyalty and spending.

  - Explore new strategies to engage the Corporate and Home Office segments, as they could be further optimized for higher sales

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

**Shipping and Order Management :**

- **A) Shipping Efficiency :**
  
  - **Insight :** Same Day shipping incurs the highest cost but results in faster delivery, while Standard Class is the most cost-effective but slower.

  - **Recommendation :** Encourage customers to choose Standard Class shipping by offering incentives, such as free shipping for orders above a certain amount.


- **B) Shipping Costs and Profitability Impact :**

  - **Insight :** High shipping costs reduce overall profitability, especially with Same Day and First-Class shipping.


 - **Recommendation :** Optimize shipping routes or partner with more cost-effective logistics providers to lower shipping expenses.

   
- **C) Order Processing Time :**
  - **Insight :** Delays are notable in Second Class shipping, with an average of 3.23 days for delivery, which can impact customer satisfaction.
  
  - **Recommendation :** Implement automation and streamline order processing workflows to reduce delays and improve delivery times

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
    
**Profitability and Cost Analysis**

- **A) Profit Margins by Category:**
 
  - **Insight :** Technology has the highest sales ($4.7M) and strong profit margins, followed by Furniture ($4.1M) and Office Supplies ($3.8M).
 

  - **Recommendation :** Promote high-margin products like Technology, and consider discontinuing or optimizing low-margin sub-categories.

   
- **B) Discounts Impact on Profitability:**
 
  - **Insight :** The Office Supplies category sees a high amount of discounting ($3.8M), which negatively impacts profitability.
 
  - **Recommendation :** Reduce the frequency or percentage of discounts on Office Supplies to improve profit margins without losing customers.

- **C) Cost Optimization Opportunities:**
 
  - **Insight :** Regions like the U.S. and Australia show high sales but also relatively high costs.
 
  - **Recommendation :** Reevaluate logistics and supplier relationships in these regions to identify areas for cost-saving

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


**Global Sales/Product Quantity Overview**
 
 - **Insight :** The United States dominates sales, followed by countries like Australia, France, and China. These top countries generate the most revenue.
 
 - **Recommendation :** Focus expansion efforts on underperforming countries like Brazil and India by analyzing local market demands and tailoring products or promotions accordingly

---------------------------------------------------------------------------------------------------------------------------------


**7. Orders And Time Analysis Overview :**

 -  time analysis for order  and order received



**Solution :**



**SQL Code :**   

    SELECT ship_mode, AVG(DATEDIFF(DAY, CAST(order_date AS DATE),CAST(ship_date AS DATE))) AS Avg_time_gap
    FROM store
    GROUP BY ship_mode;


**Orders and Time Analysis Overview**
 
 - **Insight :** Orders processed through Same Day shipping are delivered very quickly (average of 0.04 days), while Standard Class takes 5 days.


 - **Recommendation :** Implement a middle-ground shipping option that balances speed and cost to appeal to a broader customer base who need fast but affordable shipping
---------------------------------------------------------------------------------------------------------------------------------


**8. State-Level Category Exploration :**


 - Understand most-used product categories in different states.



**Solution :**



**SQL Code :**   

    SELECT  product_name,category,SUM(quantity) AS Total_quantity_sold
    FROM store
    GROUP BY state,category
    ORDER BY SUM(quantity) DESC;


**State-Level Category Exploration :**

 - **Insight :** California leads in sales by category, followed by England, New York, and Texas. Technology and Furniture are popular in high-sales states.

 - **Recommendation :** Expand product offerings and marketing campaigns tailored to popular categories (e.g., Technology and Furniture) in high-sales states. Additionally, investigate underperforming states to address unmet demands

---------------------------------------------------------------------------------------------------------------------------------


**9.Regional Sub-Category Analysis :**


 - Analyze popularity of sub-categories in different regions.



**Solution :**



**SQL Code :**   

    SELECT region,sub_category,SUM(quantity) AS Total_quantity_sold
    FROM store
    GROUP BY region,sub_category
    ORDER BY SUM(quantity) DESC

**Regional Sub-Category Analysis :**

 - **Insight :** The Central region has strong sales in all categories, particularly in Office Supplies and Furniture. The West and North regions also perform well but with varying sub-category preferences.


 - **Recommendation :** Customize marketing and product recommendations for each region to cater to sub-category preferences. For example, promote Office Supplies in the Central region and Furniture in the North

---------------------------------------------------------------------------------------------------------------------------------


**10. One Month Prediction of Sales and Profit :** (Only in Power BI)



**Solution :**

**One-Month Prediction of Sales and Profit**
 - **Insight :** The prediction model shows a consistent sales trend with minor fluctuations. The profit projection is also stable.

 - **Recommendation :** Based on the predictive trends, prepare inventory and promotional strategies in advance to meet the expected demand, ensuring minimal stockouts or oversupply.






---------------------------------------------------------------------------------------------------------------------------------






# :key: **Dashboard :**

![superstore ](https://github.com/Sumit-Baviskar/SQl-Amazon-sales/assets/153518735/f560e20d-659f-435f-ae0d-c098e7dc84eb)



![Superafter](https://github.com/user-attachments/assets/8c027d1e-5b89-47f0-bdb4-d1f2fe490ffd)


# :key: **Recommendation :**

**1. Optimize Shipping and Order Processing :**

 - Improve shipping cost efficiency by encouraging the use of cost-effective modes like Standard Class through targeted incentives.

 - Streamline order processing to reduce delays in delivery, especially for slower modes like Second Class, which affects customer satisfaction.

**2. Revise Discounting Strategies :**

 - Reduce the frequency and magnitude of discounts in categories like Office Supplies, which are negatively affecting profitability.

 - Focus discounts on high-margin categories such as Technology to maintain healthy profit margins while incentivizing more purchases.

**3. Targeted Marketing and Product Expansion :**

 - Focus on underperforming regions and countries like Brazil and India by analyzing local market demands and customizing product offerings or promotional strategies to drive growth.

 - Leverage customer segmentation insights by targeting high-value segments, such as the Consumer segment, with tailored promotions to maximize sales.

**4. Boost High-Margin Product Sales :**

 - Prioritize promoting high-margin products like Technology, which consistently contribute to revenue growth and profitability.

 - Consider expanding the Technology product line in high-sales regions to capture more market share.

**5. Invest in Data-Driven Decision Making :**

 - Utilize predictive analytics (e.g., one-month sales and profit prediction) to forecast demand accurately, manage inventory, and prepare for fluctuations in customer orders.

 - Focus inventory and supply chain strategies on projected sales trends to minimize stockouts and maximize revenue during peak periods.


# :key: **Conclusion :**

The Superstore Sales Dashboard analysis provides a clear picture of current performance across sales, customer segmentation, shipping, profitability, and regional distribution. While overall sales are strong, with a significant spike in growth and healthy customer engagement, there are opportunities to enhance profitability through shipping cost reductions, discount management, and targeted marketing.


By refining shipping strategies, adjusting discounting, and promoting high-margin products in top-performing regions, the company can further improve its profitability and sustain long-term growth. Predictive analytics should also be leveraged to align inventory and promotional strategies with future demand, ensuring the company remains competitive in an evolving market.


Focusing on these recommendations will not only help optimize operational efficiency but also improve customer satisfaction and strengthen the company’s position in both domestic and global markets.




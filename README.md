🍕 # **Pizza_Sales_Report_Using_MySQL**

---

📌 **Project Overview**

This project focuses on analyzing pizza sales data using MySQL. The goal is to extract business insights from raw sales transactions by writing SQL queries to calculate KPIs, explore sales trends, and identify best- and worst-performing pizzas.  
The analysis provides restaurant managers and stakeholders with valuable information for improving decision-making, optimizing sales strategies, and understanding customer preferences.

---
❓ **Problem Statement**  
Pizza outlets generate large amounts of transactional data daily. However, this raw data often remains underutilized. Managers struggle to answer important business questions such as:  
What is the total revenue and average order value?  
Which pizza category or size is most popular?  
What are the peak sales hours and weekly trends?  
Which pizzas generate the highest and lowest revenue?  
By leveraging SQL, this project converts raw order data into actionable insights.  

---
🎯 **KPIs**
The following Key Performance Indicators (KPIs) were calculated:  
Total Revenue → Sum of all sales (SUM(total_price))  
Average Order Value (AOV) → Total revenue ÷ total orders  
Total Pizzas Sold → Sum of all quantities ordered  
Total Orders → Count of distinct orders  
Average Pizzas per Order → Total pizzas sold ÷ total orders  

---
🧾**SQL Analysis**

1️⃣ Total number of orders placed  
SELECT COUNT(DISTINCT order_id) AS total_orders  
FROM pizza_sales;

---

2️⃣ Total revenue generated from pizza sales  
SELECT SUM(total_price) AS total_revenue  
FROM pizza_sales;

---

3️⃣ Identify the highest-priced pizza  
SELECT pizza_name, MAX(total_price) AS highest_price  
FROM pizza_sales;

---

4️⃣ Identify the most common pizza size ordered  
SELECT pizza_size, COUNT(pizza_size) AS size_count  
FROM pizza_sales  
GROUP BY pizza_size  
ORDER BY size_count DESC  
LIMIT 1;  

---

5️⃣ Top 5 most ordered pizza types with quantities  
SELECT pizza_name, SUM(quantity) AS total_quantity  
FROM pizza_sales  
GROUP BY pizza_name  
ORDER BY total_quantity DESC  
LIMIT 5;  

---

6️⃣ Total quantity of each pizza category ordered  
SELECT pizza_category, SUM(quantity) AS total_quantity  
FROM pizza_sales  
GROUP BY pizza_category;  

---

7️⃣ Distribution of orders by hour of the day  
SELECT HOUR(order_time) AS order_hour,  
       COUNT(DISTINCT order_id) AS total_orders  
FROM pizza_sales  
GROUP BY HOUR(order_time)  
ORDER BY order_hour;  

---

8️⃣ Category-wise distribution of pizzas  
SELECT pizza_category, COUNT(pizza_name) AS pizza_count  
FROM pizza_sales  
GROUP BY pizza_category;  

---

9️⃣ Average number of pizzas ordered per day  
SELECT ROUND(SUM(quantity) / COUNT(DISTINCT order_date), 2) AS avg_pizzas_per_day  
FROM pizza_sales;  

---

🔟 Top 3 most ordered pizza types by revenue  
SELECT pizza_name, SUM(total_price) AS revenue  
FROM pizza_sales  
GROUP BY pizza_name  
ORDER BY revenue DESC  
LIMIT 3;  

---
💡 **Key Insights**  
Evening hours showed the highest pizza sales volume.  
Medium-sized pizzas contributed the most to total sales.  
Classic category pizzas were the most popular overall.  
A few premium pizzas generated high revenue despite lower order counts.  
The bottom 5 pizzas revealed underperforming products that could be reconsidered for the menu.  

---
🛠️ **Tools Used**  
MySQL Workbench 8.0.36 — SQL query execution & database analysis  

---
📝 **Conclusion**  
The Pizza Sales Analysis project demonstrated how SQL can be used to transform raw transactional data into meaningful business insights. By calculating KPIs, exploring sales patterns, and identifying best- and worst-performing pizzas, we gained a deeper understanding of customer preferences and operational performance.  

---
**Key takeaways:**  
Revenue and order trends help in planning resources and promotions.  
Medium and classic pizzas dominated customer preferences.  
Peak sales hours provide insights for staffing and inventory optimization.  
Identifying low-performing pizzas helps refine the menu and reduce waste.  

Overall, this project highlights the importance of data-driven decision making in the food and beverage industry.  

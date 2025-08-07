# 🍕 Pizza Sales Data Analysis using SQL
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/67f0e91a-2f2a-4d1e-91d8-8d23ca73e5b0" />



## 📊 Overview

This project presents a complete analysis of a pizza sales dataset using SQL. The goal is to derive actionable business insights from sales transactions. The analysis explores order trends, revenue contributions, and popular pizza preferences, helping stakeholders understand customer behavior and optimize operations.

---

## 🎯 Objectives

- Analyze total sales and order volumes across the dataset.
- Examine pizza pricing and identify the most and least expensive items.
- Analyze sales trends by pizza size, type, category, and time.
- Calculate revenue and determine high-performing products.
- Explore cumulative and average performance metrics over time.
- Derive percentage contributions by category and revenue-based rankings.

---

## 🧩 Business Questions Answered

1. **Query the Total Number of Orders Placed**  
  ```sql
   SELECT COUNT(order_id) TOTAL_ORDERS_PLACED FROM pizza_orders;

  ```
2. **Query the Total Number of Pizza ID Types**  
  ```sql
    SELECT  COUNT(pizza_type_id) TOTAL_PIZZA_IDTYPE FROM pizza_types;
  ```

3. **Query the Total Number of Pizza Types**  

    ```sql
     SELECT COUNT(pizza_id) TOTAL_PIZZA_ID_Types FROM PIZZAS;
    ```

4. **Query Total Order Quantity Placed**  
     ```sql
      SELECT SUM(quantity) as Total_Qrder_Qty FROM pizza_order_details;
    ```

5. **Query the First Date of Transaction and Last Date of Transaction**  
     ```sql
     SELECT MIN(date) FIRST_TRANSACTION, MAX(date) LAST_TRANSACTION FROM pizza_orders;
    ```

6. **Query the Total Revenue Generated**  
     ```sql
     SELECT SUM(price*quantity) as revenue FROM pizzas p JOIN pizza_order_details po ON 
      p.pizza_id=po.pizza_id;
    ```

7. **Query the Highest Priced Pizza**  
     ```sql
     SELECT name, price FROM pizzas p RIGHT JOIN pizza_types pt ON pt.pizza_type_id = p.pizza_type_id
     ORDER BY price DESC LIMIT 1;
    ```

8. **Query the Lowest Priced Pizza**  
     ```sql
      SELECT name, price FROM pizzas p RIGHT JOIN pizza_types pt ON pt.pizza_type_id = p.pizza_type_id
      ORDER BY price LIMIT 1;
    ```

9. **Query the Pizza Ordered Quantity by Size**  
     ```sql
      SELECT size,SUM(quantity) TOTAL_QTY FROM pizzas A JOIN pizza_order_details B ON A.pizza_id=B.pizza_id
      GROUP BY size;
    ```

10. **Query the Pizza Ordered Quantity by Category**  
      ```sql
      SELECT category,SUM(quantity) TOTAL_QTY FROM pizza_types A JOIN pizzas B ON A.pizza_type_id=B.pizza_type_id
      JOIN pizza_order_details C ON C.pizza_id=B.pizza_id
      GROUP BY category;
    ```

11. **Query the Pizza Ordered Quantity by Pizza Name**  
      ```sql
       SELECT name,SUM(quantity) AS TOTAL_QTY FROM pizza_types A JOIN pizzas B ON A.pizza_type_id=B.pizza_type_id
       JOIN pizza_order_details C ON C.pizza_id=B.pizza_id
       GROUP BY name;
      ```

12. **Query the Top 7 Types Based on Orders Quantity**  
       ```sql
       SELECT * FROM (
       SELECT *,RANK() OVER(Order by TOTAL_QTY DESC ) AS Rnk FROM (
       SELECT A.pizza_type_id as TYPE,SUM(quantity) AS TOTAL_QTY FROM pizza_types A JOIN pizzas B ON A.pizza_type_id=B.pizza_type_id
       JOIN pizza_order_details C ON C.pizza_id=B.pizza_id
       GROUP BY A.pizza_type_id)A)B
       WHERE Rnk<=7;
       ```

13. **Query the Distribution of Orders by Hour of Day**  
       ```sql
        SELECT HOUR(A.TIME) AS HOUR, SUM(B.QUANTITY) AS TTL_DISTRIBUTED_QTY
      FROM PIZZA_ORDERS A JOIN PIZZA_ORDER_DETAILS B
      ON A.ORDER_ID=B.ORDER_ID GROUP BY HOUR
      ORDER BY TTL_DISTRIBUTED_QTY DESC;
       ```

14. **Query the Pizza Order Quantity by Date and Calculate the Average Number of Pizzas Ordered per Day**  
       ```sql
       SELECT AVG(TOTAL) FROM(
      SELECT date,SUM(quantity)AS TOTAL FROM pizza_orders A JOIN pizza_order_details B ON A.order_id=B.order_id
       GROUP BY date)A;
       ```

15. **Query the Top 7 Pizza Names by Revenue**  
 ```sql
       SELECT * FROM(
      SELECT *,Rank() OVER(Order by revenue DESC) as Rnk FROM(
      SELECT Name,SUM(price * quantity) as revenue,SUM(quantity) FROM pizza_types A JOIN pizzas B
      ON A.pizza_type_id=B.pizza_type_id JOIN pizza_order_details C ON C.pizza_id= B.pizza_id
     GROUP BY Name)A)B
      Where Rnk<=7;
  
 ```

17. **Query the Percentage Contribution of Each Pizza Category to Total Revenue**  
      ```sql
      SELECT category,ROUND(SUM(price*quantity)/
      (SELECT SUM(price*quantity) FROM pizzas A JOIN pizza_order_details B ON  A.pizza_id=B.pizza_id)*100,2)
      REVENUE_PCT  FROM pizza_types A JOIN pizzas B ON 
       A.pizza_type_id=B.pizza_type_id JOIN pizza_order_details C ON C.pizza_id=B.pizza_id
       GROUP BY category;
     ```

18. **Analyze the Cumulative Revenue Generated Over Time**  
      ```sql
      SELECT 
      A.date,SUM(B.quantity * C.price) AS daily_revenue,
      SUM(SUM(B.quantity * C.price)) OVER (ORDER BY A.date) AS cumulative_revenue
      FROM pizza_orders A
       JOIN pizza_order_details B ON A.order_id = B.order_id
      JOIN pizzas C ON B.pizza_id = C.pizza_id
      GROUP BY A.date
      ORDER BY A.date;
      
     ```

19. **Determine the Top 3 Most Ordered Pizza Types Based on Revenue for Each Category**  
      ```sql
        SELECT * FROM (
       SELECT *, RANK() OVER (PARTITION BY category ORDER BY revenue DESC) AS rnk FROM (
        SELECT a.pizza_type_id AS pizza_type, category, SUM(price * quantity) AS revenue 
        FROM pizza_types a 
        JOIN pizzas b ON a.pizza_type_id = b.pizza_type_id
        JOIN pizza_order_details c ON c.pizza_id = b.pizza_id
        GROUP BY a.pizza_type_id, category
          ) a
        ) b
    WHERE rnk <= 3;
```

---

## 📌 Key Insights

- **Order Volume & Revenue**: High order frequency is concentrated around weekends and dinner hours.
- **Popular Sizes**: Medium and Large pizzas dominate the market.
- **Top Categories**: “Classic” and “Supreme” categories contribute the highest revenue.
- **Best Performers**: A few pizza types account for a significant portion of total revenue and orders.
- **Time Trends**: There’s steady growth in cumulative revenue, indicating increased customer retention or marketing effectiveness.
- **Revenue Optimization**: Focusing on top contributors and optimizing low-performing items can yield better margins.

---

## 📈 Conclusion

The SQL-based pizza sales analysis enables a holistic view of customer preferences, operational strengths, and revenue patterns. These insights can be leveraged for:

- Menu Engineering  
- Inventory Planning  
- Targeted Promotions  
- Sales Forecasting  
- Strategic Business Decisions

This approach not only ensures data-backed operations but also improves customer satisfaction by aligning product offerings with demand.




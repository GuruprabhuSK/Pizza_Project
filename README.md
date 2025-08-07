# 🍕 Pizza Sales Data Analysis using SQL

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
    ```

4. **Query Total Order Quantity Placed**  
     ```sql
    ```

5. **Query the First Date of Transaction and Last Date of Transaction**  
     ```sql
    ```

6. **Query the Total Revenue Generated**  
     ```sql
    ```

7. **Query the Highest Priced Pizza**  
     ```sql
    ```

8. **Query the Lowest Priced Pizza**  
     ```sql
    ```

9. **Query the Pizza Ordered Quantity by Size**  
     ```sql
    ```

10. **Query the Pizza Ordered Quantity by Category**  
      ```sql
    ```

11. **Query the Pizza Ordered Quantity by Pizza Name**  
      ```sql
      ```

12. **Query the Top 7 Types Based on Orders Quantity**  
       ```sql
       ```

13. **Query the Distribution of Orders by Hour of Day**  
       ```sql
       ```

14. **Query the Pizza Order Quantity by Date and Calculate the Average Number of Pizzas Ordered per Day**  
       ```sql
       ```

15. **Query the Top 7 Pizza Names by Revenue**  
        ```sql
        ```

16. **Query the Percentage Contribution of Each Pizza Category to Total Revenue**  
      ```sql
        ```

17. **Analyze the Cumulative Revenue Generated Over Time**  
      ```sql
        ```

18. **Determine the Top 3 Most Ordered Pizza Types Based on Revenue for Each Category**  
      ```sql
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




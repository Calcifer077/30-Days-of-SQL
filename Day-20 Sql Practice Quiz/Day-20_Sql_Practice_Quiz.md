📘 30 Days Of SQL: Day 20 - Advanced SQL Practice and Quiz

Welcome to Day 20 of the 30 Days of SQL challenge! 🎉 Today is all about applying what you’ve learned so far through practice and a quiz to test your skills. Let’s sharpen your SQL abilities with real-world scenarios!

---

### Table of Contents

- [🔍 Overview](#-overview)
- [🧑‍💻 Practice Scenarios](#-practice-scenarios)
  1. [Aggregates and Joins](#1-aggregates-and-joins)
  2. [CTEs and Window Functions](#2-ctes-and-window-functions)
  3. [Subqueries and Set Operations](#3-subqueries-and-set-operations)
- [🎯 Quiz - Day 20](#-quiz---day-20)
- [📝 Day 20 Summary](#-day-20-summary)

---

### 🔍 Overview

Today’s session will reinforce your understanding of key SQL concepts, including:

- Aggregate functions and joins.
- Common Table Expressions (CTEs).
- Window functions and their applications.
- Subqueries and set operations.

You’ll also attempt a quiz to assess your grasp on these advanced topics.

---

### 🧑‍💻 Practice Scenarios

#### 1. Aggregates and Joins

Write a query to calculate the total sales revenue for each product category in the last year, including the category name and total revenue. Use joins and aggregate functions.

**Hint:** You’ll need to join the `products` table with the `sales` table and group by the category.

```sql
SELECT p.category_name, SUM(s.amount) AS total_revenue
FROM products p
JOIN sales s ON p.product_id = s.product_id
WHERE s.sale_date >= '2024-01-01'
GROUP BY p.category_name
ORDER BY total_revenue DESC;
```

#### 2. CTEs and Window Functions

Use a CTE to create a temporary result set of customers who made purchases in the last month. Then, use a window function to rank these customers by total spend.

**Hint:** Combine CTEs and `RANK()`.

```sql
WITH RecentPurchases AS (
    SELECT customer_id, SUM(amount) AS total_spent
    FROM sales
    WHERE sale_date >= '2024-12-01'
    GROUP BY customer_id
)
SELECT customer_id, total_spent,
       RANK() OVER (ORDER BY total_spent DESC) AS rank
FROM RecentPurchases;
```

#### 3. Subqueries and Set Operations

Find customers who purchased from both the `electronics` and `furniture` categories.

**Hint:** Use `INTERSECT` between two subqueries.

```sql
SELECT customer_id
FROM sales
WHERE product_id IN (
    SELECT product_id
    FROM products
    WHERE category_name = 'electronics'
)
INTERSECT
SELECT customer_id
FROM sales
WHERE product_id IN (
    SELECT product_id
    FROM products
    WHERE category_name = 'furniture'
);
```

---

### 🎯 Quiz - Day 20

#### 1. Multiple Choice

1. Which SQL clause is used to define a CTE?
   - a) SELECT
   - b) WITH
   - c) AS
   - d) CREATE

2. What does the `ROW_NUMBER()` function do?
   - a) Counts the number of rows in a table.
   - b) Assigns a unique sequential number to rows within a partition.
   - c) Sorts rows in descending order.
   - d) Removes duplicate rows from a result set.

#### 2. Query Challenges

1. Write a query using a recursive CTE to calculate the factorial of 5.
2. Use a window function to find the second-highest total sales amount in the `sales` table.
3. Combine multiple CTEs to identify top-performing products by region.

---

### 📝 Day 20 Summary

Today, you consolidated your SQL knowledge with practical exercises and quizzes. From advanced aggregates to recursive CTEs, you’ve explored scenarios that prepare you for real-world database challenges. Keep practicing, and get ready for Day 21, where we’ll cover Data Modeling and Normalization! 🚀

---

⬆️ Previous: [Day 19 - Transactions and Concurrency Control](../Day-19%20Transactions%20And%20Concurrency%20Control/Day-19_Transactions_And_Concurrency_Control.md)  
⬇️ Next: [Day 21 - Data Modeling and Normalization](../Day-21%20Data%20Modeling%20And%20Normalization/Day-21_Data_Modeling_And_Normalization.md)

---



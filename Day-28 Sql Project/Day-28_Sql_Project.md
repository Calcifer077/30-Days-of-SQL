# 30 Days Of SQL: Day 28 - Building a Real-World Project

Welcome to **Day 28** of the **30 Days of SQL** challenge! 🎉 Today, we’ll take a hands-on approach by applying everything you’ve learned to build a real-world SQL project. This is your chance to consolidate your knowledge, tackle practical challenges, and gain confidence in solving complex data problems.

---

## Project Overview

### Project Title: **Sales Analysis for an E-Commerce Platform**

You’ll design and execute SQL queries to analyze sales data for an online e-commerce company. The goal is to generate insights into sales trends, customer behavior, and product performance. These insights can help the company improve its decision-making process.

---

## Dataset Description

We’ll be working with the following tables:

### 1. **Customers**
| **Column**        | **Data Type** | **Description**                           |
|-------------------|---------------|-------------------------------------------|
| customer_id       | INT           | Unique identifier for each customer.      |
| first_name        | VARCHAR       | Customer's first name.                    |
| last_name         | VARCHAR       | Customer's last name.                     |
| email             | VARCHAR       | Customer's email address.                 |
| registration_date | DATE          | Date the customer registered.             |
| country           | VARCHAR       | Country of the customer.                  |

### 2. **Products**
| **Column**        | **Data Type** | **Description**                           |
|-------------------|---------------|-------------------------------------------|
| product_id        | INT           | Unique identifier for each product.       |
| product_name      | VARCHAR       | Name of the product.                      |
| category          | VARCHAR       | Category the product belongs to.          |
| price             | DECIMAL       | Price of the product.                     |
| stock_quantity    | INT           | Quantity of the product in stock.         |

### 3. **Orders**
| **Column**        | **Data Type** | **Description**                           |
|-------------------|---------------|-------------------------------------------|
| order_id          | INT           | Unique identifier for each order.         |
| customer_id       | INT           | ID of the customer who placed the order.  |
| order_date        | DATE          | Date the order was placed.                |
| total_amount      | DECIMAL       | Total amount of the order.                |

### 4. **Order_Details**
| **Column**        | **Data Type** | **Description**                           |
|-------------------|---------------|-------------------------------------------|
| order_detail_id   | INT           | Unique identifier for each order detail.  |
| order_id          | INT           | ID of the associated order.               |
| product_id        | INT           | ID of the product in the order.           |
| quantity          | INT           | Quantity of the product ordered.          |
| line_total        | DECIMAL       | Total price for this line (price x qty).  |

---

## Project Tasks

### 1. Basic Data Exploration
- View the first few rows of each table to understand the data.
- Check for any missing values or inconsistencies.

### 2. Analyze Customer Behavior
- Find the total number of customers and the number of customers by country.
- Identify the top 5 countries with the highest number of customers.
- Calculate the average number of orders per customer.

### 3. Product Performance Analysis
- List the top 10 best-selling products based on total quantity sold.
- Identify the top 5 product categories by revenue.
- Find products that are underperforming (low sales and high stock).

### 4. Sales Trends Analysis
- Calculate monthly sales revenue for the last year.
- Identify the month with the highest sales.
- Determine the average order value (AOV).

### 5. Advanced Insights
- Analyze repeat customers by identifying customers who placed more than 3 orders.
- Find the product-category combinations that generate the most revenue.
- Calculate the percentage contribution of each product to total revenue.

---

## SQL Queries

Here are some examples of queries you’ll write for this project:

### 1. View Data from a Table
```sql
SELECT *
FROM Customers
LIMIT 10;
```

### 2. Total Number of Customers
```sql
SELECT COUNT(*) AS total_customers
FROM Customers;
```

### 3. Best-Selling Products
```sql
SELECT p.product_name, SUM(od.quantity) AS total_quantity_sold
FROM Order_Details od
JOIN Products p ON od.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_quantity_sold DESC
LIMIT 10;
```

### 4. Monthly Sales Revenue
```sql
SELECT DATE_TRUNC('month', order_date) AS month, SUM(total_amount) AS monthly_revenue
FROM Orders
GROUP BY month
ORDER BY month;
```

### 5. Repeat Customers
```sql
SELECT c.customer_id, COUNT(o.order_id) AS order_count
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id
HAVING COUNT(o.order_id) > 3;
```

---

## Deliverables

1. **SQL Script**: A collection of all queries you write during the project.
2. **Analysis Report**: A short report summarizing your findings.
3. **Visualization** (Optional): Use tools like Tableau or Excel to create visualizations for key metrics.

---

## Hands-On Challenge

- Write SQL queries to answer the questions in the tasks above.
- Document your process and results.
- Share your insights and suggestions for improving the e-commerce platform’s performance.

---

## Summary

Today, you applied your SQL knowledge to a real-world project involving data analysis for an e-commerce company. This exercise is a culmination of the concepts you’ve learned so far, preparing you for real-world SQL challenges.

Up next, **Day 29: Final Revision**, where we’ll review everything we’ve covered in the past 28 days. 🚀

[Previous: Day 27 - SQL Security](../Day-27%20SQL%20Security/Day-27_SQL_Security.md)  
[Next: Day 29 - Final Revision](../Day-29%20Final%20Revision/Day-29_Final_Revision.md)


# Day 9: Advanced Joins 🚀

Welcome to Day 9 of the 30-Day SQL Challenge! Today, we’ll dive deeper into the world of SQL joins, exploring advanced join techniques to handle more complex data relationships. Let’s get started! 🎉

---

## Table of Contents 📖

1. [What Are Advanced Joins?](#what-are-advanced-joins)
2. [Self Join](#self-join)
3. [Full Outer Join](#full-outer-join)
4. [Cross Join](#cross-join)
5. [Using Joins with Aggregates](#using-joins-with-aggregates)
6. [Advanced Join Examples](#advanced-join-examples)
7. [Practice Exercises](#practice-exercises)
8. [Summary](#summary)

---

### What Are Advanced Joins? 🔍

Advanced joins build upon the basic join concepts by introducing more complex techniques for combining tables. These joins are particularly useful when working with hierarchical, multi-dimensional, or interrelated datasets.

---

### Self Join ✍️

A self join is a regular join where a table is joined with itself. This is useful for comparing rows within the same table.

#### Example: Employee Hierarchy

Consider an `employees` table:

| employee_id | name       | manager_id |
|-------------|------------|------------|
| 1           | Alice      | NULL       |
| 2           | Bob        | 1          |
| 3           | Charlie    | 1          |
| 4           | David      | 2          |

To find employees and their managers:

```sql
SELECT e1.name AS employee, e2.name AS manager
FROM employees e1
LEFT JOIN employees e2
ON e1.manager_id = e2.employee_id;
```

**Result:**

| employee | manager |
|----------|---------|
| Alice    | NULL    |
| Bob      | Alice   |
| Charlie  | Alice   |
| David    | Bob     |

---

### Full Outer Join 🌐

A full outer join returns all rows from both tables, with `NULL` in columns where there is no match.

#### Example: Matching Customers and Orders

Consider the following tables:

**customers**

| customer_id | name    |
|-------------|---------|
| 1           | John    |
| 2           | Sarah   |
| 3           | Michael |

**orders**

| order_id | customer_id | amount |
|----------|-------------|--------|
| 101      | 1           | 100    |
| 102      | 4           | 200    |

To find all customers and their orders:

```sql
SELECT c.name, o.amount
FROM customers c
FULL OUTER JOIN orders o
ON c.customer_id = o.customer_id;
```

**Result:**

| name    | amount |
|---------|--------|
| John    | 100    |
| Sarah   | NULL   |
| Michael | NULL   |
| NULL    | 200    |

---

### Cross Join 🌱

A cross join returns the Cartesian product of two tables. Every row in the first table is combined with every row in the second table.

#### Example: Product Combinations

**products**

| product_id | product_name |
|------------|--------------|
| 1          | Pen          |
| 2          | Notebook     |

**colors**

| color_id | color_name |
|----------|------------|
| 1        | Red        |
| 2        | Blue       |

To find all product-color combinations:

```sql
SELECT p.product_name, c.color_name
FROM products p
CROSS JOIN colors c;
```

**Result:**

| product_name | color_name |
|--------------|------------|
| Pen          | Red        |
| Pen          | Blue       |
| Notebook     | Red        |
| Notebook     | Blue       |

---

### Using Joins with Aggregates 📊

Joins can be combined with aggregate functions to summarize data across multiple tables.

#### Example: Total Sales by Customer

**orders**

| order_id | customer_id | amount |
|----------|-------------|--------|
| 101      | 1           | 100    |
| 102      | 1           | 150    |
| 103      | 2           | 200    |

**customers**

| customer_id | name    |
|-------------|---------|
| 1           | John    |
| 2           | Sarah   |

To calculate total sales by customer:

```sql
SELECT c.name, SUM(o.amount) AS total_sales
FROM customers c
JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.name;
```

**Result:**

| name  | total_sales |
|-------|-------------|
| John  | 250         |
| Sarah | 200         |

---

### Advanced Join Examples 🔄

#### Example 1: Joining More Than Two Tables

```sql
SELECT o.order_id, c.name AS customer_name, p.product_name
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN products p ON o.product_id = p.product_id;
```

#### Example 2: Conditional Joins

```sql
SELECT *
FROM orders o
LEFT JOIN customers c
ON o.customer_id = c.customer_id
AND c.name LIKE 'S%';
```

---

### Practice Exercises 🔧

1. Write a query using a self join to find pairs of employees who share the same manager.
2. Use a full outer join to list all products and their orders, including products without orders.
3. Write a cross join query to generate all possible pairs of customers and regions from a `customers` and `regions` table.
4. Combine joins with aggregates to calculate average order amounts for each product.
5. Write a query joining three tables to find detailed order summaries (e.g., customer name, product name, and total amount).

---

### Summary 🎯

Today, you learned about:

- **Self Joins**: Joining a table with itself.
- **Full Outer Joins**: Returning all rows from both tables.
- **Cross Joins**: Generating Cartesian products.
- Combining joins with aggregate functions.

Tomorrow, we’ll cover **Subqueries**. Stay tuned for more SQL fun! 🚀

---

[Previous: Day 8 - Joins Basics](../Day-8_Joins–Basics/Day-8_Joins–Basics.md) 🔼  \
[Next: Day 10 - Subqueries](../Day-10_Subqueries/Day-10_Subqueries.md) 🔽


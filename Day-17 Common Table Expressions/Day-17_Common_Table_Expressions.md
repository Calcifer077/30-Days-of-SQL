📘 30 Days Of SQL: Day 17 - Common Table Expressions (CTEs) in SQL

Welcome to Day 17 of the 30 Days of SQL challenge! 🎉 Today, we dive into Common Table Expressions (CTEs), an essential tool for writing clear, modular, and reusable SQL queries. Let’s break down their structure and power!

---

### Table of Contents

- 🔍 Overview
- 📘 Syntax and Components
  1. WITH Clause Basics
  2. Recursive CTEs
- 💡 Practical Examples
- 🔧 Best Practices
- 🎯 Hands-On Challenge
- 💻 Exercises - Day 17
- 📝 Day 17 Summary

---

### 🔍 Overview

CTEs are temporary result sets that simplify complex queries. They make your SQL code easier to read and maintain by allowing you to build modular queries. CTEs are especially useful for:

- Splitting complex queries into logical steps.
- Creating reusable query components.
- Implementing recursive queries.

---

### 📘 Syntax and Components

#### 1. WITH Clause Basics

The `WITH` clause introduces a CTE. Here’s the general syntax:

```sql
WITH cte_name AS (
    SELECT column1, column2
    FROM table_name
    WHERE condition
)
SELECT *
FROM cte_name;
```

**Example**:

```sql
WITH SalesSummary AS (
    SELECT product_id, SUM(sales_amount) AS total_sales
    FROM sales
    GROUP BY product_id
)
SELECT *
FROM SalesSummary
WHERE total_sales > 1000;
```

#### 2. Recursive CTEs

Recursive CTEs allow a query to reference itself. They’re commonly used for hierarchical data, like organizational charts or tree structures.

**Syntax**:

```sql
WITH RECURSIVE cte_name AS (
    -- Anchor member
    SELECT column1, column2
    FROM table_name
    WHERE condition

    UNION ALL

    -- Recursive member
    SELECT column1, column2
    FROM table_name
    INNER JOIN cte_name
    ON table_name.column = cte_name.column
)
SELECT *
FROM cte_name;
```

**Example**:

```sql
WITH RECURSIVE EmployeeHierarchy AS (
    -- Anchor member: Get top-level manager
    SELECT employee_id, manager_id, 1 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    -- Recursive member: Get employees reporting to the previous level
    SELECT e.employee_id, e.manager_id, eh.level + 1
    FROM employees e
    INNER JOIN EmployeeHierarchy eh
    ON e.manager_id = eh.employee_id
)
SELECT *
FROM EmployeeHierarchy;
```

---

### 💡 Practical Examples

#### 1. Simplify Complex Joins

Use CTEs to break down multi-step join operations:

```sql
WITH FilteredOrders AS (
    SELECT order_id, customer_id
    FROM orders
    WHERE order_date >= '2024-01-01'
),
CustomerSummary AS (
    SELECT customer_id, COUNT(order_id) AS order_count
    FROM FilteredOrders
    GROUP BY customer_id
)
SELECT *
FROM CustomerSummary
WHERE order_count > 5;
```

#### 2. Generate Running Totals

```sql
WITH RunningTotal AS (
    SELECT order_id, customer_id, order_date,
           SUM(order_amount) OVER (PARTITION BY customer_id ORDER BY order_date) AS cumulative_sales
    FROM orders
)
SELECT *
FROM RunningTotal
WHERE cumulative_sales > 500;
```

#### 3. Traverse Hierarchical Data

```sql
WITH RECURSIVE OrgChart AS (
    SELECT employee_id, manager_id, 0 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    SELECT e.employee_id, e.manager_id, oc.level + 1
    FROM employees e
    INNER JOIN OrgChart oc
    ON e.manager_id = oc.employee_id
)
SELECT *
FROM OrgChart
ORDER BY level;
```

---

### 🔧 Best Practices

- **Use Descriptive Names**: Name your CTEs clearly to reflect their purpose.
- **Limit Scope**: Avoid overly large or complex CTEs; keep them focused.
- **Optimize for Performance**: Use indexed columns and avoid unnecessary computations within the CTE.
- **Test Recursion**: For recursive CTEs, ensure there’s a termination condition to avoid infinite loops.

---

### 🎯 Hands-On Challenge

1. Create a CTE to calculate the average sales for each product category and filter categories with above-average sales.
2. Use a recursive CTE to display a company’s organizational hierarchy.
3. Implement a CTE to find customers with more than 3 orders in the past year.
4. Write a query using multiple CTEs to analyze product performance by region.

---

### 💻 Exercises - Day 17

#### ✅ Exercise: Level 1

1. Write a query using a CTE to list all employees in a specific department.
2. Create a CTE to calculate the total revenue for each region.
3. Use a recursive CTE to find the chain of command for a given employee.

#### 🚀 Exercise: Level 2

1. Use multiple CTEs to analyze monthly sales trends for the past year.
2. Implement a recursive CTE to calculate the factorial of a number.
3. Write a query using a CTE to identify the top 5 products by revenue.

---

### 📝 Day 17 Summary

Today, you learned about Common Table Expressions (CTEs) and how they simplify complex queries. You explored basic and recursive CTEs, practical applications, and best practices. With CTEs, your SQL queries can be more modular, readable, and powerful.

Stay tuned for Day 18, where we’ll cover Indexes and Query Optimization! 🚀

---

[Previous: Day 16 - Window Functions ⬆️ ](../Day-16%20Window%20Functions/Day-16_Window_Functions.md)  
[Next: Day 18 - Indexes and Query Optimization ⬇️ ](../Day-18%20Indexes%20and%20Query%20Optimization/Day-18_Indexes_and_Query_Optimization.md)



# 📘 30 Days Of SQL: Day 15 - Advanced Aggregate Functions in SQL

Welcome to **Day 15** of the **30 Days of SQL** challenge! 🎉 Today, we’ll take a deep dive into **Advanced Aggregate Functions**—essential tools for analyzing and summarizing data in SQL. If you've already mastered the basics of `SUM`, `COUNT`, and `AVG`, get ready to level up your SQL skills by exploring more complex and powerful aggregate functions.




## Table of Contents

- [🔍 Overview](#-overview)
- [📘 Key Aggregate Functions](#-key-aggregate-functions)
  - [1. GROUP_CONCAT / STRING_AGG](#1-group_concat--string_agg)
  - [2. LISTAGG (Oracle)](#2-listagg-oracle)
  - [3. MEDIAN](#3-median)
  - [4. PERCENTILE_CONT and PERCENTILE_DISC](#4-percentile_cont-and-percentile_disc)
  - [5. STDDEV and VARIANCE](#5-stddev-and-variance)
  - [6. ROLLUP and CUBE](#6-rollup-and-cube)
  - [7. COUNT DISTINCT with FILTER](#7-count-distinct-with-filter)
- [💡 Practical Examples](#-practical-examples)
- [📚 Examples](#-examples)
- [🔧 Best Practices](#-best-practices)
- [🎯 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises - Day 15](#-exercisesday-15)
- [📝 Day 15 Summary](#-day-15-summary)



## 🔍 Overview

SQL's aggregate functions are indispensable for summarizing and analyzing data. While basic aggregates like `SUM`, `AVG`, and `COUNT` are common, advanced aggregate functions unlock deeper insights into your datasets. They help you:

- Concatenate strings into a single value.
- Calculate statistical measures like median, variance, and standard deviation.
- Perform hierarchical aggregations with `ROLLUP` and `CUBE`.
- Handle distinct aggregations more flexibly.



## 📘 Key Aggregate Functions

Here’s a breakdown of advanced aggregate functions, their syntax, and their use cases.

### Types of Advanced Aggregate Functions 🏆

| **Function**       | **Description**                                                         |
|--|-|
| **`VARIANCE`**     | Calculates the variance of a numeric column.                           |
| **`STDDEV`**       | Calculates the standard deviation of a numeric column.                 |
| **`MEDIAN`**       | Finds the median value of a numeric column.                            |
| **`PERCENTILE_DISC`** | Returns a specific percentile (discrete).                             |
| **`PERCENTILE_CONT`** | Returns a specific percentile (continuous).                           |
| **`CUME_DIST`**    | Calculates the cumulative distribution of a value within a result set. |
| **`NTILE`**        | Divides rows into a specified number of groups and assigns a group ID. |




### **1. GROUP_CONCAT / STRING_AGG**

- **Purpose**: Concatenate values from multiple rows into a single string.
- **Supported Databases**:  
  - `GROUP_CONCAT` (MySQL)  
  - `STRING_AGG` (PostgreSQL, SQL Server)

**Syntax**:  
- MySQL: 
  ```sql
  SELECT GROUP_CONCAT(column_name SEPARATOR ', ') AS concatenated_values
  FROM table_name;
  ```
- PostgreSQL:
  ```sql
  SELECT STRING_AGG(column_name, ', ') AS concatenated_values
  FROM table_name;
  ```

**Example**:
```sql
SELECT STRING_AGG(product_name, ', ') AS products
FROM orders
WHERE category = 'Electronics';
```



### **2. LISTAGG (Oracle)**

- **Purpose**: Similar to `GROUP_CONCAT`, but specific to Oracle databases.
- **Syntax**:
  ```sql
  SELECT LISTAGG(column_name, ', ') WITHIN GROUP (ORDER BY column_name) AS concatenated_values
  FROM table_name;
  ```

**Example**:
```sql
SELECT LISTAGG(employee_name, ', ') WITHIN GROUP (ORDER BY hire_date) AS employee_list
FROM employees
WHERE department = 'HR';
```



### **3. MEDIAN**

- **Purpose**: Calculate the median value of a numeric column.
- **Supported Databases**: Oracle, PostgreSQL, SQL Server (with percentile functions).

**Syntax**:
```sql
SELECT MEDIAN(column_name) AS median_value
FROM table_name;
```

**Example**:
```sql
SELECT MEDIAN(salary) AS median_salary
FROM employees
WHERE department_id = 10;
```



### **4. PERCENTILE_CONT and PERCENTILE_DISC**

- **Purpose**: Calculate percentiles.  
  - `PERCENTILE_CONT`: Continuous percentile.  
  - `PERCENTILE_DISC`: Discrete percentile.
- **Supported Databases**: PostgreSQL, Oracle, SQL Server.

**Syntax** (PostgreSQL):
```sql
SELECT PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY column_name) AS median
FROM table_name;
```

**Example**:
```sql
SELECT PERCENTILE_CONT(0.9) WITHIN GROUP (ORDER BY score) AS top_10_percent
FROM test_results;
```



### **5. STDDEV and VARIANCE**

- **Purpose**: Calculate statistical measures like standard deviation and variance.
- **Supported Databases**: All major databases.

**Syntax**:
```sql
SELECT STDDEV(column_name) AS std_dev, VARIANCE(column_name) AS var
FROM table_name;
```

**Example**:
```sql
SELECT STDDEV(salary) AS salary_stddev, VARIANCE(salary) AS salary_variance
FROM employees;
```



### **6. ROLLUP and CUBE**

- **Purpose**: Generate subtotals and grand totals for hierarchical data.
- **Supported Databases**: PostgreSQL, MySQL, SQL Server, Oracle.

**Syntax** (ROLLUP):
```sql
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY ROLLUP(department_id);
```

**Syntax** (CUBE):
```sql
SELECT product_id, region, SUM(sales) AS total_sales
FROM sales_data
GROUP BY CUBE(product_id, region);
```



### **7. COUNT DISTINCT with FILTER**

- **Purpose**: Count distinct values with additional conditions.
- **Supported Databases**: PostgreSQL.

**Syntax**:
```sql
SELECT COUNT(DISTINCT column_name) FILTER (WHERE condition) AS count_value
FROM table_name;
```

**Example**:
```sql
SELECT COUNT(DISTINCT customer_id) FILTER (WHERE region = 'North') AS north_customers
FROM orders;
```



## 💡 Practical Examples

Here are real-world use cases for advanced aggregate functions:

1. **String Aggregation**:  
   Generate a comma-separated list of employee names by department.

   ```sql
   SELECT department_id, STRING_AGG(employee_name, ', ') AS employee_list
   FROM employees
   GROUP BY department_id;
   ```

2. **Median Salary**:  
   Find the median salary in each department.

   ```sql
   SELECT department_id, PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary) AS median_salary
   FROM employees
   GROUP BY department_id;
   ```

3. **Statistical Insights**:  
   Analyze salary distribution with standard deviation and variance.

   ```sql
   SELECT department_id, STDDEV(salary) AS salary_stddev, VARIANCE(salary) AS salary_variance
   FROM employees
   GROUP BY department_id;
   ```

4. **Hierarchical Aggregation**:  
   Get total sales by region and overall total using `ROLLUP`.

   ```sql
   SELECT region, SUM(sales) AS total_sales
   FROM sales_data
   GROUP BY ROLLUP(region);
   ```

### Syntax 🔧

Each advanced aggregate function follows this general syntax:

```sql
SELECT aggregate_function(column_name) AS result_alias
FROM table_name
[GROUP BY column_name]
[ORDER BY column_name];
```



## 📚 Examples 

#### Example 1: Variance and Standard Deviation

Suppose we have a `sales` table:

| region     | sales_amount |
|-|--|
| North      | 5000         |
| South      | 7000         |
| East       | 6000         |
| West       | 8000         |
| North      | 5500         |

To calculate the variance and standard deviation of `sales_amount`:

```sql
SELECT
    VARIANCE(sales_amount) AS sales_variance,
    STDDEV(sales_amount) AS sales_stddev
FROM sales;
```

**Result:**

| sales_variance | sales_stddev |
|-|--|
| 1250000        | 1118.03      |



#### Example 2: Median and Percentiles

To calculate the median and 75th percentile of `sales_amount`:

```sql
SELECT
    MEDIAN(sales_amount) AS median_sales,
    PERCENTILE_CONT(0.75) WITHIN GROUP (ORDER BY sales_amount) AS percentile_75
FROM sales;
```

**Result:**

| median_sales | percentile_75 |
|--|-|
| 6000         | 7500          |



#### Example 3: Cumulative Distribution

To calculate the cumulative distribution of sales amounts:

```sql
SELECT
    sales_amount,
    CUME_DIST() OVER (ORDER BY sales_amount) AS cumulative_distribution
FROM sales;
```

**Result:**

| sales_amount | cumulative_distribution |
|--|--|
| 5000         | 0.2                      |
| 5500         | 0.4                      |
| 6000         | 0.6                      |
| 7000         | 0.8                      |
| 8000         | 1.0                      |



#### Example 4: Grouping with NTILE

To divide sales into 2 groups (quartiles):

```sql
SELECT
    sales_amount,
    NTILE(2) OVER (ORDER BY sales_amount) AS group_id
FROM sales;
```

**Result:**

| sales_amount | group_id |
|--|-|
| 5000         | 1        |
| 5500         | 1        |
| 6000         | 2        |
| 7000         | 2        |
| 8000         | 2        |



## 🔧 Best Practices

1. **Optimize Queries**: Use aggregate functions with appropriate indexes to avoid performance issues.
2. **Leverage Database-Specific Features**: Some databases support advanced functions natively—use them for better performance.
3. **Understand Null Handling**: Be mindful of how NULL values are treated in aggregate functions.
4. **Combine Aggregates with Filters**: Use `FILTER` or `HAVING` clauses to target specific subsets of data.



## 🎯 Hands-On Challenge

1. **String Aggregation**: Write a query to list all product names sold in each region.
2. **Median Calculation**: Find the median revenue generated by orders in each month.
3. **Statistical Analysis**: Calculate the variance and standard deviation of employee bonuses across departments.
4. **Hierarchical Aggregation**: Use `CUBE` to analyze sales data by product and region.



## 💻 Exercises - Day 15

### ✅ Exercise: Level 1

1. Use `GROUP_CONCAT` or `STRING_AGG` to create a list of customer names by city.
2. Find the median purchase amount for each customer.
3. Calculate the standard deviation of product prices in your database.

### 🚀 Exercise: Level 2

1. Use `ROLLUP` to get subtotals and grand totals for sales by region and product category.
2. Write a query to calculate the 90th percentile of transaction amounts for each day.
3. Create a report showing the variance of employee salaries grouped by job title.



## 📝 Day 15 Summary

Today, you mastered **Advanced Aggregate Functions in SQL**, including string concatenation, statistical measures, and hierarchical aggregations. These tools empower you to uncover deeper insights from your data. Practice combining these functions with `GROUP BY`, `HAVING`, and filtering to create powerful queries.

Stay tuned for **Day 16**, where we’ll explore **Window Funtions** in SQL! 🚀  

[Previous: Day 14 - Intermediate SQL Practice and Quiz](../Day-14%20Intermediate%20Sql%20Practice%20Quiz/Day-14_Intermediate_Sql_Practice_Quiz.md) 🔼  
[Next: Day 16 - Window Functions](../Day-16%20Window%20Functions/Day-16_Window_Functions.md) 🔽

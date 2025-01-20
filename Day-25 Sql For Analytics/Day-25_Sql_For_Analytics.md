# 📘 30 Days Of SQL: Day 25 - SQL for Analytics

Welcome to **Day 25** of the **30 Days of SQL** challenge! 🎉 Today, we’ll focus on how SQL can be used for analytics, covering techniques and functions commonly employed to derive insights from data. If you're aspiring to become a data analyst or scientist, this session will provide invaluable skills.

---

## Table of Contents

- [🔍 Overview](#-overview)
- [🔢 Key Concepts in SQL for Analytics](#-key-concepts-in-sql-for-analytics)
  - [1. Ranking Functions](#1-ranking-functions)
  - [2. Rolling Aggregates](#2-rolling-aggregates)
  - [3. Pivoting and Unpivoting Data](#3-pivoting-and-unpivoting-data)
  - [4. Window Functions in Analytics](#4-window-functions-in-analytics)
  - [5. Cohort Analysis](#5-cohort-analysis)
  - [6. Time-Series Analysis](#6-time-series-analysis)
- [📊 Practical Applications](#-practical-applications)
- [🛠️ Best Practices](#-best-practices)
- [💻 Hands-On Challenge](#-hands-on-challenge)
- [🔧 Exercises - Day 25](#-exercises---day-25)
- [🗋 Day 25 Summary](#-day-25-summary)

---

## 🔍 Overview

SQL is a cornerstone of analytics workflows, enabling professionals to:

- Extract and transform data efficiently.
- Apply advanced calculations and aggregations.
- Build insights with ranking, trends, and patterns.
- Perform time-series and cohort analysis for actionable insights.

Whether working with structured data warehouses or large transactional databases, SQL’s power lies in its ability to handle analytics directly within the database.

---

## 🔢 Key Concepts in SQL for Analytics

### 1. Ranking Functions

Ranking functions assign ranks or row numbers to rows in a result set, often for ordering or comparison purposes. Common ranking functions include:

- **ROW_NUMBER**: Assigns a unique sequential integer to rows.
- **RANK**: Assigns ranks, with gaps for tied values.
- **DENSE_RANK**: Assigns ranks without gaps.

**Syntax**:
```sql
SELECT
    column_name,
    RANK() OVER (PARTITION BY category ORDER BY sales DESC) AS rank
FROM sales_data;
```

---

### 2. Rolling Aggregates

Rolling aggregates compute cumulative metrics over a defined window of rows. Examples include cumulative sums or running averages.

**Syntax**:
```sql
SELECT
    order_date,
    SUM(sales) OVER (ORDER BY order_date ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS cumulative_sales
FROM sales_data;
```

---

### 3. Pivoting and Unpivoting Data

Pivoting transforms rows into columns, often used to reshape data for analysis. Conversely, unpivoting converts columns back into rows.

**Pivot Syntax** (SQL Server):
```sql
SELECT *
FROM sales_data
PIVOT (
    SUM(sales)
    FOR region IN ([North], [South], [East], [West])
) AS pivot_table;
```

**Unpivot Syntax** (SQL Server):
```sql
SELECT *
FROM sales_data
UNPIVOT (
    sales FOR region IN ([North], [South], [East], [West])
) AS unpivot_table;
```

---

### 4. Window Functions in Analytics

Window functions allow calculations across a subset of rows, commonly used for:
- Percentile and percentile rank.
- Lag and lead analysis.
- Moving averages.

**Example**:
```sql
SELECT
    product_id,
    sales,
    LAG(sales) OVER (PARTITION BY product_id ORDER BY sale_date) AS previous_day_sales
FROM sales_data;
```

---

### 5. Cohort Analysis

Cohort analysis groups users based on shared characteristics, such as sign-up date, to analyze behavior over time.

**Example**:
```sql
SELECT
    sign_up_month,
    cohort,
    COUNT(user_id) AS active_users
FROM (
    SELECT
        user_id,
        DATE_TRUNC('month', sign_up_date) AS cohort,
        DATE_TRUNC('month', last_active_date) AS sign_up_month
    FROM user_data
) subquery
GROUP BY cohort, sign_up_month;
```

---

### 6. Time-Series Analysis

Time-series analysis evaluates trends over time, often with time-based grouping and aggregation.

**Example**:
```sql
SELECT
    DATE_TRUNC('month', order_date) AS order_month,
    SUM(sales) AS total_sales
FROM sales_data
GROUP BY order_month;
```

---

## 📊 Practical Applications

1. **Customer Segmentation**: Using ranking and cohort analysis to identify top customers and behavioral trends.
2. **Revenue Trends**: Analyzing revenue growth or decline over time with time-series data.
3. **Churn Analysis**: Employing lag functions to identify inactive customers and potential churn patterns.
4. **Operational Insights**: Aggregating and pivoting operational data to monitor performance metrics.

---

## 🛠️ Best Practices

- **Optimize Queries**: Use indexes for large datasets and avoid unnecessary computations.
- **Understand Data Granularity**: Align your queries with the granularity of the data (e.g., daily, monthly).
- **Use Window Functions Wisely**: Be mindful of memory consumption when using complex window functions.
- **Visualize Results**: Integrate SQL queries with visualization tools for clearer insights.

---

## 💻 Hands-On Challenge

1. Write a query to rank products by total sales within each region.
2. Create a time-series analysis of monthly revenue trends.
3. Perform a cohort analysis of user activity based on their sign-up month.
4. Use a window function to calculate a 7-day rolling average of daily sales.

---

## 🔧 Exercises - Day 25

### ✅ Exercise: Level 1

1. Use `ROW_NUMBER` to rank employees by their salary in each department.
2. Write a query to calculate cumulative sales for each product.
3. Pivot sales data to show total sales by region for a given year.

### 🚀 Exercise: Level 2

1. Perform a cohort analysis to evaluate user retention by their sign-up month.
2. Use window functions to calculate percentile ranks for student scores.
3. Create a query that identifies the top-performing sales agents by region.

---

## 🗋 Day 25 Summary

Today, we explored **SQL for Analytics**, a critical skill for deriving insights from data. From ranking and rolling aggregates to cohort and time-series analysis, you now have the tools to tackle real-world analytical challenges. Combine these techniques to extract actionable insights and drive data-driven decisions.

Stay tuned for **Day 26**, where we’ll dive into **Error Handling and Debugging** in SQL! 🚀

[Previous: Day 24 - Data Import and Export](../Day-24%20Data%20Import%20and%20Export/Day-24_Data_Import_and_Export.md) 🏚️  
[Next: Day 26 - Error Handling and Debugging](../Day-26%20Error%20Handling%20and%20Debugging/Day-26_Error_Handling_and_Debugging.md) 🔄


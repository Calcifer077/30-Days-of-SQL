📘 30 Days Of SQL: Day 16 - Window Functions in SQL

Welcome to Day 16 of the 30 Days of SQL challenge! 🎉 Today, we’ll explore Window Functions, a powerful feature that allows you to perform advanced data analysis across rows while retaining row-level granularity. Get ready to unlock new possibilities in SQL!

---

## Table of Contents

- [🔍 Overview](#-overview)
- [📘 Key Window Functions](#-key-window-functions)
  - [1. ROW_NUMBER](#1-row_number)
  - [2. RANK and DENSE_RANK](#2-rank-and-dense_rank)
  - [3. NTILE](#3-ntile)
  - [4. LEAD and LAG](#4-lead-and-lag)
  - [5. FIRST_VALUE and LAST_VALUE](#5-first_value-and-last_value)
  - [6. OVER Clause](#6-over-clause)
- [💡 Practical Examples](#-practical-examples)
- [🔧 Best Practices](#-best-practices)
- [🎯 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises - Day 16](#-exercises---day-16) <!-- Corrected anchor -->
- [📝 Day 16 Summary](#-day-16-summary)


---

### 🔍 Overview
Window Functions are SQL functions that operate on a set of rows related to the current row. Unlike aggregate functions, they do not collapse rows but instead add calculated values to each row. Window Functions are especially useful for:

- Ranking rows.
- Calculating moving averages.
- Retrieving values from other rows.
- Performing cumulative calculations.

---

### 📘 Key Window Functions
Here’s a breakdown of the most commonly used Window Functions:

| Function          | Description                                                                                 |
|-------------------|---------------------------------------------------------------------------------------------|
| ROW_NUMBER       | Assigns a unique sequential integer to rows within a partition.                            |
| RANK             | Assigns a rank to rows in a partition, with gaps in ranking for ties.                      |
| DENSE_RANK       | Similar to RANK but without gaps in ranking for ties.                                       |
| NTILE            | Divides rows into a specified number of groups and assigns each row a group ID.            |
| LEAD and LAG     | Retrieve values from the next or previous row in a partition.                              |
| FIRST_VALUE      | Retrieves the first value in a partition.                                                  |
| LAST_VALUE       | Retrieves the last value in a partition.                                                   |

---

### Syntax 🔧
Each Window Function is used with the `OVER` clause:

```sql
SELECT column_name,
       window_function() OVER ([PARTITION BY column_name] [ORDER BY column_name]) AS alias_name
FROM table_name;
```

---

### 💡 Practical Examples

#### 1. ROW_NUMBER
Assign a unique number to each employee within their department:

```sql
SELECT employee_id, department_id, salary,
       ROW_NUMBER() OVER (PARTITION BY department_id ORDER BY salary DESC) AS row_num
FROM employees;
```

#### 2. RANK and DENSE_RANK
Rank employees by salary within their department:

```sql
-- RANK Example
SELECT employee_id, department_id, salary,
       RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank
FROM employees;

-- DENSE_RANK Example
SELECT employee_id, department_id, salary,
       DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS dense_rank
FROM employees;
```

#### 3. NTILE
Divide employees into 4 salary quartiles:

```sql
SELECT employee_id, department_id, salary,
       NTILE(4) OVER (PARTITION BY department_id ORDER BY salary) AS quartile
FROM employees;
```

#### 4. LEAD and LAG
Retrieve the previous and next employee’s salary:

```sql
SELECT employee_id, salary,
       LAG(salary) OVER (ORDER BY salary) AS prev_salary,
       LEAD(salary) OVER (ORDER BY salary) AS next_salary
FROM employees;
```

#### 5. FIRST_VALUE and LAST_VALUE
Get the first and last salary in each department:

```sql
SELECT employee_id, department_id, salary,
       FIRST_VALUE(salary) OVER (PARTITION BY department_id ORDER BY salary) AS min_salary,
       LAST_VALUE(salary) OVER (PARTITION BY department_id ORDER BY salary ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS max_salary
FROM employees;
```

#### 6. OVER Clause
The `OVER` clause defines the window or set of rows that the window function operates on. It can include the following components:

1. **PARTITION BY**: Divides the result set into partitions.
2. **ORDER BY**: Specifies the order of rows within each partition.
3. **ROWS or RANGE**: Defines the frame of rows for calculations.

```sql
SELECT employee_id, salary,
       SUM(salary) OVER (PARTITION BY department_id ORDER BY salary) AS cumulative_salary
FROM employees;

```

---

### 🔧 Best Practices
- **Use PARTITION BY Wisely**: Partition data meaningfully to get accurate results.
- **Optimize Performance**: Combine Window Functions with indexed columns to improve query speed.
- **Understand ROWS vs RANGE**: Be clear on how the window frame affects calculations.
- **Avoid Overlapping Calculations**: Reduce redundancy by minimizing the number of Window Functions in a query.

---

### 🎯 Hands-On Challenge

1. Use ROW_NUMBER to identify the top 3 earners in each department.
2. Use RANK and DENSE_RANK to rank employees based on their performance scores.
3. Calculate a running total of sales using a Window Function.
4. Use LEAD and LAG to compare a product’s sales with its previous and next month’s performance.
5. Retrieve the first and last transaction amounts for each customer using FIRST_VALUE and LAST_VALUE.

---

## 💻 Exercises - Day 16

#### ✅ Exercise: Level 1
1. Write a query to assign row numbers to students in each class based on their grades.
2. Rank products by sales revenue within each category.
3. Retrieve the previous and next order amounts for each customer.

#### 🚀 Exercise: Level 2
1. Divide employees into 3 groups based on their salaries and assign a group ID.
2. Calculate the cumulative sum of sales for each product category.
3. Retrieve the first and last purchase amounts for each region in the sales table.

---

### 📝 Day 16 Summary
Today, you mastered Window Functions in SQL, including ROW_NUMBER, RANK, NTILE, and FIRST_VALUE. These tools allow for sophisticated data analysis while maintaining row-level details. Experiment with combining these functions to unlock powerful insights.

Stay tuned for Day 17, where we’ll explore Common Table Expressions (CTEs) in SQL! 🚀

---

Previous: [Day 15 - Advanced Aggregate Functions](../Day-15%20%20Advanced%20Aggregate%20Functions/Day-15_Advanced_Aggregate_Functions.md) 🔼

Next: [Day 17 - Common Table Expressions (CTEs)](../Day-17%20Common%20Table%20Expressions/Day-17_Common_Table_Expressions.md) 🔽


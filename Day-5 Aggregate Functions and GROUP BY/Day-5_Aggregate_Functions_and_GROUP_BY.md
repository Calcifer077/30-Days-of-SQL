# Day 5: Aggregate Functions and GROUP BY 🎉

Welcome to Day 5 of the 30-Day SQL Challenge! Today, we will explore **aggregate functions** and how to use the **GROUP BY** clause to summarize data. Let's dive in! 🚀

---

## Table of Contents 📚

1. [What are Aggregate Functions?](#what-are-aggregate-functions)
2. [Common Aggregate Functions](#common-aggregate-functions)
3. [Using GROUP BY](#using-group-by)
4. [Combining GROUP BY with Aggregate Functions](#combining-group-by-with-aggregate-functions)
5. [Practice Exercises](#practice-exercises)
6. [Summary](#summary)

---

### What are Aggregate Functions? 📊

Aggregate functions are used to perform calculations on a set of values, returning a single value as a result. These functions are commonly used to summarize data in SQL.

---

### Common Aggregate Functions 🛠️

| **Function**   | **Description**                            | **Example**                      |
|----------------|--------------------------------------------|----------------------------------|
| `COUNT()`      | Counts the number of rows.                 | `COUNT(*)`                       |
| `SUM()`        | Calculates the total sum of a column.      | `SUM(salary)`                    |
| `AVG()`        | Calculates the average value of a column.  | `AVG(salary)`                    |
| `MIN()`        | Returns the smallest value in a column.    | `MIN(age)`                       |
| `MAX()`        | Returns the largest value in a column.     | `MAX(age)`                       |

Example:

```sql
SELECT COUNT(*) AS total_employees,
       AVG(salary) AS average_salary
FROM employees;
```

---

### Using GROUP BY 🧑‍🤝‍🧑

The `GROUP BY` clause is used to group rows that have the same values in specified columns. It is often used with aggregate functions to group the results by one or more columns.

#### Syntax 🛠️

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```

#### Example:

Imagine the following `employees` table:

| id | name       | department | salary |
|----|------------|------------|--------|
| 1  | John Doe   | HR         | 50000  |
| 2  | Jane Smith | IT         | 60000  |
| 3  | Sam Brown  | HR         | 55000  |
| 4  | Lisa Wong  | IT         | 70000  |
| 5  | Mark Lee   | Marketing  | 45000  |

To calculate the total salary for each department:

```sql
SELECT department, SUM(salary) AS total_salary
FROM employees
GROUP BY department;
```

Result:

| department | total_salary |
|------------|--------------|
| HR         | 105000       |
| IT         | 130000       |
| Marketing  | 45000        |

---

### Combining GROUP BY with Aggregate Functions 🤝

You can use multiple aggregate functions with the `GROUP BY` clause. For example:

```sql
SELECT department,
       COUNT(*) AS total_employees,
       AVG(salary) AS average_salary,
       MAX(salary) AS highest_salary
FROM employees
GROUP BY department;
```

---

### Practice Exercises 📝

1. Write a query to find the total number of students in each course from a `students` table.
2. Calculate the average salary of employees in each department from an `employees` table.
3. Find the minimum and maximum price of products in each category from a `products` table.
4. Count the number of orders placed by each customer from an `orders` table.

---

### Summary 🏁

Today, you learned:

- What aggregate functions are and how to use them.
- The purpose and syntax of the `GROUP BY` clause.
- How to combine `GROUP BY` with aggregate functions to summarize data.

Tomorrow, we will explore the **HAVING clause** for filtering grouped data. Stay tuned! 🌟

---

[Previous: Day 4 - Sorting Data with ORDER BY](./day4.md) 🔙  
[Next: Day 6 - HAVING Clause](./day6.md) 🔜


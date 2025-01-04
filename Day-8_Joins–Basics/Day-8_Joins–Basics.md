# Day 8: Joins – Basics 🌟

Welcome to Day 8 of the 30-Day SQL Challenge! Today, we’ll dive into the fascinating world of SQL Joins. Joins allow you to combine data from multiple tables into meaningful insights. Let’s get started! ✨

---

## Table of Contents 🔍

1. [What Are Joins?](#what-are-joins-)
2. [Types of Joins](#types-of-joins-)
3. [Syntax of Joins](#syntax-of-joins-)
4. [Examples of Joins](#examples-of-joins-)
5. [Practice Exercises](#practice-exercises-)
6. [Summary](#summary-)

---

### What Are Joins? 🔎

Joins are SQL operations that combine rows from two or more tables based on a related column. They help in:

- Accessing data distributed across multiple tables.
- Creating meaningful associations between data entities.
- Simplifying queries for complex datasets.

---

### Types of Joins 🌐

| **Join Type**     | **Description**                                                                     |
|-------------------|-------------------------------------------------------------------------------------|
| **INNER JOIN**    | Returns records that have matching values in both tables.                         |
| **LEFT JOIN**     | Returns all records from the left table and matched records from the right table. |
| **RIGHT JOIN**    | Returns all records from the right table and matched records from the left table. |
| **FULL OUTER JOIN** | Returns all records when there is a match in either left or right table.         |

---

### Syntax of Joins 🔧

#### INNER JOIN Syntax:

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

#### LEFT JOIN Syntax:

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
```

#### RIGHT JOIN Syntax:

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```

#### FULL OUTER JOIN Syntax:

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

---

### Examples of Joins 🔄

Let’s assume we have two tables:

#### Table: `employees`

| employee_id | name       | department_id |
|-------------|------------|---------------|
| 1           | John Doe   | 101           |
| 2           | Jane Smith | 102           |
| 3           | Sam Brown  | 103           |
| 4           | Lisa White | NULL          |

#### Table: `departments`

| department_id | department_name |
|---------------|-----------------|
| 101           | HR              |
| 102           | IT              |
| 103           | Marketing       |
| 104           | Finance         |

#### Example 1: INNER JOIN

To find employees and their department names:

```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments
ON employees.department_id = departments.department_id;
```

**Result:**

| name       | department_name |
|------------|-----------------|
| John Doe   | HR              |
| Jane Smith | IT              |
| Sam Brown  | Marketing       |

#### Example 2: LEFT JOIN

To include all employees, even those without a department:

```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments
ON employees.department_id = departments.department_id;
```

**Result:**

| name       | department_name |
|------------|-----------------|
| John Doe   | HR              |
| Jane Smith | IT              |
| Sam Brown  | Marketing       |
| Lisa White | NULL            |

#### Example 3: RIGHT JOIN

To include all departments, even those without employees:

```sql
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments
ON employees.department_id = departments.department_id;
```

**Result:**

| name       | department_name |
|------------|-----------------|
| John Doe   | HR              |
| Jane Smith | IT              |
| Sam Brown  | Marketing       |
| NULL       | Finance         |

#### Example 4: FULL OUTER JOIN

To include all employees and all departments:

```sql
SELECT employees.name, departments.department_name
FROM employees
FULL OUTER JOIN departments
ON employees.department_id = departments.department_id;
```

**Result:**

| name       | department_name |
|------------|-----------------|
| John Doe   | HR              |
| Jane Smith | IT              |
| Sam Brown  | Marketing       |
| Lisa White | NULL            |
| NULL       | Finance         |

---

### Practice Exercises 🔧

1. Given a table `orders` and another table `customers`, find all orders with their customer names using an `INNER JOIN`.
2. Use a `LEFT JOIN` to list all products and their orders from `products` and `orders` tables.
3. Create a query to find departments without any employees using a `RIGHT JOIN`.
4. Write a query to combine two tables `authors` and `books` to list all authors and the books they’ve written using a `FULL OUTER JOIN`.
5. Modify the `employees` and `departments` examples above to include additional columns.

---

### Summary 🏁

Today, you learned about:

- The purpose of SQL Joins and their types.
- Writing queries using `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, and `FULL OUTER JOIN`.
- Practical use cases with examples and exercises.

Tomorrow, we’ll explore **Advanced Joins** to build on today’s foundation. Stay curious and keep querying! 🌐

---

[Previous: Day 7 - SQL Practice and Quiz](../Day-7%20SQL%20Practice%20and%20Quiz/Day-7_SQL_Practice_and_Quiz.md) 🔼\
[Next: Day 9 - Advanced Joins](../Day-9_Advanced_Joins/Day-9_Advanced_Joins.md) 🔽


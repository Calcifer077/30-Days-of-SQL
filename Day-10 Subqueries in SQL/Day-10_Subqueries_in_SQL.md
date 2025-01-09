# Day 10: Subqueries in SQL 🎉

Welcome to Day 10 of the 30-Day SQL Challenge! Today, we’ll dive into **subqueries** — a powerful way to nest one query within another. Subqueries are essential for writing advanced and efficient SQL queries. Let’s explore their syntax, types, and use cases. 🚀

---

## Table of Contents 🔖

1. [What is a Subquery?](#what-is-a-subquery-)
2. [Types of Subqueries](#types-of-subqueries-%EF%B8%8F)
3. [Subquery Syntax](#subquery-syntax-)
4. [Examples of Subqueries](#examples-of-subqueries-)
5. [Subqueries vs. Joins](#subqueries-vs-joins-%EF%B8%8F)
6. [Practice Exercises](#practice-exercises-)
7. [Summary](#summary-)

---

### What is a Subquery? 🔎

A **subquery** is a query nested inside another SQL query. Subqueries can:

- Be used in `SELECT`, `FROM`, or `WHERE` clauses.
- Provide intermediate results for the main query.
- Make complex queries easier to read and maintain.

---

### Types of Subqueries ⚖️

Subqueries are categorized based on their usage and output:

1. **Single-Row Subqueries:** Return one row with one column.
2. **Multi-Row Subqueries:** Return multiple rows with one column.
3. **Multi-Column Subqueries:** Return multiple rows with multiple columns.
4. **Correlated Subqueries:** Depend on the outer query for their execution.
5. **Non-Correlated Subqueries:** Execute independently of the outer query.

---

### Subquery Syntax 🔧

```sql
SELECT column1, column2
FROM table_name
WHERE column3 = (SELECT aggregate_function(column4) FROM table_name WHERE condition);
```

### Key Points:

- Subqueries are enclosed in parentheses `()`.
- They can use aggregate functions like `SUM`, `COUNT`, `AVG`.
- Placement depends on the clause (e.g., `SELECT`, `FROM`, or `WHERE`).

---

### Examples of Subqueries 🔄

#### Example 1: Subquery in the WHERE Clause

Find employees who earn more than the average salary:

```sql
SELECT employee_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

**Result:**

| employee_name | salary |
|---------------|--------|
| John          | 75000  |
| Sarah         | 80000  |

---

#### Example 2: Subquery in the SELECT Clause

Find each employee’s salary and the average salary of their department:

```sql
SELECT employee_name, salary,
       (SELECT AVG(salary)
        FROM employees e2
        WHERE e1.department_id = e2.department_id) AS avg_department_salary
FROM employees e1;
```

**Result:**

| employee_name | salary | avg_department_salary |
|---------------|--------|-----------------------|
| John          | 75000  | 70000                 |
| Sarah         | 80000  | 70000                 |

---

#### Example 3: Subquery in the FROM Clause

Find the department with the highest total salary:

```sql
SELECT department_name, total_salary
FROM (SELECT department_id, SUM(salary) AS total_salary
      FROM employees
      GROUP BY department_id) AS department_totals
WHERE total_salary = (SELECT MAX(total_salary)
                      FROM (SELECT department_id, SUM(salary) AS total_salary
                            FROM employees
                            GROUP BY department_id) AS department_totals);
```

**Result:**

| department_name | total_salary |
|-----------------|--------------|
| IT             | 250000       |

---

#### Example 4: Correlated Subquery

Find employees whose salary is above the average salary of their department:

```sql
SELECT employee_name, salary
FROM employees e1
WHERE salary > (SELECT AVG(salary)
                FROM employees e2
                WHERE e1.department_id = e2.department_id);
```

**Result:**

| employee_name | salary |
|---------------|--------|
| John          | 75000  |
| Sarah         | 80000  |

---

### Subqueries vs. Joins ⚖️

| **Aspect**         | **Subqueries**                              | **Joins**                              |
|--------------------|---------------------------------------------|---------------------------------------|
| **Usage**          | Nest one query inside another.             | Combine data from multiple tables.    |
| **Performance**    | May be slower for large datasets.           | Often faster with proper indexing.    |
| **Readability**    | Easier for complex logic.                   | Clearer for direct table relationships.|

---

### Practice Exercises 🎓

1. Write a query to find the highest-paid employee in each department using subqueries.
2. Use a subquery to identify customers who have placed more orders than the average number of orders.
3. Find the name and salary of employees whose salary is greater than the department’s average salary.
4. Create a query to determine which products have a price higher than the average product price.
5. Write a query to find all orders with a total value greater than the average order value.

---

### Summary 🏁

Today, you learned about:

- Different types of subqueries and their use cases.
- Writing subqueries in `SELECT`, `FROM`, and `WHERE` clauses.
- The distinction between subqueries and joins.

Subqueries are a key component of advanced SQL, and mastering them will greatly enhance your querying skills. Tomorrow, we’ll explore **Set Operations**! Get ready for another exciting session. 🚀

---

[Previous: Day 9 - Advanced Joins](../Day-9_Advanced_Joins/Day-9_Advanced_Joins.md) 👆\
[Next: Day 11 - Set Operations](../Day-11%20Set%20Operations/Day-11_Set_Operations.md) 👇


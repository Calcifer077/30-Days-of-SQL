# Day 6: The HAVING Clause 🎉

Welcome to Day 6 of the 30-Day SQL Challenge! Today, we will explore the `HAVING` clause—an essential tool for filtering grouped data in SQL. Let’s dive into its syntax and practical applications. 🚀

---

## Table of Contents 📖

1. [What is the HAVING Clause?](#what-is-the-having-clause-)
2. [Syntax of HAVING](#syntax-of-having-)
3. [Difference Between WHERE and HAVING](#difference-between-where-and-having-)
4. [Examples of HAVING](#examples-of-having-)
5. [Practice Exercises](#practice-exercises-)
6. [Summary](#summary-)

---

### What is the HAVING Clause? 🔍

The `HAVING` clause is used to filter the results of groups created by the `GROUP BY` clause. Unlike the `WHERE` clause, which filters rows before grouping, `HAVING` filters groups after aggregation.

### Syntax of HAVING 🔧

```sql
SELECT column1, column2, aggregate_function(column3)
FROM table_name
GROUP BY column1, column2
HAVING condition;
```

- **`column1, column2`**: Columns used for grouping.
- **`aggregate_function(column3)`**: Aggregate function like `SUM`, `AVG`, `COUNT`, etc.
- **`condition`**: Condition to filter grouped data.

---

### Difference Between WHERE and HAVING ⚙

| **Aspect**       | **WHERE Clause**                                   | **HAVING Clause**                               |
|------------------|--------------------------------------------------|------------------------------------------------|
| **Purpose**      | Filters rows before grouping.                     | Filters groups after aggregation.              |
| **Usage**        | Can’t use aggregate functions directly.           | Works with aggregate functions.                |
| **Example**      | `WHERE age > 30`                                  | `HAVING COUNT(*) > 5`                          |

---

### Examples of HAVING 🎓

#### Example 1: Basic Usage of HAVING

Suppose we have a table named `sales`:

| salesperson | region     | sales_amount |
|-------------|------------|--------------|
| Alice       | North      | 5000         |
| Bob         | South      | 7000         |
| Alice       | North      | 3000         |
| Bob         | South      | 2000         |
| Carol       | East       | 8000         |

To find regions with total sales greater than 10,000:

```sql
SELECT region, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY region
HAVING total_sales > 10000;
```

**Result:**

Since none of the regions have total sales greater than 10,000, the query returns **no rows**.

---

#### Example 2: Using Multiple Conditions

To find salespersons who have made more than 1 sale and whose total sales exceed 6,000:

```sql
SELECT salesperson, COUNT(*) AS sales_count, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY salesperson
HAVING sales_count > 1 AND total_sales > 6000;
```

**Result:**

| salesperson | sales_count | total_sales |
|-------------|-------------|-------------|
| Alice       | 2           | 8000        |

---

#### Example 3: Combining HAVING with Other Aggregates

To find regions where the average sales amount is greater than 4000:

```sql
SELECT region, AVG(sales_amount) AS average_sales
FROM sales
GROUP BY region
HAVING average_sales > 4000;
```

**Result:**

| region | average_sales |
|--------|---------------|
| North  | 4000          |
| South  | 6000          |
| East   | 8000          |

---

#### Example 4: Using HAVING with COUNT

Suppose there’s a `students` table:

| class  | student_name | score |
|--------|--------------|-------|
| A      | John         | 85    |
| A      | Mary         | 90    |
| B      | Jake         | 70    |
| B      | Emily        | 75    |
| A      | Steve        | 95    |

To find classes with more than 2 students:

```sql
SELECT class, COUNT(student_name) AS student_count
FROM students
GROUP BY class
HAVING student_count > 2;
```

**Result:**

| class | student_count |
|-------|---------------|
| A     | 3             |

---

### Practice Exercises 🔧

1. Given a table `orders` with columns `customer_id`, `order_date`, and `order_total`, write a query to find customers whose total order value exceeds $5000.
2. Use the `HAVING` clause to filter products from a `products` table where the average price is greater than $50.
3. Modify the examples above to include additional conditions or aggregate functions.
4. Create a query for a `library` table to find authors with more than 3 published books and an average rating above 4.5.
5. Write a query to find departments in a `company` table where the total salary of employees exceeds $100,000.

---

### Summary 🏁

Today, you learned about:

- The purpose of the `HAVING` clause and how it differs from `WHERE`.
- Writing queries with `HAVING` to filter aggregated data.
- Practical use cases with multiple examples and exercises.

Tomorrow, we’ll test your knowledge with a **Practice and Quiz Day**! Get ready to consolidate your learning so far. 🌟

---

[Previous: Day 5 - Aggregate Functions and GROUP BY](../Day-5%20Aggregate%20Functions%20and%20GROUP%20BY/Day-5_Aggregate_Functions_and_GROUP_BY.md) 🔼\
[Next: Day 7 - SQL Practice and Quiz](../Day-7%20SQL%20Practice%20and%20Quiz/Day-7_SQL_Practice_and_Quiz.md) 🔽


# Day 4: Sorting Data with ORDER BY 🎈

Welcome to Day 4 of the 30-Day SQL Challenge! Today, we'll explore the `ORDER BY` clause, which is used to sort data in ascending or descending order. Sorting is a crucial aspect of data retrieval that helps organize and analyze data effectively. Let's get started! 🚀

---

## Table of Contents 📒

1. [What is the ORDER BY Clause?](#what-is-the-order-by-clause)
2. [Basic Syntax of ORDER BY](#basic-syntax-of-order-by)
3. [Sorting in Ascending Order](#sorting-in-ascending-order)
4. [Sorting in Descending Order](#sorting-in-descending-order)
5. [Sorting by Multiple Columns](#sorting-by-multiple-columns)
6. [Practice Exercises](#practice-exercises)
7. [Summary](#summary)

---

### What is the ORDER BY Clause? 🏛️

The `ORDER BY` clause in SQL is used to sort the rows returned by a query based on one or more columns. By default, data is sorted in ascending order unless specified otherwise.

### Basic Syntax of ORDER BY 🔠

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column_name [ASC|DESC];
```

- `column_name`: The column you want to sort by.
- `ASC`: Optional keyword to sort in ascending order (default).
- `DESC`: Keyword to sort in descending order.

---

### Sorting in Ascending Order 🔼

Ascending order (`ASC`) is the default sorting order. It arranges data from smallest to largest (for numbers) or alphabetically (for strings).

#### Example:

Given the `employees` table:

| id | name       | age | department |
|----|------------|-----|------------|
| 1  | John Doe   | 30  | HR         |
| 2  | Jane Smith | 25  | IT         |
| 3  | Sam Brown  | 35  | Marketing  |

To sort employees by age in ascending order:

```sql
SELECT *
FROM employees
ORDER BY age;
```

**Result:**

| id | name       | age | department |
|----|------------|-----|------------|
| 2  | Jane Smith | 25  | IT         |
| 1  | John Doe   | 30  | HR         |
| 3  | Sam Brown  | 35  | Marketing  |

---

### Sorting in Descending Order 🔽

Descending order (`DESC`) arranges data from largest to smallest (for numbers) or reverse alphabetical order (for strings).

#### Example:

To sort employees by age in descending order:

```sql
SELECT *
FROM employees
ORDER BY age DESC;
```

**Result:**

| id | name       | age | department |
|----|------------|-----|------------|
| 3  | Sam Brown  | 35  | Marketing  |
| 1  | John Doe   | 30  | HR         |
| 2  | Jane Smith | 25  | IT         |

---

### Sorting by Multiple Columns 🔄

You can sort by multiple columns by specifying them in the `ORDER BY` clause. Sorting is applied in the order the columns are listed.

#### Example:

To sort employees by department in ascending order and by age in descending order:

```sql
SELECT *
FROM employees
ORDER BY department ASC, age DESC;
```

**Result:**

| id | name       | age | department |
|----|------------|-----|------------|
| 1  | John Doe   | 30  | HR         |
| 3  | Sam Brown  | 35  | Marketing  |
| 2  | Jane Smith | 25  | IT         |

---

### Practice Exercises 🖋️

1. Retrieve all rows from the `employees` table and sort them by `name` in ascending order.
2. Sort the `employees` table by `department` in descending order.
3. Combine sorting by `age` in ascending order and `department` in alphabetical order.
4. Create a query to sort a new table `products` by `price` in descending order and `stock_quantity` in ascending order.

---

### Summary 🎯

Today, you learned:

- How to use the `ORDER BY` clause to sort data.
- Sorting data in ascending (`ASC`) and descending (`DESC`) orders.
- Sorting by multiple columns for complex queries.

Practice these concepts to solidify your understanding. Tomorrow, we'll dive into **aggregate functions and grouping data with GROUP BY**. Stay curious! 🚀

---

[Previous: Day 3 - Filtering Data with WHERE](./day3.md) 🔼\
[Next: Day 5 - Aggregate Functions and GROUP BY](./day5.md) 🔽


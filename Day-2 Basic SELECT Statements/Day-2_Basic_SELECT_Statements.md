# Day 2: CREATE Statement and Basic SELECT Statements 🎉

Welcome to Day 2 of the 30-Day SQL Challenge! Today, we'll cover the fundamental SQL `CREATE` statement used to define and create tables, and the `SELECT` statement to retrieve data from a database. 🚀

---

## Table of Contents 📚

1. [What is the CREATE Statement?](#what-is-the-create-statement)
2. [Creating Your First Table](#creating-your-first-table)
3. [What is the SELECT Statement?](#what-is-the-select-statement)
4. [Basic Syntax of SELECT](#basic-syntax-of-select)
5. [Using SELECT with Simple Queries](#using-select-with-simple-queries)
6. [Practice Exercises](#practice-exercises)
7. [Summary](#summary)

---

### What is the CREATE Statement? 🏗️

The `CREATE` statement is used to define new database objects such as tables, views, indexes, or databases. For today, we’ll focus on creating tables.

### Basic Syntax of CREATE TABLE 🛠️

```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);
```

- **`column1, column2`**: The names of the columns.
- **`datatype`**: The data type for each column (e.g., `INT`, `VARCHAR`, `DATE`).
- **`constraints`**: Optional rules like `PRIMARY KEY` or `NOT NULL`.

### Creating Your First Table 🎓

Let’s create a table named `students`:

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    age INT,
    enrollment_date DATE
);
```

- **`student_id`**: An integer that uniquely identifies each student.
- **`name`**: A string of up to 100 characters.
- **`age`**: An integer representing the student’s age.
- **`enrollment_date`**: A date indicating when the student enrolled.

### What is the SELECT Statement? 🧐

The `SELECT` statement is the backbone of SQL queries. It allows you to retrieve data from one or more tables in a database. By specifying columns or using special symbols like `*`, you can determine exactly what data you want to retrieve.

### Basic Syntax of SELECT 🛠️

```sql
SELECT column1, column2, ...
FROM table_name;
```

- **`column1, column2, ...`**: The columns you want to retrieve.
- **`table_name`**: The table from which you want to retrieve the data.

To retrieve all columns, use `*`:

```sql
SELECT *
FROM table_name;
```

### Using SELECT with Simple Queries 🤓

Imagine a table named `employees`:

| id | name       | age | department |
| -- | ---------- | --- | ---------- |
| 1  | John Doe   | 30  | HR         |
| 2  | Jane Smith | 25  | IT         |
| 3  | Sam Brown  | 35  | Marketing  |

1. Retrieve all columns:

```sql
SELECT *
FROM employees;
```

2. Retrieve specific columns:

```sql
SELECT name, age
FROM employees;
```

### Practice Exercises 📝

1. Write a `CREATE TABLE` statement to create a new table named `products` with the following structure:
   - `product_id` (integer, primary key)
   - `product_name` (string, maximum 50 characters, cannot be null)
   - `price` (decimal with 2 decimal places)
   - `stock_quantity` (integer)
2. Insert some sample data into the `students` table you created.
3. Write a `SELECT` query to retrieve only the `name` and `department` columns from the `employees` table.
4. Use `SELECT` to retrieve all rows from your `students` table.

### Summary 🏁

Today, you learned about:

- The `CREATE` statement for defining and creating tables.
- Writing basic `CREATE TABLE` queries.
- The `SELECT` statement and its syntax for retrieving data.
- Using `SELECT` with specific columns and `*`.

Tomorrow, we’ll dive deeper into **filtering data with the WHERE clause**. 🌟

---

[Previous: Day 1 - Introduction to SQL](./day1.md) 🔙\
[Next: Day 3 - Filtering Data with WHERE](./day3.md) 🔜


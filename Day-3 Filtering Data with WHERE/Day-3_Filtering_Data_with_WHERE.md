# Day 3: Filtering Data with WHERE Clause 🌟

Welcome to Day 3 of the 30-Day SQL Challenge! Today, we'll focus on filtering data using the `WHERE` clause, one of the most essential tools for retrieving specific rows from a database table. 🚀

---

## Table of Contents 📒

1. [What is the WHERE Clause?](#what-is-the-where-clause)
2. [Basic Syntax of WHERE](#basic-syntax-of-where)
3. [Using WHERE with Comparison Operators](#using-where-with-comparison-operators)
4. [Combining Conditions with AND, OR, NOT](#combining-conditions-with-and-or-not)
5. [Using WHERE with Pattern Matching (LIKE)](#using-where-with-pattern-matching-like)
6. [Filtering NULL Values](#filtering-null-values)
7. [Practice Exercises](#practice-exercises)
8. [Summary](#summary)

---

### What is the WHERE Clause? 🔍

The `WHERE` clause is used in SQL to filter records that meet specific criteria. Without it, SQL queries would return all rows in the table, which might not be useful for large datasets.

---

### Basic Syntax of WHERE 🔧

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

- **`condition`**: Specifies the filter criteria. Rows that meet this condition will be included in the query results.

#### Example:
Retrieve employees aged 30 or above:

```sql
SELECT *
FROM employees
WHERE age >= 30;
```

---

### Using WHERE with Comparison Operators ⚙️

SQL provides several comparison operators for filtering data:

| **Operator** | **Description**               |
|--------------|-------------------------------|
| `=`          | Equal to                      |
| `<>` or `!=` | Not equal to                  |
| `>`          | Greater than                  |
| `<`          | Less than                     |
| `>=`         | Greater than or equal to      |
| `<=`         | Less than or equal to         |

#### Example:
Retrieve employees in the IT department:

```sql
SELECT *
FROM employees
WHERE department = 'IT';
```

---

### Combining Conditions with AND, OR, NOT ⚖️

You can combine multiple conditions using logical operators:

- **`AND`**: All conditions must be true.
- **`OR`**: At least one condition must be true.
- **`NOT`**: Negates a condition.

#### Example:
Retrieve employees aged above 25 in the HR department:

```sql
SELECT *
FROM employees
WHERE age > 25 AND department = 'HR';
```

Retrieve employees who are either in IT or Marketing:

```sql
SELECT *
FROM employees
WHERE department = 'IT' OR department = 'Marketing';
```

Retrieve employees not in the HR department:

```sql
SELECT *
FROM employees
WHERE NOT department = 'HR';
```

---

### Using WHERE with Pattern Matching (LIKE) 🔄

The `LIKE` operator is used for pattern matching in SQL. It supports two wildcards:

- `%`: Matches zero or more characters.
- `_`: Matches exactly one character.

#### Example:
Retrieve employees whose names start with 'J':

```sql
SELECT *
FROM employees
WHERE name LIKE 'J%';
```

Retrieve employees whose names contain 'Smith':

```sql
SELECT *
FROM employees
WHERE name LIKE '%Smith%';
```

---

### Filtering NULL Values 🏠

To filter rows with `NULL` values, use the `IS NULL` or `IS NOT NULL` operators.

#### Example:
Retrieve employees without a specified department:

```sql
SELECT *
FROM employees
WHERE department IS NULL;
```

Retrieve employees with a specified department:

```sql
SELECT *
FROM employees
WHERE department IS NOT NULL;
```

---

### Practice Exercises 📘

1. Retrieve all employees whose age is less than 30.
2. Find employees in the `Marketing` department or aged 35 and above.
3. Retrieve employees whose names end with the letter 'n'.
4. List employees who do not belong to the `IT` department.
5. Retrieve employees with non-NULL `age` values.

---

### Summary 🏁

Today, you learned about:

- The purpose and syntax of the `WHERE` clause.
- Using comparison operators for filtering.
- Combining conditions with logical operators (`AND`, `OR`, `NOT`).
- Pattern matching with `LIKE`.
- Filtering `NULL` values.

Tomorrow, we’ll explore **sorting data with the ORDER BY clause**. Stay tuned! 🚀

---

[Previous: Day 2 - CREATE Statement and Basic SELECT](./day2.md) 🔼\
[Next: Day 4 - Sorting Data with ORDER BY](./day4.md) 🔽


# Day 11: Set Operations in SQL ✨

Welcome to Day 11 of the 30 Days of SQL Challenge! Today, we delve into **Set Operations** — a powerful way to combine query results in SQL. Mastering set operations will significantly enhance your ability to work with complex datasets. Let’s begin! 🚀

---

## Table of Contents 📖

1. [What are Set Operations?](#what-are-set-operations)
2. [Types of Set Operations](#types-of-set-operations)
   - [UNION](#union)
   - [UNION ALL](#union-all)
   - [INTERSECT](#intersect)
   - [EXCEPT (MINUS)](#except-minus)
3. [Examples of Set Operations](#examples-of-set-operations)
4. [Practice Exercises](#practice-exercises)
5. [Summary](#summary)

---

## What are Set Operations? 🔎

Set operations allow you to combine results from two or more `SELECT` statements. These operations treat query results as sets and perform operations like union, intersection, and difference.

### Key Points:

- All queries involved in a set operation must have the same number of columns.
- The columns must have compatible data types.
- Column order matters.

---

## Types of Set Operations 🛠️

### 1. UNION

Combines the results of two queries and removes duplicate rows.

**Syntax:**
```sql
SELECT column1, column2 FROM table1
UNION
SELECT column1, column2 FROM table2;
```

---

### 2. UNION ALL

Combines the results of two queries but **includes duplicates**.

**Syntax:**
```sql
SELECT column1, column2 FROM table1
UNION ALL
SELECT column1, column2 FROM table2;
```

---

### 3. INTERSECT

Returns rows that are **common** to both queries.

**Syntax:**
```sql
SELECT column1, column2 FROM table1
INTERSECT
SELECT column1, column2 FROM table2;
```

---

### 4. EXCEPT (or MINUS in some systems)

Returns rows from the first query that are **not present** in the second query.

**Syntax:**
```sql
SELECT column1, column2 FROM table1
EXCEPT
SELECT column1, column2 FROM table2;
```

---

## Examples of Set Operations 🔢

### Example 1: UNION

**Scenario:** Combine employees from two different departments.

```sql
SELECT name FROM department_a
UNION
SELECT name FROM department_b;
```

**Result:**

| name     |
|----------|
| Alice    |
| Bob      |
| Carol    |

---

### Example 2: UNION ALL

**Scenario:** Combine employees, but include duplicate names.

```sql
SELECT name FROM department_a
UNION ALL
SELECT name FROM department_b;
```

**Result:**

| name     |
|----------|
| Alice    |
| Bob      |
| Alice    |

---

### Example 3: INTERSECT

**Scenario:** Find employees working in both departments.

```sql
SELECT name FROM department_a
INTERSECT
SELECT name FROM department_b;
```

**Result:**

| name     |
|----------|
| Alice    |

---

### Example 4: EXCEPT

**Scenario:** Find employees in department A but not in department B.

```sql
SELECT name FROM department_a
EXCEPT
SELECT name FROM department_b;
```

**Result:**

| name     |
|----------|
| Bob      |

---

## Practice Exercises 🔧

1. Given `orders_2023` and `orders_2024`, find all unique customers who placed orders in either year.
2. Find customers who placed orders in both `orders_2023` and `orders_2024`.
3. Retrieve products listed in `products_2023` but not in `products_2024`.
4. Combine two sales tables and include duplicate entries.
5. Write a query to find employees who work in two specific projects using `INTERSECT`.

---

## Summary 🏁

Today, you learned about:

- The four types of set operations: `UNION`, `UNION ALL`, `INTERSECT`, and `EXCEPT`.
- How to use set operations to combine query results.
- Practical scenarios where set operations can simplify complex queries.

Tomorrow, we’ll dive into **String Functions** — an exciting topic to manipulate and analyze text data! Stay tuned! 🚀

---

[Previous: Day 10 - Subqueries in SQL](../Day-10%20Subqueries%20in%20SQL/Day-10_Subqueries_in_SQL.md) 🔼  
[Next: Day 12 - String Functions in SQL](../Day-12%20String%20Functions%20in%20SQL/Day-12_String_Functions_in_SQL.md) 🔽


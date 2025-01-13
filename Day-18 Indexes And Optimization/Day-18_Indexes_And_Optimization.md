📘 30 Days Of SQL: Day 18 - Indexes and Query Optimization

Welcome to Day 18 of the 30 Days of SQL challenge! 🎉 Today, we’ll explore how to use indexes to boost query performance and the art of query optimization. These techniques are essential for making your SQL queries efficient and scalable.

---

### Table of Contents

- [🔎 Overview](#-overview)
- [📘 Understanding Indexes](#-understanding-indexes)
  - [1. Types of Indexes](#1-types-of-indexes)
  - [2. How Indexes Work](#2-how-indexes-work)
  - [3. Creating and Managing Indexes](#3-creating-and-managing-indexes)
- [🔧 Query Optimization Techniques](#-query-optimization-techniques)
  - [1. Analyzing Query Plans](#1-analyzing-query-plans)
  - [2. Avoiding Common Pitfalls](#2-avoiding-common-pitfalls)
  - [3. Optimizing Joins and Subqueries](#3-optimizing-joins-and-subqueries)
- [🔄 Best Practices for Indexing](#-best-practices-for-indexing)
- [🔟 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises - Day 18](#-exercises---day-18)
- [🗳️ Day 18 Summary](#-day-18-summary)


---

### 🔎 Overview

Indexes are data structures that improve the speed of data retrieval. However, they come at a cost: increased storage and slower write operations. Effective query optimization involves leveraging indexes and writing efficient queries.

---

### 📘 Understanding Indexes

#### 1. Types of Indexes

- **Primary Index**: Automatically created on primary keys.
- **Unique Index**: Ensures unique values in the indexed column(s).
- **Clustered Index**: Sorts and stores data rows in the table based on the key values.
- **Non-Clustered Index**: Stores pointers to the actual data rows.
- **Composite Index**: Indexes multiple columns.
- **Full-Text Index**: Optimized for text search.

#### 2. How Indexes Work

Indexes are like a book’s table of contents. Instead of scanning the entire table, the database uses the index to find rows faster.

**Example Without Index**:

```sql
SELECT *
FROM orders
WHERE customer_id = 12345;
```

**Example With Index**:

```sql
CREATE INDEX idx_customer_id ON orders(customer_id);
SELECT *
FROM orders
WHERE customer_id = 12345;
```

#### 3. Creating and Managing Indexes

**Creating an Index**:

```sql
CREATE INDEX idx_column_name ON table_name(column_name);
```

**Dropping an Index**:

```sql
DROP INDEX idx_column_name;
```

**Viewing Existing Indexes** (PostgreSQL Example):

```sql
SELECT *
FROM pg_indexes
WHERE tablename = 'table_name';
```

---

### 🔧 Query Optimization Techniques

#### 1. Analyzing Query Plans

Use the `EXPLAIN` keyword to understand how the database executes a query.

**Example**:

```sql
EXPLAIN SELECT *
FROM orders
WHERE order_date > '2024-01-01';
```

#### 2. Avoiding Common Pitfalls

- **Avoid SELECT ***: Specify only required columns.
- **Index Usage**: Ensure indexes are used for filtering and joining.
- **Avoid Functions on Indexed Columns**:

```sql
-- Avoid
SELECT *
FROM orders
WHERE YEAR(order_date) = 2024;

-- Use
SELECT *
FROM orders
WHERE order_date >= '2024-01-01' AND order_date < '2025-01-01';
```

#### 3. Optimizing Joins and Subqueries

- Use indexed columns in `JOIN` conditions.
- Avoid unnecessary subqueries; use `WITH` (CTEs) where applicable.

**Example**:

```sql
-- Inefficient Subquery
SELECT *
FROM orders
WHERE customer_id IN (
    SELECT customer_id
    FROM customers
    WHERE country = 'USA'
);

-- Optimized Query
WITH US_Customers AS (
    SELECT customer_id
    FROM customers
    WHERE country = 'USA'
)
SELECT *
FROM orders
JOIN US_Customers
ON orders.customer_id = US_Customers.customer_id;
```

---

### 🔄 Best Practices for Indexing

- **Index Selectively**: Index columns frequently used in `WHERE`, `JOIN`, or `ORDER BY` clauses.
- **Monitor Index Usage**: Use query execution plans to ensure indexes are utilized.
- **Avoid Over-Indexing**: Too many indexes can degrade performance for `INSERT`, `UPDATE`, and `DELETE` operations.
- **Regular Maintenance**: Rebuild or reorganize fragmented indexes.

---

### 🔟 Hands-On Challenge

1. Create a non-clustered index on the `order_date` column of the `orders` table and measure query performance with and without the index.
2. Use `EXPLAIN` to analyze a query and identify optimization opportunities.
3. Optimize a query using a composite index.

---

### 💻 Exercises - Day 18

#### ✅ Exercise: Level 1

1. Create an index on the `customer_id` column of the `orders` table.
2. Use `EXPLAIN` to compare query plans for a query with and without an index.
3. Write a query to find all orders placed in 2024, and optimize it using an index.

#### 🚀 Exercise: Level 2

1. Implement a composite index on `customer_id` and `order_date` in the `orders` table. Write a query to retrieve orders for a specific customer within a date range.
2. Use a query plan to analyze the performance of a complex join query and suggest optimizations.
3. Create and use a full-text index to search for keywords in a `comments` column.

---

### 🗳️ Day 18 Summary

Today, we explored the importance of indexes and query optimization. By understanding different types of indexes and applying best practices, you can significantly improve query performance. Stay tuned for Day 19, where we’ll dive into Transactions and Concurrency Control! 🚀

---

[ Previous: Day 17 - Common Table Expressions (CTEs) ⬆️](../Day-17_Common_Table_Expressions/Day-17_Common_Table_Expressions.md)  
[ Next: Day 19 - Transactions and Concurrency Control ⬇️](../Day-19_Transactions_and_Concurrency/Day-19_Transactions_and_Concurrency.md)

---



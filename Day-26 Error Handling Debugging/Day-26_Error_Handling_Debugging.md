# 📘 30 Days Of SQL: Day 26 - Error Handling and Debugging in SQL

Welcome to **Day 26** of the **30 Days of SQL** challenge! 🎉 Today, we focus on an essential aspect of SQL development: **Error Handling and Debugging**. These skills ensure the robustness, reliability, and maintainability of your SQL code.

---

## Table of Contents

- [🔍 Overview](#-overview)
- [🚩 Common SQL Errors](#-common-sql-errors)
- [🔧 Techniques for Error Handling](#-techniques-for-error-handling)
  - [1. TRY...CATCH (SQL Server)](#1-trycatch-sql-server)
  - [2. EXCEPTION Handling (PostgreSQL)](#2-exception-handling-postgresql)
  - [3. DECLARE EXIT HANDLER (MySQL)](#3-declare-exit-handler-mysql)
- [🔍 Debugging SQL Queries](#-debugging-sql-queries)
- [🔑 Best Practices](#-best-practices)
- [🎯 Hands-On Challenge](#-hands-on-challenge)
- [📝 Day 26 Summary](#-day-26-summary)

---

## 🔍 Overview

SQL code often interacts with large datasets, complex business logic, and multiple users, which makes it susceptible to errors. Effective error handling and debugging:

- **Prevents crashes** or unexpected behavior.
- **Improves maintainability** by identifying root causes of errors quickly.
- **Enhances user experience** by providing clear feedback.

By understanding SQL error-handling mechanisms, you can build more robust and user-friendly systems.

---

## 🚩 Common SQL Errors

Here are some frequent errors you may encounter:

| **Error Type**               | **Description**                                                    | **Example**                                                                                     |
|------------------------------|--------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| **Syntax Errors**            | Errors due to incorrect SQL syntax.                              | `SELEC * FROM table_name;` (Misspelled `SELECT` keyword)                                        |
| **Constraint Violations**    | Errors due to primary key, foreign key, or unique constraints.    | Attempting to insert a duplicate value into a primary key column.                              |
| **Data Type Mismatch**       | Using incompatible data types in operations or assignments.       | Adding a string to a numeric column.                                                           |
| **Null Errors**              | Unexpected null values causing runtime errors.                   | `NULL` in calculations like `1 + NULL`.                                                        |
| **Deadlocks**                | Two or more processes blocking each other indefinitely.          | Concurrent updates to the same rows from different transactions.                               |
| **Timeouts**                 | Queries taking too long due to inefficient execution plans.       | Running an unoptimized query on a large table.                                                 |
| **Permission Denied Errors** | User lacks required privileges to execute a statement.           | Attempting to `DROP` a table without `DROP` privileges.                                        |

---

## 🔧 Techniques for Error Handling

### **1. TRY...CATCH (SQL Server)**

The `TRY...CATCH` construct allows you to handle errors gracefully in SQL Server.

**Syntax:**
```sql
BEGIN TRY
    -- Code that may cause an error
END TRY
BEGIN CATCH
    -- Handle the error
    SELECT ERROR_MESSAGE() AS ErrorMessage;
END CATCH;
```

**Example:**
```sql
BEGIN TRY
    INSERT INTO employees (id, name) VALUES (1, 'John');
END TRY
BEGIN CATCH
    SELECT ERROR_MESSAGE() AS ErrorMessage;
END CATCH;
```

### **2. EXCEPTION Handling (PostgreSQL)**

In PostgreSQL, `EXCEPTION` blocks allow you to catch and handle errors.

**Syntax:**
```sql
DO $$
BEGIN
    -- Code that may cause an error
EXCEPTION WHEN others THEN
    -- Handle the error
    RAISE NOTICE 'An error occurred: %', SQLERRM;
END;
$$ LANGUAGE plpgsql;
```

**Example:**
```sql
DO $$
BEGIN
    INSERT INTO employees (id, name) VALUES (1, 'John');
EXCEPTION WHEN unique_violation THEN
    RAISE NOTICE 'Duplicate entry detected';
END;
$$ LANGUAGE plpgsql;
```

### **3. DECLARE EXIT HANDLER (MySQL)**

MySQL uses `DECLARE EXIT HANDLER` to handle errors in stored procedures.

**Syntax:**
```sql
DECLARE EXIT HANDLER FOR SQLEXCEPTION
BEGIN
    -- Handle the error
END;
```

**Example:**
```sql
DELIMITER //
CREATE PROCEDURE InsertEmployee()
BEGIN
    DECLARE EXIT HANDLER FOR SQLEXCEPTION
    BEGIN
        SELECT 'An error occurred';
    END;

    INSERT INTO employees (id, name) VALUES (1, 'John');
END;//
DELIMITER ;
```

---

## 🔍 Debugging SQL Queries

Debugging involves identifying and fixing errors in SQL code. Here are some tips:

### **1. Use EXPLAIN Plans**
Analyze query execution plans to identify bottlenecks.
```sql
EXPLAIN SELECT * FROM large_table WHERE condition;
```

### **2. Log Errors**
Use logs to capture error details for later analysis.

### **3. Divide and Conquer**
Break down complex queries into smaller parts and test each part.

### **4. Check for Data Issues**
Verify that the data matches your assumptions (e.g., no unexpected `NULL` values).

---

## 🔑 Best Practices

1. **Handle Specific Errors**: Address specific error types for clearer debugging.
2. **Validate Inputs**: Ensure user inputs are sanitized and validated.
3. **Use Transactions**: Combine error handling with transactions to maintain data integrity.
4. **Test for Edge Cases**: Test your code with boundary conditions and invalid inputs.
5. **Monitor Performance**: Use monitoring tools to identify and fix slow queries.

---

## 🎯 Hands-On Challenge

1. Write a stored procedure in MySQL that handles duplicate key errors using `DECLARE EXIT HANDLER`.
2. Use `TRY...CATCH` in SQL Server to catch and log errors during an `INSERT` operation.
3. Debug a query by analyzing its execution plan and rewriting it for better performance.

---

## 📝 Day 26 Summary

Today, you learned how to handle errors and debug SQL code effectively. These skills are critical for building reliable, maintainable, and user-friendly database applications.

In **Day 27**, we’ll explore **SQL Security**, including user roles, permissions, and best practices for securing your database. Stay tuned! 🚀

[Previous: Day 25 - SQL for Analytics](../Day-25%20SQL%20For%20Analytics/Day-25_SQL_For_Analytics.md) 🔼  
[Next: Day 27 - SQL Security](../Day-27%20SQL%20Security/Day-27_SQL_Security.md) 🔽


# 📘 30 Days Of SQL: Day 23 - Triggers and Events

Welcome to **Day 23** of the **30 Days of SQL** challenge! 🎉 Today, we will explore **Triggers and Events** in SQL, powerful tools for automating actions and maintaining data integrity in your databases.

---

## Table of Contents

- [🔍 Overview](#-overview)
- [📘 What are Triggers?](#-what-are-triggers)
  - [1. Types of Triggers](#1-types-of-triggers)
  - [2. Syntax of Triggers](#2-syntax-of-triggers)
- [⚡ Events in SQL](#-events-in-sql)
  - [1. What are Events?](#1-what-are-events)
  - [2. Creating and Managing Events](#2-creating-and-managing-events)
- [💡 Practical Examples](#-practical-examples)
- [🔧 Best Practices](#-best-practices)
- [🎯 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises - Day 23](#-exercises---day-23)
- [📝 Day 23 Summary](#-day-23-summary)

---

## 🔍 Overview

**Triggers** are database objects that execute automatically in response to certain events, such as `INSERT`, `UPDATE`, or `DELETE` operations on a table. They help enforce business rules, maintain audit trails, and automate processes.

**Events** in SQL are scheduled actions executed by the database server at specified times or intervals. They are useful for automating routine tasks like backups, archiving, or cleanup operations.

---

## 📘 What are Triggers?

### 1. Types of Triggers

| **Trigger Type**        | **Description**                                         |
|-------------------------|---------------------------------------------------------|
| `BEFORE` Trigger        | Executes before the triggering SQL operation.           |
| `AFTER` Trigger         | Executes after the triggering SQL operation.            |
| `INSTEAD OF` Trigger    | Replaces the triggering SQL operation (used in views).  |

### 2. Syntax of Triggers

**General Syntax**:

```sql
CREATE TRIGGER trigger_name
{ BEFORE | AFTER | INSTEAD OF } { INSERT | UPDATE | DELETE }
ON table_name
[FOR EACH ROW]
BEGIN
    -- Trigger logic
END;
```

**Example**: Log every new employee added to the `employees` table.

```sql
CREATE TRIGGER log_new_employee
AFTER INSERT
ON employees
FOR EACH ROW
BEGIN
    INSERT INTO employee_logs (employee_id, action, timestamp)
    VALUES (NEW.id, 'INSERT', CURRENT_TIMESTAMP);
END;
```

---

## ⚡ Events in SQL

### 1. What are Events?

Events allow you to execute predefined actions at specific intervals or times. They are often used for maintenance tasks.

### 2. Creating and Managing Events

**General Syntax**:

```sql
CREATE EVENT event_name
ON SCHEDULE { AT timestamp | EVERY interval }
DO
BEGIN
    -- Event logic
END;
```

**Example**: Clean up old records from the `logs` table every day.

```sql
CREATE EVENT daily_log_cleanup
ON SCHEDULE EVERY 1 DAY
DO
BEGIN
    DELETE FROM logs WHERE log_date < NOW() - INTERVAL 30 DAY;
END;
```

---

## 💡 Practical Examples

### Example 1: Audit Trail with Triggers

Log every deletion from the `orders` table.

```sql
CREATE TRIGGER log_order_deletion
AFTER DELETE
ON orders
FOR EACH ROW
BEGIN
    INSERT INTO order_logs (order_id, action, timestamp)
    VALUES (OLD.id, 'DELETE', CURRENT_TIMESTAMP);
END;
```

### Example 2: Automatic Backup with Events

Create a backup of the `customers` table every week.

```sql
CREATE EVENT weekly_customer_backup
ON SCHEDULE EVERY 1 WEEK
DO
BEGIN
    CREATE TABLE customers_backup AS SELECT * FROM customers;
END;
```

---

## 🔧 Best Practices

1. **Keep Trigger Logic Simple**: Avoid complex logic to minimize performance overhead.
2. **Use Events Sparingly**: Overusing events can lead to resource contention.
3. **Monitor and Test**: Regularly test triggers and events to ensure they work as intended.
4. **Document Your Triggers and Events**: Maintain clear documentation for better maintenance.

---

## 🎯 Hands-On Challenge

1. Create a trigger to log updates to a `products` table.
2. Schedule an event to archive data from a `sales` table every month.
3. Write a trigger to prevent deletion of important rows in the `users` table.

---

## 💻 Exercises - Day 23

### ✅ Exercise: Level 1

1. Write a `BEFORE INSERT` trigger to validate data before inserting into the `orders` table.
2. Create an event to delete records older than 60 days from the `sessions` table.

### 🚀 Exercise: Level 2

1. Write an `AFTER UPDATE` trigger to track changes in the `inventory` table.
2. Schedule an event to optimize all tables in the database every week.

---

## 📝 Day 23 Summary

Today, you learned about **Triggers** and **Events** in SQL, two powerful mechanisms to automate actions and maintain data integrity. These tools are vital for optimizing database operations and implementing business logic directly at the database level.

Stay tuned for **Day 24**, where we’ll dive into **Data Import and Export**! 🚀

[Previous: Day 22 - Stored Procedures and Functions](../Day-22%20Stored%20Procedures%20And%20Functions/Day-22_Stored_Procedures_And_Functions.md) 🔼  
[Next: Day 24 - Data Import and Export](../Day-24%20Data%20Import%20and%20Export/Day-24_Data_Import_and_Export.md) 🔽


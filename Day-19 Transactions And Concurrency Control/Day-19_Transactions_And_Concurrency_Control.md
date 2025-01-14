📘 30 Days Of SQL: Day 19 - Transactions and Concurrency Control

Welcome to Day 19 of the 30 Days of SQL challenge! 🎉 Today, we explore transactions and concurrency control, two critical concepts for ensuring data integrity and consistency in multi-user database environments.

---

### Table of Contents

- [🔍 Overview](#-overview)
- [📘 Transactions](#-transactions)
  - [1. Properties (ACID)](#1-properties-acid)
  - [2. Commands (BEGIN, COMMIT, ROLLBACK, SAVEPOINT)](#2-commands-begin-commit-rollback-savepoint)
- [💡 Concurrency Control](#-concurrency-control)
  - [1. Isolation Levels](#1-isolation-levels)
  - [2. Locking Mechanisms](#2-locking-mechanisms)
- [🔧 Best Practices](#-best-practices)
- [🎯 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises - Day 19](#-exercises---day-19)
- [📝 Day 19 Summary](#-day-19-summary)


---

### 🔍 Overview

A transaction is a sequence of one or more SQL operations executed as a single logical unit of work. Concurrency control ensures that multiple users can access the database simultaneously without conflicts or data inconsistencies. Together, these concepts form the foundation for reliable database operations.

---

### 📘 Transactions

#### 1. Properties of Transactions (ACID)

Transactions adhere to the following properties:

- **Atomicity**: All operations in a transaction succeed or fail as a unit.
- **Consistency**: Transactions bring the database from one valid state to another.
- **Isolation**: Transactions are independent of one another.
- **Durability**: Once a transaction is committed, its changes persist even in the event of a system failure.

#### 2. Transaction Commands

- **`BEGIN`**: Starts a transaction.
- **`COMMIT`**: Saves all changes made in the transaction.
- **`ROLLBACK`**: Undoes all changes made in the transaction.
- **`SAVEPOINT`**: Creates a point within a transaction to which you can roll back.

**Example**:

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 500
WHERE account_id = 2;

COMMIT;
```

---

### 💡 Concurrency Control

#### 1. Isolation Levels

SQL defines four isolation levels to control the visibility of changes between transactions:

- **Read Uncommitted**: Transactions can see uncommitted changes from other transactions.
- **Read Committed**: Transactions see only committed changes from other transactions.
- **Repeatable Read**: Ensures consistent reads during a transaction.
- **Serializable**: Provides the highest level of isolation by fully locking the data.

**Setting Isolation Level**:

```sql
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
BEGIN;
-- Transaction code here
COMMIT;
```

#### 2. Locking Mechanisms

- **Shared Lock**: Allows multiple transactions to read a resource but not modify it.
- **Exclusive Lock**: Allows one transaction to modify a resource while preventing others from accessing it.
- **Deadlock**: Occurs when two or more transactions block each other.

---

### 🔧 Best Practices

- **Minimize Lock Time**: Keep transactions short to avoid locking resources for extended periods.
- **Use Proper Isolation Levels**: Choose isolation levels based on application needs.
- **Avoid Deadlocks**: Ensure transactions access resources in a consistent order.
- **Test Thoroughly**: Simulate concurrent transactions to detect potential conflicts.

---

### 🎯 Hands-On Challenge

1. Write a transaction to transfer funds between accounts with proper error handling.
2. Test different isolation levels and observe their impact on concurrent transactions.
3. Create a scenario where deadlocks occur and resolve them.
4. Implement a transaction with multiple savepoints and rollbacks.

---

### 💻 Exercises - Day 19

#### ✅ Exercise: Level 1

1. Write a transaction to update stock levels and commit the changes.
2. Create a savepoint during a transaction and roll back to it.
3. Demonstrate the use of the `ROLLBACK` command in case of an error.

#### 🚀 Exercise: Level 2

1. Simulate concurrent transactions accessing the same resource with different isolation levels.
2. Write a query to detect and resolve a deadlock scenario.
3. Implement a series of transactions to maintain a consistent state in a sales database.

---

### 📝 Day 19 Summary

Today, we covered transactions and concurrency control, exploring their role in maintaining database integrity and handling multi-user environments. With this knowledge, you can create robust, error-resilient SQL applications.

Stay tuned for Day 20, where we’ll tackle Advanced SQL Practice and Quizzes! 🚀

---
⬆️ Previous: [Day 18 - Indexes and Query Optimization](../Day-18_Indexes_and_Optimization/Day-18_Indexes_and_Optimization.md)  
⬇️ Next: [Day 20 - Advanced SQL Practice and Quiz](../Day-20_Advanced_SQL_Practice/Day-20_Advanced_SQL_Practice.md)

---

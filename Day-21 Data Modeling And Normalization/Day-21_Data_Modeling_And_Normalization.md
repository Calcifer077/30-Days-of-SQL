# 📘 30 Days Of SQL: Day 21 - Data Modeling and Normalization

Welcome to **Day 21** of the **30 Days of SQL** challenge! 🎉 Today, we’ll focus on **data modeling** and **normalization**, essential techniques for designing efficient and scalable databases. Understanding these concepts ensures a strong foundation for database integrity, performance, and flexibility.

---

## Table of Contents

- [🔍 Overview](#-overview)
- [📈 Data Modeling Basics](#-data-modeling-basics)
  - [1. Conceptual Model](#1-conceptual-model)
  - [2. Logical Model](#2-logical-model)
  - [3. Physical Model](#3-physical-model)
- [🔄 Normalization Principles](#-normalization-principles)
  - [1. First Normal Form (1NF)](#1-first-normal-form-1nf)
  - [2. Second Normal Form (2NF)](#2-second-normal-form-2nf)
  - [3. Third Normal Form (3NF)](#3-third-normal-form-3nf)
  - [4. Boyce-Codd Normal Form (BCNF)](#4-boyce-codd-normal-form-bcnf)
- [🔧 Best Practices](#-best-practices)
- [🎨 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises - Day 21](#-exercises---day-21)
- [🖋️ Day 21 Summary](#-day-21-summary)

---

## 🔍 Overview

Data modeling and normalization are crucial for:

- Designing logical and efficient database schemas.
- Minimizing redundancy and preventing anomalies.
- Improving data consistency and integrity.
- Optimizing database performance and scalability.

---

## 📈 Data Modeling Basics

Data modeling is the process of defining and organizing a database structure. It involves three main stages:

### 1. Conceptual Model

- **Purpose**: Represents the overall structure of the database at a high level, focusing on entities and relationships.
- **Components**: Entities, attributes, relationships.
- **Tools**: Entity-Relationship Diagrams (ERDs).

Example:

```
Customer (CustomerID, Name, Email)
Orders (OrderID, Date, Amount, CustomerID)
Relationship: One Customer places many Orders.
```

### 2. Logical Model

- **Purpose**: Translates the conceptual model into a detailed structure, defining tables, columns, data types, and constraints.
- **Components**: Tables, columns, primary and foreign keys.

Example:
```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100) UNIQUE
);

CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    Date DATE,
    Amount DECIMAL(10, 2),
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

### 3. Physical Model

- **Purpose**: Focuses on implementing the logical model on a specific database management system (DBMS).
- **Considerations**: Indexing, partitioning, and performance optimization.

Example:
```sql
CREATE INDEX idx_customer_email ON Customers (Email);
```

---

## 🔄 Normalization Principles

Normalization organizes data into tables to minimize redundancy and improve data integrity. Here are the key normal forms:

### 1. First Normal Form (1NF)

- **Definition**: Ensures all columns contain atomic (indivisible) values.
- **Rules**:
  - Each column must contain only one value.
  - Each row must be unique.

**Example**:

Non-1NF Table:
| CustomerID | Name      | PhoneNumbers       |
|------------|-----------|--------------------|
| 1          | Alice     | 123-456, 987-654  |

1NF Table:
| CustomerID | Name      | PhoneNumber |
|------------|-----------|-------------|
| 1          | Alice     | 123-456     |
| 1          | Alice     | 987-654     |

### 2. Second Normal Form (2NF)

- **Definition**: Ensures no partial dependency exists (i.e., no attribute depends only on part of a composite primary key).
- **Prerequisite**: Must satisfy 1NF.

**Example**:

Non-2NF Table:
| OrderID | ProductID | ProductName | Quantity |
|---------|-----------|-------------|----------|
| 101     | 1         | Laptop      | 2        |

2NF Table:
| OrderID | ProductID | Quantity |
|---------|-----------|----------|
| 101     | 1         | 2        |

| ProductID | ProductName |
|-----------|-------------|
| 1         | Laptop      |

### 3. Third Normal Form (3NF)

- **Definition**: Removes transitive dependency (i.e., no non-key attribute depends on another non-key attribute).
- **Prerequisite**: Must satisfy 2NF.

**Example**:

Non-3NF Table:
| CustomerID | Name  | City      | State |
|------------|-------|-----------|-------|
| 1          | Alice | New York | NY    |

3NF Table:
| CustomerID | Name  | CityID |
|------------|-------|--------|
| 1          | Alice | 101    |

| CityID | City      | State |
|--------|-----------|-------|
| 101    | New York  | NY    |

### 4. Boyce-Codd Normal Form (BCNF)

- **Definition**: Ensures every determinant is a candidate key.
- **Prerequisite**: Must satisfy 3NF.

**Example**:

Non-BCNF Table:
| StudentID | CourseID | Instructor |
|-----------|----------|------------|
| 1         | Math101  | Dr. Smith  |
| 2         | Math101  | Dr. Smith  |

BCNF Table:
| CourseID | Instructor |
|----------|------------|
| Math101  | Dr. Smith  |

| StudentID | CourseID |
|-----------|----------|
| 1         | Math101  |
| 2         | Math101  |

---

## 🔧 Best Practices

1. **Plan Ahead**: Invest time in creating a robust conceptual model.
2. **Normalize to an Appropriate Level**: Over-normalization can impact performance.
3. **Document Your Models**: Use tools like ERDs for clear communication.
4. **Monitor Performance**: Use indexes and optimize queries when necessary.

---

## 🎨 Hands-On Challenge

1. **Conceptual Model**: Design an ERD for an e-commerce platform with Customers, Products, Orders, and Reviews.
2. **Logical Model**: Write SQL scripts to create normalized tables for the above scenario.
3. **Normalization**: Normalize the following table into 3NF:

| OrderID | CustomerName | ProductName | City      |
|---------|--------------|-------------|-----------|
| 101     | Alice        | Laptop      | New York  |
| 102     | Bob          | Tablet      | San Diego |

---

## 💻 Exercises - Day 21

### ✅ Exercise: Level 1

1. Normalize the following table to 1NF:

| EmployeeID | Name       | Departments         |
|------------|------------|---------------------|
| 1          | John Smith | HR, Finance         |

2. Create an ERD for a library database with Books, Authors, Members, and Loans.

### 🚀 Exercise: Level 2

1. Write SQL scripts to create tables for the library database in 3NF.
2. Design a physical model for optimizing query performance for book searches.

---

## 🖋 Day 21 Summary

Today, you learned about **data modeling** and **normalization**, key techniques for designing efficient and scalable databases. Practice these principles to build robust and high-performing databases.

Stay tuned for **Day 22**, where we’ll dive into **Stored Procedures and Functions**! 🚀

[Previous: Day 20 - Advanced SQL Practice and Quiz](../Day-20%20Advanced%20SQL%20Practice%20And%20Quiz/Day-20_Advanced_SQL_Practice_And_Quiz.md) 🔼  
[Next: Day 22 - Stored Procedures and Functions](../Day-22%20Stored%20Procedures%20And%20Functions/Day-22_Stored_Procedures_And_Functions.md) 🔽


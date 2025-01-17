# 📘 30 Days Of SQL: Day 22 - Stored Procedures and Functions

Welcome to **Day 22** of the **30 Days of SQL** challenge! 🎉 Today, we’ll focus on stored procedures and functions, which are essential tools for encapsulating reusable SQL logic. These features enable you to modularize your code, improve performance, and enforce business rules within your database.

---

## Table of Contents

- [🔍 Overview](#-overview)
- [📚 Key Concepts](#-key-concepts)
  - [1. What Are Stored Procedures?](#1-what-are-stored-procedures)
  - [2. What Are Functions?](#2-what-are-functions)
- [📊 Practical Examples](#-practical-examples)
  - [1. Creating a Stored Procedure](#1-creating-a-stored-procedure)
  - [2. Creating a Function](#2-creating-a-function)
- [🔧 Best Practices](#-best-practices)
- [🔢 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises - Day 22](#-exercises---day-22)
- [🖋️ Day 22 Summary](#-day-22-summary)

---

## 🔍 Overview

Stored procedures and functions allow you to group SQL statements into reusable blocks of code. They can accept input parameters, execute complex logic, and return results—making them indispensable for creating robust, efficient, and maintainable database systems.

---

## 📚 Key Concepts

### 1. What Are Stored Procedures?

Stored procedures are precompiled SQL routines that can perform a series of operations. They are commonly used for:

- Encapsulating business logic.
- Reducing network traffic by running multiple statements in one execution.
- Enhancing security by controlling access to underlying data.

**Syntax (General):**
```sql
CREATE PROCEDURE procedure_name (
    IN param1 DataType,
    OUT param2 DataType
)
BEGIN
    -- SQL statements
END;
```

### 2. What Are Functions?

Functions are similar to stored procedures but are designed to return a single value. They are typically used for:

- Calculations or transformations.
- Reusability in SELECT or WHERE clauses.
- Enforcing consistent logic.

**Syntax (General):**
```sql
CREATE FUNCTION function_name (
    param1 DataType,
    param2 DataType
) RETURNS ReturnType
BEGIN
    -- SQL statements
    RETURN value;
END;
```

---

## 📊 Practical Examples

### 1. Creating a Stored Procedure

Suppose we want to create a procedure to update employee salaries by a given percentage:

```sql
DELIMITER //
CREATE PROCEDURE UpdateSalaries (
    IN department_id INT,
    IN percentage DECIMAL(5, 2)
)
BEGIN
    UPDATE employees
    SET salary = salary + (salary * percentage / 100)
    WHERE dept_id = department_id;
END //
DELIMITER ;
```

**Usage:**
```sql
CALL UpdateSalaries(5, 10.0); -- Increase salaries by 10% for department 5
```

### 2. Creating a Function

Let’s create a function to calculate the annual bonus for employees based on their salary:

```sql
DELIMITER //
CREATE FUNCTION CalculateBonus (
    base_salary DECIMAL(10, 2),
    bonus_percentage DECIMAL(5, 2)
) RETURNS DECIMAL(10, 2)
BEGIN
    RETURN base_salary * bonus_percentage / 100;
END //
DELIMITER ;
```

**Usage:**
```sql
SELECT CalculateBonus(salary, 15.0) AS annual_bonus FROM employees;
```

---

## 🔧 Best Practices

1. **Use Descriptive Names**: Clearly indicate the purpose of the procedure or function.
2. **Limit Complexity**: Keep logic straightforward and modular.
3. **Document Parameters**: Provide comments describing input and output parameters.
4. **Error Handling**: Include error checks to handle unexpected inputs or database states.
5. **Test Thoroughly**: Validate with various edge cases to ensure reliability.

---

## 🔢 Hands-On Challenge

1. Write a stored procedure to archive old orders based on a cutoff date.
2. Create a function to calculate the total order value, including tax, for a given order ID.
3. Design a procedure to log changes to a specific table in an audit log.

---

## 💻 Exercises - Day 22

### ✅ Exercise: Level 1

1. Write a stored procedure to increase the stock of a product by a specified amount.
2. Create a function to compute the square of a number.
3. Write a procedure to fetch and print employee details for a given department ID.

### 🚀 Exercise: Level 2

1. Create a function to calculate the compound interest for a given principal, rate, and time.
2. Write a stored procedure to back up rows from one table to another before deleting them.
3. Design a function to return the full name of an employee by concatenating their first and last names.

---

## 🖋️ Day 22 Summary

Today, you learned how to:

- Define and use stored procedures to encapsulate SQL logic.
- Create and use functions for reusable computations.
- Follow best practices to ensure maintainable and efficient database code.

Stored procedures and functions are powerful tools for optimizing SQL workflows. Up next: **Day 23 - Triggers and Events**! 🚀

[Previous: Day 21 - Data Modeling and Normalization](../Day-21%20Data%20Modeling%20And%20Normalization/Day-21_Data_Modeling_And_Normalization.md) 🔼  
[Next: Day 23 - Triggers and Events](../Day-23%20Triggers%20And%20Events/Day-23_Triggers_And_Events.md) 🔽


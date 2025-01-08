# Day 13: Date and Time Functions in SQL 🌐

Welcome to Day 13 of the 30-Day SQL Challenge! Today, we dive into one of the most versatile aspects of SQL—**Date and Time Functions**. These functions help you manipulate and analyze temporal data effectively, enabling powerful query capabilities. ⏳

---

## Table of Contents 📖

1. [What are Date and Time Functions?](#what-are-date-and-time-functions)
2. [Commonly Used Date and Time Functions](#commonly-used-date-and-time-functions)
3. [Examples of Date and Time Functions](#examples-of-date-and-time-functions)
4. [Practice Exercises](#practice-exercises)
5. [Summary](#summary)

---

### What are Date and Time Functions? ❓

Date and Time functions in SQL are built-in operations that allow you to extract, modify, and compute data from temporal columns. These functions are essential for working with schedules, logs, reports, and other time-sensitive data.

---

### Commonly Used Date and Time Functions ⏰

Here are some of the most frequently used Date and Time functions:

| **Function**         | **Description**                                                   |
|----------------------|-------------------------------------------------------------------|
| `CURRENT_DATE`       | Returns the current date.                                         |
| `CURRENT_TIME`       | Returns the current time.                                         |
| `NOW()`              | Returns the current date and time.                               |
| `DATE()`             | Extracts the date part from a `DATETIME` value.                  |
| `TIME()`             | Extracts the time part from a `DATETIME` value.                  |
| `YEAR()`             | Extracts the year from a date.                                    |
| `MONTH()`            | Extracts the month from a date.                                   |
| `DAY()`              | Extracts the day of the month from a date.                       |
| `DATEDIFF()`         | Returns the number of days between two dates.                    |
| `DATE_ADD()`         | Adds a specified time interval to a date.                        |
| `DATE_SUB()`         | Subtracts a specified time interval from a date.                 |
| `DATE_FORMAT()`      | Formats a date according to a specified pattern.                 |
| `TIMESTAMPDIFF()`    | Returns the difference between two timestamps in a chosen unit.  |

---

### Examples of Date and Time Functions 🔧

#### Example 1: Get the Current Date and Time

```sql
SELECT CURRENT_DATE AS today, CURRENT_TIME AS current_time, NOW() AS current_datetime;
```
**Result:**

| today      | current_time | current_datetime       |
|------------|--------------|------------------------|
| 2024-12-28 | 15:45:00     | 2024-12-28 15:45:00    |

---

#### Example 2: Extract Parts of a Date

```sql
SELECT YEAR(NOW()) AS year, MONTH(NOW()) AS month, DAY(NOW()) AS day;
```
**Result:**

| year | month | day |
|------|-------|-----|
| 2024 | 12    | 28  |

---

#### Example 3: Calculate Date Differences

```sql
SELECT DATEDIFF('2025-01-01', '2024-12-28') AS days_difference;
```
**Result:**

| days_difference |
|-----------------|
| 4               |

---

#### Example 4: Add and Subtract Dates

```sql
SELECT
    DATE_ADD('2024-12-28', INTERVAL 7 DAY) AS next_week,
    DATE_SUB('2024-12-28', INTERVAL 1 MONTH) AS last_month;
```
**Result:**

| next_week  | last_month  |
|------------|-------------|
| 2024-01-04 | 2024-11-28  |

---

#### Example 5: Format Dates

```sql
SELECT DATE_FORMAT('2024-12-28', '%W, %M %d, %Y') AS formatted_date;
```
**Result:**

| formatted_date        |
|-----------------------|
| Saturday, December 28, 2024 |

---

### Practice Exercises ⚖️

1. Write a query to find the day of the week for the date `2024-12-25`.
2. Calculate the number of days between your birthday and today.
3. Add 3 months to the current date and display the result.
4. Extract the year, month, and day from the timestamp `2023-11-15 08:45:30`.
5. Format the current date in the pattern: `DD-MM-YYYY`.

---

### Summary 🏁

Today, we learned:

- The purpose of Date and Time functions.
- Commonly used SQL functions for temporal data.
- Practical examples and how to manipulate dates and times in queries.

Tomorrow, we’ll explore **Intermediate Practice and Quiz** to consolidate our knowledge. Keep practicing, and see you tomorrow! ✨

---

[Previous: Day 12 - String Functions](../Day-12%20String%20Functions/Day-12_String_Functions.md) 🔼

[Next: Day 14 - Intermediate Practice and Quiz](../Day-14%20Intermediate%20Practice%20and%20Quiz/Day-14_Intermediate_Practice_and_Quiz.md) 🔽


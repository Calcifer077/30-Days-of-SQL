# Day 12: String Functions in SQL 🎉

Welcome to Day 12 of the 30-Day SQL Challenge! Today, we’ll explore string functions in SQL—powerful tools for manipulating and processing textual data. Let’s dive in! 🚀

---

## Table of Contents 📖

1. [Introduction to String Functions](#introduction-to-string-functions-)
2. [Commonly Used String Functions](#commonly-used-string-functions-)
   - [UPPER and LOWER](#upper-and-lower)
   - [LENGTH/CHAR_LENGTH](#lengthchar_length)
   - [TRIM](#trim)
   - [SUBSTRING/SUBSTR](#substringsubstr)
   - [CONCAT](#concat)
   - [REPLACE](#replace)
   - [INSTR](#instr)
3. [Advanced String Functions](#advanced-string-functions-)
   - [LEFT and RIGHT](#left-and-right)
   - [LPAD and RPAD](#lpad-and-rpad)
   - [REVERSE](#reverse)
4. [Practical Examples](#practical-examples-)
5. [Practice Exercises](#practice-exercises-)
6. [Summary](#summary-)

---

### Introduction to String Functions 🔍

String functions are used to manipulate or retrieve information from string data. Whether you’re cleaning up messy data, extracting meaningful parts of text, or formatting strings for reporting, SQL string functions are indispensable.

---

### Commonly Used String Functions 🆒

#### UPPER and LOWER
- Convert text to uppercase or lowercase.

```sql
SELECT UPPER('hello') AS uppercase, LOWER('WORLD') AS lowercase;
```
**Result:**

| uppercase | lowercase |
|-----------|-----------|
| HELLO     | world     |

#### LENGTH/CHAR_LENGTH
- Find the length of a string.

```sql
SELECT LENGTH('hello world') AS length;
```
**Result:**

| length |
|--------|
| 11     |

#### TRIM
- Remove leading or trailing spaces (or specified characters).

```sql
SELECT TRIM('   hello   ') AS trimmed;
```
**Result:**

| trimmed |
|---------|
| hello   |

#### SUBSTRING/SUBSTR
- Extract a portion of a string.

```sql
SELECT SUBSTRING('hello world', 1, 5) AS substring;
```
**Result:**

| substring |
|-----------|
| hello     |

#### CONCAT
- Combine multiple strings into one.

```sql
SELECT CONCAT('hello', ' ', 'world') AS concatenated;
```
**Result:**

| concatenated |
|--------------|
| hello world  |

#### REPLACE
- Replace occurrences of a substring with another.

```sql
SELECT REPLACE('hello world', 'world', 'SQL') AS replaced;
```
**Result:**

| replaced    |
|-------------|
| hello SQL   |

#### INSTR
- Find the position of a substring within a string.

```sql
SELECT INSTR('hello world', 'world') AS position;
```
**Result:**

| position |
|----------|
| 7        |

---

### Advanced String Functions 🔬

#### LEFT and RIGHT
- Extract a specified number of characters from the start or end of a string.

```sql
SELECT LEFT('hello world', 5) AS left_part, RIGHT('hello world', 5) AS right_part;
```
**Result:**

| left_part | right_part |
|-----------|------------|
| hello     | world      |

#### LPAD and RPAD
- Pad a string to a certain length with a specified character.

```sql
SELECT LPAD('SQL', 5, '*') AS lpad, RPAD('SQL', 5, '*') AS rpad;
```
**Result:**

| lpad  | rpad  |
|-------|-------|
| **SQL | SQL** |

#### REVERSE
- Reverse the order of characters in a string.

```sql
SELECT REVERSE('SQL') AS reversed;
```
**Result:**

| reversed |
|----------|
| LQS      |

---

### Practical Examples 🌐

#### Example 1: Cleaning Up Data

Suppose you have a `users` table:

| id | username     |
|----|--------------|
| 1  |   Alice123   |
| 2  |   Bob456     |

To clean up whitespace and convert usernames to lowercase:

```sql
SELECT id, TRIM(LOWER(username)) AS cleaned_username
FROM users;
```
**Result:**

| id | cleaned_username |
|----|------------------|
| 1  | alice123         |
| 2  | bob456           |

#### Example 2: Extracting Domain from Email

Given a `contacts` table:

| id | email                |
|----|----------------------|
| 1  | alice@example.com    |
| 2  | bob@sqlchallenge.com |

To extract the domain:

```sql
SELECT id, SUBSTRING(email, INSTR(email, '@') + 1) AS domain
FROM contacts;
```
**Result:**

| id | domain              |
|----|---------------------|
| 1  | example.com         |
| 2  | sqlchallenge.com    |

---

### Practice Exercises 🏆

1. Write a query to convert all names in a `customers` table to uppercase.
2. Extract the first 3 characters of a `product_code` column from a `products` table.
3. Write a query to replace all spaces in an `address` column with underscores.
4. Find the position of the first occurrence of '@' in an `email` column.
5. Reverse the text in a `comments` column.

---

### Summary 🌟

Today, we covered:

- Common and advanced string functions like `UPPER`, `TRIM`, `SUBSTRING`, and `REVERSE`.
- Practical applications for cleaning and manipulating textual data.
- Examples and exercises to solidify your understanding.

Tomorrow, we’ll move on to **Date and Time Functions**! Stay tuned! 🚀

---

[Previous: Day 11 - Set Operations in SQL](../Day-11%20Set%20Operations/Day-11_Set_Operations.md) 🔼\
[Next: Day 13 - Date and Time Functions](../Day-13_Date-and-Time-Functions/Day-13_Date-and-Time-Functions.md) 🔽


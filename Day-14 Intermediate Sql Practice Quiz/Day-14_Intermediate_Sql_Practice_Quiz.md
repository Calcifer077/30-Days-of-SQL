# Day 14: Intermediate SQL Practice and Quiz 📚

Welcome to Day 14 of the 30-Day SQL Challenge! Today, you’ll consolidate your knowledge by solving **intermediate-level SQL problems** and testing your skills with a quiz. 🎯✨

---

## Table of Contents 🔖

1. [Practice Exercises](#practice-exercises-)
2. [Quiz Questions](#quiz-questions-)
3. [Answer Key](#answer-key-)
4. [Summary](#summary-)
---

### Practice Exercises 🔧

Here are some practice problems based on the SQL concepts you’ve learned so far:

#### Problem 1: Total Sales Per Region
Use the `sales` table to calculate total sales for each region and only include regions with sales greater than $10,000.

**Table: sales**

| salesperson | region | sales_amount |
|-------------|--------|--------------|
| Alice       | North  | 5000         |
| Bob         | South  | 7000         |
| Alice       | North  | 3000         |
| Bob         | South  | 2000         |
| Carol       | East   | 8000         |

**Expected Output:**

| region | total_sales |
|--------|-------------|
| South  | 12000       |

**Query:**
```sql
SELECT region, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY region
HAVING SUM(sales_amount) > 10000;
```

---

#### Problem 2: Average Score by Class
From a `students` table, find the average score for each class, but only include classes with an average score above 75.

**Table: students**

| class  | student_name | score |
|--------|--------------|-------|
| A      | John         | 85    |
| A      | Mary         | 90    |
| B      | Jake         | 70    |
| B      | Emily        | 75    |
| A      | Steve        | 95    |

**Expected Output:**

| class | average_score |
|-------|---------------|
| A     | 90.0          |

**Query:**
```sql
SELECT class, AVG(score) AS average_score
FROM students
GROUP BY class
HAVING AVG(score) > 75;
```

---

#### Problem 3: Customer Orders
Using an `orders` table, find customers who have placed more than 3 orders and whose total order value exceeds $5000.

**Table: orders**

| customer_id | order_id | order_total |
|-------------|----------|-------------|
| 1           | 101      | 2000        |
| 2           | 102      | 1500        |
| 1           | 103      | 3000        |
| 3           | 104      | 800         |
| 2           | 105      | 2000        |
| 1           | 106      | 1000        |

**Expected Output:**

| customer_id | total_orders | total_value |
|-------------|--------------|-------------|
| 1           | 3            | 6000        |

**Query:**
```sql
SELECT customer_id, COUNT(order_id) AS total_orders, SUM(order_total) AS total_value
FROM orders
GROUP BY customer_id
HAVING COUNT(order_id) > 3 AND SUM(order_total) > 5000;
```

---

### Quiz Questions 🕵️‍♂

Test your understanding with these questions:

#### Question 1: Identify Invalid Queries
Which of the following queries will result in an error?

1. ```sql
   SELECT region, SUM(sales_amount)
   FROM sales
   GROUP BY region
   HAVING SUM(sales_amount) > 10000;
   ```
2. ```sql
   SELECT region
   FROM sales
   HAVING SUM(sales_amount) > 10000;
   ```
3. ```sql
   SELECT region, AVG(sales_amount)
   FROM sales
   GROUP BY region
   HAVING AVG(sales_amount) > 4000;
   ```

#### Question 2: True or False
The `HAVING` clause can only be used with aggregate functions.

- [ ] True
- [ ] False

#### Question 3: Fill in the Blanks
Complete the query to find regions with total sales greater than $15,000:

```sql
SELECT region, ________(sales_amount) AS total_sales
FROM sales
GROUP BY region
HAVING ________(sales_amount) > 15000;
```

---

### Answer Key 🔐

#### Question 1: Identify Invalid Queries
- Answer: Query 2 will result in an error because the `HAVING` clause requires a `GROUP BY` clause.

#### Question 2: True or False
- Answer: True

#### Question 3: Fill in the Blanks
- Answer:

```sql
SELECT region, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY region
HAVING SUM(sales_amount) > 15000;
```

---

### Summary 🌟

Today, you practiced intermediate SQL concepts and tested your understanding with quizzes. These exercises are designed to reinforce your skills and prepare you for more advanced topics. Keep up the great work! 🏋️‍♂️

[Previous: Day 13 - Date and Time Functions](./Day-13%20Date%20And%20Time%20Functions/Day-13_Date_And_Time_Functions.md) 🔼  
[Next: Day 15 - Advanced Aggregate Functions](./Day-15%20Advanced%20Aggregate%20Functions/Day-15_Advanced_Aggregate_Functions.md) 🔽


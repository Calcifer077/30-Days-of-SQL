# Day 7: SQL Practice and Quiz 🎯

Welcome to Day 7 of the 30-Day SQL Challenge! Today, we’ll consolidate our learning from the past six days with practice problems and a quiz. Let’s sharpen your SQL skills with hands-on tasks and challenging questions. ⚡️

---

## Table of Contents 📚

1. [Practice Problems](#practice-problems)
2. [Quiz Questions](#quiz-questions)
3. [Solutions](#solutions)
4. [Next Steps](#next-steps)

---

### Practice Problems 🏋️‍♂️

#### Problem 1: Total Sales by Region

Given the following `sales` table:

| salesperson | region     | sales_amount |
|-------------|------------|--------------|
| Alice       | North      | 5000         |
| Bob         | South      | 7000         |
| Alice       | North      | 3000         |
| Bob         | South      | 2000         |
| Carol       | East       | 8000         |

**Task:** Write a query to find the total sales for each region.

---

#### Problem 2: Average Score by Class

Given the following `students` table:

| class  | student_name | score |
|--------|--------------|-------|
| A      | John         | 85    |
| A      | Mary         | 90    |
| B      | Jake         | 70    |
| B      | Emily        | 75    |
| A      | Steve        | 95    |

**Task:** Write a query to find the average score for each class.

---

#### Problem 3: High-Selling Salespersons

Given the same `sales` table as Problem 1:

**Task:** Write a query to find salespersons with total sales greater than 8000.

---

#### Problem 4: Students with More Than One Entry

Given the `students` table:

**Task:** Write a query to find all students who appear more than once in the table.

---

### Quiz Questions 🎮

#### Question 1: Filtering with WHERE and HAVING

Which of the following statements is true?

- (A) `WHERE` filters rows before grouping, while `HAVING` filters groups after aggregation.
- (B) `HAVING` filters rows before grouping, while `WHERE` filters groups after aggregation.
- (C) Both `WHERE` and `HAVING` filter rows after grouping.
- (D) None of the above.

---

#### Question 2: Aggregation

What will the following query return?

```sql
SELECT region, COUNT(*) AS region_count
FROM sales
GROUP BY region;
```

- (A) The total number of regions.
- (B) The count of sales in each region.
- (C) The count of unique regions.
- (D) None of the above.

---

#### Question 3: Combining GROUP BY and HAVING

Given the following `orders` table:

| customer_id | order_amount |
|-------------|--------------|
| 1           | 100          |
| 2           | 200          |
| 1           | 300          |
| 2           | 400          |
| 3           | 500          |

What does this query return?

```sql
SELECT customer_id, SUM(order_amount) AS total_amount
FROM orders
GROUP BY customer_id
HAVING total_amount > 400;
```

- (A) Customers whose total orders exceed 400.
- (B) Customers with more than one order.
- (C) The total amount of all orders.
- (D) None of the above.

---

### Solutions 🕵️‍♂️

#### Practice Problems

1. **Total Sales by Region**:

```sql
SELECT region, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY region;
```

2. **Average Score by Class**:

```sql
SELECT class, AVG(score) AS average_score
FROM students
GROUP BY class;
```

3. **High-Selling Salespersons**:

```sql
SELECT salesperson, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY salesperson
HAVING total_sales > 10000;
```

4. **Students with More Than One Entry**:

```sql
SELECT student_name, COUNT(*) AS entry_count
FROM students
GROUP BY student_name
HAVING entry_count > 1;
```

---

#### Quiz Answers

1. **(A)**: `WHERE` filters rows before grouping, while `HAVING` filters groups after aggregation.
2. **(B)**: The count of sales in each region.
3. **(A)**: Customers whose total orders exceed 400.

---

### Next Steps 🔄

Great work today! Practice and quizzes help solidify your understanding. Tomorrow, we’ll dive into **Joins** and explore how to combine data from multiple tables. Stay tuned! 🎉

---

[Previous: Day 6 - The HAVING Clause](./day6.md) 🔼  \
[Next: Day 8 - Joins – Basics](./day8.md) 🔽


# 📘 30 Days Of SQL: Day 24 - Data Import and Export

Welcome to **Day 24** of the **30 Days of SQL** challenge! 🎉 Today, we’ll focus on a practical and essential topic in SQL: **Data Import and Export**. Whether you’re moving data between systems, creating backups, or loading large datasets, mastering these techniques will significantly enhance your database management skills.

---

## Table of Contents

- [🔍 Overview](#-overview)
- [📚 Importance of Data Import and Export](#-importance-of-data-import-and-export)
- [🔧 Tools and Techniques](#-tools-and-techniques)
  - [1. Importing Data](#1-importing-data)
  - [2. Exporting Data](#2-exporting-data)
- [📊 Data Formats and Examples](#-data-formats-and-examples)
  - [CSV Files](#csv-files)
  - [JSON Files](#json-files)
  - [SQL Dumps](#sql-dumps)
- [⚙️ Best Practices](#⚙️-best-practices)
- [🎯 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises - Day 24](#-exercises---day-24)
- [🖋️ Day 24 Summary](#-day-24-summary)

---

## 🔍 Overview

Data import and export are vital processes for:

- **Data Migration**: Moving data from one database to another.
- **Data Integration**: Combining data from multiple sources.
- **Backups**: Creating copies of your data for recovery purposes.
- **Analytics**: Preparing data for external analysis tools.

---

## 📚 Importance of Data Import and Export

Understanding how to effectively import and export data ensures:

- **Data Integrity**: Preventing loss or corruption during transfer.
- **Efficiency**: Automating repetitive tasks.
- **Compatibility**: Adapting data for different systems and formats.

---

## 🔧 Tools and Techniques

### 1. Importing Data

#### Using SQL Commands
- **MySQL**:
  ```sql
  LOAD DATA INFILE 'file_path.csv'
  INTO TABLE table_name
  FIELDS TERMINATED BY ','
  ENCLOSED BY '"'
  LINES TERMINATED BY '\n'
  IGNORE 1 ROWS;
  ```

- **PostgreSQL**:
  ```sql
  COPY table_name(column1, column2)
  FROM '/path/to/file.csv'
  DELIMITER ','
  CSV HEADER;
  ```

#### Using GUI Tools
Most database management systems (e.g., MySQL Workbench, pgAdmin) provide graphical interfaces to import data.

#### Using External Tools
- **ETL Tools**: Apache NiFi, Talend, Pentaho.
- **Command-Line Tools**: `mysqlimport`, `psql`.

### 2. Exporting Data

#### Using SQL Commands
- **MySQL**:
  ```sql
  SELECT * FROM table_name
  INTO OUTFILE 'file_path.csv'
  FIELDS TERMINATED BY ','
  ENCLOSED BY '"'
  LINES TERMINATED BY '\n';
  ```

- **PostgreSQL**:
  ```sql
  COPY table_name(column1, column2)
  TO '/path/to/file.csv'
  DELIMITER ','
  CSV HEADER;
  ```

#### Using GUI Tools
Export data through built-in database tools or external software like DBeaver.

#### Using External Tools
- **ETL Tools** for complex workflows.
- **Command-Line Tools**: `mysqldump`, `pg_dump`.

---

## 📊 Data Formats and Examples

### CSV Files
CSV (Comma-Separated Values) is one of the most common formats for data import/export.

#### Import Example (MySQL):
```sql
LOAD DATA INFILE 'data.csv'
INTO TABLE employees
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;
```

#### Export Example (PostgreSQL):
```sql
COPY employees TO '/path/to/employees.csv' DELIMITER ',' CSV HEADER;
```

### JSON Files
JSON (JavaScript Object Notation) is widely used for APIs and web applications.

#### Import Example (MongoDB):
```bash
mongoimport --db database_name --collection collection_name --file data.json
```

#### Export Example (MongoDB):
```bash
mongoexport --db database_name --collection collection_name --out data.json
```

### SQL Dumps
SQL dumps are complete backups of a database or table, including schema and data.

#### Export Example (MySQL):
```bash
mysqldump -u username -p database_name > backup.sql
```

#### Import Example (PostgreSQL):
```bash
psql -U username -d database_name -f backup.sql
```

---

## ⚙️ Best Practices

1. **Validate Data**: Ensure data matches the table structure before importing.
2. **Backup Before Import**: Always back up the database to avoid accidental overwrites.
3. **Use Transactions**: Wrap imports in transactions for error handling.
4. **Monitor Performance**: Optimize large imports using batch processing.
5. **Secure Sensitive Data**: Encrypt files during transfer and ensure proper access controls.

---

## 🎯 Hands-On Challenge

1. **Import CSV**: Import a `products.csv` file into a database table.
2. **Export JSON**: Export employee data into a JSON file.
3. **Backup and Restore**: Create a SQL dump of a database and restore it into another database.

---

## 💻 Exercises - Day 24

### ✅ Exercise: Level 1

1. Write a query to import sales data from a CSV file.
2. Export all customer records into a CSV file.
3. Create a SQL dump of the `inventory` table.

### 🚀 Exercise: Level 2

1. Import JSON data into a MongoDB collection and query it.
2. Use `mysqldump` to back up an entire database and restore it to a new environment.
3. Automate data import using a Python script.

---

## 🖋️ Day 24 Summary

Today, you learned how to import and export data in SQL, covering tools, techniques, and formats like CSV, JSON, and SQL dumps. These skills are crucial for data migration, backups, and integrations.

Stay tuned for **Day 25**, where we’ll explore **SQL for Analytics**! 🚀

[Previous: Day 23 - Triggers and Events](../Day-23%20Triggers%20And%20Events/Day-23_Triggers_And_Events.md) 🔼  
[Next: Day 25 - SQL for Analytics](../Day-25%20SQL%20For%20Analytics/Day-25_SQL_For_Analytics.md) 🔽


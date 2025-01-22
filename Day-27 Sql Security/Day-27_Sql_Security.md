# 📘 30 Days Of SQL: Day 27 - SQL Security

Welcome to **Day 27** of the **30 Days of SQL** challenge! 🎉 Today, we will explore the crucial topic of **SQL Security**, focusing on techniques and best practices to secure your database from unauthorized access and potential threats.

---

## Table of Contents

- [🔍 Overview](#-overview)
- [🔑 Authentication and Authorization](#-authentication-and-authorization)
  - [1. User Accounts and Roles](#1-user-accounts-and-roles)
  - [2. Granting and Revoking Permissions](#2-granting-and-revoking-permissions)
- [🔒 Securing Data](#-securing-data)
  - [1. Encryption](#1-encryption)
  - [2. Masking Sensitive Data](#2-masking-sensitive-data)
  - [3. Auditing and Logging](#3-auditing-and-logging)
- [🛡️ Protecting Against SQL Injection](#%EF%B8%8F-protecting-against-sql-injection)
- [💡 Best Practices](#-best-practices)
- [🎯 Hands-On Challenge](#-hands-on-challenge)
- [💻 Exercises - Day 27](#-exercises---day-27)
- [📝 Day 27 Summary](#-day-27-summary)

---

## 🔍 Overview

Securing your database is critical to maintaining the integrity, confidentiality, and availability of your data. SQL Security encompasses a wide range of practices, from authenticating users to encrypting sensitive data. By implementing these measures, you can safeguard your database from unauthorized access and malicious attacks.

---

## 🔑 Authentication and Authorization

### 1. User Accounts and Roles

User accounts and roles form the foundation of database security:

- **User Accounts**: Unique identifiers for individuals or applications accessing the database.
- **Roles**: Groups of permissions assigned to users to simplify management.

**Example** (Creating a user and assigning roles):
```sql
-- Create a user
CREATE USER 'report_user'@'localhost' IDENTIFIED BY 'secure_password';

-- Create a role and grant it permissions
CREATE ROLE data_analyst;
GRANT SELECT, INSERT ON database_name.* TO data_analyst;

-- Assign the role to the user
GRANT data_analyst TO 'report_user'@'localhost';
```

---

### 2. Granting and Revoking Permissions

Use `GRANT` and `REVOKE` statements to control user access:

**Grant Permissions**:
```sql
GRANT SELECT, UPDATE ON employees TO 'report_user'@'localhost';
```

**Revoke Permissions**:
```sql
REVOKE UPDATE ON employees FROM 'report_user'@'localhost';
```

---

## 🔒 Securing Data

### 1. Encryption

Encryption ensures sensitive data is stored and transmitted securely:

- **At Rest**: Encrypt data stored in tables.
- **In Transit**: Use SSL/TLS for secure communication between the database and clients.

**Example** (MySQL enabling SSL):
```bash
# In the MySQL configuration file (my.cnf):
[mysqld]
ssl-ca=/path/to/ca.pem
ssl-cert=/path/to/server-cert.pem
ssl-key=/path/to/server-key.pem
```

---

### 2. Masking Sensitive Data

Data masking obscures sensitive information, such as credit card numbers, from unauthorized users:

**Example**:
```sql
-- Partial masking
SELECT CONCAT(SUBSTRING(phone_number, 1, 3), '****', SUBSTRING(phone_number, 7)) AS masked_number
FROM users;
```

---

### 3. Auditing and Logging

Auditing tracks database activity for compliance and troubleshooting purposes:

**Enable Auditing**:
```sql
-- MySQL Audit Plugin
INSTALL PLUGIN audit_log SONAME 'audit_log.so';
SET GLOBAL audit_log_policy = 'ALL';
```

---

## 🛡️ Protecting Against SQL Injection

SQL injection is a common attack where malicious SQL code is injected into queries. Preventive measures include:

1. **Parameterized Queries**:
```sql
-- Example in Python
cursor.execute("SELECT * FROM users WHERE username = %s", (username,))
```

2. **Validating Input**:
   - Sanitize user inputs.
   - Reject unexpected characters.

3. **Limiting Privileges**:
   - Ensure applications only have the necessary permissions.

---

## 💡 Best Practices

1. Use strong, unique passwords for all database accounts.
2. Regularly audit and review user permissions.
3. Enable multi-factor authentication (MFA) where possible.
4. Regularly patch and update your database system.
5. Monitor for suspicious activity using logging and alerting tools.

---

## 🎯 Hands-On Challenge

1. **Create a Secure User**: Create a user account with limited permissions for a reporting tool.
2. **Enable Logging**: Configure database auditing and logging.
3. **Test Injection**: Attempt a SQL injection attack on a test database and secure it using parameterized queries.

---

## 💻 Exercises - Day 27

### ✅ Exercise: Level 1

1. Create a user with `SELECT` permissions on a specific table.
2. Enable SSL/TLS for a MySQL or PostgreSQL database.
3. Use `GRANT` and `REVOKE` to manage user permissions.

### 🚀 Exercise: Level 2

1. Implement data masking for sensitive fields in a sample table.
2. Enable and configure auditing to track database logins and changes.
3. Write a secure query to prevent SQL injection attacks.

---

## 📝 Day 27 Summary

Today, we covered essential topics in **SQL Security**, including authentication, authorization, encryption, and protection against SQL injection. These practices ensure the integrity and safety of your database. Tomorrow, we will wrap up the challenge with **Building a Real-World Project**! 🎉

[Previous: Day 26 - Error Handling and Debugging](../Day-26%20Error%20Handling%20And%20Debugging/Day-26_Error_Handling_And_Debugging.md) 🔼  
[Next: Day 28 - Building a Real-World Project](../Day-28%20Building%20a%20Real-World%20Project/Day-28_Building_a_Real-World_Project.md) 🔽


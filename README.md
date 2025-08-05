# SQL-JOINS-TASK3_CODTECH
# 📌 Internship Task3 – Database Migration (MySQL → PostgreSQL)

*Intern Name:* Aina Marziya  
*Internship Organization:* CODTECH  
*Task:* 3 
*Topic:* Data Migration from MySQL to PostgreSQL  
*Tools Used:* MySQL 8.0, PostgreSQL 14, DBeaver (or CLI), pgAdmin

## 🎯 Objective

To successfully migrate data from a MySQL database to PostgreSQL while maintaining data structure, consistency, and integrity.

## 🛠 STEP 1: MySQL Database Creation & Sample Data

### 🔹 Table: Customers (in MySQL)
```sql
CREATE TABLE Customers (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    country VARCHAR(50)
);

INSERT INTO Customers VALUES
(1, 'Alice', 'alice@example.com', 'India'),
(2, 'Bob', 'bob@example.com', 'USA'),
(3, 'Charlie', 'charlie@example.com', 'UK');

✅ This is the data we will migrate to PostgreSQL.

📦 STEP 2: Export Data from MySQL

You can export using:

Option A: CLI

mysqldump -u root -p mydb Customers > customers.sql

Option B: DBeaver / MySQL Workbench

Right-click table → Export Data → SQL INSERTs or CSV format

📥 STEP 3: Import into PostgreSQL

A. Create Same Table in PostgreSQL

CREATE TABLE Customers (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    country VARCHAR(50)
);

B. Import Data:

If CSV: Use pgAdmin's import tool or run:


COPY Customers FROM '/path/to/customers.csv' DELIMITER ',' CSV HEADER;

If SQL: Run the customers.sql file via psql:


psql -U postgres -d mydb -f customers.sql


🔐 STEP 4: Verify Data Integrity

Compare row counts in both databases:


SELECT COUNT(*) FROM Customers;

Check data sample:


SELECT * FROM Customers ORDER BY id;

✅ All 3 records should match exactly in both systems.


🔁 Optional Enhancements

Use tools like pgloader for automatic migration:


pgloader mysql://user:pass@localhost/mydb postgresql://user:pass@localhost/mydb


🧾 Summary

Step	Tool Used	Description

Export from MySQL	mysqldump / CSV	Exported Customers table
Import to PGSQL	psql / pgAdmin	Created table and loaded data
Verification	SQL Queries	Matched row count and sample records


✅ Conclusion
The migration from MySQL to PostgreSQL was successful. Data integrity was ensured by:
Using exact schema structures
Comparing row counts and values
Validating with manual queries

This approach can be reused for larger database migrations by batching tables and automating scripts.

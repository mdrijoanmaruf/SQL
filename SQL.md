# SQL Notes

## Database
A database is a collection of data stored in a digital format that can be easily accessed and managed. A **DBMS (Database Management System)** is software used to manage databases.

```sql
-- Example: Creating a database
CREATE DATABASE my_database;
```

---

## Types of Databases
### Relational Databases
Data is stored in tables with rows and columns. Examples include **MySQL**, **Oracle**, **SQL Server**, and **PostgreSQL**.

### Non-relational (NoSQL) Databases
Data is not stored in tables. Example: **MongoDB**.

```sql
-- Example: Relational databases use SQL to interact with data.
SELECT * FROM users;
```

---

## What is SQL?
**SQL (Structured Query Language)** is a programming language used to interact with relational databases. It is used to perform **CRUD** operations:
- **Create**: Insert data.
- **Read**: Retrieve data.
- **Update**: Modify data.
- **Delete**: Remove data.

```sql
-- Example: CRUD operations
INSERT INTO users (name, age) VALUES ('John', 25);  -- Create
SELECT * FROM users;                                -- Read
UPDATE users SET age = 26 WHERE name = 'John';      -- Update
DELETE FROM users WHERE name = 'John';              -- Delete
```

---

## Database Structure
A database consists of **tables**, and each table contains **rows** and **columns** to store data.

```sql
-- Example: Database structure
-- Database: school
-- Tables: students, teachers, courses
```

---

## What is a Table?
A table is a collection of related data organized in rows and columns. Each row represents a record, and each column represents a field.

```sql
-- Example: Student Table
CREATE TABLE student (
    RollNo INT PRIMARY KEY,
    Name VARCHAR(50),
    Class VARCHAR(10),
    DOB DATE,
    Gender CHAR(1),
    City VARCHAR(20),
    Marks INT
);
```

---

## Creating our First Database
You can create a database using the `CREATE DATABASE` command and delete it using `DROP DATABASE`.

```sql
-- Example: Create and drop a database
CREATE DATABASE my_database;
DROP DATABASE my_database;
```

---

## Creating our First Table
Tables are created using the `CREATE TABLE` command. Each column has a data type and optional constraints.

```sql
-- Example: Create a table
CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT NOT NULL
);
```

---

## SQL Datatypes
Datatypes define the type of data that can be stored in a column. Common datatypes include:
- **INT**: Integer values.
- **VARCHAR**: Variable-length strings.
- **DATE**: Date values.
- **BOOLEAN**: True/False values.

```sql
-- Example: Using datatypes
CREATE TABLE employee (
    id INT,
    name VARCHAR(50),
    hire_date DATE,
    is_active BOOLEAN
);
```

---

## Types of SQL Commands
SQL commands are categorized into:
- **DDL (Data Definition Language)**: Create, alter, and drop database objects.
- **DML (Data Manipulation Language)**: Insert, update, delete data.
- **DQL (Data Query Language)**: Retrieve data using `SELECT`.
- **DCL (Data Control Language)**: Grant or revoke permissions.
- **TCL (Transaction Control Language)**: Manage transactions.

```sql
-- Example: DDL (Create Table)
CREATE TABLE users (
    id INT PRIMARY KEY,
    name VARCHAR(50)
);

-- Example: DML (Insert Data)
INSERT INTO users (id, name) VALUES (1, 'Alice');
```

---

## Database Related Queries
Common database-related queries include creating, dropping, and showing databases.

```sql
-- Example: Database queries
CREATE DATABASE my_db;
DROP DATABASE my_db;
SHOW DATABASES;
```

---

## Table Related Queries
### Create Table
Tables are created using the `CREATE TABLE` command.

```sql
-- Example: Create a table
CREATE TABLE student (
    rollno INT PRIMARY KEY,
    name VARCHAR(50)
);
```

### Select & View All Columns
Use `SELECT *` to retrieve all columns from a table.

```sql
-- Example: Select all columns
SELECT * FROM student;
```

### Insert Data
Use `INSERT INTO` to add data to a table.

```sql
-- Example: Insert data
INSERT INTO student (rollno, name)
VALUES (101, 'Karan'), (102, 'Arjun');
```

---

## Keys
### Primary Key
A column (or set of columns) that uniquely identifies each row in a table. It cannot be NULL.

```sql
-- Example: Primary Key
CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(50)
);
```

### Foreign Key
A column that refers to the primary key of another table. It creates a relationship between two tables.

```sql
-- Example: Foreign Key
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    product_id INT,
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

---

## Constraints
Constraints enforce rules on data in a table. Common constraints include:
- **NOT NULL**: Ensures a column cannot have NULL values.
- **UNIQUE**: Ensures all values in a column are unique.
- **PRIMARY KEY**: Combines NOT NULL and UNIQUE.
- **FOREIGN KEY**: Links two tables.
- **CHECK**: Ensures values meet a specific condition.

```sql
-- Example: Constraints
CREATE TABLE employee (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INT CHECK (age >= 18)
);
```

---

## Sample Table Creation
Here’s an example of creating a table and inserting data.

```sql
-- Example: Create and insert data
CREATE TABLE student (
    rollno INT PRIMARY KEY,
    name VARCHAR(50),
    marks INT NOT NULL,
    grade VARCHAR(1),
    city VARCHAR(20)
);

INSERT INTO student (rollno, name, marks, grade, city)
VALUES (101, 'Anil', 78, 'C', 'Pune'),
       (102, 'Bhumika', 93, 'A', 'Mumbai');
```

---

## Select in Detail
The `SELECT` statement retrieves data from a table.

```sql
-- Example: Select specific columns
SELECT name, marks FROM student;
```

---

## Where Clause
The `WHERE` clause filters records based on a condition.

```sql
-- Example: Where clause
SELECT * FROM student WHERE marks > 80;
```

---

## Operators in WHERE Clause
Operators are used to define conditions in the `WHERE` clause:
- **Arithmetic Operators**: +, -, *, /, %
- **Comparison Operators**: =, !=, >, <, >=, <=
- **Logical Operators**: AND, OR, NOT, IN, BETWEEN

```sql
-- Example: Using operators
SELECT * FROM student WHERE marks > 80 AND city = 'Mumbai';
```

---

## Limit Clause
The `LIMIT` clause restricts the number of rows returned.

```sql
-- Example: Limit clause
SELECT * FROM student LIMIT 3;
```

---

## Order By Clause
The `ORDER BY` clause sorts the result set in ascending or descending order.

```sql
-- Example: Order by clause
SELECT * FROM student ORDER BY marks DESC;
```

---

## Aggregate Functions
Aggregate functions perform calculations on a set of values and return a single value. Common functions include:
- **COUNT()**: Counts the number of rows.
- **MAX()**: Returns the maximum value.
- **MIN()**: Returns the minimum value.
- **SUM()**: Returns the sum of values.
- **AVG()**: Returns the average value.

```sql
-- Example: Aggregate functions
SELECT AVG(marks) FROM student;
```

---

## Group By Clause
The `GROUP BY` clause groups rows that have the same values into summary rows.

```sql
-- Example: Group by clause
SELECT city, COUNT(name) FROM student GROUP BY city;
```

---

## Having Clause
The `HAVING` clause filters groups based on a condition. It is used after `GROUP BY`.

```sql
-- Example: Having clause
SELECT city, COUNT(name) FROM student GROUP BY city HAVING COUNT(name) > 1;
```

---

## General Order of SQL Queries
The general order of SQL queries is:
1. **SELECT**: Choose columns.
2. **FROM**: Specify the table.
3. **WHERE**: Filter rows.
4. **GROUP BY**: Group rows.
5. **HAVING**: Filter groups.
6. **ORDER BY**: Sort the result.

```sql
-- Example: General order
SELECT city, COUNT(name) FROM student WHERE marks > 80 GROUP BY city HAVING COUNT(name) > 1 ORDER BY city;
```

---

## Update Query
The `UPDATE` statement modifies existing records in a table.

```sql
-- Example: Update query
UPDATE student SET grade = 'A' WHERE marks > 90;
```

---

## Delete Query
The `DELETE` statement removes records from a table.

```sql
-- Example: Delete query
DELETE FROM student WHERE marks < 33;
```

---

## Cascading for Foreign Key
Cascading ensures that changes in the parent table are reflected in the child table.

```sql
-- Example: Cascading
CREATE TABLE student (
    id INT PRIMARY KEY,
    courseID INT,
    FOREIGN KEY (courseID) REFERENCES course(id) ON DELETE CASCADE
);
```

---

## Alter Table
The `ALTER TABLE` statement modifies the structure of a table.

```sql
-- Example: Alter table
ALTER TABLE student ADD COLUMN age INT;
ALTER TABLE student DROP COLUMN age;
```

---

## Truncate Table
The `TRUNCATE TABLE` statement deletes all data from a table but keeps the structure.

```sql
-- Example: Truncate table
TRUNCATE TABLE student;
```

---

## Joins in SQL
Joins combine rows from two or more tables based on a related column.

### Types of Joins
- **Inner Join**: Returns matching rows from both tables.
- **Left Join**: Returns all rows from the left table and matching rows from the right table.
- **Right Join**: Returns all rows from the right table and matching rows from the left table.
- **Full Join**: Returns all rows when there is a match in either table.

```sql
-- Example: Inner Join
SELECT * FROM student INNER JOIN course ON student.id = course.student_id;
```

---

## Union
The `UNION` operator combines the result sets of two or more `SELECT` statements.

```sql
-- Example: Union
SELECT name FROM student UNION SELECT name FROM teacher;
```

---

## SQL Subqueries
A subquery is a query nested inside another query.

```sql
-- Example: Subquery
SELECT name FROM student WHERE marks > (SELECT AVG(marks) FROM student);
```

---

## MySQL Views
A view is a virtual table based on the result set of an SQL query.

```sql
-- Example: Create a view
CREATE VIEW top_students AS SELECT name, marks FROM student WHERE marks > 90;
SELECT * FROM top_students;
```


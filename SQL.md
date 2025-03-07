# SQL Notes

## Database
A **database** is a structured collection of data stored digitally. It allows for efficient data management, retrieval, and manipulation. A **DBMS (Database Management System)** is software that interacts with the database, allowing users to create, read, update, and delete data.

```sql
-- Example: Creating a database
CREATE DATABASE my_database;

-- Example: Dropping a database
DROP DATABASE my_database;
```

---

## Types of Databases
### Relational Databases
Relational databases store data in **tables** (rows and columns). Each table represents an entity, and relationships between tables are established using **keys**. Examples include **MySQL**, **Oracle**, **SQL Server**, and **PostgreSQL**.

### Non-relational (NoSQL) Databases
Non-relational databases store data in formats other than tables, such as key-value pairs, documents, or graphs. Example: **MongoDB**.

```sql
-- Example: Relational databases use SQL to interact with data.
SELECT * FROM users;  -- Retrieves all rows from the 'users' table.
```

---

## What is SQL?
**SQL (Structured Query Language)** is a programming language used to interact with relational databases. It is used to perform **CRUD** operations:
- **Create**: Insert data into a table.
- **Read**: Retrieve data from a table.
- **Update**: Modify existing data.
- **Delete**: Remove data from a table.

```sql
-- Example: CRUD operations
INSERT INTO users (name, age) VALUES ('John', 25);  -- Create
SELECT * FROM users;                                -- Read
UPDATE users SET age = 26 WHERE name = 'John';      -- Update
DELETE FROM users WHERE name = 'John';              -- Delete
```

---

## Database Structure
A database consists of **tables**, and each table contains **rows** (records) and **columns** (fields). Tables are related to each other using **keys**.

```sql
-- Example: Database structure
-- Database: school
-- Tables: students, teachers, courses
```

---

## What is a Table?
A **table** is a collection of related data organized in rows and columns. Each row represents a record, and each column represents a field (attribute).

```sql
-- Example: Student Table
CREATE TABLE student (
    RollNo INT PRIMARY KEY,      -- Unique identifier for each student
    Name VARCHAR(50),            -- Student's name
    Class VARCHAR(10),           -- Student's class
    DOB DATE,                    -- Date of birth
    Gender CHAR(1),              -- Gender (M/F)
    City VARCHAR(20),            -- City of residence
    Marks INT                    -- Marks obtained
);
```

---

## Creating our First Database
You can create a database using the `CREATE DATABASE` command and delete it using `DROP DATABASE`.

```sql
-- Example: Create a database
CREATE DATABASE my_database;

-- Example: Drop a database
DROP DATABASE my_database;
```

---

## Creating our First Table
Tables are created using the `CREATE TABLE` command. Each column has a **data type** and optional **constraints** (e.g., `PRIMARY KEY`, `NOT NULL`).

```sql
-- Example: Create a table
CREATE TABLE student (
    id INT PRIMARY KEY,          -- Primary key column
    name VARCHAR(50),            -- Student's name
    age INT NOT NULL             -- Age cannot be NULL
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
    id INT,                      -- Integer for employee ID
    name VARCHAR(50),            -- String for employee name
    hire_date DATE,              -- Date for hire date
    is_active BOOLEAN            -- Boolean for active status
);
```

---

## Types of SQL Commands
SQL commands are categorized into:
- **DDL (Data Definition Language)**: Create, alter, and drop database objects (e.g., `CREATE`, `ALTER`, `DROP`).
- **DML (Data Manipulation Language)**: Insert, update, delete data (e.g., `INSERT`, `UPDATE`, `DELETE`).
- **DQL (Data Query Language)**: Retrieve data using `SELECT`.
- **DCL (Data Control Language)**: Grant or revoke permissions (e.g., `GRANT`, `REVOKE`).
- **TCL (Transaction Control Language)**: Manage transactions (e.g., `COMMIT`, `ROLLBACK`).

```sql
-- Example: DDL (Create Table)
CREATE TABLE users (
    id INT PRIMARY KEY,          -- Primary key column
    name VARCHAR(50)             -- Name column
);

-- Example: DML (Insert Data)
INSERT INTO users (id, name) VALUES (1, 'Alice');  -- Insert a new row
```

---

## Database Related Queries
Common database-related queries include creating, dropping, and showing databases.

```sql
-- Example: Create a database
CREATE DATABASE my_db;

-- Example: Drop a database
DROP DATABASE my_db;

-- Example: Show all databases
SHOW DATABASES;
```

---

## Table Related Queries
### Create Table
Tables are created using the `CREATE TABLE` command.

```sql
-- Example: Create a table
CREATE TABLE student (
    rollno INT PRIMARY KEY,      -- Primary key column
    name VARCHAR(50)             -- Name column
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
VALUES (101, 'Karan'), (102, 'Arjun');  -- Insert multiple rows
```

---

## Keys
### Primary Key
A **primary key** is a column (or set of columns) that uniquely identifies each row in a table. It cannot be NULL.

```sql
-- Example: Primary Key
CREATE TABLE student (
    id INT PRIMARY KEY,          -- Primary key column
    name VARCHAR(50)             -- Name column
);
```

### Foreign Key
A **foreign key** is a column that refers to the primary key of another table. It creates a relationship between two tables.

```sql
-- Example: Foreign Key
CREATE TABLE orders (
    order_id INT PRIMARY KEY,    -- Primary key column
    product_id INT,              -- Foreign key column
    FOREIGN KEY (product_id) REFERENCES products(id)  -- Links to products table
);
```

---

## Constraints
Constraints enforce rules on data in a table. Common constraints include:
- **NOT NULL**: Ensures a column cannot have NULL values.
- **UNIQUE**: Ensures all values in a column are unique.
- **PRIMARY KEY**: Combines `NOT NULL` and `UNIQUE`.
- **FOREIGN KEY**: Links two tables.
- **CHECK**: Ensures values meet a specific condition.

```sql
-- Example: Constraints
CREATE TABLE employee (
    id INT PRIMARY KEY,          -- Primary key column
    name VARCHAR(50) NOT NULL,   -- Name cannot be NULL
    age INT CHECK (age >= 18)    -- Age must be 18 or older
);
```

---

## Sample Table Creation
Here’s an example of creating a table and inserting data.

```sql
-- Example: Create and insert data
CREATE TABLE student (
    rollno INT PRIMARY KEY,      -- Primary key column
    name VARCHAR(50),            -- Name column
    marks INT NOT NULL,          -- Marks column (cannot be NULL)
    grade VARCHAR(1),            -- Grade column
    city VARCHAR(20)             -- City column
);

-- Insert data into the table
INSERT INTO student (rollno, name, marks, grade, city)
VALUES (101, 'Anil', 78, 'C', 'Pune'),
       (102, 'Bhumika', 93, 'A', 'Mumbai');
```

---

## Select in Detail
The `SELECT` statement retrieves data from a table. You can select specific columns or all columns using `*`.

```sql
-- Example: Select specific columns
SELECT name, marks FROM student;

-- Example: Select all columns
SELECT * FROM student;
```

---

## Where Clause
The `WHERE` clause filters records based on a condition.

```sql
-- Example: Where clause
SELECT * FROM student WHERE marks > 80;  -- Retrieve students with marks > 80
```

---

## Operators in WHERE Clause
Operators are used to define conditions in the `WHERE` clause:
- **Arithmetic Operators**: +, -, *, /, %
- **Comparison Operators**: =, !=, >, <, >=, <=
- **Logical Operators**: AND, OR, NOT, IN, BETWEEN

```sql
-- Example: Using operators
SELECT * FROM student WHERE marks > 80 AND city = 'Mumbai';  -- Retrieve students with marks > 80 and from Mumbai
```

---

## Limit Clause
The `LIMIT` clause restricts the number of rows returned.

```sql
-- Example: Limit clause
SELECT * FROM student LIMIT 3;  -- Retrieve only 3 rows
```

---

## Order By Clause
The `ORDER BY` clause sorts the result set in ascending or descending order.

```sql
-- Example: Order by clause
SELECT * FROM student ORDER BY marks DESC;  -- Sort students by marks in descending order
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
SELECT AVG(marks) FROM student;  -- Calculate the average marks of all students
```

---

## Group By Clause
The `GROUP BY` clause groups rows that have the same values into summary rows.

```sql
-- Example: Group by clause
SELECT city, COUNT(name) FROM student GROUP BY city;  -- Count the number of students in each city
```

---

## Having Clause
The `HAVING` clause filters groups based on a condition. It is used after `GROUP BY`.

```sql
-- Example: Having clause
SELECT city, COUNT(name) FROM student GROUP BY city HAVING COUNT(name) > 1;  -- Retrieve cities with more than 1 student
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
UPDATE student SET grade = 'A' WHERE marks > 90;  -- Update grade to 'A' for students with marks > 90
```

---

## Delete Query
The `DELETE` statement removes records from a table.

```sql
-- Example: Delete query
DELETE FROM student WHERE marks < 33;  -- Delete students with marks < 33
```

---

## Cascading for Foreign Key
Cascading ensures that changes in the parent table are reflected in the child table.

```sql
-- Example: Cascading
CREATE TABLE student (
    id INT PRIMARY KEY,          -- Primary key column
    courseID INT,                -- Foreign key column
    FOREIGN KEY (courseID) REFERENCES course(id) ON DELETE CASCADE  -- Delete child rows when parent row is deleted
);
```

---

## Alter Table
The `ALTER TABLE` statement modifies the structure of a table.

```sql
-- Example: Alter table
ALTER TABLE student ADD COLUMN age INT;  -- Add a new column
ALTER TABLE student DROP COLUMN age;     -- Drop a column
```

---

## Truncate Table
The `TRUNCATE TABLE` statement deletes all data from a table but keeps the structure.

```sql
-- Example: Truncate table
TRUNCATE TABLE student;  -- Delete all rows from the 'student' table
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
SELECT * FROM student INNER JOIN course ON student.id = course.student_id;  -- Retrieve matching rows from both tables
```

---

## Union
The `UNION` operator combines the result sets of two or more `SELECT` statements.

```sql
-- Example: Union
SELECT name FROM student UNION SELECT name FROM teacher;  -- Combine names from student and teacher tables
```

---

## SQL Subqueries
A **subquery** is a query nested inside another query. It is used to perform complex queries.

```sql
-- Example: Subquery
SELECT name FROM student WHERE marks > (SELECT AVG(marks) FROM student);  -- Retrieve students with marks above the average
```

---

## MySQL Views
A **view** is a virtual table based on the result set of an SQL query. It simplifies complex queries and provides a layer of security.

```sql
-- Example: Create a view
CREATE VIEW top_students AS SELECT name, marks FROM student WHERE marks > 90;  -- Create a view for top students
SELECT * FROM top_students;  -- Retrieve data from the view
```


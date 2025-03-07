# SQL Notes

## Database
A database is a collection of data in a format that can be easily accessed (digital). A software application used to manage our database is called a DBMS (Database Management System).

## Types of Databases
### Relational
Data stored in tables. Examples include MySQL, Oracle, SQL Server, and PostgreSQL.

### Non-relational (NoSQL)
Data not stored in tables. Example: MongoDB.

## What is SQL?
SQL stands for Structured Query Language. It is a programming language used to interact with relational databases. It is used to perform CRUD operations:
- Create
- Read
- Update
- Delete

## Database Structure
- Database
  - Table 1
    - Data
  - Table 2
    - Data

## What is a Table?
### Example: Student Table
| RollNo | Name    | Class | DOB        | Gender | City   | Marks |
|--------|---------|-------|------------|--------|--------|-------|
| 1      | Nanda   | X     | 1995-06-06 | M      | Agra   | 551   |
| 2      | Saurabh | XII   | 1993-05-07 | M      | Mumbai | 462   |
| 3      | Sonal   | XI    | 1994-05-06 | F      | Delhi  | 400   |
| 4      | Trisla  | XII   | 1995-08-08 | F      | Mumbai | 450   |
| 5      | Store   | XII   | 1995-10-08 | M      | Delhi  | 369   |
| 6      | Marisla | XI    | 1994-12-12 | F      | Dubai  | 250   |
| 7      | Neha    | X     | 1995-12-08 | F      | Moscow | 377   |
| 8      | Mishant | X     | 1995-06-12 | M      | Moscow | 489   |

## Creating our First Database
```sql
CREATE DATABASE db_name;
DROP DATABASE db_name;
```

## Creating our First Table
```sql
USE db_name;

CREATE TABLE table_name (
    column_name1 datatype constraint,
    column_name2 datatype constraint,
    column_name3 datatype constraint
);

CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT NOT NULL
);
```

## SQL Datatypes
| DATATYPE | DESCRIPTION | USAGE |
|----------|-------------|-------|
| CHAR     | string(0-255), fixed length | CHAR(50) |
| VARCHAR  | string(0-255), up to given length | VARCHAR(50) |
| BLOB     | string(0-65535), binary large object | BLOB(1000) |
| INT      | integer(-2,147,483,648 to 2,147,483,647) | INT |
| TINYINT  | integer(-128 to 127) | TINYINT |
| BIGINT   | integer(-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807) | BIGINT |
| BIT      | x-bit values, x from 1 to 64 | BIT(2) |
| FLOAT    | Decimal number, precision to 23 digits | FLOAT |
| DOUBLE   | Decimal number, 24 to 53 digits | DOUBLE |
| BOOLEAN  | Boolean values 0 or 1 | BOOLEAN |
| DATE     | date in format YYYY-MM-DD | DATE |
| YEAR     | year in 4 digits format | YEAR |

## Types of SQL Commands
- **DDL (Data Definition Language)**: CREATE, ALTER, RENAME, TRUNCATE, DROP
- **DQL (Data Query Language)**: SELECT
- **DML (Data Manipulation Language)**: SELECT, INSERT, UPDATE, DELETE
- **DCL (Data Control Language)**: GRANT, REVOKE
- **TCL (Transaction Control Language)**: START TRANSACTION, COMMIT, ROLLBACK

## Database Related Queries
```sql
CREATE DATABASE db_name;
CREATE DATABASE IF NOT EXISTS db_name;
DROP DATABASE db_name;
DROP DATABASE IF EXISTS db_name;
SHOW DATABASES;
SHOW TABLES;
```

## Table Related Queries
### Create Table
```sql
CREATE TABLE table_name (
    column_name1 datatype constraint,
    column_name2 datatype constraint
);

CREATE TABLE student (
    rollno INT PRIMARY KEY,
    name VARCHAR(50)
);
```

### Select & View All Columns
```sql
SELECT * FROM table_name;
SELECT * FROM student;
```

### Insert Data
```sql
INSERT INTO table_name (col1, col2)
VALUES (val1, val2),
       (val3, val4);

INSERT INTO student (rollno, name)
VALUES (101, "karan"),
       (102, "arjun");
```

## Keys
### Primary Key
A column (or set of columns) in a table that uniquely identifies each row. There is only one primary key, and it should be NOT NULL.

### Foreign Key
A column (or set of columns) in a table that refers to the primary key in another table. There can be multiple foreign keys, and they can have duplicate and NULL values.

## Constraints
- **NOT NULL**: Columns cannot have a NULL value.
- **UNIQUE**: All values in the column are different.
- **PRIMARY KEY**: Makes a column unique and NOT NULL.
- **FOREIGN KEY**: Prevents actions that would destroy links between tables.
- **DEFAULT**: Sets the default value of a column.
- **CHECK**: Limits the values allowed in a column.

### Example Constraints
```sql
CREATE TABLE temp (
    id INT NOT NULL,
    PRIMARY KEY (id)
);

CREATE TABLE city (
    id INT PRIMARY KEY,
    city VARCHAR(50),
    age INT,
    CONSTRAINT age_check CHECK (age >= 18 AND city="Delhi")
);
```

## Sample Table Creation
```sql
CREATE DATABASE college;
USE college;

CREATE TABLE student (
    rollno INT PRIMARY KEY,
    name VARCHAR(50),
    marks INT NOT NULL,
    grade VARCHAR(1),
    city VARCHAR(20)
);

INSERT INTO student (rollno, name, marks, grade, city)
VALUES (101, "anil", 78, "C", "Pune"),
       (102, "bhumika", 93, "A", "Mumbai"),
       (103, "chetan", 85, "B", "Mumbai"),
       (104, "dhruv", 96, "A", "Delhi"),
       (105, "emanuel", 12, "F", "Delhi"),
       (106, "farah", 82, "B", "Delhi");
```

## Select in Detail
```sql
SELECT col1, col2 FROM table_name;
SELECT * FROM table_name;
```

## Where Clause
```sql
SELECT col1, col2 FROM table_name
WHERE condition;

SELECT * FROM student WHERE marks > 80;
SELECT * FROM student WHERE city = "Mumbai";
```

## Operators in WHERE Clause
- **Arithmetic Operators**: +, -, *, /, %
- **Comparison Operators**: =, !=, >, >=, <, <=
- **Logical Operators**: AND, OR, NOT, IN, BETWEEN, ALL, LIKE, ANY
- **Bitwise Operators**: &, |

### Example Operators
```sql
SELECT * FROM student WHERE marks > 80 AND city = "Mumbai";
SELECT * FROM student WHERE marks > 90 OR city = "Mumbai";
SELECT * FROM student WHERE marks BETWEEN 80 AND 90;
SELECT * FROM student WHERE city IN ("Delhi", "Mumbai");
SELECT * FROM student WHERE city NOT IN ("Delhi", "Mumbai");
```

## Limit Clause
```sql
SELECT * FROM student LIMIT 3;
```

## Order By Clause
```sql
SELECT * FROM student
ORDER BY city ASC;
```

## Aggregate Functions
- **COUNT()**
- **MAX()**
- **MIN()**
- **SUM()**
- **AVG()**

### Example Aggregate Functions
```sql
SELECT MAX(marks) FROM student;
SELECT AVG(marks) FROM student;
```

## Group By Clause
```sql
SELECT city, COUNT(name)
FROM student
GROUP BY city;
```

## Having Clause
```sql
SELECT COUNT(name), city
FROM student
GROUP BY city
HAVING MAX(marks) > 90;
```

## General Order of SQL Queries
```sql
SELECT column(s)
FROM table_name
WHERE condition
GROUP BY column(s)
HAVING condition
ORDER BY column(s) ASC;
```

## Update Query
```sql
UPDATE table_name
SET col1 = val1, col2 = val2
WHERE condition;

UPDATE student
SET grade = "O"
WHERE grade = "A";
```

## Delete Query
```sql
DELETE FROM table_name
WHERE condition;

DELETE FROM student
WHERE marks < 33;
```

## Cascading for Foreign Key
### On Delete Cascade
```sql
CREATE TABLE student (
    id INT PRIMARY KEY,
    courseID INT,
    FOREIGN KEY(courseID) REFERENCES course(id)
    ON DELETE CASCADE
    ON UPDATE CASCADE
);
```

## Alter Table
### Add Column
```sql
ALTER TABLE table_name
ADD COLUMN column_name datatype constraint;
```

### Drop Column
```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

### Rename Table
```sql
ALTER TABLE table_name
RENAME TO new_table_name;
```

### Change Column
```sql
ALTER TABLE table_name
CHANGE COLUMN old_name new_name new_datatype new_constraint;
```

### Modify Column
```sql
ALTER TABLE table_name
MODIFY col_name new_datatype new_constraint;
```

### Example Alter Table
```sql
ALTER TABLE student
ADD COLUMN age INT NOT NULL DEFAULT 19;

ALTER TABLE student
MODIFY age VARCHAR(2);

ALTER TABLE student
CHANGE age stu_age INT;

ALTER TABLE student
DROP COLUMN stu_age;

ALTER TABLE student
RENAME TO stu;
```

## Truncate Table
```sql
TRUNCATE TABLE table_name;
```

## Joins in SQL
Join is used to combine rows from two or more tables, based on a related column between them.

### Types of Joins
- **Inner Join**: Returns records that have matching values in both tables.
- **Left Join**: Returns all records from the left table, and the matched records from the right table.
- **Right Join**: Returns all records from the right table, and the matched records from the left table.
- **Full Join**: Returns all records when there is a match in either left or right table.

### Inner Join Example
```sql
SELECT *
FROM student
INNER JOIN course
ON student.student_id = course.student_id;
```

### Left Join Example
```sql
SELECT *
FROM student AS s
LEFT JOIN course AS c
ON s.student_id = c.student_id;
```

### Right Join Example
```sql
SELECT *
FROM student AS s
RIGHT JOIN course AS c
ON s.student_id = c.student_id;
```

### Full Join Example
```sql
SELECT * FROM student AS a
LEFT JOIN course AS b ON a.id = b.id
UNION
SELECT * FROM student AS a
RIGHT JOIN course AS b ON a.id = b.id;
```

### Self Join Example
```sql
SELECT a.name AS manager_name, b.name
FROM employee AS a
JOIN employee AS b
ON a.id = b.manager_id;
```

## Union
Used to combine the result-set of two or more SELECT statements. Gives unique records.

### Example Union
```sql
SELECT column(s) FROM tableA
UNION
SELECT column(s) FROM tableB;
```

## SQL Subqueries
A subquery or inner query or nested query is a query within another SQL query.

### Example Subquery
```sql
SELECT column(s)
FROM table_name
WHERE col_name operator
(SELECT column(s) FROM table_name);
```

### Example: Find Names of Students with Even Roll Numbers
```sql
SELECT name
FROM student
WHERE rollno IN (SELECT rollno FROM student WHERE rollno % 2 = 0);
```

## MySQL Views
A view is a virtual table based on the result-set of an SQL statement.

### Example View
```sql
CREATE VIEW view1 AS
SELECT rollno, name FROM student;

SELECT * FROM view1;
```
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
| 1      | Rijoan   | X     | 1995-06-06 | M      | Dhaka   | 551   |
| 2      | Rashed | XII   | 1993-05-07 | M      | Cumilla | 462   |
| 3      | Anik   | XI    | 1994-05-06 | F      | Chittagong  | 400   |
| 4      | Reyad  | XII   | 1995-08-08 | F      | Rajshahi | 450   |
| 5      | Rihan   | XII   | 1995-10-08 | M      | Barishal  | 369   |
| 6      | Arman | XI    | 1994-12-12 | F      | Dubai  | 250   |
| 7      | Ahnaf    | X     | 1995-12-08 | F      | Moscow | 377   |
| 8      | Rifat | X     | 1995-06-12 | M      | Moscow | 489   |

## Creating our First Database
```sql
CREATE DATABASE db_name;  -- Creates a new database
DROP DATABASE db_name;    -- Deletes an existing database
```

## Creating our First Table

#### Format :
```sql
USE db_name;  -- Selects the database to use

CREATE TABLE table_name (
    column_name1 datatype constraint,  -- Defines the first column with its data type and constraints
    column_name2 datatype constraint,  -- Defines the second column with its data type and constraints
    column_name3 datatype constraint   -- Defines the third column with its data type and constraints
);
```
#### Example :
```sql
USE db_name;  -- Selects the database to use

CREATE TABLE student (
    id INT PRIMARY KEY,  -- Defines an integer column 'id' as the primary key
    name VARCHAR(50),    -- Defines a string column 'name' with a maximum length of 50 characters
    age INT NOT NULL     -- Defines an integer column 'age' that cannot be null
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
CREATE DATABASE db_name;  -- Creates a new database
CREATE DATABASE IF NOT EXISTS db_name;  -- Creates a new database only if it does not already exist
DROP DATABASE db_name;  -- Deletes an existing database
DROP DATABASE IF EXISTS db_name;  -- Deletes an existing database only if it exists
SHOW DATABASES;  -- Lists all databases
SHOW TABLES;  -- Lists all tables in the current database
```

## Table Related Queries
### Create Table
```sql
CREATE TABLE student (
    rollno INT PRIMARY KEY,  -- Defines an integer column 'rollno' as the primary key
    name VARCHAR(50)        -- Defines a string column 'name' with a maximum length of 50 characters
);
```

### Select & View All Columns
```sql
SELECT * FROM table_name;  -- Selects all columns from the specified table
SELECT * FROM student;     -- Selects all columns from the 'student' table
```

### Insert Data
```sql
INSERT INTO student (rollno, name)   -- Inserts data into the 'student' table
VALUES (101, "karan"),              -- Inserts the first row of data
       (102, "arjun");              -- Inserts the second row of data
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
    id INT NOT NULL,  -- Defines an integer column 'id' that cannot be null
    PRIMARY KEY (id)  -- Sets 'id' as the primary key
);

CREATE TABLE city (
    id INT PRIMARY KEY,  -- Defines an integer column 'id' as the primary key
    city VARCHAR(50),    -- Defines a string column 'city' with a maximum length of 50 characters
    age INT,             -- Defines an integer column 'age'
    CONSTRAINT age_check CHECK (age >= 18 AND city="Delhi")  -- Adds a check constraint to ensure age is >= 18 and city is "Delhi"
);
```

## Sample Table Creation
```sql
CREATE DATABASE college;  -- Creates a new database named 'college'
USE college;  -- Selects the 'college' database

CREATE TABLE student (
    rollno INT PRIMARY KEY,  -- Defines an integer column 'rollno' as the primary key
    name VARCHAR(50),       -- Defines a string column 'name' with a maximum length of 50 characters
    marks INT NOT NULL,     -- Defines an integer column 'marks' that cannot be null
    grade VARCHAR(1),       -- Defines a string column 'grade' with a maximum length of 1 character
    city VARCHAR(20)        -- Defines a string column 'city' with a maximum length of 20 characters
);

INSERT INTO student (rollno, name, marks, grade, city)  -- Inserts data into the 'student' table
VALUES (101, "anil", 78, "C", "Pune"),                 -- Inserts the first row of data
       (102, "bhumika", 93, "A", "Mumbai"),            -- Inserts the second row of data
       (103, "chetan", 85, "B", "Mumbai"),             -- Inserts the third row of data
       (104, "dhruv", 96, "A", "Delhi"),               -- Inserts the fourth row of data
       (105, "emanuel", 12, "F", "Delhi"),             -- Inserts the fifth row of data
       (106, "farah", 82, "B", "Delhi");               -- Inserts the sixth row of data
```

## Select in Detail
```sql
SELECT col1, col2 FROM table_name;  -- Selects specific columns from the specified table
SELECT * FROM table_name;           -- Selects all columns from the specified table
```

## Where Clause
```sql
SELECT col1, col2 FROM table_name
WHERE condition;  -- Filters rows based on the specified condition

SELECT * FROM student WHERE marks > 80;  -- Selects all columns from 'student' where marks are greater than 80
SELECT * FROM student WHERE city = "Mumbai";  -- Selects all columns from 'student' where city is "Mumbai"
```

## Operators in WHERE Clause
- **Arithmetic Operators**: +, -, *, /, %
- **Comparison Operators**: =, !=, >, >=, <, <=
- **Logical Operators**: AND, OR, NOT, IN, BETWEEN, ALL, LIKE, ANY
- **Bitwise Operators**: &, |

### Example Operators
```sql
SELECT * FROM student WHERE marks > 80 AND city = "Mumbai";  -- Selects rows where marks > 80 and city is "Mumbai"
SELECT * FROM student WHERE marks > 90 OR city = "Mumbai";   -- Selects rows where marks > 90 or city is "Mumbai"
SELECT * FROM student WHERE marks BETWEEN 80 AND 90;         -- Selects rows where marks are between 80 and 90
SELECT * FROM student WHERE city IN ("Delhi", "Mumbai");     -- Selects rows where city is either "Delhi" or "Mumbai"
SELECT * FROM student WHERE city NOT IN ("Delhi", "Mumbai"); -- Selects rows where city is neither "Delhi" nor "Mumbai"
```

## Limit Clause
```sql
SELECT * FROM student LIMIT 3;  -- Selects the first 3 rows from the 'student' table
```

## Order By Clause
```sql
SELECT * FROM student
ORDER BY city ASC;  -- Orders the rows by the 'city' column in ascending order
```

## Aggregate Functions
- **COUNT()**
- **MAX()**
- **MIN()**
- **SUM()**
- **AVG()**

### Example Aggregate Functions
```sql
SELECT MAX(marks) FROM student;  -- Selects the maximum value from the 'marks' column
SELECT AVG(marks) FROM student;  -- Selects the average value from the 'marks' column
```

## Group By Clause
```sql
SELECT city, COUNT(name)  -- Selects the 'city' column and the count of 'name' for each city
FROM student
GROUP BY city;  -- Groups the results by the 'city' column
```

## Having Clause
```sql
SELECT COUNT(name), city  -- Selects the count of 'name' and the 'city' column
FROM student
GROUP BY city  -- Groups the results by the 'city' column
HAVING MAX(marks) > 90;  -- Filters groups where the maximum 'marks' is greater than 90
```

## General Order of SQL Queries
```sql
SELECT column(s)  -- Specifies the columns to be selected
FROM table_name   -- Specifies the table to select from
WHERE condition   -- Filters rows based on the condition
GROUP BY column(s)  -- Groups the results by the specified columns
HAVING condition    -- Filters groups based on the condition
ORDER BY column(s) ASC;  -- Orders the results by the specified columns in ascending order
```

## Update Query
```sql
UPDATE table_name
SET col1 = val1, col2 = val2  -- Updates the specified columns with new values
WHERE condition;              -- Filters rows to be updated based on the condition

UPDATE student
SET grade = "O"  -- Updates the 'grade' column to "O"
WHERE grade = "A";  -- Filters rows where the 'grade' is "A"
```

## Delete Query
```sql
DELETE FROM table_name
WHERE condition;  -- Deletes rows based on the specified condition

DELETE FROM student
WHERE marks < 33;  -- Deletes rows where 'marks' are less than 33
```

## Cascading for Foreign Key
### On Delete Cascade
```sql
CREATE TABLE student (
    id INT PRIMARY KEY,  -- Defines an integer column 'id' as the primary key
    courseID INT,        -- Defines an integer column 'courseID'
    FOREIGN KEY(courseID) REFERENCES course(id)  -- Defines 'courseID' as a foreign key referencing 'id' in the 'course' table
    ON DELETE CASCADE    -- Automatically deletes rows in 'student' when referenced rows in 'course' are deleted
    ON UPDATE CASCADE    -- Automatically updates rows in 'student' when referenced rows in 'course' are updated
);
```

## Alter Table
### Add Column
```sql
ALTER TABLE table_name
ADD COLUMN column_name datatype constraint;  -- Adds a new column to the table
```

### Drop Column
```sql
ALTER TABLE table_name
DROP COLUMN column_name;  -- Deletes an existing column from the table
```

### Rename Table
```sql
ALTER TABLE table_name
RENAME TO new_table_name;  -- Renames the table
```

### Change Column
```sql
ALTER TABLE table_name
CHANGE COLUMN old_name new_name new_datatype new_constraint;  -- Changes the name and properties of an existing column
```

### Modify Column
```sql
ALTER TABLE table_name
MODIFY col_name new_datatype new_constraint;  -- Modifies the properties of an existing column
```

### Example Alter Table
```sql
ALTER TABLE student
ADD COLUMN age INT NOT NULL DEFAULT 19;  -- Adds a new column 'age' with a default value of 19

ALTER TABLE student
MODIFY age VARCHAR(2);  -- Changes the data type of the 'age' column to VARCHAR(2)

ALTER TABLE student
CHANGE age stu_age INT;  -- Renames the 'age' column to 'stu_age' and changes its data type to INT

ALTER TABLE student
DROP COLUMN stu_age;  -- Deletes the 'stu_age' column

ALTER TABLE student
RENAME TO stu;  -- Renames the 'student' table to 'stu'
```

## Truncate Table
```sql
TRUNCATE TABLE table_name;  -- Deletes all rows from the table but keeps the table structure
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
ON student.student_id = course.student_id;  -- Combines rows from 'student' and 'course' where 'student_id' matches
```

### Left Join Example
```sql
SELECT *
FROM student AS s
LEFT JOIN course AS c
ON s.student_id = c.student_id;  -- Returns all rows from 'student' and matched rows from 'course'
```

### Right Join Example
```sql
SELECT *
FROM student AS s
RIGHT JOIN course AS c
ON s.student_id = c.student_id;  -- Returns all rows from 'course' and matched rows from 'student'
```

### Full Join Example
```sql
SELECT * FROM student AS a
LEFT JOIN course AS b ON a.id = b.id  -- Returns all rows from 'student' and matched rows from 'course'
UNION
SELECT * FROM student AS a
RIGHT JOIN course AS b ON a.id = b.id;  -- Returns all rows from 'course' and matched rows from 'student'
```

### Self Join Example
```sql
SELECT a.name AS manager_name, b.name
FROM employee AS a
JOIN employee AS b
ON a.id = b.manager_id;  -- Combines rows from the same table to find manager-employee relationships
```

## Union
Used to combine the result-set of two or more SELECT statements. Gives unique records.

### Example Union
```sql
SELECT column(s) FROM tableA
UNION
SELECT column(s) FROM tableB;  -- Combines the results of two SELECT statements and removes duplicates
```

## SQL Subqueries
A subquery or inner query or nested query is a query within another SQL query.

### Example Subquery
```sql
SELECT column(s)
FROM table_name
WHERE col_name operator
(SELECT column(s) FROM table_name);  -- Uses the result of the inner query in the outer query
```

### Example: Find Names of Students with Even Roll Numbers
```sql
SELECT name
FROM student
WHERE rollno IN (SELECT rollno FROM student WHERE rollno % 2 = 0);  -- Finds students with even roll numbers
```

## MySQL Views
A view is a virtual table based on the result-set of an SQL statement.

### Example View
```sql
CREATE VIEW view1 AS
SELECT roll
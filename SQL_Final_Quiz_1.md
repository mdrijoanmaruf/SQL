# **Database**

---

## **Lecture 9: DDL and DML Commands**

### **1. SQL Data Types Overview**
Data types define what kind of data can be stored in columns.

| Data Type       | Description                          | Example Values |
|-----------------|--------------------------------------|----------------|
| `CHAR(10)`      | Fixed-length text (padded with spaces) | 'Hello     '   |
| `VARCHAR(50)`   | Variable-length text (standard SQL)  | 'Hello'        |
| `DATE`          | Stores dates                         | '2024-05-20'   |
| `NUMBER(5,2)`   | Decimal numbers (5 digits, 2 decimal)| 123.45         |

---

### **2. Data Definition Language (DDL)**
Commands that define database structure.

#### **a. Creating Tables**
*Stores data in rows and columns with defined structure.*
```sql
-- CREATE TABLE syntax:
-- CREATE TABLE table_name (col1 datatype(size), col2 datatype(size)...);

CREATE TABLE employees (
    emp_id NUMBER(5) PRIMARY KEY,       -- Unique employee ID
    name VARCHAR2(50) NOT NULL,         -- Name cannot be empty
    hire_date DATE,                     -- Date of joining
    salary NUMBER(10,2)                 -- Decimal salary amount
);
```

#### **b. Modifying Tables**
*Alters existing table structure.*

**Adding a column:**
```sql
-- ALTER TABLE table_name ADD (new_col datatype(size));
ALTER TABLE employees ADD (department VARCHAR2(30));  -- Adds department column
```

**Removing a column:**
```sql
-- ALTER TABLE table_name DROP COLUMN column_name;
ALTER TABLE employees DROP COLUMN hire_date;  -- Deletes hire_date column
```

#### **c. Table Maintenance**
**Renaming a table:**
```sql
-- RENAME old_name TO new_name;
RENAME employees TO staff;  -- Changes table name
```

**Deleting all data (keeping structure):**
```sql
-- TRUNCATE TABLE table_name;
TRUNCATE TABLE staff;  -- Removes all rows quickly
```

**Deleting entire table:**
```sql
-- DROP TABLE table_name;
DROP TABLE staff;  -- Completely removes table
```

---

### **3. Data Manipulation Language (DML)**
Commands for working with data in tables.

#### **a. Inserting Data**
*Adds new records to tables.*

**Specifying columns:**
```sql
-- INSERT INTO table (col1,col2) VALUES (val1,val2);
INSERT INTO employees (emp_id, name, salary)
VALUES (101, 'John Doe', 50000);  -- Adds specific columns
```

**Without column names:**
```sql
-- INSERT INTO table VALUES (all_values);
INSERT INTO employees 
VALUES (102, 'Jane Smith', DATE '2023-01-15', 60000);  -- Must match column order
```

#### **b. Updating Data**
*Modifies existing records.*

**Updating all rows:**
```sql
-- UPDATE table SET col=new_value;
UPDATE employees SET salary = salary * 1.1;  -- Gives 10% raise to all
```

**Conditional update:**
```sql
-- UPDATE table SET col=value WHERE condition;
UPDATE employees SET salary = 70000 
WHERE emp_id = 101;  -- Updates only John's salary
```

#### **c. Deleting Data**
*Removes records from tables.*

**Deleting all data:**
```sql
-- DELETE FROM table_name;
DELETE FROM employees;  -- Removes all employee records
```

**Conditional deletion:**
```sql
-- DELETE FROM table WHERE condition;
DELETE FROM employees 
WHERE salary < 30000;  -- Removes low-paid employees
```

---

## **Lecture 10: Data Constraints**

### **1. Key Constraints**
*Rules that enforce data integrity.*

**Primary Key (Unique identifier):**
```sql
-- column datatype PRIMARY KEY
CREATE TABLE students (
    student_id NUMBER(5) PRIMARY KEY,  -- Unique ID for each student
    name VARCHAR2(50)
);
```

**Foreign Key (Relationship between tables):**
```sql
-- CONSTRAINT name FOREIGN KEY (col) REFERENCES parent(col)
CREATE TABLE enrollments (
    enroll_id NUMBER(5),
    student_id NUMBER(5),
    CONSTRAINT fk_student 
    FOREIGN KEY (student_id) REFERENCES students(student_id)  -- Links to students
);
```

### **2. Data Validation Constraints**
**NOT NULL (Mandatory fields):**
```sql
-- column datatype NOT NULL
CREATE TABLE products (
    product_id NUMBER(5) NOT NULL,  -- Must have an ID
    name VARCHAR2(100)
);
```

**CHECK (Custom validation rules):**
```sql
-- column datatype CHECK (condition)
CREATE TABLE employees (
    salary NUMBER(10,2) CHECK (salary > 0)  -- Salary must be positive
);
```

### **3. Managing Constraints**
**Adding constraints later:**
```sql
-- ALTER TABLE table ADD CONSTRAINT name constraint_type (column);
ALTER TABLE employees 
ADD CONSTRAINT chk_salary CHECK (salary < 100000);  -- Adds salary cap
```

**Removing constraints:**
```sql
-- ALTER TABLE table DROP CONSTRAINT name;
ALTER TABLE employees 
DROP CONSTRAINT chk_salary;  -- Removes salary check
```

---

## **Lecture 17: Sequences**

### **1. Creating Sequences**
*Auto-number generators for IDs.*
```sql
-- CREATE SEQUENCE name INCREMENT BY n START WITH n...;
CREATE SEQUENCE emp_seq
    INCREMENT BY 1      -- Increases by 1 each time
    START WITH 1000     -- First number will be 1000
    MAXVALUE 9999       -- Won't go beyond 9999
    NOCYCLE;            -- Won't restart after max
```

### **2. Using Sequences**
**Getting next value:**
```sql
-- sequence_name.NEXTVAL
INSERT INTO employees (emp_id, name)
VALUES (emp_seq.NEXTVAL, 'Alice');  -- Auto-generates ID
```

**Checking current value:**
```sql
-- sequence_name.CURRVAL
SELECT emp_seq.CURRVAL FROM dual;  -- Shows last generated number
```

### **3. Modifying Sequences**
```sql
-- ALTER SEQUENCE name new_settings;
ALTER SEQUENCE emp_seq
    INCREMENT BY 2      -- Now increases by 2 each time
    MAXVALUE 99999;     -- New maximum limit
```

### **4. Removing Sequences**
```sql
-- DROP SEQUENCE sequence_name;
DROP SEQUENCE emp_seq;  -- Deletes the sequence
```

---

## **Summary Cheat Sheet**

### **DDL Commands**
- `CREATE TABLE` - Makes new tables
- `ALTER TABLE` - Changes table structure
- `DROP TABLE` - Deletes tables completely

### **DML Commands**
- `INSERT` - Adds new data
- `UPDATE` - Changes existing data
- `DELETE` - Removes data

### **Constraints**
- `PRIMARY KEY` - Unique row identifier
- `FOREIGN KEY` - Links between tables
- `CHECK` - Validates data rules

### **Sequences**
- `CREATE SEQUENCE` - Auto-number generator
- `NEXTVAL/CURRVAL` - Get next/current sequence value

These notes provide **clear explanations** with **real-world examples** for all key database operations. Each concept is presented with:
1. **Purpose** - Why it's used
2. **Syntax** - How to write it (as comments)
3. **Example** - Practical implementation
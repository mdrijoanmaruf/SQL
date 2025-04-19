# Database AIUB Mid Term

## Keywords Writing (Fill in the Blanks) - 10 Marks

### Important Concepts and Terms:

1. **SQL**: Structured Query Language, standard language for RDBMS
2. **DDL**: Data Definition Language (CREATE, ALTER, DROP)
3. **DML**: Data Manipulation Language (SELECT, INSERT, UPDATE, DELETE)
4. **WHERE**: Clause to filter rows in a query
5. **ORDER BY**: Clause to sort query results
6. **GROUP BY**: Clause to group rows for aggregate functions
7. **HAVING**: Clause to filter groups
8. **JOIN**: Combines rows from two or more tables
9. **Primary Key**: Unique identifier for a table
10. **Foreign Key**: Field that references primary key in another table
11. **NULL**: Represents missing or unknown data
12. **DISTINCT**: Eliminates duplicate rows from results
13. **Schema**: Logical structure of the database
14. **Entity**: Object in the real world represented in database
15. **Attribute**: Property of an entity
16. **Relationship**: Association between entities
17. **Cardinality**: Number of instances in one entity related to another
18. **Aggregate Functions**: Functions that operate on sets of values (COUNT, SUM, AVG, etc.)
19. **Normalization**: Process of organizing data to reduce redundancy
20. **Transaction**: Sequence of operations performed as a single logical unit

## Query Writing - 25 Marks

### Basic SELECT Statements
```sql
-- Select all columns from a table
SELECT * FROM emp;

-- Select specific columns
SELECT ename, sal, deptno FROM emp;

-- Using arithmetic expressions
SELECT ename, sal, sal*12 AS annual_salary FROM emp;

-- Using column aliases
SELECT ename AS "Employee Name", sal "Salary" FROM emp;
```

### Filtering Data with WHERE Clause
```sql
-- Simple condition
SELECT ename, job FROM emp WHERE deptno = 20;

-- Comparison operators
SELECT ename, sal FROM emp WHERE sal > 2000;

-- BETWEEN operator
SELECT ename, sal FROM emp WHERE sal BETWEEN 1000 AND 2000;

-- IN operator
SELECT ename, job FROM emp WHERE job IN ('CLERK', 'SALESMAN');

-- LIKE operator with wildcards
SELECT ename FROM emp WHERE ename LIKE 'S%';

-- IS NULL operator
SELECT ename, mgr FROM emp WHERE mgr IS NULL;
```

### Sorting with ORDER BY
```sql
-- Ascending order (default)
SELECT ename, hiredate FROM emp ORDER BY hiredate;

-- Descending order
SELECT ename, sal FROM emp ORDER BY sal DESC;

-- Sorting by multiple columns
SELECT ename, deptno, sal FROM emp ORDER BY deptno, sal DESC;
```

### Single-Row Functions
```sql
-- Character functions
SELECT UPPER(ename), LENGTH(ename) FROM emp;
SELECT SUBSTR(ename, 1, 3), INSTR(ename, 'A') FROM emp;

-- Number functions
SELECT ROUND(45.926, 2), TRUNC(45.926, 2), MOD(1600, 300) FROM dual;

-- Date functions
SELECT ename, MONTHS_BETWEEN(SYSDATE, hiredate) FROM emp;
SELECT ename, TO_CHAR(hiredate, 'DD-MON-YYYY') FROM emp;

-- Conversion functions
SELECT TO_CHAR(sal, '$99,999') FROM emp;
SELECT TO_DATE('01-JAN-2023', 'DD-MON-YYYY') FROM dual;

-- General functions
SELECT ename, sal, NVL(comm, 0) FROM emp;
SELECT ename, sal, DECODE(job, 'MANAGER', sal*1.1, 'CLERK', sal*1.05, sal) FROM emp;
```

### Aggregate Functions
```sql
-- Basic aggregate functions
SELECT AVG(sal), MAX(sal), MIN(sal), SUM(sal) FROM emp;

-- COUNT functions
SELECT COUNT(*) FROM emp;
SELECT COUNT(comm) FROM emp; -- Counts non-null values

-- GROUP BY clause
SELECT deptno, AVG(sal) FROM emp GROUP BY deptno;

-- HAVING clause
SELECT deptno, AVG(sal) 
FROM emp 
GROUP BY deptno 
HAVING AVG(sal) > 2000;

-- Nesting group functions
SELECT MAX(AVG(sal)) FROM emp GROUP BY deptno;
```

### Joins (Implied in lecture materials)
```sql
-- Basic join
SELECT e.ename, d.dname 
FROM emp e, dept d 
WHERE e.deptno = d.deptno;
```

## ER Diagram - 15 Marks

### Key Concepts for ER Diagrams:

1. **Entity Sets**: Represented by rectangles
2. **Attributes**: Represented by ellipses
   - Simple vs. Composite
   - Single-valued vs. Multi-valued (double ellipse)
   - Derived (dashed ellipse)
3. **Relationship Sets**: Represented by diamonds
4. **Cardinality Constraints**:
   - One-to-one (1:1)
   - One-to-many (1:N)
   - Many-to-one (N:1)
   - Many-to-many (M:N)
5. **Participation Constraints**:
   - Total participation (double line)
   - Partial participation (single line)
6. **Weak Entity Sets**: Double rectangles, identifying relationship with double diamond
7. **Specialization/Generalization**:
   - ISA hierarchy (triangle)
   - Disjoint/Overlapping constraints
8. **Aggregation**: Representing relationships as entities

### Example ER Diagram Scenario:

**University Management System**:
- Student (student_id, name, address)
- Class (class_id, name) with total participation in "attends" relationship
- Section (section_id) which is weak entity dependent on Class
- Teacher (teacher_id, name) with subclasses Lecturer and Professor
- Course (course_id, title)
- Lecture (lecture_id, topic) with components like Assignment
- Assignment specialized into Homework, Exam, Project
- Guardian (guardian_id, name) with "enquires" relationship to Course and Lecture

## Short Questions - 10 Marks

### Potential Questions and Answers:

1. **What is the difference between data and information?**
   - Data: Raw facts without context (e.g., 42, 63, 96)
   - Information: Data processed to have meaning (e.g., test scores converted to grades)

2. **Explain the difference between WHERE and HAVING clauses.**
   - WHERE filters rows before grouping
   - HAVING filters groups after aggregation
   - WHERE cannot contain aggregate functions, HAVING can

3. **What are the different types of attributes in ER modeling?**
   - Simple vs. Composite
   - Single-valued vs. Multi-valued
   - Stored vs. Derived
   - Key attributes

4. **Explain the NVL function with an example.**
   - NVL replaces NULL with a specified value
   - Example: `SELECT ename, sal, NVL(comm, 0) FROM emp;` replaces NULL comm with 0

5. **What is the difference between GROUP BY and ORDER BY?**
   - GROUP BY groups rows for aggregate calculations
   - ORDER BY sorts the final result set
   - GROUP BY affects how data is processed, ORDER BY affects how it's displayed

6. **Explain the different types of participation constraints in ER diagrams.**
   - Total participation: Every entity must participate (double line)
   - Partial participation: Some entities may not participate (single line)

7. **What are the different types of SQL functions? Give examples.**
   - Single-row: Work on individual rows (e.g., UPPER, ROUND, TO_CHAR)
   - Aggregate: Work on groups of rows (e.g., SUM, AVG, COUNT)

8. **Explain the LIKE operator with examples.**
   - Pattern matching with wildcards:
     - % for zero or more characters ('S%' - names starting with S)
     - _ for exactly one character ('_A%' - names with A as second letter)

9. **What is the difference between a weak entity and a strong entity?**
   - Strong entity: Has its own primary key
   - Weak entity: Depends on another entity for identification, has partial key

10. **Explain the DECODE function with an example.**
    - Provides IF-THEN-ELSE logic:
    ```sql
    SELECT job, sal, DECODE(job, 'ANALYST', sal*1.1,
                            'CLERK', sal*1.15,
                            sal) AS revised_sal
    FROM emp;
    ```


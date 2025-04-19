# SQL AIUB MID

## Keyword
### Data Query Language (DQL)

1. **SELECT** - Retrieves data from a database  
   `SELECT ename, sal FROM emp;`

2. **DISTINCT** - Eliminates duplicate rows  
   `SELECT DISTINCT deptno FROM emp;`

3. **FROM** - Specifies the table to query  
   `SELECT * FROM dept;`

4. **WHERE** - Filters rows based on conditions  
   `SELECT ename FROM emp WHERE job='CLERK';`

5. **ORDER BY** - Sorts the result set  
   `SELECT ename, hiredate FROM emp ORDER BY hiredate DESC;`

6. **GROUP BY** - Groups rows that have the same values  
   `SELECT deptno, AVG(sal) FROM emp GROUP BY deptno;`

7. **HAVING** - Filters groups based on conditions  
   `SELECT deptno, MAX(sal) FROM emp GROUP BY deptno HAVING MAX(sal)>2900;`

### Data Manipulation Language (DML)

8. **INSERT** - Adds new rows to a table  
   `INSERT INTO emp VALUES(1234, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);`

9. **UPDATE** - Modifies existing rows  
   `UPDATE emp SET sal = 3000 WHERE empno = 7788;`

10. **DELETE** - Removes rows from a table  
    `DELETE FROM emp WHERE empno = 1234;`

11. **MERGE** - Performs insert/update operations conditionally  
    `MERGE INTO bonuses USING emp ON (...) WHEN MATCHED THEN UPDATE...`

### Data Definition Language (DDL)

12. **CREATE** - Creates database objects  
    `CREATE TABLE emp (empno NUMBER(4), ename VARCHAR2(10));`

13. **ALTER** - Modifies database objects  
    `ALTER TABLE emp ADD (address VARCHAR2(50));`

14. **DROP** - Removes database objects  
    `DROP TABLE emp;`

15. **RENAME** - Renames database objects  
    `RENAME emp TO employee;`

16. **TRUNCATE** - Removes all rows from a table  
    `TRUNCATE TABLE emp;`

### Operators

17. **BETWEEN** - Range condition  
    `SELECT ename FROM emp WHERE sal BETWEEN 1000 AND 2000;`

18. **IN** - Tests for values in a list  
    `SELECT ename FROM emp WHERE deptno IN (10, 20);`

19. **LIKE** - Pattern matching  
    `SELECT ename FROM emp WHERE ename LIKE 'S%';`

20. **IS NULL** - Tests for null values  
    `SELECT ename FROM emp WHERE comm IS NULL;`

21. **NOT** - Negates a condition  
    `SELECT ename FROM emp WHERE job NOT IN ('CLERK','MANAGER');`

22. **AND** - Logical AND  
    `SELECT ename FROM emp WHERE job='MANAGER' AND sal>2500;`

23. **OR** - Logical OR  
    `SELECT ename FROM emp WHERE job='MANAGER' OR job='PRESIDENT';`

### Functions

24. **NVL** - Replaces null with specified value  
    `SELECT ename, NVL(comm, 0) FROM emp;`

25. **NVL2** - Returns different values based on null  
    `SELECT NVL2(comm, 'Has Commission', 'No Commission') FROM emp;`

26. **NULLIF** - Returns null if equal  
    `SELECT NULLIF(sal, comm) FROM emp;`

27. **DECODE** - Conditional logic  
    `SELECT DECODE(job, 'MANAGER', sal*1.1, 'CLERK', sal*1.15, sal) FROM emp;`

28. **TO_CHAR** - Converts to character  
    `SELECT TO_CHAR(hiredate, 'DD-MON-YYYY') FROM emp;`

29. **TO_NUMBER** - Converts to number  
    `SELECT TO_NUMBER('1234') FROM dual;`

30. **TO_DATE** - Converts to date  
    `SELECT TO_DATE('01-JAN-2023', 'DD-MON-YYYY') FROM dual;`

### Aggregate Functions

31. **AVG** - Average value  
    `SELECT AVG(sal) FROM emp;`

32. **COUNT** - Counts rows  
    `SELECT COUNT(*) FROM emp;`

33. **MAX** - Maximum value  
    `SELECT MAX(sal) FROM emp;`

34. **MIN** - Minimum value  
    `SELECT MIN(hiredate) FROM emp;`

35. **SUM** - Sum of values  
    `SELECT SUM(sal) FROM emp WHERE deptno=10;`

36. **STDDEV** - Standard deviation  
    `SELECT STDDEV(sal) FROM emp;`

37. **VARIANCE** - Variance  
    `SELECT VARIANCE(sal) FROM emp;`

### Other Keywords

38. **AS** - Column alias  
    `SELECT ename AS name FROM emp;`

39. **DESC** - Descending sort order  
    `SELECT ename FROM emp ORDER BY hiredate DESC;`

40. **ASC** - Ascending sort order (default)  
    `SELECT ename FROM emp ORDER BY ename ASC;`

41. **||** - Concatenation operator  
    `SELECT ename || ' works as ' || job FROM emp;`

42. **DUAL** - Dummy table  
    `SELECT SYSDATE FROM dual;`

43. **SYSDATE** - Current date/time  
    `SELECT SYSDATE FROM dual;`







## SQL Queries 

### Basic SELECT Queries (Lecture 02)
```sql
-- Select all columns from DEPT table
SELECT * FROM dept;

-- Select specific columns (deptno and loc) from DEPT table
SELECT deptno, loc FROM dept;

-- Select with arithmetic operations (add 300 to salary)
SELECT ename, sal, sal+300 FROM emp;

-- Operator precedence example (multiplication before addition)
SELECT ename, sal, 12*sal+100 FROM emp;

-- Using parentheses to control calculation order
SELECT ename, sal, 12*(sal+100) FROM emp;

-- Handling NULL values in arithmetic (NULL results in NULL)
SELECT ename, 12*sal+comm FROM emp WHERE ename='KING';

-- Column aliases (rename columns in output)
SELECT ename AS name, sal salary FROM emp;
SELECT ename "Name", sal*12 "Annual Salary" FROM emp;

-- String concatenation
SELECT ename||job AS "Employees" FROM emp;

-- Literal character strings in output
SELECT ename||' is a '||job AS "Employee Details" FROM emp;

-- Eliminating duplicate rows
SELECT DISTINCT deptno FROM emp;
```

### Restricting and Sorting Data (Lecture 04)
```sql
-- Basic WHERE clause (filter clerks)
SELECT ename, job, deptno FROM emp WHERE job='CLERK';

-- Case sensitivity in strings
SELECT ename, job, deptno FROM emp WHERE ename = 'JAMES';

-- Comparison operators (salary <= commission)
SELECT ename, sal, comm FROM emp WHERE sal<=comm;

-- BETWEEN operator (salary range)
SELECT ename, sal FROM emp WHERE sal BETWEEN 1000 AND 1500;

-- IN operator (multiple possible values)
SELECT empno, ename, sal, mgr FROM emp WHERE mgr IN (7902, 7566, 7788);

-- LIKE operator (wildcard search)
SELECT ename FROM emp WHERE ename LIKE 'S%'; -- names starting with S
SELECT ename FROM emp WHERE ename LIKE '_A%'; -- names with A as second letter

-- IS NULL operator (find null values)
SELECT ename, mgr FROM emp WHERE mgr IS NULL;

-- Logical operators (AND, OR, NOT)
SELECT empno, ename, job, sal FROM emp WHERE sal>=1100 AND job='CLERK';
SELECT empno, ename, job, sal FROM emp WHERE sal>=1100 OR job='CLERK';
SELECT ename, job FROM emp WHERE job NOT IN ('CLERK','MANAGER','ANALYST');

-- ORDER BY clause (sorting)
SELECT ename, job, deptno, hiredate FROM emp ORDER BY hiredate;
SELECT ename, job, deptno, hiredate FROM emp ORDER BY hiredate DESC;
SELECT empno, ename, sal*12 annsal FROM emp ORDER BY annsal;
SELECT ename, deptno, sal FROM emp ORDER BY deptno, sal DESC;
```

### Single-Row Functions (Lecture 06)
```sql
-- Case conversion functions
SELECT empno, ename, deptno FROM emp WHERE ename = UPPER('blake');

-- Character manipulation functions
SELECT ename, CONCAT(ename, job), LENGTH(ename), INSTR(ename, 'A')
FROM emp WHERE SUBSTR(job,1,5) = 'SALES';

-- Number functions
SELECT ROUND(45.923,2), ROUND(45.923,0), ROUND(45.923,-1) FROM DUAL;
SELECT TRUNC(45.923,2), TRUNC(45.923), TRUNC(45.923,-1) FROM DUAL;
SELECT ename, sal, comm, MOD(sal, comm) FROM emp WHERE job = 'SALESMAN';

-- Date functions
SELECT ename, (SYSDATE-hiredate)/7 WEEKS FROM emp WHERE deptno = 10;

-- TO_CHAR with dates
SELECT ename, TO_CHAR(hiredate, 'fmDD Month YYYY') HIREDATE FROM emp;

-- TO_CHAR with numbers
SELECT TO_CHAR(sal,'$99,999') SALARY FROM emp WHERE ename = 'SCOTT';

-- NVL function (handle NULL values)
SELECT ename, sal, comm, (sal*12)+NVL(comm,0) FROM emp;

-- NVL2 function (different actions for NULL/non-NULL)
SELECT NVL2(comm,comm+sal,sal) FROM emp;

-- NULLIF function (compare two expressions)
SELECT ename, LENGTH(ename), job, LENGTH(job), NULLIF(ename,job) FROM emp;

-- DECODE function (conditional logic)
SELECT job, sal,
       DECODE(job, 'ANALYST', SAL*1.1,
                   'CLERK',   SAL*1.15,
                   'MANAGER', SAL*1.20,
                              SAL) REVISED_SALARY
FROM emp;

-- Nested functions
SELECT ename, NVL(TO_CHAR(mgr),'No Manager') FROM emp WHERE mgr IS NULL;
```

### Aggregate Functions (Lecture 08)
```sql
-- Basic aggregate functions
SELECT AVG(sal), MAX(sal), MIN(sal), SUM(sal) FROM emp WHERE job LIKE 'SALES%';
SELECT MIN(hiredate), MAX(hiredate) FROM emp;
SELECT COUNT(*) FROM emp WHERE deptno = 30;
SELECT COUNT(comm) FROM emp WHERE deptno = 30;

-- Handling NULLs with NVL in aggregates
SELECT AVG(comm) FROM emp; -- ignores NULLs
SELECT AVG(NVL(comm,0)) FROM emp; -- includes NULLs as 0

-- GROUP BY clause
SELECT deptno, AVG(sal) FROM emp GROUP BY deptno;
SELECT deptno, job, SUM(sal) FROM emp GROUP BY deptno, job;

-- HAVING clause (filter groups)
SELECT deptno, MAX(sal) FROM emp GROUP BY deptno HAVING MAX(sal)>2900;
SELECT job, SUM(sal) PAYROLL FROM emp
WHERE job NOT LIKE 'SALES%'
GROUP BY job
HAVING SUM(sal)>5000
ORDER BY SUM(sal);

-- Nested group functions
SELECT MAX(AVG(sal)) FROM emp GROUP BY deptno;
```
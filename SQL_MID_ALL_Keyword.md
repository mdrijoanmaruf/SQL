# SQL Keywords AIUB MID

## Data Query Language (DQL)

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

## Data Manipulation Language (DML)

8. **INSERT** - Adds new rows to a table  
   `INSERT INTO emp VALUES(1234, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);`

9. **UPDATE** - Modifies existing rows  
   `UPDATE emp SET sal = 3000 WHERE empno = 7788;`

10. **DELETE** - Removes rows from a table  
    `DELETE FROM emp WHERE empno = 1234;`

11. **MERGE** - Performs insert/update operations conditionally  
    `MERGE INTO bonuses USING emp ON (...) WHEN MATCHED THEN UPDATE...`

## Data Definition Language (DDL)

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

## Operators

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

## Functions

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

## Aggregate Functions

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

## Other Keywords

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
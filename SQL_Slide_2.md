### **1. Basic SQL SELECT Statement**
```sql
SELECT [DISTINCT] {*, column [alias], ...} FROM table;
```
- `SELECT` chooses columns
- `FROM` specifies the table

---

### **2. Selecting Columns**
- **All Columns:**
  ```sql
  SELECT * FROM dept;
  ```
- **Specific Columns:**
  ```sql
  SELECT deptno, loc FROM dept;
  ```

---

### **3. Arithmetic Operations**
- Add, Subtract, Multiply, Divide:
  ```sql
  SELECT ename, sal, sal + 300 FROM emp;
  ```
- Operator precedence (multiplication/division before addition/subtraction):
  ```sql
  SELECT ename, sal, 12 * sal + 100 FROM emp;
  ```
- Using parentheses to change order:
  ```sql
  SELECT ename, sal, 12 * (sal + 100) FROM emp;
  ```

---

### **4. Null Values**
- Nulls result in null when used in arithmetic:
  ```sql
  SELECT ename, 12 * sal + comm FROM emp WHERE ename = 'KING';
  ```

---

### **5. Column Aliases**
- Renaming columns:
  ```sql
  SELECT ename AS name, sal salary FROM emp;
  SELECT ename "Name", sal * 12 "Annual Salary" FROM emp;
  ```

---

### **6. Concatenation**
- Using `||` to combine strings:
  ```sql
  SELECT ename || job AS "Employees" FROM emp;
  SELECT ename || ' is a ' || job AS "Employee Details" FROM emp;
  ```

---

### **7. Removing Duplicate Rows**
- Use `DISTINCT`:
  ```sql
  SELECT DISTINCT deptno FROM emp;
  ```

---

### **8. SQL vs SQL\*Plus**
- **SQL**: ANSI standard language to interact with databases.
- **SQL\*Plus**: Oracle tool/environment for running SQL with its own commands (e.g., `DESCRIBE`).

---

### **9. Describing Table Structure**
```sql
DESCRIBE dept;
```


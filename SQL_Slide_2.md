## Lecture 2

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
---

## Lecture 5

### 🔶 **Key Concepts of E-R Modeling**

#### ✅ **E-R Diagram Elements**
- **Rectangles** = Entity sets  
- **Diamonds** = Relationship sets  
- **Ellipses** = Attributes  
  - *Double ellipses*: Multivalued attributes  
  - *Dashed ellipses*: Derived attributes  
- **Underlined attributes** = Primary keys  
- **Lines** link attributes to entities and relationships

---

### 👤 **Entity Sets**
- Entities = Distinct objects (e.g., person, company)
- Entity sets = Collection of similar entities
- Entities have **attributes** (e.g., name, address)

---

### 🧾 **Attributes**
- **Simple** vs **Composite** (e.g., name vs full address)
- **Single-valued** vs **Multivalued** (e.g., one phone vs multiple phones)
- **Derived attributes** = Calculated from other attributes (e.g., age from DOB)
- **Domain** = Allowed values for an attribute

---

### 🔗 **Relationship Sets**
- Associations among entities  
  - e.g., A *borrower* relates **customer** and **loan**
- Can include **attributes** too
- **Degree** of relationship = number of entities involved  
  - Most are **binary** (2 entities)

---

### 🔢 **Mapping Cardinalities** (Constraints)
Defines how many entities participate in a relationship:
- **One-to-One**
- **One-to-Many**
- **Many-to-One**
- **Many-to-Many**

Use lines:
- **→** for "one"
- **—** for "many"

---

### 📚 **ER Diagram Example – Library System**
Scenario includes:
- **Member** (memberNo, name, address [house, street, city])
- **Book** (bookID, name, ISBN, edition)
- **Author** (authorID, name)
- **Category** (categoryNo, name)
- **Borrowing** (date, copyNo)
- **Reservation** (date)

Key relationships:
- Member **rents** many books → One-to-Many
- Member **reserves** many books, and books can be **reserved** by many → Many-to-Many
- Book **written by** one or more authors → Many-to-Many
- Book **belongs to** one category → Many-to-One


# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="1234" height="458" alt="image" src="https://github.com/user-attachments/assets/a342b628-b09e-4785-a4bf-0038738f2ea8" />


```sql
SELECT * FROM EmployeeInfo 
WHERE EmpLname LIKE '____a';
```

**Output:**

<img width="1180" height="226" alt="image" src="https://github.com/user-attachments/assets/988643ef-feb8-4073-aeb6-f364bd541707" />


**Question 2**
---
<img width="1230" height="706" alt="image" src="https://github.com/user-attachments/assets/176d01d7-1083-49d3-b7bf-d198e6566d48" />


```sql
SELECT ename,
    CAST((julianday('2024-08-30')-julianday(hiredate))/365.25 AS INTEGER) AS Tenure
FROM emp;
```

**Output:**

<img width="1181" height="345" alt="image" src="https://github.com/user-attachments/assets/6c98606c-faa8-42f0-91a6-6251688f78a4" />


**Question 3**
---
<img width="1218" height="529" alt="image" src="https://github.com/user-attachments/assets/88448211-3bb0-4b83-947c-f5edab10fa2e" />


```sql
SELECT product_id, original_price, discount_percentage, (original_price*(1-discount_percentage)) AS discounted_price
FROM Products;
```

**Output:**

<img width="1185" height="433" alt="image" src="https://github.com/user-attachments/assets/c7f45623-0c8b-4f7f-80c2-9bf1656aca62" />

**Question 4**
---
<img width="1232" height="483" alt="image" src="https://github.com/user-attachments/assets/531b9ddb-57bf-4fc7-8a37-88d00b3ad2bf" />

```sql
SELECT customer_id,cust_name, city, grade, salesman_id FROM customer
WHERE city='New York' OR grade<=100;
```

**Output:**

<img width="1184" height="406" alt="image" src="https://github.com/user-attachments/assets/c98d416e-2bd6-46d6-92d4-b0186bcb98de" />

**Question 5**
---
<img width="1211" height="567" alt="image" src="https://github.com/user-attachments/assets/f8857ef0-83c8-4514-90d5-7408225aa21e" />

```sql
SELECT first_name, last_name, (julianday(discharge_date)- julianday(admission_date))+1 AS no_of_days
FROM  Patients
WHERE no_of_days>3;
```

**Output:**

<img width="1178" height="314" alt="image" src="https://github.com/user-attachments/assets/49740bf2-9e52-4581-b809-7b7b4c4da506" />


**Question 6**
---
<img width="1227" height="730" alt="image" src="https://github.com/user-attachments/assets/96138d3b-198e-440a-a24d-4eba9c5740a1" />

```sql
UPDATE employees
SET salary=salary+500, email='updated'
WHERE job_id='SA_REP' AND commission_pct>0.15;
```

**Output:**

<img width="1190" height="508" alt="image" src="https://github.com/user-attachments/assets/29f16457-5c32-47fa-a60c-7f40f150ba5e" />


**Question 7**
---
<img width="1217" height="680" alt="image" src="https://github.com/user-attachments/assets/b1d75256-8128-463c-9152-7725e6af2d55" />


```sql
SELECT DISTINCT job, SUBSTR(job, 1,3) AS job_abbr
FROM emp;
```

**Output:**

<img width="1181" height="519" alt="image" src="https://github.com/user-attachments/assets/87f1a58d-35c6-423d-b988-8f874fd8f8ab" />


**Question 8**
---
<img width="1216" height="456" alt="image" src="https://github.com/user-attachments/assets/c87dafa1-9e75-47f0-8bcb-7415fe23dfa7" />


```sql
UPDATE suppliers 
SET supplier_name=UPPER(supplier_name)
WHERE contact_person LIKE '%Singh';
```

**Output:**

<img width="1185" height="332" alt="image" src="https://github.com/user-attachments/assets/0e9a79c8-971a-4dde-9d33-cadff4f4ffbd" />


**Question 9**
---
<img width="1226" height="506" alt="image" src="https://github.com/user-attachments/assets/ef69fc5d-9485-4b8a-9dac-77897b07714e" />


```sql
DELETE FROM Customer
WHERE GRADE%2<>0;
```

**Output:**

<img width="1179" height="415" alt="image" src="https://github.com/user-attachments/assets/2b2c799d-d61a-4f0d-a7c9-cbe1261dc3f5" />


**Question 10**
---
<img width="1231" height="667" alt="image" src="https://github.com/user-attachments/assets/20cbc032-309c-41ed-8baf-f31284fa3c2c" />


```sql
SELECT ord_no,purch_amt,ord_date ,customer_id,salesman_id
FROM orders
WHERE purch_amt<200 OR NOT (ord_date>='2012-02-10' AND customer_id<3009);
```

**Output:**

<img width="1185" height="462" alt="image" src="https://github.com/user-attachments/assets/e631348b-c831-41e2-b278-aa7d11389fc7" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
<img width="1366" height="77" alt="image" src="https://github.com/user-attachments/assets/d4acb443-2469-4014-bb0a-515d6cdf8121" />


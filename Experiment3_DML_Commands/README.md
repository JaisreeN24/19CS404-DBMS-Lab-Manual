# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
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
Thus, the SQL queries to implement different types of constraints and DML commands have been executed successfully.
<img width="1366" height="81" alt="image" src="https://github.com/user-attachments/assets/dc6ca0b0-1d11-4d87-b015-0639bcb896e3" />

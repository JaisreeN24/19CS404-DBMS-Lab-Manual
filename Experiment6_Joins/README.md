# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1180" height="653" alt="image" src="https://github.com/user-attachments/assets/dc11fd7b-7a8b-481c-aa4f-b1bbf91accb8" />


```sql
SELECT s.*
FROM salesman s
LEFT JOIN customer c ON s.salesman_id=c.salesman_id
WHERE c.cust_name='Fabian Johns';
```

**Output:**
<img width="1182" height="393" alt="image" src="https://github.com/user-attachments/assets/50b2f4ca-cb32-4ff9-8886-ee07b894a66c" />


**Question 2**
---
<img width="1216" height="631" alt="image" src="https://github.com/user-attachments/assets/be02f2f3-5851-474a-8719-b1c6ee52c11f" />


```sql
SELECT customer.cust_name AS "Customer Name", customer.city AS "city", salesman.name AS "Salesman", salesman.commission AS "commission"
FROM customer
INNER JOIN salesman ON customer.salesman_id=salesman.salesman_id;
```

**Output:**

<img width="1180" height="907" alt="image" src="https://github.com/user-attachments/assets/f844ce25-69fc-41cb-8be5-6914005214a9" />


**Question 3**
---
<img width="1179" height="658" alt="image" src="https://github.com/user-attachments/assets/53e4a45a-29b5-4f4b-bf20-909a5d809f8f" />


```sql
SELECT p.*
FROM patients AS p
INNER JOIN test_results AS tr ON p.patient_id=tr.patient_id
WHERE (tr.test_name='Blood Test' OR tr.test_name='Blood Pressure')
AND tr.result NOT LIKE '%Normal%';
```

**Output:**
<img width="1173" height="401" alt="image" src="https://github.com/user-attachments/assets/7ffd5ecb-414c-49a9-b5a8-1fffc4c4f4e3" />


**Question 4**
---
<img width="1212" height="760" alt="image" src="https://github.com/user-attachments/assets/db241ac2-569b-4be5-af4f-8e8aa2d03ecf" />


```sql
SELECT c.cust_name, c.city, o.ord_no, o.ord_date, o.purch_amt AS "Order Amount", s.name, s.commission
FROM customer c
LEFT OUTER JOIN orders o ON c.customer_id=o.customer_id
LEFT OUTER JOIN salesman s ON o.salesman_id=s.salesman_id;
```

**Output:**

<img width="1181" height="888" alt="image" src="https://github.com/user-attachments/assets/4ed5d9e1-c2d0-4772-8682-5fc27660c41f" />


**Question 5**
---
<img width="1208" height="668" alt="image" src="https://github.com/user-attachments/assets/f8184c9d-7840-40d0-b086-ec7c96c0a62e" />


```sql
SELECT s.name
FROM salesman AS s
LEFT JOIN Customer AS c ON s.salesman_Id=c.salesman_Id
WHERE c.city='New York';
```

**Output:**

<img width="620" height="371" alt="image" src="https://github.com/user-attachments/assets/bed23e5a-456f-488e-9d99-3c83a296c083" />


**Question 6**
---
<img width="1210" height="755" alt="image" src="https://github.com/user-attachments/assets/1cbf4386-2560-4eec-95a6-7d5bbb8eb120" />


```sql
SELECT a.cust_name, a.city, b.ord_no, b.ord_date, b.purch_amt AS "Order Amount"
FROM customer a
LEFT OUTER JOIN orders b
ON a.customer_id=b.customer_id
ORDER BY b.ord_date;
```

**Output:**

<img width="1188" height="895" alt="image" src="https://github.com/user-attachments/assets/07c1fdd7-eb07-4610-8bbc-87ee4ab50522" />


**Question 7**
---
<img width="1211" height="886" alt="image" src="https://github.com/user-attachments/assets/c7fd70d1-7e2f-4941-a587-10a0304f62f7" />


```sql
SELECT C.cust_name
FROM CUSTOMER C
LEFT JOIN ORDERS O ON C.customer_id=O.customer_id;
```

**Output:**

<img width="841" height="891" alt="image" src="https://github.com/user-attachments/assets/05e4c0ca-0e6c-4798-be8f-fadbf2e128a0" />


**Question 8**
---
<img width="1206" height="632" alt="image" src="https://github.com/user-attachments/assets/d9199529-bcaa-41a5-8939-49a0735ddc44" />


```sql
SELECT p.first_name AS patient_name
FROM patients p
JOIN doctors d ON p.doctor_id=d.doctor_id
WHERE d.first_name='Emily' AND d.last_name='Johnson';
```

**Output:**

<img width="601" height="389" alt="image" src="https://github.com/user-attachments/assets/c535ff8d-b50d-4f30-93dc-9b1c78685b83" />


**Question 9**
---
<img width="1197" height="749" alt="image" src="https://github.com/user-attachments/assets/fa02d3f4-177a-4987-999d-4785b0e29476" />


```sql
SELECT s.name, c.cust_name, c.city, c.grade, c.salesman_id
FROM salesman s
LEFT JOIN customer c ON s.salesman_id=c.salesman_id
WHERE s.salesman_id IN(
SELECT salesman_id
FROM customer
GROUP BY salesman_id
HAVING COUNT(*)>1);
```

**Output:**

<img width="1179" height="609" alt="image" src="https://github.com/user-attachments/assets/8063ed98-a80b-4224-82be-ba4897621396" />


**Question 10**
---
<img width="1224" height="849" alt="image" src="https://github.com/user-attachments/assets/fcb78d96-c6fb-41ef-ae19-1ca6622bb4fb" />


```sql
SELECT s.name AS "salesman_name", c.cust_name AS "customer_name"
FROM salesman s
LEFT JOIN customer c
ON s.salesman_id=c.salesman_id;
```

**Output:**

<img width="943" height="882" alt="image" src="https://github.com/user-attachments/assets/cef7faf1-2412-46fd-9aa3-7fedd04dc553" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

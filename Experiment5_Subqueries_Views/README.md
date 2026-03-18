# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1215" height="809" alt="image" src="https://github.com/user-attachments/assets/df2ca94b-2fd1-40d3-9b54-fc33ccae7ac5" />


```sql
SELECT O.ord_no, O.purch_amt, O.ord_date, O.customer_id, O.salesman_id 
FROM ORDERS O
JOIN SALESMAN S ON O.salesman_id=S.salesman_id
WHERE S.city='New York';
```

**Output:**

<img width="1177" height="464" alt="image" src="https://github.com/user-attachments/assets/63ae1a8d-95ef-463a-85fb-f41fc35e7cc7" />


**Question 2**
---
<img width="1122" height="500" alt="image" src="https://github.com/user-attachments/assets/33fde0ed-1bab-4130-b5ca-368b88d86c51" />


```sql
SELECT * FROM Medications WHERE dosage=(SELECT MAX(dosage) FROM Medications);
```

**Output:**

<img width="972" height="378" alt="image" src="https://github.com/user-attachments/assets/96598e51-8ea1-4824-a02f-c0b16804c9eb" />


**Question 3**
---
<img width="966" height="512" alt="image" src="https://github.com/user-attachments/assets/aee82c44-d204-4389-98dc-adeaa6d2532e" />


```sql
SELECT * FROM Medications WHERE dosage=(SELECT MIN(dosage) FROM Medications);
```

**Output:**

<img width="875" height="379" alt="image" src="https://github.com/user-attachments/assets/32b7fd9b-0104-48f0-bca1-c56397053ec0" />


**Question 4**
---
<img width="1244" height="633" alt="image" src="https://github.com/user-attachments/assets/a51bd92a-3925-4405-b125-6783244ac43f" />


```sql
SELECT * FROM ORDERS 
WHERE purch_amt>(SELECT AVG(purch_amt) FROM ORDERS
                WHERE ord_date = '2012-10-10' );
```

**Output:**

<img width="1176" height="440" alt="image" src="https://github.com/user-attachments/assets/6a5a29de-edba-42c5-9791-29f0d1324ac3" />


**Question 5**
---
<img width="1041" height="720" alt="image" src="https://github.com/user-attachments/assets/c94275f5-68d4-4edf-b543-e4e92e27ae16" />



```sql
SELECT * FROM CUSTOMERS WHERE SALARY>1500;
```

**Output:**

<img width="1180" height="592" alt="image" src="https://github.com/user-attachments/assets/7d95c21f-cd81-42e6-a675-bcb19c331934" />

**Question 6**
---
<img width="1153" height="620" alt="image" src="https://github.com/user-attachments/assets/31f51292-a4d4-494c-b6b5-4b1cb69d52dc" />


```sql
SELECT * FROM CUSTOMERS 
WHERE ADDRESS='Delhi';
```

**Output:**
<img width="1181" height="328" alt="image" src="https://github.com/user-attachments/assets/0f500c0f-e81b-4566-bb20-af3d3cc1442e" />


**Question 7**
---
<img width="1174" height="637" alt="image" src="https://github.com/user-attachments/assets/dcc4decc-4978-46ae-b7eb-1a1319b377ac" />


```sql
SELECT * FROM CUSTOMERS
WHERE ADDRESS='Delhi' AND AGE<30
ORDER BY ID;
```

**Output:**

<img width="1179" height="356" alt="image" src="https://github.com/user-attachments/assets/e1486d13-6c9e-4956-ba32-394a03189114" />


**Question 8**
---
<img width="1184" height="714" alt="image" src="https://github.com/user-attachments/assets/d45c4a0b-dd10-4b53-889c-6dbc62c17e13" />


```sql
SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c ON s.salesman_id=c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id)>1;
```

**Output:**

<img width="970" height="459" alt="image" src="https://github.com/user-attachments/assets/46442816-b38c-4462-a209-9d3fb7d717ff" />

**Question 9**
---
<img width="1208" height="576" alt="image" src="https://github.com/user-attachments/assets/3c947676-4e3a-44f9-b874-b468cba742f1" />


```sql
SELECT name FROM customer
WHERE phone IN( SELECT phone FROM customer
                    GROUP BY phone
                    HAVING COUNT(phone)=1);
```

**Output:**

<img width="600" height="438" alt="image" src="https://github.com/user-attachments/assets/d205b3ed-30d0-40ad-ba66-f6a85b4abeb3" />


**Question 10**
---
<img width="1145" height="539" alt="image" src="https://github.com/user-attachments/assets/a1a68091-474e-4cea-8374-3e3029a29056" />


```sql
SELECT name, city FROM customer
WHERE city IN(SELECT city FROM customer
                WHERE id IN (3,7));
```

**Output:**

<img width="727" height="437" alt="image" src="https://github.com/user-attachments/assets/8e5794c0-9298-4ba6-97ba-e00f057f4407" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

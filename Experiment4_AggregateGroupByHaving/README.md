# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
<img width="1203" height="530" alt="image" src="https://github.com/user-attachments/assets/ba86602d-114a-41c2-be1e-23cabc07e6e2" />


```sql
SELECT COUNT(DISTINCT customer_id) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
```

**Output:**
<img width="1140" height="296" alt="image" src="https://github.com/user-attachments/assets/616fd36e-c0d9-4ec1-b3a0-ee1f43863b99" />


**Question 2**
---
<img width="1214" height="469" alt="image" src="https://github.com/user-attachments/assets/4488591d-7cae-476a-82cd-cc57daccbfcf" />

```sql
<img width="1214" height="469" alt="image" src="https://github.com/user-attachments/assets/d4d741e7-3d06-4f0e-8dc7-7645029f577a" />
```

**Output:**

<img width="1161" height="293" alt="image" src="https://github.com/user-attachments/assets/ee4b2408-5fc3-40ae-ac02-9ead77464870" />

**Question 3**
---
<img width="1150" height="475" alt="image" src="https://github.com/user-attachments/assets/090b17e6-d856-4cc5-b714-f01f1d078936" />

```sql
SELECT COUNT(DISTINCT city) AS unique_cities
FROM customer;
```

**Output:**
<img width="1083" height="286" alt="image" src="https://github.com/user-attachments/assets/0ce7929a-80df-479b-9df7-73b9820e723b" />


**Question 4**
---
<img width="956" height="645" alt="image" src="https://github.com/user-attachments/assets/37fbbe74-9914-4dd2-869c-72391a317b36" />


```sql
SELECT InsuranceCompany, COUNT(PatientID) AS TotalPatients
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

<img width="1071" height="666" alt="image" src="https://github.com/user-attachments/assets/de6ea558-f6cf-49c0-ac72-b8c87b7369cf" />

**Question 5**
---
<img width="1200" height="581" alt="image" src="https://github.com/user-attachments/assets/c3e3e987-2190-49a7-aa38-b17c966e532a" />


```sql
SELECT Specialty,Gender,COUNT(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty,Gender;
```

**Output:**

<img width="925" height="633" alt="image" src="https://github.com/user-attachments/assets/234375f8-0acc-4292-871b-91e72502268f" />


**Question 6**
---
<img width="1044" height="581" alt="image" src="https://github.com/user-attachments/assets/7f4cc2ef-ee72-4e9e-9232-41ed363f20f5" />


```sql
SELECT PatientID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

<img width="681" height="627" alt="image" src="https://github.com/user-attachments/assets/81c4b343-56e3-4c8d-84ce-2a7333208a91" />

**Question 7**
---<img width="1222" height="562" alt="image" src="https://github.com/user-attachments/assets/c1e4898d-79ef-4eea-8ca3-9c612181f9e1" />


```sql
SELECT occupation, MIN(workhour)
FROM employee1
GROUP BY occupation
HAVING MIN(workhour)>8
```

**Output:**

<img width="820" height="456" alt="image" src="https://github.com/user-attachments/assets/92b23394-7a9d-426e-891d-8562ef149ebc" />


**Question 8**
---
<img width="1223" height="501" alt="image" src="https://github.com/user-attachments/assets/00870936-7e54-4ef3-94e3-5e8299e64a2f" />


```sql
SELECT jdate, MAX(workhour)
FROM employee1
GROUP BY jdate
HAVING MAX(workhour)>12;
```

**Output:**

<img width="776" height="359" alt="image" src="https://github.com/user-attachments/assets/4cdb4a51-9685-4414-9437-998db306d244" />


**Question 9**
---
<img width="1182" height="511" alt="image" src="https://github.com/user-attachments/assets/b0745abd-a1da-4de7-bfb6-740d7d69cb9f" />


```sql
SELECT category_id, product_name, MAX(price) AS Price
FROM products 
GROUP BY category_id
HAVING MAX(price)>15;
```

**Output:**

!<img width="910" height="346" alt="image" src="https://github.com/user-attachments/assets/b0be383d-2418-4c83-88d0-326d9ca150f5" />


**Question 10**
---
<img width="937" height="579" alt="image" src="https://github.com/user-attachments/assets/1baa19ff-8fda-436d-a82f-0cc0752a7e25" />


```sql
SELECT address, AVG(salary)
FROM customer1
GROUP BY address
HAVING AVG(salary)<15000.0;
```

**Output:**
<img width="1190" height="590" alt="image" src="https://github.com/user-attachments/assets/ebdd4c83-2940-403c-aa77-4bbcda530c50" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

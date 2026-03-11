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
<img width="1227" height="372" alt="image" src="https://github.com/user-attachments/assets/7e084829-c8e9-4441-a133-95d2359c6c6b" />


```sql
CREATE TABLE Products(
    ProductID PRIMARY KEY,
    ProductName NOT NULL,
    Price REAL CHECK(Price>0),
    Stock INTEGER CHECK(Stock>=0)
)
```

**Output:**

<img width="1185" height="256" alt="image" src="https://github.com/user-attachments/assets/e88ea190-ba54-4e49-8cbe-a14ae5d83fdb" />


**Question 2**
---
<img width="1217" height="475" alt="image" src="https://github.com/user-attachments/assets/c279073f-887b-420a-8768-9fccfd00110f" />


```sql
CREATE TABLE item(
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT(4),
    Foreign Key(icom_id) REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE
)
```

**Output:**

<img width="1181" height="336" alt="image" src="https://github.com/user-attachments/assets/08383ae1-166d-4831-9630-391077066b65" />


**Question 3**
---
<img width="1225" height="361" alt="image" src="https://github.com/user-attachments/assets/79d674ec-3d5e-4d55-8950-d2b1692b4f36" />


```sql
INSERT INTO Books
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM Out_of_print_books;
```

**Output:**

<img width="1184" height="271" alt="image" src="https://github.com/user-attachments/assets/95a0429d-b6dd-4bfe-8727-4ca3e89ba3c5" />

**Question 4**
---
<img width="1228" height="500" alt="image" src="https://github.com/user-attachments/assets/74ff395f-4f96-4f6d-9e57-1fb4354f6f9d" />

```sql
INSERT INTO Student_details
SELECT RollNo, Name, Gender, Subject, MARKS
FROM Archived_students;
```

**Output:**

<img width="1183" height="273" alt="image" src="https://github.com/user-attachments/assets/2da4d2c6-0fb9-4489-9f9e-0e65d1b53cba" />


**Question 5**
---
<img width="1233" height="619" alt="image" src="https://github.com/user-attachments/assets/07cc48ea-46a8-4e28-9b69-5aa5e15bc967" />


```sql
ALTER TABLE Student_details
ADD COLUMN Mobilenumber number;
```

**Output:**

<img width="1184" height="348" alt="image" src="https://github.com/user-attachments/assets/25d897b8-c998-4957-b180-f8336dfef377" />


**Question 6**
---
<img width="1230" height="368" alt="image" src="https://github.com/user-attachments/assets/e554af75-40db-4a50-a39f-fd63a4cfdf38" />

```sql
CREATE TABLE Orders(
    OrderID INTEGER PRIMARY KEY,
    OrderDate DATE NOT NULL,
    CustomerID INTEGER,
    FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID)
)
```

**Output:**

<img width="1192" height="274" alt="image" src="https://github.com/user-attachments/assets/4bcd7754-e0eb-4342-b24e-f7eec64753e3" />


**Question 7**
---
<img width="1227" height="438" alt="image" src="https://github.com/user-attachments/assets/7d668e7d-6ab7-4b95-90ea-154dac86d323" />


```sql
CREATE TABLE Employees(
    EmployeeID INTEGER PRIMARY KEY,
    FirstName TEXT NOT NULL,
    LastName TEXT NOT NULL,
    Email TEXT UNIQUE,
    Salary INTEGER CHECK(Salary>0),
    DepartmentID INTEGER,
    Foreign Key(DepartmentID) References Departments(DepartmentID)
)
```

**Output:**

<img width="1184" height="418" alt="image" src="https://github.com/user-attachments/assets/55370874-ca33-4d06-8660-92485d61b141" />


**Question 8**
---
<img width="1234" height="438" alt="image" src="https://github.com/user-attachments/assets/fd834c7d-fc47-4843-8992-132f4878c4e0" />


```sql
CREATE TABLE contacts(
    contact_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT,
    phone TEXT NOT NULL CHECK(LENGTH(phone)=10)
)
```

**Output:**

<img width="1187" height="311" alt="image" src="https://github.com/user-attachments/assets/4c38ef9c-1b6d-411a-9c71-23f6ec8bf1ac" />


**Question 9**
---
<img width="1210" height="450" alt="image" src="https://github.com/user-attachments/assets/65860b2a-a0d7-4d3c-bf88-5c8ec76f260d" />


```sql
ALTER TABLE Companies RENAME COLUMN name TO first_name;
ALTER TABLE Companies ADD COLUMN mobilenumber number;
ALTER TABLE Companies ADD COLUMN DOB Date;
ALTER TABLE Companies ADD COLUMN State varchar(30);
```

**Output:**

<img width="1185" height="394" alt="image" src="https://github.com/user-attachments/assets/54c0a10b-3317-42ce-bb80-4228b60e073f" />


**Question 10**
---
<img width="1228" height="272" alt="image" src="https://github.com/user-attachments/assets/7383db31-9009-425c-929f-3f66759b0ee7" />


```sql
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode) Values(301,'Michael Jordan','123 Maple St','Chicago',60616);
```

**Output:**

<img width="1179" height="227" alt="image" src="https://github.com/user-attachments/assets/671843fd-bcca-490b-9a0b-8a360b02eeae" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
<img width="1362" height="82" alt="image" src="https://github.com/user-attachments/assets/af98f7c6-5cbb-431b-8ab2-b9fde81cf2f8" />


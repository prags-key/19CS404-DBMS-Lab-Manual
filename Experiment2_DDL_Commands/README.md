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
<img width="952" height="395" alt="image" src="https://github.com/user-attachments/assets/6a6feebd-3659-4180-98ab-04aad57ce1f8" />


```sql
INSERT INTO Products(Name,Category,Price,Stock)VALUES
("Smartphone","Electronics",800,150),
("Headphones","Accessories",200,300);
```

**Output:**

<img width="1192" height="341" alt="image" src="https://github.com/user-attachments/assets/2ef0fea9-897d-432e-bcc4-9e953736453b" />



**Question 2**
---
<img width="955" height="450" alt="image" src="https://github.com/user-attachments/assets/d2fe2391-cf6e-462e-909b-0cae3b12a0ad" />


```sql
ALTER TABLE books ADD COLUMN ISBN varchar(30);
ALTER TABLE books ADD COLUMN domain_dep varchar(30);
```

**Output:**
<img width="1192" height="372" alt="image" src="https://github.com/user-attachments/assets/fa63fe0d-aaad-454d-89d0-50b49f576610" />



**Question 3**
---
<img width="1006" height="255" alt="image" src="https://github.com/user-attachments/assets/9d071155-a7ce-40ce-af08-add67d019e8b" />


```sql
create table Orders
(
OrderID  INTEGER primary key,
OrderDate  DATE  not NULL,
CustomerID  INTEGER  references Customers(CustomerID)
);
```

**Output:**
<img width="1293" height="160" alt="image" src="https://github.com/user-attachments/assets/b07dd8f1-e1d5-4fe2-a41a-149f60c60280" />


**Question 4**
---
<img width="947" height="218" alt="image" src="https://github.com/user-attachments/assets/bcb912e9-6462-4395-84cf-34c9e60f99c6" />


```sql
ALTER TABLE employee ADD first_name varchar(50);
ALTER TABLE employee ADD last_name varchar(50);
```

**Output:**
<img width="1152" height="187" alt="image" src="https://github.com/user-attachments/assets/be23ac5e-b031-46d5-8d06-a44266f3b8e2" />


**Question 5**
---
<img width="571" height="246" alt="image" src="https://github.com/user-attachments/assets/dd3c2c69-4e7c-4713-9663-0ffbc2fa3f77" />


```sql
INSERT INTO Products(ProductID, ProductName, Price, Stock)
select ProductID, ProductName, Price, Stock FROM Discontinued_products;
```

**Output:**
<img width="851" height="165" alt="image" src="https://github.com/user-attachments/assets/854cd4e8-6cdf-4a8b-9eee-4830f5c18e6a" />

**Question 6**
---
<img width="1047" height="252" alt="image" src="https://github.com/user-attachments/assets/ead66360-9343-445a-a570-519e09f6be2f" />


```sql
create table Attendance (
AttendanceID INTEGER primary key,
EmployeeID  INTEGER  references Employees(EmployeeID),
AttendanceDate  DATE,
Status  TEXT check(status=='Present' or status=='Absent' or status=='Leave')
);
```

**Output:**
<img width="1302" height="182" alt="image" src="https://github.com/user-attachments/assets/0b4e446f-d0de-4fc4-9ac4-705c3dea3a48" />



**Question 7**
---
<img width="872" height="273" alt="image" src="https://github.com/user-attachments/assets/c1a297d2-1273-4828-967a-948bbd150400" />


```sql
create table Employees(
EmployeeID INTEGER primary key,
FirstName varchar(30) NOT NULL,
LastName varchar(30) NOT NULL,
Email varchar(30) UNIQUE,
Salary INTEGER CHECK(Salary>0),
DepartmentID  INTEGER references  Departments(DepartmentID)
);
```

**Output:**
<img width="1301" height="258" alt="image" src="https://github.com/user-attachments/assets/e36b851c-e9cb-40d9-a601-fe563aa887f3" />


**Question 8**
---
<img width="807" height="155" alt="image" src="https://github.com/user-attachments/assets/01724311-4363-4c16-9e77-29c06fc8910b" />


```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
values(201,"David Lee","M","Physics",92);
```

**Output:**

<img width="1120" height="136" alt="image" src="https://github.com/user-attachments/assets/176e3c9d-1c35-47f0-8fa7-4bc8903831da" />


**Question 9**
---
<img width="1310" height="167" alt="image" src="https://github.com/user-attachments/assets/85c619b8-4cab-4c7b-b5b0-f603e3780f4f" />


```sql
create table jobs(
job_id INTEGER , 
job_title varchar(30) DEFAULT "",
min_salary INTEGER DEFAULT 8000,
max_salary INTEGER DEFAULT NULL
);

```

**Output:**
<img width="1298" height="215" alt="image" src="https://github.com/user-attachments/assets/369bafdb-d83a-4cc6-83ad-2ce66976710a" />




**Question 10**
---
<img width="757" height="237" alt="image" src="https://github.com/user-attachments/assets/87fa6108-5dcd-4160-8bcc-0c142c68c41e" />


```sql
CREATE TABLE Departments
(DepartmentID  INTEGER,
DepartmentName TEXT
);

```

**Output:**
<img width="1197" height="207" alt="image" src="https://github.com/user-attachments/assets/c28cc078-4ab0-4272-b761-bf4f08392e6a" />





## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
<img width="1237" height="62" alt="image" src="https://github.com/user-attachments/assets/82bf8a65-4624-4b1a-bae6-cc0bfaf89303" />


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

Create a table named Products with the following constraints:ProductID as INTEGER should be the primary key.ProductName as TEXT should be unique and not NULL.Price as REAL should be greater than 0.StockQuantity as INTEGER should be non-negative.

```
CREATE TABLE Products(
   ProductID INTEGER PRIMARY KEY,
   ProductName TEXT UNIQUE NOT NULL,
   Price REAL CHECK (Price>0),
   StockQuantity INTEGER CHECK (StockQuantity >= 0)
);
```

**Output:**

<img width="1809" height="211" alt="image" src="https://github.com/user-attachments/assets/17b150ac-d425-46bf-92c3-f83697708abf" />






**Question 2**

Create a table named Attendance with the following constraints:AttendanceID as INTEGER should be the primary key.EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).AttendanceDate as DATE.Status as TEXT should be one of 'Present', 'Absent', 'Leave'.


```
CREATE TABLE Attendance(
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT  CHECK (Status IN ('Present','Absent','Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1692" height="203" alt="image" src="https://github.com/user-attachments/assets/d54971e8-1239-4947-a30f-af9627c12d46" />



**Question 3**


Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.

```
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES(101,"Laptop","Electronics",1500,50)
```

**Output:**

<img width="1315" height="163" alt="image" src="https://github.com/user-attachments/assets/65661d23-fa28-4802-99e3-9ac84a32726d" />


**Question 4**

Create a table named Products with the following columns:ProductID as INTEGER,ProductName as TEXT,Price as REAL,Stock as INTEGER.


```
CREATE TABLE Products(
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);
```

**Output:**

<img width="1307" height="230" alt="image" src="https://github.com/user-attachments/assets/871f38d0-3759-4f7e-b5e5-8dcbe993cdb4" />


**Question 5**

Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:designation as VARCHAR(50),net_salary as NUMBER,dob as DATE.


```
ALTER TABLE Companies
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number;

ALTER TABLE Companies
ADD COLUMN dob date;
```

**Output:**

<img width="1430" height="302" alt="image" src="https://github.com/user-attachments/assets/83b81f7a-62be-49a6-b12f-b57c39c258e5" />


**Question 6**

Insert the following students into the Student_details table:


```
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(202,"Ella King","F","Chemistry",87),(203,"James Bond","M","Literature",78);
```

**Output:**

<img width="1214" height="177" alt="image" src="https://github.com/user-attachments/assets/c4b22fe3-81fb-44f9-87be-59c4de8b4afb" />


**Question 7**

Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

```
ALTER TABLE customer
ADD COLUMN birth_date timestamp;
```

**Output:**

<img width="1685" height="253" alt="image" src="https://github.com/user-attachments/assets/1bb9f96c-6685-445b-bcd4-ab475ba5d118" />


**Question 8**

Create a table named ProjectAssignments with the following constraints:AssignmentID as INTEGER should be the primary key.EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).AssignmentDate as DATE should be NOT NULL

```
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN kEY (ProjectID) REFERENCES Projects(ProjectID)
);
```


**Output:**

<img width="1704" height="198" alt="image" src="https://github.com/user-attachments/assets/e194a4a7-bd61-4670-8ebc-5eb8f73a823d" />


**Question 9**

Create a table named Departments with the following columns:DepartmentID as INTEGER,DepartmentName as TEXT

```
CREATE TABLE Departments(
   DepartmentID INTEGER,
   DepartmentName TEXT
);
```

**Output:**

<img width="1466" height="242" alt="image" src="https://github.com/user-attachments/assets/10d29483-e7db-45da-a1ac-5d835311664f" />


**Question 10**

Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

```
INSERT INTO Student_details(RollNO,Name,Gender)
VALUES(204,"Samuel Black","M");
```

**Output:**

<img width="939" height="235" alt="image" src="https://github.com/user-attachments/assets/37e01190-8818-45c3-b273-f5b52a0ad330" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

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
-- Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
-- alter table Companies add column designation varchar(50);
--alter table Companies add column net_salary number;
```

**Output:**
![image](https://github.com/user-attachments/assets/1d10eaa9-049a-42cd-9014-e489416f2757)


**Question 2**
---
-- Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.

```sql
-- insert into Customers(CustomerID,Name,Address)
-- values(304,'Peter Parker','Spider St')
```

**Output:**

![image](https://github.com/user-attachments/assets/27d283a0-8965-4f06-a72e-e156b042a895)

**Question 3**
---
-- Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
--  create table Department(
-- DepartmentID INTEGER primary key,
-- DepartmentName TEXT unique not null,
-- Location TEXT
)
```

**Output:**

![image](https://github.com/user-attachments/assets/78be5014-bd1a-44e8-96e4-76a27190b738)


**Question 4**
---
-- Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
--create table Invoices(
--InvoiceID INTEGER primary key,
--InvoiceDate DATE,
--Amount REAL,
--DueDate DATE,
--OrderID INTEGER,
--CHECK(Amount >0 and DueDate > InvoiceDate),
--foreign key (OrderID) references Orders(OrderID)
)
```

**Output:**
![image](https://github.com/user-attachments/assets/e8e8e924-2585-46ad-a5f8-72b450b60094)


**Question 5**
---
-- Insert all customers from Old_customers into Customers
  Table attributes are CustomerID, Name, Address, Email

```sql
-- insert into Customers(CustomerID, Name, Address, Email)
-- select CustomerID, Name, Address, Email from Old_customers
```

**Output:**
![image](https://github.com/user-attachments/assets/89d36eef-9895-4f4e-9542-dd2b2d50f5ce)


**Question 6**
---
-- Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE

```sql
-- create table Employees(
-- EmployeeID INTEGER,
-- FirstName TEXT,
-- LastName TEXT,
-- HireDate DATE
)
```

**Output:**
![image](https://github.com/user-attachments/assets/162c9230-0a98-4b5a-98d0-e3771687f922)


**Question 7**
---
-- Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
-- create table ProjectAssignments(
-- AssignmentID int primary key,
-- EmployeeID int ,
-- ProjectID int,
-- AssignmentDate Date not null,
-- foreign key (EmployeeID) references Employees(EmployeeID),
-- foreign key (ProjectID) references Projects(ProjectID)
)
```

**Output:**
![image](https://github.com/user-attachments/assets/e34d7616-9fbe-403f-88ca-389af486a255)


**Question 8**
---
-- Write a SQL query for adding a new column named "email" with the datatype VARCHAR(100) to the  table "customer" 

Sample table: customer

```sql
-- alter table customer add column email VARCHAR(100);
```

**Output:**
![image](https://github.com/user-attachments/assets/c609fb53-122b-4988-8f36-4b05b1a4ec9d)


**Question 9**
---
--In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
-- insert into Employee (EmployeeID,Name, Position)
-- values(5,'George Clark','Consultant');
-- insert into Employee (EmployeeID,Name, Position, Department, Salary)
-- values(7,'Noah Davis','Manager','HR',60000);
-- insert into Employee (EmployeeID,Name, Position, Department)
-- values(8,'Ava Miller','Consultant','IT');
```

**Output:**
![image](https://github.com/user-attachments/assets/c3393393-8769-495b-9ca7-deed8f4b6b50)


**Question 10**
---
-- Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
-- create table Products(
-- ProductID int primary key,
-- ProductName text unique not null,
-- Price REAL ,
-- StockQuantity int,
-- CHECK(Price>0 and StockQuantity>0)
)
```

**Output:**
![image](https://github.com/user-attachments/assets/eca26191-b1e1-40db-aa83-8d603ab7cad3)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

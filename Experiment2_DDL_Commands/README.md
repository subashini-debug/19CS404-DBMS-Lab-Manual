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

Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

## CODE:
```
create table Employees(
EmployeeID int primary key ,
FirstName varchar(100) not null,
Lastname varchar(100) not null,
Email varchar(255) not null unique,
Salary decimal(10,2) check (salary>0),
DepartmentID int not null,
Foreign key (DepartmentID) references Departments(DepartmentID)
);
```
## OUTPUT:

<img width="1253" height="727" alt="Screenshot 2026-08-26 173934" src="https://github.com/user-attachments/assets/fac5a358-9fc5-4492-ad47-3378c392bede" />


**Question 2**

Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE

## CODE:
```
create table Tasks( TaskID INTEGER,TaskName TEXT,DueDate DATE);
```
## OUTPUT:

<img width="1230" height="713" alt="Screenshot 2026-08-26 173952" src="https://github.com/user-attachments/assets/78c8893e-bd64-4496-9179-51bd2a910984" />


**Question 3**

In the Cusomers table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

CustomerID  Name          Address      City        ZipCode
----------  ------------  ----------   ----------  ----------
306         Diana Prince  Themyscira
307         Bruce Wayne   Wayne Manor  Gotham      10007
308         Peter Parker  Queens                   11375

## CODE:
```
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode)
VALUES(306,'Diana Prince','Themyscira',null,null);
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode)
VALUES(307,'Bruce Wayne','Wayne Manor','Gotham',10007);
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode)
VALUES(308,'Peter Parker','Queens',null,11375);
```
## OUTPUT:

<img width="1166" height="615" alt="Screenshot 2026-08-26 174009" src="https://github.com/user-attachments/assets/5db37da1-0ead-41a0-b4f6-1feb2d88cff9" />


**Question 4**

Write an SQL command can to add a column named email of type TEXT to the customers table

## CODE:
```
ALTER TABLE Customers ADD COLUMN email TEXT;
```

**Output:**

<img width="1190" height="625" alt="Screenshot 2026-08-26 174023" src="https://github.com/user-attachments/assets/9d2f5b26-a2c9-4218-8c78-35741a94f3ee" />


**Question 5**

Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

## CODE:
```
INSERT INTO Books(ISBN,Title,Author,Publisher,YearPublished)
select ISBN,Title,Author,Publisher,YearPublished
From Out_of_print_books;
```

**Output:**

<img width="1232" height="637" alt="Screenshot 2026-08-26 174035" src="https://github.com/user-attachments/assets/37ac569a-aa23-4103-a1a5-fd9a55cd4064" />


**Question 6**

Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

## CODE:
```
create table contacts(
contact_id int primary key,first_name text not null,last_name text not null,email text,
phone text not null check(LENGTH(phone)>=10));
```

**Output:**

<img width="1266" height="667" alt="Screenshot 2026-08-26 174046" src="https://github.com/user-attachments/assets/4d69fd02-677a-4e5b-bc7f-0229b981658d" />


**Question 7**

Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

## CODE:
```
create table ProjectAssignments(AssignmentID int primary key,
EmployeeID int references Employees(EmployeeID),ProjectID int references Projects(ProjectID),
AssignmentDate date not null);
```

**Output:**

<img width="1227" height="647" alt="Screenshot 2026-08-26 174058" src="https://github.com/user-attachments/assets/c34b81da-5578-46c3-b462-356131b2e5c6" />


**Question 8**

Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.

## CODE:
```
create table Attendance(
AttendanceID int primary key,
EmployeeID int references Employees(EmployeeID),
AttendanceDate date,
Status text check (Status IN ('Present','Absent','LEave')));
```

**Output:**

<img width="1247" height="615" alt="Screenshot 2026-08-26 174111" src="https://github.com/user-attachments/assets/2c35e962-9e17-48e7-bd44-2705d5f11673" />


**Question 9**

Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.

## CODE:
```
ALTER TABLE Employees ADD COLUMN salary INTEGER check(salary>0);
```

**Output:**

<img width="1238" height="631" alt="Screenshot 2026-08-26 174122" src="https://github.com/user-attachments/assets/0af22e8c-850d-4638-b3f7-b0908adb9484" />


**Question 10**

Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default values.

## CODE:
```
INSERT INTO Products(ProductID,Name,Category) VALUES (104,'Tablet','Electronics');
```

**Output:**

<img width="1240" height="632" alt="Screenshot 2026-08-26 174136" src="https://github.com/user-attachments/assets/918123e9-7b80-4d55-ae30-fec954a04a2b" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

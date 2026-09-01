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
## Question 1

Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.
```
Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```

## CODE;
```
update Employees set hire_date='2024-01-24'
where department_id=50;
```

**Output:**

<img width="1206" height="262" alt="Screenshot 2026-08-29 191452" src="https://github.com/user-attachments/assets/901a3160-5e1b-45f5-ab99-8f5ad9b93284" />


## Question 2

For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE
```
name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
```

## CODE:

```
update Products
set sell_price=CAST(cost_price*1.35 as int)
where ((sell_price-cost_price)/sell_price)*100<30;
```

**Output:**

<img width="1190" height="536" alt="Screenshot 2026-08-29 191506" src="https://github.com/user-attachments/assets/cb536b74-3e91-416b-b7d1-f952c5e3119a" />


## Question 3

Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules.

Salary will be increased by 25% for the department 40, 15% for department 90 and 10% for the department 110 and the rest of the departments will remain same.
```
Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```

## CODE:

```
UPDATE Employees set salary =CASE
when department_id=40 then round(salary*1.25)
when department_id=90 then round(salary*1.15)
when department_id=110 then round(salary*1.1)
else salary
end;
```

**Output:**

<img width="1192" height="512" alt="Screenshot 2026-08-29 191519" src="https://github.com/user-attachments/assets/7e83b015-5043-4c88-94cb-5dd1bacbc580" />



## Question 4

Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.
```
Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```

## CODE:

```
update Employees set email='not available' ,commission_pct=0.55
where department_id=110;
```

**Output:**

<img width="1218" height="447" alt="Screenshot 2026-08-29 191548" src="https://github.com/user-attachments/assets/0dfb14b3-fd28-470c-892d-806c2d8cfe92" />

## Question 5

Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 
```
name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT           
```

## CODE:

```update Products
set category='Household' where product_name LIKE '%Detergent%';
```

**Output:**

<img width="1203" height="540" alt="Screenshot 2026-08-29 191558" src="https://github.com/user-attachments/assets/d226c064-8ca1-4192-b8a1-fd337bfdec63" />


## Question 6

Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.
```
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```

## CODE:

```
delete from customer where length(CUST_NAME)=6;
```

**Output:**

<img width="1210" height="788" alt="Screenshot 2026-08-29 191613" src="https://github.com/user-attachments/assets/3c2af222-baa7-441c-9469-4c270176cc4c" />


## Question 7

Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer
```
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```

## CODE:

```
delete from customer
where CUST_NAME like '%Holmes%';
```

**Output:**

<img width="1200" height="612" alt="Screenshot 2026-08-29 191623" src="https://github.com/user-attachments/assets/85edbe60-fb09-4f48-8b0f-7a09284ea58e" />


## Question 8

Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

Sample table: Customer
```
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```

## CODE:
```
delete from customer
where(GRADE>2 and PAYMENT_AMT<(select avg(payment_amt) from customer))
or outstanding_amt>8000;
```

**Output:**

<img width="1186" height="695" alt="Screenshot 2026-08-29 191635" src="https://github.com/user-attachments/assets/6ba4a780-3399-4867-a7dc-911173a59cf9" />


## Question 9

Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

Sample table: Customer
```
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```

## CODE:
```
delete from customer where cust_country='UK'
and working_area='London'
and grade<3;
```

**Output:**

<img width="1222" height="532" alt="Screenshot 2026-08-29 191644" src="https://github.com/user-attachments/assets/5be2c464-97f3-4240-85af-d90a1133b78a" />


## Question 10

Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

## CODE:
```
delete from doctors
where specialization is null;
```

**Output:**

<img width="1163" height="845" alt="Screenshot 2026-08-29 191703" src="https://github.com/user-attachments/assets/31ee4cd8-ec44-4cbb-a401-b575b84ec6dd" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

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

## Question 1

What is the most common diagnosis among patients?

Sample table:MedicalRecords Table

## CODE:
```
select diagnosis,count(diagnosis) as DiagnosisCount from MedicalRecords group by diagnosis order by diagnosiscount desc limit 1;
```

**Output:**

<img width="817" height="255" alt="Screenshot 2026-08-29 193540" src="https://github.com/user-attachments/assets/5024e919-2042-428c-ab61-a767a0852881" />

## Question 2

What is the count of male and female patients?

Sample table: Patients Table

## CODE:
```
select gender,count(patientid) as TotalPatients from Patients group by gender order by gender asc;
```

**Output:**

<img width="691" height="392" alt="Screenshot 2026-08-29 193546" src="https://github.com/user-attachments/assets/cadfb06e-b681-4a5b-b3bb-ccefdd41a138" />

## Question 3

What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table

## CODE:
```
select doctorid,count('AppointmentDat...') as TotalAppointments from Appointments group by doctorId order by doctorid asc;
```

**Output:**

<img width="761" height="607" alt="Screenshot 2026-08-29 193553" src="https://github.com/user-attachments/assets/10a462d7-dd74-4e2c-80b8-87363597e0f4" />

## Question 4

Write a SQL query to find the maximum purchase amount.

Sample table: orders
```
ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```

## CODE:
```
select max(purch_amt) as MAXIMUM from orders;
```

**Output:**

<img width="523" height="360" alt="Screenshot 2026-08-29 193559" src="https://github.com/user-attachments/assets/f862c6c5-f458-4c83-9b7d-e55fb66c038c" />


## Question 5

Write a SQL query to find the average length of email addresses (in characters):

Table: customer
```
name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
```

## CODE:
```
select avg(length(email)) as avg_email_length from customer;
```

**Output:**

<img width="532" height="348" alt="Screenshot 2026-08-29 193604" src="https://github.com/user-attachments/assets/b76f71b6-c660-423c-9e62-b487d37a1081" />

## Question 6

Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders
```
ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```
## CODE:
```
select sum(purch_amt) as TOTAL from orders;
```

**Output:**

<img width="600" height="372" alt="Screenshot 2026-08-29 193609" src="https://github.com/user-attachments/assets/2f93e73e-cf68-4478-b179-2646f4487726" />

## Question 7

Write a SQL query to find all employees along with the day of the week on which they were hired from the emp table

emp table

```
cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT
```


## CODE:
```
SELECT ename,hiredate,
CASE strftime('%w',hiredate)
WHEN '0' THEN 'Sunday'
WHEN '1' THEN 'Monday'
WHEN '2' THEN 'Tuesday'
WHEN '3' THEN 'Wednesday'
WHEN '4' THEN 'Thursday'
WHEN '5' THEN 'Friday'
WHEN '6' THEN 'Saturday'
END AS day_of_week
FROM emp;
```

**Output:**

<img width="603" height="243" alt="Screenshot 2026-08-29 193620" src="https://github.com/user-attachments/assets/75a9286f-0ae0-4ebc-b33a-c6cb11f7ddae" />

## Question 8

Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1

## CODE:
```
select occupation,sum(workhour) as 'SUM(workhour)' from employee1 group by occupation having sum(workhour)>20;
```

**Output:**

<img width="641" height="400" alt="Screenshot 2026-08-29 193632" src="https://github.com/user-attachments/assets/fea18274-10be-4ec1-9681-a87152e10b77" />

## Question 9

Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Sample table: customer1

## CODE:
```
select (age/5)*5 as age_group,AVG(age) from customer1 group by age_group having avg(age)<24 order by age_group;
```

**Output:**

<img width="631" height="345" alt="Screenshot 2026-08-29 193636" src="https://github.com/user-attachments/assets/58cb8fe1-c35b-4606-9625-35a97fe750d7" />

## Question 10

Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.

Sample table: employee1


## CODE:
```
select jdate,AVG(workhour) from employee1 group by jdate having avg(workhour)<10;
```

**Output:**

<img width="657" height="385" alt="Screenshot 2026-08-29 193642" src="https://github.com/user-attachments/assets/540c5fdf-aa06-4245-a6a3-a8ae5c499416" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

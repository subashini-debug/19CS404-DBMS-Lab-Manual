# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Greater number is: 80
### program:
```
DECLARE
    a NUMBER := 50;
    b NUMBER :=80;
BEGIN
    IF a > b THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
    END IF;
END;
```
### OUTPUT:
<img width="306" height="141" alt="Screenshot 2026-08-25 102252" src="https://github.com/user-attachments/assets/7c574725-ef81-4103-9ada-4d0ab3715d88" />

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55
### PROGRAM:
```
DECLARE
    n NUMBER := 10;
    i NUMBER := 1;
    sum NUMBER := 0;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
```
### OUTPUT
<img width="332" height="161" alt="Screenshot 2026-08-25 102623" src="https://github.com/user-attachments/assets/3e4b79c2-6af4-449d-827a-8362377ab083" />

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
### PROGRAM:
~~~
DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 1;
BEGIN
    DBMS_OUTPUT.PUT('Fibonacci sequence: ');

    WHILE i <= n LOOP
        DBMS_OUTPUT.PUT(a || ' ');

        c := a + b;
        a := b;
        b := c;

        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.NEW_LINE;
END;
~~~

### OUTPUT:
<img width="302" height="136" alt="Screenshot 2026-08-25 103111" src="https://github.com/user-attachments/assets/7625c7e9-0a09-4cf1-97e5-2aab9efb7c58" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351
### PROGRAM:
```
DECLARE
    n NUMBER := 1535;
    rev NUMBER := 0;
    digit NUMBER;
BEGIN
    WHILE n > 0 LOOP
        digit := MOD(n, 10);
        rev := rev * 10 + digit;
        n := TRUNC(n / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reversed number is: ' || rev);
END;
```

### OUTPUT:
<img width="337" height="155" alt="Screenshot 2026-08-25 103316" src="https://github.com/user-attachments/assets/f4fdb4e8-abdf-4383-a4bf-7591145670e3" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

### PROGRAM
```
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
    largest NUMBER;
BEGIN
    IF a >= b AND a >= c THEN
        largest := a;
    ELSIF b >= a AND b >= c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;

    DBMS_OUTPUT.PUT_LINE('Largest of three numbers is: ' || largest);
END;
```
### OUTPUT:
<img width="320" height="147" alt="Screenshot 2026-08-25 103439" src="https://github.com/user-attachments/assets/72479b3f-0330-419e-9582-3aeedb9abb14" />

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

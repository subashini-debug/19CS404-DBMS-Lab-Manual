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

### CODE:
```sql
DECLARE
    num1 NUMBER := &num1;
    num2 NUMBER := &num2;
BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greatest number is: ' || num1);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greatest number is: ' || num2);
    END IF;
END;
/
```

**Expected Output:**  
Greater number is: 80


### OUTPUT:


<img width="957" height="278" alt="Screenshot 2026-08-25 102423" src="https://github.com/user-attachments/assets/2674e22d-83b6-4415-8914-78dcad7e94ab" />





---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

### CODE:

```sql
DECLARE
    n NUMBER :=&n;
    sum NUMBER := 0;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```


**Expected Output:**  
Sum of first 10 natural numbers is: 55


### OUTPUT:

<img width="940" height="152" alt="Screenshot 2026-08-25 102557" src="https://github.com/user-attachments/assets/dd5621cc-12a1-41fb-8af5-12eb2829dfb6" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

### CODE:

```sql
DECLARE
    n NUMBER := 10;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 1;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci Series:');

    WHILE i <= n LOOP
        DBMS_OUTPUT.PUT_LINE(a);

        c := a + b;
        a := b;
        b := c;

        i := i + 1;
    END LOOP;
END;
/
```


**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

### OUTPUT:

<img width="952" height="422" alt="Screenshot 2026-08-25 102709" src="https://github.com/user-attachments/assets/7dd7e26d-b362-4f25-b3e6-7c929323286a" />




---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.


### CODE:

```sql
SET SERVEROUTPUT ON;

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
/
```

**Expected Output:**  
n = 1535  
Reversed number is 5351

### OUTPUT:

<img width="978" height="280" alt="Screenshot 2026-08-25 102809" src="https://github.com/user-attachments/assets/7ed41bc9-2789-443a-bfbe-b0fef469812d" />


---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

### CODE:

```sql
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
BEGIN
    IF a > b AND a > c THEN
        DBMS_OUTPUT.PUT_LINE('Largest number is: ' || a);
    ELSIF b > a AND b > c THEN
        DBMS_OUTPUT.PUT_LINE('Largest number is: ' || b);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Largest number is: ' || c);
    END IF;
END;
/
```

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

### OUTPUT:

<img width="951" height="277" alt="Screenshot 2026-08-25 102956" src="https://github.com/user-attachments/assets/957917dc-4e30-4f1a-86dd-5e6f7354b4a7" />



## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

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

<img width="944" height="596" alt="image" src="https://github.com/user-attachments/assets/16535aec-5c17-4820-be78-1f228947e169" />


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

<img width="947" height="585" alt="image" src="https://github.com/user-attachments/assets/0c22a3d9-e56f-46d9-a10e-9c52de216c58" />

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

<img width="915" height="598" alt="image" src="https://github.com/user-attachments/assets/4c8ed11c-8684-45d7-a053-b3443c4cf530" />



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

<img width="914" height="668" alt="image" src="https://github.com/user-attachments/assets/7fe076ae-baf6-419d-8b8a-e910dcc0c2cf" />


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

<img width="937" height="594" alt="image" src="https://github.com/user-attachments/assets/a292a743-c269-43b3-9ead-d337be64e5f2" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

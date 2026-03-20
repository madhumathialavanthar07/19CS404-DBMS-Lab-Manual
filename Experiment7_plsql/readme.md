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

### Program
```
DECLARE
    num1 NUMBER := 80;  -- First number
    num2 NUMBER := 50;  -- Second number
BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
    END IF;
END;
```
### Output

<img width="398" height="278" alt="443112871-f710e18d-069e-4a86-a30a-ab599047da90" src="https://github.com/user-attachments/assets/dec6d66a-95b6-4c4b-a622-c9937356ff70" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55

### Program
```
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := 10;       -- Number up to which sum is calculated
    i NUMBER := 1;        -- Loop counter
    total_sum NUMBER := 0; -- To store the sum
BEGIN
    WHILE i <= n LOOP
        total_sum := total_sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || total_sum);
END;
```

### output
<img width="665" height="283" alt="443113960-5d3792b8-094e-4a7b-8b2b-6c937c6a94a1" src="https://github.com/user-attachments/assets/0e104133-42a7-4a28-8b2b-88ce8ce28981" />

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

### Program
```
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := 7;     -- Number of terms in the series
    a NUMBER := 0;     -- First term
    b NUMBER := 1;     -- Second term
    c NUMBER;          -- Next term
    i NUMBER := 3;     -- Counter starting from 3 since first two terms are already known
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');
    DBMS_OUTPUT.PUT_LINE(a);
    DBMS_OUTPUT.PUT_LINE(b);

    WHILE i <= n LOOP
        c := a + b;
        DBMS_OUTPUT.PUT_LINE(c);
        a := b;
        b := c;
         i := i + 1;
    END LOOP;
END;
```
### Output
<img width="468" height="251" alt="443118609-446d9757-6104-48d3-bdbb-78a931402e71" src="https://github.com/user-attachments/assets/cdf6c530-f9cb-4540-91c6-193a8103b6b7" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

### Program
```
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := 1535;       -- Original number
    original NUMBER := 1535;-- To keep the original number for display
    reversed NUMBER := 0;   -- To store the reversed number
    digit NUMBER;           -- To extract each digit
BEGIN
    WHILE n > 0 LOOP
        digit := MOD(n, 10);              -- Get the last digit
        reversed := reversed * 10 + digit;-- Build the reversed number
        n := TRUNC(n / 10);               -- Remove the last digit
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('n = ' || original);
    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reversed);
END;
```
### Output

<img width="776" height="280" alt="443119034-066ca7c4-1e5e-436b-9571-ba4338bb1271" src="https://github.com/user-attachments/assets/555a3882-9972-48f0-a37d-a9538cecb581" />


---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

### Program
```
SET SERVEROUTPUT ON;

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

    DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
    DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
```

### Output
<img width="565" height="284" alt="443119502-dbca8d99-6e52-423f-a997-ded9f9cdf18d" src="https://github.com/user-attachments/assets/402d1ad5-32a2-43b9-a0e1-5f05d4d8dded" />

## RESULT

Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.


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

### program:
 ```
DECLARE
   num1 NUMBER := 45;
   num2 NUMBER := 80;
BEGIN
   IF num1 > num2 THEN
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
   END IF;
END;
/
```
**Expected Output:**  
Greater number is: 80
### output
![WhatsApp Image 2025-05-12 at 14 12 01_00d3f1ce](https://github.com/user-attachments/assets/62af1655-a120-4b08-9b6d-9719e6d5cc9d)

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

### program:
```
DECLARE
   n   NUMBER := 10;
   i   NUMBER := 1;
   sum NUMBER := 0;
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

### output
![WhatsApp Image 2025-05-12 at 14 12 22_a275abf9](https://github.com/user-attachments/assets/120cf9a2-769f-45e9-a0df-7cd5ae6592ed)

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

### program:
```
DECLARE
   n   NUMBER := 7;    
   a   NUMBER := 0;      
   b   NUMBER := 1;     
   c   NUMBER;          
   i   NUMBER := 3;      
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
/
```
**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

### output
![WhatsApp Image 2025-05-12 at 14 15 22_ee629a00](https://github.com/user-attachments/assets/7fb33840-d8d1-470f-8b1f-631694cf8fde)

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

### program:
```
DECLARE
   n        NUMBER := 1535;  
   reversed NUMBER := 0;     
   digit    NUMBER;       
   temp     NUMBER;          
BEGIN
   temp := n;
   
   WHILE temp > 0 LOOP
      digit := MOD(temp, 10);           
      reversed := (reversed * 10) + digit; 
      temp := TRUNC(temp / 10);         
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reversed);
END;
/
```
**Expected Output:**  
n = 1535  
Reversed number is 5351

### output
![WhatsApp Image 2025-05-12 at 14 17 43_2a8b70bb](https://github.com/user-attachments/assets/98734a2e-04a7-4bce-8b7e-a256280966e2)

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

### program:
```
DECLARE
   a NUMBER := 10;
   b NUMBER := 9;
   c NUMBER := 15;
   largest NUMBER;
BEGIN
   IF (a >= b) AND (a >= c) THEN
      largest := a;
   ELSIF (b >= a) AND (b >= c) THEN
      largest := b;
   ELSE
      largest := c;
   END IF;

   DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
/
```
**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

### output

![WhatsApp Image 2025-05-12 at 14 19 18_d3f5abb2](https://github.com/user-attachments/assets/4c39d61f-ece5-4629-934b-c4f18ae434ef)

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

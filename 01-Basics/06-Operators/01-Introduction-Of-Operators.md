# 📘 Chapter 6: Operators in Java (Part 1)

> "Operators are special symbols that perform operations on variables and values."

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what operators are.
- Learn different types of operators in Java.
- Perform arithmetic operations.
- Understand unary operators.
- Learn increment and decrement operators.
- Understand operator precedence.
- Answer interview questions related to operators.

---

# 📚 Table of Contents

1. Why do we need Operators?
2. What are Operators?
3. Types of Operators
4. Arithmetic Operators
5. Unary Operators
6. Increment & Decrement Operators
7. Operator Precedence
8. JVM Working
9. Memory Diagram
10. Beginner Examples
11. Real-World Examples
12. Common Mistakes
13. Best Practices
14. Interview Questions
15. Quick Revision
16. Practice Problems
17. Related Topics
18. References

---

# 🤔 Why do we need Operators?

Imagine you're building an **Online Banking System**.

You need to perform operations like:

- Add money
- Subtract balance
- Calculate interest
- Compare account balances
- Check login conditions

Without operators, Java cannot perform calculations or make decisions.

Operators make programs dynamic by allowing them to process and manipulate data.

---

# 📖 What are Operators?

An **Operator** is a special symbol that performs an operation on one or more operands.

Example

```java
int sum = 10 + 20;
```

Here:

```
10  → Operand

20  → Operand

+   → Operator
```

Result:

```
30
```

---

# 📚 Types of Operators

Java provides several types of operators.

```text
                    Operators
                         │
 ┌──────────────┬──────────────┬──────────────┬──────────────┐
 │              │              │              │
Arithmetic   Unary      Relational     Logical
 │
 ├──────────────┬──────────────┬──────────────┐
 │              │              │
Bitwise    Assignment    Ternary
                    │
             Shift Operators
```

---

# 📖 Arithmetic Operators

Arithmetic operators perform mathematical calculations.

| Operator | Description | Example |
|----------|-------------|----------|
| + | Addition | 10 + 5 |
| - | Subtraction | 10 - 5 |
| * | Multiplication | 10 * 5 |
| / | Division | 10 / 5 |
| % | Modulus | 10 % 3 |

---

## Addition (+)

```java
int a = 10;
int b = 20;

System.out.println(a + b);
```

Output

```
30
```

---

## Subtraction (-)

```java
System.out.println(20 - 5);
```

Output

```
15
```

---

## Multiplication (*)

```java
System.out.println(5 * 6);
```

Output

```
30
```

---

## Division (/)

```java
System.out.println(20 / 4);
```

Output

```
5
```

### Integer Division

```java
System.out.println(5 / 2);
```

Output

```
2
```

Because both operands are integers, the decimal part is discarded.

To get a decimal result:

```java
System.out.println(5.0 / 2);
```

Output

```
2.5
```

---

## Modulus (%)

Returns the remainder after division.

```java
System.out.println(10 % 3);
```

Output

```
1
```

### Real-World Use

Checking whether a number is even or odd.

```java
if(number % 2 == 0)
```

---

# 📖 Unary Operators

Unary operators operate on a single operand.

| Operator | Description |
|----------|-------------|
| + | Unary Plus |
| - | Unary Minus |
| ++ | Increment |
| -- | Decrement |
| ! | Logical NOT |

---

## Unary Plus

```java
int a = +10;
```

No effect on the value.

---

## Unary Minus

```java
int a = -10;
```

Changes the sign of the number.

---

## Logical NOT

```java
boolean isLoggedIn = false;

System.out.println(!isLoggedIn);
```

Output

```
true
```

---

# 📖 Increment Operator (++)

Increases the value by **1**.

```java
int a = 10;

a++;

System.out.println(a);
```

Output

```
11
```

Equivalent to:

```java
a = a + 1;
```

---

# 📖 Decrement Operator (--)

Decreases the value by **1**.

```java
int a = 10;

a--;

System.out.println(a);
```

Output

```
9
```

Equivalent to:

```java
a = a - 1;
```

---

# 📖 Pre Increment

Syntax

```java
++a
```

The value is incremented **before** it is used.

Example

```java
int a = 10;

int b = ++a;

System.out.println(a);
System.out.println(b);
```

Output

```
11
11
```

---

# 📖 Post Increment

Syntax

```java
a++
```

The value is used first and then incremented.

Example

```java
int a = 10;

int b = a++;

System.out.println(a);
System.out.println(b);
```

Output

```
11
10
```

---

# 📖 Pre Decrement

```java
int a = 10;

int b = --a;
```

Output

```
9
9
```

---

# 📖 Post Decrement

```java
int a = 10;

int b = a--;
```

Output

```
9
10
```

---

# 🧠 JVM Internal Working

Example

```java
int a = 5;

int b = a++;
```

Execution Flow

```text
a = 5

↓

Assign b = 5

↓

Increment a

↓

a = 6
```

---

# 📦 Memory Diagram

```text
Stack Memory

a = 5

↓

Post Increment

↓

b = 5

↓

a = 6
```

---

# 🌍 Real-World Applications

Arithmetic Operators are used in:

- Banking Applications
- Shopping Cart Calculations
- Salary Management
- Scientific Calculations
- Billing Software
- Tax Calculations

Unary Operators are commonly used in:

- Loop Counters
- Login Systems
- Boolean Flags
- Counters and Iterators

---

➡️ **Next Part (Part 2):**

- Relational Operators
- Logical Operators
- Short Circuit Evaluation (`&&`, `||`)
- Assignment Operators
- Ternary Operator
- Operator Precedence & Associativity
- JVM Internal Working
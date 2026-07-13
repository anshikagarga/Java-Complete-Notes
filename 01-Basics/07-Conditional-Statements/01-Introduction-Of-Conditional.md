# 📘 Chapter 7: Conditional Statements in Java (Part 1)

> "Conditional statements allow a program to make decisions based on different conditions."

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand why Conditional Statements are needed.
- Learn different types of Conditional Statements.
- Understand `if`, `if-else`, and `else-if` statements.
- Understand Nested `if` statements.
- Learn JVM execution flow.
- Solve decision-making problems in Java.

---

# 📚 Table of Contents

1. Why do we need Conditional Statements?
2. What are Conditional Statements?
3. Types of Conditional Statements
4. if Statement
5. if-else Statement
6. else-if Ladder
7. Nested if
8. JVM Execution Flow
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

# 🤔 Why do we need Conditional Statements?

Imagine you're developing an **ATM Machine**.

The machine should allow withdrawal only if:

- The account has sufficient balance.
- The PIN is correct.
- The card is active.

Similarly,

An Online Shopping Application decides

- Whether to apply a discount.
- Whether free shipping is available.
- Whether the user is a premium member.

A Java program needs a mechanism to make decisions based on conditions.

This is where **Conditional Statements** come into the picture.

---

# 📖 What are Conditional Statements?

A **Conditional Statement** allows a program to execute a specific block of code only when a condition is satisfied.

The condition always evaluates to either:

```text
true

or

false
```

If the condition is `true`, the corresponding block executes.

Otherwise, Java skips it or executes another block.

---

# 📚 Types of Conditional Statements

Java provides the following Conditional Statements.

```text
             Conditional Statements
                     │
     ┌───────────────┼────────────────┐
     │               │                │
     if           if-else       else-if Ladder
                                      │
                                 Nested if
                                      │
                                   switch
```

---

# 📖 if Statement

The `if` statement executes a block of code only when the condition is **true**.

---

## Syntax

```java
if(condition){

    // code

}
```

---

## Flow Diagram

```text
        Condition
            │
      ┌─────┴─────┐
      │           │
    true       false
      │           │
 Execute      Skip Block
```

---

## Beginner Example

```java
public class Demo {

    public static void main(String[] args) {

        int age = 20;

        if(age >= 18){

            System.out.println("Eligible to Vote");

        }

    }

}
```

### Output

```
Eligible to Vote
```

---

# 🌍 Real-World Example

```java
double balance = 10000;

if(balance >= 5000){

    System.out.println("Withdrawal Allowed");

}
```

---

# 📖 if-else Statement

When one block should execute if the condition is **true** and another block should execute if the condition is **false**, use `if-else`.

---

## Syntax

```java
if(condition){

    // true block

}else{

    // false block

}
```

---

## Flow Diagram

```text
          Condition
              │
       ┌──────┴──────┐
       │             │
     true          false
       │             │
 Execute if     Execute else
```

---

## Example

```java
int marks = 25;

if(marks >= 33){

    System.out.println("Pass");

}else{

    System.out.println("Fail");

}
```

### Output

```
Fail
```

---

# 🌍 Real-World Example

```java
boolean loggedIn = true;

if(loggedIn){

    System.out.println("Welcome");

}else{

    System.out.println("Login First");

}
```

---

# 📖 else-if Ladder

Used when there are multiple conditions.

Java checks the conditions **from top to bottom**.

As soon as one condition becomes **true**, the remaining conditions are skipped.

---

## Syntax

```java
if(condition1){

}

else if(condition2){

}

else if(condition3){

}

else{

}
```

---

## Flow Diagram

```text
Condition 1
     │
True? ──► Execute

False
 │
 ▼

Condition 2
 │
True? ──► Execute

False
 │
 ▼

Condition 3

...

Else Block
```

---

## Example

```java
int marks = 78;

if(marks >= 90){

    System.out.println("Grade A");

}

else if(marks >= 75){

    System.out.println("Grade B");

}

else if(marks >= 60){

    System.out.println("Grade C");

}

else{

    System.out.println("Fail");

}
```

### Output

```
Grade B
```

---

# 📖 Nested if Statement

An `if` statement inside another `if` statement is called a **Nested if**.

---

## Syntax

```java
if(condition1){

    if(condition2){

        // code

    }

}
```

---

## Example

```java
int age = 22;

boolean hasLicense = true;

if(age >= 18){

    if(hasLicense){

        System.out.println("Can Drive");

    }

}
```

### Output

```
Can Drive
```

---

# 🧠 JVM Internal Working

Example

```java
int age = 16;

if(age >= 18){

    System.out.println("Eligible");

}
```

Execution

```text
Load Variable

↓

Evaluate Condition

↓

false

↓

Skip Block

↓

Program Continues
```

---

# 📦 Memory Diagram

```text
Stack Memory

age = 16

↓

Condition

age >= 18

↓

false

↓

Skip if Block
```

---

# 🌍 Real-World Applications

Conditional Statements are used in:

- ATM Machines
- Login Systems
- Online Shopping
- Banking Applications
- Hospital Management
- Student Portals
- Food Delivery Apps
- Ticket Booking Systems

---

➡️ **Next Part (Part 2):**

- `switch` Statement
- Enhanced `switch` (Java 14+)
- `yield` Keyword
- Switch vs if-else
- JVM Internal Working
- Common Mistakes
- Best Practices
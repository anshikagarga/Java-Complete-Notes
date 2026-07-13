# 📘 Chapter 7: Conditional Statements in Java (Part 3)

## Interview Preparation, Best Practices & Revision

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Compare all conditional statements.
- Understand when to use `if-else` and `switch`.
- Answer interview questions confidently.
- Revise the complete Conditional Statements chapter.
- Practice real interview coding questions.

---

# 📚 Table of Contents

1. JVM Decision Flow
2. Time & Space Complexity
3. Common Mistakes
4. Best Practices
5. Interview Questions
6. Quick Revision
7. Practice Problems
8. Related Topics
9. References
10. Chapter Summary

---

# 🧠 JVM Decision Flow

Consider the following program:

```java
int age = 20;

if(age >= 18){

    System.out.println("Eligible");

}else{

    System.out.println("Not Eligible");

}
```

### JVM Execution Flow

```text
Program Starts
      │
      ▼

Load Variable (age = 20)

      │
      ▼

Evaluate Condition

(age >= 18)

      │
 ┌────┴─────┐
 │          │
True      False
 │          │
 ▼          ▼

Execute    Execute
if Block   else Block

      │
      ▼

Continue Program

      │
      ▼

Program Ends
```

---

# 📦 Memory Diagram

```text
Stack Memory

-------------------------

age = 20

-------------------------

Condition

20 >= 18

↓

true

↓

Execute if Block
```

---

# ⚡ Time & Space Complexity

Conditional statements do not depend on the size of input.

| Statement | Time | Space |
|-----------|------|-------|
| if | O(1) | O(1) |
| if-else | O(1) | O(1) |
| else-if | O(n)* | O(1) |
| switch | O(1)** | O(1) |

### Notes

- **`else-if`** may evaluate multiple conditions until a match is found. In the worst case, if there are **n conditions**, the time complexity is **O(n)**.
- **`switch`** on constant values is often optimized by the JVM (for example, using jump tables or lookup tables), making lookup close to **O(1)** in many cases. This is an implementation optimization and should not always be assumed.

---

# 🌍 Real-World Applications

Conditional statements are used almost everywhere.

### 🏦 Banking System

```java
if(balance >= amount){

    withdraw();

}else{

    System.out.println("Insufficient Balance");

}
```

---

### 🛒 E-Commerce

```java
if(cartValue >= 999){

    freeShipping();

}
```

---

### 🎓 Student Management

```java
if(marks >= 33){

    System.out.println("Pass");

}else{

    System.out.println("Fail");

}
```

---

### 🚦 Traffic Signal

```java
switch(signal){

    case "RED" -> stop();

    case "GREEN" -> move();

    case "YELLOW" -> slowDown();

}
```

---

### 🔐 Login System

```java
if(username.equals("admin") && password.equals("1234")){

    login();

}
```

---

# ⚠️ Common Mistakes

## ❌ Forgetting Curly Braces

Wrong

```java
if(age >= 18)
    System.out.println("Eligible");
    System.out.println("Welcome");
```

Only the first statement belongs to the `if`.

Correct

```java
if(age >= 18){

    System.out.println("Eligible");

    System.out.println("Welcome");

}
```

---

## ❌ Using '=' instead of '=='

Wrong

```java
if(a = 10)
```

Correct

```java
if(a == 10)
```

---

## ❌ Incorrect Order in else-if

Wrong

```java
if(marks >= 33)

else if(marks >= 90)
```

The first condition catches all marks above 33, so the second condition is never reached.

Correct

```java
if(marks >= 90)

else if(marks >= 75)

else if(marks >= 33)
```

Always write more specific conditions first.

---

## ❌ Forgetting break in Traditional switch

```java
case 1:

System.out.println("One");
```

Without `break`, execution continues to the next case (fall-through).

---

## ❌ Using switch for Range Checks

Wrong

```java
switch(marks > 80)
```

Use `if-else` for ranges.

---

# 💡 Best Practices

- Keep conditions simple and readable.
- Use meaningful variable names.
- Prefer `switch` for fixed values.
- Prefer `if-else` for ranges or complex boolean expressions.
- Always include a `default` case in `switch`.
- Prefer Enhanced Switch (`->`) in Java 14+.
- Avoid deeply nested `if` statements; extract logic into methods if necessary.

---

# 📊 if-else vs switch

| Feature | if-else | switch |
|----------|----------|---------|
| Multiple Conditions | ✅ | ❌ |
| Range Checking | ✅ | ❌ |
| Constant Values | ✅ | ✅ |
| Readability | Medium | High |
| Fall-through | ❌ | ✅ (Traditional switch) |
| Enhanced Syntax | ❌ | ✅ (Java 14+) |

---

# 🧩 Interview Questions

## Beginner

1. What are Conditional Statements?
2. Why do we need Conditional Statements?
3. Difference between `if` and `if-else`.
4. What is an `else-if` ladder?
5. What is a Nested `if`?

---

## Intermediate

6. Difference between `if-else` and `switch`.
7. What is the purpose of `break`?
8. What is fall-through?
9. What is the `default` case?
10. Explain Enhanced Switch.

---

## Advanced

11. How does the JVM execute a `switch` statement?
12. What is the `yield` keyword?
13. Why is Enhanced Switch preferred?
14. How does the compiler optimize a `switch` statement?
15. When should you choose `if-else` over `switch`?

---

# 📝 Quick Revision

## Types of Conditional Statements

```text
if

↓

if-else

↓

else-if Ladder

↓

Nested if

↓

switch
```

---

## if

```java
if(condition){

}
```

---

## if-else

```java
if(condition){

}else{

}
```

---

## else-if

```java
if(){

}

else if(){

}

else{

}
```

---

## switch

```java
switch(value){

case 1:

break;

default:

}
```

---

## Enhanced Switch

```java
switch(value){

case 1 -> "One";

default -> "Invalid";

}
```

---

# 🧪 Practice Problems

## Beginner

1. Check whether a number is positive or negative.
2. Check whether a number is even or odd.
3. Find the largest of two numbers.
4. Print the day name using `switch`.

---

## Intermediate

5. Build a grade calculator using an `else-if` ladder.
6. Create a simple ATM menu using `switch`.
7. Build a calculator using `switch`.
8. Check leap year using `if-else`.

---

## Advanced

9. Create a login system using nested `if`.
10. Convert a traditional `switch` to an Enhanced Switch.
11. Create a menu-driven banking application.
12. Compare the performance of `switch` and `if-else` for multiple choices.

---

# 🏆 LeetCode Practice

### Easy

- 2235. Add Two Integers
- 2011. Final Value of Variable After Performing Operations
- 1523. Count Odd Numbers in an Interval Range

### Medium

- 7. Reverse Integer
- 9. Palindrome Number
- 50. Pow(x, n)

---

# 🔗 Related Topics

- Variables
- Data Types
- Operators
- Loops
- Methods
- Arrays
- Exception Handling

---

# 📚 References

- Oracle Java Documentation
- Java Language Specification (JLS)
- Effective Java — Joshua Bloch
- OpenJDK Documentation

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have successfully completed **Chapter 7: Conditional Statements in Java**.

### ✔️ Concepts Covered

- if Statement
- if-else Statement
- else-if Ladder
- Nested if
- switch Statement
- break
- default
- Fall-through
- Enhanced Switch (Java 14+)
- yield Keyword
- JVM Execution Flow
- Best Practices
- Interview Questions
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Use **if** when only one condition needs to be checked.
- ✅ Use **if-else** when there are two possible outcomes.
- ✅ Use an **else-if ladder** for multiple ordered conditions.
- ✅ Use **switch** when comparing a variable against fixed constant values.
- ✅ Always remember `break` in a traditional `switch`.
- ✅ Prefer **Enhanced Switch (`->`)** in modern Java.
- ✅ Write conditions from **most specific** to **least specific**.
- ✅ Keep conditional logic simple, readable, and maintainable.

➡️ **Next Chapter:** `08-Loops.md`
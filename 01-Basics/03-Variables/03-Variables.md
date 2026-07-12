# 📦 Variables in Java

> **Variables** are the fundamental building blocks of every Java program. They allow us to store, modify, and retrieve data during program execution.

> **Prerequisites:** Java Basics, JVM, JRE, JDK

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what variables are and why they are needed.
- Learn how variables are stored in JVM memory.
- Declare and initialize variables correctly.
- Follow Java variable naming conventions.
- Understand the life cycle of variables.
- Differentiate between declaration, initialization, and assignment.
- Prepare for Local, Instance, and Static Variables (covered in Part 2).

---

# 📚 Table of Contents

1. Why Do We Need Variables?
2. What is a Variable?
3. Variable Life Cycle
4. Variable Declaration
5. Variable Initialization
6. Variable Assignment
7. Memory Representation
8. Syntax
9. Beginner Examples
10. Common Mistakes
11. Best Practices
12. Quick Revision

---

# 🤔 Why Do We Need Variables?

Imagine you are developing an online banking application.

A customer deposits:

```
₹10,000
```

Where should the program store this value?

Without variables, every value would have to be hardcoded, making programs inflexible and impossible to update dynamically.

Variables solve this problem by acting as **named storage locations** that hold data while the program is running.

---

# 🌍 Real-World Analogy

Think of a variable as a **labeled storage box**.

```
+------------------+
|  Balance         |
|------------------|
| ₹10,000          |
+------------------+
```

- **Box Name** → Variable Name
- **Stored Item** → Variable Value
- **Box Type** → Data Type

---

# 📖 Definition

A **variable** is a named memory location used to store data that can change during the execution of a program.

---

## 📌 Interview Definition

> A variable is a named memory location that stores a value of a specific data type. The value can be modified during program execution unless the variable is declared as `final`.

---

# 🧠 How Variables Work (JVM Perspective)

When the JVM executes:

```java
int age = 21;
```

It performs the following steps:

1. Allocates memory for an integer.
2. Stores the value `21`.
3. Associates the memory location with the name `age`.
4. Allows the program to access the value using the variable name.

---

# 📦 Memory Representation (ASCII)

```text
Stack Memory

+----------------------+
| age = 21             |
| salary = 50000       |
| isStudent = true     |
+----------------------+
```

Primitive variables are generally stored in the **Stack Memory** (inside method scope).

Objects will be covered later.

---

# 📝 Variable Syntax

## Declaration

```java
dataType variableName;
```

Example

```java
int age;
```

---

## Initialization

```java
variableName = value;
```

Example

```java
age = 21;
```

---

## Declaration + Initialization

```java
int age = 21;
```

---

# 💻 Beginner Example

```java
public class VariablesExample {

    public static void main(String[] args) {

        int age = 21;

        System.out.println(age);

    }

}
```

### Output

```
21
```

---

# 💻 Multiple Variables

```java
public class Student {

    public static void main(String[] args) {

        String name = "Anshika";
        int age = 21;
        double cgpa = 8.75;
        boolean placed = false;

        System.out.println(name);
        System.out.println(age);
        System.out.println(cgpa);
        System.out.println(placed);

    }

}
```

### Output

```
Anshika
21
8.75
false
```

---

# 🔄 Declaration vs Initialization vs Assignment

These three terms are often confused in interviews.

## 1️⃣ Declaration

Creating the variable.

```java
int age;
```

Memory is reserved.

---

## 2️⃣ Initialization

Giving the variable its first value.

```java
age = 21;
```

---

## 3️⃣ Assignment

Updating the value.

```java
age = 22;
```

Now the previous value is replaced.

---

# 📦 Memory Flow

```text
Step 1

int age;

+---------+
| age=?   |
+---------+

↓

Step 2

age = 21;

+---------+
| age=21  |
+---------+

↓

Step 3

age = 25;

+---------+
| age=25  |
+---------+
```

---

# 🧠 Variable Life Cycle

Every variable goes through these stages:

```text
Declaration

↓

Initialization

↓

Usage

↓

Modification (Optional)

↓

Destroyed when its scope ends
```

Example:

```java
public static void main(String[] args) {

    int x = 10;

    System.out.println(x);

}
```

When the `main()` method finishes execution, the local variable `x` is removed from memory.

---

# 🌍 Real-World Example

Consider an e-commerce application.

```java
String productName = "Laptop";
double price = 74999.99;
int quantity = 2;
```

These variables store information needed to calculate the total bill, display product details, and process orders.

---

# 💡 Did You Know?

Java is a **statically typed language**.

This means every variable must have a data type before it can store a value.

```java
int age = 21;
```

The compiler already knows `age` will always store an integer.

---

# ⚠ Common Mistakes

## ❌ Using an Uninitialized Variable

```java
int age;

System.out.println(age);
```

Compilation Error:

```
Variable age might not have been initialized.
```

---

## ❌ Declaring the Same Variable Twice

```java
int age = 20;

int age = 25;
```

Compilation Error:

```
Duplicate local variable age
```

---

## ❌ Invalid Variable Names

Wrong

```java
int 1age = 20;
```

Correct

```java
int age1 = 20;
```

---

## ❌ Case Sensitivity

```java
int age = 20;

System.out.println(Age);
```

Compilation Error.

`age` and `Age` are different variables.

---

# 💡 Best Practices

- Use meaningful variable names.
- Initialize variables before use.
- Keep variable scope as small as possible.
- Follow Java naming conventions.
- Avoid single-letter names except in loops (`i`, `j`, `k`).

---

# 📝 Quick Revision

- ✅ Variables store data.
- ✅ Every variable has a data type.
- ✅ Variables must be declared before use.
- ✅ Variables can change during execution.
- ✅ Java is case-sensitive.
- ✅ Local variables must be initialized before use.

---

# 🔗 Related Topics

⬅ Previous: **02-JVM-JRE-JDK.md**

➡ Next: **04-Data-Types.md**

Understanding variables naturally leads to learning about the different types of data that variables can store.

---

## 🚀 Coming in Part 2

In the next part, we'll cover:

- 🔹 Types of Variables (Local, Instance, Static)
- 🔹 Variable Scope & Lifetime
- 🔹 Default Values
- 🔹 `final` Variables
- 🔹 Variable Naming Rules & Conventions
- 🔹 Shadowing
- 🔹 `var` (Local Variable Type Inference)
- 🔹 Mermaid Memory Diagrams
- 🔹 Interview Questions
- 🔹 Practice Problems
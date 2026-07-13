# 📘 Chapter 4: Data Types in Java (Part 1)

> "Data Types define what kind of data a variable can store and how much memory it occupies."

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what Data Types are.
- Learn why Data Types are important.
- Differentiate between Primitive and Non-Primitive Data Types.
- Understand how the JVM stores different types of data.
- Learn memory allocation for variables.
- Understand default values.
- Answer Data Type interview questions confidently.

---

# 📚 Table of Contents

1. Why do we need Data Types?
2. What are Data Types?
3. Types of Data Types
4. Primitive Data Types
5. Non-Primitive Data Types
6. JVM Memory Perspective
7. Memory Diagram
8. Syntax
9. Beginner Example
10. Real-World Example
11. Applications
12. Common Mistakes
13. Best Practices
14. Interview Questions
15. Quick Revision
16. Practice Problems
17. Related Topics
18. References

---

# 🤔 Why do we need Data Types?

Imagine you are developing an Online Banking Application.

The application stores different kinds of information.

- Customer Name
- Account Number
- Account Balance
- Is Account Active?
- Interest Rate

Every piece of information is different.

For example,

```
Name

↓

Anshika
```

contains text,

whereas

```
Balance

↓

₹50,000
```

contains numbers.

Java needs a way to identify what kind of data is being stored.

This is where **Data Types** come into the picture.

Without Data Types,

- JVM wouldn't know how much memory to allocate.
- Mathematical operations would become unreliable.
- Programs would become slower and more error-prone.

---

# 📖 What is a Data Type?

A **Data Type** specifies:

- What type of value can be stored.
- How much memory is required.
- What operations can be performed on that value.

Think of a Data Type as a **label** attached to every variable.

Example

```java
int age = 21;
```

Here,

- Variable → `age`
- Value → `21`
- Data Type → `int`

The JVM now knows:

- Allocate **4 bytes** of memory.
- Store only integer values.
- Allow arithmetic operations.

---

# 🌍 Real-World Analogy

Imagine you have different containers.

```
🥤 Bottle

Stores Water
```

```
📦 Box

Stores Books
```

```
💰 Wallet

Stores Money
```

Each container is designed for a specific purpose.

Similarly,

Data Types are containers for storing different kinds of data.

---

# 📚 Types of Data Types

Java has two categories of Data Types.

```
                Data Types
                     │
        ┌────────────┴────────────┐
        │                         │
 Primitive Data Types      Non-Primitive Data Types
```

---

# 1️⃣ Primitive Data Types

Primitive Data Types are predefined by Java.

They store **actual values**.

Java provides **8 Primitive Data Types**.

```
byte
short
int
long
float
double
char
boolean
```

Characteristics

- Fixed Size
- Faster
- Stored directly
- Not Objects

---

# 2️⃣ Non-Primitive Data Types

Non-Primitive Data Types store **references** to objects.

Examples

- String
- Array
- Class
- Interface
- Object
- Enum

Characteristics

- Variable Size
- Created by the programmer or Java library
- Stored as references
- Can contain methods and fields

---

# 🧠 JVM Perspective

Consider the following program.

```java
int age = 21;

String name = "Anshika";
```

Inside JVM,

```
Stack Memory

-----------------------

age

21

-----------------------

name

↓

Reference

-----------------------
```

```
Heap Memory

-----------------------

"Anshika"

-----------------------
```

Notice

Primitive Data Types store their values directly.

Non-Primitive Data Types store only a reference.

---

# 📦 Memory Diagram

```text
                JVM Memory

      +--------------------------+
      |        Stack             |
      |--------------------------|
      | age = 21                 |
      | name ------------------+ |
      +------------------------|--+
                               |
                               v
      +--------------------------+
      |         Heap             |
      |--------------------------|
      |      "Anshika"           |
      +--------------------------+
```

---

# 📝 Syntax

### Primitive

```java
int age = 20;

double salary = 55000.75;

char grade = 'A';

boolean isPlaced = true;
```

---

### Non-Primitive

```java
String name = "Anshika";

int[] marks = {90, 85, 95};
```

---

# 💻 Beginner Example

```java
public class DataTypeDemo {

    public static void main(String[] args) {

        int age = 21;

        double cgpa = 8.9;

        char grade = 'A';

        boolean placed = false;

        String name = "Anshika";

        System.out.println(name);
        System.out.println(age);
        System.out.println(cgpa);
        System.out.println(grade);
        System.out.println(placed);

    }

}
```

### Output

```
Anshika
21
8.9
A
false
```

---

# 🚀 Real-World Example

Imagine an Employee Management System.

```java
String employeeName = "Rahul";

int employeeId = 105;

double salary = 65000.50;

boolean isActive = true;
```

Each variable uses a different Data Type depending on the information it stores.

---

# 🌍 Real-World Applications

Data Types are used everywhere.

Examples include:

- Banking Applications
- Hospital Management Systems
- E-commerce Websites
- Student Management Systems
- Online Payment Applications
- Social Media Platforms
- Mobile Applications
- Game Development

---

➡️ **Part 2 will cover:**

- All 8 Primitive Data Types in detail
- Size & Range Table
- Default Values
- ASCII Memory Diagrams
- Numeric Literals
- Interview Notes
- JVM Internal Working
# 📘 Chapter 5: Type Casting in Java (Part 1)

> "Type Casting is the process of converting one data type into another."

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what Type Casting is.
- Learn why Type Casting is required.
- Differentiate between Implicit and Explicit Type Casting.
- Understand Widening and Narrowing Conversion.
- Learn how JVM performs automatic conversions.
- Understand data loss during conversions.
- Answer interview questions related to Type Casting.

---

# 📚 Table of Contents

1. Why do we need Type Casting?
2. What is Type Casting?
3. Types of Type Casting
4. Widening (Implicit Casting)
5. Narrowing (Explicit Casting)
6. JVM Internal Working
7. Memory Diagram
8. Syntax
9. Beginner Examples
10. Real-World Examples
11. Common Mistakes
12. Best Practices
13. Interview Questions
14. Quick Revision
15. Practice Problems
16. Related Topics
17. References

---

# 🤔 Why do we need Type Casting?

Imagine you are developing a Student Management System.

You calculate the average marks.

```java
int totalMarks = 450;
int subjects = 5;
```

Now,

```java
double average = totalMarks / subjects;
```

Without type casting,

Java performs integer division first.

Result

```
90
```

But if the result were

```
91.8
```

You would lose the decimal part.

Correct approach

```java
double average = (double) totalMarks / subjects;
```

Output

```
90.0
```

Type Casting helps Java convert one data type into another whenever required.

---

# 📖 What is Type Casting?

Type Casting is the process of converting a value from one data type to another.

For example,

```
int

↓

double
```

or

```
double

↓

int
```

Java performs this conversion either:

- Automatically
- Manually

---

# 📚 Types of Type Casting

```
                 Type Casting
                      │
        ┌─────────────┴─────────────┐
        │                           │
Implicit Casting             Explicit Casting
(Widening)                   (Narrowing)
```

---

# 📖 Implicit Type Casting (Widening)

## Definition

When Java automatically converts a smaller data type into a larger data type.

No data loss occurs.

No explicit cast is required.

---

## Conversion Order

```text
byte
  │
  ▼
short
  │
  ▼
int
  │
  ▼
long
  │
  ▼
float
  │
  ▼
double
```

---

# 📝 Syntax

```java
int number = 100;

double value = number;
```

No cast is required.

---

# 💻 Example

```java
public class Demo {

    public static void main(String[] args) {

        int number = 50;

        double value = number;

        System.out.println(value);

    }

}
```

### Output

```
50.0
```

---

# 🧠 JVM Internal Working

Initially

```text
Stack

number

50
```

During Assignment

```text
int

↓

double
```

The JVM automatically converts

```
50

↓

50.0
```

No information is lost.

---

# 📦 Memory Diagram

```text
Stack Memory

number

50

↓

Automatic Conversion

↓

value

50.0
```

---

# 🌍 Real-World Example

```java
int products = 250;

double totalProducts = products;
```

Used while generating reports and analytics where decimal values may be required.

---

# 📖 Explicit Type Casting (Narrowing)

## Definition

When a larger data type is converted into a smaller data type manually.

Java does **not** perform this conversion automatically because data loss may occur.

---

## Conversion Order

```text
double
  │
  ▼
float
  │
  ▼
long
  │
  ▼
int
  │
  ▼
short
  │
  ▼
byte
```

---

# 📝 Syntax

```java
double salary = 55000.75;

int amount = (int) salary;
```

Notice the cast operator

```java
(int)
```

---

# 💻 Example

```java
public class Demo {

    public static void main(String[] args) {

        double marks = 95.75;

        int roundedMarks = (int) marks;

        System.out.println(roundedMarks);

    }

}
```

### Output

```
95
```

The decimal part is removed.

---

# 🧠 Internal Working

Before

```text
marks

95.75
```

After Casting

```text
(int)

↓

95
```

Java truncates the decimal portion instead of rounding the value.

---

# 📦 Memory Diagram

```text
Stack

marks

95.75

↓

Explicit Cast

↓

roundedMarks

95
```

---

# ⚠️ Does Data Loss Occur?

Yes.

Example

```java
double value = 19.99;

int number = (int) value;
```

Output

```
19
```

The fractional part is lost.

---

# 🚀 Real-World Example

Suppose an e-commerce website calculates a discount.

```java
double discount = 149.99;

int displayDiscount = (int) discount;
```

Displayed Result

```
149
```

This is useful when only whole numbers are needed.

---

# 🌍 Applications of Type Casting

Type Casting is widely used in:

- Banking Applications
- Billing Software
- Scientific Calculations
- Graphics Programming
- Game Development
- Data Analytics
- Financial Systems
- Machine Learning

---

➡️ **Next Part (Part 2):**

- Data Loss
- Overflow
- Type Promotion
- Arithmetic Promotion Rules
- ASCII Memory Diagrams
- Interview Notes
- JVM Internals
# Strings in Java

> "Everything in Java is Object-Oriented, except primitive data types.
Strings are Objects."

---

# 🎯 Learning Objectives

After completing this chapter you will understand:

- What is String?
- Why String is immutable?
- String Constant Pool
- Heap Memory
- Stack Memory
- String using new keyword
- String Literal
- == vs equals()
- JVM Internal Working

---

# 📚 Table of Contents

1. Introduction
2. Why Strings?
3. What is String?
4. String Literal
5. String Object
6. JVM Memory
7. String Constant Pool
8. Immutability
9. Garbage Collection
10. == vs equals()
11. Examples
12. Best Practices
13. Interview Questions

---

# 🤔 Why do we need String?

Almost every application stores text.

Examples

- Username
- Password
- Email
- Address
- Product Name

Without String,
storing text would become extremely difficult.

---

# 📖 What is String?

A String is an object that stores a sequence of characters.

```java
String name = "Anshika";
```

Internally

```
A
n
s
h
i
k
a
```

---

# ☕ Creating Strings

There are two ways.

## Method 1

```java
String name = "Navin";
```

This is called

> String Literal

---

## Method 2

```java
String name = new String("Navin");
```

This creates a completely new object.

---

# 🧠 JVM Memory

When Java runs,

memory is divided into

```
+------------------------+
|        JVM             |
|                        |
|  Stack Memory          |
|  Heap Memory           |
+------------------------+
```

---

## Stack

Stores

- Local Variables
- References

Example

```java
String name = "Navin";
```

Stack

```
name
 │
 ▼
```

---

## Heap

Stores actual Objects.

```
Heap

+-----------+
| "Navin"   |
+-----------+
```

Reference

```
Stack

name
 │
 ▼

Heap

"Navin"
```

---

# String Literal

Example

```java
String s1 = "Navin";
String s2 = "Navin";
```

Question

How many objects?

Answer

Only ONE.

Because Java stores literals inside

```
String Constant Pool
```

Diagram

```
Stack

s1 ----\
         \
          -----> "Navin"

s2 ----/
```

Both point to the same object.

Memory Efficient.

---

# Using new Keyword

```java
String s1 = new String("Navin");
```

Now

Java creates

```
Heap

Object

"Navin"
```

Even if "Navin" already exists in SCP.

```
Stack

s1
 │
 ▼

Heap

Object
```

---

# Real Example

```java
String name = new String();
```

Output

```
""
```

Empty String.

Not null.

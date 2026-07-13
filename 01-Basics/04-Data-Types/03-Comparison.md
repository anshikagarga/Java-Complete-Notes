# 📘 Chapter 4: Data Types in Java (Part 3)

## Primitive vs Non-Primitive, Wrapper Classes, Interview Preparation & Revision

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Differentiate between Primitive and Non-Primitive Data Types.
- Understand Wrapper Classes.
- Learn AutoBoxing and Unboxing.
- Understand Numeric Overflow.
- Know Java Literal Types.
- Answer interview questions related to Data Types.
- Revise the complete chapter.

---

# 📚 Table of Contents

1. Primitive vs Non-Primitive
2. Wrapper Classes
3. AutoBoxing & Unboxing
4. Numeric Literals
5. Numeric Overflow
6. Real-World Applications
7. Common Mistakes
8. Best Practices
9. Interview Questions
10. Quick Revision
11. Practice Problems
12. Related Topics
13. References

---

# 🤔 Primitive vs Non-Primitive Data Types

Java categorizes data into two types.

```
                Data Types
                     │
      ┌──────────────┴──────────────┐
      │                             │
 Primitive                   Non-Primitive
```

---

## 📊 Comparison Table

| Feature | Primitive | Non-Primitive |
|----------|-----------|---------------|
| Stores | Actual Value | Reference to Object |
| Size | Fixed | Variable |
| Memory | Stack | Heap (Object), Reference in Stack |
| Default Value | Yes | null |
| Methods | ❌ No | ✅ Yes |
| Created By | Java Language | Programmer / Java Library |
| Performance | Faster | Slightly Slower |

---

# 🧠 JVM Memory Representation

```java
int age = 22;

String name = "Anshika";
```

Memory

```text
Stack Memory

age = 22

name --------┐
             │
             ▼

Heap Memory

"Anshika"
```

Notice

Primitive variables directly store values.

Objects store only references.

---

# 📖 Wrapper Classes

Every primitive data type has a corresponding Wrapper Class.

Wrapper Classes allow primitive values to behave like objects.

| Primitive | Wrapper Class |
|------------|---------------|
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean |

---

## Why Wrapper Classes?

Many Java APIs and Collection classes (like `ArrayList`, `HashMap`) work only with objects.

Primitive values need to be converted into objects.

Example

```java
ArrayList<Integer> marks = new ArrayList<>();
```

`ArrayList<int>` is not allowed.

---

# 📖 AutoBoxing

Automatic conversion of a primitive into its Wrapper Class.

```java
int number = 100;

Integer value = number;
```

Internally

```java
Integer value = Integer.valueOf(number);
```

---

# 📖 Unboxing

Automatic conversion of a Wrapper Object into a primitive.

```java
Integer value = 200;

int number = value;
```

Internally

```java
int number = value.intValue();
```

---

# 📦 Memory Diagram

```text
Stack

number = 100

↓

AutoBoxing

↓

Integer Object

Heap

100
```

---

# 📖 Numeric Literals

Java supports different types of numeric literals.

## Decimal

```java
int number = 100;
```

---

## Binary

```java
int number = 0b1010;
```

Output

```
10
```

---

## Octal

```java
int number = 012;
```

Output

```
10
```

---

## Hexadecimal

```java
int number = 0x1A;
```

Output

```
26
```

---

# 📖 Underscore Literals

Improves readability.

```java
int population = 1_400_000_000;
```

Same as

```java
1400000000
```

---

# 📖 Numeric Overflow

Every primitive has a fixed range.

When the value exceeds the range,

overflow occurs.

Example

```java
byte number = 127;

number++;
```

Output

```
-128
```

---

## Why?

```
Maximum

127

↓

+1

↓

Overflow

↓

-128
```

---

# 🌍 Real-World Applications

Primitive Data Types are used everywhere.

Examples

- Banking Software
- Hospital Management Systems
- Student Portals
- E-commerce Applications
- Mobile Apps
- IoT Devices
- Game Development

---

# ⚠️ Common Mistakes

### ❌ Using float without 'f'

```java
float pi = 3.14;
```

Correct

```java
float pi = 3.14f;
```

---

### ❌ Forgetting 'L'

```java
long population = 5000000000;
```

Correct

```java
long population = 5000000000L;
```

---

### ❌ Confusing char with String

```java
char c = "A";
```

Wrong

Correct

```java
char c = 'A';
```

---

### ❌ Assuming Objects are stored in Stack

Only the **reference** is stored in Stack.

The object itself is stored in Heap.

---

# 💡 Best Practices

- Use the smallest suitable data type.
- Prefer `int` for integers.
- Prefer `double` over `float` for precision.
- Use Wrapper Classes when working with Collections.
- Use meaningful variable names.
- Avoid unnecessary type conversions.

---

# 🧩 Interview Questions

## Basic

1. What is a Data Type?
2. How many primitive data types are there in Java?
3. Difference between `float` and `double`?
4. Difference between `char` and `String`?

---

## Intermediate

5. Difference between Primitive and Non-Primitive Data Types.
6. What are Wrapper Classes?
7. Explain AutoBoxing and Unboxing.
8. Where are primitive variables stored?

---

## Advanced

9. Explain JVM memory allocation for primitive variables.
10. What is Numeric Overflow?
11. Why do Collections use Wrapper Classes?
12. Explain Integer Caching (Hint: `Integer.valueOf()` caches values from **-128 to 127**).

---

# 📝 Quick Revision

## Primitive Data Types

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

---

## Wrapper Classes

```
byte      → Byte
short     → Short
int       → Integer
long      → Long
float     → Float
double    → Double
char      → Character
boolean   → Boolean
```

---

## Memory

```
Primitive

↓

Stack
```

```
Object

↓

Heap
```

---

## Keywords

- Primitive
- Reference
- Wrapper Class
- AutoBoxing
- Unboxing
- Overflow
- Literals

---

# 🧪 Practice Problems

### Beginner

1. Declare variables of all primitive data types.
2. Print their values.
3. Display the size of each data type using Wrapper Classes.

---

### Intermediate

4. Demonstrate AutoBoxing and Unboxing.
5. Write a program to show Numeric Overflow.
6. Convert decimal numbers to binary literals.

---

### Advanced

7. Explain JVM memory using ASCII diagrams.
8. Compare Wrapper Classes and Primitive Data Types.
9. Explain why Collections use Wrapper Classes.

---

# 🔗 Related Topics

- Variables
- Type Casting
- Operators
- Wrapper Classes
- Strings
- Arrays

---

# 📚 References

- Oracle Java Documentation
- Java Language Specification (JLS)
- Effective Java — Joshua Bloch
- OpenJDK Documentation

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have successfully completed **Chapter 4: Data Types in Java**.

### ✔️ What You Learned

- Primitive Data Types
- Non-Primitive Data Types
- JVM Memory Representation
- Size & Range
- Wrapper Classes
- AutoBoxing & Unboxing
- Numeric Literals
- Numeric Overflow
- Best Practices
- Interview Questions

➡️ **Next Chapter:** `05-Type-Casting.md`
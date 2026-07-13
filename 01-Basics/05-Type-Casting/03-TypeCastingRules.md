# 📘 Chapter 5: Type Casting in Java (Part 3)

## Type Conversion Rules, Interview Preparation & Revision

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Compare Widening and Narrowing conversions.
- Understand Java's complete type conversion hierarchy.
- Learn best practices for type casting.
- Answer interview questions confidently.
- Revise the complete Type Casting chapter.

---

# 📚 Table of Contents

1. Widening vs Narrowing
2. Complete Type Conversion Chart
3. JVM Execution Flow
4. Real-World Applications
5. Time & Space Complexity
6. Common Mistakes
7. Best Practices
8. Interview Questions
9. Quick Revision
10. Practice Problems
11. Related Topics
12. References

---

# 📊 Widening vs Narrowing

| Feature | Widening | Narrowing |
|----------|----------|------------|
| Conversion | Small → Large | Large → Small |
| Automatic | ✅ Yes | ❌ No |
| Cast Required | ❌ No | ✅ Yes |
| Data Loss | ❌ No | ✅ Possible |
| Safe | ✅ Yes | ⚠️ Depends |
| Performance | Fast | Fast |

---

## Example of Widening

```java
int number = 100;

double value = number;

System.out.println(value);
```

Output

```
100.0
```

Java performs the conversion automatically.

---

## Example of Narrowing

```java
double price = 99.99;

int amount = (int) price;

System.out.println(amount);
```

Output

```
99
```

The decimal part is removed.

---

# 📈 Complete Type Conversion Chart

```text
Automatic (Widening)

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

```text
Manual (Narrowing)

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

# 🧠 JVM Execution Flow

Example

```java
byte a = 20;
byte b = 30;

int sum = a + b;
```

JVM internally performs

```text
byte
↓

int

+

byte
↓

int

↓

Addition

↓

int Result
```

Therefore,

```java
byte result = a + b;
```

produces a compilation error.

Correct

```java
byte result = (byte)(a + b);
```

---

# 📦 JVM Memory Diagram

```text
Stack Memory

a = 20

b = 30

↓

Promoted

↓

20 (int)

30 (int)

↓

Addition

↓

50 (int)

↓

Stored in sum
```

---

# 🌍 Real-World Applications

Type Casting is used in almost every software application.

### Banking

```java
double balance = 10500.75;

int displayBalance = (int) balance;
```

---

### E-Commerce

```java
double discount = 199.99;

int roundedDiscount = (int) discount;
```

---

### Scientific Applications

```java
float temperature = 36.5f;

double preciseTemperature = temperature;
```

---

### Game Development

```java
double playerSpeed = 9.87;

int movement = (int) playerSpeed;
```

---

### Graphics Programming

```java
double x = 150.9;

int pixelX = (int) x;
```

---

# ⚡ Time & Space Complexity

Type Casting is a compiler/JVM operation.

| Operation | Time Complexity | Space Complexity |
|------------|-----------------|------------------|
| Widening | O(1) | O(1) |
| Narrowing | O(1) | O(1) |
| Type Promotion | O(1) | O(1) |

---

# ⚠️ Common Mistakes

## ❌ Forgetting Explicit Cast

```java
double d = 10.5;

int x = d;
```

Compilation Error

Correct

```java
int x = (int)d;
```

---

## ❌ Assuming Java Rounds Values

```java
double d = 8.99;

int x = (int)d;
```

Output

```
8
```

Java truncates the value.

---

## ❌ Ignoring Overflow

```java
byte value = 127;

value++;
```

Output

```
-128
```

---

## ❌ Forgetting Promotion Rules

```java
byte a = 10;

byte b = 20;

byte c = a + b;
```

Compiler Error

Reason

```
byte + byte

↓

int
```

---

# 💡 Best Practices

✅ Prefer Widening over Narrowing.

✅ Avoid unnecessary casting.

✅ Use `double` when precision is important.

✅ Always check for possible overflow.

✅ Use meaningful variable names.

✅ Understand promotion rules before writing arithmetic expressions.

---

# 💼 Interviewer's Notes

Interviewers frequently ask these concepts because they test your understanding of the Java language and JVM behavior.

Be prepared to explain:

- Why does `byte + byte` return `int`?
- Why does Java perform type promotion?
- Why is explicit casting required?
- Difference between widening and narrowing.
- Why is `double` the default type for decimal literals?
- Why must `float` literals end with `f`?
- Why must `long` literals sometimes end with `L`?

Explain the answer with both **code** and **JVM execution flow**.

---

# 🧩 Interview Questions

## Basic

1. What is Type Casting?
2. What is Widening Conversion?
3. What is Narrowing Conversion?
4. Difference between `float` and `double`.

---

## Intermediate

5. Why is explicit casting required?
6. What is Type Promotion?
7. Why does `byte + byte` return `int`?
8. What is Numeric Overflow?

---

## Advanced

9. Explain JVM execution during arithmetic operations.
10. Why are decimal literals treated as `double`?
11. What happens internally when casting `double` to `int`?
12. Explain overflow with binary representation.

---

# 📝 Quick Revision

### Widening

```
byte

↓

short

↓

int

↓

long

↓

float

↓

double
```

Automatic

No Data Loss

---

### Narrowing

```
double

↓

float

↓

long

↓

int

↓

short

↓

byte
```

Manual

Possible Data Loss

---

### Important Rules

✔ Small → Large = Automatic

✔ Large → Small = Manual

✔ `byte + byte = int`

✔ Decimal literals are `double` by default.

✔ Use `f` for float literals.

✔ Use `L` for long literals when needed.

---

# 🧪 Practice Problems

## Beginner

1. Convert `int` to `double`.
2. Convert `double` to `int`.
3. Convert `char` to `int`.
4. Print ASCII values of characters.

---

## Intermediate

5. Demonstrate Numeric Overflow.
6. Explain Type Promotion using code.
7. Compare Widening and Narrowing.

---

## Advanced

8. Draw JVM memory diagrams for casting.
9. Explain `byte + byte` internally.
10. Build a calculator demonstrating automatic type promotion.

---

# 🔗 Related Topics

- Variables
- Data Types
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

You have completed **Chapter 5: Type Casting in Java**.

### ✔️ In this chapter, you learned:

- Primitive Type Conversion
- Widening Conversion
- Narrowing Conversion
- Data Loss
- Numeric Overflow
- Type Promotion
- JVM Execution Flow
- Memory Representation
- Best Practices
- Interview Questions

➡️ **Next Chapter:** `06-Operators.md`
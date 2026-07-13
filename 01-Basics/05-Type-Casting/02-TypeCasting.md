# 📘 Chapter 5: Type Casting in Java (Part 2)

## Data Loss, Overflow & Type Promotion

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Understand data loss during type casting.
- Learn numeric overflow.
- Understand arithmetic type promotion.
- Learn Java's automatic conversion rules.
- Understand how JVM evaluates expressions.
- Avoid common mistakes related to type casting.

---

# 📚 Table of Contents

1. Data Loss
2. Numeric Overflow
3. Type Promotion
4. Arithmetic Promotion Rules
5. JVM Internal Working
6. Memory Diagrams
7. Real-World Examples
8. Common Mistakes
9. Best Practices

---

# 📖 Data Loss

## What is Data Loss?

Data Loss occurs when a value is converted into a smaller data type that cannot store all of its information.

Example

```java
double salary = 55000.75;

int value = (int) salary;

System.out.println(value);
```

### Output

```
55000
```

Notice

```
55000.75

↓

55000
```

The decimal part is permanently removed.

---

# 📦 Memory Diagram

Before Casting

```text
Stack

salary

55000.75
```

After Casting

```text
Stack

value

55000
```

The fractional value is lost.

---

# 📖 Numeric Overflow

Every primitive data type has a fixed range.

If a value exceeds its maximum limit,

Java wraps around to the minimum value.

---

## Example

```java
byte number = 127;

number++;

System.out.println(number);
```

### Output

```
-128
```

---

# 🧠 Why Does Overflow Occur?

A `byte` uses only **8 bits**.

Maximum value

```
127
```

Binary Representation

```text
01111111
```

Adding one more

```text
10000000
```

Java interprets it as

```
-128
```

---

# Another Example

```java
byte value = 126;

value++;

System.out.println(value);

value++;

System.out.println(value);
```

### Output

```
127
-128
```

---

# 📖 Type Promotion

Type Promotion is the automatic conversion of smaller data types into larger data types during arithmetic operations.

Java promotes operands before performing calculations.

---

## Why?

The CPU performs calculations efficiently using `int` or larger data types.

---

# Example 1

```java
byte a = 10;
byte b = 20;

int result = a + b;

System.out.println(result);
```

### Output

```
30
```

Notice

Although both variables are `byte`,

the result is an `int`.

---

# JVM Internal Working

```text
byte

↓

int

↓

Addition

↓

int Result
```

---

# Example 2

```java
char a = 'A';
char b = 2;

int result = a + b;

System.out.println(result);
```

### Output

```
67
```

Because

```
'A'

↓

Unicode

65

↓

65 + 2

↓

67
```

---

# Example 3

```java
int number = 10;

double value = 5.5;

double result = number + value;

System.out.println(result);
```

Output

```
15.5
```

The `int` is promoted to `double`.

---

# 📊 Arithmetic Promotion Rules

When two different primitive types are used,

Java converts the smaller type into the larger type.

```text
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

The final result will always be the larger data type.

---

## Examples

```java
int + double

↓

double
```

---

```java
long + float

↓

float
```

---

```java
float + double

↓

double
```

---

# 📦 JVM Memory Representation

Example

```java
int number = 50;

double price = 19.5;

double total = number + price;
```

Memory

```text
Stack

number = 50

↓

Promoted

↓

50.0

+

19.5

↓

69.5
```

---

# 🌍 Real-World Example

Suppose you're calculating the average salary.

```java
int employees = 4;

double salary = 25000.75;

double average = salary / employees;
```

The JVM promotes the integer value before performing division.

Result

```
6250.1875
```

---

# 📖 Explicit Casting after Promotion

Sometimes Java requires explicit casting even after promotion.

Example

```java
byte a = 10;
byte b = 20;

byte result = (byte)(a + b);
```

Without casting

```java
byte result = a + b;
```

Compiler Error

```
Possible lossy conversion from int to byte
```

Because

```
byte

↓

int

↓

Addition

↓

int Result
```

---

# ⚠️ Common Mistakes

## ❌ Forgetting Explicit Casting

```java
double value = 9.8;

int number = value;
```

Compilation Error

Correct

```java
int number = (int)value;
```

---

## ❌ Assuming Java Rounds Values

```java
(double)

↓

(int)
```

does NOT round.

Example

```java
9.99

↓

9
```

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

## ❌ Storing Arithmetic Result into byte

Wrong

```java
byte a = 10;

byte b = 20;

byte c = a + b;
```

Correct

```java
byte c = (byte)(a + b);
```

---

# 💡 Best Practices

- Use implicit casting whenever possible.
- Use explicit casting only when necessary.
- Avoid unnecessary narrowing conversions.
- Be careful while converting decimal values to integers.
- Always check for overflow when using smaller data types.
- Understand arithmetic promotion rules before writing calculations.

---

# 🚀 Interviewer's Notes

Interviewers frequently ask:

- Why does `byte + byte` return `int`?
- Why is explicit casting required?
- What is numeric overflow?
- Difference between widening and narrowing?
- Does Java round values while casting?
- What is type promotion?

👉 Always explain the JVM's promotion rules with a simple code example.
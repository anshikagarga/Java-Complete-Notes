# 📘 Chapter 4: Data Types in Java (Part 2)

## Primitive Data Types, Size, Range & Default Values

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Learn all 8 Primitive Data Types.
- Understand their memory size.
- Know their value ranges.
- Understand default values.
- Choose the appropriate data type.
- Explain primitive data types in interviews.

---

# 📚 Table of Contents

1. Primitive Data Types
2. Numeric Data Types
3. Character Data Type
4. Boolean Data Type
5. Size & Range Table
6. Default Values
7. Memory Representation
8. Real-World Examples
9. Common Mistakes
10. Best Practices

---

# 📖 Primitive Data Types

Java provides **8 Primitive Data Types**.

```
Primitive Data Types

│

├── byte
├── short
├── int
├── long
├── float
├── double
├── char
└── boolean
```

Primitive data types store **actual values**, not references.

---

# 1️⃣ byte

## Definition

`byte` is the smallest integer data type in Java.

It occupies **1 byte (8 bits)** of memory.

### Syntax

```java
byte age = 25;
```

### Memory Representation

```
byte

8 Bits

┌──┬──┬──┬──┬──┬──┬──┬──┐
│0 │0 │0 │1 │1 │0 │0 │1 │
└──┴──┴──┴──┴──┴──┴──┴──┘
```

### Range

```
-128 to 127
```

### Real-World Use

- Image Processing
- Network Communication
- File Handling

---

# 2️⃣ short

## Definition

`short` stores integer values larger than `byte`.

Memory

```
2 Bytes

16 Bits
```

### Syntax

```java
short marks = 250;
```

### Range

```
-32,768

to

32,767
```

### Example

```java
short temperature = 250;
```

---

# 3️⃣ int

## Definition

The most commonly used integer data type.

Memory

```
4 Bytes

32 Bits
```

### Syntax

```java
int salary = 45000;
```

### Range

```
-2^31

to

2^31 - 1
```

Approximately

```
-2.1 Billion

to

2.1 Billion
```

### Real-World Applications

- Age
- Salary
- Student Marks
- Employee ID

---

# 4️⃣ long

## Definition

Used for storing very large integer values.

Memory

```
8 Bytes

64 Bits
```

### Syntax

```java
long population = 1400000000L;
```

Notice the suffix

```
L
```

It tells the compiler that the value is of type `long`.

### Range

```
-2^63

to

2^63-1
```

### Real-World Applications

- Population
- Bank Transactions
- Scientific Calculations
- Distance Between Planets

---

# 5️⃣ float

## Definition

Stores decimal numbers with single precision.

Memory

```
4 Bytes
```

### Syntax

```java
float percentage = 95.5f;
```

Notice

```
f
```

must be written.

Otherwise Java treats decimal numbers as `double`.

---

### Example

```java
float pi = 3.14f;
```

---

# 6️⃣ double

## Definition

Stores decimal numbers with double precision.

Memory

```
8 Bytes
```

### Syntax

```java
double cgpa = 8.94;
```

Unlike float,

no suffix is required.

### Example

```java
double salary = 65000.75;
```

---

# Difference between float and double

| Feature | float | double |
|----------|--------|---------|
| Size | 4 Bytes | 8 Bytes |
| Precision | Less | More |
| Suffix | f | Not Required |

---

# 7️⃣ char

## Definition

Stores a **single Unicode character**.

Memory

```
2 Bytes

16 Bits
```

### Syntax

```java
char grade = 'A';
```

Notice

Characters are enclosed in

```
''
```

not

```
""
```

### Example

```java
char symbol = '@';
```

---

# Unicode Example

```java
char letter = 65;

System.out.println(letter);
```

Output

```
A
```

Because

```
Unicode

65

↓

A
```

---

# 8️⃣ boolean

## Definition

Stores logical values.

Possible values

```
true

false
```

### Syntax

```java
boolean isPlaced = true;
```

### Example

```java
boolean isLoggedIn = false;
```

### Real-World Applications

- Login Systems
- Authentication
- Conditions
- Flags

---

# 📊 Size & Range Table

| Data Type | Size | Range |
|------------|------|-----------------------------|
| byte | 1 Byte | -128 to 127 |
| short | 2 Bytes | -32,768 to 32,767 |
| int | 4 Bytes | -2³¹ to 2³¹−1 |
| long | 8 Bytes | -2⁶³ to 2⁶³−1 |
| float | 4 Bytes | ~6-7 decimal digits |
| double | 8 Bytes | ~15-16 decimal digits |
| char | 2 Bytes | 0 to 65,535 |
| boolean | JVM Dependent | true / false |

---

# 📋 Default Values

Default values are assigned when variables are declared as **instance variables** (class members).

| Data Type | Default Value |
|------------|---------------|
| byte | 0 |
| short | 0 |
| int | 0 |
| long | 0L |
| float | 0.0f |
| double | 0.0 |
| char | '\u0000' |
| boolean | false |

> **Note:** Local variables do **not** receive default values. They must be initialized before use.

---

# 📦 JVM Memory Representation

```text
Stack Memory

age = 21

cgpa = 8.5

grade = 'A'

placed = true
```

Each primitive variable stores its **actual value** directly in Stack Memory.

Unlike Objects,

no Heap allocation is required.

---

# 🌍 Real-World Example

```java
public class Student {

    int rollNo = 101;

    double cgpa = 8.85;

    char section = 'A';

    boolean placed = true;

}
```

Different information requires different primitive data types.

---

# ⚠️ Common Mistakes

### ❌ Forgetting the 'L'

```java
long population = 1400000000;
```

Prefer

```java
long population = 1400000000L;
```

---

### ❌ Forgetting the 'f'

```java
float pi = 3.14;
```

Correct

```java
float pi = 3.14f;
```

---

### ❌ Using double when int is enough

```java
double age = 21;
```

Better

```java
int age = 21;
```

Choose the most appropriate data type.

---

# 💡 Best Practices

- Use `int` for most integer values.
- Use `long` for very large numbers.
- Prefer `double` over `float` unless memory optimization is required.
- Use `boolean` for conditions and flags.
- Choose the smallest suitable data type without sacrificing readability.
- Always use descriptive variable names.

---

➡️ **Next Part (Part 3):**

- Primitive vs Non-Primitive Comparison
- Wrapper Classes (Introduction)
- Type Literals
- Numeric Overflow
- Memory Optimization
- Interview Questions (Basic → Advanced)
- Quick Revision Sheet
- Practice Problems
- References
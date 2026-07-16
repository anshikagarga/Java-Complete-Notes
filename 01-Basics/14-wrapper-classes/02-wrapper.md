# 📘 Chapter 14: Wrapper Classes (Part 2)

## Wrapper Class Caching, Equality, Performance & Internal Working

> *"Understanding Wrapper Classes is not just about converting primitives into objects. Interviews often focus on Integer Caching, Autoboxing, Unboxing, `==` vs `.equals()`, and performance implications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Integer Caching.
- Learn Wrapper Object Comparison.
- Understand `==` vs `.equals()`.
- Learn NullPointerException caused by Unboxing.
- Analyze Wrapper Class Performance.
- Learn Common Mistakes.
- Follow Best Practices.

---

# 📚 Table of Contents

1. Integer Caching
2. Wrapper Object Comparison
3. == vs equals()
4. NullPointerException
5. Performance Considerations
6. Internal Working
7. Common Mistakes
8. Best Practices

---

# 📖 Integer Caching

Java does not always create a new `Integer` object.

Instead,

Java maintains an **Integer Cache**.

Cache Range

```text
-128

↓

127
```

Whenever an Integer object is created within this range,

Java reuses the same object.

---

# 💻 Example

```java
Integer a = 100;
Integer b = 100;

System.out.println(a == b);
```

Output

```text
true
```

Reason

Both variables refer to the same cached object.

---

# 📦 Memory Diagram

```text
Integer Cache

↓

100

↑      ↑

a      b
```

Only one object exists.

---

# 💻 Example Outside Cache

```java
Integer a = 200;
Integer b = 200;

System.out.println(a == b);
```

Output

```text
false
```

Reason

200 is outside the cache range.

Java creates two different objects.

---

# 📦 Memory Diagram

```text
a

↓

200

----------------

b

↓

200
```

Different objects.

---

# 📖 Why Integer Cache?

Creating objects repeatedly is expensive.

Java reuses frequently used Integer objects to

- Improve Performance
- Reduce Memory Usage
- Reduce Garbage Collection

---

# 📖 Comparing Wrapper Objects

There are two ways to compare objects.

## Using ==

Compares

```text
Memory Address (Reference)
```

---

## Using equals()

Compares

```text
Actual Value
```

---

# 💻 Example

```java
Integer a = 100;
Integer b = 100;

System.out.println(a == b);

System.out.println(a.equals(b));
```

Output

```text
true

true
```

---

# 💻 Example

```java
Integer a = 200;
Integer b = 200;

System.out.println(a == b);

System.out.println(a.equals(b));
```

Output

```text
false

true
```

Explanation

- `==` compares object references.
- `.equals()` compares object values.

---

# 📊 == vs equals()

| Operator | Compares |
|----------|----------|
| == | Object Reference |
| equals() | Object Value |

Example

```java
Integer x = 500;
Integer y = 500;

System.out.println(x == y);        // false
System.out.println(x.equals(y));   // true
```

---

# 📖 Unboxing and NullPointerException

One of the most common interview questions.

Example

```java
Integer num = null;

int value = num;
```

Output

```text
NullPointerException
```

---

# 📖 Why?

Java performs

```java
num.intValue();
```

Internally.

Since

```java
num == null
```

Calling

```java
intValue()
```

throws

```text
NullPointerException
```

---

# 📦 Internal Working

```text
Integer num = null

↓

num.intValue()

↓

NullPointerException
```

---

# 💻 Safe Approach

```java
Integer num = null;

if(num != null){

    int value = num;

}
```

Always check for `null` before unboxing.

---

# 📖 Autoboxing Internally

When you write

```java
Integer x = 50;
```

Java internally converts it to

```java
Integer x = Integer.valueOf(50);
```

---

# 📖 Unboxing Internally

When you write

```java
int x = obj;
```

Java internally converts it to

```java
int x = obj.intValue();
```

---

# 📊 Complete Flow

```text
Primitive

↓

Autoboxing

↓

Wrapper Object

↓

Integer Cache

↓

Object

↓

Unboxing

↓

Primitive
```

---

# ⚡ Performance Considerations

Primitive

```java
int a = 100;
```

Fast

↓

No object creation.

---

Wrapper

```java
Integer a = 100;
```

Slower

↓

Object creation (or cache lookup).

---

### Frequent Autoboxing

```java
for(int i=0;i<1000000;i++){

    Integer x = i;

}
```

Creates many wrapper objects (or cache lookups).

Avoid unnecessary boxing in performance-critical code.

---

# 📊 Primitive vs Wrapper

| Feature | Primitive | Wrapper |
|----------|-----------|----------|
| Object | ❌ | ✅ |
| Null Allowed | ❌ | ✅ |
| Collections | ❌ | ✅ |
| Generics | ❌ | ✅ |
| Memory Usage | Less | More |
| Speed | Faster | Slightly Slower |

---

# ⚠️ Common Mistakes

## ❌ Using == for Wrapper Objects

Wrong

```java
Integer a = 500;
Integer b = 500;

System.out.println(a == b);
```

Correct

```java
System.out.println(a.equals(b));
```

---

## ❌ Forgetting Integer Cache

Many beginners think

```java
Integer a = 100;

Integer b = 100;

a == b
```

always compares values.

Actually,

it returns true only because of Integer Cache.

---

## ❌ Unboxing Null

Wrong

```java
Integer x = null;

int y = x;
```

Correct

```java
if(x != null){

    int y = x;

}
```

---

## ❌ Using Deprecated Constructor

Wrong

```java
Integer obj = new Integer(10);
```

Correct

```java
Integer obj = Integer.valueOf(10);
```

or

```java
Integer obj = 10;
```

---

# 💡 Best Practices

- Prefer primitives for calculations.
- Use wrapper classes only when objects are required.
- Use `.equals()` to compare wrapper objects.
- Prefer `Integer.valueOf()` over constructors.
- Avoid unnecessary boxing and unboxing.
- Check for `null` before unboxing.
- Understand Integer Cache for interviews.

---

# 🌍 Real-World Applications

Wrapper Classes are heavily used in:

- Collections Framework
- HashMap
- HashSet
- Stream API
- Hibernate
- Spring Boot
- JDBC
- JSON Parsing
- REST APIs
- Java Generics

---

# 🎯 Interview Tip

### Question

Why does this code print `true`?

```java
Integer a = 100;
Integer b = 100;

System.out.println(a == b);
```

### Answer

Java caches `Integer` objects in the range **-128 to 127**. Since `100` falls within this range, both variables reference the same cached object, so `==` returns `true`. For values outside this range (such as `200`), separate objects are created, and `==` returns `false`.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Wrapper Classes Interview Questions
- MCQs
- Practice Problems
- Wrapper Classes vs Primitive Types
- Quick Revision
- Chapter Summary
- Frequently Asked Interview Questions
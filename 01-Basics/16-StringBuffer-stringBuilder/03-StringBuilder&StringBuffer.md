# 📘 Chapter 17: StringBuffer & StringBuilder (Part 3)

## StringBuilder, Thread Safety & Performance

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what StringBuilder is.
- Differentiate between StringBuffer and StringBuilder.
- Understand Thread Safety.
- Learn when to use String, StringBuffer and StringBuilder.
- Answer String-related interview questions confidently.

---

# 📚 Table of Contents

1. Introduction to StringBuilder
2. Why do we need StringBuilder?
3. Internal Working
4. Thread Safety
5. String vs StringBuffer vs StringBuilder
6. Performance Comparison
7. Real-World Applications
8. Common Mistakes
9. Best Practices
10. Interview Questions
11. Quick Revision
12. Practice Problems
13. Related Topics
14. References

---

# 🤔 Why do we need StringBuilder?

`StringBuffer` solves the immutability problem of `String`, but every method in `StringBuffer` is synchronized.

Synchronization provides thread safety but also introduces additional overhead.

When thread safety is **not required**, Java provides a faster alternative:

> **StringBuilder**

Introduced in **Java 5**.

---

# 📖 What is StringBuilder?

`StringBuilder` is a mutable sequence of characters, just like `StringBuffer`, but it is **not thread-safe**.

Because it does not use synchronization, it performs faster in single-threaded applications.

---

# 📝 Syntax

```java
StringBuilder sb = new StringBuilder();
```

With an initial value:

```java
StringBuilder sb = new StringBuilder("Java");
```

---

# 💻 Beginner Example

```java
public class Demo {

    public static void main(String[] args) {

        StringBuilder sb = new StringBuilder("Java");

        sb.append(" Programming");

        System.out.println(sb);

    }

}
```

### Output

```
Java Programming
```

---

# 🧠 Internal Working

```text
Stack

sb
 │
 ▼

Heap

+-------------------------+
| Java Programming        |
+-------------------------+
```

The same object is modified.

No new String object is created.

---

# 📦 Memory Comparison

### String

```text
Java

↓

Java Programming

(New Object Created)
```

---

### StringBuffer

```text
Java

↓

Java Programming

(Same Object Modified)
```

---

### StringBuilder

```text
Java

↓

Java Programming

(Same Object Modified)
```

---

# 🧠 Thread Safety

## What is Thread Safety?

A thread-safe object can be accessed safely by multiple threads simultaneously without producing incorrect results.

---

### String

- Immutable
- Thread Safe

---

### StringBuffer

- Mutable
- Thread Safe
- Uses Synchronization

---

### StringBuilder

- Mutable
- Not Thread Safe
- No Synchronization

---

# 📊 Performance Comparison

| Class | Mutable | Thread Safe | Performance |
|--------|----------|-------------|-------------|
| String | ❌ | ✅ | Slow |
| StringBuffer | ✅ | ✅ | Medium |
| StringBuilder | ✅ | ❌ | Fast |

---

# 🧠 Why is StringBuilder Faster?

Since there is **no synchronization**, the JVM does not need to lock methods before execution.

This reduces overhead and improves performance.

```text
StringBuffer

↓

Synchronization

↓

More Overhead

↓

Slower
```

```text
StringBuilder

↓

No Synchronization

↓

Less Overhead

↓

Faster
```

---

# 🌍 Real-World Applications

### Use String

- Passwords
- URLs
- File Names
- Configuration Values
- Constants

---

### Use StringBuffer

- Logging in Multi-threaded Applications
- Banking Systems
- Concurrent Programs

---

### Use StringBuilder

- Building SQL Queries
- Generating HTML
- Creating JSON/XML
- String Manipulation in Loops
- Competitive Programming

---

# 🚀 Which One Should You Use?

```text
Need immutable text?

        │

        ▼

     String
```

---

```text
Need mutable string
in multiple threads?

        │

        ▼

   StringBuffer
```

---

```text
Need maximum speed
in single thread?

        │

        ▼

   StringBuilder
```

---

# ⚡ Time Complexity

| Operation | Complexity |
|-----------|------------|
| append() | O(1) (Amortized) |
| insert() | O(n) |
| delete() | O(n) |
| replace() | O(n) |
| reverse() | O(n) |
| toString() | O(n) |

---

# ⚠️ Common Mistakes

### ❌ Using String inside loops

```java
String s = "";

for(int i = 0; i < 1000; i++){

    s += i;

}
```

Creates hundreds of unnecessary objects.

---

### ✅ Better Approach

```java
StringBuilder sb = new StringBuilder();

for(int i = 0; i < 1000; i++){

    sb.append(i);

}
```

---

### ❌ Using StringBuffer in a Single Thread

It works correctly, but synchronization adds unnecessary overhead.

Prefer `StringBuilder`.

---

### ❌ Assuming StringBuilder is Thread Safe

It is **not** safe when accessed by multiple threads simultaneously.

---

# 💡 Best Practices

- Use `String` for immutable text.
- Use `StringBuilder` in single-threaded applications.
- Use `StringBuffer` only when thread safety is required.
- Avoid String concatenation inside loops.
- Initialize capacity when the expected size is known.

---

# 🧩 Interview Questions

## Basic

1. What is StringBuilder?
2. Why was StringBuilder introduced?
3. Is StringBuilder mutable?
4. Is StringBuilder thread-safe?

---

## Intermediate

5. Difference between StringBuffer and StringBuilder.
6. Why is StringBuilder faster?
7. Explain synchronization in StringBuffer.
8. Difference between capacity() and length().

---

## Advanced

9. Explain internal working of StringBuilder.
10. When should you use StringBuffer instead of StringBuilder?
11. Why is String immutable?
12. Explain memory allocation for StringBuilder.

---

# 📝 Quick Revision

✅ String → Immutable

✅ StringBuffer → Mutable + Thread Safe

✅ StringBuilder → Mutable + Fast

✅ StringBuilder introduced in Java 5

✅ StringBuffer uses synchronization

✅ StringBuilder does not use synchronization

✅ StringBuilder is preferred in single-threaded applications

---

# 🧪 Practice Problems

### Beginner

1. Append two strings using StringBuilder.
2. Reverse a string using `reverse()`.
3. Insert a word at a specific index.
4. Delete a character using `deleteCharAt()`.

---

### Intermediate

5. Compare execution time of String and StringBuilder.
6. Build a sentence using `append()`.
7. Create a custom text editor using StringBuilder.

---

### Advanced

8. Explain memory allocation using diagrams.
9. Compare all three classes with examples.
10. Explain why StringBuilder is faster than StringBuffer.

---

# 🔗 Related Topics

- Strings
- String Constant Pool
- Wrapper Classes
- Arrays
- Collections Framework

---

# 📚 References

- Oracle Java Documentation
- Java Language Specification (JLS)
- Effective Java — Joshua Bloch
- OpenJDK Documentation

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed the **StringBuffer & StringBuilder** chapter.

You now understand:

- ✅ Mutable Strings
- ✅ StringBuffer
- ✅ StringBuilder
- ✅ Thread Safety
- ✅ Synchronization
- ✅ Capacity & Length
- ✅ Performance Comparison
- ✅ Best Practices
- ✅ Interview Questions

➡️ **Next Chapter:** `18-Arrays-of-Objects.md`
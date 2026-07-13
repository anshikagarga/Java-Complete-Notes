# 📘 Chapter 16: Strings (Part 2)
## String Pool, Immutability & Memory Management

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the String Constant Pool.
- Explain why Strings are immutable.
- Understand memory allocation of String objects.
- Differentiate between String literals and `new String()`.
- Compare Strings using `==` and `equals()`.
- Understand Garbage Collection with Strings.
- Explain why Java made Strings immutable.

---

# 📚 Table of Contents

1. String Constant Pool
2. Why String Pool?
3. String Literal vs new String()
4. Internal Working
5. String Immutability
6. Memory Diagram
7. Why Strings are Immutable?
8. String Comparison
9. Garbage Collection
10. Best Practices
11. Common Mistakes
12. Interview Questions
13. Quick Revision
14. Practice Problems
15. Related Topics

---

# 🤔 Why do we need String Pool?

(Content)

---

# 📖 String Constant Pool

(Content)

---

# 🧠 Internal Working (JVM Perspective)

(Content)

---

# 📦 Memory Diagram (ASCII)

```text
           Heap
   +------------------+
   | String Pool      |
   |                  |
   | "Java"           |
   +--------▲---------+
            │
      ┌─────┴─────┐
      │           │
     s1          s2
```

---

# 📖 String Literal vs new String()

(Content)

---

# 🧠 Behind the Scene

(Content)

---

# 📦 Memory Diagram

```text
Stack                 Heap

name
 │
 ▼
Object ---------> "Naveen"

Pool
"Naveen"
```

---

# 📖 String Immutability

(Content)

---

# 🌍 Real World Example

(Content)

---

# ⚡ Time & Space Complexity

| Operation | Time |
|-----------|------|
| equals() | O(n) |
| == | O(1) |

---

# ⚠️ Common Mistakes

(Content)

---

# 💡 Best Practices

(Content)

---

# 🧩 Interview Questions

(Content)

---

# 📝 Quick Revision

(Content)

---

# 🧪 Practice Problems

(Content)

---

# 🔗 Related Topics

- StringBuffer
- StringBuilder
- Wrapper Classes
- Arrays

---

# 📚 References

- Java Documentation
- JVM Specification
- Effective Java
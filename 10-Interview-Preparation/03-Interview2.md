# 📘 Chapter 10: Java Interview Questions (Part 3)

> *"This chapter focuses on advanced Java interview questions related to Multithreading, File Handling, JDBC, JVM, Garbage Collection, Java 8, and real-world interview scenarios. These are among the most frequently asked topics in software engineering interviews."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Answer advanced Java interview questions.
- Understand JVM internals.
- Explain Garbage Collection.
- Revise Multithreading concepts.
- Answer JDBC interview questions.
- Revise Java 8 features.
- Prepare for real interview scenarios.

---

# 📚 Table of Contents

1. Multithreading Questions
2. File Handling Questions
3. JDBC Questions
4. JVM & Garbage Collection
5. Java 8 Questions
6. Scenario-Based Questions
7. MCQs
8. Best Practices
9. Chapter Summary

---

# 🎤 Java Interview Questions

## Q41. What is Multithreading?

### Answer

Multithreading is the process of executing multiple threads concurrently within a single process.

Advantages

- Better CPU utilization
- Faster execution
- Improved responsiveness
- Parallel task execution

---

## Q42. Difference between Process and Thread?

| Process | Thread |
|----------|---------|
| Independent program | Part of a process |
| Heavyweight | Lightweight |
| Separate memory | Shared memory |
| Higher creation cost | Lower creation cost |

---

## Q43. Difference between Thread and Runnable?

| Thread | Runnable |
|---------|-----------|
| Class | Interface |
| Uses inheritance | Uses interface implementation |
| Cannot extend another class | Can extend another class |
| Less flexible | More flexible |

---

## Q44. What is Synchronization?

### Answer

Synchronization ensures that only one thread accesses a shared resource at a time.

Keyword

```java
synchronized
```

Advantages

- Prevents race conditions
- Maintains data consistency
- Ensures thread safety

---

## Q45. What is Deadlock?

### Answer

Deadlock occurs when two or more threads wait indefinitely for resources held by each other.

Example

```text
Thread A → Waiting for Lock B

↓

Thread B → Waiting for Lock A
```

Result

```text
Program Hangs
```

---

## Q46. What is File Handling?

### Answer

File Handling is used to create, read, write, update, and delete files.

Common Classes

- File
- FileReader
- FileWriter
- BufferedReader
- BufferedWriter
- Scanner

---

## Q47. Difference between Byte Stream and Character Stream?

| Byte Stream | Character Stream |
|--------------|------------------|
| Binary Data | Text Data |
| InputStream / OutputStream | Reader / Writer |
| Images, PDFs | Text Files |

---

## Q48. What is Serialization?

### Answer

Serialization converts an object into a byte stream so that it can be stored or transmitted.

Interface

```java
Serializable
```

---

## Q49. What is Deserialization?

### Answer

Deserialization converts a byte stream back into a Java object.

Classes

- ObjectInputStream
- ObjectOutputStream

---

## Q50. What is JDBC?

### Answer

JDBC (Java Database Connectivity) is the standard API used to connect Java applications with relational databases.

---

## Q51. Difference between Statement and PreparedStatement?

| Statement | PreparedStatement |
|------------|-------------------|
| Dynamic SQL | Precompiled SQL |
| Slower | Faster |
| SQL Injection Possible | Prevents SQL Injection |
| No Parameters | Supports Parameters |

---

## Q52. What is SQL Injection?

### Answer

SQL Injection is a security vulnerability where malicious SQL statements are inserted through user input.

Solution

```java
PreparedStatement
```

---

## Q53. What is Garbage Collection?

### Answer

Garbage Collection automatically removes unused objects from heap memory.

Advantages

- Automatic memory management
- Prevents memory leaks
- Frees unused memory

---

## Q54. Which class performs Garbage Collection?

### Answer

Garbage Collection is managed automatically by the JVM's Garbage Collector.

Developers can request it using

```java
System.gc();
```

However, execution is **not guaranteed**.

---

## Q55. What is Java 8?

### Answer

Java 8 introduced several important features.

Major Features

- Lambda Expressions
- Stream API
- Functional Interfaces
- Method References
- Default Methods
- Optional Class
- Date & Time API

---

## Q56. What is a Functional Interface?

### Answer

A Functional Interface contains exactly one abstract method.

Example

```java
@FunctionalInterface

interface Demo{

    void show();

}
```

Examples

- Runnable
- Comparator
- Predicate
- Consumer
- Supplier
- Function

---

## Q57. What are Method References?

### Answer

Method References provide a shorter syntax for calling existing methods.

Example

```java
list.forEach(System.out::println);
```

---

## Q58. What is Optional?

### Answer

Optional is a container object that may or may not contain a value.

It helps avoid

```text
NullPointerException
```

Example

```java
Optional<String> name =

Optional.of("Java");
```

---

## Q59. Difference between map() and filter() in Stream API?

| map() | filter() |
|--------|-----------|
| Transforms data | Filters data |
| Returns modified values | Returns matching values |

Example

```java
list.stream()

.filter(x -> x > 10)

.map(x -> x * 2)

.forEach(System.out::println);
```

---

## Q60. Why should we use Streams?

### Answer

Advantages

- Less code
- Better readability
- Functional programming support
- Easy parallel processing
- Improved maintainability

---

# 🎯 Scenario-Based Interview Questions

### Q61. How would you prevent SQL Injection?

**Answer**

Use `PreparedStatement` instead of `Statement` because it uses parameterized queries.

---

### Q62. Which Collection would you use to store unique elements?

**Answer**

```java
HashSet
```

If sorting is required

```java
TreeSet
```

---

### Q63. Which Map would you use for fast lookups?

**Answer**

```java
HashMap
```

Average lookup time is **O(1)**.

---

### Q64. When would you use StringBuilder instead of String?

**Answer**

When frequent string modifications are required because `StringBuilder` is mutable and more efficient.

---

### Q65. How would you improve Java application performance?

**Answer**

- Use efficient algorithms.
- Choose appropriate collections.
- Reuse database connections with Connection Pooling.
- Use `PreparedStatement`.
- Minimize object creation.
- Use Streams where appropriate.
- Profile and optimize bottlenecks.

---

# 🎓 MCQs

### Q1. Which interface is used for Serialization?

- A. Serializable ✅
- B. Cloneable
- C. Runnable
- D. Comparable

---

### Q2. Which class is preferred for parameterized SQL queries?

- A. Statement
- B. PreparedStatement ✅
- C. CallableStatement
- D. ResultSet

---

### Q3. Which keyword is used for Synchronization?

- A. static
- B. synchronized ✅
- C. final
- D. volatile

---

### Q4. Which Java 8 feature supports functional programming?

- A. Threads
- B. Streams
- C. Lambda Expressions ✅
- D. Packages

---

### Q5. Which memory area stores objects?

- A. Stack
- B. Heap ✅
- C. Method Area
- D. PC Register

---

### Q6. Which collection stores unique elements?

- A. ArrayList
- B. LinkedList
- C. HashSet ✅
- D. Vector

---

### Q7. Which collection maintains insertion order?

- A. HashSet
- B. TreeSet
- C. LinkedHashSet ✅
- D. PriorityQueue

---

### Q8. Which interface represents a single abstract method?

- A. Runnable
- B. Functional Interface ✅
- C. Serializable
- D. Cloneable

---

### Q9. Which class helps avoid `NullPointerException`?

- A. Object
- B. Optional ✅
- C. String
- D. Stream

---

### Q10. Which Java version introduced the Stream API?

- A. Java 6
- B. Java 7
- C. Java 8 ✅
- D. Java 11

---

# 💻 Practice Questions

## Beginner

1. Explain JVM, JRE, and JDK.
2. Explain OOP principles with examples.
3. Differentiate Array and ArrayList.
4. Explain String Pool.
5. Explain Exception Handling.

---

## Intermediate

6. Compare HashMap and Hashtable.
7. Explain Synchronization with an example.
8. Implement a Functional Interface.
9. Write a program using Stream API.
10. Explain Serialization and Deserialization.

---

## Advanced

11. Explain Connection Pooling.
12. Implement CRUD operations using JDBC.
13. Explain Garbage Collection.
14. Explain Deadlock with an example.
15. Build a multithreaded producer-consumer application.

---

# 💡 Best Practices

- Explain concepts with real-world examples.
- Prefer `PreparedStatement` over `Statement`.
- Use `StringBuilder` for frequent string modifications.
- Use appropriate Collection classes.
- Avoid deprecated features like `finalize()`.
- Use Java 8 features effectively.
- Keep answers concise and structured.

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have successfully completed **10-Java-Interview-Questions.md**

### ✔️ Concepts Covered

- Core Java Interview Questions
- OOP Interview Questions
- String Interview Questions
- Collections Interview Questions
- Exception Handling Questions
- Multithreading Questions
- File Handling Questions
- JDBC Questions
- JVM & Garbage Collection
- Java 8 Questions
- Scenario-Based Questions
- MCQs
- Practice Questions

---

# 📌 Key Takeaways

- ✅ Understand concepts instead of memorizing answers.
- ✅ Be comfortable explaining Java internals like JVM, Garbage Collection, and Memory Management.
- ✅ Revise Collections, Exception Handling, JDBC, and Multithreading regularly.
- ✅ Practice Java 8 features such as Streams, Lambda Expressions, and Optional.
- ✅ Strengthen coding skills alongside theoretical preparation for technical interviews.

---

# 🚀 Next Chapter

➡️ **11-System-Design-Basics.md**

### Topics Covered

- What is System Design?
- Functional vs Non-Functional Requirements
- Scalability
- Load Balancer
- Caching
- Database Basics
- CAP Theorem
- High-Level Design (HLD)
- Low-Level Design (LLD)
- Interview Questions
- MCQs
- Practice Problems
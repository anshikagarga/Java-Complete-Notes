# 📘 Chapter 06: Streams and Java 8 (Part 3)

## Optional, Date & Time API, Default Methods, Parallel Streams, Interview Questions & Chapter Summary

> *"Java 8 introduced several powerful features beyond the Stream API, such as Optional, the modern Date & Time API, Default Methods, and Parallel Streams, making Java more expressive, safer, and easier to develop."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Optional class.
- Learn the Java 8 Date & Time API.
- Understand Default and Static methods in Interfaces.
- Learn Parallel Streams.
- Solve interview questions.
- Practice MCQs.
- Revise all Java 8 concepts.

---

# 📚 Table of Contents

1. Optional Class
2. Date & Time API
3. Default Methods
4. Static Methods in Interfaces
5. Parallel Streams
6. Best Practices
7. Common Mistakes
8. Interview Questions
9. MCQs
10. Quick Revision
11. Practice Problems
12. Related Topics
13. References
14. Chapter Summary

---

# 📖 Optional Class

The **Optional** class is a container object that may or may not contain a value.

It helps avoid:

- NullPointerException
- Explicit null checks
- Cleaner code

---

## Creating Optional Objects

### Using of()

```java
Optional<String> name = Optional.of("Anshika");

System.out.println(name.get());
```

Output

```text
Anshika
```

---

### Using ofNullable()

```java
String name = null;

Optional<String> optional = Optional.ofNullable(name);

System.out.println(optional);
```

Output

```text
Optional.empty
```

---

### Using empty()

```java
Optional<String> optional = Optional.empty();

System.out.println(optional);
```

Output

```text
Optional.empty
```

---

# 📖 Useful Optional Methods

| Method | Purpose |
|---------|----------|
| `get()` | Returns the value |
| `isPresent()` | Checks whether a value exists |
| `orElse()` | Returns default value |
| `orElseGet()` | Returns value from Supplier if empty |
| `orElseThrow()` | Throws exception if value is absent |
| `ifPresent()` | Executes code if value exists |

---

## Example

```java
Optional<String> name = Optional.ofNullable(null);

System.out.println(

    name.orElse("Guest")

);
```

Output

```text
Guest
```

---

# 📖 Date & Time API

Before Java 8, developers used:

- Date
- Calendar

These classes had several design issues.

Java 8 introduced the **java.time** package.

Common Classes

- LocalDate
- LocalTime
- LocalDateTime
- Period
- Duration
- DateTimeFormatter

---

## LocalDate

```java
LocalDate today = LocalDate.now();

System.out.println(today);
```

Output

```text
2026-07-24
```

---

## LocalTime

```java
LocalTime time = LocalTime.now();

System.out.println(time);
```

Possible Output

```text
18:30:12.123
```

---

## LocalDateTime

```java
LocalDateTime now = LocalDateTime.now();

System.out.println(now);
```

Possible Output

```text
2026-07-24T18:30:12.123
```

---

## Formatting Date

```java
LocalDate date = LocalDate.now();

DateTimeFormatter formatter =

    DateTimeFormatter.ofPattern("dd-MM-yyyy");

System.out.println(date.format(formatter));
```

Output

```text
24-07-2026
```

---

# 📖 Default Methods

Java 8 allows interfaces to contain method implementations using the **default** keyword.

Example

```java
interface Animal{

    default void sound(){

        System.out.println("Animal Sound");

    }

}
```

Implementing Class

```java
class Dog implements Animal{

}
```

```java
Dog d = new Dog();

d.sound();
```

Output

```text
Animal Sound
```

---

# 📖 Why Default Methods?

Before Java 8, adding a new method to an interface would break all implementing classes.

Default methods solve this problem by providing a default implementation.

Benefits

- Backward Compatibility
- Interface Evolution
- Less Code Duplication

---

# 📖 Static Methods in Interfaces

Interfaces can also contain static methods.

Example

```java
interface Calculator{

    static void show(){

        System.out.println("Static Method");

    }

}
```

Calling

```java
Calculator.show();
```

Output

```text
Static Method
```

Static interface methods cannot be overridden by implementing classes.

---

# 📖 Parallel Streams

A Parallel Stream processes data using multiple threads.

Sequential Stream

```java
list.stream()
```

Parallel Stream

```java
list.parallelStream()
```

or

```java
list.stream()

    .parallel()
```

---

## Example

```java
List<Integer> list =

    List.of(10,20,30,40,50);

list.parallelStream()

    .forEach(System.out::println);
```

Output

The order is **not guaranteed** because elements are processed concurrently.

Possible Output

```text
30
10
50
20
40
```

---

# 📊 Stream vs Parallel Stream

| Stream | Parallel Stream |
|---------|-----------------|
| Single Thread | Multiple Threads |
| Predictable Order | Order may change |
| Lower Overhead | Better for large datasets |
| Easier to Debug | More Complex |

---

# 📦 Internal Working

```text
Collection

↓

Stream

↓

Lambda Expression

↓

Intermediate Operations

↓

Terminal Operation

↓

Result
```

Parallel Stream

```text
Collection

↓

Split into Multiple Parts

↓

Multiple Threads

↓

Process Data

↓

Combine Results
```

---

# ⚠️ Common Mistakes

## ❌ Calling get() Without Checking

Wrong

```java
Optional<String> name = Optional.empty();

System.out.println(name.get());
```

Output

```text
NoSuchElementException
```

Correct

```java
System.out.println(

    name.orElse("Guest")

);
```

---

## ❌ Using Parallel Streams for Small Collections

Parallel processing introduces thread-management overhead.

For small collections, sequential streams are usually faster.

---

## ❌ Using Streams for Heavy Side Effects

Avoid modifying external variables inside stream operations.

Streams work best with pure, stateless functions.

---

# 💡 Best Practices

- Prefer `Optional` over returning `null`.
- Use `orElse()` or `orElseThrow()` instead of blindly calling `get()`.
- Use `java.time` instead of `Date` and `Calendar` for new code.
- Keep stream operations stateless and side-effect free.
- Use Parallel Streams only after performance testing.
- Use Default Methods to evolve interfaces without breaking existing implementations.

---

# 🌍 Real-World Applications

Java 8 features are widely used in:

- Spring Boot Applications
- Microservices
- REST APIs
- Banking Software
- E-Commerce Platforms
- Analytics Systems
- Data Processing Pipelines
- Cloud Applications

---

# 🧩 Interview Questions

## Beginner

1. What are the major features introduced in Java 8?
2. What is a Lambda Expression?
3. What is a Functional Interface?
4. What is the Stream API?
5. What is the Optional class?

---

## Intermediate

6. Difference between Stream and Parallel Stream.
7. Difference between map() and filter().
8. Difference between Optional.of() and Optional.ofNullable().
9. What are Default Methods?
10. What are Static Methods in Interfaces?

---

## Advanced

11. Explain Lazy Evaluation in Streams.
12. Why was the Date & Time API introduced?
13. When should Parallel Streams be avoided?
14. What is Method Reference?
15. Explain Intermediate and Terminal Operations.

---

# 🎓 MCQs

### Q1. Which package contains the Stream API?

- A. java.stream
- B. java.io
- C. java.util.stream ✅
- D. java.lang.stream

---

### Q2. Which class helps avoid NullPointerException?

- A. Objects
- B. Optional ✅
- C. Stream
- D. Date

---

### Q3. Which method creates a parallel stream?

- A. streamParallel()
- B. parallel()
- C. parallelStream() ✅
- D. parallelData()

---

### Q4. Which package contains `LocalDate`?

- A. java.sql
- B. java.time ✅
- C. java.date
- D. java.util

---

### Q5. Which keyword is used to create a default method?

- A. public
- B. final
- C. default ✅
- D. static

---

# 📝 Quick Revision

## Lambda Expression

```java
(a, b) -> a + b
```

---

## Method Reference

```java
System.out::println
```

---

## Stream

```java
list.stream()
```

---

## Parallel Stream

```java
list.parallelStream()
```

---

## Optional

```java
Optional.ofNullable(value)

        .orElse("Default");
```

---

## Date & Time

```java
LocalDate.now();

LocalTime.now();

LocalDateTime.now();
```

---

# 🧪 Practice Problems

## Beginner

- Print even numbers using Streams.
- Convert names to uppercase using `map()`.
- Remove duplicates using `distinct()`.

---

## Intermediate

- Find the maximum salary using Streams.
- Count students with marks greater than 80.
- Sort employees using Streams.

---

## Advanced

- Build an Employee Management System using Stream API.
- Create a Sales Report Generator using Streams.
- Process large datasets using Parallel Streams.
- Implement a Student Analytics Dashboard using Java 8 features.

---

# 🔗 Related Topics

- Collections Framework
- Multithreading
- File Handling
- JDBC
- Spring Boot
- Functional Programming

---

# 📚 References

- Oracle Java Documentation
- Effective Java by Joshua Bloch
- Java: The Complete Reference
- OpenJDK Documentation
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 06: Streams and Java 8**.

### ✔️ Concepts Covered

- Java 8 Features
- Functional Programming
- Lambda Expressions
- Functional Interfaces
- Method References
- Stream API
- Intermediate Operations
- Terminal Operations
- Optional Class
- Date & Time API
- Default Methods
- Static Methods in Interfaces
- Parallel Streams
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Java 8 introduced Functional Programming concepts into Java.
- ✅ Lambda Expressions make code shorter and more readable.
- ✅ Stream API simplifies processing collections.
- ✅ `Optional` helps reduce `NullPointerException`.
- ✅ The `java.time` package replaces the older Date and Calendar APIs.
- ✅ Default methods allow interfaces to evolve without breaking existing implementations.
- ✅ Parallel Streams can improve performance for large, CPU-intensive workloads but should be used carefully.

---

# 🚀 Next Chapter

➡️ **07-File-Handling.md**

### Topics Covered

- Introduction to File Handling
- File Class
- Reading Files
- Writing Files
- Buffered Streams
- Character vs Byte Streams
- Serialization
- Deserialization
- Interview Questions
- MCQs
- Practice Problems
# 📘 Chapter 06: Streams and Java 8 (Part 1)

> *"Java 8 was one of the biggest releases in Java history. It introduced Functional Programming concepts, Lambda Expressions, Stream API, Method References, and many other features that simplified Java development and improved performance."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Java 8 Features.
- Learn Functional Programming.
- Understand Lambda Expressions.
- Learn Functional Interfaces.
- Understand Method References.
- Learn Stream API basics.
- Know why Java 8 is important in modern development.

---

# 📚 Table of Contents

1. Introduction to Java 8
2. Why Java 8?
3. Features of Java 8
4. Functional Programming
5. Lambda Expressions
6. Functional Interfaces
7. Method References
8. Stream API Introduction
9. Internal Working
10. Real-World Applications

---

# 🤔 What is Java 8?

Java 8 is one of the most significant versions of Java released by Oracle.

It introduced:

- Functional Programming
- Lambda Expressions
- Stream API
- Method References
- Optional Class
- Date & Time API
- Default Methods
- Static Interface Methods

These features made Java code:

- Cleaner
- Shorter
- Faster
- Easier to Read
- More Maintainable

---

# 💡 Why Java 8?

Before Java 8, Java code was often lengthy.

Example (Before Java 8)

```java
Collections.sort(list, new Comparator<Integer>() {

    @Override
    public int compare(Integer a, Integer b) {

        return a - b;

    }

});
```

Java 8

```java
Collections.sort(list, (a, b) -> a - b);
```

Much shorter and easier to understand.

---

# 🚀 Major Features of Java 8

- Lambda Expressions
- Functional Interfaces
- Stream API
- Method References
- Optional Class
- Date & Time API
- Default Methods
- Static Methods in Interfaces
- Parallel Streams
- Nashorn JavaScript Engine (deprecated in later versions)

---

# 📖 Functional Programming

Functional Programming focuses on:

- Functions
- Immutability
- Declarative Code
- Less Boilerplate

Instead of telling **how** to perform a task, we describe **what** should be done.

Example

Traditional

```java
for(int i=0;i<list.size();i++){

    System.out.println(list.get(i));

}
```

Java 8

```java
list.forEach(System.out::println);
```

---

# 📖 Lambda Expression

A Lambda Expression is an anonymous function.

Syntax

```java
(parameters) -> expression
```

or

```java
(parameters) -> {

    statements;

}
```

---

## Example

Before Java 8

```java
Runnable r = new Runnable(){

    @Override
    public void run(){

        System.out.println("Hello");

    }

};
```

After Java 8

```java
Runnable r = () -> System.out.println("Hello");
```

---

# 📖 Advantages of Lambda Expressions

- Less Code
- Better Readability
- Functional Programming Support
- Easier Event Handling
- Better Collection Processing
- Works perfectly with Streams

---

# 📖 Functional Interface

A Functional Interface contains **exactly one abstract method**.

Examples

- Runnable
- Comparator
- Callable
- Consumer
- Supplier
- Predicate
- Function

---

## Example

```java
@FunctionalInterface

interface Demo{

    void display();

}
```

Lambda

```java
Demo d = () -> System.out.println("Java");

d.display();
```

Output

```text
Java
```

---

# 📖 @FunctionalInterface Annotation

This annotation tells the compiler that the interface must contain only one abstract method.

```java
@FunctionalInterface

interface Test{

    void show();

}
```

Adding another abstract method results in a compile-time error.

---

# 📖 Method Reference

A Method Reference is a shorthand for a lambda expression that simply calls an existing method.

Syntax

```java
ClassName::methodName
```

---

## Example

Lambda

```java
list.forEach(x -> System.out.println(x));
```

Method Reference

```java
list.forEach(System.out::println);
```

Output

```text
Java
Python
C++
```

---

# 📖 Types of Method References

### Static Method

```java
ClassName::staticMethod
```

---

### Instance Method of Particular Object

```java
object::instanceMethod
```

---

### Instance Method of Arbitrary Object

```java
ClassName::instanceMethod
```

---

### Constructor Reference

```java
ClassName::new
```

---

# 📖 Introduction to Stream API

A Stream is used to process collections of data efficiently.

A Stream does **not** store data.

It performs operations on data coming from a source such as:

- Array
- ArrayList
- HashSet
- HashMap (through entry sets)
- Files

---

## Example

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);
list.add(30);

list.stream()

    .forEach(System.out::println);
```

Output

```text
10
20
30
```

---

# 📦 Internal Working

```text
Collection

↓

Stream()

↓

Intermediate Operations

↓

Terminal Operation

↓

Result
```

---

# 🌍 Real-World Applications

Java 8 is heavily used in:

- Spring Boot
- Microservices
- REST APIs
- Banking Applications
- E-Commerce Platforms
- Android (Partial Support)
- Big Data
- Backend Development

---

# 🎯 Interview Tip

### Question

Why was Java 8 considered a revolutionary release?

### Answer

Because it introduced Functional Programming concepts like Lambda Expressions, Stream API, Functional Interfaces, Method References, Optional, and the Date & Time API, making Java code shorter, cleaner, and more efficient.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Stream API
- Intermediate Operations
- Terminal Operations
- Filter
- Map
- Sorted
- Distinct
- Limit
- Skip
- Reduce
- Collect
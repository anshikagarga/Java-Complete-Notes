# 📘 Chapter 10: Java Interview Questions (Part 1)

> *"Java interviews usually begin with Core Java concepts. Before asking coding questions, interviewers test your understanding of Java fundamentals, OOP, memory management, JVM, and commonly used language features."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Answer Core Java interview questions confidently.
- Understand important Java concepts.
- Learn commonly asked interview questions.
- Prepare for fresher and experienced Java interviews.
- Build a strong conceptual foundation.

---

# 📚 Table of Contents

1. Java Basics
2. JVM, JRE & JDK
3. OOP Questions
4. Variables & Memory
5. Constructors
6. this & super
7. Wrapper Classes
8. String Questions
9. Arrays
10. Interview Tips

---

# 🎤 Java Interview Questions

## Q1. What is Java?

### Answer

Java is a high-level, object-oriented, platform-independent programming language developed by Sun Microsystems (now Oracle).

Features

- Platform Independent
- Object-Oriented
- Robust
- Secure
- Multithreaded
- Portable
- High Performance (using JIT Compiler)

---

## Q2. Why is Java Platform Independent?

### Answer

Java source code is compiled into **Bytecode (.class)**.

The bytecode runs on the **Java Virtual Machine (JVM)**, which is available for different operating systems.

```text
Java Code (.java)

↓

Compiler (javac)

↓

Bytecode (.class)

↓

JVM

↓

Windows / Linux / macOS
```

---

## Q3. Difference between JDK, JRE and JVM?

| JDK | JRE | JVM |
|-----|-----|-----|
| Java Development Kit | Java Runtime Environment | Java Virtual Machine |
| Used for Development | Used to Run Java Programs | Executes Bytecode |
| Contains Compiler | Contains JVM | Converts Bytecode into Machine Code |

---

## Q4. What are the features of Java?

### Answer

- Platform Independent
- Object-Oriented
- Secure
- Robust
- Portable
- Architecture Neutral
- Dynamic
- Multithreaded
- High Performance
- Distributed

---

## Q5. What is JVM?

### Answer

JVM (Java Virtual Machine) is a virtual machine that executes Java bytecode.

Responsibilities

- Loads classes
- Verifies bytecode
- Executes bytecode
- Performs Garbage Collection
- Manages Memory

---

## Q6. What is JIT Compiler?

### Answer

JIT (Just-In-Time) Compiler converts frequently executed bytecode into native machine code during runtime.

Advantages

- Faster execution
- Improved performance
- Reduced interpretation overhead

---

## Q7. What is ClassLoader?

### Answer

ClassLoader loads Java classes into JVM memory dynamically.

Types

- Bootstrap ClassLoader
- Platform (Extension) ClassLoader
- Application ClassLoader

---

## Q8. What are the Memory Areas in JVM?

### Answer

JVM Memory is divided into

```text
Heap Memory

Method Area

Stack Memory

PC Register

Native Method Stack
```

---

## Q9. Difference between Heap and Stack Memory?

| Heap Memory | Stack Memory |
|--------------|--------------|
| Stores Objects | Stores Local Variables |
| Shared | Thread Specific |
| Managed by Garbage Collector | Automatically Released After Method Execution |
| Larger | Smaller |

---

## Q10. What is Object-Oriented Programming (OOP)?

### Answer

OOP is a programming paradigm based on objects.

Four Pillars

- Encapsulation
- Inheritance
- Polymorphism
- Abstraction

---

## Q11. What is a Class?

### Answer

A class is a blueprint or template used to create objects.

Example

```java
class Student{

    int id;

    String name;

}
```

---

## Q12. What is an Object?

### Answer

An object is an instance of a class.

Example

```java
Student s = new Student();
```

Here,

- `Student` → Class
- `s` → Object Reference
- `new Student()` → Object

---

## Q13. What is Encapsulation?

### Answer

Encapsulation is the process of wrapping data and methods into a single unit (class).

It is achieved using

- Private variables
- Public getter and setter methods

Advantages

- Data Hiding
- Better Security
- Better Maintainability

---

## Q14. What is Inheritance?

### Answer

Inheritance allows one class to acquire the properties and methods of another class.

Keyword

```java
extends
```

Advantages

- Code Reusability
- Reduced Code Duplication
- Easy Maintenance

---

## Q15. What is Polymorphism?

### Answer

Polymorphism means **"one interface, many forms."**

Types

- Compile-Time Polymorphism (Method Overloading)
- Runtime Polymorphism (Method Overriding)

---

## Q16. What is Abstraction?

### Answer

Abstraction hides implementation details and shows only essential features.

It is achieved using

- Abstract Classes
- Interfaces

---

## Q17. What is the difference between Method Overloading and Method Overriding?

| Method Overloading | Method Overriding |
|--------------------|-------------------|
| Same Method Name | Same Method Name |
| Different Parameters | Same Parameters |
| Compile-Time Polymorphism | Runtime Polymorphism |
| Same Class | Parent & Child Class |

---

## Q18. What is a Constructor?

### Answer

A constructor is a special method that initializes an object.

Properties

- Same name as class
- No return type
- Called automatically when an object is created

Example

```java
class Student{

    Student(){

        System.out.println("Constructor Called");

    }

}
```

---

## Q19. What is the difference between Default Constructor and Parameterized Constructor?

| Default Constructor | Parameterized Constructor |
|----------------------|---------------------------|
| No Parameters | Has Parameters |
| Initializes Default Values | Initializes User-Defined Values |

---

## Q20. What is the `this` keyword?

### Answer

`this` refers to the current object.

Uses

- Access instance variables
- Call current class methods
- Invoke another constructor using `this()`
- Pass current object as an argument

Example

```java
class Student{

    int id;

    Student(int id){

        this.id = id;

    }

}
```

---

# 💡 Interview Tips

- Focus on explaining concepts with examples.
- Use simple and precise language.
- Mention real-world use cases whenever possible.
- Don't memorize definitions; understand the concepts.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- `super` Keyword
- final, finally, finalize()
- Static Keyword
- Access Modifiers
- String vs StringBuilder vs StringBuffer
- Exception Handling Questions
- Collections Framework Questions
- Java 8 Questions
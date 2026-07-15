# 📘 Chapter 14: static Keyword (Part 3)

## Static vs Non-static, Singleton Pattern, Interview Preparation & Best Practices

> *"The `static` keyword enables class-level behavior, while non-static members belong to individual objects. Understanding when to use each is essential for writing efficient and maintainable Java applications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Differentiate between static and non-static members.
- Understand the Singleton Design Pattern.
- Learn Static Factory Methods.
- Understand the JVM memory model for static members.
- Prepare for Java interview questions.
- Revise the complete static keyword chapter.

---

# 📚 Table of Contents

1. Static vs Non-static
2. Static Factory Methods
3. Singleton Pattern
4. JVM Memory Model
5. Memory Diagram
6. Real-World Examples
7. Time & Space Complexity
8. Common Mistakes
9. Best Practices
10. Interview Questions
11. Quick Revision
12. Practice Problems
13. Related Topics
14. References
15. Chapter Summary

---

# 📖 Static vs Non-static

| Feature | Static | Non-static |
|----------|---------|------------|
| Belongs To | Class | Object |
| Memory Allocation | Once | Every Object |
| Access | Class Name | Object |
| Shared | ✅ Yes | ❌ No |
| Can Access Instance Variables | ❌ No | ✅ Yes |
| Requires Object | ❌ No | ✅ Yes |

---

## Example

```java
class Student{

    static String college = "AKTU";

    String name;

}
```

Memory

```text
Method Area

college = AKTU

↓

Heap

Student 1

name = Anshika

-------------

Student 2

name = Rahul
```

The college name is shared,

while each student has a different name.

---

# 📖 Static Factory Method

Instead of using constructors directly,

Java often provides static methods that create objects.

Example

```java
Integer num = Integer.valueOf("100");
```

Here,

```java
valueOf()
```

is a static factory method.

---

Another Example

```java
List<String> list = List.of("Java", "React");
```

Instead of

```java
new ArrayList<>();
```

Java internally creates the appropriate implementation.

---

# 🤔 Advantages of Static Factory Methods

- Better readability
- Can cache objects
- Can return subclasses
- Better control over object creation
- Improved performance

---

# 📖 Singleton Pattern

Sometimes,

we want only **one object** of a class.

Examples

- Database Connection
- Logger
- Configuration Manager
- Cache Manager

The Singleton Pattern ensures only one instance exists.

---

## Example

```java
class Database{

    private static Database obj = new Database();

    private Database(){

    }

    public static Database getInstance(){

        return obj;

    }

}
```

Using

```java
Database db1 = Database.getInstance();

Database db2 = Database.getInstance();
```

Memory

```text
db1

↓

Database Object

↑

db2
```

Both references point to the same object.

---

# 🧠 JVM Memory Model

```text
Program Starts

        │

        ▼

Class Loader

        │

        ▼

Method Area

        │

        ├── Static Variables

        ├── Static Methods

        └── Static Blocks

        │

        ▼

Heap

(Object Instances)

        │

        ▼

Stack

(Method Calls)
```

Static members remain in memory until the class is unloaded.

---

# 📦 Memory Diagram

```text
Method Area

+-------------------------+

Student.class

college = AKTU

count = 10

display()

+-------------------------+

          ▲

          │

Heap

+--------------------+

Student Object

name = Anshika

+--------------------+

+--------------------+

Student Object

name = Rahul

+--------------------+
```

Only one copy of static members exists.

---

# 🚀 Real-World Example

## Employee Management System

Every employee has

- Employee ID
- Name
- Salary

But every employee belongs to the same company.

```java
class Employee{

    static String company = "Google";

    String name;

}
```

Memory

```text
Google

↑

Shared

↑

Employee 1

Employee 2

Employee 3
```

---

# 🌍 Real-World Applications

The `static` keyword is widely used in:

- `Math` Class
- `Collections` Utility Class
- `Arrays` Utility Class
- `Objects` Utility Class
- Singleton Pattern
- Logger Classes
- Spring Boot Utilities
- Hibernate Utility Classes
- Builder Pattern Helpers

---

# ⚡ Time & Space Complexity

| Operation | Complexity |
|-----------|------------|
| Static Variable Access | O(1) |
| Static Method Call | O(1) |
| Static Block Execution | O(1) *(Executed once)* |
| Object Creation | O(number of fields) |

---

# ⚠️ Common Mistakes

## ❌ Accessing Instance Variables

Wrong

```java
static void show(){

    System.out.println(name);

}
```

Correct

```java
Student s = new Student();

System.out.println(s.name);
```

---

## ❌ Using `this` in Static Methods

Wrong

```java
static void show(){

    this.display();

}
```

Compilation Error

```
non-static variable this cannot be referenced from a static context
```

---

## ❌ Assuming Static Variables are Thread Safe

Static variables are shared across all threads.

If multiple threads modify the same static variable without synchronization, race conditions can occur.

---

## ❌ Storing Object-specific Data in Static Variables

Wrong

```java
static String studentName;
```

Each object should have its own name.

---

# 💡 Best Practices

- Use static only for shared data.
- Prefer static methods for utility functions.
- Avoid global mutable static variables.
- Keep static initialization lightweight.
- Use Singleton only when one instance is genuinely required.
- Access static members using the class name instead of an object reference.

---

# 🧩 Interview Questions

## Beginner

1. What is the `static` keyword?
2. Why are static variables shared?
3. Can we access static methods without creating an object?
4. Can constructors be static?
5. What is a static block?

---

## Intermediate

6. Difference between static and non-static methods.
7. Why can't static methods access instance variables directly?
8. What is static import?
9. Explain class loading.
10. Explain static nested classes.

---

## Advanced

11. Explain the JVM memory model for static members.
12. What is the Singleton Pattern?
13. Why are static methods not overridden?
14. What happens when a class is loaded?
15. Explain static factory methods with examples.
16. Are static variables thread-safe?

---

# 📝 Quick Revision

## Static Variable

```text
Class

↓

One Copy

↓

Shared by All Objects
```

---

## Static Method

```text
Class Name

↓

Method Call

↓

No Object Required
```

---

## Class Loading

```text
Program Starts

↓

Class Loader

↓

Method Area

↓

Static Variables

↓

Static Block

↓

main()

↓

Objects
```

---

## Singleton

```text
getInstance()

↓

Single Object

↓

Shared Everywhere
```

---

# 🧪 Practice Problems

### Beginner

- Create a class with a static variable.
- Create a static method.
- Count the number of objects using a static counter.

---

### Intermediate

- Create multiple objects and observe shared static variables.
- Demonstrate static block execution.
- Use static import with the `Math` class.

---

### Advanced

- Implement the Singleton Pattern.
- Build a Student Management System using static variables.
- Create a Logger class using Singleton.
- Explain the JVM memory flow for static members.

---

# 🔗 Related Topics

- Classes & Objects
- Constructors
- `this` Keyword
- `super` Keyword
- Method Overloading
- Inheritance
- JVM Memory Model
- Singleton Pattern
- Builder Pattern
- Design Patterns

---

# 📚 References

- Oracle Java Documentation
- Java Language Specification (JLS)
- Effective Java – Joshua Bloch
- Head First Java

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 14: static Keyword**.

### ✔️ Concepts Covered

- What is `static`?
- Static Variables
- Static Methods
- Static Blocks
- Static Nested Classes
- Static Import
- JVM Class Loading
- Memory Allocation
- Static Factory Methods
- Singleton Pattern
- Best Practices
- Interview Questions

---

# 📌 Key Takeaways

- ✅ `static` members belong to the **class**, not individual objects.
- ✅ Only **one copy** of a static variable exists, shared across all objects.
- ✅ Static methods can be called **without creating an object**.
- ✅ Static blocks execute **only once** when the class is loaded.
- ✅ Static methods **cannot directly access instance variables or use `this`**.
- ✅ Static nested classes don't require an outer class object.
- ✅ Static factory methods provide flexible and readable object creation.
- ✅ The Singleton Pattern uses `static` to ensure a single shared instance.
- ✅ Use `static` only for class-level behavior and shared resources.

---

# 🚀 Next Chapter

➡️ **15-Wrapper-Classes.md**

### Topics Covered

- Primitive Data Types vs Wrapper Classes
- Why Wrapper Classes?
- Boxing & Auto-boxing
- Unboxing & Auto-unboxing
- Parsing Methods
- Utility Methods
- Caching Mechanism
- Memory Model
- Interview Questions
- Practice Problems
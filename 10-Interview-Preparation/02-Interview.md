# 📘 Chapter 10: Java Interview Questions (Part 2)

> *"This section covers advanced Core Java interview questions that are frequently asked in interviews for Java Developer, Full Stack Developer, and Software Engineer roles."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand advanced Java concepts
- Answer frequently asked interview questions
- Explain Java keywords confidently
- Differentiate important Java concepts
- Prepare for technical interviews

---

# 📚 Table of Contents

1. super Keyword
2. final, finally & finalize()
3. Static Keyword
4. Access Modifiers
5. String Questions
6. Exception Handling
7. Collections Framework
8. Java 8 Questions
9. Interview Tips

---

# 🎤 Java Interview Questions

## Q21. What is the `super` keyword?

### Answer

The `super` keyword refers to the immediate parent class object.

Uses

- Access parent class variables
- Call parent class methods
- Invoke parent class constructor

Example

```java
class Animal{

    Animal(){

        System.out.println("Animal Constructor");

    }

}

class Dog extends Animal{

    Dog(){

        super();

        System.out.println("Dog Constructor");

    }

}
```

---

## Q22. Difference between `this` and `super`?

| this | super |
|------|-------|
| Refers to current object | Refers to parent object |
| Access current class members | Access parent class members |
| Calls current constructor | Calls parent constructor |

---

## Q23. What is the `final` keyword?

### Answer

The `final` keyword is used to restrict modification.

It can be applied to

- Variable
- Method
- Class

Example

```java
final int MAX = 100;
```

---

## Q24. Difference between `final`, `finally`, and `finalize()`?

| final | finally | finalize() |
|--------|----------|------------|
| Keyword | Block | Method |
| Restricts modification | Executes after try-catch | Invoked by Garbage Collector (deprecated) |
| Used with variables, methods, classes | Used in exception handling | Defined in Object class |

> **Note:** `finalize()` has been deprecated and should not be used in modern Java.

---

## Q25. What is the `static` keyword?

### Answer

`static` belongs to the class rather than an object.

It can be used with

- Variables
- Methods
- Blocks
- Nested Classes

Example

```java
class Student{

    static String college = "ABC College";

}
```

---

## Q26. Can we override a static method?

### Answer

No.

Static methods belong to the class, not to objects.

They are **hidden**, not overridden.

---

## Q27. Can we overload static methods?

### Answer

Yes.

Example

```java
class Demo{

    static void show(){}

    static void show(int a){}

}
```

---

## Q28. What are Access Modifiers?

### Answer

Access modifiers control the visibility of classes, variables and methods.

Types

- private
- default
- protected
- public

---

## Q29. Difference between Public, Protected, Default and Private?

| Modifier | Same Class | Same Package | Subclass | Other Package |
|-----------|------------|--------------|-----------|---------------|
| public | ✅ | ✅ | ✅ | ✅ |
| protected | ✅ | ✅ | ✅ | ❌* |
| default | ✅ | ✅ | ❌ | ❌ |
| private | ✅ | ❌ | ❌ | ❌ |

*Accessible in another package only through inheritance.

---

## Q30. Difference between String, StringBuilder and StringBuffer?

| String | StringBuilder | StringBuffer |
|----------|---------------|--------------|
| Immutable | Mutable | Mutable |
| Slow for modification | Fast | Fast |
| Thread Safe | ❌ | ✅ |
| Most Used | Performance | Multi-threading |

---

## Q31. Why is String immutable?

### Answer

String is immutable because it provides

- Security
- Thread Safety
- String Pool optimization
- Better performance

---

## Q32. What is String Pool?

### Answer

String Pool is a special memory area inside the Heap that stores string literals.

Example

```java
String s1 = "Java";

String s2 = "Java";
```

Both references point to the same object in the String Pool.

---

## Q33. What is Exception Handling?

### Answer

Exception Handling is the mechanism used to handle runtime errors gracefully.

Keywords

- try
- catch
- finally
- throw
- throws

---

## Q34. Difference between Checked and Unchecked Exceptions?

| Checked Exception | Unchecked Exception |
|-------------------|---------------------|
| Checked at Compile Time | Occur at Runtime |
| Must be handled | Optional to handle |
| IOException | NullPointerException |

---

## Q35. Difference between throw and throws?

| throw | throws |
|--------|---------|
| Used to explicitly throw an exception | Declares exceptions |
| Used inside method | Used in method signature |

Example

```java
throw new ArithmeticException();
```

---

## Q36. What is the Collections Framework?

### Answer

Collections Framework is a set of interfaces and classes used to store and manipulate groups of objects.

Main Interfaces

- List
- Set
- Queue
- Map (part of the Collections Framework but not a subtype of `Collection`)

---

## Q37. Difference between Array and ArrayList?

| Array | ArrayList |
|--------|-----------|
| Fixed Size | Dynamic Size |
| Stores primitives and objects | Stores objects (or wrapper classes) |
| Faster | More Flexible |

---

## Q38. Difference between HashMap and Hashtable?

| HashMap | Hashtable |
|----------|------------|
| Not Thread Safe | Thread Safe |
| Allows one null key | Does not allow null keys or values |
| Faster | Slower |

---

## Q39. What are Lambda Expressions?

### Answer

Lambda Expressions provide a concise way to implement functional interfaces.

Syntax

```java
(parameters) -> expression
```

Example

```java
(a, b) -> a + b
```

---

## Q40. What are Streams in Java?

### Answer

Streams process collections of data in a functional style.

Common Operations

- filter()
- map()
- sorted()
- distinct()
- limit()
- skip()
- collect()
- forEach()

Example

```java
list.stream()

.filter(x -> x > 10)

.forEach(System.out::println);
```

---

# 💡 Interview Tips

- Explain concepts before giving examples.
- Use comparison tables wherever possible.
- Mention practical applications.
- Highlight modern Java practices (e.g., avoid `finalize()`, prefer `StringBuilder` for repeated concatenation, use Streams where appropriate).

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Multithreading Questions
- File Handling Questions
- JDBC Questions
- JVM & Garbage Collection
- Java 8 Advanced Questions
- Spring Boot Basics
- Most Asked HR + Java Scenario Questions
- MCQs
- Chapter Summary
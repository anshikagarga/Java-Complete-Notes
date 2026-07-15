# 📘 Chapter 14: static Keyword (Part 2)

## Static Blocks, Static Nested Classes, Static Import & JVM Class Loading

> *"Before any object is created, Java loads the class into memory. During this process, static variables and static blocks are initialized. Understanding this lifecycle helps developers write efficient and predictable Java programs."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Static Blocks.
- Learn why Static Blocks are used.
- Understand JVM Class Loading.
- Learn Static Nested Classes.
- Understand Static Import.
- Learn the initialization order in Java.
- Understand how static members are loaded into memory.

---

# 📚 Table of Contents

1. Static Block
2. Why Static Block?
3. Static Block Execution Order
4. JVM Class Loading Process
5. Static Nested Class
6. Static Import
7. Initialization Order
8. Memory Diagram
9. Beginner Examples
10. Real-World Example
11. Common Mistakes
12. Best Practices

---

# 📖 What is a Static Block?

A **static block** is a block of code that executes **only once** when the class is loaded into memory.

It is mainly used to initialize static variables or perform one-time setup operations.

Syntax

```java
class Student{

    static{

        System.out.println("Static Block Executed");

    }

}
```

---

# 🤔 Why Do We Need Static Blocks?

Suppose your application needs to:

- Load configuration files
- Read environment variables
- Create database drivers
- Initialize loggers
- Load application settings

These tasks should execute **only once**, not every time an object is created.

Static blocks are designed for this purpose.

---

# 💻 Example

```java
class Student{

    static{

        System.out.println("Class Loaded");

    }

    Student(){

        System.out.println("Constructor");

    }

}

public class Main{

    public static void main(String[] args){

        Student s1 = new Student();

        Student s2 = new Student();

    }

}
```

Output

```
Class Loaded

Constructor

Constructor
```

Notice:

The static block executes **only once**, while the constructor executes for every object.

---

# 📖 Multiple Static Blocks

A class can contain multiple static blocks.

Example

```java
class Demo{

    static{

        System.out.println("First");

    }

    static{

        System.out.println("Second");

    }

}
```

Output

```
First

Second
```

Static blocks execute **from top to bottom**.

---

# 🧠 JVM Internal Working

```text
Program Starts

        │

        ▼

Class Loader

        │

        ▼

Load Class

        │

        ▼

Initialize Static Variables

        │

        ▼

Execute Static Blocks

        │

        ▼

main()

        │

        ▼

Objects Created
```

The JVM performs static initialization **before** executing the `main()` method.

---

# 📖 Static Nested Class

A nested class can also be declared static.

Example

```java
class Outer{

    static class Inner{

        void display(){

            System.out.println("Inner Class");

        }

    }

}
```

Object Creation

```java
Outer.Inner obj = new Outer.Inner();

obj.display();
```

Output

```
Inner Class
```

---

# 🤔 Why Static Nested Classes?

Normally, an inner class requires an object of the outer class.

```java
Outer outer = new Outer();

Outer.Inner obj = outer.new Inner();
```

A static nested class **does not require** an outer object.

This saves memory when the inner class doesn't depend on the outer class.

---

# 📖 Static Import

Normally

```java
System.out.println(Math.sqrt(25));
```

Using Static Import

```java
import static java.lang.Math.*;

public class Main{

    public static void main(String[] args){

        System.out.println(sqrt(25));

    }

}
```

Output

```
5.0
```

---

# 📦 Memory Diagram

```text
Method Area

+------------------------+

Student.class

college

Static Block

Static Methods

+------------------------+

             │

             ▼

Heap Memory

+----------------------+

Student Object

name

id

+----------------------+
```

The static block and static variables are stored in the class metadata, while object fields are stored in heap memory.

---

# 📖 Initialization Order

Suppose

```java
class Student{

    static{

        System.out.println("Static Block");

    }

    Student(){

        System.out.println("Constructor");

    }

}
```

Execution

```java
Student s = new Student();
```

Order

```text
Load Class

↓

Static Variables

↓

Static Block

↓

Constructor

↓

Object Ready
```

---

# 📖 Initialization Flow

```text
Program Starts

↓

Class Loaded

↓

Static Variables Initialized

↓

Static Blocks Execute

↓

main() Starts

↓

Object Created

↓

Constructor Executes
```

---

# 🚀 Real-World Example

### Spring Boot Application

When a Spring Boot application starts:

```text
Application Starts

↓

Configuration Classes Loaded

↓

Static Variables Initialized

↓

Static Blocks Execute

↓

Beans Created

↓

Application Ready
```

Static initialization ensures one-time setup before the application begins handling requests.

---

# 🌍 Real-World Applications

Static blocks are commonly used for:

- Loading configuration files
- Initializing JDBC drivers
- Creating logger instances
- Loading environment variables
- Caching frequently used data
- Initializing constants

Static nested classes are used in:

- Builder Pattern
- Helper Classes
- Utility Classes
- Configuration Classes

---

# ⚠️ Common Mistakes

## ❌ Expecting Static Block to Execute for Every Object

Wrong Assumption

```text
Object Created

↓

Static Block
```

Correct

```text
Class Loaded

↓

Static Block

↓

Objects Created
```

---

## ❌ Accessing Instance Variables

Wrong

```java
class Student{

    int id;

    static{

        System.out.println(id);

    }

}
```

Compilation Error.

---

## ❌ Creating Unnecessary Static Blocks

Avoid placing business logic inside static blocks.

Use them only for initialization.

---

## ❌ Overusing Static Import

Wrong

```java
import static java.lang.Math.*;
```

Using too many static imports can reduce code readability.

---

# 💡 Best Practices

- Use static blocks only for one-time initialization.
- Keep static blocks short and simple.
- Avoid expensive operations inside static blocks.
- Use static nested classes when they don't require outer class data.
- Prefer explicit class names over excessive static imports.

---

# 🎯 Interview Tip

### Question

What is the difference between a constructor and a static block?

### Answer

| Constructor | Static Block |
|--------------|--------------|
| Executes when an object is created | Executes when the class is loaded |
| Runs for every object | Runs only once |
| Initializes objects | Initializes class-level resources |
| Uses object state | Uses class-level state |

---

➡️ **Next: Part 3** will cover:

- Static vs Non-static
- Singleton Pattern
- Static Factory Methods
- Interview Questions (Basic → Advanced)
- JVM Memory Model
- Best Practices
- Practice Problems
- Chapter Summary
- Quick Revision Sheet
```
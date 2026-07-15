# 📘 Chapter 14: static Keyword (Part 1)

> *"The `static` keyword belongs to the class rather than any individual object. It allows members to be shared among all objects, reducing memory usage and providing class-level functionality."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what the `static` keyword is.
- Learn why `static` is needed.
- Understand static variables.
- Learn static methods.
- Understand the difference between instance and static members.
- Learn how the JVM loads static members.
- Understand memory allocation for static members.

---

# 📚 Table of Contents

1. Why do we need static?
2. What is static?
3. Static Variable
4. Static Method
5. Instance vs Static Members
6. JVM Memory Allocation
7. Memory Diagram
8. Beginner Examples
9. Real-World Example
10. Common Mistakes
11. Best Practices

---

# 🤔 Why Do We Need static?

Imagine a college has **1000 students**.

Every student object stores:

- Name
- Roll Number
- Branch
- College Name

```text
Student 1

↓

Name

Roll No

Branch

College = AKTU

-----------------------

Student 2

↓

Name

Roll No

Branch

College = AKTU

-----------------------

Student 3

↓

Name

Roll No

Branch

College = AKTU
```

Notice that **College Name is the same for every student.**

Creating a separate copy of the same value for every object wastes memory.

Instead, Java stores one shared copy using the `static` keyword.

---

# 📖 What is static?

The `static` keyword makes a variable, method, block, or nested class belong to the **class instead of individual objects**.

This means:

- Only one copy exists.
- Shared among all objects.
- Loaded when the class is loaded into memory.

---

# 🧠 Key Points

- Belongs to the class.
- Shared by all objects.
- Memory allocated only once.
- Can be accessed without creating an object.
- Loaded before objects are created.

---

# 📖 Static Variable

A **static variable** is shared among all objects of a class.

Example

```java
class Student{

    String name;

    static String college = "AKTU";

}
```

Object Creation

```java
Student s1 = new Student();

Student s2 = new Student();

Student s3 = new Student();
```

Memory

```text
s1

↓

name = Anshika

college ----+

             |

s2           |

↓            |

name = Rahul |

college -----+

             |

s3           |

↓            |

name = Aman  |

college -----+

             |

             ▼

        "AKTU"
```

Only one copy of `college` exists.

---

# 💻 Example

```java
class Student{

    String name;

    static String college = "AKTU";

    Student(String name){

        this.name = name;

    }

    void display(){

        System.out.println(name + " " + college);

    }

}

public class Main{

    public static void main(String[] args){

        Student s1 = new Student("Anshika");

        Student s2 = new Student("Rahul");

        s1.display();

        s2.display();

    }

}
```

Output

```
Anshika AKTU

Rahul AKTU
```

---

# 📖 Static Method

A static method belongs to the class.

It can be called without creating an object.

Example

```java
class Calculator{

    static void message(){

        System.out.println("Welcome");

    }

}
```

Calling

```java
Calculator.message();
```

Output

```
Welcome
```

---

# 🤔 Why Use Static Methods?

Suppose a utility method doesn't depend on object data.

Examples:

- Math calculations
- Unit conversion
- Validation
- Utility methods

Creating objects just to call these methods is unnecessary.

Static methods solve this problem.

---

# 📖 Instance vs Static Members

| Feature | Instance | Static |
|----------|----------|---------|
| Belongs To | Object | Class |
| Memory | Every Object | One Copy |
| Access | Object | Class Name |
| Depends on Object | ✅ | ❌ |
| Shared | ❌ | ✅ |

---

# 🧠 JVM Memory Allocation

When a class is loaded,

the JVM creates an area for static members.

```text
Class Loading

↓

Method Area

↓

Static Variables

↓

Objects Created Later
```

Static members exist even if no object has been created.

---

# 📦 Memory Diagram

```text
Method Area

+----------------------+

Student.class

college = "AKTU"

message()

+----------------------+

            ▲

            │

Heap

+------------------+

Student Object

name = "Anshika"

+------------------+

+------------------+

Student Object

name = "Rahul"

+------------------+
```

Notice:

The static variable is stored only once.

---

# 🚀 Real-World Example

### Banking Application

Every customer has:

- Name
- Account Number
- Balance

But every customer belongs to the same bank.

```text
Bank Name

↓

State Bank of India
```

Instead of storing the bank name in every account object,

make it static.

```java
static String bankName = "SBI";
```

---

# 🌍 Real-World Applications

The `static` keyword is commonly used in:

- Utility Classes
- Math Class (`Math.sqrt()`)
- Collections Utility Methods
- Spring Boot Utility Classes
- Configuration Classes
- Constants
- Singleton Pattern
- Logging Frameworks

---

# ⚠️ Common Mistakes

## ❌ Accessing Instance Variables Directly from Static Methods

Wrong

```java
class Student{

    int id;

    static void show(){

        System.out.println(id);

    }

}
```

Compilation Error

```
Cannot make a static reference to the non-static field.
```

---

## ✅ Correct

```java
class Student{

    int id;

    static void show(){

        Student s = new Student();

        System.out.println(s.id);

    }

}
```

---

## ❌ Calling Non-static Methods Directly

Wrong

```java
static void show(){

    display();

}
```

---

## ❌ Assuming Every Object Gets a Static Copy

Static members belong to the class.

Objects only reference them.

---

# 💡 Best Practices

- Use static variables for shared data.
- Use static methods for utility functions.
- Access static members using the class name.
- Avoid unnecessary static variables.
- Keep static methods independent of object state.

---

# 🎯 Interview Tip

### Question

What is the `static` keyword?

### Answer

The `static` keyword makes a member belong to the class rather than individual objects. Static members are loaded when the class is loaded, shared among all objects, and can be accessed without creating an object.

---

➡️ **Next: Part 2** will cover:

- Static Blocks
- Static Nested Classes
- Static Import
- Static Memory Allocation
- JVM Class Loading Process
- Initialization Order
- Internal Working
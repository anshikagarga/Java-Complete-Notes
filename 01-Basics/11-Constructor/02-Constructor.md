# 📘 Chapter 12: Constructors (Part 2)

## Constructor Overloading, Constructor Chaining & `this()`

> *"A constructor not only initializes an object but can also delegate initialization to other constructors using constructor chaining, reducing code duplication and improving maintainability."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Constructor Overloading.
- Learn Constructor Chaining.
- Understand `this()` constructor calls.
- Learn Copy Constructors.
- Understand Private Constructors.
- Learn Constructor Execution Order.
- Understand constructor execution from the JVM's perspective.

---

# 📚 Table of Contents

1. Constructor Overloading
2. Why Constructor Overloading?
3. Constructor Chaining
4. this()
5. Copy Constructor
6. Private Constructor
7. Constructor Execution Order
8. JVM Internal Working
9. Memory Diagram
10. Beginner Examples
11. Real-World Example
12. Common Mistakes
13. Best Practices

---

# 📖 Constructor Overloading

A class can have **multiple constructors** with different parameter lists.

The compiler identifies which constructor should execute based on the arguments passed during object creation.

---

## Syntax

```java
class Student{

    Student(){

        System.out.println("Default Constructor");

    }

    Student(String name){

        System.out.println(name);

    }

    Student(int age){

        System.out.println(age);

    }

}
```

Object Creation

```java
Student s1 = new Student();

Student s2 = new Student("Anshika");

Student s3 = new Student(22);
```

Output

```
Default Constructor

Anshika

22
```

---

# 🤔 Why Constructor Overloading?

Suppose a student management system allows creating students in different ways.

Sometimes

```text
Only Name
```

Sometimes

```text
Name + Age
```

Sometimes

```text
Name + Age + Course
```

Instead of creating different classes,

we overload constructors.

---

# 📦 Memory Diagram

```text
Student

│

├── Student()

├── Student(String)

├── Student(int)

└── Student(String,int)
```

Compiler chooses the appropriate constructor.

---

# 📖 Constructor Chaining

Constructor Chaining means

**one constructor calls another constructor of the same class.**

Instead of repeating code,

reuse existing constructors.

---

## Example

```java
class Student{

    Student(){

        System.out.println("Default");

    }

    Student(String name){

        this();

        System.out.println(name);

    }

}
```

Object

```java
Student s = new Student("Anshika");
```

Output

```
Default

Anshika
```

---

# 🧠 Internal Working

```text
Student("Anshika")

        │

        ▼

this()

        │

        ▼

Student()

        │

        ▼

Return

        │

        ▼

Execute Remaining Code
```

The constructor called using `this()` executes **first**.

---

# 📖 What is `this()`?

`this()` is used to call **another constructor of the same class**.

Rules

- Must be the **first statement**.
- Only one constructor call is allowed.
- Cannot call itself recursively.

---

## Example

```java
class Employee{

    Employee(){

        System.out.println("Employee Created");

    }

    Employee(String name){

        this();

        System.out.println(name);

    }

}
```

Output

```
Employee Created

Anshika
```

---

# ⚠️ Important Rule

Correct

```java
Employee(String name){

    this();

    System.out.println(name);

}
```

Wrong

```java
Employee(String name){

    System.out.println(name);

    this();

}
```

Compilation Error

```
Constructor call must be the first statement.
```

---

# 📖 Constructor Chaining Example

```java
class Student{

    Student(){

        System.out.println("1");

    }

    Student(int age){

        this();

        System.out.println("2");

    }

    Student(int age,String name){

        this(age);

        System.out.println("3");

    }

}
```

Object

```java
new Student(22,"Anshika");
```

Execution

```text
Student(int,String)

↓

Student(int)

↓

Student()

↓

Return

↓

Print 2

↓

Return

↓

Print 3
```

Output

```
1

2

3
```

---

# 📖 Copy Constructor

Java **does not provide** a built-in copy constructor like C++.

However,

we can create one manually.

Example

```java
class Student{

    String name;

    Student(String name){

        this.name = name;

    }

    Student(Student obj){

        this.name = obj.name;

    }

}
```

Object

```java
Student s1 = new Student("Anshika");

Student s2 = new Student(s1);
```

Both objects now contain the same values.

---

# 📦 Memory Diagram

```text
s1

│

▼

+------------------+

name = "Anshika"

+------------------+

        │

Copy

        ▼

s2

│

▼

+------------------+

name = "Anshika"

+------------------+
```

Both objects are different,

but their data is copied.

---

# 📖 Private Constructor

A constructor can be declared **private**.

Example

```java
class Database{

    private Database(){

    }

}
```

Objects cannot be created outside the class.

---

# 🌍 Real-World Usage

Private constructors are used in

- Singleton Pattern
- Utility Classes
- Factory Pattern
- Database Connections
- Configuration Managers

---

# 🧠 Constructor Execution Order

Consider

```java
Student s = new Student("Anshika");
```

JVM Execution

```text
new Keyword

↓

Memory Allocation

↓

Default Values

↓

Call Constructor

↓

Constructor Body Executes

↓

Object Initialized

↓

Reference Assigned
```

---

# 💻 Beginner Example

```java
class Student{

    Student(){

        System.out.println("Default");

    }

    Student(String name){

        this();

        System.out.println(name);

    }

}
```

Output

```
Default

Anshika
```

---

# 🚀 Real-World Example

Food Delivery App

```text
Create User

        │

        ▼

Initialize User ID

        │

        ▼

Initialize Name

        │

        ▼

Initialize Address

        │

        ▼

Ready to Use
```

Instead of writing initialization repeatedly,

constructor chaining reuses existing constructors.

---

# 🌍 Real-World Applications

Constructor chaining is used in:

- Spring Framework
- Hibernate
- Android Activities
- Banking Applications
- Game Development
- REST APIs
- Enterprise Java Applications

---

# ⚠️ Common Mistakes

## ❌ Calling `this()` Twice

Wrong

```java
this();

this();
```

Only one constructor call is allowed.

---

## ❌ Recursive Constructor Calls

Wrong

```java
Student(){

    this();

}
```

Causes infinite recursion.

---

## ❌ Not Keeping `this()` First

Wrong

```java
System.out.println();

this();
```

Compilation Error.

---

## ❌ Assuming Java Has a Built-in Copy Constructor

Unlike C++,

Java requires developers to implement copy constructors manually.

---

# 💡 Best Practices

- Use constructor overloading for flexible object creation.
- Use constructor chaining to avoid duplicate code.
- Keep constructors lightweight.
- Prefer parameterized constructors for mandatory fields.
- Use private constructors only when object creation must be restricted.

---

# 🎯 Interview Tip

### Question

What is Constructor Chaining?

### Answer

Constructor Chaining is the process where one constructor calls another constructor of the same class using `this()`. It helps reuse initialization logic, reduces duplicate code, and improves maintainability. The `this()` call must always be the first statement inside the constructor.

---

➡️ **Next: Part 3** will cover:

- Constructors vs Methods
- `super()` Constructor Calls
- Constructors in Inheritance
- Constructor Call Order
- Object Creation in Parent & Child Classes
- Interview Questions (Basic → Advanced)
- Practice Problems
- Quick Revision Sheet
- Chapter Summary
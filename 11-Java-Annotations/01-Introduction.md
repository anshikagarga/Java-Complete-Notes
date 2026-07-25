# 📘 Chapter 11: Java Annotations (Part 1)

> *"Annotations provide metadata about Java code. They do not directly affect program execution but are used by the compiler, JVM, and frameworks such as Spring Boot, Hibernate, and JUnit to perform special operations."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Java Annotations
- Learn why annotations are used
- Understand different types of annotations
- Learn built-in annotations
- Understand annotation syntax
- Learn marker, single-value, and normal annotations
- Prepare for Java interview questions

---

# 📚 Table of Contents

1. Introduction to Annotations
2. Why Annotations?
3. Annotation Syntax
4. Types of Annotations
5. Built-in Annotations
6. Marker Annotations
7. Single-Value Annotations
8. Normal Annotations
9. Best Practices
10. Common Mistakes

---

# 📖 What are Annotations?

Annotations are **metadata** that provide additional information about classes, methods, variables, constructors, interfaces, and packages.

Annotations do **not** change the logic of a program directly.

They are mainly used by:

- Compiler
- JVM
- Development Tools
- Frameworks
- Reflection API

---

## Real-Life Analogy

Suppose a file has a sticker saying:

```text
CONFIDENTIAL
```

The sticker doesn't change the file's contents.

It only provides additional information.

Similarly,

Annotations provide information about Java code.

---

# 📖 Why Do We Need Annotations?

Before Java 5,

Developers used configuration files such as XML.

Example

```xml
<bean id="student">
```

Managing XML files became difficult.

Annotations solved this problem.

Example

```java
@Override

public void display(){

}
```

Advantages

- Cleaner Code
- Better Readability
- Less XML Configuration
- Compiler Checking
- Framework Support
- Easier Maintenance

---

# 📖 Annotation Syntax

General Syntax

```java
@AnnotationName
```

Example

```java
@Override

public String toString(){

    return "Student";

}
```

---

# 📖 Where Can We Use Annotations?

Annotations can be applied to

- Classes
- Interfaces
- Methods
- Constructors
- Variables
- Parameters
- Packages
- Local Variables
- Type Uses

Example

```java
class Student{

    @Deprecated

    void show(){

    }

}
```

---

# 📖 Types of Annotations

Java annotations are commonly classified into three categories.

```text
Annotations

│

├── Marker Annotation

├── Single-Value Annotation

└── Normal Annotation
```

---

# 📖 Marker Annotation

A Marker Annotation does not contain any elements (values).

Example

```java
@Override

public String toString(){

    return "Java";

}
```

Another Example

```java
@Deprecated

class Demo{

}
```

Common Marker Annotations

- @Override
- @Deprecated
- @FunctionalInterface

---

# 📖 Single-Value Annotation

Contains only one value.

Example

```java
@SuppressWarnings("unchecked")

public void display(){

}
```

Here

```java
"unchecked"
```

is the single value.

---

Another Example

```java
@SuppressWarnings("deprecation")

public void show(){

}
```

---

# 📖 Normal Annotation

Contains multiple values.

Example

```java
@Author(

name = "Anshika",

version = 1

)
```

A custom annotation with multiple elements is called a normal annotation.

---

# 📖 Built-in Annotations

Java provides several predefined annotations.

Most commonly used:

- @Override
- @Deprecated
- @SuppressWarnings
- @SafeVarargs
- @FunctionalInterface

---

# 📖 @Override

`@Override` tells the compiler that a method is intended to override a parent class method.

Example

```java
class Animal{

    void sound(){

        System.out.println("Animal");

    }

}

class Dog extends Animal{

    @Override

    void sound(){

        System.out.println("Dog");

    }

}
```

Advantages

- Compile-time checking
- Prevents spelling mistakes
- Improves readability

---

# 📖 @Deprecated

Marks a class, method, or field as deprecated.

Deprecated means

> It is still available but should not be used in new code.

Example

```java
class Demo{

    @Deprecated

    void oldMethod(){

    }

}
```

Using this method generates a compiler warning.

---

# 📖 @SuppressWarnings

Suppresses specific compiler warnings.

Example

```java
@SuppressWarnings("unchecked")

public void display(){

}
```

Common Values

```text
unchecked

deprecation

rawtypes

serial
```

Use it only when you understand why the warning is safe to ignore.

---

# 📖 @SafeVarargs

Used to suppress warnings related to generic varargs methods.

Applicable to

- static methods
- final methods
- private methods

Example

```java
@SafeVarargs

static void print(String... names){

    for(String name : names){

        System.out.println(name);

    }

}
```

---

# 📦 Internal Working

```text
Java Source Code

↓

Compiler

↓

Reads Annotations

↓

Performs Validation

↓

Generates Bytecode

↓

JVM

↓

Frameworks / Reflection
```

---

# 💡 Best Practices

- Use annotations only where necessary.
- Always use `@Override` when overriding methods.
- Remove deprecated APIs from new code.
- Avoid excessive use of `@SuppressWarnings`.
- Write meaningful custom annotations.

---

# ⚠️ Common Mistakes

## ❌ Forgetting @Override

Wrong

```java
class Dog extends Animal{

    void sound(){

    }

}
```

Better

```java
class Dog extends Animal{

    @Override

    void sound(){

    }

}
```

---

## ❌ Ignoring Deprecation Warnings

Using deprecated methods without considering alternatives may cause maintenance issues.

---

## ❌ Overusing @SuppressWarnings

Avoid suppressing all warnings unnecessarily.

Wrong

```java
@SuppressWarnings("all")
```

Only suppress the specific warning you understand.

---

# 🎯 Interview Tip

### Question

What are annotations in Java?

### Answer

Annotations are metadata that provide additional information about Java code. They are used by the compiler, JVM, and frameworks for validation, configuration, and runtime processing. They do not directly change the program's business logic.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Meta Annotations
- @Target
- @Retention
- @Inherited
- @Documented
- @Repeatable
- Retention Policies
- ElementType
- Custom Annotation Basics
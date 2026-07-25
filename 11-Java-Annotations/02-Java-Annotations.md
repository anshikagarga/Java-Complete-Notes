# 📘 Chapter 11: Java Annotations (Part 2)

> *"Meta Annotations are annotations that are used to define the behavior of other annotations. They specify where an annotation can be applied, how long it is retained, whether it is inherited, and more."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Meta Annotations
- Learn @Target
- Learn @Retention
- Learn @Inherited
- Learn @Documented
- Learn @Repeatable
- Understand Retention Policies
- Understand ElementType
- Create Custom Annotations

---

# 📚 Table of Contents

1. Meta Annotations
2. @Target
3. ElementType
4. @Retention
5. Retention Policies
6. @Inherited
7. @Documented
8. @Repeatable
9. Custom Annotations
10. Best Practices

---

# 📖 What are Meta Annotations?

Meta Annotations are annotations that are applied **to other annotations**.

They define:

- Where an annotation can be used
- How long it is available
- Whether child classes inherit it
- Whether it appears in JavaDocs

---

## Java Meta Annotations

- @Target
- @Retention
- @Inherited
- @Documented
- @Repeatable

---

# 📖 @Target

`@Target` specifies where an annotation can be applied.

Syntax

```java
@Target(ElementType.METHOD)
```

Example

```java
@Target(ElementType.METHOD)

@interface MyAnnotation{

}
```

Now the annotation can only be used on methods.

Example

```java
class Demo{

    @MyAnnotation

    void display(){

    }

}
```

---

# 📖 ElementType

`ElementType` defines the program element where an annotation can be applied.

Common Element Types

| ElementType | Description |
|-------------|-------------|
| TYPE | Class, Interface, Enum |
| METHOD | Method |
| FIELD | Variable |
| CONSTRUCTOR | Constructor |
| PARAMETER | Method Parameter |
| LOCAL_VARIABLE | Local Variable |
| PACKAGE | Package |
| TYPE_PARAMETER | Generic Type Parameter |
| TYPE_USE | Any Type Usage |

---

## Example

```java
@Target({

ElementType.TYPE,

ElementType.METHOD

})

@interface Test{

}
```

This annotation can be applied to

- Classes
- Methods

---

# 📖 @Retention

`@Retention` specifies how long an annotation is available.

Syntax

```java
@Retention(RetentionPolicy.RUNTIME)
```

---

# 📖 Retention Policies

Java provides three retention policies.

---

## SOURCE

Annotation exists only in source code.

Removed during compilation.

Example

```java
@Retention(RetentionPolicy.SOURCE)
```

Uses

- Compiler checking
- Static analysis

---

## CLASS

Stored inside the `.class` file.

Not available at runtime.

Example

```java
@Retention(RetentionPolicy.CLASS)
```

---

## RUNTIME ⭐

Stored in the class file and available at runtime.

Can be accessed using Reflection.

Example

```java
@Retention(RetentionPolicy.RUNTIME)
```

This is the most commonly used retention policy for frameworks.

---

# 📊 Retention Policy Comparison

| Policy | Source Code | Class File | Runtime |
|----------|------------|------------|----------|
| SOURCE | ✅ | ❌ | ❌ |
| CLASS | ✅ | ✅ | ❌ |
| RUNTIME | ✅ | ✅ | ✅ |

---

# 📖 @Inherited

Allows child classes to inherit an annotation from the parent class.

Example

```java
@Inherited

@interface Author{

}
```

```java
@Author

class Parent{

}

class Child extends Parent{

}
```

The `Child` class also inherits `@Author`.

---

# 📖 @Documented

Specifies that an annotation should appear in generated JavaDocs.

Example

```java
@Documented

@interface Version{

}
```

Without `@Documented`, the annotation is omitted from JavaDoc documentation.

---

# 📖 @Repeatable

Allows the same annotation to be used multiple times on a single declaration.

Example

```java
@Repeatable(Roles.class)

@interface Role{

    String value();

}
```

Usage

```java
@Role("Admin")

@Role("Developer")

class Employee{

}
```

---

# 📖 Creating Custom Annotations

A custom annotation is created using the `@interface` keyword.

Example

```java
@interface Author{

    String name();

}
```

Usage

```java
@Author(

name = "Anshika"

)

class Student{

}
```

---

# 📖 Annotation Elements

Annotations can contain elements.

Example

```java
@interface StudentInfo{

    int id();

    String name();

}
```

Usage

```java
@StudentInfo(

id = 101,

name = "Rahul"

)

class Student{

}
```

---

# 📖 Default Values

Default values can be assigned using the `default` keyword.

Example

```java
@interface Version{

    int number() default 1;

}
```

Usage

```java
@Version

class Demo{

}
```

The default value of `number` is `1`.

---

# 📦 Internal Working

```text
Java Source Code

↓

Compiler

↓

Reads Meta Annotations

↓

Creates Annotation Metadata

↓

Stores in Bytecode

↓

Reflection API

↓

Framework Uses Metadata
```

---

# 💡 Best Practices

- Use `@Target` to restrict where annotations can be applied.
- Use `@Retention(RetentionPolicy.RUNTIME)` when annotations need to be accessed through Reflection.
- Keep custom annotations simple and meaningful.
- Use `@Documented` for public APIs.
- Avoid creating unnecessary custom annotations.

---

# ⚠️ Common Mistakes

## ❌ Forgetting Retention Policy

Wrong

```java
@interface Demo{

}
```

Without `@Retention`, the default policy is `CLASS`, so the annotation is not available at runtime.

Correct

```java
@Retention(

RetentionPolicy.RUNTIME

)

@interface Demo{

}
```

---

## ❌ Wrong ElementType

Wrong

```java
@Target(ElementType.FIELD)
```

Applying the annotation to a method will cause a compile-time error.

---

## ❌ Missing Required Elements

Wrong

```java
@interface Employee{

    int id();

}
```

Usage

```java
@Employee
```

Compilation Error because `id` is required.

Correct

```java
@Employee(id = 1)
```

---

# 🎯 Interview Tip

### Question

What is the difference between `@Target` and `@Retention`?

### Answer

- `@Target` specifies **where** an annotation can be applied (class, method, field, etc.).
- `@Retention` specifies **how long** the annotation is retained (source, class, or runtime).

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Reflection with Annotations
- Annotation Processing
- Real-World Applications
- Spring Boot Annotations Overview
- Interview Questions
- MCQs
- Practice Problems
- Chapter Summary
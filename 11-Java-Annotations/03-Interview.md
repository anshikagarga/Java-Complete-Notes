# 📘 Chapter 11: Java Annotations (Part 3)

> *"Annotations become truly powerful when combined with Reflection and frameworks like Spring Boot, Hibernate, and JUnit. Modern Java applications heavily rely on annotations to reduce boilerplate code and improve readability."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Access Annotations using Reflection
- Understand Annotation Processing
- Learn Real-World Applications
- Understand Spring Boot Annotations
- Prepare for Java Interviews
- Solve MCQs
- Practice Annotation Programs

---

# 📚 Table of Contents

1. Reflection with Annotations
2. Annotation Processing
3. Real-World Applications
4. Spring Boot Annotations Overview
5. Interview Questions
6. MCQs
7. Practice Problems
8. Chapter Summary

---

# 📖 Reflection with Annotations

Reflection allows Java programs to inspect classes, methods, constructors, and annotations during runtime.

Example Annotation

```java
import java.lang.annotation.*;

@Retention(RetentionPolicy.RUNTIME)

@interface Author{

    String name();

}
```

Usage

```java
@Author(name="Anshika")

class Student{

}
```

---

# 📖 Reading Annotation Using Reflection

```java
import java.lang.annotation.*;
import java.lang.reflect.*;

@Retention(RetentionPolicy.RUNTIME)

@interface Author{

    String name();

}

@Author(name="Anshika")

class Student{

}

public class Demo{

    public static void main(String[] args){

        Class<Student> c = Student.class;

        Author a = c.getAnnotation(Author.class);

        System.out.println(a.name());

    }

}
```

Output

```text
Anshika
```

---

# 📖 Reflection on Methods

Example

```java
@Retention(RetentionPolicy.RUNTIME)

@interface Test{

}

class Demo{

    @Test

    void show(){

    }

}
```

Reading Method Annotation

```java
Method m =

Demo.class.getDeclaredMethod(

"show"

);

System.out.println(

m.isAnnotationPresent(Test.class)

);
```

Output

```text
true
```

---

# 📖 Annotation Processing

Annotation Processing is the mechanism where annotations are processed during compilation or runtime.

Types

- Compile-Time Processing
- Runtime Processing

Examples

- Lombok
- MapStruct
- Dagger
- Spring Framework
- Hibernate

---

# 📖 Compile-Time Processing

The compiler processes annotations while compiling Java code.

Examples

- @Override
- @SuppressWarnings

Advantages

- Faster runtime
- Compiler validation
- Code generation

---

# 📖 Runtime Processing

Annotations are processed while the application is running.

Uses Reflection API.

Examples

- Spring Boot
- Hibernate
- JUnit

---

# 📖 Real-World Applications

Annotations are widely used in

- Spring Boot
- Hibernate
- JPA
- JUnit
- Jakarta EE
- Android Development
- REST APIs
- Dependency Injection
- Validation Frameworks
- JSON Serialization Libraries

---

# 📖 Common Spring Boot Annotations

| Annotation | Purpose |
|------------|---------|
| @SpringBootApplication | Main Spring Boot class |
| @Component | Marks a component |
| @Service | Business logic layer |
| @Repository | Database layer |
| @Controller | MVC Controller |
| @RestController | REST API Controller |
| @Autowired | Dependency Injection |
| @Configuration | Configuration class |
| @Bean | Creates Spring Bean |
| @Value | Reads property values |

---

# 📖 Common Hibernate Annotations

| Annotation | Purpose |
|------------|---------|
| @Entity | Marks a class as an entity |
| @Table | Maps class to database table |
| @Id | Primary key |
| @GeneratedValue | Auto-generates IDs |
| @Column | Maps a field to a column |
| @OneToOne | One-to-one relationship |
| @OneToMany | One-to-many relationship |
| @ManyToOne | Many-to-one relationship |

---

# 📖 Common JUnit Annotations

| Annotation | Purpose |
|------------|---------|
| @Test | Test method |
| @BeforeEach | Runs before each test |
| @AfterEach | Runs after each test |
| @BeforeAll | Runs once before all tests |
| @AfterAll | Runs once after all tests |
| @Disabled | Skips a test |

---

# 📦 Internal Working

```text
Java Source Code

↓

Annotations

↓

Compiler

↓

Bytecode

↓

Reflection API

↓

Framework Reads Metadata

↓

Runtime Execution
```

---

# 💡 Best Practices

- Use built-in annotations whenever possible.
- Keep custom annotations simple.
- Always specify an appropriate Retention Policy.
- Avoid unnecessary custom annotations.
- Use meaningful annotation names.
- Document custom annotations clearly.

---

# ⚠️ Common Mistakes

## ❌ Forgetting Runtime Retention

Wrong

```java
@interface Demo{

}
```

Reflection cannot access it.

Correct

```java
@Retention(

RetentionPolicy.RUNTIME

)

@interface Demo{

}
```

---

## ❌ Wrong Target

Wrong

```java
@Target(ElementType.FIELD)
```

Used on a method.

Compilation Error.

---

## ❌ Creating Too Many Custom Annotations

Wrong

```text
One annotation for every small task.
```

Better

```text
Create annotations only when they improve readability and reusability.
```

---

## ❌ Ignoring Existing Built-in Annotations

Instead of creating custom annotations,

prefer using

- @Override
- @Deprecated
- @FunctionalInterface

when appropriate.

---

# 🎤 Interview Questions

## Q1. What are Annotations?

**Answer**

Annotations are metadata that provide additional information about Java code. They are used by the compiler, JVM, Reflection API, and frameworks.

---

## Q2. What are Meta Annotations?

**Answer**

Meta Annotations are annotations applied to other annotations.

Examples

- @Target
- @Retention
- @Inherited
- @Documented
- @Repeatable

---

## Q3. What is the difference between SOURCE, CLASS and RUNTIME retention policies?

| SOURCE | CLASS | RUNTIME |
|---------|--------|----------|
| Removed after compilation | Stored in class file | Available during runtime |
| Reflection ❌ | Reflection ❌ | Reflection ✅ |

---

## Q4. Why is `@Override` useful?

**Answer**

It enables compile-time checking and ensures that a method correctly overrides a superclass method.

---

## Q5. What is Reflection?

**Answer**

Reflection allows Java programs to inspect and manipulate classes, methods, fields, constructors, and annotations during runtime.

---

## Q6. Can we create custom annotations?

**Answer**

Yes.

Custom annotations are created using

```java
@interface
```

---

## Q7. Which Retention Policy is required for Reflection?

**Answer**

```java
RetentionPolicy.RUNTIME
```

---

## Q8. Name some popular frameworks that use annotations.

**Answer**

- Spring Boot
- Hibernate
- JPA
- JUnit
- Jakarta EE

---

## Q9. What is Annotation Processing?

**Answer**

Annotation Processing is the mechanism of reading and processing annotations during compile time or runtime.

---

## Q10. Why are annotations preferred over XML configuration?

**Answer**

Because annotations provide

- Cleaner code
- Better readability
- Less configuration
- Easier maintenance
- Strong compiler support

---

# 🎓 MCQs

### Q1. Which symbol is used for annotations?

- A. #
- B. @ ✅
- C. $
- D. %

---

### Q2. Which keyword is used to create a custom annotation?

- A. annotation
- B. interface
- C. @interface ✅
- D. extends

---

### Q3. Which Retention Policy allows Reflection?

- A. SOURCE
- B. CLASS
- C. RUNTIME ✅
- D. PACKAGE

---

### Q4. Which annotation indicates method overriding?

- A. @Deprecated
- B. @Override ✅
- C. @Target
- D. @Documented

---

### Q5. Which annotation suppresses compiler warnings?

- A. @Deprecated
- B. @SuppressWarnings ✅
- C. @Override
- D. @Inherited

---

### Q6. Which annotation restricts where another annotation can be used?

- A. @Retention
- B. @Target ✅
- C. @Inherited
- D. @Repeatable

---

### Q7. Which API is commonly used to read annotations at runtime?

- A. Streams API
- B. Reflection API ✅
- C. Collections API
- D. Swing API

---

### Q8. Which framework heavily uses annotations?

- A. Spring Boot ✅
- B. AWT
- C. Applet
- D. JavaFX

---

### Q9. Which annotation marks old APIs?

- A. @Deprecated ✅
- B. @SafeVarargs
- C. @Inherited
- D. @Target

---

### Q10. Which annotation defines a Functional Interface?

- A. @FunctionalInterface ✅
- B. @Repeatable
- C. @Documented
- D. @Target

---

# 💻 Practice Problems

## Beginner

1. Use `@Override`.
2. Use `@Deprecated`.
3. Suppress compiler warnings using `@SuppressWarnings`.
4. Create a simple custom annotation.
5. Apply an annotation to a class.

---

## Intermediate

6. Create an annotation with multiple elements.
7. Create an annotation with default values.
8. Use `@Target`.
9. Use `@Retention`.
10. Read annotations using Reflection.

---

## Advanced

11. Build a custom validation annotation.
12. Implement runtime annotation processing.
13. Create a role-based annotation system.
14. Read method annotations dynamically.
15. Build a mini annotation-driven framework.

---

# 📚 References

- Oracle Java Documentation
- OpenJDK Documentation
- Effective Java – Joshua Bloch
- Java: The Complete Reference
- Head First Java

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have successfully completed **11-Java-Annotations.md**

### ✔️ Concepts Covered

- Introduction to Annotations
- Built-in Annotations
- Marker, Single-Value & Normal Annotations
- Meta Annotations
- @Target
- @Retention
- @Inherited
- @Documented
- @Repeatable
- Custom Annotations
- Reflection with Annotations
- Annotation Processing
- Spring Boot Annotations
- Hibernate Annotations
- JUnit Annotations
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Annotations provide metadata and improve code readability.
- ✅ `@Override`, `@Deprecated`, and `@SuppressWarnings` are among the most commonly used built-in annotations.
- ✅ Use `RetentionPolicy.RUNTIME` when annotations need to be accessed through Reflection.
- ✅ Frameworks like Spring Boot, Hibernate, and JUnit rely heavily on annotations.
- ✅ Custom annotations combined with Reflection enable powerful and flexible application designs.

---

# 🚀 Next Chapter

➡️ **12-Java-Generics.md**

### Topics Covered

- Introduction to Generics
- Generic Classes
- Generic Methods
- Generic Interfaces
- Bounded Types
- Wildcards
- Type Erasure
- Best Practices
- Interview Questions
- MCQs
- Practice Problems
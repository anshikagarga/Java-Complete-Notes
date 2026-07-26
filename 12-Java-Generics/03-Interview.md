# 📘 Chapter 12: Java Generics (Part 3)

> *"Generics are extensively used in the Java Collections Framework and modern frameworks like Spring Boot, Hibernate, and Java Streams. They improve type safety, eliminate explicit casting, and make code more reusable."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Generic Collections
- Learn Generics with Arrays
- Understand Restrictions of Generics
- Learn Reflection with Generics
- Explore Real-World Applications
- Prepare for Java Interviews
- Solve MCQs
- Practice Generic Programs

---

# 📚 Table of Contents

1. Generic Collections
2. Generics with Arrays
3. Restrictions of Generics
4. Reflection and Generics
5. Real-World Applications
6. Interview Questions
7. MCQs
8. Practice Problems
9. Chapter Summary

---

# 📖 Generic Collections

The Java Collections Framework heavily uses Generics.

Example

```java
ArrayList<String> names =

new ArrayList<>();

names.add("Anshika");

names.add("Rahul");
```

Without Generics

```java
ArrayList list =

new ArrayList();

list.add("Java");

list.add(100);
```

This allows mixed data types.

With Generics

```java
ArrayList<String> list =

new ArrayList<>();
```

Only `String` objects can be added.

---

# 📖 Common Generic Collections

| Collection | Generic Example |
|------------|-----------------|
| ArrayList | `ArrayList<String>` |
| LinkedList | `LinkedList<Integer>` |
| HashSet | `HashSet<Double>` |
| TreeSet | `TreeSet<String>` |
| HashMap | `HashMap<Integer, String>` |
| PriorityQueue | `PriorityQueue<Integer>` |

---

# 📖 Example

```java
HashMap<Integer, String> students =

new HashMap<>();

students.put(101,"Anshika");

students.put(102,"Rahul");

System.out.println(students);
```

Output

```text
{101=Anshika, 102=Rahul}
```

---

# 📖 Generics with Arrays

Arrays and Generics do not work together directly.

Wrong

```java
T[] arr =

new T[10];
```

Compilation Error

---

Correct Approach

```java
Object[] arr =

new Object[10];
```

or

```java
ArrayList<T> list =

new ArrayList<>();
```

Generics are usually preferred with Collections instead of Arrays.

---

# 📖 Restrictions of Generics

Generics have certain limitations because of **Type Erasure**.

---

## 1. Cannot Create Objects of Type Parameter

Wrong

```java
T obj =

new T();
```

Correct

Pass the object from outside or use Reflection.

---

## 2. Cannot Create Generic Arrays

Wrong

```java
T[] arr =

new T[10];
```

---

## 3. Cannot Use Primitive Data Types

Wrong

```java
ArrayList<int> list;
```

Correct

```java
ArrayList<Integer> list;
```

Generics work only with reference types.

---

## 4. Static Members Cannot Use Type Parameter

Wrong

```java
class Box<T>{

    static T value;

}
```

Compilation Error

Correct

```java
class Box<T>{

    static int count;

}
```

---

## 5. Cannot Throw Generic Exceptions

Wrong

```java
class Demo<T extends Exception>{

    throw new T();

}
```

This is not allowed because of Type Erasure.

---

# 📖 Reflection and Generics

Reflection can inspect generic type information.

Example

```java
import java.lang.reflect.*;

Field field =

Demo.class.getDeclaredField("list");

Type type =

field.getGenericType();

System.out.println(type);
```

Output

```text
java.util.List<java.lang.String>
```

---

# 📖 Real-World Applications

Generics are widely used in

- Java Collections Framework
- Spring Boot
- Hibernate
- JPA
- Stream API
- Optional
- CompletableFuture
- Repository Pattern
- REST APIs
- Enterprise Applications

---

# 📖 Advantages of Generics

- Compile-time Type Checking
- Eliminates Explicit Casting
- Improves Code Reusability
- Better Readability
- Reduces Runtime Errors
- Safer APIs
- Easier Maintenance

---

# 📦 Internal Working

```text
Java Source Code

↓

Compiler

↓

Generic Type Checking

↓

Type Erasure

↓

Bytecode

↓

JVM

↓

Runtime Execution
```

---

# 💡 Best Practices

- Always use Generics with Collections.
- Avoid Raw Types.
- Use Wrapper Classes instead of Primitive Types.
- Use Wildcards for flexible APIs.
- Prefer the Diamond Operator (`<>`).
- Follow the PECS principle:
  - Producer → `extends`
  - Consumer → `super`

---

# ⚠️ Common Mistakes

## ❌ Using Raw Collections

Wrong

```java
ArrayList list =

new ArrayList();
```

Correct

```java
ArrayList<String> list =

new ArrayList<>();
```

---

## ❌ Using Primitive Types

Wrong

```java
List<int> list;
```

Correct

```java
List<Integer> list;
```

---

## ❌ Creating Generic Arrays

Wrong

```java
T[] arr =

new T[10];
```

Correct

```java
List<T> list =

new ArrayList<>();
```

---

## ❌ Ignoring Type Safety

Wrong

```java
List list =

new ArrayList();

list.add(100);

String s =

(String) list.get(0);
```

This may cause a `ClassCastException`.

---

# 🎤 Interview Questions

## Q1. What are Generics?

**Answer**

Generics allow classes, interfaces, and methods to work with different data types while providing compile-time type safety.

---

## Q2. Why are Generics used?

**Answer**

- Type Safety
- Code Reusability
- Eliminates Casting
- Better Readability
- Fewer Runtime Errors

---

## Q3. What is Type Erasure?

**Answer**

Type Erasure is the process where generic type information is removed during compilation.

---

## Q4. What are Raw Types?

**Answer**

Raw Types are generic classes used without specifying a type parameter.

Example

```java
List list =

new ArrayList();
```

---

## Q5. Why can't Generics use primitive data types?

**Answer**

Generics work only with objects. Primitive types are not objects, so Wrapper Classes (`Integer`, `Double`, `Character`, etc.) are used instead.

---

## Q6. What is the Diamond Operator?

**Answer**

The Diamond Operator (`<>`) allows the compiler to infer generic types automatically.

---

## Q7. What is the difference between `extends` and `super` in Generics?

**Answer**

- `extends` → Used for reading (Producer).
- `super` → Used for writing (Consumer).

---

## Q8. Can we create Generic Arrays?

**Answer**

No.

Because of Type Erasure, Java does not allow creating generic arrays directly.

---

## Q9. Which Java packages heavily use Generics?

**Answer**

- `java.util`
- `java.util.stream`
- `java.util.concurrent`

---

## Q10. Name some frameworks that heavily use Generics.

**Answer**

- Spring Boot
- Hibernate
- JPA
- Jackson
- Mockito

---

# 🎓 MCQs

### Q1. Generics were introduced in

- A. Java 1.3
- B. Java 1.4
- C. Java 5 ✅
- D. Java 8

---

### Q2. Which operator is used for Generics?

- A. ()
- B. {}
- C. <> ✅
- D. []

---

### Q3. Which collection declaration is correct?

- A. `ArrayList<int>`
- B. `ArrayList<String>` ✅
- C. `ArrayList<char>`
- D. `ArrayList<boolean>`

---

### Q4. Which process removes generic type information?

- A. Boxing
- B. Type Erasure ✅
- C. Reflection
- D. Serialization

---

### Q5. Which wildcard accepts subclasses?

- A. `<? super T>`
- B. `<? extends T>` ✅
- C. `<?>`
- D. `<T>`

---

### Q6. Which wildcard accepts superclasses?

- A. `<? extends T>`
- B. `<? super T>` ✅
- C. `<?>`
- D. `<T extends Object>`

---

### Q7. Which class cannot be used directly with Generics?

- A. Integer
- B. Double
- C. String
- D. int ✅

---

### Q8. Which feature improves type safety?

- A. Reflection
- B. Generics ✅
- C. Threads
- D. Serialization

---

### Q9. Which operator was introduced in Java 7?

- A. `@`
- B. `::`
- C. `<>` ✅
- D. `->`

---

### Q10. Which principle is associated with Wildcards?

- A. DRY
- B. SOLID
- C. PECS ✅
- D. JVM

---

# 💻 Practice Problems

## Beginner

1. Create a Generic Class.
2. Create a Generic Method.
3. Store different data types using Generics.
4. Create a Generic Interface.
5. Use Generics with `ArrayList`.

---

## Intermediate

6. Implement Upper Bounded Wildcards.
7. Implement Lower Bounded Wildcards.
8. Create a Generic Calculator.
9. Use Generics with `HashMap`.
10. Demonstrate Type Erasure.

---

## Advanced

11. Build a Generic Stack.
12. Build a Generic Queue.
13. Create a Generic Repository.
14. Implement Reflection with Generics.
15. Build a Generic Cache System.

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

You have successfully completed **12-Java-Generics.md**

### ✔️ Concepts Covered

- Introduction to Generics
- Generic Classes
- Generic Methods
- Generic Interfaces
- Generic Inheritance
- Bounded Types
- Multiple Bounds
- Wildcards
- Type Erasure
- Raw Types
- Diamond Operator
- Generic Collections
- Generics with Arrays
- Restrictions of Generics
- Reflection and Generics
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Generics provide compile-time type safety.
- ✅ They eliminate unnecessary type casting.
- ✅ Use Wrapper Classes instead of primitive types.
- ✅ Understand `extends`, `super`, and the PECS principle.
- ✅ Avoid Raw Types and prefer the Diamond Operator (`<>`).
- ✅ Generics are extensively used in the Java Collections Framework and enterprise frameworks like Spring Boot and Hibernate.

---

# 🚀 Next Chapter

➡️ **13-Java-Memory-Management.md**

### Topics Covered

- JVM Memory Structure
- Heap Memory
- Stack Memory
- Method Area
- Program Counter (PC) Register
- Native Method Stack
- String Pool
- Garbage Collection
- Memory Leaks
- References (Strong, Weak, Soft, Phantom)
- Interview Questions
- MCQs
- Practice Problems
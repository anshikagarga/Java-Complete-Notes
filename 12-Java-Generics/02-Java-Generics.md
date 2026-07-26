# 📘 Chapter 12: Java Generics (Part 2)

> *"Generics become truly powerful with bounded types, wildcards, and generic inheritance. These features allow developers to write flexible, reusable, and type-safe code while maintaining compile-time type checking."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Bounded Types
- Learn Multiple Bounds
- Master Wildcards
- Understand Generic Inheritance
- Learn Type Erasure
- Understand Raw Types
- Learn the Diamond Operator
- Prepare for Java Interviews

---

# 📚 Table of Contents

1. Generic Inheritance
2. Bounded Types
3. Multiple Bounds
4. Wildcards
5. Upper Bounded Wildcards
6. Lower Bounded Wildcards
7. Unbounded Wildcards
8. Type Erasure
9. Raw Types
10. Diamond Operator

---

# 📖 Generic Inheritance

Generic classes can participate in inheritance just like normal classes.

Example

```java
class Box<T>{

    T value;

}
```

```java
class NumberBox<T>

extends Box<T>{

}
```

Usage

```java
NumberBox<Integer> box =

new NumberBox<>();

box.value = 100;
```

---

# 📖 Bounded Types

Sometimes we want a generic type to accept only a certain type or its subclasses.

Syntax

```java
<T extends ClassName>
```

Example

```java
class Calculator<T extends Number>{

    T number;

}
```

Valid

```java
Calculator<Integer>

Calculator<Double>

Calculator<Float>
```

Invalid

```java
Calculator<String>
```

Compilation Error because `String` is not a subclass of `Number`.

---

# 📖 Why Use Bounded Types?

Advantages

- Better type safety
- Prevents invalid types
- Allows use of methods from the parent class
- Improves readability

---

# 📖 Example

```java
class Demo<T extends Number>{

    T value;

    void show(){

        System.out.println(

        value.doubleValue()

        );

    }

}
```

Since every subclass of `Number` has `doubleValue()`, the method can be called safely.

---

# 📖 Multiple Bounds

A generic type can have multiple bounds.

Syntax

```java
<T extends ClassA & InterfaceB & InterfaceC>
```

Example

```java
class Demo<T extends Number & Comparable<T>>{

}
```

Rules

- Only one class can be extended.
- It must appear first.
- Multiple interfaces can follow.

---

# 📖 Wildcards

Wildcards make generic methods more flexible.

Symbol

```java
?
```

Example

```java
List<?> list;
```

This list can reference any type.

Examples

```java
List<Integer>

List<String>

List<Double>
```

---

# 📖 Upper Bounded Wildcards

Syntax

```java
<? extends Type>
```

Example

```java
List<? extends Number>
```

Valid

```java
List<Integer>

List<Double>

List<Float>
```

Example

```java
void print(

List<? extends Number> list

){

    for(Number n : list){

        System.out.println(n);

    }

}
```

---

# 📖 Lower Bounded Wildcards

Syntax

```java
<? super Type>
```

Example

```java
List<? super Integer>
```

Valid

```java
List<Integer>

List<Number>

List<Object>
```

Useful when adding elements.

Example

```java
void add(

List<? super Integer> list

){

    list.add(100);

}
```

---

# 📖 Unbounded Wildcards

Syntax

```java
List<?>
```

Used when the exact type is not important.

Example

```java
void display(

List<?> list

){

    for(Object obj : list){

        System.out.println(obj);

    }

}
```

---

# 📊 Wildcards Comparison

| Wildcard | Meaning |
|-----------|---------|
| `<?>` | Any Type |
| `<? extends T>` | T or Subclass |
| `<? super T>` | T or Superclass |

---

# 📖 Type Erasure

Java Generics exist only during compilation.

During runtime,

generic type information is removed.

This process is called **Type Erasure**.

Example

```java
Box<Integer>

↓

Box
```

Purpose

- Backward compatibility
- JVM simplicity
- Compatibility with older Java versions

---

# 📖 Raw Types

A raw type is a generic class used **without specifying a type parameter**.

Example

```java
Box box =

new Box();
```

Problems

- No type safety
- Compiler warnings
- Possible `ClassCastException`

Preferred

```java
Box<String> box =

new Box<>();
```

---

# 📖 Diamond Operator (<>)

Introduced in Java 7.

The compiler automatically infers the generic type.

Before Java 7

```java
ArrayList<String> list =

new ArrayList<String>();
```

Java 7+

```java
ArrayList<String> list =

new ArrayList<>();
```

Advantages

- Cleaner code
- Less repetition
- Better readability

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

JVM Execution
```

---

# 💡 Best Practices

- Always specify generic types.
- Prefer bounded types when appropriate.
- Use wildcards to write flexible APIs.
- Avoid raw types.
- Use the diamond operator (`<>`) to reduce redundancy.
- Prefer compile-time type safety over casting.

---

# ⚠️ Common Mistakes

## ❌ Using Raw Types

Wrong

```java
List list =

new ArrayList();
```

Correct

```java
List<String> list =

new ArrayList<>();
```

---

## ❌ Incorrect Upper Bound

Wrong

```java
class Demo<T extends String>{

}
```

Although syntactically valid, this is rarely useful because `String` is final and cannot be subclassed.

A more practical example is:

```java
class Demo<T extends Number>{

}
```

---

## ❌ Confusing extends and super

Remember

```text
extends → Read Data

super → Write Data
```

A common mnemonic is:

**PECS**

- **Producer → extends**
- **Consumer → super**

---

## ❌ Excessive Casting

Wrong

```java
Object obj =

list.get(0);

String s =

(String)obj;
```

Using proper generic types avoids unnecessary casting.

---

# 🎯 Interview Tip

### Question

What is the difference between `<? extends Number>` and `<? super Integer>`?

### Answer

- `<? extends Number>` accepts `Number` and its subclasses. It is mainly used for **reading** data.
- `<? super Integer>` accepts `Integer` and its superclasses. It is mainly used for **writing** data.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Generic Collections
- Generics with Arrays
- Restrictions of Generics
- Reflection and Generics
- Real-World Applications
- Interview Questions
- MCQs
- Practice Problems
- Chapter Summary
# 📘 Chapter 13: this Keyword (Part 3)

## this vs super, Static Context, Interview Preparation & Best Practices

> *"The `this` keyword always refers to the current object, while `super` refers to the immediate parent object. Understanding the difference is essential for writing clean object-oriented Java programs."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Differentiate between `this` and `super`.
- Understand how `this` behaves in inheritance.
- Learn why `this` cannot be used in static methods.
- Understand JVM handling of `this`.
- Prepare for Java interview questions.
- Revise the complete `this` keyword chapter.

---

# 📚 Table of Contents

1. `this` vs `super`
2. `this` in Inheritance
3. `this` in Static Context
4. Internal Working of `this`
5. Memory Diagram
6. Real-World Example
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

# 📖 this vs super

Both keywords refer to objects, but they point to different objects.

| Feature | `this` | `super` |
|----------|---------|----------|
| Refers To | Current Object | Parent Object |
| Used For | Current class members | Parent class members |
| Calls Constructor | `this()` | `super()` |
| Access Variables | Current Class | Parent Class |
| Access Methods | Current Class | Parent Class |

---

## Example

```java
class Animal{

    String type = "Animal";

}

class Dog extends Animal{

    String type = "Dog";

    void display(){

        System.out.println(this.type);

        System.out.println(super.type);

    }

}
```

Output

```
Dog

Animal
```

---

# 📖 this in Inheritance

The `this` keyword always refers to the **current object**, even when inheritance is involved.

Example

```java
class Animal{

    void sound(){

        System.out.println("Animal Sound");

    }

}

class Dog extends Animal{

    void display(){

        this.sound();

    }

}
```

Output

```
Animal Sound
```

Although the method is inherited, `this` still points to the current `Dog` object.

---

# 🧠 Internal Working

```text
Dog Object

       │

this

       │

Inherited Methods

       │

Current Methods

       ▼

Same Object
```

---

# 📖 this in Static Context

`this` **cannot** be used inside a static method.

Why?

Because static methods belong to the **class**, not to any specific object.

Since no object exists, there is no current object reference.

---

## Wrong Example

```java
class Student{

    static void display(){

        System.out.println(this);

    }

}
```

Compilation Error

```
non-static variable this cannot be referenced from a static context
```

---

## Correct Example

```java
class Student{

    void display(){

        System.out.println(this);

    }

}
```

An object must exist for `this` to refer to it.

---

# 📦 Memory Diagram

Suppose

```java
Student s = new Student();
```

Memory

```text
Stack

s

│

▼

Heap

+------------------------+

Student Object

name = "Anshika"

id = 101

this ─────────────┐

+------------------------+
                  │
                  ▼
           Current Object
```

Whenever a non-static method executes,

`this` automatically points to the current object.

---

# 📖 Internal Working of this

Consider

```java
Student s = new Student();

s.display();
```

JVM View

```text
display(s)

↓

this = s

↓

Current Object

↓

Method Executes
```

Java automatically passes the object's reference as the hidden `this` parameter.

---

# 🚀 Real-World Example

## Builder Pattern

```java
Employee emp = new Employee()

.setName("Anshika")

.setDepartment("Engineering")

.setSalary(80000);
```

Each setter returns

```java
return this;
```

Result

```text
Employee

↓

setName()

↓

setDepartment()

↓

setSalary()

↓

Final Object
```

This creates a clean and readable API.

---

# 🌍 Real-World Applications

The `this` keyword is commonly used in:

- Spring Boot
- Hibernate
- JavaBeans
- Builder Design Pattern
- Fluent APIs
- Android Development
- Desktop Applications
- Enterprise Java Systems

---

# ⚡ Time & Space Complexity

| Operation | Complexity |
|------------|------------|
| Access Instance Variable using `this` | O(1) |
| Method Call using `this` | O(1) |
| Returning `this` | O(1) |
| Passing `this` | O(1) |

The `this` keyword is simply a reference to the current object, so accessing it takes constant time.

---

# ⚠️ Common Mistakes

## ❌ Using `this` in Static Methods

Wrong

```java
static void display(){

    this.show();

}
```

Correct

```java
void display(){

    this.show();

}
```

---

## ❌ Confusing `this` with `super`

Wrong Assumption

```
this → Parent Object
```

Correct

```
this → Current Object

super → Parent Object
```

---

## ❌ Thinking `this` Creates a New Object

`this` never creates an object.

It only refers to an existing object.

---

## ❌ Returning a New Object Instead of `this`

Wrong

```java
return new Student();
```

Correct (for method chaining)

```java
return this;
```

---

# 💡 Best Practices

- Use `this` to resolve variable shadowing.
- Use `this()` for constructor chaining.
- Return `this` for fluent APIs and Builder Pattern.
- Avoid unnecessary use of `this` when there is no ambiguity.
- Never use `this` inside static methods.
- Use meaningful parameter names to improve readability.

---

# 🧩 Interview Questions

## Beginner

1. What is the `this` keyword?
2. Why do we use `this`?
3. What does `this` refer to?
4. Can `this` be used in constructors?
5. Can `this` call another constructor?

---

## Intermediate

6. Difference between `this` and `super`.
7. Explain variable shadowing.
8. Why can't `this` be used in static methods?
9. What is constructor chaining?
10. Explain method chaining.

---

## Advanced

11. How does JVM handle `this` internally?
12. Is `this` passed as a hidden parameter?
13. Explain Builder Pattern using `this`.
14. Can `this` be null?
15. What happens if `this()` is not the first statement?
16. Explain `this` in inheritance.

---

# 📝 Quick Revision

## this Keyword

```text
Current Object

↓

Access Variables

↓

Call Methods

↓

Constructor Chaining

↓

Return Current Object
```

---

## Constructor Chaining

```text
Constructor A

↓

this()

↓

Constructor B

↓

Initialization Complete
```

---

## Method Chaining

```text
obj.display()

↓

returns this

↓

show()

↓

returns this

↓

print()
```

---

## this vs super

```text
Current Object

↓

this

------------------

Parent Object

↓

super
```

---

# 🧪 Practice Problems

### Beginner

- Initialize object fields using `this`.
- Resolve variable shadowing.
- Call one method using `this`.

---

### Intermediate

- Implement constructor chaining using `this()`.
- Pass the current object to another method.
- Return the current object for method chaining.

---

### Advanced

- Build a Student Management System using `this`.
- Create a Builder Pattern implementation.
- Compare `this` and `super` in inheritance.
- Explain the JVM execution flow of `this`.

---

# 🔗 Related Topics

- Constructors
- `super` Keyword
- Inheritance
- Encapsulation
- Method Overloading
- Builder Design Pattern
- JVM Memory Model
- Object-Oriented Programming (OOP)

---

# 📚 References

- Oracle Java Documentation
- Java Language Specification (JLS)
- Effective Java – Joshua Bloch
- Head First Java

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 13: this Keyword**.

### ✔️ Concepts Covered

- What is `this`?
- Current Object Reference
- Variable Shadowing
- Accessing Instance Variables
- Calling Methods using `this`
- Constructor Chaining using `this()`
- Passing Current Object
- Returning Current Object
- Method Chaining
- `this` vs `super`
- `this` in Inheritance
- `this` in Static Context
- JVM Internal Working
- Best Practices
- Interview Questions

---

# 📌 Key Takeaways

- ✅ `this` always refers to the **current object**.
- ✅ It resolves conflicts between instance variables and local variables.
- ✅ `this()` is used for **constructor chaining** within the same class.
- ✅ `this` can invoke methods, pass the current object, and return the current object.
- ✅ Returning `this` enables **method chaining** and the **Builder Pattern**.
- ✅ `this` cannot be used in a **static context** because static methods belong to the class, not an object.
- ✅ `super` refers to the **parent object**, while `this` refers to the **current object**.
- ✅ Understanding `this` is essential for writing clean, maintainable, object-oriented Java code.

---

# 🚀 Next Chapter

➡️ **14-static-Keyword.md**

### Topics Covered

- What is the `static` Keyword?
- Static Variables
- Static Methods
- Static Blocks
- Static Nested Classes
- Static Import
- Memory Allocation
- JVM Loading Process
- Best Practices
- Interview Questions
- Practice Problems
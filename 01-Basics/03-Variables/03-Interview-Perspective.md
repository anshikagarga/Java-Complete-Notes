---

# 🎯 Interviewer's Perspective

Variables are one of the first topics interviewers ask because they reveal whether you truly understand Java fundamentals.

Interviewers usually test:

- Variable declaration
- Initialization
- Scope
- Lifetime
- Heap vs Stack
- Static vs Instance variables
- `final` keyword
- Variable shadowing

If you understand variables well, learning OOP becomes much easier.

---

# 🧩 Interview Questions

## 🟢 Basic Level

### 1. What is a variable?

**Answer**

A variable is a named memory location used to store data that can change during program execution.

---

### 2. Why do we use variables?

To store data so that it can be reused and modified during execution.

---

### 3. What are the different types of variables in Java?

- Local Variable
- Instance Variable
- Static Variable

---

### 4. Where are local variables stored?

Inside **Stack Memory**.

---

### 5. Where are instance variables stored?

Inside **Heap Memory** as part of an object.

---

### 6. Where are static variables stored?

Inside the **Method Area** (or Metaspace in modern JVM implementations).

---

### 7. What is variable initialization?

Assigning the first value to a variable.

Example

```java
int age = 21;
```

---

### 8. Can we use an uninitialized local variable?

No.

```java
int x;

System.out.println(x);
```

Compilation Error.

---

### 9. Do instance variables get default values?

Yes.

Example

```java
int age;
```

Default value

```
0
```

---

### 10. Is Java case-sensitive?

Yes.

```java
age

Age
```

These are two different variables.

---

# 🟡 Intermediate Level

### 11. Explain the difference between declaration and initialization.

Declaration

```java
int age;
```

Initialization

```java
age = 21;
```

---

### 12. Explain variable scope.

Scope determines where a variable can be accessed.

---

### 13. Explain variable lifetime.

- Local → Until method ends.
- Instance → Until object is destroyed.
- Static → Until JVM shuts down.

---

### 14. Can two variables have the same name?

Yes, if they belong to different scopes.

Example

```java
class Student{

    int age = 20;

    void display(){

        int age = 30;

    }

}
```

---

### 15. What is variable shadowing?

A local variable hides an instance variable with the same name.

Access the instance variable using:

```java
this.age
```

---

### 16. Why should variables have meaningful names?

Improves:

- Readability
- Maintainability
- Collaboration

---

### 17. What is the purpose of `final` variables?

They cannot be reassigned after initialization.

---

### 18. What is `var`?

Introduced in Java 10.

Allows local variable type inference.

Example

```java
var name = "Anshika";
```

---

### 19. Can `var` be used for instance variables?

No.

Only local variables.

---

### 20. Can variable names contain numbers?

Yes.

Example

```java
student1
```

Invalid

```java
1student
```

---

# 🔴 Advanced Level

### 21. Explain Heap vs Stack using variables.

Stack stores:

- Local variables
- References

Heap stores:

- Objects
- Instance variables

---

### 22. Why don't local variables receive default values?

Because Java forces developers to initialize them, preventing unpredictable behavior.

---

### 23. What happens to a local variable after a method returns?

It is removed from Stack Memory.

---

### 24. What happens to instance variables after an object becomes unreachable?

They become eligible for Garbage Collection.

---

### 25. Why should static variables be used carefully?

Because all objects share the same copy.

Incorrect usage can lead to unexpected behavior.

---

### 26. Can two objects have different values for static variables?

No.

Static variables belong to the class.

---

### 27. Can local variables be static?

No.

---

### 28. Can instance variables be final?

Yes.

---

### 29. Explain default values in Java.

Only instance and static variables receive default values.

Local variables do not.

---

### 30. Explain the complete lifecycle of a variable.

```
Declaration

↓

Initialization

↓

Usage

↓

Modification

↓

Scope Ends

↓

Destroyed
```

---

# 💼 Industry Insight

Large enterprise applications may contain **thousands of variables**.

Poor naming leads to:

- Bugs
- Difficult debugging
- Poor readability
- Higher maintenance costs

This is why companies enforce coding standards.

---

# 🎯 Interview Tip

Instead of saying:

> Variables store data.

Say:

> Variables are named memory locations that allow programs to store, retrieve, and manipulate data during execution while maintaining type safety.

This sounds much more professional.

---

# 🧪 Practice Problems

## Beginner

### 1.

Declare variables of all primitive data types.

---

### 2.

Store your:

- Name
- Age
- CGPA
- IsPlaced

inside variables.

---

### 3.

Swap two numbers using a temporary variable.

---

### 4.

Print the value of every variable.

---

## Intermediate

### 5.

Create a Student class containing:

- Name
- Age
- College

Make College static.

---

### 6.

Create two Student objects.

Observe:

- Name changes
- College remains shared

---

### 7.

Create a program using:

- Local Variable
- Instance Variable
- Static Variable

---

## Advanced

### 8.

Explain memory allocation for:

```java
Student s = new Student();
```

using a Heap and Stack diagram.

---

### 9.

Predict the output.

```java
class Test{

    int x = 10;

    void show(){

        int x = 20;

        System.out.println(x);

    }

}
```

---

### 10.

Rewrite the program using:

```java
this.x
```

---

# 📝 Quick Revision

```
Variable

↓

Stores Data

-----------------------

Types

↓

Local

Instance

Static

-----------------------

Memory

↓

Local

↓

Stack

-----------------------

Instance

↓

Heap

-----------------------

Static

↓

Method Area

-----------------------

Default Values

↓

Instance

↓

Yes

-----------------------

Local

↓

No
```

---

# 📌 Cheat Sheet

| Topic | Remember |
|--------|----------|
| Local Variable | Stack Memory |
| Instance Variable | Heap Memory |
| Static Variable | Method Area |
| Local Variable | No Default Value |
| Instance Variable | Default Value |
| Static Variable | Shared Across Objects |
| final Variable | Cannot be Reassigned |
| var | Java 10+, Local Only |

---

# 📚 References

### Official Documentation

- Oracle Java Documentation
- OpenJDK Documentation
- Java Language Specification (JLS)

### Books

- Effective Java — Joshua Bloch
- Head First Java
- Core Java Volume I

---

# 🔗 Related Topics

⬅ Previous

**02-JVM-JRE-JDK.md**

➡ Next

**04-Data-Types.md**

Variables define **where** data is stored.

The next chapter explains **what kind of data** can be stored.

---

# 🎉 Chapter Summary

Congratulations!

You now understand:

- ✅ What variables are
- ✅ Why variables are needed
- ✅ Types of variables
- ✅ Scope and lifetime
- ✅ Heap vs Stack
- ✅ `final` variables
- ✅ `var` keyword
- ✅ Naming conventions
- ✅ Common mistakes
- ✅ Best practices
- ✅ Interview questions
- ✅ Practice exercises

You are now ready to learn **Java Data Types**, where you'll explore how different kinds of data are represented and stored in memory.
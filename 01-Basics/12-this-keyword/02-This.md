# 📘 Chapter 13: this Keyword (Part 2)

## Calling Methods, Constructor Chaining, Passing Current Object & Method Chaining

> *"The `this` keyword is more than just a way to resolve variable shadowing. It can call constructors, invoke methods, pass the current object as an argument, and even enable method chaining."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Call current class methods using `this`.
- Understand constructor chaining using `this()`.
- Pass the current object as a method argument.
- Pass the current object to another constructor.
- Return the current object.
- Understand method chaining.
- Learn the JVM's internal working of `this`.

---

# 📚 Table of Contents

1. Calling Current Class Methods
2. Why use `this.method()`?
3. Constructor Chaining using `this()`
4. Passing Current Object as a Method Argument
5. Passing Current Object to a Constructor
6. Returning Current Object
7. Method Chaining
8. JVM Internal Working
9. Memory Diagram
10. Beginner Examples
11. Real-World Example
12. Common Mistakes
13. Best Practices

---

# 📖 Calling Current Class Methods

The `this` keyword can be used to invoke another method of the same class.

Although Java automatically calls the current object's methods, using `this` makes the code more readable.

---

## Example

```java
class Student{

    void display(){

        System.out.println("Display Method");

    }

    void show(){

        this.display();

    }

}
```

Output

```
Display Method
```

---

# 🧠 Internal Working

```text
show()

    │

    ▼

this.display()

    │

    ▼

Current Object

    │

    ▼

display()
```

The JVM executes the `display()` method on the current object.

---

# 📖 Why use `this.method()`?

Both statements are valid.

```java
display();
```

and

```java
this.display();
```

However,

using `this.display()` makes it clear that the method belongs to the current object.

---

# 📖 Constructor Chaining using `this()`

A constructor can call another constructor in the same class using `this()`.

This avoids duplicate initialization code.

---

## Example

```java
class Student{

    Student(){

        System.out.println("Default Constructor");

    }

    Student(String name){

        this();

        System.out.println(name);

    }

}
```

Object Creation

```java
Student s = new Student("Anshika");
```

Output

```
Default Constructor

Anshika
```

---

# ⚠️ Rules of `this()`

- Must be the first statement inside a constructor.
- Only one constructor call is allowed.
- Cannot call itself recursively.

Correct

```java
Student(){

    this(101);

}
```

Wrong

```java
Student(){

    System.out.println("Hello");

    this(101);

}
```

Compilation Error

```
Constructor call must be the first statement.
```

---

# 📖 Passing Current Object as a Method Argument

The current object can be passed to another method using `this`.

Example

```java
class Student{

    void display(Student obj){

        System.out.println("Student Passed");

    }

    void show(){

        display(this);

    }

}
```

Output

```
Student Passed
```

---

# 🧠 Memory Diagram

```text
Current Object

↓

this

↓

display(this)

↓

Method Receives

↓

Same Object
```

No new object is created.

Only the reference is passed.

---

# 📖 Passing Current Object to a Constructor

We can also pass the current object to another constructor.

Example

```java
class Student{

    Student(){

        Test t = new Test(this);

    }

}

class Test{

    Test(Student s){

        System.out.println("Object Received");

    }

}
```

Output

```
Object Received
```

---

# 📖 Returning Current Object

A method can return the current object using `this`.

Example

```java
class Student{

    Student getObject(){

        return this;

    }

}
```

Output

```
Returns Current Object
```

---

# 📖 Method Chaining

Method chaining means calling multiple methods in a single statement.

Example

```java
class Student{

    Student display(){

        System.out.println("Display");

        return this;

    }

    Student show(){

        System.out.println("Show");

        return this;

    }

}
```

Object

```java
Student s = new Student();

s.display().show();
```

Output

```
Display

Show
```

---

# 🧠 Internal Working

```text
Student Object

      │

display()

      │

returns this

      │

show()

      │

returns this

      ▼

Finished
```

---

# 🚀 Real-World Example

### Builder Pattern

```java
User user = new User()

.setName("Anshika")

.setAge(22)

.setCity("Noida");
```

Each setter returns the current object.

This allows multiple method calls in a single statement.

---

# 🌍 Real-World Applications

The `this` keyword is widely used in:

- Builder Design Pattern
- Spring Boot
- Hibernate
- Lombok
- JavaBeans
- REST APIs
- Android Development
- Enterprise Applications

---

# ⚠️ Common Mistakes

## ❌ Calling `this()` from a Method

Wrong

```java
void display(){

    this();

}
```

Compilation Error.

`this()` can only be used inside constructors.

---

## ❌ Recursive Constructor Calls

Wrong

```java
Student(){

    this();

}
```

This causes infinite recursion.

---

## ❌ Returning New Objects Instead of Current Object

Wrong

```java
return new Student();
```

If method chaining is intended, return

```java
return this;
```

---

## ❌ Assuming `this` Creates a New Object

`this` only refers to the current object.

It never creates a new object.

---

# 💡 Best Practices

- Use `this()` to reuse constructor code.
- Return `this` when implementing fluent APIs.
- Pass `this` only when another object genuinely requires the current object.
- Avoid unnecessary use of `this.method()` when there is no ambiguity.
- Keep constructor chaining simple and readable.

---

# 🎯 Interview Tip

### Question

What is method chaining in Java?

### Answer

Method chaining is a technique where multiple methods are called in a single statement by returning the current object (`this`) from each method. It improves readability and is commonly used in the Builder Design Pattern and fluent APIs.

---

➡️ **Next: Part 3** will cover:

- `this` vs `super`
- `this` in Inheritance
- `this` in Static Context
- `this` vs Local Variables
- Interview Questions (Basic → Advanced)
- Quick Revision
- Practice Problems
- Chapter Summary
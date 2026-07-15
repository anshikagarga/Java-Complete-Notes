# 📘 Chapter 12: Constructors (Part 3)

## Constructors vs Methods, super(), Inheritance & Interview Preparation

> *"Constructors play a crucial role in object-oriented programming by ensuring that every object is properly initialized before it is used. Understanding how constructors behave during inheritance is essential for mastering Java."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Differentiate between Constructors and Methods.
- Understand constructor execution in inheritance.
- Learn the `super()` constructor call.
- Understand constructor call order.
- Learn constructor behavior in parent-child relationships.
- Prepare for Java interview questions.
- Revise the complete Constructors chapter.

---

# 📚 Table of Contents

1. Constructors vs Methods
2. Constructors in Inheritance
3. super() Constructor
4. Constructor Execution Order
5. JVM Internal Working
6. Memory Diagram
7. Real-World Example
8. Time & Space Complexity
9. Common Mistakes
10. Best Practices
11. Interview Questions
12. Quick Revision
13. Practice Problems
14. Related Topics
15. References
16. Chapter Summary

---

# 📖 Constructor vs Method

Although constructors look similar to methods, they serve completely different purposes.

| Feature | Constructor | Method |
|----------|------------|---------|
| Purpose | Initialize an object | Perform operations |
| Name | Same as class | Any valid identifier |
| Return Type | No return type | Must have a return type or `void` |
| Invocation | Automatically called | Called explicitly |
| Can be Overloaded | ✅ Yes | ✅ Yes |
| Can be Overridden | ❌ No | ✅ Yes |
| Inherited | ❌ No | ✅ Yes |

---

## Example

```java
class Student{

    Student(){

        System.out.println("Constructor");

    }

    void display(){

        System.out.println("Method");

    }

}
```

Object Creation

```java
Student s = new Student();

s.display();
```

Output

```
Constructor

Method
```

Notice that the constructor executes automatically, while the method requires an explicit call.

---

# 📖 Constructors in Inheritance

Whenever a child object is created,

the **parent constructor executes first**.

Example

```java
class Animal{

    Animal(){

        System.out.println("Animal Constructor");

    }

}

class Dog extends Animal{

    Dog(){

        System.out.println("Dog Constructor");

    }

}
```

Object

```java
Dog d = new Dog();
```

Output

```
Animal Constructor

Dog Constructor
```

---

# 🤔 Why Does Parent Constructor Execute First?

The child class inherits properties and behavior from its parent.

Before initializing the child,

Java ensures that the parent object is initialized.

This guarantees a valid inheritance hierarchy.

---

# 📖 What is `super()`?

`super()` is used to call the constructor of the parent class.

Java inserts

```java
super();
```

automatically if we don't write it.

---

## Example

```java
class Animal{

    Animal(){

        System.out.println("Animal");

    }

}

class Dog extends Animal{

    Dog(){

        super();

        System.out.println("Dog");

    }

}
```

Output

```
Animal

Dog
```

---

# 📦 Internal Working

```text
new Dog()

        │

        ▼

Memory Allocation

        │

        ▼

Dog Constructor

        │

        ▼

super()

        │

        ▼

Animal Constructor

        │

        ▼

Return

        │

        ▼

Dog Constructor Continues

        │

        ▼

Object Ready
```

---

# 📖 Parameterized Parent Constructor

```java
class Animal{

    Animal(String type){

        System.out.println(type);

    }

}

class Dog extends Animal{

    Dog(){

        super("Mammal");

    }

}
```

Output

```
Mammal
```

---

# 📖 Constructor Execution Order

Suppose

```java
class A{

    A(){

        System.out.println("A");

    }

}

class B extends A{

    B(){

        System.out.println("B");

    }

}

class C extends B{

    C(){

        System.out.println("C");

    }

}
```

Object

```java
new C();
```

Execution

```text
C()

↓

super()

↓

B()

↓

super()

↓

A()

↓

Return

↓

Print B

↓

Return

↓

Print C
```

Output

```
A

B

C
```

---

# 📦 Memory Diagram

```text
Stack

obj

│

▼

Heap

+-----------------------+

Parent Variables

Child Variables

+-----------------------+

↓

Parent Constructor

↓

Child Constructor

↓

Object Ready
```

---

# 🧠 JVM Perspective

Object creation involves multiple stages.

```text
new Keyword

↓

Heap Memory Allocated

↓

Fields Get Default Values

↓

Parent Constructor Executes

↓

Child Constructor Executes

↓

Reference Returned

↓

Object Ready
```

The JVM ensures constructors execute from the **top of the inheritance hierarchy to the bottom**.

---

# 🚀 Real-World Example

### Vehicle Management System

```text
Vehicle

↓

Car

↓

ElectricCar
```

When an ElectricCar object is created:

```text
Vehicle Constructor

↓

Car Constructor

↓

ElectricCar Constructor
```

Each constructor initializes its own part of the object.

---

# 🌍 Real-World Applications

Constructors are widely used in:

- Spring Boot Dependency Injection
- Hibernate Entity Initialization
- Android Activities
- JavaFX Applications
- Banking Systems
- Inventory Management
- REST APIs
- Enterprise Software

---

# ⚡ Time & Space Complexity

| Operation | Complexity |
|------------|------------|
| Constructor Call | O(1) |
| Constructor Chaining | O(n) *(n = inheritance depth)* |
| Object Initialization | O(number of fields) |

---

# ⚠️ Common Mistakes

## ❌ Calling Constructor Like a Method

Wrong

```java
Student();

```

Constructors are invoked only using `new`.

---

## ❌ Forgetting Parent Constructor

If the parent class doesn't have a default constructor,

you must explicitly call it.

Wrong

```java
class Parent{

    Parent(int x){}

}

class Child extends Parent{

    Child(){

    }

}
```

Compilation Error.

Correct

```java
Child(){

    super(10);

}
```

---

## ❌ Thinking Constructors are Inherited

Constructors are **never inherited**.

Only methods and fields participate in inheritance.

---

## ❌ Adding Return Type

Wrong

```java
void Student(){

}
```

This is a method, not a constructor.

---

# 💡 Best Practices

- Keep constructors focused on object initialization.
- Avoid complex business logic inside constructors.
- Use constructor chaining to eliminate duplicate code.
- Use `super()` whenever the parent requires initialization.
- Prefer immutable initialization where possible.
- Validate constructor parameters before assigning them.

---

# 🧩 Interview Questions

## Beginner

1. What is a constructor?
2. Why do constructors not have a return type?
3. Difference between constructor and method?
4. What is a default constructor?
5. What is a parameterized constructor?

---

## Intermediate

6. What is constructor overloading?
7. Explain constructor chaining.
8. What is `this()`?
9. What is `super()`?
10. Why must `super()` be the first statement?

---

## Advanced

11. Can constructors be inherited?
12. Can constructors be overridden?
13. Does Java support copy constructors?
14. What happens if the parent class has no default constructor?
15. Explain constructor execution from the JVM perspective.
16. Explain constructor call order in multi-level inheritance.

---

# 📝 Quick Revision

## Constructor

```text
Object Creation

↓

Memory Allocation

↓

Default Values

↓

Constructor Executes

↓

Object Ready
```

---

## Constructor Chaining

```text
this()

↓

Another Constructor

↓

Initialization
```

---

## Inheritance

```text
Child Object

↓

super()

↓

Parent Constructor

↓

Child Constructor
```

---

## Object Creation Flow

```text
new

↓

Heap Memory

↓

Parent Constructor

↓

Child Constructor

↓

Reference Assigned
```

---

# 🧪 Practice Problems

### Beginner

- Create a class with a default constructor.
- Create a parameterized constructor.
- Demonstrate constructor overloading.
- Initialize object fields using constructors.

---

### Intermediate

- Implement constructor chaining using `this()`.
- Create a copy constructor manually.
- Demonstrate private constructors.
- Create a class hierarchy using `super()`.

---

### Advanced

- Build a Student Management System using constructors.
- Implement a Bank Account class with constructor validation.
- Create a Singleton class using a private constructor.
- Trace constructor execution in a three-level inheritance hierarchy.

---

# 🔗 Related Topics

- Classes & Objects
- Methods
- `this` Keyword
- `static` Keyword
- Encapsulation
- Inheritance
- Polymorphism
- Object Memory
- JVM
- Garbage Collection

---

# 📚 References

- Oracle Java Documentation
- Java Language Specification (JLS)
- Effective Java – Joshua Bloch
- Head First Java

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 12: Constructors**.

### ✔️ Concepts Covered

- Constructors
- Default Constructor
- Parameterized Constructor
- Constructor Overloading
- Constructor Chaining
- `this()`
- Copy Constructor
- Private Constructor
- Constructors vs Methods
- `super()`
- Constructors in Inheritance
- JVM Object Creation
- Memory Diagrams
- Best Practices
- Interview Questions

---

# 📌 Key Takeaways

- ✅ Constructors initialize objects automatically.
- ✅ Constructor names must exactly match the class name.
- ✅ Constructors have **no return type**.
- ✅ Java provides a default constructor only if no constructor is defined.
- ✅ Constructor overloading allows multiple ways to create objects.
- ✅ `this()` calls another constructor in the **same class**.
- ✅ `super()` calls the **parent class constructor**.
- ✅ Parent constructors always execute before child constructors.
- ✅ Constructors cannot be inherited or overridden.
- ✅ Keeping constructors simple and focused improves code maintainability.

---

# 🚀 Next Chapter

➡️ **12-this-Keyword.md**

### Topics Covered

- What is `this` Keyword?
- Why do we need `this`?
- Instance Variables vs Local Variables
- Using `this` for Variable Shadowing
- Passing Current Object
- Returning Current Object
- Constructor Chaining with `this()`
- Method Chaining
- Interview Questions
- Practice Problems
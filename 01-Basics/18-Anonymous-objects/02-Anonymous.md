# 📘 Chapter 18: Anonymous Object (Part 2)

## Method Chaining, Garbage Collection & Internal Working

> *"Anonymous Objects are powerful when an object is needed only once. They are commonly used in method chaining, passing temporary objects to methods, and reducing unnecessary reference variables."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Pass Anonymous Objects as method arguments.
- Return Anonymous Objects from methods.
- Understand Method Chaining.
- Learn the relationship between Anonymous Objects and Garbage Collection.
- Identify common mistakes.
- Follow best practices.

---

# 📚 Table of Contents

1. Anonymous Objects as Method Arguments
2. Returning Anonymous Objects
3. Method Chaining
4. Anonymous Objects & Garbage Collection
5. Internal Working
6. Common Mistakes
7. Best Practices

---

# 📖 Anonymous Object as a Method Argument

Instead of creating a reference variable,

```java
Student s = new Student();

display(s);
```

we can directly pass an anonymous object.

```java
display(new Student());
```

---

## Example

```java
class Student{

    String name = "Anshika";

}

public class Demo{

    static void display(Student s){

        System.out.println(s.name);

    }

    public static void main(String[] args){

        display(new Student());

    }

}
```

Output

```text
Anshika
```

---

# 📖 Returning an Anonymous Object

A method can return a newly created object directly.

```java
class Student{

    int rollNo = 101;

}

public class Demo{

    static Student createStudent(){

        return new Student();

    }

    public static void main(String[] args){

        Student s = createStudent();

        System.out.println(s.rollNo);

    }

}
```

Output

```text
101
```

---

# 📖 Method Chaining

Anonymous Objects are often used with method chaining.

## Example

```java
class Calculator{

    Calculator add(){

        System.out.println("Add");

        return this;

    }

    Calculator subtract(){

        System.out.println("Subtract");

        return this;

    }

}
```

Calling

```java
new Calculator()

.add()

.subtract();
```

Output

```text
Add

Subtract
```

---

# 📖 Why Method Chaining Works?

Each method returns

```java
this
```

which represents the current object.

Flow

```text
new Calculator()

↓

add()

↓

Current Object

↓

subtract()

↓

Current Object
```

---

# 📖 Anonymous Object with Constructor

```java
class Employee{

    Employee(){

        System.out.println("Employee Created");

    }

}
```

Calling

```java
new Employee();
```

Output

```text
Employee Created
```

The constructor executes immediately after object creation.

---

# 📖 Multiple Anonymous Objects

```java
new Student().show();

new Student().show();

new Student().show();
```

Output

```text
Show

Show

Show
```

Important

Three **different objects** are created.

---

# 📦 Memory Representation

```text
new Student()

↓

Object 1

----------------

new Student()

↓

Object 2

----------------

new Student()

↓

Object 3
```

Each statement creates a separate object.

---

# 📖 Garbage Collection

Consider

```java
new Student().show();
```

Execution Flow

```text
Create Object

↓

Call show()

↓

Method Ends

↓

Reference Lost

↓

Eligible for Garbage Collection
```

The object is **not destroyed immediately**. It simply becomes **eligible** for garbage collection. The JVM decides **when** to reclaim its memory.

---

# 📖 Internal Working

When Java executes

```java
new Student().show();
```

Internally,

```text
Heap Memory

↓

Create Student Object

↓

Invoke show()

↓

No Reference Exists

↓

Garbage Collector May Remove It Later
```

---

# 📊 Anonymous Object vs Normal Object

| Feature | Anonymous Object | Normal Object |
|----------|------------------|---------------|
| Reference Variable | ❌ No | ✅ Yes |
| Reusable | ❌ No | ✅ Yes |
| Best for | One-time use | Multiple operations |
| Memory | Heap | Heap |
| Eligible for GC | Quickly | When no references remain |

---

# ⚠️ Common Mistakes

## ❌ Expecting Reuse

Wrong

```java
new Student().show();

new Student().print();
```

Many beginners think both methods are called on the same object.

Actually,

two different objects are created.

---

Correct

```java
Student s = new Student();

s.show();

s.print();
```

---

## ❌ Using Anonymous Objects Repeatedly

Wrong

```java
new Student().show();

new Student().show();

new Student().show();
```

This creates three separate objects.

If you need the same object multiple times,

use a reference variable.

---

## ❌ Assuming Object is Destroyed Immediately

Wrong assumption

```text
Method Finished

↓

Object Destroyed
```

Correct

```text
Method Finished

↓

Eligible for Garbage Collection

↓

JVM decides when to remove it
```

---

## ❌ Confusing Anonymous Objects with Anonymous Classes

These are **different concepts**.

Anonymous Object

```java
new Student().show();
```

Anonymous Class

```java
Runnable r = new Runnable(){

    @Override
    public void run(){

        System.out.println("Running");

    }

};
```

An anonymous object is simply an object without a reference. An anonymous class defines a new class without giving it a name.

---

# 💡 Best Practices

- Use anonymous objects only for one-time operations.
- Use reference variables if the object will be reused.
- Avoid creating unnecessary anonymous objects in loops.
- Use method chaining only when it improves readability.
- Do not confuse anonymous objects with anonymous classes.
- Remember that objects become **eligible** for garbage collection; they are not removed instantly.

---

# 🌍 Real-World Applications

Anonymous Objects are used in:

- Logging frameworks
- Builder Pattern
- Fluent APIs
- Utility method calls
- Unit Testing
- Temporary DTO/VO objects
- Framework configuration code

---

# 🎯 Interview Tip

### Question

Which object is created here?

```java
new Student().show();

new Student().show();
```

### Answer

Two different `Student` objects are created. Each `new Student()` expression creates a separate object. Since no reference variable stores them, each object becomes eligible for garbage collection after its corresponding statement completes (provided no other reference exists).

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Anonymous Object vs Anonymous Class
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision
- Chapter Summary
- Frequently Asked Interview Questions
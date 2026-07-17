# 📘 Chapter 18: Anonymous Object (Part 1)

> *"An Anonymous Object is an object that has no reference variable. It is created and used immediately, making the code shorter and reducing unnecessary object references."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what an Anonymous Object is.
- Learn why Anonymous Objects are used.
- Differentiate between normal and anonymous objects.
- Understand memory allocation.
- Learn when to use Anonymous Objects.
- Analyze advantages and limitations.

---

# 📚 Table of Contents

1. What is an Anonymous Object?
2. Why Do We Need It?
3. Normal Object vs Anonymous Object
4. Creating Anonymous Objects
5. Internal Working
6. Memory Representation
7. Advantages
8. Limitations
9. Real-World Applications

---

# 🤔 What is an Anonymous Object?

An **Anonymous Object** is an object that **does not have a reference variable**.

Normally we create an object like this:

```java
Student s = new Student();
```

Here,

- `Student` → Class
- `s` → Reference Variable
- `new Student()` → Object

In an Anonymous Object,

there is **no reference variable**.

```java
new Student();
```

The object is created but no variable stores its reference.

---

# 💡 Why Do We Need Anonymous Objects?

Sometimes we need an object only once.

Creating a reference variable becomes unnecessary.

Instead of

```java
Student s = new Student();

s.show();
```

we can simply write

```java
new Student().show();
```

The object is created,

used once,

and becomes eligible for Garbage Collection.

---

# 📖 Normal Object

```java
class Student{

    void display(){

        System.out.println("Hello");

    }

}
```

```java
Student s = new Student();

s.display();
```

Output

```text
Hello
```

---

# 📖 Anonymous Object

```java
new Student().display();
```

Output

```text
Hello
```

Notice

There is no reference variable.

---

# 📊 Normal Object vs Anonymous Object

| Normal Object | Anonymous Object |
|---------------|------------------|
| Has Reference Variable | No Reference Variable |
| Can be reused | Used only once |
| Easy to access later | Cannot be reused |
| Better for multiple operations | Better for one-time operations |

---

# 💻 Complete Example

```java
class Student{

    void show(){

        System.out.println("Welcome");

    }

}

public class Demo{

    public static void main(String[] args){

        new Student().show();

    }

}
```

Output

```text
Welcome
```

---

# 📖 Anonymous Object with Constructor

```java
class Student{

    Student(){

        System.out.println("Constructor Called");

    }

}
```

```java
new Student();
```

Output

```text
Constructor Called
```

The constructor is executed immediately after object creation.

---

# 📖 Anonymous Object Calling Multiple Methods

```java
class Student{

    void show(){

        System.out.println("Show");

    }

    void print(){

        System.out.println("Print");

    }

}
```

Wrong

```java
new Student().show();

new Student().print();
```

Output

```text
Show

Print
```

Two different objects are created.

---

Correct

```java
Student s = new Student();

s.show();

s.print();
```

Only one object is created.

---

# 📦 Memory Representation

### Normal Object

```text
Student s

↓

Student Object
```

---

### Anonymous Object

```text
new Student()

↓

Student Object

↓

No Reference Variable
```

After execution,

```text
Eligible for Garbage Collection
```

---

# 📖 Internal Working

When Java executes

```java
new Student().show();
```

Internally

```text
Create Object

↓

Call show()

↓

Reference Lost

↓

Garbage Collector Can Remove It
```

---

# ⚡ Time Complexity

| Operation | Complexity |
|-----------|------------|
| Object Creation | O(1) |
| Method Call | O(1) |

---

# ✅ Advantages

- Less code.
- No unnecessary variables.
- Easy for one-time use.
- Cleaner syntax.
- Reduces reference management.

---

# ⚠️ Limitations

- Cannot reuse the object.
- Cannot call multiple methods on the same object efficiently.
- Difficult to debug.
- May create unnecessary objects if overused.

---

# 🌍 Real-World Applications

Anonymous Objects are commonly used in:

- Method chaining
- Testing small programs
- Utility classes
- Temporary calculations
- Framework APIs
- Builder Pattern (internally)
- Fluent APIs

---

# 🎯 Interview Tip

### Question

Is an Anonymous Object stored in memory?

### Answer

Yes. It is created in the **Heap Memory**, just like any other object. The only difference is that **no reference variable points to it**, so after the current statement finishes execution, it becomes eligible for **Garbage Collection** if no other reference exists.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Anonymous Objects with Constructors
- Anonymous Objects as Method Arguments
- Method Chaining
- Garbage Collection
- Common Mistakes
- Best Practices
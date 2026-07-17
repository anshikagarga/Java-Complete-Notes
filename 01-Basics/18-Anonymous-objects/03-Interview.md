# 📘 Chapter 18: Anonymous Object (Part 3)

## Interview Questions, MCQs, Practice Problems & Chapter Summary

> *"Anonymous Objects are objects without reference variables. They are useful for one-time operations, but they should be used carefully to avoid unnecessary object creation."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Differentiate between Anonymous Objects and Anonymous Classes.
- Decide when to use Anonymous Objects.
- Answer interview questions confidently.
- Solve MCQs and coding problems.
- Revise the complete chapter quickly.

---

# 📚 Table of Contents

1. Anonymous Object vs Anonymous Class
2. Advantages
3. Limitations
4. Real-World Applications
5. Common Mistakes
6. Best Practices
7. Interview Questions
8. MCQs
9. Quick Revision
10. Practice Problems
11. Related Topics
12. References
13. Chapter Summary

---

# 📊 Anonymous Object vs Anonymous Class

| Feature | Anonymous Object | Anonymous Class |
|----------|------------------|-----------------|
| Definition | Object without a reference variable | Class without a name |
| Creates New Class | ❌ No | ✅ Yes |
| Creates Object | ✅ Yes | ✅ Yes |
| Reusability | No | No |
| Common Use | One-time method calls | Interface/Abstract Class implementation |
| Memory | Heap | Heap |
| Syntax | `new Student();` | `new Runnable(){...};` |

---

# 📖 Example of Anonymous Object

```java
class Student{

    void display(){

        System.out.println("Hello");

    }

}

public class Demo{

    public static void main(String[] args){

        new Student().display();

    }

}
```

Output

```text
Hello
```

---

# 📖 Example of Anonymous Class

```java
interface Greeting{

    void sayHello();

}

public class Demo{

    public static void main(String[] args){

        Greeting g = new Greeting(){

            @Override
            public void sayHello(){

                System.out.println("Hello");

            }

        };

        g.sayHello();

    }

}
```

Output

```text
Hello
```

---

# 🌍 Real-World Applications

Anonymous Objects are commonly used in:

- One-time method calls
- Temporary calculations
- Builder Pattern
- Fluent APIs
- Logging
- Utility classes
- Unit Testing

---

Anonymous Classes are commonly used in:

- Event Handling
- Threads (`Runnable`)
- Comparator
- Listener Interfaces
- Callback Functions
- Swing Applications
- JavaFX

---

# ✅ Advantages

- Reduces unnecessary variables.
- Cleaner code for one-time use.
- Easy to read for simple operations.
- Avoids clutter in small programs.
- Useful with method chaining.

---

# ⚠️ Limitations

- Cannot reuse the object.
- Not suitable for multiple operations.
- Creates a new object every time.
- Can reduce readability if overused.

---

# ⚠️ Common Mistakes

## ❌ Thinking Multiple Calls Use the Same Object

Wrong

```java
new Student().show();

new Student().print();
```

Each statement creates a **new object**.

---

Correct

```java
Student s = new Student();

s.show();
s.print();
```

---

## ❌ Confusing Anonymous Object with Anonymous Class

Wrong assumption

```text
Anonymous Object = Anonymous Class
```

Correct

```text
Anonymous Object

↓

Unnamed Object

-------------------------

Anonymous Class

↓

Unnamed Class
```

---

## ❌ Creating Anonymous Objects Inside Loops

Wrong

```java
for(int i = 0; i < 1000; i++){

    new Student().show();

}
```

This creates **1000 objects**.

Better

```java
Student s = new Student();

for(int i = 0; i < 1000; i++){

    s.show();

}
```

Only one object is reused.

---

# 💡 Best Practices

- Use anonymous objects only for one-time tasks.
- Reuse objects when multiple method calls are required.
- Avoid unnecessary object creation inside loops.
- Use anonymous classes only when implementing interfaces or abstract classes.
- Prefer readability over reducing a single variable.

---

# 🧩 Interview Questions

## Beginner

1. What is an Anonymous Object?
2. Why do we use Anonymous Objects?
3. Can an Anonymous Object be reused?
4. Where is an Anonymous Object stored?
5. Does an Anonymous Object occupy heap memory?

---

## Intermediate

6. Difference between a normal object and an anonymous object.
7. Difference between an anonymous object and an anonymous class.
8. Can we pass an anonymous object to a method?
9. Can a method return an anonymous object?
10. When does an anonymous object become eligible for Garbage Collection?

---

## Advanced

11. Explain the memory representation of an anonymous object.
12. Why are anonymous objects commonly used with method chaining?
13. How does the JVM handle anonymous objects?
14. What happens if an anonymous object is created inside a loop?
15. When should you avoid using anonymous objects?

---

# 🎓 MCQs

### Q1. An Anonymous Object is

- A. An object with two references
- B. An object without a reference variable ✅
- C. An unnamed class
- D. A primitive value

---

### Q2. Where is an Anonymous Object stored?

- A. Stack
- B. Heap ✅
- C. Method Area
- D. CPU Cache

---

### Q3. Which keyword creates an Anonymous Object?

- A. create
- B. object
- C. new ✅
- D. this

---

### Q4. What happens after the statement finishes executing?

- A. Object is immediately deleted
- B. Object becomes eligible for Garbage Collection ✅
- C. Object moves to the stack
- D. JVM stores it permanently

---

### Q5. Which statement creates two different objects?

```java
new Student().show();
new Student().show();
```

- A. One object
- B. Two objects ✅
- C. Three objects
- D. No object

---

# 📝 Quick Revision

## Anonymous Object

```java
new Student().display();
```

---

## Normal Object

```java
Student s = new Student();

s.display();
```

---

## Anonymous Object Flow

```text
Create Object

↓

Call Method

↓

Reference Lost

↓

Eligible for Garbage Collection
```

---

## Memory Representation

```text
new Student()

↓

Heap Object

↓

No Reference Variable
```

---

## Time Complexity

| Operation | Complexity |
|-----------|------------|
| Object Creation | O(1) |
| Method Call | O(1) |

---

# 🧪 Practice Problems

## Beginner

- Create an anonymous object and call a method.
- Compare anonymous and normal object syntax.
- Create a constructor and invoke it using an anonymous object.

---

## Intermediate

- Pass an anonymous object as a method argument.
- Return an object from a method.
- Demonstrate method chaining using `this`.

---

## Advanced

- Compare memory usage of normal and anonymous objects.
- Implement a Builder Pattern example using method chaining.
- Explain Garbage Collection behavior using anonymous objects.
- Write an example showing why anonymous objects should not be created repeatedly inside loops.

---

# 🔗 Related Topics

- Classes and Objects
- Constructors
- `this` Keyword
- Method Chaining
- Garbage Collection
- Anonymous Classes
- Lambda Expressions
- Functional Interfaces

---

# 📚 References

- Oracle Java Documentation
- Effective Java by Joshua Bloch
- Java: The Complete Reference
- OpenJDK Documentation
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 18: Anonymous Object**.

### ✔️ Concepts Covered

- Anonymous Object
- Normal Object vs Anonymous Object
- Method Chaining
- Passing Anonymous Objects
- Returning Objects
- Garbage Collection
- Internal Working
- Anonymous Object vs Anonymous Class
- Best Practices
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ An **Anonymous Object** is an object **without a reference variable**.
- ✅ It is created using the `new` keyword and is generally used **only once**.
- ✅ It resides in **Heap Memory**, just like any other object.
- ✅ After use, if no reference exists, it becomes **eligible for Garbage Collection**.
- ✅ Every `new` expression creates a **new object**.
- ✅ Anonymous Objects are ideal for **one-time operations**, while normal objects should be used when the object needs to be reused.
- ✅ Do **not confuse Anonymous Objects with Anonymous Classes**—they are different concepts.

---

# 🚀 Next Chapter

➡️ **19-Encapsulation.md**

### Topics Covered

- Introduction to Encapsulation
- Why Encapsulation?
- Types of Encapsulation
- `extends` Keyword
- IS-A Relationship
- Constructor Chaining
- Method Overriding
- `super` Keyword
- Interview Questions
- MCQs
- Practice Problems
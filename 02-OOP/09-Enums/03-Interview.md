# 📘 Chapter 20: Enums (Part 3)

## Enum vs Constants, Interview Questions, MCQs & Chapter Summary

> *"Enums are much more than a collection of constants. They are full-fledged Java classes with a fixed number of predefined instances, making them one of the safest ways to represent constant values."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Enums with constants and classes.
- Decide when to use Enums.
- Answer interview questions confidently.
- Solve MCQs and coding problems.
- Quickly revise the complete chapter.

---

# 📚 Table of Contents

1. Enum vs Constants
2. Enum vs Class
3. Advantages
4. Limitations
5. Real-World Applications
6. Common Mistakes
7. Best Practices
8. Interview Questions
9. MCQs
10. Quick Revision
11. Practice Problems
12. Related Topics
13. References
14. Chapter Summary

---

# 📊 Enum vs Constants (`public static final`)

| Feature | Enum | `public static final` Constants |
|---------|------|----------------------------------|
| Type Safety | ✅ Yes | ❌ No |
| Readability | High | Medium |
| Can Have Methods | ✅ Yes | ❌ No |
| Can Have Constructors | ✅ Yes | ❌ No |
| Can Have Fields | ✅ Yes | ❌ No |
| Fixed Values | ✅ Yes | Depends |
| Used in switch | ✅ Yes | ✅ Yes |
| Extends `Enum` Class | ✅ Yes | ❌ No |

---

# 📊 Enum vs Class

| Feature | Enum | Class |
|---------|------|-------|
| Object Creation | JVM creates fixed instances | Programmer creates objects using `new` |
| Constructors | Allowed (implicitly private) | Any valid access modifier |
| Number of Objects | Fixed | Unlimited |
| Can Extend Class | ❌ No (already extends `Enum`) | ✅ Yes |
| Can Implement Interface | ✅ Yes | ✅ Yes |
| Inheritance | Cannot extend another class | Can extend another class |

---

# 📖 When Should You Use Enums?

Use Enums when the values are **fixed and predefined**.

Examples:

- Days of the Week
- Months
- Payment Status
- Order Status
- User Roles
- Traffic Signals
- Seasons
- HTTP Request Methods (`GET`, `POST`, etc.)

---

# ❌ When Should You Avoid Enums?

Avoid Enums when:

- Values are dynamic.
- Data comes from a database and changes frequently.
- Users can create new values at runtime.

Example:

Product Categories

```text
Electronics
Mobiles
Books
Furniture
```

These may change over time, so an Enum is usually not the right choice.

---

# 🌍 Real-World Applications

Enums are heavily used in:

- Banking Systems
- E-Commerce Applications
- Spring Boot Applications
- REST APIs
- Android Development
- Game Development
- Hospital Management Systems
- Airline Reservation Systems
- Inventory Management
- Workflow Engines

---

# ✅ Advantages

- Type-safe.
- Prevents invalid values.
- Improves readability.
- Easy to maintain.
- Better than integer or String constants.
- Supports methods, fields, and constructors.
- Can implement interfaces.
- Works seamlessly with `switch`.

---

# ⚠️ Limitations

- Cannot create new constants at runtime.
- Cannot extend another class.
- Constructor is implicitly private.
- Not suitable for dynamic values.
- Declaration order affects `ordinal()`.

---

# ⚠️ Common Mistakes

## ❌ Comparing Enum with String

Wrong

```java
if(day == "MONDAY"){

}
```

Correct

```java
if(day == Day.MONDAY){

}
```

---

## ❌ Using `new` Keyword

Wrong

```java
Day d = new Day();
```

Compile-time Error.

---

## ❌ Incorrect Case in `valueOf()`

Wrong

```java
Day.valueOf("monday");
```

Correct

```java
Day.valueOf("MONDAY");
```

---

## ❌ Using `ordinal()` as Database ID

Wrong

```java
int id = Day.MONDAY.ordinal();
```

If the enum declaration order changes, the IDs also change.

Instead, define an explicit field.

---

# 💡 Best Practices

- Use Enums for fixed constants.
- Name Enum constants in **UPPER_CASE**.
- Avoid business logic based on `ordinal()`.
- Store additional data using fields.
- Keep related behavior inside the Enum.
- Prefer Enums over integer or String constants.

---

# 🧩 Interview Questions

## Beginner

1. What is an Enum?
2. Why are Enums used?
3. How do you create an Enum?
4. Can an Enum contain methods?
5. Can an Enum contain variables?

---

## Intermediate

6. Difference between Enum and `public static final` constants.
7. Explain the `values()` method.
8. What is the use of `ordinal()`?
9. What does `valueOf()` do?
10. Why are Enum constructors private?

---

## Advanced

11. Can an Enum extend another class? Why?
12. Can an Enum implement an interface?
13. Explain the internal working of Enums.
14. How are Enum constants stored in memory?
15. Why is `ordinal()` not recommended for business logic?

---

# 🎓 MCQs

### Q1. Enum constants are created by:

- A. Programmer
- B. JVM ✅
- C. Compiler only
- D. Garbage Collector

---

### Q2. Which method returns all enum constants?

- A. `list()`
- B. `values()` ✅
- C. `getAll()`
- D. `fetch()`

---

### Q3. Which method returns the declaration position?

- A. `position()`
- B. `index()`
- C. `ordinal()` ✅
- D. `number()`

---

### Q4. Can an Enum implement interfaces?

- A. Yes ✅
- B. No
- C. Only abstract interfaces
- D. Only marker interfaces

---

### Q5. Which statement is correct?

- A. Enums can extend multiple classes.
- B. Enum constructors are public.
- C. Enum constants are singleton instances. ✅
- D. We can create Enum objects using `new`.

---

# 📝 Quick Revision

## Creating an Enum

```java
enum Day{

    MONDAY,
    TUESDAY,
    WEDNESDAY

}
```

---

## Accessing Constants

```java
Day today = Day.MONDAY;
```

---

## Iterating

```java
for(Day d : Day.values()){

    System.out.println(d);

}
```

---

## Using `switch`

```java
switch(today){

    case MONDAY:

        System.out.println("Start");

        break;

    default:

        System.out.println("Other Day");

}
```

---

## Useful Methods

| Method | Purpose |
|---------|---------|
| `values()` | Returns all constants |
| `valueOf()` | Converts String to Enum |
| `ordinal()` | Returns declaration index |
| `name()` | Returns constant name |
| `compareTo()` | Compares declaration order |
| `toString()` | Returns String representation (can be overridden) |

---

# 🧪 Practice Problems

## Beginner

- Create an Enum for Days of the Week.
- Print all enum constants using `values()`.
- Display the `ordinal()` of each constant.

---

## Intermediate

- Create an Enum for Months with the number of days.
- Implement a Traffic Signal program using `switch`.
- Create an Enum with a constructor and getter.

---

## Advanced

- Build an Order Management System using Enums.
- Create a Payment Status Enum with additional fields.
- Implement an Enum that overrides a method differently for each constant.
- Use an Enum in a Spring Boot REST API.

---

# 🔗 Related Topics

- Classes and Objects
- Constructors
- Static Keyword
- Final Keyword
- Interfaces
- Switch Statement
- Collections Framework
- Generics

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

You have completed **Chapter 20: Enums**.

### ✔️ Concepts Covered

- What are Enums?
- Creating and Using Enums
- Enum Methods (`values()`, `name()`, `ordinal()`, `valueOf()`)
- Enum Constructors
- Enum Fields and Methods
- Internal Working
- Enum vs Constants
- Enum vs Class
- Best Practices
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ An **Enum** is a special Java type representing a **fixed set of predefined constants**.
- ✅ Every enum constant is a **singleton object** created automatically by the JVM.
- ✅ Enums are **type-safe**, preventing invalid assignments.
- ✅ Enums can contain **constructors, fields, methods, and implement interfaces**.
- ✅ Enum constructors are **implicitly private** and cannot be called directly.
- ✅ Avoid using `ordinal()` for business logic because declaration order may change.
- ✅ Prefer Enums over integer or String constants whenever the set of values is fixed.

---

# 🚀 Next Chapter

➡️ **21-Exception-Handling.md**

### Topics Covered

- Introduction to Exceptions
- Types of Exceptions
- `try`, `catch`, `finally`
- `throw` and `throws`
- Custom Exceptions
- Checked vs Unchecked Exceptions
- Interview Questions
- MCQs
- Practice Problems
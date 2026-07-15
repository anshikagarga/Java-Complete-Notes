# 📘 Chapter 05: Comparator Interface (Part 3)

## Comparator vs Comparable, Interview Questions, MCQs & Practice Problems

> *"Comparator is the preferred choice when an application requires multiple sorting strategies. It keeps the sorting logic separate from the data model, making the code flexible, reusable, and easier to maintain."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Comparator and Comparable.
- Understand when to use Comparator.
- Learn the advantages and limitations of Comparator.
- Revise the complete chapter.
- Prepare for Java interviews.
- Solve practice problems.

---

# 📚 Table of Contents

1. Comparator vs Comparable
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

# 📊 Comparator vs Comparable

| Feature | Comparator | Comparable |
|----------|------------|------------|
| Package | java.util | java.lang |
| Method | compare() | compareTo() |
| Sorting Order | Custom Ordering | Natural Ordering |
| Number of Sorting Criteria | Multiple | One |
| Original Class Modification | ❌ No | ✅ Yes |
| Lambda Support | ✅ Yes | ❌ No |
| Method Reference Support | ✅ Yes | ❌ No |
| Java 8 Utility Methods | ✅ Yes | ❌ No |
| Best For | Multiple Sorting Rules | Default Sorting |

---

# 📖 When Should You Use Comparator?

Use Comparator when:

- Multiple sorting orders are required.
- The original class cannot be modified.
- Sorting logic changes frequently.
- Different modules require different sorting rules.

Example

```text
Student

↓

Sort by Name

↓

Sort by Marks

↓

Sort by Roll Number

↓

Sort by Age
```

Each sorting rule can have its own Comparator.

---

# 📖 When Should You NOT Use Comparator?

Avoid Comparator when

- Only one natural ordering exists.
- Every object should always be sorted the same way.

Example

```text
Book

↓

ISBN
```

or

```text
Employee

↓

Employee ID
```

In such cases,

Comparable is a better choice.

---

# 🌍 Real-World Example

Suppose an Employee Management System.

Different users require different sorting.

HR

↓

Sort by Salary

Manager

↓

Sort by Experience

Finance

↓

Sort by Bonus

Admin

↓

Sort by Employee ID

Instead of changing the Employee class,

we create multiple Comparators.

---

# 📊 Comparator Decision Flow

```text
Need Multiple Sorting Orders?

↓

YES

↓

Comparator

-------------------------

Need Default Ordering?

↓

YES

↓

Comparable
```

---

# 📖 Advantages

- Supports multiple sorting criteria.
- Does not modify the original class.
- Easy to reuse.
- Easy to maintain.
- Supports Lambda Expressions.
- Supports Method References.
- Supports Comparator chaining.
- Supports null handling.

---

# ⚠️ Limitations

- Requires additional Comparator objects.
- Can increase the number of classes if each comparator is written separately.
- Slightly more complex for beginners.
- Too many Comparators can reduce readability if poorly organized.

---

# ⚠️ Common Mistakes

## ❌ Returning Boolean

Wrong

```java
return s1.id > s2.id;
```

Correct

```java
return Integer.compare(s1.id, s2.id);
```

---

## ❌ Comparing Strings Incorrectly

Wrong

```java
return s1.name - s2.name;
```

Correct

```java
return s1.name.compareTo(s2.name);
```

---

## ❌ Using Subtraction

Wrong

```java
return s1.salary - s2.salary;
```

Correct

```java
return Integer.compare(

    s1.salary,

    s2.salary

);
```

---

## ❌ Ignoring Null Values

Wrong

```java
Comparator.comparing(Student::getName)
```

Better

```java
Comparator.nullsFirst(

    Comparator.comparing(Student::getName)

);
```

or

```java
Comparator.nullsLast(

    Comparator.comparing(Student::getName)

);
```

---

## ❌ Writing Large compare() Methods

Instead of

```java
if(...)
else if(...)
else...
```

Prefer

```java
Comparator

.comparing(...)

.thenComparing(...)
```

Cleaner and easier to maintain.

---

# 💡 Best Practices

- Prefer `Comparator.comparing()`.
- Use Method References whenever possible.
- Use `thenComparing()` for secondary sorting.
- Use `reversed()` for descending order.
- Use `nullsFirst()` and `nullsLast()` for null-safe sorting.
- Keep Comparator classes reusable.
- Prefer Lambda Expressions over anonymous classes.

---

# 🧩 Interview Questions

## Beginner

1. What is Comparator?
2. Why do we use Comparator?
3. Which package contains Comparator?
4. What is the return type of compare()?
5. Difference between compare() and compareTo()?

---

## Intermediate

6. Difference between Comparator and Comparable.
7. Why is Comparator preferred for multiple sorting?
8. Explain Comparator chaining.
9. Explain Comparator.comparing().
10. What does reversed() do?

---

## Advanced

11. Explain thenComparing().
12. Explain nullsFirst() and nullsLast().
13. Can Comparator sort immutable classes?
14. Why are Method References preferred?
15. Can multiple Comparators be used for the same class?

---

# 🎓 MCQs

### Q1. Comparator belongs to:

- A. java.lang
- B. java.io
- C. java.util ✅
- D. java.sql

---

### Q2. Comparator contains:

- A. compare() ✅
- B. compareTo()
- C. equals()
- D. hashCode()

---

### Q3. Comparator supports:

- A. One Sorting Order
- B. Multiple Sorting Orders ✅
- C. Natural Ordering Only
- D. Random Ordering

---

### Q4. Which method is commonly used for Comparator chaining?

- A. compare()
- B. thenComparing() ✅
- C. equals()
- D. hashCode()

---

### Q5. Which method creates a descending Comparator?

- A. reverse()
- B. descending()
- C. reversed() ✅
- D. compareDescending()

---

# 📝 Quick Revision

## Comparator Flow

```text
Comparator

↓

compare()

↓

Collections.sort()

↓

Sorted List
```

---

## compare()

```text
Negative

↓

Object 1 First

----------------------

Zero

↓

Equal

----------------------

Positive

↓

Object 2 First
```

---

## Java 8 Utilities

```text
Comparator.comparing()

↓

thenComparing()

↓

reversed()

↓

nullsFirst()

↓

nullsLast()
```

---

## Properties

```text
Multiple Sorting

✅

Natural Ordering

❌

Original Class Modified

❌

Lambda Supported

✅

Method References

✅
```

---

# 🧪 Practice Problems

## Beginner

- Sort students by Name.
- Sort students by Marks.
- Sort employees by Salary.
- Sort products by Price.

---

## Intermediate

- Sort students by Marks and then by Name.
- Sort employees by Department and then by Salary.
- Sort products by Rating in descending order.
- Sort books by Author Name.

---

## Advanced

- Build a reusable Comparator library.
- Sort nested objects using Comparator.
- Sort objects containing null values.
- Implement Comparator using Lambda Expressions and Method References.
- Compare the performance of Comparator and Comparable.

---

# 🔗 Related Topics

- Comparable Interface
- Collections.sort()
- Arrays.sort()
- Lambda Expressions
- Method References
- Functional Interfaces
- Generics
- Stream API

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

You have completed **Chapter 11: Comparator Interface**.

### ✔️ Concepts Covered

- Comparator Interface
- compare() Method
- Custom Ordering
- Multiple Sorting Criteria
- Comparator Chaining
- Java 8 Comparator Utilities
- Lambda Expressions
- Method References
- Comparator vs Comparable
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Comparator belongs to the **java.util** package.
- ✅ It provides **custom sorting** without modifying the original class.
- ✅ It contains a single abstract method: **compare()**.
- ✅ It supports **multiple sorting strategies**.
- ✅ Java 8 introduced powerful methods such as `comparing()`, `thenComparing()`, `reversed()`, `nullsFirst()`, and `nullsLast()`.
- ✅ Comparator works seamlessly with **Lambda Expressions** and **Method References**.
- ✅ It is the preferred choice for modern Java applications when flexible sorting is required.

---

# 🚀 Next Chapter

➡️ **06-Lambda-with-Comparator.md**

### Topics Covered

- What are Lambda Expressions?
- Functional Interfaces
- Comparator with Lambda
- Sorting using Lambda
- Method References
- Comparator.comparing()
- thenComparing()
- reversed()
- Interview Questions
- Practice Problems
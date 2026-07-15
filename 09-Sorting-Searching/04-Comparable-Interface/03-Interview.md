# 📘 Chapter 4: Comparable Interface (Part 3)

## Comparable vs Comparator, Interview Questions, MCQs & Practice Problems

> *"Comparable defines the natural ordering of objects, whereas Comparator allows multiple custom sorting strategies without modifying the original class."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Comparable and Comparator.
- Decide when to use Comparable.
- Understand the limitations of Comparable.
- Revise the complete chapter.
- Prepare for Java interviews.
- Solve practice problems.

---

# 📚 Table of Contents

1. Comparable vs Comparator
2. Advantages & Limitations
3. Real-World Applications
4. Common Mistakes
5. Best Practices
6. Interview Questions
7. MCQs
8. Quick Revision
9. Practice Problems
10. Related Topics
11. References
12. Chapter Summary

---

# 📊 Comparable vs Comparator

| Feature | Comparable | Comparator |
|----------|------------|------------|
| Package | java.lang | java.util |
| Method | compareTo() | compare() |
| Interface Type | Functional Interface | Functional Interface |
| Sorting Order | Natural (Default) | Custom |
| Number of Sorting Criteria | One | Multiple |
| Modifies Original Class | ✅ Yes | ❌ No |
| Lambda Support | ❌ No | ✅ Yes |
| Used By | Collections.sort(), Arrays.sort() | Collections.sort(list, comparator) |

---

# 📖 When Should You Use Comparable?

Use Comparable when:

- The class has one natural ordering.
- The sorting logic rarely changes.
- Every object should always be sorted in the same way.

Example

```text
Employee

↓

Employee ID
```

or

```text
Book

↓

ISBN
```

---

# 📖 When Should You NOT Use Comparable?

Avoid Comparable when:

- Multiple sorting criteria are required.
- Sorting rules change frequently.
- You cannot modify the source class.

Example

Student can be sorted by

```text
Roll Number

↓

Name

↓

Marks

↓

Age
```

Comparable supports only **one** default ordering.

---

# 🌍 Real-World Example

Suppose an Employee class.

You may want to sort employees by

```text
Employee ID
```

This is the natural order.

So Comparable is a good choice.

However,

if tomorrow you need to sort by

```text
Salary
```

or

```text
Department
```

Comparator is a better choice.

---

# 📊 Comparable Decision Flow

```text
Need Default Sorting?

↓

YES

↓

Comparable

-----------------------

Need Multiple Sort Orders?

↓

YES

↓

Comparator
```

---

# 📖 Advantages

- Easy to implement.
- Defines a natural ordering.
- Automatically works with Collections.sort().
- Automatically works with Arrays.sort().
- Less code for simple sorting.
- Commonly used in Java libraries.

---

# ⚠️ Limitations

- Supports only one sorting order.
- Requires modifying the original class.
- Not suitable for multiple sorting criteria.
- Difficult to extend for different business requirements.

---

# ⚠️ Common Mistakes

## ❌ Forgetting to Implement Comparable

Wrong

```java
class Student{

}
```

Correct

```java
class Student implements Comparable<Student>{

}
```

---

## ❌ Returning Boolean

Wrong

```java
return true;
```

Correct

```java
return Integer.compare(this.id, other.id);
```

---

## ❌ Comparing Strings Incorrectly

Wrong

```java
return this.name - other.name;
```

Correct

```java
return this.name.compareTo(other.name);
```

---

## ❌ Using Subtraction for Comparison

Wrong

```java
return this.salary - other.salary;
```

Correct

```java
return Integer.compare(this.salary, other.salary);
```

---

## ❌ Defining Multiple Natural Orders

Comparable should define only **one** natural ordering.

If you need multiple sorting rules,

use Comparator instead.

---

# 💡 Best Practices

- Use Comparable only for the natural ordering.
- Prefer `Integer.compare()` over subtraction.
- Prefer `Double.compare()` for decimal values.
- Keep `compareTo()` simple and consistent.
- Use Comparator for custom sorting.
- Make compareTo() consistent with equals() whenever possible.

---

# 🧩 Interview Questions

## Beginner

1. What is Comparable?
2. Why do we use Comparable?
3. What is natural ordering?
4. Which package contains Comparable?
5. What is the return type of compareTo()?

---

## Intermediate

6. Difference between Comparable and Comparator.
7. Why can Comparable define only one sorting order?
8. How does Collections.sort() use Comparable?
9. Why should compareTo() be consistent?
10. Can Strings be sorted using Comparable?

---

## Advanced

11. Why is Comparable called natural ordering?
12. Can one class implement both Comparable and Comparator?
13. Why is Integer.compare() preferred?
14. Can compareTo() return any positive or negative integer?
15. Is compareTo() mandatory after implementing Comparable?

---

# 🎓 MCQs

### Q1. Comparable belongs to:

- A. java.util
- B. java.io
- C. java.lang ✅
- D. java.sql

---

### Q2. Comparable contains:

- A. compare()
- B. compareTo() ✅
- C. equals()
- D. hashCode()

---

### Q3. Comparable supports:

- A. Multiple sorting orders
- B. One natural ordering ✅
- C. Random sorting
- D. Descending only

---

### Q4. Which method uses Comparable internally?

- A. Collections.sort() ✅
- B. Scanner
- C. Thread
- D. File

---

### Q5. Which interface is better for multiple sorting criteria?

- A. Comparable
- B. Comparator ✅
- C. Serializable
- D. Cloneable

---

# 📝 Quick Revision

## Comparable Flow

```text
Class

↓

implements Comparable

↓

Override compareTo()

↓

Collections.sort()

↓

Sorted List
```

---

## compareTo()

```text
Negative

↓

Current Object First

---------------------

Zero

↓

Equal

---------------------

Positive

↓

Other Object First
```

---

## Properties

```text
Natural Ordering

✅

One Sorting Order

✅

Multiple Sorting Orders

❌

Default Sorting

✅
```

---

# 🧪 Practice Problems

## Beginner

- Sort students by Roll Number.
- Sort employees by Employee ID.
- Sort books by ISBN.
- Sort products by Product ID.

---

## Intermediate

- Sort students by Marks using Comparable.
- Sort employees by Salary using Comparable.
- Sort strings alphabetically.
- Sort dates using Comparable.

---

## Advanced

- Create an immutable class implementing Comparable.
- Compare custom objects containing nested fields.
- Implement Comparable with null-safe comparison.
- Analyze the performance of Collections.sort() with Comparable.

---

# 🔗 Related Topics

- Collections.sort()
- Arrays.sort()
- Comparator Interface
- Lambda Expressions
- Functional Interfaces
- Generics
- Object Class
- equals() and hashCode()

---

# 📚 References

- Oracle Java Documentation
- Effective Java by Joshua Bloch
- Java: The Complete Reference
- GeeksforGeeks
- OpenJDK Documentation

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 10: Comparable Interface**.

### ✔️ Concepts Covered

- Comparable Interface
- Natural Ordering
- compareTo() Method
- Java Implementation
- Internal Working
- Collections.sort()
- Time Complexity
- Comparable vs Comparator
- Best Practices
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Comparable is present in the **java.lang** package.
- ✅ It defines the **natural (default) ordering** of objects.
- ✅ It contains a single method: **compareTo()**.
- ✅ `Collections.sort()` and `Arrays.sort()` use `compareTo()` internally.
- ✅ A class can define **only one natural ordering** using Comparable.
- ✅ For **multiple sorting criteria**, use the **Comparator** interface instead.
- ✅ Prefer `Integer.compare()` and `Double.compare()` over subtraction to avoid overflow.

---

# 🚀 Next Chapter

➡️ **11-Comparator-Interface.md**

### Topics Covered

- What is Comparator?
- Why Comparator?
- compare() Method
- Comparator vs Comparable
- Sorting by Multiple Fields
- Lambda Expressions
- Method References
- Java 8+ Comparator Utilities
- Interview Questions
- Practice Problems
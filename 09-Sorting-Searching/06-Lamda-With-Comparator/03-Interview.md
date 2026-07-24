# 📘 Chapter 06: Lambda with Comparator (Part 3)

> *"Lambda Expressions and Comparator are among the most commonly used Java 8 features in interviews and real-world applications. Understanding them helps you write cleaner, shorter, and more maintainable code."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Revise Lambda with Comparator
- Solve Interview Questions
- Practice MCQs
- Solve Coding Problems
- Understand Best Practices
- Revise Comparator Utility Methods

---

# 📚 Table of Contents

1. Interview Questions
2. MCQs
3. Coding Practice
4. Best Practices
5. Common Mistakes
6. Quick Revision
7. Real-World Applications
8. References
9. Chapter Summary

---

# 🎤 Interview Questions

## Beginner Level

### Q1. What is a Lambda Expression?

**Answer**

A Lambda Expression is an anonymous function introduced in Java 8 that allows functional programming and reduces boilerplate code.

Syntax

```java
(parameters) -> expression
```

---

### Q2. Why is Lambda used with Comparator?

**Answer**

Lambda Expressions eliminate the need to create anonymous Comparator classes, making the code shorter, cleaner, and easier to maintain.

---

### Q3. Which interface does Comparator belong to?

**Answer**

```java
java.util.Comparator
```

---

### Q4. What is Comparator.comparing()?

**Answer**

`Comparator.comparing()` creates a Comparator based on a specific object property.

Example

```java
Comparator.comparing(Student::getMarks)
```

---

### Q5. What is Method Reference?

**Answer**

A Method Reference is a shorter form of a Lambda Expression.

Example

```java
Student::getName
```

instead of

```java
student -> student.getName()
```

---

# 🎤 Intermediate Questions

### Q6. Difference between Lambda and Anonymous Class?

| Lambda | Anonymous Class |
|---------|-----------------|
| Short syntax | Large syntax |
| More readable | More boilerplate |
| Java 8 feature | Available before Java 8 |
| Better for functional interfaces | Can extend abstract classes and implement interfaces |

---

### Q7. What is thenComparing()?

**Answer**

It performs secondary sorting when the primary comparison results in equality.

Example

```java
Comparator.comparing(Student::getMarks)
          .thenComparing(Student::getName);
```

---

### Q8. What does reversed() do?

**Answer**

It reverses the current Comparator.

Example

```java
Comparator.comparing(Employee::getSalary)
          .reversed();
```

---

### Q9. Difference between naturalOrder() and reverseOrder()?

| naturalOrder() | reverseOrder() |
|----------------|----------------|
| Ascending order | Descending order |
| Default ordering | Reverse ordering |

---

### Q10. What are nullsFirst() and nullsLast()?

**Answer**

These methods handle null values during sorting.

```java
Comparator.nullsFirst(...)
```

Places null values at the beginning.

```java
Comparator.nullsLast(...)
```

Places null values at the end.

---

# 🎤 Advanced Questions

### Q11. Why is Integer.compare() preferred over subtraction?

**Answer**

Using subtraction like `a - b` may cause integer overflow.

Safer approach

```java
Integer.compare(a, b)
```

---

### Q12. Can Lambda Expressions access local variables?

**Answer**

Yes, but only if the local variables are **final** or **effectively final**.

---

### Q13. Can Comparator be implemented using Lambda?

**Answer**

Yes.

Example

```java
Comparator<Integer> comparator =

(a, b) -> Integer.compare(a, b);
```

---

### Q14. Can Lambda Expressions replace all Anonymous Classes?

**Answer**

No.

Lambda Expressions can replace only implementations of **Functional Interfaces** (interfaces with exactly one abstract method).

---

### Q15. What is the biggest advantage of Lambda with Comparator?

**Answer**

- Less code
- Better readability
- Easier maintenance
- Functional programming support
- Seamless integration with Streams API

---

# 💡 Best Practices

✔ Prefer Lambda over anonymous Comparator classes.

✔ Use Method References whenever possible.

✔ Use `Comparator.comparing()` instead of manually writing compare logic.

✔ Use `Integer.compare()` instead of subtraction.

✔ Use `thenComparing()` for multi-level sorting.

✔ Handle null values using `nullsFirst()` or `nullsLast()`.

✔ Keep Lambda expressions small and readable.

---

# ⚠️ Common Mistakes

## ❌ Using Subtraction

Wrong

```java
(a, b) -> a - b
```

Correct

```java
Integer.compare(a, b)
```

---

## ❌ Writing Long Lambda Expressions

Wrong

```java
(a, b) -> {

    if(a.getAge() > b.getAge()){

        return 1;

    }

    else{

        return -1;

    }

}
```

Correct

```java
Comparator.comparing(Person::getAge)
```

---

## ❌ Ignoring Null Values

Wrong

```java
list.sort(

Comparator.comparing(Student::getName)

);
```

Correct

```java
list.sort(

Comparator.nullsLast(

Comparator.comparing(Student::getName)

)

);
```

---

## ❌ Forgetting Method References

Instead of

```java
student -> student.getName()
```

Prefer

```java
Student::getName
```

---

# 📝 Quick Revision

## Ascending Order

```java
list.sort(

Comparator.naturalOrder()

);
```

---

## Descending Order

```java
list.sort(

Comparator.reverseOrder()

);
```

---

## Sort by Field

```java
Comparator.comparing(

Student::getMarks

);
```

---

## Secondary Sorting

```java
Comparator.comparing(Student::getMarks)

.thenComparing(Student::getName);
```

---

## Reverse Comparator

```java
Comparator.comparing(Student::getMarks)

.reversed();
```

---

## Handle Null Values

```java
Comparator.nullsFirst(

Comparator.comparing(Student::getName)

);
```

```java
Comparator.nullsLast(

Comparator.comparing(Student::getName)

);
```

---

# 🎓 MCQs

### Q1. Lambda Expressions were introduced in

- A. Java 6
- B. Java 7
- C. Java 8 ✅
- D. Java 11

---

### Q2. Which package contains Comparator?

- A. java.lang
- B. java.util ✅
- C. java.io
- D. java.sql

---

### Q3. Which method creates a Comparator using an object field?

- A. compare()
- B. comparing() ✅
- C. compareTo()
- D. compareWith()

---

### Q4. Which method performs secondary sorting?

- A. comparing()
- B. reversed()
- C. thenComparing() ✅
- D. reverseOrder()

---

### Q5. Which method reverses the Comparator?

- A. reverse()
- B. reversed() ✅
- C. descending()
- D. flip()

---

### Q6. Which method places null values first?

- A. firstNull()
- B. nullFirst()
- C. nullsFirst() ✅
- D. nullComparator()

---

### Q7. Which method places null values last?

- A. nullLast()
- B. lastNull()
- C. nullsLast() ✅
- D. endNull()

---

### Q8. Which Comparator method sorts in ascending order?

- A. reverseOrder()
- B. comparing()
- C. naturalOrder() ✅
- D. sort()

---

### Q9. Which Comparator method sorts in descending order?

- A. reverseOrder() ✅
- B. naturalOrder()
- C. comparing()
- D. thenComparing()

---

### Q10. Which Java feature makes Comparator code concise?

- A. Generics
- B. Streams
- C. Lambda Expressions ✅
- D. Reflection

---

# 💻 Practice Problems

## Beginner

1. Sort a list of integers using Lambda.
2. Sort a list in descending order.
3. Sort strings alphabetically.
4. Sort strings by length.
5. Sort names ignoring case.

---

## Intermediate

6. Sort students by marks.
7. Sort employees by salary.
8. Sort products by price in descending order.
9. Handle null values while sorting.
10. Sort using Method References.

---

## Advanced

11. Sort employees by department and then by salary.
12. Sort students by marks (descending) and then by name.
13. Build a product catalog sorted by category and price.
14. Sort movie objects by rating and release year.
15. Integrate Comparator with Stream API for complex sorting.

---

# 🌍 Real-World Applications

Lambda with Comparator is widely used in:

- Student Management Systems
- Employee Management Systems
- Banking Applications
- HR Software
- Airline Reservation Systems
- Hospital Management
- Inventory Management
- E-commerce Product Sorting
- Spring Boot Applications
- REST APIs

---

# 📚 References

- Oracle Java Documentation
- Effective Java – Joshua Bloch
- OpenJDK Documentation
- Java: The Complete Reference
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **06-Lambda-with-Comparator.md**

### ✔️ Concepts Covered

- Lambda Expressions
- Comparator with Lambda
- Comparator Utility Methods
- `comparing()`
- `thenComparing()`
- `reversed()`
- `naturalOrder()`
- `reverseOrder()`
- `nullsFirst()`
- `nullsLast()`
- Method References
- Sorting Objects
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Lambda Expressions significantly reduce Comparator boilerplate code.
- ✅ `Comparator.comparing()` is the preferred way to sort objects by a field.
- ✅ `thenComparing()` enables multi-level sorting.
- ✅ `reversed()` reverses the current Comparator without rewriting logic.
- ✅ `nullsFirst()` and `nullsLast()` safely handle null values.
- ✅ Method References (`Class::method`) make Comparator code cleaner and more readable.
- ✅ These Java 8 features are heavily used in Spring Boot applications and frequently asked in interviews.

---

# 🚀 Next Chapter

➡️ **07-Custom-Sorting.md**

### Topics Covered

- What is Custom Sorting?
- Custom Sorting using Comparator
- Custom Sorting using Comparable
- Multi-Level Sorting
- Sorting by Multiple Fields
- Practical Examples
- Interview Questions
- MCQs
- Practice Problems
```
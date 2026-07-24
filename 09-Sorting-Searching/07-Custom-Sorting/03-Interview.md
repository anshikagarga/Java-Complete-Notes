# 📘 Chapter 07: Custom Sorting (Part 3)

> *"Custom Sorting is one of the most frequently asked interview topics because it demonstrates your understanding of Comparable, Comparator, Lambda Expressions, and Java Collections."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Revise Custom Sorting
- Solve Interview Questions
- Practice MCQs
- Solve Coding Problems
- Understand Best Practices
- Revise Comparable & Comparator

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

### Q1. What is Custom Sorting?

**Answer**

Custom Sorting means sorting data according to user-defined business logic instead of Java's default (natural) ordering.

Example

- Highest Salary
- Lowest Price
- Name Length
- Department Wise

---

### Q2. Which interface is mainly used for Custom Sorting?

**Answer**

```java
Comparator
```

Package

```java
java.util.Comparator
```

---

### Q3. Which method performs custom comparison?

**Answer**

```java
compare()
```

Syntax

```java
int compare(T o1, T o2)
```

---

### Q4. Can Comparable perform Custom Sorting?

**Answer**

Yes, but only for **one default (natural) ordering**.

If multiple sorting rules are required, use **Comparator**.

---

### Q5. Which method starts Comparator creation in Java 8?

**Answer**

```java
Comparator.comparing()
```

---

# 🎤 Intermediate Questions

### Q6. Difference between Comparable and Comparator?

| Comparable | Comparator |
|------------|------------|
| Inside class | Outside class |
| compareTo() | compare() |
| One sorting rule | Multiple sorting rules |
| java.lang | java.util |

---

### Q7. Why is Comparator preferred?

**Answer**

Because one object may need multiple sorting rules.

Example

Employee can be sorted by

- Name
- Salary
- Experience
- Department
- Joining Date

---

### Q8. What is Multi-Level Sorting?

**Answer**

Sorting based on multiple fields.

Example

```text
Department

↓

Salary

↓

Name
```

Implemented using

```java
thenComparing()
```

---

### Q9. Difference between comparing() and comparingInt()?

| comparing() | comparingInt() |
|--------------|---------------|
| Object fields | int fields |
| Generic | Primitive int |
| Slightly slower (boxing) | Faster (no boxing) |

---

### Q10. Why use Integer.compare()?

**Answer**

To avoid integer overflow.

Wrong

```java
return a.salary - b.salary;
```

Correct

```java
return Integer.compare(

a.salary,

b.salary

);
```

---

# 🎤 Advanced Questions

### Q11. Can we chain multiple Comparators?

**Answer**

Yes.

Example

```java
Comparator

.comparing(Employee::getDepartment)

.thenComparing(Employee::getSalary)

.thenComparing(Employee::getName);
```

---

### Q12. Can we reverse custom sorting?

**Answer**

Yes.

```java
Comparator

.comparing(Employee::getSalary)

.reversed();
```

---

### Q13. Can Comparator be implemented using Lambda?

**Answer**

Yes.

Example

```java
Comparator<Employee> cmp =

(a,b) ->

Integer.compare(

a.getSalary(),

b.getSalary()

);
```

---

### Q14. Why is Comparator better than writing compare() manually?

**Answer**

Because Java 8 provides utility methods such as

- comparing()
- thenComparing()
- reversed()
- nullsFirst()
- nullsLast()

making the code cleaner and easier to maintain.

---

### Q15. Is Custom Sorting stable?

**Answer**

It depends on the sorting algorithm used underneath.

For example:

- **Collections.sort()** uses **TimSort**, which is stable.
- **Arrays.sort()** for object arrays also uses **TimSort** (stable).

---

# 💡 Best Practices

✔ Use Comparable only for natural ordering.

✔ Use Comparator for business-specific sorting.

✔ Prefer

```java
Comparator.comparing()
```

over manual comparison.

✔ Use

```java
Integer.compare()
```

instead of subtraction.

✔ Use

```java
thenComparing()
```

for multi-level sorting.

✔ Keep sorting logic outside the model class whenever possible.

---

# ⚠️ Common Mistakes

## ❌ Using Comparable for Multiple Sorting Rules

Wrong

```java
class Employee

implements Comparable<Employee>
```

Trying to sort by

- Salary
- Name
- Age
- Department

Not possible with one compareTo().

Use Comparator.

---

## ❌ Returning Boolean

Wrong

```java
return a.salary > b.salary;
```

Correct

```java
return Integer.compare(

a.salary,

b.salary

);
```

---

## ❌ Using Subtraction

Wrong

```java
return a.salary - b.salary;
```

Correct

```java
Integer.compare(

a.salary,

b.salary

);
```

---

## ❌ Forgetting Comparator Chain

Wrong

```java
Comparator.comparing(

Employee::getDepartment
);
```

Correct

```java
Comparator

.comparing(Employee::getDepartment)

.thenComparing(Employee::getSalary)

.thenComparing(Employee::getName);
```

---

# 📝 Quick Revision

## Sort by Name

```java
Comparator.comparing(

Employee::getName

);
```

---

## Sort by Salary

```java
Comparator.comparing(

Employee::getSalary

);
```

---

## Descending Salary

```java
Comparator

.comparing(Employee::getSalary)

.reversed();
```

---

## Multi-Level Sorting

```java
Comparator

.comparing(Employee::getDepartment)

.thenComparing(Employee::getSalary)

.thenComparing(Employee::getName);
```

---

## Lambda Comparator

```java
(a,b) ->

Integer.compare(

a.getSalary(),

b.getSalary()

);
```

---

# 🎓 MCQs

### Q1. Which interface is mainly used for Custom Sorting?

- A. Runnable
- B. Comparable
- C. Comparator ✅
- D. Serializable

---

### Q2. Comparator belongs to

- A. java.lang
- B. java.util ✅
- C. java.io
- D. java.sql

---

### Q3. Which method performs comparison?

- A. compare() ✅
- B. compareTo()
- C. equals()
- D. sort()

---

### Q4. Which method performs secondary sorting?

- A. comparing()
- B. reversed()
- C. thenComparing() ✅
- D. compare()

---

### Q5. Which method reverses sorting?

- A. reverse()
- B. reversed() ✅
- C. descending()
- D. compareReverse()

---

### Q6. Which Java version introduced Lambda Expressions?

- A. Java 6
- B. Java 7
- C. Java 8 ✅
- D. Java 11

---

### Q7. Which method is preferred for integer comparison?

- A. a-b
- B. compare()
- C. Integer.compare() ✅
- D. equals()

---

### Q8. Which Comparator method creates a Comparator using an object field?

- A. compare()
- B. comparing() ✅
- C. compareTo()
- D. sort()

---

### Q9. Which sorting utility method creates descending order?

- A. naturalOrder()
- B. comparing()
- C. reverseOrder() ✅
- D. descending()

---

### Q10. Custom Sorting is mostly used for

- A. Business Rules ✅
- B. Memory Allocation
- C. JVM
- D. Threads

---

# 💻 Practice Problems

## Beginner

1. Sort students by marks.
2. Sort employees by salary.
3. Sort products by price.
4. Sort names alphabetically.
5. Sort strings by length.

---

## Intermediate

6. Sort employees by department.
7. Sort students by marks and then by name.
8. Sort products by category and then by price.
9. Sort cities alphabetically ignoring case.
10. Sort employees in descending salary order.

---

## Advanced

11. Build a Student Ranking System.
12. Create an Employee Payroll Sorting Module.
13. Develop an E-commerce Product Sorting Engine.
14. Sort Movie objects by rating and release year.
15. Implement Airline Passenger Priority Sorting.

---

# 🌍 Real-World Applications

Custom Sorting is used in:

- Banking Systems
- Student Management Systems
- HR Management Software
- E-Commerce Websites
- Inventory Management
- Airline Reservation Systems
- Hospital Management
- Logistics & Delivery Applications
- Spring Boot REST APIs
- Financial Reporting Systems

---

# 📚 References

- Oracle Java Documentation
- OpenJDK Documentation
- Effective Java – Joshua Bloch
- Java: The Complete Reference
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **07-Custom-Sorting.md**

### ✔️ Concepts Covered

- Custom Sorting
- Natural vs Custom Sorting
- Comparable
- Comparator
- Lambda Expressions
- Comparator Utility Methods
- Multi-Level Sorting
- Sorting by Multiple Fields
- Business-Based Sorting
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Custom Sorting allows sorting according to business requirements.
- ✅ Use **Comparable** for a single natural ordering.
- ✅ Use **Comparator** when multiple sorting rules are needed.
- ✅ Java 8's `Comparator.comparing()` and `thenComparing()` make sorting concise and readable.
- ✅ Use `reversed()` for descending order instead of writing separate comparison logic.
- ✅ Prefer `Integer.compare()` over subtraction to avoid integer overflow.
- ✅ Custom Sorting is widely used in enterprise applications, Spring Boot projects, and Java interviews.

---

# 🚀 Next Chapter

➡️ **08-Sorting-Objects.md**

### Topics Covered

- Introduction to Sorting Objects
- Sorting Objects using Comparable
- Sorting Objects using Comparator
- Lambda Expressions
- Collections.sort()
- Arrays.sort()
- Real-World Examples
- Interview Questions
- MCQs
- Practice Problems
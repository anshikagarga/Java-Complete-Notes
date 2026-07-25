# 📘 Chapter 08: Sorting Objects (Part 3)

> *"Sorting Objects is one of the most important Java interview topics. Every enterprise application works with objects rather than primitive data types, making this concept essential for every Java developer."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Revise Object Sorting
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

### Q1. What is Object Sorting?

**Answer**

Object Sorting is the process of arranging objects according to one or more fields such as ID, Name, Marks, Salary, Price, or Department.

---

### Q2. Which interfaces are used for sorting objects?

**Answer**

- Comparable
- Comparator

---

### Q3. What is Comparable?

**Answer**

Comparable defines the **natural ordering** of objects.

Method

```java
compareTo()
```

Package

```java
java.lang
```

---

### Q4. What is Comparator?

**Answer**

Comparator defines **custom ordering**.

Method

```java
compare()
```

Package

```java
java.util
```

---

### Q5. Difference between Comparable and Comparator?

| Comparable | Comparator |
|------------|------------|
| Natural ordering | Custom ordering |
| compareTo() | compare() |
| One sorting rule | Multiple sorting rules |
| java.lang | java.util |

---

# 🎤 Intermediate Questions

### Q6. Which sorting algorithm is used internally?

**Answer**

For object sorting,

- `Collections.sort()`
- `List.sort()`
- `Arrays.sort(Object[])`

internally use **TimSort**, which is a stable sorting algorithm.

---

### Q7. Why is Comparator preferred?

**Answer**

Because a class can have multiple sorting requirements.

Example

Employee

- Salary
- Department
- Experience
- Name

Comparable can define only one natural ordering.

Comparator allows unlimited custom sorting.

---

### Q8. How do you sort objects by multiple fields?

**Answer**

Using

```java
thenComparing()
```

Example

```java
Comparator

.comparing(Student::getMarks)

.thenComparing(Student::getName);
```

---

### Q9. How do you sort in descending order?

**Answer**

Use

```java
reversed()
```

Example

```java
Comparator

.comparing(Employee::getSalary)

.reversed();
```

---

### Q10. Which methods are used for sorting?

| Method | Used For |
|---------|----------|
| Collections.sort() | List |
| List.sort() | List |
| Arrays.sort() | Arrays |

---

# 🎤 Advanced Questions

### Q11. Why should Integer.compare() be preferred?

**Answer**

Using subtraction

```java
a - b
```

can cause integer overflow.

Preferred

```java
Integer.compare(a,b)
```

---

### Q12. Can objects be sorted without Comparable?

**Answer**

Yes.

By providing a Comparator.

Example

```java
students.sort(

Comparator.comparing(

Student::getMarks

)

);
```

---

### Q13. Can Arrays.sort() sort custom objects?

**Answer**

Yes.

```java
Arrays.sort(

students,

Comparator.comparing(

Student::getMarks

)

);
```

---

### Q14. Can Comparator be implemented using Lambda?

**Answer**

Yes.

```java
Comparator<Student> cmp =

(a,b)->

Integer.compare(

a.getMarks(),

b.getMarks()

);
```

---

### Q15. Why override toString() while sorting objects?

**Answer**

Without overriding `toString()`,

printing objects displays

```text
Student@5a07e868
```

After overriding

```java
@Override

public String toString(){

return id + " " + name;

}
```

Output becomes

```text
101 Anshika

102 Aman

103 Riya
```

---

# 💡 Best Practices

✔ Use Comparable for natural ordering.

✔ Use Comparator for multiple sorting rules.

✔ Prefer `Comparator.comparing()` over manual comparisons.

✔ Use Method References whenever possible.

✔ Use `thenComparing()` for multi-level sorting.

✔ Use `Integer.compare()` instead of subtraction.

✔ Override `toString()` for meaningful output.

✔ Keep comparison logic clean and reusable.

---

# ⚠️ Common Mistakes

## ❌ Forgetting Comparable

Wrong

```java
Collections.sort(students);
```

If `Student` doesn't implement Comparable and no Comparator is supplied, compilation fails.

Correct

```java
Collections.sort(

students,

Comparator.comparing(

Student::getMarks

)

);
```

---

## ❌ Using Subtraction

Wrong

```java
return this.id - s.id;
```

Correct

```java
Integer.compare(

this.id,

s.id

);
```

---

## ❌ Forgetting to Override toString()

Wrong Output

```text
Student@4e25154f
```

Correct Output

```text
101 Anshika

102 Aman

103 Riya
```

---

## ❌ Writing Long Anonymous Classes

Wrong

```java
new Comparator<Student>(){

@Override

public int compare(Student a, Student b){

return Integer.compare(

a.getMarks(),

b.getMarks()

);

}

}
```

Correct

```java
Comparator.comparing(

Student::getMarks

)
```

---

# 📝 Quick Revision

## Natural Sorting

```java
class Student

implements Comparable<Student>
```

Method

```java
compareTo()
```

---

## Custom Sorting

```java
Comparator.comparing(

Student::getMarks

)
```

---

## Descending Order

```java
Comparator

.comparing(Student::getMarks)

.reversed();
```

---

## Multi-Level Sorting

```java
Comparator

.comparing(Student::getDepartment)

.thenComparing(Student::getMarks)

.thenComparing(Student::getName);
```

---

## Arrays

```java
Arrays.sort(

students,

Comparator.comparing(

Student::getMarks

)

);
```

---

## Lists

```java
Collections.sort(

students,

Comparator.comparing(

Student::getMarks

)

);
```

or

```java
students.sort(

Comparator.comparing(

Student::getMarks

)

);
```

---

# 🎓 MCQs

### Q1. Which interface defines natural ordering?

- A. Comparator
- B. Comparable ✅
- C. Cloneable
- D. Serializable

---

### Q2. Comparator belongs to

- A. java.lang
- B. java.util ✅
- C. java.io
- D. java.sql

---

### Q3. Comparable belongs to

- A. java.util
- B. java.lang ✅
- C. java.sql
- D. java.io

---

### Q4. Which method is used in Comparable?

- A. compare()
- B. compareTo() ✅
- C. sort()
- D. equals()

---

### Q5. Which method is used in Comparator?

- A. compare() ✅
- B. compareTo()
- C. compareObject()
- D. sort()

---

### Q6. Which algorithm is used internally for object sorting?

- A. Bubble Sort
- B. Merge Sort
- C. TimSort ✅
- D. Quick Sort

---

### Q7. Which method performs secondary sorting?

- A. comparing()
- B. reversed()
- C. thenComparing() ✅
- D. compare()

---

### Q8. Which method sorts arrays?

- A. Collections.sort()
- B. Arrays.sort() ✅
- C. List.sort()
- D. Stream.sort()

---

### Q9. Which method sorts lists?

- A. Arrays.sort()
- B. Collections.sort() ✅
- C. String.sort()
- D. Object.sort()

---

### Q10. Comparator is mainly used for

- A. Memory Management
- B. Custom Sorting ✅
- C. Exception Handling
- D. Multithreading

---

# 💻 Practice Problems

## Beginner

1. Sort students by ID.
2. Sort students by name.
3. Sort employees by salary.
4. Sort products by price.
5. Sort cities alphabetically.

---

## Intermediate

6. Sort employees by department.
7. Sort students by marks and then by name.
8. Sort products by category and price.
9. Sort movies by rating.
10. Sort employees by joining date.

---

## Advanced

11. Build a Student Ranking System.
12. Create an Employee Payroll Sorting Module.
13. Develop an E-commerce Product Sorting Engine.
14. Build a Hospital Patient Priority System.
15. Create an Airline Passenger Sorting Module.

---

# 🌍 Real-World Applications

Sorting Objects is widely used in:

- Banking Applications
- Student Management Systems
- Employee Payroll Software
- Hospital Management Systems
- Airline Reservation Systems
- E-Commerce Websites
- Inventory Management
- Library Management
- HR Software
- Spring Boot REST APIs

---

# 📚 References

- Oracle Java Documentation
- OpenJDK Documentation
- Effective Java – Joshua Bloch
- Java: The Complete Reference
- Head First Java
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have successfully completed **08-Sorting-Objects.md**

### ✔️ Concepts Covered

- Object Sorting
- Comparable Interface
- Comparator Interface
- Collections.sort()
- Arrays.sort()
- Lambda Expressions
- Method References
- Multi-Level Sorting
- Comparator Chaining
- Natural vs Custom Ordering
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Objects are sorted using **Comparable** or **Comparator**.
- ✅ Comparable provides **one natural ordering** through `compareTo()`.
- ✅ Comparator provides **multiple custom orderings** through `compare()`.
- ✅ `Comparator.comparing()` and `thenComparing()` simplify object sorting.
- ✅ `Collections.sort()`, `List.sort()`, and `Arrays.sort()` are the primary sorting methods.
- ✅ Object sorting internally uses **TimSort**, which is efficient and stable.
- ✅ Object sorting is an essential concept for Java interviews and enterprise application development.

---

# 🚀 Next Chapter

➡️ **09-Searching.md**

### Topics Covered

- Introduction to Searching
- Linear Search
- Binary Search
- Arrays.binarySearch()
- Collections.binarySearch()
- Searching Objects
- Time Complexity Comparison
- Interview Questions
- MCQs
- Practice Problems
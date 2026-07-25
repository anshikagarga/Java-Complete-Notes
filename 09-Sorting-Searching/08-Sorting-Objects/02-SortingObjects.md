# 📘 Chapter 08: Sorting Objects (Part 2)

> *"In enterprise applications, object sorting is rarely limited to a single field. Java provides Comparator chaining, Lambda Expressions, Method References, and utility methods to perform complex object sorting with minimal code."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Perform Multi-Level Object Sorting
- Chain Comparators
- Sort Objects using Lambda Expressions
- Sort Objects using Method References
- Sort Lists and Arrays of Objects
- Handle Null Values while Sorting
- Learn Advanced Object Sorting Techniques

---

# 📚 Table of Contents

1. Multi-Level Sorting
2. Comparator Chaining
3. Lambda Expressions
4. Method References
5. Sorting Arrays of Objects
6. Sorting Lists of Objects
7. Handling Null Values
8. Advanced Examples
9. Internal Working
10. Best Practices

---

# 📖 Multi-Level Sorting

Sometimes one field is not enough.

Example

```text
Department

↓

Salary

↓

Name
```

Meaning

- First sort by Department.
- If the Department is the same, sort by Salary.
- If Salary is also the same, sort by Name.

---

# 📖 Example

```java
students.sort(

Comparator

.comparing(Student::getMarks)

.thenComparing(Student::getName)

);
```

Output

```text
85 Aman

85 Riya

90 Anshika

95 Rahul
```

---

# 📖 Comparator Chaining

Multiple Comparators can be combined together.

```java
Comparator<Student> cmp =

Comparator

.comparing(Student::getMarks)

.thenComparing(Student::getName);

students.sort(cmp);
```

Advantages

- Reusable
- Readable
- Easy Maintenance

---

# 📖 Descending Order

Sort students by highest marks.

```java
students.sort(

Comparator

.comparing(Student::getMarks)

.reversed()

);
```

Output

```text
95

90

85

70
```

---

# 📖 Multiple Fields with Descending Order

```java
students.sort(

Comparator

.comparing(Student::getDepartment)

.thenComparing(

Comparator

.comparing(Student::getMarks)

.reversed()

)

.thenComparing(Student::getName)

);
```

Sorting Order

```text
Department

↓

Highest Marks

↓

Name
```

---

# 📖 Sorting using Lambda

Instead of

```java
Comparator<Student> cmp =

new Comparator<Student>(){

@Override

public int compare(Student a, Student b){

return Integer.compare(

a.getMarks(),

b.getMarks()

);

}

};
```

Use Lambda

```java
students.sort(

(a,b)->

Integer.compare(

a.getMarks(),

b.getMarks()

)

);
```

Much shorter.

---

# 📖 Using Method References

Instead of

```java
(a,b)->

a.getName()

.compareTo(

b.getName()

)
```

Use

```java
students.sort(

Comparator.comparing(

Student::getName

)

);
```

Cleaner and more readable.

---

# 📖 Sorting Arrays of Objects

Example

```java
Student[] students={

new Student(1,"Anshika",95),

new Student(2,"Aman",80),

new Student(3,"Riya",90)

};
```

Sort by Name

```java
Arrays.sort(

students,

Comparator.comparing(

Student::getName

)

);
```

Sort by Marks

```java
Arrays.sort(

students,

Comparator.comparing(

Student::getMarks

)

);
```

---

# 📖 Sorting Lists of Objects

```java
List<Student> students =

new ArrayList<>();
```

Sort by Marks

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

# 📖 Handling Null Values

Suppose

```java
List<String> names =

Arrays.asList(

"Java",

null,

"Python",

"C"

);
```

Null First

```java
names.sort(

Comparator.nullsFirst(

String::compareTo

)

);
```

Output

```text
null

C

Java

Python
```

---

Null Last

```java
names.sort(

Comparator.nullsLast(

String::compareTo

)

);
```

Output

```text
C

Java

Python

null
```

---

# 📖 Sorting by String Length

```java
students.sort(

Comparator.comparingInt(

student ->

student.getName().length()

)

);
```

Output

```text
Aman

Riya

Anshika
```

---

# 📖 Advanced Example

Employee

```java
employees.sort(

Comparator

.comparing(Employee::getDepartment)

.thenComparing(

Employee::getSalary

)

.reversed()

.thenComparing(

Employee::getName

)

);
```

Priority

```text
Department

↓

Salary (Descending)

↓

Name
```

---

# 📖 Sorting by Date

```java
employees.sort(

Comparator.comparing(

Employee::getJoiningDate

)

);
```

Output

```text
Oldest Joining Date

↓

Newest Joining Date
```

---

# 📦 Internal Working

```text
Objects

↓

Comparator

↓

Lambda / Method Reference

↓

Comparison Logic

↓

Collections.sort()

or

Arrays.sort()

↓

TimSort

↓

Sorted Objects
```

---

# 💡 Best Practices

- Prefer `Comparator.comparing()` for object fields.
- Use `thenComparing()` for secondary sorting.
- Use `reversed()` instead of writing reverse logic manually.
- Use Method References whenever possible.
- Use `comparingInt()`, `comparingDouble()`, and `comparingLong()` for primitive fields.
- Handle null values using `nullsFirst()` or `nullsLast()`.

---

# ⚠️ Common Mistakes

## ❌ Forgetting Secondary Sorting

Wrong

```java
Comparator.comparing(

Student::getMarks

);
```

Correct

```java
Comparator

.comparing(Student::getMarks)

.thenComparing(Student::getName);
```

---

## ❌ Using Subtraction

Wrong

```java
(a,b)->

a.getMarks()-b.getMarks();
```

Correct

```java
Integer.compare(

a.getMarks(),

b.getMarks()

);
```

---

## ❌ Not Handling Null Values

Wrong

```java
students.sort(

Comparator.comparing(

Student::getName

)

);
```

If names contain `null`, it may throw a `NullPointerException`.

Correct

```java
students.sort(

Comparator.nullsLast(

Comparator.comparing(

Student::getName

)

)

);
```

---

## ❌ Writing Long Anonymous Comparator Classes

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

# 🌍 Real-World Applications

Advanced Object Sorting is used in:

- Banking Systems
- Student Ranking Systems
- Employee Payroll Software
- Hospital Management Systems
- Airline Reservation Systems
- E-Commerce Platforms
- Inventory Management
- Spring Boot REST APIs
- HR Management Systems
- Financial Reporting Applications

---

# 🎯 Interview Tip

### Question

How do you sort students by marks in descending order and then by name?

### Answer

```java
students.sort(

Comparator

.comparing(Student::getMarks)

.reversed()

.thenComparing(Student::getName)

);
```

This first sorts students by **highest marks**, and if two students have the same marks, they are sorted **alphabetically by name**.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Interview Questions
- MCQs
- Coding Practice
- Best Practices Revision
- Chapter Summary
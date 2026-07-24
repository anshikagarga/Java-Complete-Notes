# 📘 Chapter 07: Custom Sorting (Part 1)

> *"Custom Sorting allows developers to sort data according to their own business rules instead of Java's default ascending order. It is one of the most frequently used concepts in real-world Java applications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Custom Sorting.
- Learn why Custom Sorting is needed.
- Perform Custom Sorting using Comparator.
- Perform Custom Sorting using Comparable.
- Sort objects by different fields.
- Understand business-specific sorting.

---

# 📚 Table of Contents

1. Introduction
2. Why Custom Sorting?
3. Natural vs Custom Sorting
4. Custom Sorting using Comparator
5. Custom Sorting using Comparable
6. Business Rules
7. Internal Working
8. Best Practices
9. Common Mistakes

---

# 📖 What is Custom Sorting?

Custom Sorting means sorting data according to **our own logic** instead of Java's default ordering.

Examples

- Highest Salary First
- Youngest Student First
- Product Price (Low → High)
- Product Price (High → Low)
- Alphabetical Name
- Name Length
- Department then Salary

---

# 💡 Why Do We Need Custom Sorting?

Default sorting only sorts using the natural order.

Example

```text
10

20

30

40
```

But businesses often need different rules.

Example

```text
Employees

↓

Highest Salary First

↓

Experience

↓

Name
```

---

# 📖 Natural Sorting vs Custom Sorting

| Natural Sorting | Custom Sorting |
|-----------------|----------------|
| Default ordering | User-defined ordering |
| Comparable | Comparator |
| One sorting logic | Unlimited sorting logic |
| Fixed | Flexible |

---

# 📖 Example Class

```java
class Student{

    int id;

    String name;

    int marks;

    Student(int id,String name,int marks){

        this.id=id;

        this.name=name;

        this.marks=marks;

    }

}
```

---

# 📖 Custom Sorting using Comparator

Sort students by marks.

```java
students.sort(

Comparator.comparing(

Student::getMarks

)

);
```

Output

```text
Lowest Marks First
```

---

# 📖 Descending Order

```java
students.sort(

Comparator

.comparing(Student::getMarks)

.reversed()

);
```

Output

```text
Highest Marks First
```

---

# 📖 Sort by Name

```java
students.sort(

Comparator.comparing(

Student::getName

)

);
```

Output

```text
Aman

Anshika

Riya

Rohan
```

---

# 📖 Sort by ID

```java
students.sort(

Comparator.comparingInt(

Student::getId

)

);
```

Output

```text
101

102

103

104
```

---

# 📖 Custom Sorting using Comparable

Implement Comparable.

```java
class Student implements Comparable<Student>{

    int marks;

    @Override

    public int compareTo(Student s){

        return Integer.compare(

        this.marks,

        s.marks

        );

    }

}
```

Now

```java
Collections.sort(students);
```

works automatically.

---

# 📖 Business Example

Sort Employees

Priority

```text
Salary

↓

Experience

↓

Name
```

Comparator

```java
employees.sort(

Comparator

.comparing(Employee::getSalary)

.reversed()

.thenComparing(Employee::getExperience)

.reversed()

.thenComparing(Employee::getName)

);
```

---

# 📖 Another Example

Sort Products

Priority

```text
Category

↓

Price

↓

Product Name
```

```java
products.sort(

Comparator

.comparing(Product::getCategory)

.thenComparing(Product::getPrice)

.thenComparing(Product::getName)

);
```

---

# 📦 Internal Working

```text
Collection

↓

Comparator / Comparable

↓

Custom Comparison Logic

↓

Sorting Algorithm

↓

Sorted Collection
```

---

# 📊 Comparable vs Comparator

| Comparable | Comparator |
|------------|------------|
| Inside Class | Outside Class |
| compareTo() | compare() |
| One Natural Order | Multiple Custom Orders |
| java.lang | java.util |

---

# 💡 Best Practices

- Use **Comparable** for the default (natural) ordering of a class.
- Use **Comparator** when multiple sorting criteria are required.
- Prefer `Comparator.comparing()` over manually writing comparison logic.
- Use `comparingInt()`, `comparingDouble()`, and `comparingLong()` for primitive fields.
- Keep comparison logic simple and readable.

---

# ⚠️ Common Mistakes

## ❌ Using Comparable for Multiple Sorting Rules

Wrong

```java
class Student

implements Comparable<Student>
```

Trying to sort by

- Name
- Marks
- Age
- Department

Not possible using only one `compareTo()` implementation.

Use Comparator instead.

---

## ❌ Using Subtraction

Wrong

```java
return this.salary - e.salary;
```

Correct

```java
return Integer.compare(

this.salary,

e.salary

);
```

---

## ❌ Forgetting reversed()

Wrong

```java
Comparator.comparing(

Employee::getSalary

);
```

Expected Highest Salary First.

Correct

```java
Comparator

.comparing(Employee::getSalary)

.reversed();
```

---

# 🌍 Real-World Applications

Custom Sorting is widely used in:

- Employee Management Systems
- Banking Applications
- Student Result Portals
- Airline Reservation Systems
- Hospital Management
- E-Commerce Product Listings
- Inventory Systems
- Spring Boot REST APIs

---

# 🎯 Interview Tip

### Question

When should you use Comparable and when should you use Comparator?

### Answer

- Use **Comparable** when the class has **one natural ordering**, such as sorting students by roll number.
- Use **Comparator** when different sorting rules are needed, such as sorting students by marks, name, age, or department.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Multi-Level Sorting
- Comparator Chaining
- Sorting with Lambda
- Sorting Arrays of Objects
- Sorting Maps
- Advanced Custom Sorting Examples
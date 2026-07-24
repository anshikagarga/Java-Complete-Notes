# 📘 Chapter 08: Sorting Objects (Part 1)

> *"In real-world Java applications, we rarely sort primitive values. Most of the time, we sort objects such as Students, Employees, Products, Customers, and Orders. Java provides multiple ways to sort objects efficiently using Comparable and Comparator."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Object Sorting
- Learn why Object Sorting is needed
- Sort objects using Comparable
- Sort objects using Comparator
- Sort objects using Collections.sort()
- Sort objects using Arrays.sort()
- Understand Natural Ordering vs Custom Ordering

---

# 📚 Table of Contents

1. Introduction
2. Why Object Sorting?
3. Natural Ordering
4. Sorting Objects using Comparable
5. Sorting Objects using Comparator
6. Collections.sort()
7. Arrays.sort()
8. Internal Working
9. Best Practices
10. Common Mistakes

---

# 📖 What is Object Sorting?

Object Sorting means arranging objects according to one or more properties.

Example

Instead of sorting

```text
10

50

20

30
```

we sort

```text
Student

↓

Roll Number

↓

Marks

↓

Name
```

or

```text
Employee

↓

Salary

↓

Department

↓

Experience
```

---

# 💡 Why Do We Need Object Sorting?

Real-world applications store data as objects.

Examples

- Student Management System
- Banking System
- Hospital Management
- Employee Payroll
- E-Commerce Applications

Instead of sorting integers,

we sort objects.

---

# 📖 Example Class

```java
class Student{

    private int id;
    private String name;
    private int marks;

    public Student(int id, String name, int marks){

        this.id = id;
        this.name = name;
        this.marks = marks;

    }

    public int getId(){

        return id;

    }

    public String getName(){

        return name;

    }

    public int getMarks(){

        return marks;

    }

}
```

---

# 📖 Natural Ordering using Comparable

If a class implements Comparable,

Java automatically knows how to sort it.

Example

```java
class Student implements Comparable<Student>{

    private int id;

    @Override

    public int compareTo(Student s){

        return Integer.compare(this.id, s.id);

    }

}
```

Sorting

```java
Collections.sort(students);
```

Output

```text
Sorted by Student ID
```

---

# 📖 Sorting Objects using Comparable

Complete Example

```java
import java.util.*;

class Student implements Comparable<Student>{

    int id;
    String name;

    Student(int id, String name){

        this.id = id;
        this.name = name;

    }

    @Override

    public int compareTo(Student s){

        return Integer.compare(this.id, s.id);

    }

    @Override

    public String toString(){

        return id + " " + name;

    }

}

public class Demo{

    public static void main(String[] args){

        List<Student> students = new ArrayList<>();

        students.add(new Student(103,"Riya"));
        students.add(new Student(101,"Anshika"));
        students.add(new Student(102,"Aman"));

        Collections.sort(students);

        System.out.println(students);

    }

}
```

Output

```text
[101 Anshika, 102 Aman, 103 Riya]
```

---

# 📖 Sorting Objects using Comparator

Suppose we want to sort students by **marks** instead of **id**.

```java
students.sort(

Comparator.comparing(

Student::getMarks

)

);
```

Output

```text
Sorted by Marks
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

# 📖 Sorting by Name

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
```

---

# 📖 Collections.sort()

Collections.sort() is used for **List** objects.

Syntax

```java
Collections.sort(list);
```

or

```java
Collections.sort(

list,

Comparator.comparing(

Student::getMarks

)

);
```

---

# 📖 Arrays.sort()

Arrays.sort() is used for **arrays of objects**.

Example

```java
Student[] students = {

new Student(101,"Anshika",95),

new Student(102,"Riya",88),

new Student(103,"Aman",91)

};

Arrays.sort(

students,

Comparator.comparing(

Student::getMarks

)

);
```

Output

```text
Sorted Array of Objects
```

---

# 📦 Internal Working

```text
Objects

↓

Comparable / Comparator

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

# 📊 Comparable vs Comparator

| Comparable | Comparator |
|------------|------------|
| Natural Ordering | Custom Ordering |
| compareTo() | compare() |
| Inside Class | Outside Class |
| One Sorting Rule | Multiple Sorting Rules |

---

# 💡 Best Practices

- Use **Comparable** for natural ordering.
- Use **Comparator** for custom sorting.
- Prefer `Comparator.comparing()` over manual comparison logic.
- Override `toString()` for better output.
- Keep comparison logic simple and readable.

---

# ⚠️ Common Mistakes

## ❌ Forgetting Comparable

Wrong

```java
Collections.sort(students);
```

Compilation Error if `Student` does not implement `Comparable` and no `Comparator` is provided.

---

## ❌ Using Subtraction

Wrong

```java
return this.id - s.id;
```

Correct

```java
return Integer.compare(

this.id,

s.id

);
```

---

## ❌ Not Overriding toString()

Wrong Output

```text
Student@4a54c0de
```

Correct

```text
101 Anshika
102 Aman
103 Riya
```

Override

```java
@Override
public String toString(){

    return id + " " + name;

}
```

---

# 🌍 Real-World Applications

Sorting Objects is used in:

- Employee Payroll Systems
- Student Result Management
- Banking Applications
- E-Commerce Product Listings
- Airline Reservation Systems
- Hospital Management
- Library Management
- Spring Boot REST APIs

---

# 🎯 Interview Tip

### Question

When should you use Comparable and when should you use Comparator for sorting objects?

### Answer

- Use **Comparable** when there is **one natural ordering** (e.g., sort students by ID).
- Use **Comparator** when multiple sorting rules are required (e.g., by marks, name, salary, or department).

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Sorting by Multiple Fields
- Comparator Chaining
- Lambda Expressions
- Method References
- Sorting Lists and Arrays
- Advanced Object Sorting Examples
# 📘 Chapter 06: Lambda with Comparator (Part 2)

> *"Java 8 made Comparator much more powerful by introducing utility methods like `comparing()`, `thenComparing()`, `reversed()`, `nullsFirst()`, and `nullsLast()`. These methods make sorting objects simple, readable, and reusable."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Use `Comparator.comparing()`
- Learn `thenComparing()`
- Reverse sorting using `reversed()`
- Handle null values using `nullsFirst()` and `nullsLast()`
- Sort objects using Lambda
- Use Method References with Comparator

---

# 📚 Table of Contents

1. Comparator.comparing()
2. Sorting Objects
3. thenComparing()
4. reversed()
5. nullsFirst()
6. nullsLast()
7. Method References
8. Internal Working
9. Best Practices
10. Common Mistakes

---

# 📖 Comparator.comparing()

Instead of writing

```java
(a, b) -> a.getAge() - b.getAge()
```

Java 8 provides

```java
Comparator.comparing()
```

which makes the code more readable.

Syntax

```java
Comparator.comparing(Class::getterMethod)
```

---

# 📖 Example

```java
class Student{

    private int age;

    public Student(int age){

        this.age = age;

    }

    public int getAge(){

        return age;

    }

}
```

Sorting

```java
students.sort(

Comparator.comparing(Student::getAge)

);
```

Output

```text
Sorted by Age
```

---

# 📖 Sorting by Name

```java
class Employee{

    String name;

    Employee(String name){

        this.name = name;

    }

    public String getName(){

        return name;

    }

}
```

```java
employees.sort(

Comparator.comparing(Employee::getName)

);
```

Output

```text
Employees Sorted Alphabetically
```

---

# 📖 thenComparing()

Sometimes one field is not enough.

Example

Sort by Department first,

then by Salary.

```java
employees.sort(

Comparator

.comparing(Employee::getDepartment)

.thenComparing(Employee::getSalary)

);
```

Sorting Order

```text
Department

↓

Salary
```

---

# 📖 Example

```java
class Student{

    int marks;

    String name;

}
```

```java
students.sort(

Comparator

.comparing(Student::getMarks)

.thenComparing(Student::getName)

);
```

Output

```text
Sorted by Marks

↓

If Marks Same

↓

Sorted by Name
```

---

# 📖 reversed()

Reverse any Comparator.

Example

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

# 📖 Combining thenComparing() and reversed()

```java
students.sort(

Comparator

.comparing(Student::getDepartment)

.thenComparing(

Comparator

.comparing(Student::getMarks)

.reversed()

)

);
```

Meaning

```text
Department

↓

Marks (Descending)
```

---

# 📖 nullsFirst()

Sometimes collections contain null values.

Without handling,

```java
Collections.sort(list);
```

may throw a

```text
NullPointerException
```

Use

```java
Comparator.nullsFirst()
```

Example

```java
List<String> list =

Arrays.asList(

"Java",

null,

"Python",

"C"

);

list.sort(

Comparator.nullsFirst(

String::compareTo

)

);

System.out.println(list);
```

Output

```text
[null, C, Java, Python]
```

---

# 📖 nullsLast()

Places null values at the end.

Example

```java
list.sort(

Comparator.nullsLast(

String::compareTo

)

);
```

Output

```text
[C, Java, Python, null]
```

---

# 📖 Method References with Comparator

Instead of

```java
(a,b) ->

a.getName().compareTo(

b.getName()

)
```

Use

```java
Comparator.comparing(

Student::getName

)
```

Much cleaner.

---

# 📖 Sorting Strings by Length

Example

```java
List<String> list =

Arrays.asList(

"Java",

"Python",

"C",

"Spring"

);

list.sort(

Comparator.comparing(

String::length

)

);

System.out.println(list);
```

Output

```text
[C, Java, Python, Spring]
```

---

# 📖 Sorting Ignoring Case

```java
List<String> names =

Arrays.asList(

"java",

"Python",

"c",

"HTML"

);

names.sort(

String.CASE_INSENSITIVE_ORDER

);

System.out.println(names);
```

Output

```text
[c, HTML, java, Python]
```

---

# 📦 Internal Working

```text
Collection

↓

Comparator.comparing()

↓

Lambda / Method Reference

↓

Comparator Object

↓

Sorting Algorithm

↓

Sorted Collection
```

---

# 💡 Best Practices

- Prefer `Comparator.comparing()` over manually writing comparison logic.
- Use `thenComparing()` for multi-level sorting.
- Use `reversed()` instead of rewriting comparison logic.
- Handle possible null values using `nullsFirst()` or `nullsLast()`.
- Prefer Method References (`Class::method`) whenever they improve readability.
- Use `Integer.compare()` instead of subtraction when comparing integers manually.

---

# ⚠️ Common Mistakes

## ❌ Using Subtraction for Integer Comparison

Wrong

```java
(a,b) ->

a.getAge() - b.getAge()
```

Correct

```java
Comparator.comparing(

Student::getAge
)
```

or

```java
(a,b) ->

Integer.compare(

a.getAge(),

b.getAge()

)
```

---

## ❌ Forgetting thenComparing()

Wrong

```java
Comparator.comparing(

Student::getMarks
)
```

Students with equal marks remain unordered.

Correct

```java
Comparator

.comparing(Student::getMarks)

.thenComparing(Student::getName)
```

---

## ❌ Not Handling Null Values

Wrong

```java
Collections.sort(list);
```

Correct

```java
list.sort(

Comparator.nullsLast(

String::compareTo

)

);
```

---

# 🌍 Real-World Applications

These Comparator features are widely used in:

- Employee Management Systems
- Student Result Portals
- Banking Applications
- Flight Booking Systems
- Hospital Management
- HR Software
- E-commerce Product Sorting
- Spring Boot REST APIs

---

# 🎯 Interview Tip

### Question

What is the advantage of `Comparator.comparing()` over writing the compare() method manually?

### Answer

`Comparator.comparing()` creates Comparators in a concise and readable way using method references or lambda expressions. It reduces boilerplate code, improves maintainability, and can be easily combined with methods like `thenComparing()`, `reversed()`, `nullsFirst()`, and `nullsLast()`.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Interview Questions
- MCQs
- Coding Practice
- Best Practices Revision
- Chapter Summary
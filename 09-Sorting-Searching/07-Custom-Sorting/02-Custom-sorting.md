# 📘 Chapter 07: Custom Sorting (Part 2)

> *"Real-world applications rarely sort data using a single field. Java provides powerful Comparator methods to perform multi-level sorting, object sorting, array sorting, and even map sorting with minimal code."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Perform Multi-Level Sorting
- Chain Comparators
- Sort Objects using Lambda
- Sort Arrays of Objects
- Sort Maps
- Sort by Multiple Fields
- Learn Advanced Custom Sorting Techniques

---

# 📚 Table of Contents

1. Multi-Level Sorting
2. Comparator Chaining
3. Sorting using Lambda
4. Sorting Arrays of Objects
5. Sorting Maps
6. Advanced Examples
7. Internal Working
8. Best Practices
9. Common Mistakes
10. Interview Tips

---

# 📖 Multi-Level Sorting

Sometimes sorting based on one field is not enough.

Example

```text
Department

↓

Salary

↓

Name
```

If two employees belong to the same department,

then sort them by salary.

If salary is also same,

sort by name.

---

# 📖 Example

```java
employees.sort(

Comparator

.comparing(Employee::getDepartment)

.thenComparing(Employee::getSalary)

.thenComparing(Employee::getName)

);
```

Output

```text
HR

↓

Salary

↓

Name

IT

↓

Salary

↓

Name
```

---

# 📖 Comparator Chaining

Comparator methods can be chained together.

Example

```java
Comparator<Employee> cmp =

Comparator

.comparing(Employee::getDepartment)

.thenComparing(Employee::getSalary)

.thenComparing(Employee::getName);

employees.sort(cmp);
```

Advantages

- Cleaner Code
- Reusable Comparator
- Easy Maintenance

---

# 📖 Sorting using Lambda

Instead of creating a separate Comparator class,

Java 8 allows sorting using Lambda.

Example

```java
employees.sort(

(a,b) ->

Integer.compare(

a.getSalary(),

b.getSalary()

)

);
```

Descending

```java
employees.sort(

(a,b) ->

Integer.compare(

b.getSalary(),

a.getSalary()

)

);
```

---

# 📖 Sorting Arrays of Objects

Suppose

```java
Employee[] employees = {

new Employee(101,"Anshika",80000),

new Employee(102,"Riya",50000),

new Employee(103,"Aman",65000)

};
```

Sort by Salary

```java
Arrays.sort(

employees,

Comparator.comparing(Employee::getSalary)

);
```

Descending

```java
Arrays.sort(

employees,

Comparator

.comparing(Employee::getSalary)

.reversed()

);
```

---

# 📖 Sorting by Multiple Fields

Example

```java
students.sort(

Comparator

.comparing(Student::getMarks)

.thenComparing(Student::getName)

);
```

Meaning

```text
Marks

↓

If Same

↓

Name
```

---

# 📖 Sorting Maps

Suppose

```java
Map<String,Integer> map =

new HashMap<>();

map.put("Java",95);

map.put("Python",80);

map.put("C++",90);
```

Sort by Key

```java
map.entrySet()

.stream()

.sorted(Map.Entry.comparingByKey())

.forEach(System.out::println);
```

Output

```text
C++=90

Java=95

Python=80
```

---

# 📖 Sort Map by Value

```java
map.entrySet()

.stream()

.sorted(

Map.Entry.comparingByValue()

)

.forEach(System.out::println);
```

Output

```text
Python=80

C++=90

Java=95
```

---

# 📖 Advanced Example

Sort Employees

Priority

```text
Department

↓

Salary (Descending)

↓

Experience

↓

Name
```

Program

```java
employees.sort(

Comparator

.comparing(Employee::getDepartment)

.thenComparing(

Comparator

.comparing(Employee::getSalary)

.reversed()

)

.thenComparing(Employee::getExperience)

.thenComparing(Employee::getName)

);
```

---

# 📖 Sorting Strings by Length

```java
List<String> list =

Arrays.asList(

"Java",

"SpringBoot",

"C",

"Python"

);

list.sort(

Comparator.comparingInt(

String::length

)

);
```

Output

```text
[C, Java, Python, SpringBoot]
```

---

# 📖 Sorting Ignoring Case

```java
List<String> names =

Arrays.asList(

"java",

"HTML",

"Python",

"css"

);

names.sort(

String.CASE_INSENSITIVE_ORDER

);
```

Output

```text
[css, HTML, java, Python]
```

---

# 📦 Internal Working

```text
Collection

↓

Comparator

↓

Lambda / Method Reference

↓

Comparison Logic

↓

Sorting Algorithm

↓

Sorted Data
```

---

# 💡 Best Practices

- Use `Comparator.comparing()` for object fields.
- Use `thenComparing()` for secondary sorting.
- Use `comparingInt()`, `comparingDouble()`, and `comparingLong()` for primitive fields.
- Store reusable Comparator objects in variables.
- Use Method References instead of lengthy Lambda expressions whenever possible.

---

# ⚠️ Common Mistakes

## ❌ Forgetting Secondary Sorting

Wrong

```java
Comparator.comparing(

Employee::getDepartment

);
```

Employees in the same department remain unordered.

Correct

```java
Comparator

.comparing(Employee::getDepartment)

.thenComparing(Employee::getSalary);
```

---

## ❌ Using a-b for Comparison

Wrong

```java
(a,b)->

a.getSalary()-b.getSalary();
```

Correct

```java
Integer.compare(

a.getSalary(),

b.getSalary()

);
```

---

## ❌ Writing Large Lambda Expressions

Wrong

```java
(a,b)->{

if(a.getMarks()>b.getMarks())

return 1;

else

return -1;

}
```

Correct

```java
Comparator.comparing(

Student::getMarks

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

Multi-level Custom Sorting is used in:

- Banking Systems
- Employee Payroll
- HR Management
- Student Ranking Systems
- E-Commerce Websites
- Flight Booking Systems
- Hospital Management
- Logistics Platforms
- Spring Boot REST APIs
- Financial Applications

---

# 🎯 Interview Tip

### Question

How do you sort employees by department, then salary (descending), and finally by name?

### Answer

```java
employees.sort(

Comparator

.comparing(Employee::getDepartment)

.thenComparing(

Comparator

.comparing(Employee::getSalary)

.reversed()

)

.thenComparing(Employee::getName)

);
```

This performs **multi-level sorting** using Comparator chaining.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Interview Questions
- MCQs
- Coding Practice
- Best Practices Revision
- Chapter Summary
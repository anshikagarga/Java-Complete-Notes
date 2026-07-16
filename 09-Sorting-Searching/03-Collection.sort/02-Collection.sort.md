# 📘 Chapter 03: Collections.sort() (Part 2)

## Sorting Custom Objects, Comparable & Comparator

> *"`Collections.sort()` becomes even more powerful when working with custom objects. By combining it with Comparable and Comparator, Java allows us to sort objects in different ways with minimal code."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Sort custom objects using Collections.sort().
- Use Comparable with Collections.sort().
- Use Comparator with Collections.sort().
- Sort objects in ascending and descending order.
- Understand the internal working.
- Learn common mistakes and best practices.

---

# 📚 Table of Contents

1. Sorting Custom Objects
2. Collections.sort() with Comparable
3. Collections.sort() with Comparator
4. Sorting in Descending Order
5. Internal Working
6. Common Mistakes
7. Best Practices

---

# 📖 Sorting Custom Objects

Suppose we have a Student class.

```java
class Student{

    int rollNo;
    String name;
    double marks;

}
```

Can Java sort this list?

```java
ArrayList<Student> list = new ArrayList<>();

Collections.sort(list);
```

❌ No.

Reason

Java does not know

- which field to compare
- roll number?
- name?
- marks?

Therefore,

we need either

- Comparable
- Comparator

---

# 📖 Using Comparable

Suppose

```java
class Student implements Comparable<Student>{

    int rollNo;
    String name;

    Student(int rollNo,String name){

        this.rollNo = rollNo;
        this.name = name;

    }

    @Override
    public int compareTo(Student other){

        return Integer.compare(this.rollNo, other.rollNo);

    }

}
```

Now

```java
ArrayList<Student> list = new ArrayList<>();

list.add(new Student(103,"Anshika"));
list.add(new Student(101,"Riya"));
list.add(new Student(102,"Karan"));

Collections.sort(list);
```

Output

```text
101 Riya

102 Karan

103 Anshika
```

Collections.sort() automatically calls

```java
compareTo()
```

---

# 📖 Using Comparator

Suppose

```java
class NameComparator implements Comparator<Student>{

    @Override
    public int compare(Student s1, Student s2){

        return s1.name.compareTo(s2.name);

    }

}
```

Now

```java
Collections.sort(

    list,

    new NameComparator()

);
```

Output

```text
Anshika

Karan

Riya
```

Collections.sort() now calls

```java
compare()
```

instead of

```java
compareTo()
```

---

# 📖 Sorting by Marks

```java
class MarksComparator implements Comparator<Student>{

    @Override
    public int compare(Student s1, Student s2){

        return Double.compare(

            s1.marks,

            s2.marks

        );

    }

}
```

Usage

```java
Collections.sort(

    list,

    new MarksComparator()

);
```

Output

```text
72.5

81.3

90.4

95.8
```

---

# 📖 Descending Order using Comparator

Ascending

```java
return Integer.compare(s1.rollNo, s2.rollNo);
```

Descending

```java
return Integer.compare(s2.rollNo, s1.rollNo);
```

Output

```text
105

104

103

102

101
```

---

# 📖 Descending Order using reverseOrder()

```java
Collections.sort(

    list,

    Collections.reverseOrder()

);
```

Works only if the objects implement

```java
Comparable
```

because `reverseOrder()` reverses the natural ordering.

---

# 📖 Java 8 Lambda Example

Instead of creating a Comparator class,

we can use Lambda Expressions.

```java
Collections.sort(

    list,

    (s1, s2) -> Integer.compare(

        s1.rollNo,

        s2.rollNo

    )

);
```

Cleaner and shorter.

---

# 📖 Java 8 Method Reference

```java
Collections.sort(

    list,

    Comparator.comparing(Student::getName)

);
```

Sorts students alphabetically by name.

---

# 📖 Comparator Chaining

Suppose

First

Sort by Marks

If marks are equal

↓

Sort by Name

```java
Collections.sort(

    list,

    Comparator

        .comparingDouble(Student::getMarks)

        .thenComparing(Student::getName)

);
```

Output

```text
72.5 Aman

72.5 Riya

90.3 Anshika

95.8 Karan
```

---

# 🧠 Internal Working

### Case 1

```java
Collections.sort(list);
```

```text
Collections.sort()

↓

compareTo()

↓

Compare Objects

↓

Sort List
```

---

### Case 2

```java
Collections.sort(list, comparator);
```

```text
Collections.sort()

↓

compare()

↓

Compare Objects

↓

Sort List
```

---

# 📦 Memory Diagram

Before Sorting

```text
103

101

102
```

↓

Collections.sort()

↓

compareTo()

↓

After Sorting

```text
101

102

103
```

---

Comparator Example

```text
Riya

Anshika

Karan
```

↓

Name Comparator

↓

```text
Anshika

Karan

Riya
```

---

# ⚠️ Common Mistakes

## ❌ Forgetting Comparable

Wrong

```java
Collections.sort(list);
```

when Student does not implement Comparable.

Result

```text
ClassCastException
```

---

## ❌ Returning Boolean

Wrong

```java
return s1.id > s2.id;
```

Correct

```java
return Integer.compare(

    s1.id,

    s2.id

);
```

---

## ❌ Comparing Strings Using '-'

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

Better

```java
return Integer.compare(

    s1.salary,

    s2.salary

);
```

---

## ❌ Ignoring Null Values

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

# 💡 Best Practices

- Use Comparable for one default sorting order.
- Use Comparator for multiple sorting criteria.
- Prefer `Integer.compare()` over subtraction.
- Use `Comparator.comparing()` in Java 8+.
- Prefer Lambda Expressions and Method References.
- Use `thenComparing()` for secondary sorting.
- Keep Comparator classes reusable.

---

# 🌍 Real-World Applications

Collections.sort() is widely used for sorting:

- Student Records
- Employee Lists
- Product Catalogs
- Customer Information
- Orders
- Books
- Movies
- Banking Transactions

---

# 🎯 Interview Tip

### Question

When should we use Comparable and when should we use Comparator with `Collections.sort()`?

### Answer

Use **Comparable** when the class has a single natural ordering (such as sorting employees by ID). Use **Comparator** when multiple sorting criteria are required (such as sorting students by name, marks, or roll number). `Collections.sort()` can work with both approaches depending on the method overload used.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Collections.sort() vs Arrays.sort()
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision
- Chapter Summary
- Frequently Asked Interview Questions
# 📘 Chapter 5: Comparator Interface (Part 1)

> *"The Comparator interface allows us to define custom sorting logic without modifying the original class. It is the preferred approach when objects need to be sorted in multiple different ways."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Comparator Interface.
- Learn why Comparator is needed.
- Understand Custom Ordering.
- Implement Comparator in Java.
- Learn how `Collections.sort()` uses Comparator.
- Analyze Time Complexity.
- Understand when to use Comparator instead of Comparable.

---

# 📚 Table of Contents

1. What is Comparator?
2. Why Comparator?
3. Custom Ordering
4. Comparator Interface
5. compare() Method
6. Internal Working
7. Java Implementation
8. Time Complexity
9. Advantages
10. Limitations

---

# 🤔 Why Do We Need Comparator?

Suppose we have a `Student` class.

```java
class Student {

    int rollNo;
    String name;
    double marks;

}
```

Now suppose we want to sort students by

- Roll Number
- Name
- Marks
- Age

Can Comparable do this?

❌ No.

Comparable allows only **one natural ordering**.

To support multiple sorting orders, Java provides the **Comparator Interface**.

---

# 📖 What is Comparator?

Comparator is a predefined interface present in Java.

Package

```java
java.util
```

It allows us to define **custom sorting logic**.

Unlike Comparable,

Comparator does **not** require modifying the original class.

---

# 📖 Custom Ordering

Custom Ordering means choosing the sorting order according to the application's requirement.

Example

Student

```text
↓

Sort by Name
```

or

```text
↓

Sort by Marks
```

or

```text
↓

Sort by Roll Number
```

Each sorting rule can have its own Comparator.

---

# 📖 Comparator Interface Syntax

```java
public interface Comparator<T>{

    int compare(T o1, T o2);

}
```

It contains one abstract method.

```java
compare()
```

---

# 📖 What is compare()?

The `compare()` method compares **two different objects**.

Syntax

```java
public int compare(Student s1, Student s2)
```

Unlike Comparable,

we compare

```text
Object 1

↓

Object 2
```

instead of

```text
this

↓

other
```

---

# 📊 Return Values

If

```text
Object1 < Object2
```

Return

```text
Negative Value
```

---

If

```text
Object1 == Object2
```

Return

```text
0
```

---

If

```text
Object1 > Object2
```

Return

```text
Positive Value
```

---

# 📊 compare() Flow

```text
Object 1

↓

compare()

↓

Object 2

↓

Negative

↓

Object 1 First

----------------------

Zero

↓

Equal

----------------------

Positive

↓

Object 2 First
```

---

# 📖 How Comparator Works Internally

Suppose

```java
Collections.sort(list, comparator);
```

Java internally performs something similar to

```java
comparator.compare(obj1, obj2);
```

If

```text
Negative
```

↓

Keep order.

If

```text
Positive
```

↓

Swap objects.

Java keeps comparing objects until the list becomes sorted.

---

# 💻 Java Example

```java
import java.util.*;

class Student{

    int rollNo;
    String name;

    Student(int rollNo, String name){

        this.rollNo = rollNo;
        this.name = name;

    }

}

class RollComparator implements Comparator<Student>{

    @Override
    public int compare(Student s1, Student s2){

        return Integer.compare(s1.rollNo, s2.rollNo);

    }

}
```

---

Now

```java
ArrayList<Student> list = new ArrayList<>();

list.add(new Student(103,"Anshika"));
list.add(new Student(101,"Riya"));
list.add(new Student(102,"Karan"));

Collections.sort(list, new RollComparator());
```

---

Output

```text
101 Riya

102 Karan

103 Anshika
```

---

# 🧠 Internal Working

```text
Collections.sort()

↓

Comparator.compare()

↓

Compare Two Objects

↓

Negative

↓

Keep Order

----------------------

Positive

↓

Swap

↓

Repeat

↓

Sorted List
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

compare()

↓

After Sorting

```text
101

102

103
```

---

# ⚡ Time Complexity

Comparator itself does not perform sorting.

The complexity depends on the sorting algorithm used.

| Method | Time Complexity |
|---------|-----------------|
| Collections.sort() | O(n log n) |
| List.sort() | O(n log n) |

---

# ✅ Advantages

- Supports multiple sorting criteria.
- Does not modify the original class.
- Easy to maintain.
- Supports Lambda Expressions.
- Supports Method References.
- Preferred in modern Java.

---

# ⚠️ Limitations

- Requires an additional Comparator class or Lambda.
- Slightly more code than Comparable (before Java 8).
- Multiple Comparators may increase project complexity if not organized well.

---

# 🌍 Real-World Applications

Comparator is commonly used for sorting:

- Students by Marks.
- Students by Name.
- Employees by Salary.
- Employees by Experience.
- Products by Price.
- Products by Rating.
- Files by Size.
- Movies by Release Date.

---

# 🎯 Interview Tip

### Question

Why should we use Comparator instead of Comparable?

### Answer

Use **Comparator** when you need **multiple sorting orders** or when you cannot modify the original class. Comparator keeps the sorting logic separate from the model class, making the code more flexible, reusable, and easier to maintain.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Sorting by Different Fields
- Multiple Comparator Classes
- Comparator Utility Methods
- Java 8 Comparator Features
- Chaining Comparators
- Common Mistakes
- Best Practices
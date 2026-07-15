# 📘 Chapter 4: Comparable Interface (Part 1)

> *"The Comparable interface allows objects of a class to define their own natural ordering. It is the default way of sorting custom objects in Java."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Comparable Interface.
- Learn why Comparable is needed.
- Understand Natural Ordering.
- Implement Comparable in Java.
- Learn how Collections.sort() uses Comparable.
- Analyze Time Complexity.
- Understand when to use Comparable.

---

# 📚 Table of Contents

1. What is Comparable?
2. Why Comparable?
3. Natural Ordering
4. Comparable Interface
5. compareTo() Method
6. Internal Working
7. Java Implementation
8. Time Complexity
9. Advantages
10. Limitations

---

# 🤔 Why Do We Need Comparable?

Primitive data types can easily be sorted.

Example

```java
int[] arr = {5, 2, 8, 1};
Arrays.sort(arr);
```

Output

```text
1 2 5 8
```

---

But what about custom objects?

Example

```java
class Student {

    int id;
    String name;
    double marks;

}
```

Now suppose we have

```java
Student s1 = new Student(101, "Anshika", 95.5);
Student s2 = new Student(102, "Riya", 88.2);
Student s3 = new Student(103, "Karan", 91.4);
```

How will Java know whether to sort students by

- ID
- Name
- Marks

Java doesn't know.

That's why Comparable exists.

---

# 📖 What is Comparable?

Comparable is a predefined interface present in Java.

Package

```java
java.lang
```

It allows an object to define its **Natural Ordering**.

---

# 📖 Natural Ordering

Natural Ordering means

the **default order** in which objects should be sorted.

Examples

For Integers

```text
1 2 3 4 5
```

Ascending Order

---

For Strings

```text
Apple

Banana

Cat

Dog
```

Alphabetical Order

---

For Students

You decide the natural order.

For example

```text
Sort by Roll Number
```

or

```text
Sort by Marks
```

Only one default order can be defined using Comparable.

---

# 📖 Comparable Interface Syntax

```java
public interface Comparable<T> {

    int compareTo(T obj);

}
```

It contains only one method

```java
compareTo()
```

---

# 📖 What is compareTo()?

The `compareTo()` method compares the current object with another object.

Syntax

```java
public int compareTo(Student other)
```

---

### Return Values

If

```text
Current < Other
```

Return

```text
Negative Value
```

Usually

```java
return -1;
```

---

If

```text
Current == Other
```

Return

```text
0
```

---

If

```text
Current > Other
```

Return

```text
Positive Value
```

Usually

```java
return 1;
```

---

# 📊 compareTo() Flow

```text
Current Object

↓

compareTo()

↓

Compare with Other Object

↓

Negative

↓

Current Comes First

----------------------------

Zero

↓

Both Equal

----------------------------

Positive

↓

Other Comes First
```

---

# 📖 How Comparable Works Internally

Suppose

```java
Collections.sort(list);
```

Java internally performs something similar to

```java
obj1.compareTo(obj2);
```

If

```java
compareTo()

↓

Negative
```

No Swap

---

If

```java
compareTo()

↓

Positive
```

Swap Objects

---

Java keeps comparing objects until the collection becomes sorted.

---

# 💻 Java Example

```java
class Student implements Comparable<Student>{

    int rollNo;
    String name;

    Student(int rollNo, String name){

        this.rollNo = rollNo;
        this.name = name;

    }

    @Override
    public int compareTo(Student other){

        return this.rollNo - other.rollNo;

    }

}
```

---

Now create a list

```java
ArrayList<Student> list = new ArrayList<>();

list.add(new Student(103, "Anshika"));
list.add(new Student(101, "Riya"));
list.add(new Student(102, "Karan"));

Collections.sort(list);
```

---

Output

```text
101 Riya

102 Karan

103 Anshika
```

Objects are sorted according to Roll Number.

---

# 🧠 Internal Working

```text
Collections.sort()

↓

compareTo()

↓

Compare Objects

↓

Swap if Needed

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

compareTo()

↓

After Sorting

```text
101

102

103
```

---

# ⚡ Time Complexity

The Comparable interface itself does not define a sorting algorithm.

The complexity depends on the sorting method used.

| Method | Time Complexity |
|---------|-----------------|
| Collections.sort() | O(n log n) |
| Arrays.sort() (Objects) | O(n log n) |

---

# ✅ Advantages

- Easy to implement.
- Defines a default sorting order.
- Automatically works with `Collections.sort()`.
- Automatically works with `Arrays.sort()`.
- Widely used in Java projects.

---

# ⚠️ Limitations

- Only one natural ordering can be defined.
- Cannot easily switch between multiple sorting criteria.
- Modifying the sorting logic requires changing the class itself.

---

# 🌍 Real-World Applications

Comparable is commonly used for sorting:

- Students by Roll Number.
- Employees by Employee ID.
- Products by Product ID.
- Books by ISBN.
- Files by Name.
- Dates in chronological order.

---

# 🎯 Interview Tip

### Question

Why do we implement Comparable?

### Answer

The Comparable interface allows a class to define its **natural (default) ordering** by implementing the `compareTo()` method. Once implemented, Java's built-in sorting methods like `Collections.sort()` and `Arrays.sort()` can automatically sort objects of that class.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- compareTo() in Detail
- Sorting by Different Fields
- Rules of compareTo()
- Internal Working of Collections.sort()
- Common Mistakes
- Best Practices
- Comparable vs Comparator (Introduction)
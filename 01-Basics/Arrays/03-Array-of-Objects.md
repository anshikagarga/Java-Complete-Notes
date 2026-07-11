# 📚 Array of Objects in Java

An **Array of Objects** is an array that stores **references to objects** instead of primitive values.

Unlike primitive arrays (`int[]`, `double[]`), each element in an object array points to an object stored in memory.

---

# Why do we need an Array of Objects?

Suppose we want to store information about multiple students.

Without an array:

```java
Student s1 = new Student();
Student s2 = new Student();
Student s3 = new Student();
```

Managing many objects individually becomes difficult.

Instead, we can store them inside an array.

```java
Student[] students = new Student[3];
```

Now all student references are stored in a single array.

---

# Step 1: Create the Student Class

```java
class Student {

    int rollNo;
    String name;
    int marks;

}
```

---

# Step 2: Create Student Objects

```java
Student s1 = new Student();

s1.rollNo = 1;
s1.name = "Navin";
s1.marks = 88;
```

Another object

```java
Student s2 = new Student();

s2.rollNo = 2;
s2.name = "Harsh";
s2.marks = 67;
```

Another object

```java
Student s3 = new Student();

s3.rollNo = 3;
s3.name = "Kiran";
s3.marks = 97;
```

---

# Step 3: Create an Array of Objects

```java
Student[] students = new Student[3];
```

At this point,

```
students[0] → null
students[1] → null
students[2] → null
```

The array contains **null references**, not actual Student objects.

---

# Step 4: Store Objects in the Array

```java
students[0] = s1;
students[1] = s2;
students[2] = s3;
```

Memory Representation

```
students
+-------+      +----------------------+
|   ●---|----->| Student (Navin)      |
+-------+      +----------------------+
|   ●---|----->| Student (Harsh)      |
+-------+      +----------------------+
|   ●---|----->| Student (Kiran)      |
+-------+      +----------------------+
```

The array stores **references**, not the objects themselves.

---

# Accessing Object Data

```java
System.out.println(students[0].name);
System.out.println(students[0].marks);
```

Output

```
Navin
88
```

---

# Printing All Student Details

Using a normal for loop

```java
for(int i = 0; i < students.length; i++)
{
    System.out.println(
        students[i].rollNo + " " +
        students[i].name + " " +
        students[i].marks
    );
}
```

Output

```
1 Navin 88
2 Harsh 67
3 Kiran 97
```

---

# Using Enhanced For Loop

```java
for(Student student : students)
{
    System.out.println(
        student.rollNo + " " +
        student.name + " " +
        student.marks
    );
}
```

Output

```
1 Navin 88
2 Harsh 67
3 Kiran 97
```

---

# Memory Representation

```
Heap Memory

Student Object
---------------
rollNo = 1
name = "Navin"
marks = 88

Student Object
---------------
rollNo = 2
name = "Harsh"
marks = 67

Student Object
---------------
rollNo = 3
name = "Kiran"
marks = 97


students Array

Index
0 -----> s1
1 -----> s2
2 -----> s3
```

---

# Important Note

Creating an object array

```java
Student[] students = new Student[3];
```

**does not create Student objects.**

It only creates space to store references.

You still need to create each object.

```java
students[0] = new Student();
students[1] = new Student();
students[2] = new Student();
```

---

# Common Mistake

```java
Student[] students = new Student[3];

System.out.println(students[0].name);
```

Output

```
NullPointerException
```

Why?

Because `students[0]` is still `null`.

Always create an object before accessing its fields.

---

# Advantages

- Stores multiple objects together.
- Easy to iterate over objects.
- Cleaner and more organized code.
- Useful for managing collections of similar objects.

---

# Disadvantages

- Fixed size.
- Stores references instead of actual objects.
- Can cause `NullPointerException` if objects are not initialized.

---

# Time Complexity

| Operation | Complexity |
|-----------|------------|
| Access an Object | O(1) |
| Update | O(1) |
| Traversal | O(n) |

---

# Interview Questions

## 1. What is an Array of Objects?

An array of objects stores **references to objects** instead of primitive values.

---

## 2. Does `new Student[5]` create five Student objects?

No.

It only creates an array capable of storing five references.

Each object must be created separately.

---

## 3. Where are objects stored?

Objects are stored in **Heap Memory**, while the array stores their references.

---

## 4. Why do we get `NullPointerException`?

Because object references are `null` until actual objects are created.

---

# Key Takeaways

- Arrays can store object references.
- Objects must be created separately using `new`.
- Enhanced for loops simplify traversal.
- Arrays store references, not the actual objects.
- Accessing a `null` reference causes `NullPointerException`.
# 📘 Chapter 17: Array of Objects (Part 1)

> *"An Array of Objects is an array where each element stores the reference of an object instead of a primitive value. It is one of the most important concepts in Object-Oriented Programming and is widely used in real-world Java applications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what an Array of Objects is.
- Learn why we use Arrays of Objects.
- Differentiate between Primitive Arrays and Object Arrays.
- Create and initialize Arrays of Objects.
- Access object data using arrays.
- Understand the internal memory representation.
- Learn real-world applications.

---

# 📚 Table of Contents

1. What is an Array of Objects?
2. Why Do We Need It?
3. Primitive Array vs Object Array
4. Declaring an Array of Objects
5. Creating Objects
6. Accessing Objects
7. Internal Memory Representation
8. Advantages
9. Limitations
10. Real-World Applications

---

# 🤔 What is an Array of Objects?

An **Array of Objects** is an array whose elements are references to objects instead of primitive values.

Instead of storing

```java
10
20
30
```

it stores

```text
Student Object

↓

Student Object

↓

Student Object
```

Each element points to an object in memory.

---

# 💡 Why Do We Need an Array of Objects?

Suppose you want to store information about 100 students.

Each student has

- Roll Number
- Name
- Marks

Using separate arrays

```java
int[] rollNo;
String[] name;
double[] marks;
```

is difficult to manage.

Instead,

create a Student class

```java
class Student{

    int rollNo;
    String name;
    double marks;

}
```

Then

```java
Student[] students = new Student[100];
```

Now each element stores a Student object.

---

# 📊 Primitive Array vs Object Array

| Primitive Array | Object Array |
|-----------------|--------------|
| Stores primitive values | Stores object references |
| Faster | Slightly slower |
| Less memory | More memory |
| Cannot store methods | Can access object methods |
| Example: `int[]` | Example: `Student[]` |

---

# 📖 Declaring an Array of Objects

Syntax

```java
ClassName[] arrayName = new ClassName[size];
```

Example

```java
Student[] students = new Student[3];
```

At this point,

**no Student objects are created.**

Only an array capable of holding **3 references** is created.

---

# 📦 Memory Representation

```text
students

↓

+---------+---------+---------+
|  null   |  null   |  null   |
+---------+---------+---------+
```

Initially,

all elements contain

```text
null
```

because no objects exist yet.

---

# 📖 Creating Objects

Each object must be created separately.

```java
students[0] = new Student();
students[1] = new Student();
students[2] = new Student();
```

Now memory becomes

```text
students

↓

+-------+-------+-------+

↓

↓

↓

Student Student Student
```

Each array element stores the reference of a Student object.

---

# 💻 Example

```java
class Student{

    int rollNo;
    String name;

}

public class Demo{

    public static void main(String[] args){

        Student[] students = new Student[2];

        students[0] = new Student();
        students[1] = new Student();

        students[0].rollNo = 101;
        students[0].name = "Anshika";

        students[1].rollNo = 102;
        students[1].name = "Riya";

        System.out.println(students[0].name);
        System.out.println(students[1].name);

    }

}
```

Output

```text
Anshika

Riya
```

---

# 📖 Creating Objects Using Constructor

```java
class Student{

    int rollNo;
    String name;

    Student(int rollNo,String name){

        this.rollNo = rollNo;
        this.name = name;

    }

}
```

Now

```java
Student[] students = new Student[3];

students[0] = new Student(101,"Anshika");
students[1] = new Student(102,"Riya");
students[2] = new Student(103,"Karan");
```

---

# 📖 Accessing Object Data

```java
System.out.println(students[0].rollNo);

System.out.println(students[1].name);
```

Output

```text
101

Riya
```

---

# 📖 Traversing an Array of Objects

Using a normal for loop

```java
for(int i = 0; i < students.length; i++){

    System.out.println(students[i].name);

}
```

---

Using an enhanced for loop

```java
for(Student s : students){

    System.out.println(s.name);

}
```

Output

```text
Anshika

Riya

Karan
```

---

# 📦 Complete Memory Diagram

```text
students

↓

+-------+-------+-------+

↓

↓

↓

Student Student Student

↓

↓

↓

101     102     103

↓

↓

↓

Anshika Riya Karan
```

---

# ⚡ Time Complexity

| Operation | Complexity |
|-----------|------------|
| Access by Index | O(1) |
| Update Object | O(1) |
| Traversal | O(n) |
| Search | O(n) |

---

# ✅ Advantages

- Stores multiple objects together.
- Easy to manage related data.
- Supports Object-Oriented Programming.
- Easy to iterate.
- Better organization than multiple arrays.

---

# ⚠️ Limitations

- Uses more memory than primitive arrays.
- Objects must be created separately.
- Accessing a null reference causes `NullPointerException`.

---

# 🌍 Real-World Applications

Arrays of Objects are commonly used in:

- Student Management Systems
- Employee Management Systems
- Library Management Systems
- Banking Applications
- Hospital Management Systems
- Product Catalogs
- E-Commerce Applications
- Inventory Systems

---

# 🎯 Interview Tip

### Question

What is stored inside an Array of Objects?

### Answer

An Array of Objects does **not** store the actual objects. It stores **references (memory addresses)** that point to objects created in the heap memory. Initially, all elements contain `null` until objects are created using the `new` keyword.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Array of Objects using Constructors
- Passing Arrays of Objects to Methods
- Returning Arrays of Objects
- Common Mistakes
- Best Practices
- Internal Working
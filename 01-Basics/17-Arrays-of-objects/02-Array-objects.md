# 📘 Chapter 17: Array of Objects (Part 2)

## Constructors, Passing Arrays to Methods & Internal Working

> *"Arrays of Objects become truly useful when combined with constructors, methods, and Object-Oriented Programming principles. This is how real-world Java applications manage collections of related objects."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Initialize Arrays of Objects using constructors.
- Pass Arrays of Objects to methods.
- Return Arrays of Objects from methods.
- Understand deep vs shallow references.
- Learn internal working.
- Identify common mistakes.
- Follow best practices.

---

# 📚 Table of Contents

1. Initializing using Constructors
2. Passing Array of Objects to Methods
3. Returning Array of Objects
4. Updating Objects
5. Internal Working
6. Common Mistakes
7. Best Practices

---

# 📖 Initializing using Constructors

Instead of creating empty objects,

```java
students[0] = new Student();
```

we can initialize the object directly.

```java
class Student{

    int rollNo;
    String name;

    Student(int rollNo, String name){

        this.rollNo = rollNo;
        this.name = name;

    }

}
```

Now,

```java
Student[] students = new Student[3];

students[0] = new Student(101,"Anshika");
students[1] = new Student(102,"Riya");
students[2] = new Student(103,"Karan");
```

Output

```text
101 Anshika

102 Riya

103 Karan
```

---

# 💻 Complete Example

```java
class Student{

    int rollNo;
    String name;

    Student(int rollNo,String name){

        this.rollNo = rollNo;
        this.name = name;

    }

}

public class Demo{

    public static void main(String[] args){

        Student[] students = {

            new Student(101,"Anshika"),
            new Student(102,"Riya"),
            new Student(103,"Karan")

        };

        for(Student s : students){

            System.out.println(

                s.rollNo + " " + s.name

            );

        }

    }

}
```

Output

```text
101 Anshika

102 Riya

103 Karan
```

---

# 📖 Passing an Array of Objects to a Method

Arrays can be passed just like any other object.

Example

```java
public static void display(Student[] students){

    for(Student s : students){

        System.out.println(

            s.rollNo + " " + s.name

        );

    }

}
```

Calling

```java
display(students);
```

Output

```text
101 Anshika

102 Riya

103 Karan
```

---

# 📖 Returning an Array of Objects

Methods can also return object arrays.

Example

```java
public static Student[] createStudents(){

    Student[] students = {

        new Student(101,"Anshika"),
        new Student(102,"Riya")

    };

    return students;

}
```

Usage

```java
Student[] list = createStudents();
```

---

# 📖 Updating Objects

Objects can be modified after creation.

```java
students[0].name = "Priya";

students[0].rollNo = 120;
```

Output

```text
120 Priya
```

---

# 📖 Object References

Suppose

```java
Student s = students[0];
```

Now

```text
students[0]

↓

Student Object

↑

s
```

Both variables refer to the same object.

---

# 💻 Example

```java
Student s = students[0];

s.name = "Rahul";

System.out.println(students[0].name);
```

Output

```text
Rahul
```

Reason

Only one object exists.

---

# 📦 Memory Representation

```text
students

↓

+--------+--------+--------+

↓

↓

↓

Student   Student   Student

↑

s
```

Both `students[0]` and `s` point to the same object.

---

# 📖 Passing Reference to Methods

```java
public static void update(Student s){

    s.name = "Aman";

}
```

Calling

```java
update(students[0]);
```

Output

```text
Aman
```

Reason

Java passes the object reference by value. Both references point to the same object, so modifying its fields affects the original object.

---

# 📖 Null References

Suppose

```java
Student[] students = new Student[3];
```

Current Memory

```text
null

null

null
```

Trying

```java
students[0].name = "Anshika";
```

Output

```text
NullPointerException
```

Reason

No Student object has been created.

Correct

```java
students[0] = new Student(101,"Anshika");
```

---

# 📖 Internal Working

```text
Student[] students

↓

Array

↓

Reference 1

Reference 2

Reference 3

↓

↓

↓

Student Objects

↓

Fields

↓

rollNo

name
```

---

# 📊 Operations

| Operation | Complexity |
|-----------|------------|
| Access by Index | O(1) |
| Modify Object | O(1) |
| Traverse | O(n) |
| Search | O(n) |

---

# ⚠️ Common Mistakes

## ❌ Forgetting to Create Objects

Wrong

```java
Student[] students = new Student[2];

students[0].name = "Anshika";
```

Result

```text
NullPointerException
```

Correct

```java
students[0] = new Student();

students[0].name = "Anshika";
```

---

## ❌ Accessing Invalid Index

Wrong

```java
students[5];
```

Result

```text
ArrayIndexOutOfBoundsException
```

---

## ❌ Comparing Objects with ==

Wrong

```java
students[0] == students[1];
```

This compares references, not object content.

If logical equality is needed, override `equals()` in the class and use:

```java
students[0].equals(students[1]);
```

---

## ❌ Assuming New Array Creates Objects

Wrong

```java
Student[] students = new Student[5];
```

Many beginners think this creates five Student objects.

Actually, it creates an array of **five null references**.

---

# 💡 Best Practices

- Always initialize every object before accessing it.
- Prefer constructors for object creation.
- Use enhanced for-loops for traversal.
- Validate indexes before accessing elements.
- Override `toString()` for easy printing.
- Override `equals()` and `hashCode()` when comparing object contents.
- Avoid unnecessary object creation.

---

# 🌍 Real-World Applications

Arrays of Objects are used in:

- Student Records
- Employee Databases
- Product Catalogs
- Hospital Management
- Banking Systems
- Flight Reservation Systems
- Inventory Management
- Library Management Systems

---

# 🎯 Interview Tip

### Question

What is the difference between

```java
Student[] students = new Student[5];
```

and

```java
students[0] = new Student();
```

### Answer

`new Student[5]` creates **only an array capable of storing five Student references**. All elements are initially `null`. No `Student` objects are created until `new Student()` is called for each element.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Array of Objects vs ArrayList of Objects
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision
- Chapter Summary
- Frequently Asked Interview Questions
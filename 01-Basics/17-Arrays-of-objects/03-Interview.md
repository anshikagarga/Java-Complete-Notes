# 📘 Chapter 17: Array of Objects (Part 3)

## Array of Objects vs ArrayList of Objects, Interview Questions, MCQs & Practice Problems

> *"Arrays of Objects are suitable when the number of objects is fixed, whereas ArrayList of Objects is preferred when the size can change dynamically. Understanding the difference is essential for Java interviews and real-world development."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Arrays of Objects and ArrayList of Objects.
- Know when to use each.
- Revise the complete chapter.
- Prepare for Java interviews.
- Solve practice problems.

---

# 📚 Table of Contents

1. Array of Objects vs ArrayList of Objects
2. Advantages
3. Limitations
4. Real-World Applications
5. Common Mistakes
6. Best Practices
7. Interview Questions
8. MCQs
9. Quick Revision
10. Practice Problems
11. Related Topics
12. References
13. Chapter Summary

---

# 📊 Array of Objects vs ArrayList of Objects

| Feature | Array of Objects | ArrayList of Objects |
|----------|------------------|----------------------|
| Size | Fixed | Dynamic |
| Memory Allocation | Fixed | Grows automatically |
| Performance | Slightly Faster | Slightly Slower |
| Add New Object | Difficult | Easy |
| Delete Object | Manual | Built-in Methods |
| Built-in Methods | ❌ | ✅ |
| Package | Java Language | java.util |
| Generics Support | ❌ | ✅ |

---

# 📖 When Should You Use an Array of Objects?

Use an Array of Objects when:

- Number of objects is fixed.
- High performance is required.
- Memory usage is predictable.
- Frequent resizing is not needed.

Example

```java
Student[] students = new Student[100];
```

---

# 📖 When Should You Use ArrayList of Objects?

Use an ArrayList when:

- Size is unknown.
- Objects are frequently added or removed.
- Built-in utility methods are needed.
- Flexibility is more important than fixed size.

Example

```java
ArrayList<Student> students = new ArrayList<>();
```

---

# 💻 Example: Array of Objects

```java
class Student{

    int rollNo;
    String name;

    Student(int rollNo, String name){

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

            System.out.println(s.rollNo + " " + s.name);

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

# 💻 Example: ArrayList of Objects

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

public class Demo{

    public static void main(String[] args){

        ArrayList<Student> students = new ArrayList<>();

        students.add(new Student(101,"Anshika"));
        students.add(new Student(102,"Riya"));
        students.add(new Student(103,"Karan"));

        for(Student s : students){

            System.out.println(s.rollNo + " " + s.name);

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

# 📊 Internal Working

### Array of Objects

```text
Student[]

↓

Fixed Size Array

↓

Reference

↓

Student Object
```

---

### ArrayList of Objects

```text
ArrayList

↓

Dynamic Array

↓

References

↓

Student Objects
```

---

# 🌍 Real-World Applications

### Array of Objects

- Student Records
- Sensor Data
- Employee Attendance
- Fixed Inventory
- Exam Results

---

### ArrayList of Objects

- Shopping Cart
- Banking Transactions
- Social Media Posts
- Hospital Patients
- Flight Bookings
- Employee Management System
- E-Commerce Products

---

# ✅ Advantages of Array of Objects

- Faster access.
- Simple implementation.
- Less overhead.
- Fixed memory allocation.
- Suitable for static data.

---

# ⚠️ Limitations

- Cannot grow automatically.
- Insertion and deletion are difficult.
- Wastes memory if array is oversized.
- May overflow if capacity is exceeded.

---

# ⚠️ Common Mistakes

## ❌ Forgetting to Initialize Objects

Wrong

```java
Student[] students = new Student[2];

students[0].name = "Anshika";
```

Output

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

Output

```text
ArrayIndexOutOfBoundsException
```

---

## ❌ Assuming Array Size Can Increase

Wrong

```java
Student[] students = new Student[2];

// Need third student
```

Arrays cannot resize automatically.

Use

```java
ArrayList<Student>
```

instead.

---

## ❌ Comparing References Instead of Values

Wrong

```java
students[0] == students[1]
```

Correct

```java
students[0].equals(students[1])
```

(After overriding `equals()`.)

---

# 💡 Best Practices

- Use arrays when the number of objects is fixed.
- Use ArrayList when size is dynamic.
- Always initialize object references.
- Prefer enhanced for-loops for traversal.
- Override `toString()` for easy debugging.
- Override `equals()` and `hashCode()` when comparing objects.
- Validate indexes before accessing array elements.

---

# 🧩 Interview Questions

## Beginner

1. What is an Array of Objects?
2. How is it different from a primitive array?
3. Why are all elements initially `null`?
4. How do you create an object inside an object array?
5. Can we store different object types in the same object array?

---

## Intermediate

6. Difference between Array of Objects and ArrayList of Objects.
7. Why do we get a NullPointerException in object arrays?
8. How do we traverse an Array of Objects?
9. Can we pass an Array of Objects to a method?
10. Can a method return an Array of Objects?

---

## Advanced

11. Explain the memory representation of an Array of Objects.
12. Why does `new Student[5]` not create five Student objects?
13. How are references stored inside an object array?
14. When should you choose an array instead of an ArrayList?
15. How do object references behave when passed to methods?

---

# 🎓 MCQs

### Q1. An Array of Objects stores:

- A. Primitive values
- B. Object references ✅
- C. Methods
- D. Classes

---

### Q2. Initially, every element of an object array contains:

- A. 0
- B. Empty Object
- C. null ✅
- D. Garbage Value

---

### Q3. Which exception occurs if you access a field without creating the object?

- A. ArithmeticException
- B. ArrayStoreException
- C. NullPointerException ✅
- D. IOException

---

### Q4. Which loop is commonly used to traverse an Array of Objects?

- A. while
- B. do-while
- C. for / enhanced for ✅
- D. switch

---

### Q5. Which is better for a dynamic number of objects?

- A. Object Array
- B. ArrayList ✅
- C. Primitive Array
- D. String Array

---

# 📝 Quick Revision

## Creating an Object Array

```java
Student[] students = new Student[3];
```

---

## Creating Objects

```java
students[0] = new Student(101,"Anshika");
```

---

## Traversing

```java
for(Student s : students){

    System.out.println(s.name);

}
```

---

## Memory Representation

```text
Array

↓

References

↓

Objects

↓

Fields
```

---

## Time Complexity

| Operation | Complexity |
|-----------|------------|
| Access | O(1) |
| Update | O(1) |
| Search | O(n) |
| Traversal | O(n) |

---

# 🧪 Practice Problems

## Beginner

- Store 5 Student objects in an array.
- Print all student names.
- Print all roll numbers.
- Update one student's marks.

---

## Intermediate

- Find the student with the highest marks.
- Search a student by roll number.
- Sort an array of Student objects by roll number.
- Sort students by marks.

---

## Advanced

- Implement a Student Management System using an Array of Objects.
- Convert an Array of Objects into an ArrayList.
- Compare the performance of Arrays and ArrayLists.
- Build a mini Employee Database using object arrays.

---

# 🔗 Related Topics

- Arrays
- Classes and Objects
- Constructors
- this Keyword
- Static Keyword
- Encapsulation
- ArrayList
- Collections Framework
- Comparable
- Comparator

---

# 📚 References

- Oracle Java Documentation
- Effective Java by Joshua Bloch
- Java: The Complete Reference
- OpenJDK Documentation
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 17: Array of Objects**.

### ✔️ Concepts Covered

- Array of Objects
- Object References
- Constructors
- Traversing Object Arrays
- Passing Arrays to Methods
- Returning Arrays
- Internal Working
- Array vs ArrayList
- Best Practices
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ An Array of Objects stores **references**, not actual objects.
- ✅ `new Student[5]` creates an array of **five null references**, not five Student objects.
- ✅ Each object must be created individually using the `new` keyword.
- ✅ Arrays have a **fixed size**, whereas `ArrayList` can grow dynamically.
- ✅ Accessing an uninitialized element results in a **NullPointerException**.
- ✅ Arrays provide **O(1)** index-based access.
- ✅ Use Arrays for fixed-size collections and `ArrayList` for dynamic collections.

---

# 🚀 Next Chapter

➡️ **18-Varargs.md**

### Topics Covered

- What are Varargs?
- Syntax of Varargs
- Variable-Length Arguments
- Varargs vs Arrays
- Method Overloading with Varargs
- Interview Questions
- MCQs
- Practice Problems
```
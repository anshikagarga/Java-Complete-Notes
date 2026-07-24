# 📘 Chapter 07: File Handling (Part 3)

## Serialization, Deserialization, Interview Questions, MCQs & Chapter Summary

> *"Serialization allows Java objects to be stored permanently or transmitted over a network, while Deserialization reconstructs those objects back into memory."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Serialization.
- Learn Deserialization.
- Use ObjectOutputStream.
- Use ObjectInputStream.
- Understand the Serializable interface.
- Learn transient keyword.
- Solve Interview Questions.
- Practice MCQs.

---

# 📚 Table of Contents

1. Serialization
2. Serializable Interface
3. ObjectOutputStream
4. Deserialization
5. ObjectInputStream
6. transient Keyword
7. serialVersionUID
8. Internal Working
9. Best Practices
10. Common Mistakes
11. Interview Questions
12. MCQs
13. Quick Revision
14. Practice Problems
15. Related Topics
16. References
17. Chapter Summary

---

# 📖 What is Serialization?

**Serialization** is the process of converting a Java object into a byte stream.

This byte stream can be:

- Stored in a file
- Sent over a network
- Stored in a database
- Cached

---

## Serialization Flow

```text
Java Object

↓

ObjectOutputStream

↓

Byte Stream

↓

File / Network
```

---

# 📖 Serializable Interface

For serialization, a class must implement the **Serializable** interface.

Package

```java
import java.io.Serializable;
```

Example

```java
import java.io.Serializable;

class Student implements Serializable {

    int id;
    String name;

    Student(int id, String name){

        this.id = id;
        this.name = name;

    }

}
```

> `Serializable` is a **marker interface**, meaning it contains no methods.

---

# 📖 ObjectOutputStream

`ObjectOutputStream` is used to serialize objects.

Example

```java
import java.io.*;

class Student implements Serializable {

    int id;
    String name;

    Student(int id, String name){

        this.id = id;
        this.name = name;

    }

}

public class Demo {

    public static void main(String[] args) throws Exception {

        Student s = new Student(101, "Anshika");

        ObjectOutputStream out =

            new ObjectOutputStream(

                new FileOutputStream("student.ser")

            );

        out.writeObject(s);

        out.close();

        System.out.println("Object Serialized");

    }

}
```

Output

```text
Object Serialized
```

---

# 📖 What is Deserialization?

**Deserialization** is the process of converting a byte stream back into a Java object.

Flow

```text
File

↓

Byte Stream

↓

ObjectInputStream

↓

Java Object
```

---

# 📖 ObjectInputStream

Used to read serialized objects.

Example

```java
import java.io.*;

class Student implements Serializable {

    int id;
    String name;

}

public class Demo {

    public static void main(String[] args) throws Exception {

        ObjectInputStream in =

            new ObjectInputStream(

                new FileInputStream("student.ser")

            );

        Student s = (Student) in.readObject();

        System.out.println(s.id);

        System.out.println(s.name);

        in.close();

    }

}
```

Output

```text
101

Anshika
```

---

# 📖 transient Keyword

Sometimes we don't want certain fields to be serialized.

Use the `transient` keyword.

Example

```java
import java.io.Serializable;

class Student implements Serializable {

    int id;

    String name;

    transient String password;

}
```

When serialized,

```text
id

✔ Saved

name

✔ Saved

password

❌ Not Saved
```

After deserialization, the `password` field will have its default value (`null` for objects, `0` for numeric primitives, `false` for boolean).

---

# 📖 serialVersionUID

Every serializable class has a version identifier.

Example

```java
class Student implements Serializable {

    private static final long serialVersionUID = 1L;

}
```

Why use it?

- Version Control
- Prevents `InvalidClassException`
- Maintains Serialization Compatibility

---

# 📦 Internal Working

Serialization

```text
Java Object

↓

ObjectOutputStream

↓

Byte Stream

↓

student.ser
```

Deserialization

```text
student.ser

↓

ObjectInputStream

↓

Java Object

↓

Use Object
```

---

# ⚠️ Common Mistakes

## ❌ Forgetting Serializable

Wrong

```java
class Student{

}
```

Output

```text
NotSerializableException
```

Correct

```java
class Student implements Serializable{

}
```

---

## ❌ Forgetting to Close Streams

Wrong

```java
ObjectOutputStream out =

new ObjectOutputStream(...);

// No close()
```

Correct

```java
try(ObjectOutputStream out =

        new ObjectOutputStream(

            new FileOutputStream("student.ser")

        )){

    out.writeObject(student);

}
```

---

## ❌ Expecting transient Variables to be Saved

Wrong Assumption

```text
transient password

↓

Saved
```

Correct

```text
transient password

↓

Ignored During Serialization
```

---

## ❌ Changing Class Structure Without Managing Version

Changing fields in a serialized class without handling `serialVersionUID` can cause compatibility issues.

---

# 💡 Best Practices

- Always implement `Serializable` when object serialization is required.
- Declare an explicit `serialVersionUID`.
- Use `transient` for sensitive fields like passwords, OTPs, and tokens.
- Prefer Try-with-Resources for stream management.
- Never serialize confidential information unless necessary.
- Validate deserialized data before using it in critical applications.

---

# 🌍 Real-World Applications

Serialization is used in:

- Banking Systems
- Session Management
- Distributed Systems
- Caching
- Object Persistence
- RMI (Remote Method Invocation)
- Network Communication
- Backup Systems

---

# 🧩 Interview Questions

## Beginner

1. What is File Handling?
2. What is the File class?
3. Difference between Character Stream and Byte Stream?
4. What is Serialization?
5. What is Deserialization?

---

## Intermediate

6. Difference between FileReader and FileInputStream.
7. Difference between BufferedReader and FileReader.
8. What is the Serializable interface?
9. What is the transient keyword?
10. What is Try-with-Resources?

---

## Advanced

11. What is `serialVersionUID`?
12. What happens if a class does not implement `Serializable`?
13. Why is `Serializable` called a Marker Interface?
14. Difference between `ObjectInputStream` and `ObjectOutputStream`.
15. What are the security risks of deserialization?

---

# 🎓 MCQs

### Q1. Which package provides File Handling?

- A. java.lang
- B. java.io ✅
- C. java.sql
- D. java.util

---

### Q2. Which class writes objects to a file?

- A. FileWriter
- B. BufferedWriter
- C. ObjectOutputStream ✅
- D. FileOutputStream

---

### Q3. Which interface enables Serialization?

- A. Cloneable
- B. Comparable
- C. Serializable ✅
- D. Runnable

---

### Q4. Which keyword prevents a field from being serialized?

- A. static
- B. volatile
- C. transient ✅
- D. final

---

### Q5. Which class reads serialized objects?

- A. FileReader
- B. BufferedReader
- C. ObjectInputStream ✅
- D. Scanner

---

# 📝 Quick Revision

## Create File

```java
File file = new File("student.txt");

file.createNewFile();
```

---

## Read File

```java
FileReader reader =

    new FileReader("student.txt");
```

---

## Write File

```java
FileWriter writer =

    new FileWriter("student.txt");
```

---

## Serialization

```java
ObjectOutputStream out =

    new ObjectOutputStream(

        new FileOutputStream("student.ser")

    );

out.writeObject(student);
```

---

## Deserialization

```java
ObjectInputStream in =

    new ObjectInputStream(

        new FileInputStream("student.ser")

    );

Student s =

    (Student) in.readObject();
```

---

# 🧪 Practice Problems

## Beginner

- Create a file named `student.txt`.
- Write your name into a file.
- Read the file and display its contents.

---

## Intermediate

- Copy the contents of one text file to another.
- Count the number of lines in a file.
- Append new data without overwriting existing content.

---

## Advanced

- Serialize an `Employee` object and deserialize it.
- Build a Student Record Management System using File Handling.
- Create a simple Log File Generator.
- Store and retrieve user information using object serialization.

---

# 🔗 Related Topics

- Exception Handling
- Collections Framework
- Streams API
- JDBC
- NIO (New I/O)
- Networking

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

You have completed **Chapter 07: File Handling**.

### ✔️ Concepts Covered

- Introduction to File Handling
- File Class
- Creating, Deleting & Renaming Files
- FileReader
- FileWriter
- BufferedReader
- BufferedWriter
- Character Streams
- Byte Streams
- FileInputStream
- FileOutputStream
- Try-with-Resources
- Serialization
- Deserialization
- Serializable Interface
- transient Keyword
- serialVersionUID
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Use the `File` class to represent files and directories.
- ✅ Use **Character Streams** (`Reader`/`Writer`) for text files.
- ✅ Use **Byte Streams** (`InputStream`/`OutputStream`) for binary files.
- ✅ Prefer buffered streams for better performance.
- ✅ Use Try-with-Resources to automatically close resources.
- ✅ Serialization converts an object into a byte stream; Deserialization reconstructs it.
- ✅ Use `transient` for fields that should not be serialized.
- ✅ Define `serialVersionUID` for better serialization compatibility.

---

# 🚀 Next Chapter

➡️ **08-JDBC.md**

### Topics Covered

- Introduction to JDBC
- JDBC Architecture
- JDBC Drivers
- DriverManager
- Connection
- Statement
- PreparedStatement
- ResultSet
- CRUD Operations
- Batch Processing
- Transactions
- Interview Questions
- MCQs
- Practice Problems
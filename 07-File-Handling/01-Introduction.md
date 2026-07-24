# 📘 Chapter 07: File Handling (Part 1)

> *"File Handling in Java allows programs to create, read, write, update, and delete files. It is an essential concept for storing data permanently instead of keeping it only in memory."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand File Handling in Java.
- Learn why File Handling is required.
- Understand the File class.
- Create, delete, and rename files.
- Create directories.
- Learn file properties.
- Understand File vs Streams.

---

# 📚 Table of Contents

1. Introduction to File Handling
2. Why File Handling?
3. Types of Files
4. File Class
5. Creating Files
6. Deleting Files
7. Renaming Files
8. Creating Directories
9. File Properties
10. File vs Stream
11. Internal Working
12. Real-World Applications

---

# 🤔 What is File Handling?

File Handling is the process of performing operations on files such as:

- Creating files
- Reading files
- Writing files
- Updating files
- Deleting files

Java provides the **java.io** package for File Handling.

Some commonly used classes are:

- File
- FileReader
- FileWriter
- BufferedReader
- BufferedWriter
- FileInputStream
- FileOutputStream
- ObjectInputStream
- ObjectOutputStream

---

# 💡 Why Do We Need File Handling?

Without File Handling, data is stored only in RAM.

When the program terminates,

➡️ Data is lost.

Example

```text
Program Starts

↓

Store Student Details

↓

Program Ends

↓

Data Lost
```

Using files,

```text
Program

↓

Write Data

↓

File

↓

Data Saved Permanently
```

---

# 📖 Types of Files

There are mainly two types of files.

## 1. Text Files

Examples

- notes.txt
- student.csv
- data.json
- config.properties

These files store readable text.

---

## 2. Binary Files

Examples

- image.jpg
- song.mp3
- video.mp4
- object.ser

These files store binary data.

---

# 📖 Java IO Package

The **java.io** package contains classes for file handling.

Common Classes

| Class | Purpose |
|---------|----------|
| File | Represents a file or directory |
| FileReader | Reads text files |
| FileWriter | Writes text files |
| BufferedReader | Reads efficiently |
| BufferedWriter | Writes efficiently |
| FileInputStream | Reads binary files |
| FileOutputStream | Writes binary files |
| ObjectInputStream | Reads serialized objects |
| ObjectOutputStream | Writes serialized objects |

---

# 📖 File Class

The **File** class represents a file or directory.

Package

```java
import java.io.File;
```

Constructor

```java
File file = new File("student.txt");
```

This does **not** create the file.

It only creates a File object representing the path.

---

# 📖 Creating a File

Method

```java
createNewFile()
```

Example

```java
import java.io.*;

public class Demo {

    public static void main(String[] args) throws IOException {

        File file = new File("student.txt");

        if(file.createNewFile()) {

            System.out.println("File Created");

        }

        else {

            System.out.println("Already Exists");

        }

    }

}
```

Output

```text
File Created
```

---

# 📖 Deleting a File

Method

```java
delete()
```

Example

```java
File file = new File("student.txt");

if(file.delete()) {

    System.out.println("Deleted");

}
```

Output

```text
Deleted
```

---

# 📖 Renaming a File

Method

```java
renameTo()
```

Example

```java
File oldFile = new File("student.txt");

File newFile = new File("details.txt");

oldFile.renameTo(newFile);
```

---

# 📖 Creating a Directory

Method

```java
mkdir()
```

Example

```java
File folder = new File("JavaNotes");

folder.mkdir();
```

Output

```text
Directory Created
```

---

# 📖 Creating Nested Directories

Method

```java
mkdirs()
```

Example

```java
File folder = new File("Java/Notes/FileHandling");

folder.mkdirs();
```

---

# 📖 File Properties

Useful Methods

| Method | Description |
|---------|-------------|
| exists() | Checks if file exists |
| getName() | Returns file name |
| getAbsolutePath() | Returns absolute path |
| length() | Returns file size |
| canRead() | Checks read permission |
| canWrite() | Checks write permission |
| isFile() | Checks if it is a file |
| isDirectory() | Checks if it is a directory |
| lastModified() | Returns last modified time |

---

## Example

```java
File file = new File("student.txt");

System.out.println(file.exists());

System.out.println(file.getName());

System.out.println(file.length());

System.out.println(file.canRead());
```

Output

```text
true

student.txt

250

true
```

---

# 📖 File vs Stream

| File | Stream |
|------|--------|
| Represents a file | Represents data flow |
| Used for file information | Used for reading/writing data |
| Doesn't read data itself | Reads/Writes data |
| File class | Reader/Writer/InputStream/OutputStream |

---

# 📦 Internal Working

```text
Application

↓

File Object

↓

Operating System

↓

Hard Disk

↓

Permanent Storage
```

---

# 🌍 Real-World Applications

File Handling is used in:

- Banking Systems
- Student Management
- Employee Records
- Log Files
- Configuration Files
- Billing Systems
- Hospital Management
- E-Commerce Applications

---

# 🎯 Interview Tip

### Question

What is the difference between File and FileInputStream?

### Answer

- **File** represents the file or directory path.
- **FileInputStream** is used to read binary data from a file.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- FileReader
- FileWriter
- BufferedReader
- BufferedWriter
- Character Streams
- Byte Streams
- FileInputStream
- FileOutputStream
- Try-with-Resources
# 📘 Chapter 07: File Handling (Part 2)

## Reading Files, Writing Files, Character Streams & Byte Streams

> *"Java provides different classes for reading and writing files. Choosing the correct stream depends on whether you are working with text data or binary data."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Read text files using `FileReader`.
- Write text files using `FileWriter`.
- Use `BufferedReader` and `BufferedWriter`.
- Understand Character Streams.
- Understand Byte Streams.
- Learn `FileInputStream` and `FileOutputStream`.
- Use Try-with-Resources.
- Follow best practices while handling files.

---

# 📚 Table of Contents

1. Reading Files
2. Writing Files
3. FileReader
4. FileWriter
5. BufferedReader
6. BufferedWriter
7. Character Streams
8. Byte Streams
9. FileInputStream
10. FileOutputStream
11. Try-with-Resources
12. Internal Working
13. Best Practices

---

# 📖 Reading Files

Java provides several ways to read files.

Common classes

- FileReader
- BufferedReader
- FileInputStream
- Scanner
- Files (NIO)

---

# 📖 FileReader

`FileReader` is used to read **text files** character by character.

Package

```java
import java.io.FileReader;
```

---

## Example

Suppose **student.txt** contains:

```text
Hello Java
Welcome to File Handling
```

Program

```java
import java.io.FileReader;
import java.io.IOException;

public class Demo {

    public static void main(String[] args) throws IOException {

        FileReader reader = new FileReader("student.txt");

        int ch;

        while((ch = reader.read()) != -1){

            System.out.print((char) ch);

        }

        reader.close();

    }

}
```

Output

```text
Hello Java
Welcome to File Handling
```

---

# 📖 FileWriter

`FileWriter` is used to write **text data** into a file.

Package

```java
import java.io.FileWriter;
```

---

## Example

```java
import java.io.FileWriter;
import java.io.IOException;

public class Demo {

    public static void main(String[] args) throws IOException {

        FileWriter writer = new FileWriter("student.txt");

        writer.write("Learning Java File Handling");

        writer.close();

        System.out.println("Data Written");

    }

}
```

Output

```text
Data Written
```

---

## Appending Data

By default, `FileWriter` overwrites the file.

To append data,

```java
FileWriter writer = new FileWriter("student.txt", true);

writer.write("\nNew Line");
writer.close();
```

---

# 📖 BufferedReader

`BufferedReader` reads text efficiently using an internal buffer.

Package

```java
import java.io.BufferedReader;
```

---

## Example

```java
import java.io.*;

public class Demo {

    public static void main(String[] args) throws Exception {

        BufferedReader br =

            new BufferedReader(new FileReader("student.txt"));

        String line;

        while((line = br.readLine()) != null){

            System.out.println(line);

        }

        br.close();

    }

}
```

---

# 📖 BufferedWriter

`BufferedWriter` writes text efficiently.

Example

```java
BufferedWriter bw =

    new BufferedWriter(new FileWriter("student.txt"));

bw.write("Java");

bw.newLine();

bw.write("Python");

bw.close();
```

Output

```text
Java
Python
```

---

# 📖 Character Streams

Character Streams work with **text data**.

Common Classes

- FileReader
- FileWriter
- BufferedReader
- BufferedWriter
- PrintWriter

Suitable for

- Text Files
- CSV Files
- JSON Files
- XML Files

---

# 📖 Byte Streams

Byte Streams work with **binary data**.

Common Classes

- FileInputStream
- FileOutputStream
- BufferedInputStream
- BufferedOutputStream

Suitable for

- Images
- Audio
- Video
- PDF Files
- ZIP Files

---

# 📊 Character Stream vs Byte Stream

| Character Stream | Byte Stream |
|------------------|-------------|
| Handles text | Handles binary data |
| Reads characters | Reads bytes |
| Uses Unicode | Uses raw bytes |
| Reader / Writer classes | InputStream / OutputStream classes |

---

# 📖 FileInputStream

Used for reading binary files.

Example

```java
import java.io.FileInputStream;
import java.io.IOException;

public class Demo {

    public static void main(String[] args) throws IOException {

        FileInputStream fis =

            new FileInputStream("image.jpg");

        int data;

        while((data = fis.read()) != -1){

            // Process byte

        }

        fis.close();

    }

}
```

---

# 📖 FileOutputStream

Used for writing binary files.

Example

```java
import java.io.FileOutputStream;
import java.io.IOException;

public class Demo {

    public static void main(String[] args) throws IOException {

        FileOutputStream fos =

            new FileOutputStream("sample.txt");

        fos.write("Hello Java".getBytes());

        fos.close();

    }

}
```

Output

```text
Hello Java
```

---

# 📖 Try-with-Resources

Introduced in **Java 7**, Try-with-Resources automatically closes resources.

Without Try-with-Resources

```java
FileReader reader = new FileReader("student.txt");

try{

    // Read File

}

finally{

    reader.close();

}
```

---

With Try-with-Resources

```java
try(FileReader reader = new FileReader("student.txt")){

    int ch;

    while((ch = reader.read()) != -1){

        System.out.print((char) ch);

    }

}
catch(IOException e){

    e.printStackTrace();

}
```

No need to explicitly call `close()`.

---

# 📦 Internal Working

```text
Application

↓

Reader / InputStream

↓

Buffer (Optional)

↓

Operating System

↓

Hard Disk

↓

Data
```

For writing,

```text
Application

↓

Writer / OutputStream

↓

Buffer (Optional)

↓

Operating System

↓

Hard Disk
```

---

# ⚠️ Common Mistakes

## ❌ Forgetting to Close Streams

Wrong

```java
FileReader reader = new FileReader("student.txt");

// No close()
```

Correct

```java
try(FileReader reader = new FileReader("student.txt")){

    // Read File

}
```

---

## ❌ Using FileReader for Images

Wrong

```java
FileReader reader =

    new FileReader("image.jpg");
```

Correct

```java
FileInputStream fis =

    new FileInputStream("image.jpg");
```

---

## ❌ Overwriting File Accidentally

Wrong

```java
FileWriter writer =

    new FileWriter("student.txt");
```

This replaces existing content.

Correct

```java
FileWriter writer =

    new FileWriter("student.txt", true);
```

---

# 💡 Best Practices

- Use `BufferedReader` for efficient text reading.
- Use `BufferedWriter` for efficient text writing.
- Use Character Streams for text files.
- Use Byte Streams for binary files.
- Prefer Try-with-Resources to manage resources automatically.
- Handle exceptions properly using `try-catch`.

---

# 🌍 Real-World Applications

File reading and writing are commonly used in:

- Log Management
- Configuration Files
- Report Generation
- Data Export/Import
- Image Processing
- Document Management
- Backup Utilities
- Banking Applications

---

# 🎯 Interview Tip

### Question

What is the difference between `FileReader` and `BufferedReader`?

### Answer

| FileReader | BufferedReader |
|------------|----------------|
| Reads character by character | Reads using an internal buffer |
| Slower for large files | Faster and more efficient |
| Does not provide `readLine()` | Provides `readLine()` method |

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Serialization
- Deserialization
- ObjectInputStream
- ObjectOutputStream
- File Handling Interview Questions
- MCQs
- Practice Problems
- Chapter Summary
---

# 🧠 JVM Internal Architecture

The Java Virtual Machine (JVM) is much more than just a program that runs Java code. It consists of several components that work together to load, verify, execute, and manage Java applications.

## High-Level JVM Architecture

```text
                  +----------------------------+
                  |        Java Program        |
                  |      (Hello.class)         |
                  +-------------+--------------+
                                |
                                ▼
                    +----------------------+
                    |    Class Loader      |
                    +----------------------+
                                |
                                ▼
                    +----------------------+
                    | Bytecode Verifier    |
                    +----------------------+
                                |
                                ▼
                    +----------------------+
                    | Runtime Data Areas   |
                    +----------------------+
                                |
                                ▼
                    +----------------------+
                    | Execution Engine     |
                    | Interpreter + JIT    |
                    +----------------------+
                                |
                                ▼
                    +----------------------+
                    | Garbage Collector    |
                    +----------------------+
                                |
                                ▼
                         Machine Code
```

---

# 📚 JVM Components

The JVM consists of five major components:

1. Class Loader
2. Bytecode Verifier
3. Runtime Data Areas
4. Execution Engine
5. Garbage Collector

---

# 📦 1. Class Loader

The **Class Loader** loads `.class` files into memory.

Whenever the JVM needs a class, it asks the Class Loader to locate and load it.

```
Hello.class

      │

      ▼

Class Loader

      │

      ▼

Memory
```

## Responsibilities

- Loads bytecode into memory.
- Loads classes only when required.
- Avoids loading duplicate classes.

---

## Types of Class Loaders

### Bootstrap Class Loader

Loads core Java classes such as:

```
java.lang.*

java.util.*

java.io.*
```

---

### Platform Class Loader

Loads Java extension libraries.

---

### Application Class Loader

Loads classes written by developers.

Example

```
Student.class

Employee.class

Main.class
```

---

# 📦 2. Bytecode Verifier

After loading the class, JVM verifies whether the bytecode is safe.

It checks:

- Invalid bytecode
- Illegal memory access
- Stack overflow possibilities
- Type safety

If verification fails,

```
ClassFormatError
```

or

```
VerifyError
```

may occur.

---

# 📦 3. Runtime Data Areas

One of the most important interview topics.

The JVM creates several memory areas during program execution.

```
                JVM Memory

        +----------------------+

        | Method Area          |

        +----------------------+

        | Heap Memory          |

        +----------------------+

        | Stack Memory         |

        +----------------------+

        | PC Register          |

        +----------------------+

        | Native Method Stack  |

        +----------------------+
```

---

# 🏠 Heap Memory

Heap stores:

- Objects
- Arrays
- Instance variables

Example

```java
Student s = new Student();
```

Memory

```
Stack

s

↓

Heap

Student Object
```

Characteristics

- Shared by all threads.
- Largest memory area.
- Managed by Garbage Collector.

---

# 📚 Stack Memory

Stack stores:

- Local variables
- Method calls
- References

Example

```java
int x = 10;
```

```
Stack

x = 10
```

Every thread has its own stack.

---

# 📝 Method Area

Stores:

- Class metadata
- Static variables
- Constant pool
- Method information

Example

```java
static int count = 0;
```

Stored inside the Method Area.

---

# 📍 Program Counter (PC Register)

Each thread has its own PC Register.

It stores the address of the next instruction to execute.

Think of it as:

```
Current Line Number
```

---

# 🔗 Native Method Stack

Used when Java calls native methods written in languages such as C or C++.

Example

```
Java

↓

JNI

↓

C/C++
```

---

# 🚀 Execution Engine

The Execution Engine executes bytecode.

It consists of:

```
Execution Engine

│

├── Interpreter

└── JIT Compiler
```

---

# 📖 Interpreter

Reads bytecode one instruction at a time.

Advantages

- Starts quickly.

Disadvantages

- Slower execution.

---

# ⚡ JIT Compiler

JIT stands for

```
Just-In-Time Compiler
```

Instead of interpreting every instruction repeatedly,

JIT converts frequently executed bytecode into machine code.

```
Bytecode

↓

JIT Compiler

↓

Machine Code
```

This greatly improves performance.

---

# 💡 Why JIT is Important?

Suppose a loop executes

```
10 Million Times
```

Without JIT

```
Interpret

Interpret

Interpret

Interpret
```

With JIT

```
Compile Once

↓

Reuse Machine Code
```

Much faster.

---

# 🗑 Garbage Collector

Java automatically removes unused objects.

Example

```java
Student s = new Student();

s = null;
```

Now the object has no reference.

The Garbage Collector can remove it.

---

# Garbage Collection Process

```
Object Created

↓

Object Used

↓

Reference Removed

↓

Garbage Collector

↓

Memory Reclaimed
```

---

# 🌍 Real-World Example

Imagine a shopping website.

```
User opens Cart

↓

Objects Created

↓

User checks out

↓

Objects become unused

↓

Garbage Collector frees memory
```

Without GC,

memory usage would continuously increase.

---

# 📊 Runtime Memory Summary

| Memory Area | Stores | Shared? |
|-------------|--------|---------|
| Heap | Objects & Arrays | ✅ Yes |
| Stack | Local Variables | ❌ No |
| Method Area | Class Metadata | ✅ Yes |
| PC Register | Current Instruction | ❌ No |
| Native Method Stack | Native Calls | ❌ No |

---

# 💡 Interview Tip

Remember this simple rule:

```
Objects

↓

Heap

------------------

Local Variables

↓

Stack

------------------

Static Variables

↓

Method Area
```

This is one of the most frequently asked Java interview questions.

---

# 🧠 Behind the Scenes

When you write:

```java
Student s = new Student();
```

The JVM performs these steps:

```
Step 1

Create reference variable

↓

Step 2

Allocate memory in Heap

↓

Step 3

Store object address in Stack

↓

Step 4

Execute constructor

↓

Step 5

Program continues
```

---

# ⚠ Common Mistakes

## ❌ Heap and Stack are the same.

No.

Heap stores **objects**.

Stack stores **references and local variables**.

---

## ❌ Garbage Collector immediately removes objects.

No.

GC runs automatically when the JVM decides it is necessary.

---

## ❌ Stack stores objects.

Incorrect.

Stack stores **references**, not the actual objects.

---

# 💡 Best Practices

- Understand the execution flow instead of memorizing definitions.
- Learn Heap vs Stack with diagrams.
- Do not rely on `System.gc()` for memory management.
- Avoid creating unnecessary objects.

---

# 🚀 Coming in Part 3

- JVM vs JRE vs JDK Comparison Table
- Java Commands (`java`, `javac`, `jar`, `javadoc`, `jdb`)
- Java Installation & Environment Variables
- 35+ Interview Questions (Basic → Advanced)
- Practice Problems
- Quick Revision Sheet
- References
- Related Topics
- GitHub Mermaid Diagrams
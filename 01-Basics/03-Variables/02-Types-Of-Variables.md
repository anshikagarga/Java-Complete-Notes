---

# 📚 Types of Variables in Java

Java provides three main types of variables based on **where they are declared** and **how long they exist**.

```text
Variables
│
├── Local Variables
├── Instance Variables
└── Static Variables
```

Each type has a different purpose and memory location.

---

# 1️⃣ Local Variables

A **local variable** is declared inside a method, constructor, or block.

## Example

```java
public class Demo {

    public static void main(String[] args) {

        int age = 21;

        System.out.println(age);

    }

}
```

---

## Memory

```
Stack Memory

+----------------------+
| age = 21             |
+----------------------+
```

---

## Characteristics

- Declared inside methods.
- Stored in Stack Memory.
- Must be initialized before use.
- Destroyed when the method finishes.

---

# 🌍 Real-World Example

```java
public void calculateBill() {

    double total = 2500.50;

}
```

`total` exists only while the method executes.

---

# 2️⃣ Instance Variables

Instance variables belong to an object.

Every object gets its own copy.

## Example

```java
class Student {

    String name;
    int age;

}
```

---

## Memory

```
Heap Memory

Student Object

+----------------------+
| name = "Anshika"     |
| age = 21             |
+----------------------+
```

---

## Characteristics

- Declared inside a class.
- Outside methods.
- Stored in Heap Memory.
- Every object has its own copy.
- Gets default values.

---

## Example

```java
Student s1 = new Student();

Student s2 = new Student();
```

Memory

```
Heap

Student 1

name = null

age = 0

------------------

Student 2

name = null

age = 0
```

Each object stores separate values.

---

# 3️⃣ Static Variables

Static variables belong to the **class**, not to individual objects.

Only **one copy** exists.

---

## Example

```java
class Student {

    static String college = "AKTU";

}
```

---

## Memory

```
Method Area

college

↓

AKTU
```

All objects share this variable.

---

## Example

```java
Student s1 = new Student();

Student s2 = new Student();
```

Memory

```
Heap

Student 1

↓

college

↑

Student 2

↓

Method Area

AKTU
```

Both objects access the same variable.

---

# 📊 Comparison

| Feature | Local | Instance | Static |
|----------|--------|-----------|---------|
| Declared Inside | Method | Class | Class |
| Memory | Stack | Heap | Method Area |
| Default Value | ❌ No | ✅ Yes | ✅ Yes |
| Shared | ❌ No | ❌ No | ✅ Yes |
| Lifetime | Method | Object | Entire Program |

---

# 📍 Scope of Variables

Scope determines **where a variable can be accessed**.

---

## Local Scope

```java
public void demo(){

    int x = 10;

}
```

`x` is accessible only inside `demo()`.

---

## Class Scope

```java
class Student{

    int age;

}
```

Accessible by every method of the object.

---

## Static Scope

```java
static int count;
```

Accessible through

```java
ClassName.count
```

---

# ⏳ Lifetime of Variables

| Variable | Lifetime |
|-----------|-----------|
| Local | Until method ends |
| Instance | Until object is destroyed |
| Static | Until JVM terminates |

---

# 🔄 Default Values

Only **instance** and **static** variables receive default values.

| Data Type | Default Value |
|-----------|---------------|
| byte | 0 |
| short | 0 |
| int | 0 |
| long | 0L |
| float | 0.0f |
| double | 0.0 |
| char | '\u0000' |
| boolean | false |
| Object | null |

---

## Example

```java
class Student {

    int age;

    boolean placed;

    String name;

}
```

Output

```
age = 0

placed = false

name = null
```

---

# 🚫 final Variables

A variable declared as `final` cannot be reassigned.

```java
final double PI = 3.14159;
```

Wrong

```java
PI = 4.0;
```

Compilation Error.

---

# 🌍 Real-World Example

```java
final int MAX_LOGIN_ATTEMPTS = 3;
```

The value should never change during execution.

---

# 📝 Variable Naming Rules

✔ Can contain:

- Letters
- Digits
- `_`
- `$`

---

Cannot:

❌ Start with a digit

```java
int 1age;
```

---

Cannot use keywords

```java
int class;
```

---

Correct

```java
studentAge

employeeSalary

totalAmount
```

---

# 💡 Naming Conventions

| Type | Convention |
|--------|------------|
| Variable | camelCase |
| Constant | UPPER_CASE |
| Class | PascalCase |
| Method | camelCase |

Examples

```java
studentName

totalSalary

MAX_SIZE

Employee

calculateSalary()
```

---

# 🧠 Variable Shadowing

A local variable can hide an instance variable.

Example

```java
class Student {

    int age = 20;

    void display(){

        int age = 30;

        System.out.println(age);

    }

}
```

Output

```
30
```

To access the instance variable,

```java
this.age
```

---

# 🆕 var Keyword (Java 10+)

Java introduced local variable type inference.

Instead of

```java
String name = "Anshika";
```

You can write

```java
var name = "Anshika";
```

The compiler automatically determines the type.

---

## Limitations

✔ Only for local variables.

❌ Cannot be used for instance variables.

❌ Cannot initialize with `null`.

---

# 🧠 Memory Diagram

```text
               JVM Memory

+------------------------------+
|        Method Area           |
|------------------------------|
| Student.college = AKTU       |
+------------------------------+

+------------------------------+
|           Heap               |
|------------------------------|
| Student Object               |
| name = "Anshika"             |
| age = 21                     |
+------------------------------+

+------------------------------+
|           Stack              |
|------------------------------|
| studentRef                   |
| total = 2500                 |
+------------------------------+
```

---

# 🌍 Real-World Scenario

A student management system.

```java
class Student {

    static String college = "AKTU";

    String name;

    int age;

}
```

Memory

```
College

↓

Shared

↓

Every Student

↓

Own Name

↓

Own Age
```

Static data is shared.

Instance data is unique.

---

# ⚠ Common Mistakes

❌ Using local variables without initialization.

❌ Declaring unnecessary static variables.

❌ Confusing instance variables with local variables.

❌ Giving meaningless names like

```
a

b

c
```

---

# 💡 Best Practices

✔ Use descriptive variable names.

✔ Keep variable scope as small as possible.

✔ Use `final` whenever the value should not change.

✔ Avoid global/static variables unless necessary.

✔ Follow Java naming conventions consistently.

---

## 🚀 Coming in Part 3

- 🧩 40+ Interview Questions
- 🧪 Practice Problems
- 🎯 Interview Tips
- 💼 Industry Insights
- 📝 Quick Revision Sheet
- 📚 References
- 🔗 Related Topics
- Mermaid Diagrams
# 📘 Chapter 19: Encapsulation (Part 2)

## Advantages, Validation, Immutable Classes & Encapsulation vs Data Hiding

> *"Encapsulation is not just about making variables private. It is about controlling how data is accessed and modified, ensuring that objects always remain in a valid state."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the advantages of Encapsulation.
- Learn how validation works using Setter methods.
- Understand Immutable Classes.
- Differentiate Encapsulation and Data Hiding.
- Learn how Encapsulation improves software design.
- Understand internal object flow.

---

# 📚 Table of Contents

1. Advantages of Encapsulation
2. Data Validation
3. Encapsulation with Business Logic
4. Immutable Classes
5. Encapsulation vs Data Hiding
6. Internal Working
7. Memory Diagram
8. Real-World Example
9. Common Mistakes
10. Best Practices

---

# 📖 Advantages of Encapsulation

Encapsulation provides several benefits that make software more secure, maintainable, and flexible.

### ✅ Data Security

Private variables cannot be modified directly from outside the class.

```java
private double balance;
```

Only controlled methods can modify it.

---

### ✅ Data Validation

Every value passes through Setter methods before being stored.

```java
public void setAge(int age){

    if(age > 0){

        this.age = age;

    }

}
```

Invalid values are rejected.

---

### ✅ Flexibility

Internal implementation can change without affecting other classes.

For example,

today you store salary as

```java
double salary;
```

Later you decide to use

```java
BigDecimal salary;
```

Other classes continue using

```java
getSalary();
```

No code changes are required outside the class.

---

### ✅ Better Maintainability

Business rules remain inside one class instead of being scattered throughout the application.

---

### ✅ Loose Coupling

Other classes interact only through public methods.

They never depend on internal implementation details.

---

# 📖 Validation using Setter Methods

One of the biggest advantages of Encapsulation is validation.

Suppose we have an Employee class.

Wrong

```java
Employee e = new Employee();

e.salary = -5000;
```

A negative salary is invalid.

Instead,

```java
class Employee{

    private double salary;

    public void setSalary(double salary){

        if(salary > 0){

            this.salary = salary;

        }

    }

}
```

Now invalid values are automatically rejected.

---

# 💻 Example

```java
class Employee{

    private int age;

    public void setAge(int age){

        if(age >= 18){

            this.age = age;

        }else{

            System.out.println("Invalid Age");

        }

    }

    public int getAge(){

        return age;

    }

}

public class Main{

    public static void main(String[] args){

        Employee e = new Employee();

        e.setAge(15);

        System.out.println(e.getAge());

    }

}
```

Output

```
Invalid Age

0
```

---

# 📖 Encapsulation with Business Logic

Setter methods are not limited to assigning values.

They can also enforce business rules.

Example

```java
class BankAccount{

    private double balance;

    public void deposit(double amount){

        if(amount > 0){

            balance += amount;

        }

    }

}
```

Here,

the business rule is:

> Only positive amounts can be deposited.

---

# 📖 Immutable Classes

Sometimes we don't want an object's data to change after creation.

Such classes are called **Immutable Classes**.

Example

```java
final class Student{

    private final String name;

    Student(String name){

        this.name = name;

    }

    public String getName(){

        return name;

    }

}
```

Notice

- No Setter method
- Value assigned only once
- Object becomes read-only

---

# 🤔 Why Immutable Objects?

They provide

- Better Security
- Thread Safety
- Easier Debugging
- Predictable Behavior

Example

```java
String
```

is an immutable class.

```java
String name = "Java";

name.concat(" Programming");
```

The original string remains unchanged.

---

# 📖 Encapsulation vs Data Hiding

Many beginners think these terms mean the same thing.

They are related but different.

| Feature | Encapsulation | Data Hiding |
|----------|---------------|-------------|
| Definition | Wrapping data and methods together | Restricting direct access to data |
| Goal | Better design | Better security |
| Achieved Using | Classes | Access Modifiers |
| Focus | Entire Object | Variables |
| Includes | Data + Methods | Only Data Protection |

---

# 🧠 Internal Working

Suppose

```java
student.setAge(22);
```

Execution

```text
Method Called

        │

        ▼

Setter Executes

        │

Validation

        │

        ▼

Private Variable Updated

        │

        ▼

Object State Changed
```

Every modification passes through validation.

---

# 📦 Memory Diagram

```text
Stack

student

        │

        ▼

Heap

+----------------------+

age = 22

private

+----------------------+

        ▲

        │

setAge()

        │

Validation

        │

getAge()
```

The object itself controls how its data is modified.

---

# 🚀 Real-World Example

## Online Shopping Application

Every product has

```text
Price

Stock

Discount
```

Instead of allowing

```java
product.price = -100;
```

the application uses

```java
setPrice()
```

to validate

- Price > 0
- Discount within allowed range
- Stock cannot be negative

---

# 🌍 Real-World Applications

Encapsulation is heavily used in:

- Banking Systems
- E-commerce Platforms
- Hospital Management
- Airline Reservation Systems
- Student Portals
- Spring Boot Applications
- Hibernate Entities
- REST APIs
- JavaBeans

---

# ⚠️ Common Mistakes

## ❌ Public Fields

Wrong

```java
public String password;
```

Sensitive information should always be private.

---

## ❌ Setter Without Validation

Wrong

```java
public void setMarks(int marks){

    this.marks = marks;

}
```

Correct

```java
if(marks >= 0 && marks <= 100){

    this.marks = marks;

}
```

---

## ❌ Exposing Internal Collections

Wrong

```java
public List<String> getSubjects(){

    return subjects;

}
```

External code can modify the list.

Instead, return an unmodifiable copy when appropriate.

---

## ❌ Making Every Variable Public

Doing so completely breaks Encapsulation.

---

# 💡 Best Practices

- Keep instance variables private.
- Validate all incoming data.
- Expose only required methods.
- Prefer immutable objects where possible.
- Hide implementation details.
- Keep business rules inside the class.
- Follow JavaBeans naming conventions.

---

# 🎯 Interview Tip

### Question

What is the difference between Encapsulation and Data Hiding?

### Answer

**Encapsulation** is the process of combining data and methods into a single unit while providing controlled access to that data.

**Data Hiding** is a technique used within Encapsulation that prevents direct access to internal data using access modifiers like `private`.

Encapsulation focuses on object design, whereas Data Hiding focuses on protecting object data.

---

➡️ **Next: Part 3** will cover:

- Encapsulation vs Abstraction
- Interview Questions (Basic → Advanced)
- Time Complexity
- UML Diagram
- Quick Revision
- Practice Problems
- Chapter Summary
- Best Interview Answers
```
# 📘 Chapter 20: Enums (Part 2)

## Enum Methods, Constructors, Fields & Internal Working

> *"Enums in Java are much more powerful than simple constants. They can have constructors, variables, methods, and even implement interfaces, making them full-fledged classes with restricted instances."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Use built-in Enum methods.
- Create Enum constructors.
- Add variables and methods inside Enums.
- Understand how Enum constructors work.
- Learn the internal working of Enums.
- Follow best practices.

---

# 📚 Table of Contents

1. Built-in Enum Methods
2. values() Method
3. ordinal() Method
4. name() Method
5. valueOf() Method
6. Enum Constructors
7. Enum Variables (Fields)
8. Enum Methods
9. Internal Working
10. Common Mistakes
11. Best Practices

---

# 📖 Built-in Enum Methods

Every Enum automatically inherits several useful methods from the `java.lang.Enum` class.

Some commonly used methods are:

- `values()`
- `ordinal()`
- `name()`
- `valueOf()`
- `compareTo()`
- `toString()`

---

# 📖 values() Method

The `values()` method returns an array containing all enum constants in the order they are declared.

Example

```java
enum Day{

    MONDAY,
    TUESDAY,
    WEDNESDAY

}

public class Demo{

    public static void main(String[] args){

        for(Day d : Day.values()){

            System.out.println(d);

        }

    }

}
```

Output

```text
MONDAY
TUESDAY
WEDNESDAY
```

---

# 📖 ordinal() Method

The `ordinal()` method returns the position (index) of an enum constant.

Index starts from **0**.

Example

```java
enum Day{

    MONDAY,
    TUESDAY,
    WEDNESDAY

}

public class Demo{

    public static void main(String[] args){

        System.out.println(Day.MONDAY.ordinal());

        System.out.println(Day.WEDNESDAY.ordinal());

    }

}
```

Output

```text
0
2
```

> ⚠️ **Best Practice:** Avoid using `ordinal()` for business logic because changing the declaration order changes the ordinal values.

---

# 📖 name() Method

The `name()` method returns the exact name of the enum constant.

Example

```java
System.out.println(Day.MONDAY.name());
```

Output

```text
MONDAY
```

---

# 📖 valueOf() Method

The `valueOf()` method converts a String into an enum constant.

Example

```java
Day d = Day.valueOf("MONDAY");

System.out.println(d);
```

Output

```text
MONDAY
```

If the String does not match any constant exactly, Java throws an `IllegalArgumentException`.

Example

```java
Day.valueOf("Monday");
```

Output

```text
Exception in thread "main"
java.lang.IllegalArgumentException
```

---

# 📖 Enum Constructors

Enums can have constructors.

Example

```java
enum Laptop{

    DELL,
    HP,
    ASUS;

    Laptop(){

        System.out.println("Constructor Called");

    }

}
```

Output

```text
Constructor Called
Constructor Called
Constructor Called
```

The constructor is called **once for each enum constant** when the enum class is loaded.

---

# 📖 Parameterized Enum Constructor

```java
enum Laptop{

    DELL(60000),
    HP(55000),
    ASUS(70000);

    int price;

    Laptop(int price){

        this.price = price;

    }

}
```

Accessing

```java
System.out.println(Laptop.DELL.price);
```

Output

```text
60000
```

---

# 📖 Enum Variables (Fields)

Enums can have instance variables.

Example

```java
enum Level{

    LOW(1),
    MEDIUM(2),
    HIGH(3);

    private int priority;

    Level(int priority){

        this.priority = priority;

    }

    public int getPriority(){

        return priority;

    }

}
```

Usage

```java
System.out.println(Level.HIGH.getPriority());
```

Output

```text
3
```

---

# 📖 Enum Methods

Enums can contain methods just like normal classes.

Example

```java
enum Day{

    MONDAY,
    TUESDAY;

    public void message(){

        System.out.println("Have a nice day!");

    }

}
```

Usage

```java
Day.MONDAY.message();
```

Output

```text
Have a nice day!
```

---

# 💻 Complete Example

```java
enum Laptop{

    DELL(60000),
    HP(55000),
    ASUS(70000);

    private int price;

    Laptop(int price){

        this.price = price;

    }

    public int getPrice(){

        return price;

    }

}

public class Demo{

    public static void main(String[] args){

        for(Laptop l : Laptop.values()){

            System.out.println(

                l + " : " + l.getPrice()

            );

        }

    }

}
```

Output

```text
DELL : 60000
HP : 55000
ASUS : 70000
```

---

# 📦 Internal Working

Consider

```java
enum Day{

    MONDAY,
    TUESDAY

}
```

Internally, it behaves similarly to:

```java
final class Day extends Enum<Day>{

    public static final Day MONDAY = new Day();

    public static final Day TUESDAY = new Day();

    private Day(){

    }

}
```

Important points:

- Enum constructors are implicitly **private**.
- Enum constants are created only once.
- No object can be created using `new`.

---

# ⚠️ Common Mistakes

## ❌ Trying to Create an Enum Object

Wrong

```java
Day d = new Day();
```

Compile-time Error.

---

## ❌ Assuming values() is an Instance Method

Wrong

```java
Day.MONDAY.values();
```

Correct

```java
Day.values();
```

---

## ❌ Using ordinal() for Database Values

Wrong

```java
if(day.ordinal() == 2){

    // Business Logic

}
```

If the order of constants changes, the logic breaks.

Prefer explicit fields.

---

## ❌ Incorrect Case with valueOf()

Wrong

```java
Day.valueOf("monday");
```

Correct

```java
Day.valueOf("MONDAY");
```

---

# 💡 Best Practices

- Use Enums instead of integer or String constants.
- Prefer explicit fields over `ordinal()`.
- Keep Enum names in uppercase.
- Use `switch` with Enums for clean branching.
- Add meaningful methods inside Enums when behavior belongs to the constants.
- Do not rely on declaration order for application logic.

---

# 🌍 Real-World Applications

Enums are commonly used in:

- Payment Status
- Order Tracking
- User Roles
- Game Levels
- API Response Status
- Traffic Signals
- Log Levels
- File Permissions
- Days and Months
- Workflow States

---

# 🎯 Interview Tip

### Question

Can an Enum have constructors and methods?

### Answer

✅ Yes.

Enums are special classes. They can have:

- Constructors
- Instance variables
- Methods
- Static methods
- Implement interfaces

However, **their constructors cannot be called explicitly**, and enum constants are created automatically by the JVM.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Enum vs Constants
- Enum vs Classes
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision
- Chapter Summary
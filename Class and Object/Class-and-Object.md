# 📘 Class and Object in Java

> "A class is a blueprint, and an object is the real-world instance created from that blueprint."

---

# 📚 Table of Contents

- What is OOP?
- What is a Class?
- What is an Object?
- Class vs Object
- How to Create an Object
- Example
- Memory Management (Stack & Heap)
- Instance Variable vs Local Variable
- Methods
- Method Overloading
- Interview Questions
- Quick Revision

---

# 🚀 Object-Oriented Programming (OOP)

Object-Oriented Programming (OOP) is a programming paradigm where programs are designed using **objects**.

Every object contains:

- **Properties (State)**
- **Behavior (Methods)**

### Real-Life Example

## Car

Properties

- Brand
- Color
- Speed

Behavior

- Start()
- Stop()
- Accelerate()

---

# 🏗️ What is a Class?

## Definition

A **Class** is a blueprint or template used to create objects.

A class defines:

- Data (Variables)
- Behavior (Methods)

### Syntax

```java
class Calculator{

}
```

---

# 🧱 Example of Class

```java
class Calculator {

    int version = 1;

    public int add(int a, int b){
        return a + b;
    }

}
```

Here,

- `version` → Property
- `add()` → Behavior

---

# 🎯 What is an Object?

An **Object** is an instance of a class.

When an object is created:

- Memory is allocated.
- Variables and methods become accessible.

---

## Real-Life Analogy

```
Blueprint
      ↓

House 1

House 2

House 3
```

Blueprint = Class

House = Object

---

# 📝 How to Create an Object?

## Syntax

```java
ClassName objectName = new ClassName();
```

Example

```java
Calculator calc = new Calculator();
```

Explanation

| Part | Meaning |
|------|----------|
| Calculator | Class Name |
| calc | Reference Variable |
| new | Allocates Memory |
| Calculator() | Constructor |

---

# 🎯 Calling Methods

```java
int result = calc.add(5,4);

System.out.println(result);
```

Output

```
9
```

---

# 💻 Complete Program

```java
class Calculator{

    public int add(int a,int b){
        return a+b;
    }

}

public class Demo{

    public static void main(String[] args){

        Calculator calc = new Calculator();

        int result = calc.add(5,4);

        System.out.println(result);

    }

}
```

Output

```
9
```

---

# 🧠 Memory Management

When we write

```java
Calculator calc = new Calculator();
```

### Stack Memory

```
calc
↓

101
```

### Heap Memory

```
Address 101

Calculator Object
```

The reference variable (`calc`) stores only the memory address.

The actual object is stored inside the Heap.

---

# 📦 Stack vs Heap

| Stack | Heap |
|---------|---------|
| Stores local variables | Stores Objects |
| Stores method calls | Stores Instance Variables |
| Faster | Larger Memory |
| Automatically cleared | Cleared by Garbage Collector |

---

# 🔥 Instance Variable

```java
class Student{

    int age;

}
```

Each object gets its own copy.

```java
Student s1 = new Student();

Student s2 = new Student();

s1.age = 20;

s2.age = 18;
```

Output

```
s1.age = 20

s2.age = 18
```

---

# 📌 Local Variable

```java
public void display(){

    int x = 10;

}
```

- Created inside method.
- Lives only while method executes.
- Stored inside Stack Memory.

---

# ⚙️ Methods

A method is a block of code that performs a particular task.

Example

```java
public void playMusic(){

    System.out.println("Playing Music");

}
```

---

# 🔙 Method Returning Value

```java
public int getNumber(){

    return 5;

}
```

---

# 📝 Method Returning String

```java
public String getPen(int cost){

    if(cost>=10){
        return "Pen";
    }

    return "Nothing";

}
```

---

# 🔄 Method Overloading

Method Overloading means:

- Same method name
- Different parameter list

Example

```java
class Calculator{

    public int add(int a,int b){
        return a+b;
    }

    public int add(int a,int b,int c){
        return a+b+c;
    }

    public double add(double a,double b){
        return a+b;
    }

}
```

---

# ❌ Invalid Method Overloading

Changing only return type is NOT method overloading.

```java
int add(int a,int b)

double add(int a,int b)
```

Compilation Error ❌

---

# 💡 Key Points

✅ Class is a blueprint.

✅ Object is an instance.

✅ Object is stored in Heap.

✅ Reference variable is stored in Stack.

✅ Methods define behavior.

✅ Variables define state.

✅ One class can create multiple objects.

---

# 🧠 Frequently Asked Interview Questions

## Q1. What is a Class?

A class is a blueprint used to create objects.

---

## Q2. What is an Object?

An object is an instance of a class.

---

## Q3. What is the difference between Class and Object?

| Class | Object |
|---------|----------|
| Blueprint | Instance |
| Logical Entity | Physical Entity |
| No Memory | Memory Allocated |

---

## Q4. What does the `new` keyword do?

It allocates memory in Heap and creates an object.

---

## Q5. Where is an object stored?

Heap Memory.

---

## Q6. Where is the reference variable stored?

Stack Memory.

---

## Q7. Can we create multiple objects from one class?

Yes.

---

## Q8. Difference between Local Variable and Instance Variable?

| Local Variable | Instance Variable |
|----------------|-------------------|
| Inside Method | Inside Class |
| Stack | Heap |
| No Default Value | Default Value Exists |

---

## Q9. What is a Method?

A method is a block of code that performs a specific task.

---

## Q10. What is Method Overloading?

Same method name with different parameter lists.

---

## Q11. Can methods be overloaded by changing only the return type?

No.

---

# 📌 Quick Revision

- Class = Blueprint
- Object = Instance
- Object → Heap
- Reference Variable → Stack
- Method = Behavior
- Variable = State
- new = Creates Object
- One Class → Multiple Objects
- Method Overloading = Same Name + Different Parameters

---

# 🎯 Practice Questions

1. Create a `Student` class with `name` and `age`.
2. Create three objects of `Student`.
3. Create a `Car` class with `start()` and `stop()` methods.
4. Demonstrate Method Overloading.
5. Explain Stack and Heap using a memory diagram.

---

⭐ **Tip for Interviews:** Don't just memorize definitions. Be ready to explain **what happens in memory** when you execute:

```java
Calculator calc = new Calculator();
```

Interviewers often ask this follow-up question to test your understanding.
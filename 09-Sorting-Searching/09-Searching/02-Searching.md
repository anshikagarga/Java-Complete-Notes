# 📘 Chapter 09: Searching (Part 2)

> *"Java provides built-in searching methods that are optimized and easy to use. Understanding both manual searching algorithms and Java library methods is essential for writing efficient and interview-ready code."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Use `Arrays.binarySearch()`
- Use `Collections.binarySearch()`
- Search Objects
- Understand Recursive Binary Search
- Learn Searching with Comparator
- Understand Advanced Searching Techniques

---

# 📚 Table of Contents

1. Arrays.binarySearch()
2. Collections.binarySearch()
3. Recursive Binary Search
4. Searching Objects
5. Searching using Comparator
6. Advanced Examples
7. Internal Working
8. Best Practices
9. Common Mistakes
10. Interview Tips

---

# 📖 Arrays.binarySearch()

Java provides a built-in Binary Search method.

Package

```java
java.util.Arrays
```

Syntax

```java
Arrays.binarySearch(array, key);
```

Returns

- Index of the element if found
- Negative value if not found

---

# 💻 Example

```java
import java.util.Arrays;

public class Demo {

    public static void main(String[] args) {

        int arr[] = {10,20,30,40,50,60};

        int index = Arrays.binarySearch(arr,40);

        System.out.println(index);

    }

}
```

Output

```text
3
```

---

# 📖 Element Not Found

```java
import java.util.Arrays;

public class Demo {

    public static void main(String[] args) {

        int arr[] = {10,20,30,40,50};

        System.out.println(

        Arrays.binarySearch(arr,100)

        );

    }

}
```

Output

```text
Negative Value
```

Example

```text
-6
```

A negative value means the element does not exist.

---

# 📖 Important Rule

The array **must be sorted**.

Correct

```java
int arr[] = {10,20,30,40,50};
```

Wrong

```java
int arr[] = {40,10,50,20,30};
```

---

# 📖 Collections.binarySearch()

Used for searching in a **List**.

Package

```java
java.util.Collections
```

Syntax

```java
Collections.binarySearch(list,key);
```

---

# 💻 Example

```java
import java.util.*;

public class Demo {

    public static void main(String[] args) {

        List<Integer> list =

        Arrays.asList(10,20,30,40,50);

        int index =

        Collections.binarySearch(list,30);

        System.out.println(index);

    }

}
```

Output

```text
2
```

---

# 📖 Recursive Binary Search

Binary Search can also be implemented recursively.

Algorithm

```text
Search

↓

Find Middle

↓

Match?

↓

Yes

↓

Return

↓

No

↓

Call Left Half

or

Right Half
```

---

# 💻 Java Program

```java
public class Demo {

    static int binarySearch(int arr[],

                            int low,

                            int high,

                            int key){

        if(low > high){

            return -1;

        }

        int mid = low + (high-low)/2;

        if(arr[mid] == key){

            return mid;

        }

        if(arr[mid] > key){

            return binarySearch(

            arr,

            low,

            mid-1,

            key

            );

        }

        return binarySearch(

        arr,

        mid+1,

        high,

        key

        );

    }

    public static void main(String[] args){

        int arr[] =

        {10,20,30,40,50,60};

        System.out.println(

        binarySearch(

        arr,

        0,

        arr.length-1,

        50

        ));

    }

}
```

Output

```text
4
```

---

# 📖 Searching Objects

Suppose

```java
class Student{

    int id;

    String name;

}
```

Search by ID

```java
for(Student s : students){

    if(s.getId() == 101){

        System.out.println(s);

    }

}
```

This is **Linear Search**.

---

# 📖 Binary Search on Objects

Objects must first be sorted.

Example

```java
Collections.sort(

students,

Comparator.comparing(

Student::getId

)

);
```

Now

```java
Collections.binarySearch(

students,

new Student(101,""),

Comparator.comparing(

Student::getId

)

);
```

Java compares objects using the supplied Comparator.

---

# 📖 Searching using Comparator

Example

```java
Comparator<Student> cmp =

Comparator.comparing(

Student::getMarks

);
```

Search

```java
Collections.binarySearch(

students,

new Student(0,"Rahul",95),

cmp

);
```

The list **must already be sorted using the same Comparator**.

---

# 📖 Advanced Example

Search Employee

```java
Employee target =

new Employee(

101,

"Anshika",

80000

);

int index =

Collections.binarySearch(

employees,

target,

Comparator.comparing(

Employee::getId

)

);
```

Output

```text
Employee Found
```

---

# 📊 Linear Search vs Binary Search

| Feature | Linear Search | Binary Search |
|----------|---------------|---------------|
| Data | Sorted/Unsorted | Sorted Only |
| Speed | Slower | Faster |
| Best Case | O(1) | O(1) |
| Average Case | O(n) | O(log n) |
| Worst Case | O(n) | O(log n) |

---

# 📦 Internal Working

```text
Sorted Collection

↓

Binary Search

↓

Find Middle

↓

Compare

↓

Left Half

or

Right Half

↓

Repeat

↓

Found
```

---

# 💡 Best Practices

- Always sort data before using Binary Search.
- Use `Arrays.binarySearch()` for arrays.
- Use `Collections.binarySearch()` for lists.
- Use the same Comparator for sorting and searching objects.
- Use Linear Search for very small or unsorted datasets.
- Prefer Binary Search for large sorted datasets.

---

# ⚠️ Common Mistakes

## ❌ Binary Search on Unsorted Data

Wrong

```java
int arr[] = {40,10,20,50};
```

Correct

```java
Arrays.sort(arr);

Arrays.binarySearch(arr,20);
```

---

## ❌ Using Different Comparators

Wrong

```java
Collections.sort(

students,

Comparator.comparing(Student::getId)

);

Collections.binarySearch(

students,

student,

Comparator.comparing(Student::getMarks)

);
```

Sorting and searching use different criteria, producing incorrect results.

Correct

Use the **same Comparator** for both operations.

---

## ❌ Ignoring Negative Return Values

Wrong

```java
int index =

Arrays.binarySearch(arr,100);

System.out.println(arr[index]);
```

This may throw an exception.

Correct

```java
if(index >= 0){

    System.out.println("Found");

}

else{

    System.out.println("Not Found");

}
```

---

# 🌍 Real-World Applications

Searching algorithms are used in:

- Search Engines
- Banking Systems
- Student Record Systems
- Employee Databases
- E-Commerce Product Search
- Hospital Management Systems
- Airline Reservation Systems
- Library Management
- Spring Boot REST APIs
- Inventory Management

---

# 🎯 Interview Tip

### Question

What is the difference between `Arrays.binarySearch()` and `Collections.binarySearch()`?

### Answer

- `Arrays.binarySearch()` is used to search **arrays**.
- `Collections.binarySearch()` is used to search **List** implementations.
- Both require the data to be **sorted** before searching.
- Both have a time complexity of **O(log n)**.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Interview Questions
- MCQs
- Coding Practice
- Best Practices Revision
- Chapter Summary
- Frequently Asked Interview Scenarios
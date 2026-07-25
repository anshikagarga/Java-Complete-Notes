# 📘 Chapter 09: Searching (Part 1)

> *"Searching is one of the most fundamental operations in Computer Science. Whether you're finding a student's record, searching for a product on an e-commerce website, or locating a file in a system, searching algorithms are used everywhere."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Searching
- Learn different Searching Techniques
- Understand Linear Search
- Understand Binary Search
- Learn when to use each searching algorithm
- Understand Time Complexity
- Learn Java searching methods

---

# 📚 Table of Contents

1. Introduction to Searching
2. Types of Searching
3. Linear Search
4. Binary Search
5. Time Complexity
6. Internal Working
7. Best Practices
8. Common Mistakes
9. Interview Tips

---

# 📖 What is Searching?

Searching is the process of finding a particular element inside a collection of data.

For example,

Suppose we have

```text
10 20 30 40 50
```

Search

```text
40
```

Output

```text
Element Found
```

If the element does not exist,

Output

```text
Element Not Found
```

---

# 🌍 Real-World Examples

Searching is used in

- Google Search
- Student Management Systems
- Employee Records
- Banking Applications
- E-Commerce Websites
- Hospital Management Systems
- Library Management
- Mobile Contact Search

---

# 📖 Types of Searching

There are two major searching algorithms:

## 1️⃣ Linear Search

Checks each element one by one.

```text
10

↓

20

↓

30

↓

40

↓

50
```

---

## 2️⃣ Binary Search

Repeatedly divides the sorted array into two halves.

```text
10 20 30 40 50 60 70

↓

Middle

↓

Left or Right

↓

Repeat
```

---

# 📊 Linear Search

Linear Search is the simplest searching algorithm.

It checks every element until the required element is found.

No sorting is required.

---

## Algorithm

```text
Start

↓

Check First Element

↓

Match?

↓

Yes → Found

↓

No

↓

Next Element

↓

Repeat

↓

End
```

---

# 📖 Linear Search Example

Array

```text
25 10 50 40 70
```

Search

```text
40
```

Steps

```text
25 ❌

↓

10 ❌

↓

50 ❌

↓

40 ✅
```

Found at index

```text
3
```

---

# 💻 Java Program (Linear Search)

```java
public class LinearSearch {

    public static int linearSearch(int arr[], int key){

        for(int i = 0; i < arr.length; i++){

            if(arr[i] == key){

                return i;

            }

        }

        return -1;

    }

    public static void main(String[] args){

        int arr[] = {25,10,50,40,70};

        int key = 40;

        int index = linearSearch(arr,key);

        if(index != -1){

            System.out.println("Element Found at Index : " + index);

        }

        else{

            System.out.println("Element Not Found");

        }

    }

}
```

Output

```text
Element Found at Index : 3
```

---

# 📖 Time Complexity of Linear Search

| Case | Complexity |
|------|------------|
| Best Case | O(1) |
| Average Case | O(n) |
| Worst Case | O(n) |

---

# 📖 Binary Search

Binary Search is a much faster searching algorithm.

It works only on **sorted data**.

Instead of checking every element,

it repeatedly divides the search space into two halves.

---

## Binary Search Requirement

The array **must be sorted**.

Correct

```text
10 20 30 40 50 60
```

Wrong

```text
20 50 10 40 30
```

---

# 📖 Binary Search Algorithm

```text
Start

↓

Find Middle

↓

Key == Middle ?

↓

Yes → Found

↓

No

↓

Key < Middle ?

↓

Search Left Half

OR

Search Right Half

↓

Repeat
```

---

# 📖 Example

Sorted Array

```text
10 20 30 40 50 60 70
```

Search

```text
60
```

Step 1

```text
Middle = 40
```

Since

```text
60 > 40
```

Search Right

```text
50 60 70
```

Middle

```text
60
```

Found.

---

# 💻 Java Program (Binary Search)

```java
public class BinarySearch {

    public static int binarySearch(int arr[], int key){

        int low = 0;

        int high = arr.length - 1;

        while(low <= high){

            int mid = low + (high - low) / 2;

            if(arr[mid] == key){

                return mid;

            }

            else if(arr[mid] < key){

                low = mid + 1;

            }

            else{

                high = mid - 1;

            }

        }

        return -1;

    }

    public static void main(String[] args){

        int arr[] = {10,20,30,40,50,60,70};

        int key = 60;

        int index = binarySearch(arr,key);

        if(index != -1){

            System.out.println("Element Found at Index : " + index);

        }

        else{

            System.out.println("Element Not Found");

        }

    }

}
```

Output

```text
Element Found at Index : 5
```

---

# 📊 Linear Search vs Binary Search

| Feature | Linear Search | Binary Search |
|----------|---------------|---------------|
| Data Required | Any | Sorted |
| Best Case | O(1) | O(1) |
| Average Case | O(n) | O(log n) |
| Worst Case | O(n) | O(log n) |
| Faster | ❌ | ✅ |
| Easy to Implement | ✅ | ✅ |

---

# 📦 Internal Working

```text
User Searches

↓

Linear Search

↓

Check Every Element

↓

Found / Not Found
```

OR

```text
User Searches

↓

Binary Search

↓

Find Middle

↓

Left / Right

↓

Repeat

↓

Found
```

---

# 💡 Best Practices

- Use **Linear Search** for small or unsorted datasets.
- Use **Binary Search** only when the data is sorted.
- Prefer `Arrays.binarySearch()` for arrays instead of implementing Binary Search manually when appropriate.
- Always calculate the middle index as:

```java
int mid = low + (high - low) / 2;
```

to avoid integer overflow.

---

# ⚠️ Common Mistakes

## ❌ Using Binary Search on an Unsorted Array

Wrong

```text
50 20 10 70 40
```

Binary Search will produce incorrect results.

Correct

```text
10 20 40 50 70
```

---

## ❌ Incorrect Middle Calculation

Wrong

```java
int mid = (low + high) / 2;
```

Correct

```java
int mid = low + (high - low) / 2;
```

---

## ❌ Forgetting to Update low or high

Wrong

```java
while(low <= high){

    // Missing low/high update

}
```

This can cause an infinite loop.

---

# 🎯 Interview Tip

### Question

Which searching algorithm is faster: Linear Search or Binary Search?

### Answer

Binary Search is faster because it reduces the search space by half in every iteration and has a time complexity of **O(log n)**. However, it only works on **sorted data**, whereas Linear Search works on both sorted and unsorted collections.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Arrays.binarySearch()
- Collections.binarySearch()
- Searching Objects
- Recursive Binary Search
- Advanced Searching Examples
- Searching with Comparator
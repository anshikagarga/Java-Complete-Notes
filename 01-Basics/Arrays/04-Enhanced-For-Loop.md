# 🔁 Enhanced For Loop (For-Each Loop) in Java

The **Enhanced For Loop**, also known as the **For-Each Loop**, is a simplified way to traverse arrays and collections.

It automatically accesses each element one by one without using an index.

---

# Why do we need an Enhanced For Loop?

Suppose we have an array:

```java
int[] nums = {4, 8, 3, 9};
```

Using a normal `for` loop:

```java
for (int i = 0; i < nums.length; i++) {
    System.out.println(nums[i]);
}
```

This requires:

- Managing the counter (`i`)
- Knowing the array length
- Accessing elements using the index

Using an enhanced for loop:

```java
for (int n : nums) {
    System.out.println(n);
}
```

Much cleaner and easier to read.

---

# Syntax

```java
for(dataType variable : array){
    // code
}
```

Example:

```java
int[] nums = {4, 8, 3, 9};

for(int n : nums){
    System.out.println(n);
}
```

Output

```
4
8
3
9
```

---

# How Does It Work?

Array:

```
Index

0 → 4
1 → 8
2 → 3
3 → 9
```

Enhanced for loop:

```java
for(int n : nums)
```

Iteration:

```
n = 4

n = 8

n = 3

n = 9
```

One element is assigned to `n` during each iteration.

---

# Example with Student Objects

```java
class Student{

    int rollNo;
    String name;
    int marks;

}
```

```java
Student[] students = {s1, s2, s3};

for(Student student : students){

    System.out.println(student.name);
    System.out.println(student.marks);

}
```

Output

```
Navin 88
Harsh 67
Kiran 97
```

---

# Enhanced For Loop with 2D Arrays

```java
int[][] nums = {

    {5,2,6,1},
    {3,2,7,4},
    {4,8,1,2}

};
```

Traversal

```java
for(int[] row : nums){

    for(int value : row){

        System.out.print(value + " ");

    }

    System.out.println();

}
```

Output

```
5 2 6 1
3 2 7 4
4 8 1 2
```

---

# Advantages

- Cleaner syntax
- Easy to read
- No need to manage indexes
- Less chance of mistakes
- Best for traversal

---

# Limitations

## Cannot Access Index

This is **not possible**:

```java
for(int n : nums){

    System.out.println(index);

}
```

Because there is no index variable.

---

## Cannot Traverse in Reverse

Normal loop:

```java
for(int i = nums.length - 1; i >= 0; i--){

}
```

Enhanced loop cannot do this.

---

## Cannot Skip Elements Easily

With a normal loop:

```java
for(int i = 0; i < nums.length; i += 2){

}
```

Enhanced for loop always visits every element.

---

## Cannot Replace Primitive Elements

```java
for(int n : nums){

    n = 100;

}
```

Output

```
Array remains unchanged.
```

Because `n` is only a copy of each element.

Correct way:

```java
for(int i = 0; i < nums.length; i++){

    nums[i] = 100;

}
```

---

# Comparison

| Normal For Loop | Enhanced For Loop |
|-----------------|-------------------|
| Uses index | No index |
| Can update elements | Limited for primitives |
| Can traverse backwards | No |
| Can skip elements | No |
| Easier to write | ✅ Yes |
| Best for reading data | ✅ Yes |

---

# Time Complexity

| Operation | Complexity |
|-----------|------------|
| Traversal | O(n) |

---

# When Should You Use It?

Use the enhanced for loop when:

- You only need to read elements.
- You don't need the index.
- You don't need reverse traversal.
- You want cleaner code.

---

# Interview Questions

## 1. What is an Enhanced For Loop?

It is a simplified loop used to iterate over arrays and collections without using an index.

---

## 2. Can we modify array elements using an Enhanced For Loop?

For primitive types like `int`, changes won't affect the original array because the loop variable stores a copy.

For object references, you can modify the object's fields.

Example:

```java
for(Student student : students){

    student.marks = 100;

}
```

This updates the original objects.

---

## 3. Can we access the index in an Enhanced For Loop?

No.

---

## 4. Can we iterate in reverse order?

No.

---

# Common Mistakes

❌ Trying to access the index.

```java
for(int n : nums){

}
```

No index exists.

---

❌ Trying to update primitive values.

```java
for(int n : nums){

    n = 50;

}
```

Original array remains unchanged.

---

# Key Takeaways

- Enhanced For Loop is also called the **For-Each Loop**.
- It automatically visits every element.
- It is simpler than a traditional `for` loop.
- It is ideal for reading data.
- It cannot access indexes or traverse backward.
- It works with arrays and collections.
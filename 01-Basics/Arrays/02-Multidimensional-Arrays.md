# 📚 Multidimensional Arrays in Java

A **multidimensional array** is an **array of arrays**.

The most commonly used multidimensional array is the **2D array**, which represents data in the form of **rows and columns**.

---

# Why do we need Multidimensional Arrays?

Suppose we want to store marks of 3 students in 4 subjects.

Without a 2D array:

```java
int[] student1 = {52, 61, 78, 90};
int[] student2 = {64, 85, 91, 70};
int[] student3 = {75, 81, 68, 95};
```

Using a 2D array:

```java
int[][] marks = {
    {52, 61, 78, 90},
    {64, 85, 91, 70},
    {75, 81, 68, 95}
};
```

---

# Syntax

## Declaration

```java
int[][] nums;
```

## Declaration + Memory Allocation

```java
int[][] nums = new int[3][4];
```

This means:

- 3 Rows
- 4 Columns

---

# Memory Representation

```
        Column
       0   1   2   3

Row 0 [5] [2] [6] [1]

Row 1 [3] [2] [7] [4]

Row 2 [4] [8] [1] [2]
```

Element Position:

```
nums[0][0] = 5
nums[0][2] = 6
nums[1][3] = 4
nums[2][1] = 8
```

---

# Accessing Elements

```java
System.out.println(nums[1][2]);
```

Output

```
7
```

---

# Updating Elements

```java
nums[2][3] = 100;
```

Now,

```
4 8 1 100
```

---

# Traversing a 2D Array

Using Nested Loops

```java
for(int i = 0; i < nums.length; i++)
{
    for(int j = 0; j < nums[i].length; j++)
    {
        System.out.print(nums[i][j] + " ");
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

# Enhanced For Loop

```java
for(int[] row : nums)
{
    for(int value : row)
    {
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

# Jagged Array

A **Jagged Array** is a multidimensional array where **each row can have a different number of columns**.

Unlike a normal 2D array, every row does not need to have the same size.

---

## Syntax

```java
int[][] nums = new int[3][];
```

Now allocate memory for each row separately.

```java
nums[0] = new int[3];
nums[1] = new int[4];
nums[2] = new int[2];
```

Memory Representation

```
Row 0 -> [ ][ ][ ]

Row 1 -> [ ][ ][ ][ ]

Row 2 -> [ ][ ]
```

---

# Traversing Jagged Array

```java
for(int i = 0; i < nums.length; i++)
{
    for(int j = 0; j < nums[i].length; j++)
    {
        System.out.print(nums[i][j] + " ");
    }

    System.out.println();
}
```

Or using Enhanced For Loop

```java
for(int[] row : nums)
{
    for(int value : row)
    {
        System.out.print(value + " ");
    }

    System.out.println();
}
```

---

# Three-Dimensional Array

A **3D array** is an array of 2D arrays.

Syntax

```java
int[][][] nums = new int[3][4][5];
```

Meaning

- 3 Blocks
- 4 Rows
- 5 Columns

Accessing an element

```java
nums[1][2][3] = 50;
```

---

# Advantages

✅ Organizes data into rows and columns.

✅ Easy to represent matrices and tables.

✅ Faster element access using indexes.

✅ Useful in games, image processing, and scientific computing.

---

# Disadvantages

❌ Fixed size.

❌ Stores only one data type.

❌ Can waste memory if many elements are unused.

❌ Nested loops make traversal slightly more complex.

---

# Time Complexity

| Operation | Complexity |
|-----------|------------|
| Access | O(1) |
| Update | O(1) |
| Traversal | O(rows × columns) |

---

# Interview Questions

### Q1. What is a multidimensional array?

A multidimensional array is an array whose elements are themselves arrays.

---

### Q2. What is a Jagged Array?

A jagged array is a multidimensional array where each row can have a different number of columns.

---

### Q3. Difference between 2D Array and Jagged Array?

| 2D Array | Jagged Array |
|-----------|--------------|
| Same number of columns in every row | Different number of columns allowed |
| Fixed structure | Flexible structure |

---

# Key Takeaways

- A multidimensional array is an array of arrays.
- A 2D array stores data in rows and columns.
- Nested loops are used to traverse 2D arrays.
- Enhanced for loop makes traversal simpler.
- Jagged arrays allow variable-sized rows.
- A 3D array is an array of 2D arrays.
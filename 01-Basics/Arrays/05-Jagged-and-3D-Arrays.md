# 📚 Jagged Arrays and Three-Dimensional Arrays in Java

> **Prerequisites**
>
> - Arrays
> - Multidimensional Arrays
> - Nested Loops

---

# 🎯 Learning Objectives

After reading this chapter, you will be able to:

- Understand what a Jagged Array is.
- Differentiate between a 2D Array and a Jagged Array.
- Create and traverse Jagged Arrays.
- Understand the concept of 3D Arrays.
- Learn where these arrays are used in real-world applications.

---

# 📖 What is a Jagged Array?

A **Jagged Array** is a multidimensional array where **each row can have a different number of columns**.

Unlike a normal 2D array, every row does **not** need to be of the same length.

---

# 🧠 Why do we need Jagged Arrays?

Suppose we want to store marks of students.

Student A has **3 subjects**.

Student B has **5 subjects**.

Student C has **2 subjects**.

A normal 2D array wastes memory because every row must have the same number of columns.

Jagged Arrays solve this problem.

---

# 📦 Syntax

```java
int[][] nums = new int[3][];
```

Here,

- 3 rows are created.
- Columns are **not allocated** yet.

---

# Allocate Memory

```java
nums[0] = new int[3];
nums[1] = new int[5];
nums[2] = new int[2];
```

---

# 🖥 Memory Representation

```
nums

Row 0
+---+---+---+
|   |   |   |
+---+---+---+

Row 1
+---+---+---+---+---+
|   |   |   |   |   |
+---+---+---+---+---+

Row 2
+---+---+
|   |   |
+---+---+
```

Notice that each row has a different size.

---

# Example

```java
public class JaggedArray {

    public static void main(String[] args) {

        int[][] nums = new int[3][];

        nums[0] = new int[3];
        nums[1] = new int[4];
        nums[2] = new int[2];

    }

}
```

---

# Storing Values

```java
nums[0][0] = 10;
nums[0][1] = 20;
nums[0][2] = 30;

nums[1][0] = 40;
nums[1][1] = 50;
nums[1][2] = 60;
nums[1][3] = 70;

nums[2][0] = 80;
nums[2][1] = 90;
```

---

# Traversing Jagged Array

```java
for(int i = 0; i < nums.length; i++) {

    for(int j = 0; j < nums[i].length; j++) {

        System.out.print(nums[i][j] + " ");

    }

    System.out.println();

}
```

Output

```
10 20 30
40 50 60 70
80 90
```

---

# Enhanced For Loop

```java
for(int[] row : nums){

    for(int value : row){

        System.out.print(value + " ");

    }

    System.out.println();

}
```

---

# 💡 Behind the Scenes

Java does **not** create one large block of memory.

Instead,

```
nums
 │
 ├──► Row 0 → int[3]
 │
 ├──► Row 1 → int[4]
 │
 └──► Row 2 → int[2]
```

Every row is an independent array.

---

# 🚀 Three-Dimensional Array

A **3D Array** is an array of 2D arrays.

Think of it like multiple tables stacked together.

---

# Syntax

```java
int[][][] cube = new int[3][4][5];
```

Meaning

- 3 Tables
- 4 Rows
- 5 Columns

---

# Memory Diagram

```
Block 0

[ ][ ][ ][ ]
[ ][ ][ ][ ]
[ ][ ][ ][ ]

-----------------

Block 1

[ ][ ][ ][ ]
[ ][ ][ ][ ]
[ ][ ][ ][ ]

-----------------

Block 2

[ ][ ][ ][ ]
[ ][ ][ ][ ]
[ ][ ][ ][ ]
```

---

# Accessing Elements

```java
cube[1][2][3] = 100;
```

---

# Traversing a 3D Array

```java
for(int i=0;i<cube.length;i++){

    for(int j=0;j<cube[i].length;j++){

        for(int k=0;k<cube[i][j].length;k++){

            System.out.print(cube[i][j][k]+" ");

        }

        System.out.println();

    }

}
```

---

# 📊 Time Complexity

| Operation | Complexity |
|-----------|------------|
| Access | O(1) |
| Update | O(1) |
| Traversal | O(n × m × p) |

---

# ✅ Advantages

- Efficient memory usage.
- Flexible row sizes.
- Useful for irregular datasets.
- Easy to represent matrices and grids.

---

# ❌ Disadvantages

- Slightly complex traversal.
- Fixed row count.
- Can become difficult to understand for beginners.

---

# 🌍 Real-World Applications

### Jagged Arrays

- Student marks
- Timetables
- Game levels
- Sparse data

### 3D Arrays

- 3D Graphics
- Medical Imaging (MRI/CT Scan)
- Scientific Simulations
- Rubik's Cube
- Voxel Games (Minecraft)

---

# ⚠ Common Mistakes

❌ Assuming every row has the same length.

```java
nums[i][j]
```

Always use

```java
nums[i].length
```

instead of

```java
nums[0].length
```

---

❌ Forgetting to allocate memory.

```java
nums[0][0] = 10;
```

This throws a **NullPointerException** if the row hasn't been initialized.

---

# 🧩 Interview Questions

### 1. What is a Jagged Array?

A Jagged Array is an array whose rows can have different lengths.

---

### 2. Is a Jagged Array a true matrix?

No.

A matrix has equal columns in every row.

---

### 3. Where are Jagged Arrays stored?

Each row is stored as a separate array on the Heap, and the main array stores references to these rows.

---

### 4. Difference between a 2D Array and a Jagged Array?

| 2D Array | Jagged Array |
|-----------|--------------|
| Equal columns | Variable columns |
| Fixed structure | Flexible structure |
| Easier indexing | Better memory utilization |

---

# 📝 Summary

- Jagged Arrays are arrays of arrays with variable row sizes.
- They save memory for irregular datasets.
- A 3D Array is an array of 2D arrays.
- Always use `nums[i].length` when traversing Jagged Arrays.
- Jagged Arrays are widely used in real-world software systems.

---

> ⭐ **Pro Tip:** Use a normal 2D array when every row has the same number of columns. Use a Jagged Array when row sizes differ to avoid wasting memory.
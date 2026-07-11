# 📚 Arrays in Java

## What is an Array?

An array is a collection of elements of the **same data type** stored in **contiguous memory locations**.

### Why do we need arrays?

Without arrays:

```java
int a = 10;
int b = 20;
int c = 30;
int d = 40;
```

With arrays:

```java
int[] numbers = {10,20,30,40};
```

---

## Syntax

### Declaration

```java
int[] nums;
```

### Declaration + Memory Allocation

```java
int[] nums = new int[4];
```

Default values

| Data Type | Default Value |
|-----------|---------------|
| int | 0 |
| double | 0.0 |
| boolean | false |
| char | '\u0000' |
| Object | null |

---

## Accessing Elements

```java
int[] nums = {3,7,2,4};

System.out.println(nums[0]); // 3
System.out.println(nums[3]); // 4
```

Index starts from **0**.

---

## Updating Elements

```java
nums[2] = 100;

System.out.println(nums[2]);
```

Output

```
100
```

---

## Printing Array

```java
for(int i=0;i<nums.length;i++)
{
    System.out.println(nums[i]);
}
```

---

## Advantages

- Stores multiple values
- Faster access using index
- Easy traversal
- Memory efficient

---

## Disadvantages

- Fixed size
- Stores same data type only
- Insertion/Deletion is costly
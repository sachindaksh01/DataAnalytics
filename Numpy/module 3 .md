
# 📘 Module 3: Indexing and Slicing in NumPy

Indexing and slicing are very important in **Data Analytics**, because we often deal with big datasets, and we need to **pick only some rows/columns** or filter data. NumPy gives us powerful ways to do this.

---

## 1. Indexing in 1D Arrays

👉 Indexing means selecting elements using their position.
👉 NumPy arrays start with **index 0** (like Python lists).

```python
import numpy as np

# Creating a 1D array
arr = np.array([10, 20, 30, 40, 50])

print(arr[0])   # First element
print(arr[2])   # Third element
print(arr[-1])  # Last element
```

**Output:**

```
10
30
50
```

📝 *Explanation:*

* `arr[0]` → first element (10).
* `arr[2]` → third element (30).
* `arr[-1]` → last element (50).
  💡 *Real-life example:* Think of `arr` like roll numbers list; indexing helps you pick a specific student.

---

## 2. Indexing in 2D Arrays

👉 A **2D array** is like a matrix (rows × columns).
👉 Use `[row, column]` format.

```python
arr2d = np.array([[1,2,3],
                  [4,5,6],
                  [7,8,9]])

print(arr2d[0, 0])   # element at row 0, column 0
print(arr2d[1, 2])   # element at row 1, column 2
print(arr2d[2, 1])   # element at row 2, column 1
```

**Output:**

```
1
6
8
```

📝 *Explanation:*

* `arr2d[0,0]` → top-left corner (1).
* `arr2d[1,2]` → row 2, col 3 → (6).
* `arr2d[2,1]` → row 3, col 2 → (8).
  💡 *Analogy:* 2D array is like a **classroom seating chart**. Rows = benches, columns = seats.

---

## 3. Slicing Arrays

👉 Slicing means selecting a **range of elements**.
👉 Format: `start:end:step` (just like Python lists).

### 1D Array Slicing

```python
arr = np.array([10,20,30,40,50,60])

print(arr[1:4])    # elements from index 1 to 3
print(arr[:3])     # first 3 elements
print(arr[3:])     # from index 3 to end
print(arr[::2])    # every 2nd element
```

**Output:**

```
[20 30 40]
[10 20 30]
[40 50 60]
[10 30 50]
```

### 2D Array Slicing

```python
arr2d = np.array([[1,2,3],
                  [4,5,6],
                  [7,8,9]])

print(arr2d[0:2, 1:3])   # slice rows 0-1, cols 1-2
print(arr2d[:, 0])       # all rows, first column
print(arr2d[1, :])       # row 1, all columns
```

**Output:**

```
[[2 3]
 [5 6]]

[1 4 7]

[4 5 6]
```

📝 *Real-world use:* slicing is like selecting **a portion of dataset** (e.g., only certain columns like "Age" or "Salary").

---

## 4. Advanced Indexing

👉 Sometimes we don’t want a range, we want **specific elements** using index lists.

```python
arr = np.array([10,20,30,40,50])

indices = [0,2,4]   # pick 1st, 3rd, and 5th element
print(arr[indices])
```

**Output:**

```
[10 30 50]
```

📝 *Use case:* Selecting **non-continuous data points** from a dataset.

---

## 5. Fancy Indexing (2D)

👉 Fancy indexing = selecting multiple rows/columns at once.

```python
arr2d = np.array([[10,20,30],
                  [40,50,60],
                  [70,80,90]])

# Select rows 0 and 2
print(arr2d[[0,2]])

# Select elements at (0,0), (1,1), (2,2)
print(arr2d[[0,1,2],[0,1,2]])
```

**Output:**

```
[[10 20 30]
 [70 80 90]]

[10 50 90]
```

📝 *Use case:* Very useful in ML/AI to **pick diagonal values** or **select specific samples**.

---

## 6. Boolean Indexing

👉 Boolean indexing = filter values based on condition.
👉 Returns only elements where condition is **True**.

```python
arr = np.array([10, 15, 20, 25, 30])

print(arr[arr > 18])     # all elements greater than 18
print(arr[arr % 2 == 0]) # even numbers only
```

**Output:**

```
[20 25 30]
[10 20 30]
```

📝 *Use case:* Filtering dataset rows (e.g., selecting only customers with `Age > 18`).

---

Perfect 👍
Here’s a **set of 20 practice questions** only from **Module 3: Indexing & Slicing in NumPy**.
These cover **1D, 2D indexing, slicing, advanced indexing, fancy indexing, boolean indexing**.

---

# 📝 Practice Set – NumPy Indexing & Slicing

### **Part A – 1D Indexing & Slicing**

1. Create a 1D array `[5,10,15,20,25,30]`. Print the **first element** and the **last element** using indexing.
2. From the array `[2,4,6,8,10,12,14]`, select the **3rd element**.
3. Create a 1D array `[100,200,300,400,500]`. Use slicing to get `[200,300,400]`.
4. From `[1,2,3,4,5,6,7,8,9]`, print only **even numbers** using slicing (`start:end:step`).
5. Create `[10,20,30,40,50,60]` and slice it to get `[20,30,40]`.

---

### **Part B – 2D Indexing & Slicing**

6. Create a 2D array

   ```
   [[1,2,3],
    [4,5,6],
    [7,8,9]]
   ```

   Print the element at **row 2, column 3**.
7. From the same array, print the **first row only**.
8. Print the **second column** from all rows.
9. Slice the array to get:

   ```
   [[2,3],
    [5,6]]
   ```
10. Slice the same array to get the **last 2 rows**.

---

### **Part C – Advanced Indexing**

11. Create `[10,20,30,40,50,60]` and select elements at index `[0,3,5]`.
12. Create a 2D array

    ```
    [[10,20,30],
     [40,50,60],
     [70,80,90]]
    ```

    Use indexing to pick **30, 50, 70**.
13. From the same array, pick **row 0 and row 2** using advanced indexing.

---

### **Part D – Fancy Indexing**

14. Create

    ```
    [[1,2,3],
     [4,5,6],
     [7,8,9],
     [10,11,12]]
    ```

    Select rows `[0,2,3]`.
15. From the same array, select elements `(0,0), (1,1), (2,2)`.
16. Pick the entire **first and last column** from the array using fancy indexing.

---

### **Part E – Boolean Indexing**

17. Create `[5,10,15,20,25,30]`. Select elements **greater than 18**.
18. From `[3,6,9,12,15,18,21]`, filter only the elements that are **multiples of 6**.
19. Create `[2,4,6,8,10,12]`. Use boolean indexing to select only **odd positions** (indexes 1,3,5).
20. Create a 2D array

    ```
    [[12, 7, 5],
     [20, 25, 30],
     [4, 8, 16]]
    ```

    Select all elements **greater than 10**.

---

✅ These 20 exercises move step by step from **basic indexing → slicing → advanced/fancy → boolean indexing**, exactly aligned with the lecture.

---

Do you want me to also prepare an **answer key with outputs** (so you can verify student answers quickly), or should I keep them as assignments only?


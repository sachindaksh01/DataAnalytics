---

# 📘 Lecture 2: NumPy Arrays

---

## 1. Creating Arrays

In NumPy, arrays are the most important data structure.

* **1D Array = like a roll number list** (straight line of data).
* **2D Array = like a classroom seating chart (rows and columns).**
* **3D Array = like a group of classrooms (multiple 2D arrays together).**

---

### (A) Using `np.array()`

We can create arrays from Python lists and tuple.

```python
import numpy as np

# 1D Array (like roll numbers in a single line)
arr1 = np.array([10, 20, 30, 40])
print("1D Array:\n", arr1)

# 2D Array (like seating chart: rows & columns)
arr2 = np.array([[1, 2, 3], [4, 5, 6]])
print("2D Array:\n", arr2)

# 3D Array (like group of 2D classrooms)
arr3 = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
print("3D Array:\n", arr3)
```

**Output:**

```
1D Array:
 [10 20 30 40]

2D Array:
 [[1 2 3]
  [4 5 6]]

3D Array:
 [[[1 2]
   [3 4]]

  [[5 6]
   [7 8]]]
```

👉 Explanation (Hinglish):

* 1D array = ek list of numbers.
* 2D array = rows aur columns.
* 3D array = multiple 2D blocks.
  ✅ Useful in data analytics for organizing data (rows = records, columns = features).

---

### (B) `np.zeros()`

Creates arrays filled with **0s**. Often used to initialize data.

```python
# 1D array of zeros
arr = np.zeros(5)
print("1D Zeros:\n", arr)

# 2D array of zeros
arr2 = np.zeros((2, 3))
print("2D Zeros:\n", arr2)
```

**Output:**

```
1D Zeros:
 [0. 0. 0. 0. 0.]

2D Zeros:
 [[0. 0. 0.]
  [0. 0. 0.]]
```

👉 Explanation:

* Creates empty data placeholders.
* **Analytics Example:** Before filling dataset values, we can start with zeros.

---

### (C) `np.ones()`

Creates arrays filled with **1s**.

```python
# 1D ones
arr = np.ones(4)
print("1D Ones:\n", arr)

# 2D ones with shape
arr2 = np.ones((3, 2))
print("2D Ones:\n", arr2)
```

**Output:**

```
1D Ones:
 [1. 1. 1. 1.]

2D Ones:
 [[1. 1.]
  [1. 1.]
  [1. 1.]]
```

👉 Explanation:

* Quick way to create default arrays with value 1.
* **Example in ML:** Initialize weights with 1s before training a model.

---

### (D) `np.full()`

Create arrays filled with a custom value.

```python
# 1D full array
arr = np.full(5, 7)  # 5 elements, all 7
print("1D Full:\n", arr)

# 2D full array
arr2 = np.full((2, 3), 9)
print("2D Full:\n", arr2)
```

**Output:**

```
1D Full:
 [7 7 7 7 7]

2D Full:
 [[9 9 9]
  [9 9 9]]
```

👉 Useful when we need fixed default values. Example:

* Represent missing marks as 0 or -1 initially.

---

### (E) `np.arange()`

Creates arrays with values in a range (like Python’s `range`).

```python
# Simple range
arr = np.arange(5)  # start=0, end=5 (not included), step=1
print("0 to 4:\n", arr)

# Custom start, end, step
arr2 = np.arange(2, 10, 2)  # start=2, end=10, step=2
print("2 to 8 step 2:\n", arr2)
```

**Output:**

```
0 to 4:
 [0 1 2 3 4]

2 to 8 step 2:
 [2 4 6 8]
```

👉 **Analytics Example:** Generate time intervals, age groups, etc.

---

### (F) `np.linspace()`

Creates evenly spaced numbers between two values.

```python
arr = np.linspace(0, 1, 5)  # from 0 to 1, 5 points
print("Linspace:\n", arr)
```

**Output:**

```
Linspace:
 [0.   0.25 0.5  0.75 1.  ]
```

👉 Useful when we need equal divisions, e.g., splitting data range into equal bins.

---

### (G) `np.eye()`

Creates an **identity matrix** (diagonal = 1, rest = 0).

```python
arr = np.eye(3)
print("Identity Matrix using eye:\n", arr)
```

**Output:**

```
Identity Matrix using eye:
 [[1. 0. 0.]
  [0. 1. 0.]
  [0. 0. 1.]]
```

👉 In ML, identity matrix is used in **linear algebra, transformations, covariance matrices**.

---

### (H) `np.identity()`

Another way to create identity matrix.

```python
arr = np.identity(4)
print("Identity Matrix using identity:\n", arr)
```

**Output:**

```
Identity Matrix using identity:
 [[1. 0. 0. 0.]
  [0. 1. 0. 0.]
  [0. 0. 1. 0.]
  [0. 0. 0. 1.]]
```

👉 Difference:

* `np.eye()` → allows more control (like offset diagonals).
* `np.identity()` → simple identity matrix only.

---

## 2. Array Attributes

Every NumPy array has some important properties.

---

### (A) `shape`

Gives number of rows and columns.

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
print("Shape:", arr.shape)
```

**Output:**

```
Shape: (2, 3)
```

👉 Explanation: 2 rows × 3 columns.
(Hindi: "2 rows aur 3 columns ka chart hai.")

---

### (B) `size`

Total number of elements.

```python
print("Size:", arr.size)
```

**Output:**

```
Size: 6
```

👉 Means total 6 data points.

---

### (C) `ndim`

Number of dimensions.

```python
print("Dimensions:", arr.ndim)
```

**Output:**

```
Dimensions: 2
```

👉 2D array (rows and columns).

---

### (D) `dtype`

Type of data stored.

```python
print("Data type:", arr.dtype)
```

**Output:**

```
Data type: int64
```

👉 In analytics, we often need to check if data is integer, float, etc.

---

### (E) `itemsize`

Size of each element in bytes.

```python
print("Item size:", arr.itemsize)
```

**Output:**

```
Item size: 8
```

👉 Each element takes 8 bytes in memory.
(Hindi: "Har ek element ko memory me 8 bytes lag rahe hain.")

---

## 🎯 Summary 

* NumPy arrays are the **foundation of Data Analytics**.
* We learned different ways to **create arrays** (`array, zeros, ones, full, arange, linspace, eye, identity`).
* We explored **array attributes** (`shape, size, ndim, dtype, itemsize`).
* These methods help us organize and analyze data easily.

👉 **In simple words:**
NumPy arrays = backbone of data handling. Without arrays, Data Analytics is almost impossible.



---



# 📝 NumPy Arrays Practice Questions

### Part A: Creating Arrays

1. Create a **1D NumPy array** from a Python list `[2, 4, 6, 8]`. Print the array.
2. Create a **2D NumPy array** (2 rows, 3 columns) from a nested Python list. Example: `[[1,2,3],[4,5,6]]`.
3. Create a **3D NumPy array** with shape `(2,2,2)` using `np.array()`.
4. Use `np.zeros()` to create a **1D array of 5 zeros**. Print array and shape.
5. Create a **2D 3x3 array of zeros** using `np.zeros()`.
6. Use `np.ones()` to create a **1D array of length 6 filled with ones**.
7. Create a **4x2 array of ones** using `np.ones()`.
8. Use `np.full()` to create a **1D array of length 5 filled with the number 7**.
9. Create a **2D 3x3 array filled with the number 9** using `np.full()`.
10. Use `np.arange()` to create an array from `5 to 25` with step size `5`.
11. Use `np.arange()` to create a 2D array reshaped as `3x3` from numbers `1–9`.
12. Use `np.linspace()` to generate **5 numbers between 0 and 1 (inclusive)**.
13. Create **10 evenly spaced numbers between 50 and 100** using `np.linspace()`.
14. Create a **3x3 identity matrix** using `np.eye()`.
15. Create a **4x4 identity matrix** using `np.identity()`.
16. Explain the difference between `np.eye(3)` and `np.identity(3)` by showing both outputs.

---

### Part B: Array Attributes

17. Create a 2D array `[[1,2,3],[4,5,6]]`. Print its `shape`, `size`, `ndim`.
18. Create a NumPy array with numbers `[1, 2, 3, 4, 5]`. Print its `dtype`.
19. Create a NumPy array of floats `[1.2, 3.4, 5.6]`. Print `dtype` and `itemsize`.
20. Create a 2D 4x5 array of ones and print all its attributes (`shape`, `ndim`, `size`, `dtype`, `itemsize`).

---


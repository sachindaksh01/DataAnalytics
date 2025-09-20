---

# 📘 Lecture 1: Introduction to NumPy

### Topics we will cover:

1. What is NumPy and Why use it?
2. Installing and Importing NumPy
3. Difference between Python Lists and NumPy Arrays

---

## 1. What is NumPy and Why use it?

**NumPy (Numerical Python)** is an **open-source library** mainly used for:

* Working with **arrays**
* Performing **fast mathematical and numerical computations**

It is very popular in:

* **Data Science**
* **Machine Learning**
* **Scientific domains**

👉 Compared to Python’s built-in list, NumPy arrays are much faster.
👉 Reason: NumPy arrays are stored in **contiguous memory locations**, which makes processing efficient.

---

### Example

#### Normal Python List

```python
# Python list
my_list = [1, 2, 3, 4, 5]

# Multiply each element by 2 (using loop)
result_list = []
for x in my_list:
    result_list.append(x * 2)

print("Python List:", result_list)
```

**Output:**

```
Python List: [2, 4, 6, 8, 10]
```

---

#### NumPy Array

```python
import numpy as np   # Import NumPy

# NumPy array
my_array = np.array([1, 2, 3, 4, 5])

# Multiply each element by 2 (direct operation, no loop needed)
result_array = my_array * 2

print("NumPy Array:", result_array)
```

**Output:**

```
NumPy Array: [ 2  4  6  8 10]
```

✅ With NumPy, we don’t need to write a loop.
✅ Operations are much faster and easier.

---

### Built-in Mathematical Functions in NumPy

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

print("Sum:", np.sum(arr))        # Add all elements
print("Mean:", np.mean(arr))      # Average
print("Standard Deviation:", np.std(arr))  # Standard deviation
print("Square:", np.square(arr))  # Square of each element
```

**Output:**

```
Sum: 15
Mean: 3.0
Standard Deviation: 1.4142135623730951
Square: [ 1  4  9 16 25]
```

---

## 2. Installing and Importing NumPy

👉 NumPy is not included by default in Python. We must install it.

### Installation:

```bash
pip install numpy
```

### Import:

```python
import numpy as np
```

* Here, `np` is a short name (alias) commonly used.
* Now we can use NumPy functions like `np.array()`, `np.sum()`, etc.

---

## 3. Difference between Python Lists and NumPy Arrays

Let’s compare them step by step.

---

### (A) Element-wise Operations

**Python List Example:**

```python
list1 = [1, 2, 3, 4]
list2 = [5, 6, 7, 8]

# Add element by element using loop
result = []
for i in range(len(list1)):
    result.append(list1[i] + list2[i])

print("List Result:", result)
```

**Output:**

```
List Result: [6, 8, 10, 12]
```

---

**NumPy Array Example:**

```python
import numpy as np

arr1 = np.array([1, 2, 3, 4])
arr2 = np.array([5, 6, 7, 8])

# Add directly (no loop needed)
result = arr1 + arr2
print("Array Result:", result)
```

**Output:**

```
Array Result: [ 6  8 10 12]
```

---

### (B) Speed and Performance

**Python list is slower**, NumPy is faster.
(We can show timing test in later lectures.)

---

### (C) Memory Usage

**Python List Example:**

```python
import sys

list1 = [1, 2, 3, 4, 5]
print("List size in bytes:", sys.getsizeof(list1))
```

**NumPy Array Example:**

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
print("NumPy array size in bytes:", arr.nbytes)
```

✅ NumPy uses less memory compared to lists.

---

## 🎯 Summary (Lecture 1)

* NumPy = Numerical Python → Open-source library for arrays and fast numerical operations.
* Faster than Python lists (stored in contiguous memory).
* Built-in functions make complex operations simple (sum, mean, std, square, etc.).
* Install with `pip install numpy` and import as `import numpy as np`.
* NumPy arrays are **faster, more memory efficient, and easier** to use than Python lists.

---

👉 Next Lecture: **Creating and Exploring NumPy Arrays** (array creation, dimensions, indexing, slicing).

---


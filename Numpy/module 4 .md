
# 📘 Module 4: Array Manipulation

When working with data, sometimes we need to **rearrange, reshape, or change** the way our arrays look or behave. NumPy gives powerful tools for this.

👉 This is very important in **Data Analytics** because:

* Datasets often come in different shapes (rows × columns).
* We may need to **reshape data** for analysis or machine learning.
* We may need to **change data types** (like integer → float).

---

## 1. Reshaping Arrays with `reshape()`

👉 **Definition:**

* `reshape()` changes the shape of an array **without changing the data**.
* Shape = how many rows and columns the array has.

**Analogy:**

* Imagine you have 12 students standing in a line (1D array).
* You can rearrange them into **3 rows × 4 columns** or **2 rows × 6 columns**.
* Students (data) are the same, only their arrangement changes.

```python
import numpy as np

arr = np.arange(1, 13)   # 1D array with values 1 to 12
print("Original Array:\n", arr)

# Reshape to 3 rows × 4 columns
reshaped1 = arr.reshape(3, 4)
print("\nReshaped to 3x4:\n", reshaped1)

# Reshape to 2 rows × 6 columns
reshaped2 = arr.reshape(2, 6)
print("\nReshaped to 2x6:\n", reshaped2)
```

**Output:**

```
Original Array:
 [ 1  2  3  4  5  6  7  8  9 10 11 12]

Reshaped to 3x4:
 [[ 1  2  3  4]
  [ 5  6  7  8]
  [ 9 10 11 12]]

Reshaped to 2x6:
 [[ 1  2  3  4  5  6]
  [ 7  8  9 10 11 12]]
```

📝 **Use in Data Analytics:**

* Converting raw data into structured **rows and columns** for easier analysis.
* Preparing data before feeding into **Machine Learning models** (which require specific shapes).

---

## 2. Flattening Arrays with `ravel()` and `flatten()`

👉 **Definition:**

* Flattening means converting a **multi-dimensional array → 1D array**.
* Both `ravel()` and `flatten()` do this.

**Analogy:**

* Think of a **classroom seating chart (2D)**. If you make all students stand in a single line, that’s flattening.

### Example with `ravel()`

```python
arr2d = np.array([[1,2,3],
                  [4,5,6],
                  [7,8,9]])

print("Original 2D Array:\n", arr2d)

# Flatten using ravel()
flat1 = arr2d.ravel()
print("\nFlattened with ravel():\n", flat1)
```

**Output:**

```
Original 2D Array:
 [[1 2 3]
  [4 5 6]
  [7 8 9]]

Flattened with ravel():
 [1 2 3 4 5 6 7 8 9]
```

### Example with `flatten()`

```python
flat2 = arr2d.flatten()
print("\nFlattened with flatten():\n", flat2)
```

**Output:**

```
Flattened with flatten():
 [1 2 3 4 5 6 7 8 9]
```

👉 **Difference:**

* `ravel()` → returns a **view** (changes affect original array sometimes).
* `flatten()` → returns a **copy** (independent of original).

📝 **Use in Analytics:**

* When converting 2D/3D datasets into **1D vector** for ML models.
* Example: flattening an **image (matrix of pixels)** into a 1D vector.

---

## 3. Transposing Arrays with `.T`

👉 **Definition:**

* Transpose means **rows become columns and columns become rows**.
* `.T` is used for transposing.

**Analogy:**

* Think of a **student attendance sheet**. Rows = students, Columns = days.
* If we transpose, Rows = days, Columns = students.

```python
arr = np.array([[1,2,3],
                [4,5,6]])

print("Original Array:\n", arr)

# Transpose
transposed = arr.T
print("\nTransposed Array:\n", transposed)
```

**Output:**

```
Original Array:
 [[1 2 3]
  [4 5 6]]

Transposed Array:
 [[1 4]
  [2 5]
  [3 6]]
```

📝 **Use in Analytics:**

* Transposing is very common in **matrix operations, linear algebra, and ML**.
* Example: Swapping features and samples in a dataset.

---

## 4. Changing Data Types with `astype()`

👉 **Definition:**

* `astype()` converts the data type of array elements.
* Example: int → float, float → int, string → int, etc.

**Analogy:**

* Think of changing the **units** of measurement. Like converting `20` students → `20.0` students (integer → float).

```python
arr = np.array([1,2,3,4])
print("Original dtype:", arr.dtype)

# Convert to float
arr_float = arr.astype(float)
print("Converted to float:", arr_float, "dtype:", arr_float.dtype)

# Convert float to int
arr2 = np.array([1.5, 2.7, 3.2])
arr_int = arr2.astype(int)
print("Converted to int:", arr_int, "dtype:", arr_int.dtype)
```

**Output:**

```
Original dtype: int64
Converted to float: [1. 2. 3. 4.] dtype: float64
Converted to int: [1 2 3] dtype: int64
```

📝 **Use in Analytics:**

* Many times data is stored as **string** (e.g., `"25"`, `"30"`), but we need **integers** to perform math.
* Converting data types is essential in **data cleaning & preprocessing**.

---

# 🔑 Summary (Hinglish)

* `reshape()` → change array shape (rows × columns).
* `ravel(), flatten()` → convert multi-d arrays into 1D.
* `.T` → transpose (swap rows and columns).
* `astype()` → change data type (int, float, string).

👉 **Real-world in Data Analytics:**

* Reshape data before ML model input.
* Flatten images/text for analysis.
* Transpose matrices in linear algebra.
* Convert data types while cleaning datasets.

---

Perfect 👍
Here’s a **20-question practice set** for **Module 4: Array Manipulation**.
All questions are **real-life / data-analytics based** so students can connect theory to practice.

---

# 📝 Practice Set – Array Manipulation (NumPy)

---

## **Part A: Reshaping with `reshape()`**

1. You have sales data for **12 months** in a 1D array.
   Convert it into a **3x4 array** (3 years × 4 quarters).

2. You collected **16 student marks** in one array.
   Reshape it into a **4x4 matrix** (4 students × 4 subjects).

3. Create an array of numbers from **1 to 20**.
   Reshape it into a **5x4** dataset (5 rows = students, 4 columns = subjects).

4. Suppose you have a dataset of **24 temperatures (hourly)**.
   Reshape into a **2D array with 3 days × 8 hours**.

5. Create a 1D array of **30 employee IDs**.
   Reshape it into a **2D array of 6 rows × 5 columns**.

---

## **Part B: Flattening with `ravel()` and `flatten()`**

6. Create a **3x3 seating chart** (2D array). Flatten it using `ravel()`.

7. You have student marks in a **4x3 matrix** (rows = students, cols = subjects).
   Flatten the data into a 1D list for analysis.

8. Create a **2x5 exam marks table** and use `.flatten()` to get a 1D array.

9. Make a 2D array of **monthly rainfall (3 years × 4 quarters)**. Flatten it into a 1D array of rainfall values.

10. Create a **3x3x2 (3D) array** of product sales (3 stores × 3 months × 2 products).
    Flatten it into 1D for ML model input.

---

## **Part C: Transposing with `.T`**

11. Create a dataset for **students and their subjects**:

    ```
    [[80, 90, 85],
     [70, 88, 92]]
    ```

    Transpose it so columns become students and rows become subjects.

12. Suppose you have a **2x4 dataset (2 students, 4 subjects)**.
    Transpose it to get **4x2 (4 subjects, 2 students)**.

13. Create a **3x2 matrix** representing 3 customers’ **purchases in 2 months**.
    Transpose it to see **monthly view instead of customer view**.

14. Create a dataset of **employee work hours (5 days × 3 employees)**.
    Transpose it to see data as **employees × days**.

15. You have a **4x3 attendance sheet** (4 students × 3 days).
    Transpose it to see **days × students**.

---

## **Part D: Changing Data Types with `astype()`**

16. Create an integer array `[1, 2, 3, 4, 5]`.
    Convert it into **float** using `astype()`.

17. Suppose ages are stored as **strings**: `["21", "22", "23"]`.
    Convert them into **integers** for analysis.

18. You have floating-point scores `[89.5, 76.3, 92.7]`.
    Convert them into **integers** (floor values).

19. Create a **2D array of employee salaries** (floats).
    Convert the salaries into integers for reporting.

20. You downloaded a dataset where IDs are stored as **strings**: `["101","102","103"]`.
    Convert them into integers using `astype()`.

---

# 🔑 Why this matters (Hinglish wrap-up)

* **Reshape**: Like arranging sales/attendance into rows & columns.
* **Flatten**: Like taking a full table and converting into a single line of values.
* **Transpose**: Like flipping student vs subject data.
* **astype()**: Like converting text `"25"` into number `25` so we can calculate.



---




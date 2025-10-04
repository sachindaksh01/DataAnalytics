---

# 📘 Module 7: Advanced Array Operations

---

## 1. Broadcasting Concept

👉 **Definition:**
Broadcasting is NumPy’s way of performing operations on arrays of **different shapes**.
If dimensions don’t match, NumPy automatically "expands" the smaller array to match the bigger one.

**Why important?**

* Saves time → no need to write loops.
* Helps perform operations across different dimensions.

---

### Example: Adding a constant to all elements

```python
import numpy as np

arr = np.array([10, 20, 30, 40])
result = arr + 5
print(result)
```

**Output:**

```
[15 25 35 45]
```

📌 **Explanation:**

* The scalar `5` is "broadcast" to every element in the array.
* Useful for applying the same transformation to an entire dataset.

---

### Example: 2D and 1D Broadcasting

```python
matrix = np.array([[1,2,3],
                   [4,5,6],
                   [7,8,9]])
vector = np.array([10,20,30])

result = matrix + vector
print(result)
```

**Output:**

```
[[11 22 33]
 [14 25 36]
 [17 28 39]]
```

📌 **Explanation:**

* The 1D vector `[10,20,30]` is broadcast across each row of the matrix.
* Real-life use: Adding **extra charges (like tax)** to all products in a sales table.

---

## 2. Vectorized Operations

👉 **Definition:**
Vectorization means performing operations on the entire array at once, instead of looping through elements.

**Why important?**

* Much faster than Python loops.
* Makes code shorter and more readable.

---

### Example: Comparing Loop vs Vectorized

```python
# Python loop
data = [1,2,3,4,5]
squared_loop = [x**2 for x in data]

# NumPy vectorized
arr = np.array([1,2,3,4,5])
squared_np = arr**2

print("Loop Result:", squared_loop)
print("Vectorized Result:", squared_np)
```

**Output:**

```
Loop Result: [1, 4, 9, 16, 25]
Vectorized Result: [ 1  4  9 16 25]
```

📌 **Explanation:**

* Same result, but NumPy version is cleaner and faster.
* Real-life use: Calculating **sales growth, marks percentage, transformations** on large datasets.

---

## 3. Conditional Operations – `np.where()`

👉 **Definition:**
`np.where(condition, value_if_true, value_if_false)`
Returns elements based on a condition.

**Why important?**

* Helps apply business rules, filtering, and data cleaning.

---

### Example 1: Pass/Fail Check

```python
marks = np.array([45, 70, 30, 90, 50])
result = np.where(marks >= 50, "Pass", "Fail")
print(result)
```

**Output:**

```
['Fail' 'Pass' 'Fail' 'Pass' 'Pass']
```

📌 **Explanation:**

* Students scoring ≥50 are Pass, others are Fail.
* Real-life use: Quick categorization of results.

---

### Example 2: Apply Discount on Products

```python
price = np.array([200, 150, 300, 120])
discounted = np.where(price > 180, price*0.9, price)
print(discounted)
```

**Output:**

```
[180. 150. 270. 120.]
```

📌 **Explanation:**

* If price > 180 → 10% discount applied.
* Useful in **e-commerce pricing rules**.

---

## 4. Checking for NaN and Infinity

👉 **Problem:**
Real-world datasets often contain **missing values (NaN)** or **infinite values (Inf)**, which can break analysis.

NumPy provides:

* `np.isnan()` → checks if value is NaN (Not a Number).
* `np.isinf()` → checks if value is infinity.

---

### Example: Detecting NaN

```python
data = np.array([10, np.nan, 25, np.nan, 50])
print("Is NaN:", np.isnan(data))
```

**Output:**

```
[False  True False  True False]
```

📌 **Explanation:**

* NaN found in positions 1 and 3.
* Real-life use: Missing data in surveys, sensor errors, incomplete datasets.

---

### Example: Detecting Infinity

```python
data = np.array([5, 10, np.inf, -np.inf, 20])
print("Is Inf:", np.isinf(data))
```

**Output:**

```
[False False  True  True False]
```

📌 **Explanation:**

* Infinite values detected.
* Real-life use: Appears in **division by zero** or bad calculations.

---

### Handling NaN and Inf

```python
data = np.array([10, np.nan, 20, np.inf, 30])

# Replace NaN with 0
cleaned = np.where(np.isnan(data), 0, data)

# Replace Inf with max value
cleaned = np.where(np.isinf(cleaned), np.max(data[np.isfinite(data)]), cleaned)

print("Cleaned Data:", cleaned)
```

**Output:**

```
Cleaned Data: [10.  0. 20. 30. 30.]
```

📌 **Explanation:**

* NaN replaced with 0.
* Inf replaced with the maximum finite value (30).
* Real-life use: **Data cleaning** before feeding into analytics/ML models.

---

# 🔑 Summary

* **Broadcasting** → Perform operations on arrays of different shapes (e.g., adding tax to all rows).
* **Vectorized Operations** → Fast, loop-free operations on entire arrays (e.g., squaring all marks).
* **np.where()** → Conditional replacement (e.g., pass/fail, discounts).
* **np.isnan(), np.isinf()** → Identify and handle missing/infinite values (e.g., cleaning survey or sensor data).

👉 These advanced operations are **essential in real-world analytics and ML**, where datasets are huge, messy, and need fast processing.

---



Here’s a **20-question scenario-based practice set** for **Module 7: Advanced Array Operations**.
These will make students apply **broadcasting, vectorized operations, np.where(), isnan(), isinf()** in real-life style problems.

---

# 📝 Practice Set – Advanced Array Operations (Module 7)

---

## **Part A – Broadcasting**

1. Add a **constant tax of 50** to each product price in the array `[200, 300, 400, 500]`.

2. A company has a **3x3 matrix of employee salaries**. Add a **bonus array `[1000, 2000, 3000]`** (per department) to each row using broadcasting.

3. Create a **matrix of sales** for 3 months (rows) and 4 products (columns). Add a **1D array of transportation cost per product** to the matrix using broadcasting.

4. Multiply a **5-element sales array** with a **scalar 1.05** to apply a 5% growth factor.

5. Subtract a **1D discount array `[10,20,30]`** from a **2D matrix of product prices (3 rows, 3 columns)** using broadcasting.

---

## **Part B – Vectorized Operations**

6. Square each number in the array `[2,4,6,8,10]` using vectorized operations (without loop).

7. Calculate the percentage increase of `[100,200,300]` when sales grow to `[120,250,330]`.

8. A dataset contains `[50, 60, 70, 80, 90]` marks. Convert them into grades by applying formula: `grade = marks * 1.1`.

9. Compute BMI for 5 people given `weights = [60,70,80,90,100]` (kg) and `heights = [1.6,1.7,1.8,1.9,2.0]` (m) using formula `BMI = weight / height^2`.

10. Vectorize subtraction: Given two arrays `[100,200,300]` (expected sales) and `[90,250,280]` (actual sales), calculate difference in one line.

---

## **Part C – Conditional Operations (`np.where`)**

11. Given marks `[45,60,30,75,90]`, label each student as `"Pass"` if marks ≥50, otherwise `"Fail"`.

12. An e-commerce site applies 10% discount if price > 500. Apply this rule to `[200,600,800,300]`.

13. Replace negative numbers in `[10,-5,20,-8,30]` with `0`.

14. Classify temperatures `[25,35,15,40]` into `"Hot"` if ≥30 else `"Normal"`.

15. A bank wants to flag loan applications: If credit score ≥700 → `"Approved"`, else `"Rejected"`. Test on `[650,720,580,800]`.

---

## **Part D – Checking for NaN / Infinity**

16. From `[10, np.nan, 20, np.nan, 30]`, identify which values are NaN.

17. Replace NaN values in `[5, np.nan, 15, np.nan, 25]` with `0`.

18. Detect infinity values in `[1, np.inf, 3, -np.inf, 5]`.

19. Replace infinity values in `[10,20,np.inf,30,-np.inf]` with the maximum finite value.

20. A dataset `[50, np.nan, 70, 100, np.inf]` is corrupted. Clean it by:

* Replacing NaN with average of valid numbers.
* Replacing Inf with the max valid number.

---




---

# 📘 Module 9: Linear Algebra with NumPy
Linear algebra is **the backbone of data science, machine learning, and computer graphics**. NumPy provides efficient functions to handle **matrix operations**, which are essential for ML algorithms, data transformations, and analytics.

---

## 1. Dot Product – `np.dot()`

👉 **Definition:** The dot product is the sum of products of corresponding elements.
👉 **Use in analytics:** Used in calculating **similarity (cosine similarity), projections, and ML weights**.

### Example: Job Performance Evaluation

```python
import numpy as np

scores = np.array([85, 95, 80])      # scores in 3 areas ( Communication, Technical, Teamwork)
weights = np.array([0.2, 0.5, 0.3])  # importance (weights)

final_score = np.dot(scores, weights)
print("Weighted Performance Score:", final_score)

```

**Output:**

```
Weighted Final Score: 81.0
```



---

## 2. Matrix Multiplication – `np.matmul()`

👉 **Definition:** Multiplication of two matrices (row × column).
👉 **Use in analytics:** Transformations, combining datasets, ML algorithms (e.g., neural networks).

### Example: Sales Data Transformation

```python
sales = np.array([[2,3],   # 2 apples, 3 bananas
                  [1,4]])  # 1 apple, 4 bananas
prices = np.array([[50],   # price of apple
                   [30]])  # price of banana

total = np.matmul(sales, prices)
print("Total Sales per Customer:\n", total)
```

**Output:**

```
Total Sales per Customer:
 [[190]
  [170]]
```

📌 **Interpretation:**

* Customer 1 → 2×50 + 3×30 = 190
* Customer 2 → 1×50 + 4×30 = 170

---

## 3. Transpose – `.T`

👉 **Definition:** Swaps rows with columns.
👉 **Use in analytics:** Used in **linear equations, dataset reshaping, ML optimization**.

### Example: Student Marks Table

```python
marks = np.array([[80, 90, 70],  # Student 1
                  [85, 95, 75]]) # Student 2

print("Original:\n", marks)
print("Transposed:\n", marks.T)
```

**Output:**

```
Original:
 [[80 90 70]
 [85 95 75]]

Transposed:
 [[80 85]
 [90 95]
 [70 75]]
```

📌 **Interpretation:** Now each row represents **subject-wise marks** instead of student-wise.

---



## 4. Determinant – `np.linalg.det()`

👉 **Definition:** A scalar value representing a matrix’s properties.
👉 **Use in analytics:**

* If det = 0 → matrix is **singular** (no inverse).
* Used in transformations, stability analysis.

### Example:

```python
A = np.array([[2,1],
              [3,4]])

det = np.linalg.det(A)
print("Determinant:", det)
```

**Output:**

```
Determinant: 5.000000000000001
```

📌 **Interpretation:** Since determinant ≠ 0, the matrix has an inverse.

---

## 5. Eigenvalues and Eigenvectors – `np.linalg.eig()`

👉 **Definition:**

* **Eigenvalues** show how much variance/direction a vector explains.
* **Eigenvectors** are the directions of maximum variance.
  👉 **Use in analytics:** Very important in **PCA (Principal Component Analysis)** for dimensionality reduction in ML.

### Example:

```python
A = np.array([[4,2],
              [1,3]])

values, vectors = np.linalg.eig(A)
print("Eigenvalues:", values)
print("Eigenvectors:\n", vectors)
```

**Possible Output:**

```
Eigenvalues: [5. 2.]
Eigenvectors:
 [[ 0.89442719 -0.70710678]
 [ 0.4472136   0.70710678]]
```

📌 **Interpretation:**

* Eigenvalues → [5,2] (show strength of directions).
* Eigenvectors → directions of variance.
* Used in ML (PCA) to reduce dataset from **high dimension → fewer features**.

---


👉 Linear Algebra with NumPy is the **foundation for Data Analytics, Machine Learning, and AI models**.

---
Great ✅
Here’s a **10-question practice set** for **Module 9: Linear Algebra with NumPy**.
All problems are **real-world style** so students can connect them easily.

---

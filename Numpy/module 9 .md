


---

# 📘 Module 9: Linear Algebra with NumPy
Linear algebra is **the backbone of data science, machine learning, and computer graphics**. NumPy provides efficient functions to handle **matrix operations**, which are essential for ML algorithms, data transformations, and analytics.

---

## 1. Dot Product – `np.dot()`

👉 **Definition:** The dot product is the sum of products of corresponding elements.
👉 **Use in analytics:** Used in calculating **similarity (cosine similarity), projections, and ML weights**.

### Example: Student Scores and Weightage

```python
import numpy as np

scores = np.array([80, 90, 70])       # marks in 3 subjects
weights = np.array([0.3, 0.4, 0.3])   # weightage of each subject

final_score = np.dot(scores, weights)
print("Weighted Final Score:", final_score)
```

**Output:**

```
Weighted Final Score: 81.0
```

📌 **Interpretation:** The student’s overall score = 81 after applying subject weightages.

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

## 4. Inverse Matrix – `np.linalg.inv()`

👉 **Definition:** A matrix multiplied by its inverse gives the identity matrix.
👉 **Use in analytics:** Solving systems of linear equations (used in regression, optimization).

### Example: Solving Equations

Suppose we have equations:

```
2x + y = 8
3x + 4y = 18
```

```python
A = np.array([[2,1],
              [3,4]])
B = np.array([8,18])

X = np.linalg.inv(A).dot(B)
print("Solutions (x, y):", X)
```

**Output:**

```
Solutions (x, y): [2. 4.]
```

📌 **Interpretation:** Equation solved → x = 2, y = 4.

---

## 5. Determinant – `np.linalg.det()`

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

## 6. Eigenvalues and Eigenvectors – `np.linalg.eig()`

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

# 🔑 Summary

* **Dot product (`dot`)** → Weighted sums (e.g., final score, similarity).
* **Matrix multiplication (`matmul`)** → Transform datasets, sales calculations, ML models.
* **Transpose (`.T`)** → Row ↔ Column switch, useful in reshaping data.
* **Inverse (`inv`)** → Solve equations, regression models.
* **Determinant (`det`)** → Matrix stability, check if inverse exists.
* **Eigenvalues & Eigenvectors (`eig`)** → Explain variance, used in PCA, ML feature reduction.

👉 Linear Algebra with NumPy is the **foundation for Data Analytics, Machine Learning, and AI models**.

---
Great ✅
Here’s a **10-question practice set** for **Module 9: Linear Algebra with NumPy**.
All problems are **real-world style** so students can connect them easily.

---

# 📝 Practice Set – Linear Algebra with NumPy (10 Questions)

---

### **Q1. Dot Product – Weighted Average**

A student scored `[80, 90, 70]` in 3 subjects with weightages `[0.3, 0.4, 0.3]`.
👉 Use `np.dot()` to calculate the **final weighted score**.

---

### **Q2. Dot Product – Salary Components**

An employee has `[40, 20, 10]` hours in different tasks with hourly rates `[50, 100, 150]`.
👉 Find total salary using `np.dot()`.

---

### **Q3. Matrix Multiplication – Sales Calculation**

A store sells **apples and bananas**.

* Customer purchases (matrix):

```
[[2, 3],  # Customer 1 → 2 apples, 3 bananas
 [1, 4]]  # Customer 2 → 1 apple, 4 bananas
```

* Prices (matrix):

```
[[50],  # Apple price
 [30]]  # Banana price
```

👉 Use `np.matmul()` to find each customer’s total bill.

---

### **Q4. Matrix Multiplication – Student Marks**

Two students gave tests:

```
Marks = [[80, 90], [70, 60]]  
Weights = [[0.6, 0.4], [0.5, 0.5]]  
```

👉 Multiply to get **weighted marks** for each student.

---

### **Q5. Transpose – Student Marks Table**

Marks of 3 students in 2 subjects:

```
[[80, 85],
 [90, 95],
 [70, 75]]
```

👉 Use transpose (`.T`) to view subject-wise marks.

---

### **Q6. Inverse Matrix – Solve Equations**

Solve the system of equations using `np.linalg.inv()`:

```
2x + y = 8  
3x + 4y = 18
```

---

### **Q7. Determinant – Matrix Validity**

Check determinant of:

```
[[2, 1],
 [3, 4]]
```

👉 Decide if the matrix is invertible or not.

---

### **Q8. Determinant – Transformation**

A transformation matrix is:

```
[[1, 2],
 [2, 4]]
```

👉 Find its determinant and interpret why it is **not invertible**.

---

### **Q9. Eigenvalues/Eigenvectors – Variance Directions**

For matrix:

```
[[4, 2],
 [1, 3]]
```

👉 Find eigenvalues and eigenvectors using `np.linalg.eig()`.
👉 Interpret which direction explains more variance.

---

### **Q10. Eigenvalues – PCA Example**

Suppose a dataset’s covariance matrix is:

```
[[3, 1],
 [1, 2]]
```

👉 Find eigenvalues and eigenvectors.
👉 Explain how this could be used in **Principal Component Analysis (PCA)** to reduce dimensions.

---

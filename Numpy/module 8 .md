---

# 📘 Module 8: Merging and Splitting Arrays

---

## 1. Why Merge and Split Arrays?

* **Merging (Stacking/Concatenating):**
  Useful when combining data from different sources (e.g., merging multiple student marks, combining product sales).

* **Splitting:**
  Useful for dividing datasets into training/testing sets, or separating features from labels in machine learning.

---

## 2. Stacking Arrays

NumPy provides functions to **stack arrays along different axes**.

---

### (A) Horizontal Stacking – `np.hstack()`

👉 Stacks arrays side by side (column-wise).

**Scenario:** Combine two subjects’ marks into a single table.

```python
import numpy as np

math = np.array([80, 90, 70])
science = np.array([85, 95, 75])

result = np.hstack((math, science))
print(result)
```

**Output:**

```
[80 90 70 85 95 75]
```

📌 Explanation: Arrays are placed **next to each other horizontally**.

---

### (B) Vertical Stacking – `np.vstack()`

👉 Stacks arrays on top of each other (row-wise).

**Scenario:** Combine marks of two students row-wise.

```python
student1 = np.array([80, 90, 70])
student2 = np.array([85, 95, 75])

result = np.vstack((student1, student2))
print(result)
```

**Output:**

```
[[80 90 70]
 [85 95 75]]
```

📌 Explanation: Each student’s marks become one row.

---

### (C) Depth Stacking – `np.dstack()`

👉 Stacks arrays along a new third dimension (depth).

**Scenario:** Combine scores of **two exams** into a 3D array.

```python
exam1 = np.array([80, 90, 70])
exam2 = np.array([85, 95, 75])

result = np.dstack((exam1, exam2))
print(result)
```

**Output:**

```
[[[80 85]
  [90 95]
  [70 75]]]
```

📌 Explanation: Each element is now stacked along **depth (z-axis)**.

---

## 3. Concatenating Arrays – `np.concatenate()`

👉 Joins arrays along an existing axis.

**Scenario:** Merge sales data from two months.

```python
sales_jan = np.array([200, 300, 400])
sales_feb = np.array([250, 350, 450])

merged = np.concatenate((sales_jan, sales_feb))
print(merged)
```

**Output:**

```
[200 300 400 250 350 450]
```

📌 Explanation: Both arrays are joined into a single row.

---

## 4. Splitting Arrays

NumPy allows us to **split arrays into multiple parts**.

---

### (A) `np.split()`

👉 Splits array into equal parts.

**Scenario:** Split sales data for **6 months into 3 equal parts**.

```python
sales = np.array([200,300,400,500,600,700])
parts = np.split(sales, 3)
print(parts)
```

**Output:**

```
[array([200, 300]), array([400, 500]), array([600, 700])]
```

📌 Explanation: Data is divided into **3 equal sub-arrays**.

---

### (B) `np.hsplit()` – Horizontal Split

👉 Splits 2D array **column-wise**.

**Scenario:** Split student dataset into **subjects separately**.

```python
data = np.array([[80,85],
                 [90,95],
                 [70,75]])

parts = np.hsplit(data, 2)
print(parts)
```

**Output:**

```
[array([[80],
       [90],
       [70]]), array([[85],
       [95],
       [75]])]
```

📌 Explanation: Columns are separated (Math vs Science marks).

---

### (C) `np.vsplit()` – Vertical Split

👉 Splits 2D array **row-wise**.

**Scenario:** Split dataset into **individual student records**.

```python
data = np.array([[80,85],
                 [90,95],
                 [70,75]])

parts = np.vsplit(data, 3)
print(parts)
```

**Output:**

```
[array([[80, 85]]), array([[90, 95]]), array([[70, 75]])]
```

📌 Explanation: Each row is extracted as one array.

---

# 🔑 Summary

* **Stacking**:

  * `hstack()` → horizontal merge (side by side).
  * `vstack()` → vertical merge (one on top of other).
  * `dstack()` → depth merge (adds 3rd dimension).

* **Concatenate**:

  * `concatenate()` → general merging along axis.

* **Splitting**:

  * `split()` → split 1D array into equal parts.
  * `hsplit()` → split columns.
  * `vsplit()` → split rows.

👉 These functions are essential in **data preprocessing**, where we often **merge multiple datasets** or **split one dataset into smaller training/testing sets**.

---




Here’s a **20-question scenario-based practice set** for **Module 8: Merging and Splitting Arrays**.
These questions will help students practice **stacking, concatenating, splitting** with **real-life style data**.

---

# 📝 Practice Set – Merging and Splitting Arrays (Module 8)

---

## **Part A – Stacking (hstack, vstack, dstack)**

1. Two classes’ marks are stored: `[80, 85, 90]` and `[75, 88, 92]`. Combine them **side by side** using `hstack()`.

2. Marks of two students are stored separately: `[70, 80, 90]` and `[65, 75, 85]`. Stack them **row-wise** using `vstack()`.

3. A shop records prices `[100,200,300]` and quantities `[2,3,4]`. Stack them **depth-wise** using `dstack()` to create a 3D array.

4. Create two arrays: `sales_q1 = [200,300,400]` and `sales_q2 = [250,350,450]`. Use `hstack()` to merge them into one row.

5. Stack the following 2 arrays vertically:
   `arr1 = [10,20,30]`
   `arr2 = [40,50,60]`

---

## **Part B – Concatenating**

6. Concatenate sales data from two months: `[500,600,700]` and `[800,900,1000]`.

7. Concatenate two 2D arrays row-wise:

   ```
   [[1,2],
    [3,4]]
   ```

   and

   ```
   [[5,6],
    [7,8]]
   ```

8. Concatenate two 2D arrays column-wise:

   ```
   [[10,20],
    [30,40]]
   ```

   and

   ```
   [[50,60],
    [70,80]]
   ```

9. Merge two employee ID arrays: `[101,102,103]` and `[104,105,106]`.

10. Combine two product names arrays: `["Tea","Coffee"]` and `["Juice","Soda"]`.

---

## **Part C – Splitting (split, hsplit, vsplit)**

11. Split sales data `[200,300,400,500,600,700]` into **3 equal parts**.

12. Split a student marks array `[50,60,70,80,90,100]` into **2 equal halves**.

13. A dataset

```
[[80,85],
 [90,95],
 [70,75]]
```

Split it into **two column arrays** using `hsplit()`.

14. The same dataset:

```
[[80,85],
 [90,95],
 [70,75]]
```

Split it into **individual student rows** using `vsplit()`.

15. A 1D array `[10,20,30,40,50,60]` needs to be split into **3 parts** using `split()`.

---

## **Part D – Applied Real-World Scenarios**

16. A company has two arrays: employee salaries `[40000,50000,60000]` and bonuses `[5000,6000,7000]`. Stack them horizontally to see total compensation structure.

17. Daily sales for **Week 1** = `[100,200,150,300,250,400,350]`.
    Split this array into two equal halves: **first 3 days** and **last 4 days**.

18. Store sales records of **two branches** in arrays `[200,300,400]` and `[150,250,350]`. Stack them vertically to compare.

19. You have exam scores of students in two arrays: `[60,70,80]` (Math) and `[65,75,85]` (Science). Use `dstack()` to create a combined dataset for analysis.

20. Split a 2D array of employee performance:

```
[[80,75,90],
 [85,70,95],
 [60,88,92]]
```

* First split into 3 row arrays (`vsplit`).
* Then split into 3 column arrays (`hsplit`).

---






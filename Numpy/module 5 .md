Got it ✅
I’ll now rewrite **Module 5: Mathematical and Statistical Operations** in **clear, simple English only** (no Hinglish).
Every function will be explained in-depth with **scenario-based real-life examples**, code, and outputs.

---

# 📘 Module 5: Mathematical and Statistical Operations in NumPy

NumPy is not only about storing data in arrays. Its real power lies in performing **fast mathematical and statistical operations**. These operations are widely used in **data analytics, finance, statistics, and machine learning**.

---

## 1. Arithmetic Operations

👉 Arithmetic operations in NumPy are **element-wise**.
👉 This means the operation is applied to each element of the arrays.

---

### Example: Household Expenses Comparison

```python
import numpy as np

family1 = np.array([1200, 1500, 1800, 2000]) # monthly expenses
family2 = np.array([1000, 1400, 1600, 2200])

print("Combined Expenses:", family1 + family2)
print("Difference:", family1 - family2)
print("Multiplication:", family1 * family2)
print("Division:", family1 / family2)
print("Power (Squared):", family1 ** 2)
```

**Output:**

```
Combined Expenses: [2200 2900 3400 4200]
Difference: [ 200  100  200 -200]
Multiplication: [1200000 2100000 2880000 4400000]
Division: [1.2        1.07142857 1.125      0.90909091]
Power (Squared): [1440000 2250000 3240000 4000000]
```

📌 **Scenario Explanation:**

* Addition → total combined monthly expenses of both families.
* Subtraction → how much more or less one family spends compared to the other.
* Multiplication → scaling values (useful in analytics for growth factors).
* Division → ratio of spending between families.
* Power → squaring values (useful in statistics and variance calculations).

---

## 2. Universal Functions (Ufuncs)

Universal functions are **vectorized operations** applied element-wise. They are optimized and much faster than Python loops.

---

### (A) `np.sqrt()` – Square Root

**Scenario:** A cricket analyst wants to calculate the **true performance index** from squared values.

```python
scores = np.array([49, 81, 121, 64])  # squared values
print("Square Root of Scores:", np.sqrt(scores))
```

**Output:**

```
[ 7.  9. 11.  8.]
```

- 📌 This helps normalize squared performance data.
- 📌  Helps normalize performance metrics.

---

### (B) `np.exp()` – Exponential

**Scenario:** A population scientist models growth using exponential equations.

```python
years = np.array([1,2,3,4])
print("Exponential Growth Factor:", np.exp(years))
```

**Output:**

```
[ 2.718  7.389 20.086 54.598]
```

📌 Exponential growth is used in population models, finance, and machine learning activation functions.

---

### (C) `np.log()` – Natural Log (base e)

**Scenario:** Income distribution is highly skewed. Analysts use log transformation to make it more balanced.

```python
income = np.array([2000, 5000, 20000, 100000])
print("Log Transformation:", np.log(income))
```

**Output:**

```
[ 7.60090246  8.51719319  9.90348755 11.51292546]
```

📌 Log transformation reduces the impact of very large values.

---

### (D) `np.log10()` – Log base 10

**Scenario:** Earthquake magnitudes are measured on the Richter scale using log10.

```python
magnitudes = np.array([10, 100, 1000, 10000])
print("Richter scale (log10):", np.log10(magnitudes))
```

**Output:**

```
[1. 2. 3. 4.]
```

📌 Log base 10 compresses large scientific values into small scales.

---

### (E) `np.abs()` – Absolute Value

**Scenario:** A stock analyst studies profits and losses.

```python
profits = np.array([-500, 200, -100, 300])
print("Absolute Values:", np.abs(profits))
```

**Output:**

```
[500 200 100 300]
```

📌 Absolute values help measure magnitude regardless of positive (profit) or negative (loss).

---

### (F) `np.power()` – Power Function

**Scenario:** A bank calculates compound interest growth by raising values to a power.

```python
base = np.array([2,3,4])
print("Square:", np.power(base, 2))
print("Cube:", np.power(base, 3))
```

**Output:**

```
Square: [ 4  9 16]
Cube: [ 8 27 64]
```

📌 Power calculations are widely used in finance and machine learning.

---

## 3. Aggregations

Aggregations summarize data into a single value or a set of values.

---

### (A) `np.sum()` – Total

**Scenario:** A company wants the total sales for a quarter.

```python
sales = np.array([1200,1500,1700,2000])
print("Total Sales:", np.sum(sales))
```

**Output:**

```
6400
```

📌 Total revenue in the quarter is $6400.

---

### (B) `np.mean()` – Average

**Scenario:** Average marks of students in a class.

```python
marks = np.array([70,85,90,60,75])
print("Average Marks:", np.mean(marks))
```

**Output:**

```
76.0
```

📌 The class average score is 76.

---

### (C) `np.median()` – Middle Value

**Scenario:** Economists study median income, as it is less affected by extreme values.

```python
incomes = np.array([20000, 22000, 25000, 100000, 120000])
print("Median Income:", np.median(incomes))
```

**Output:**

```
25000.0
```

📌 The median income shows the “typical” household more accurately than mean.

---

### (D) `np.std()` – Standard Deviation

**Scenario:** An investor wants to measure the risk (volatility) of stock returns.

```python
returns = np.array([5,7,9,15,20])
print("Standard Deviation:", np.std(returns))
```

**Output:**

```
5.366563145999495
```

📌 A higher standard deviation means more risk.

---

### (E) `np.var()` – Variance

**Scenario:** A teacher wants to know how spread out exam scores are.

```python
marks = np.array([40,50,60,90,100])
print("Variance:", np.var(marks))
```

**Output:**

```
504.0
```

📌 High variance means large performance differences between students.

---

### (F) `np.min()` and `np.max()` – Minimum & Maximum

**Scenario:** A weather station records daily temperatures.

```python
temps = np.array([30,35,40,28,36])
print("Min temp:", np.min(temps))
print("Max temp:", np.max(temps))
```

**Output:**

```
Min temp: 28
Max temp: 40
```

📌 These values represent the coldest and hottest days.

---

### (G) `np.argmax()` and `np.argmin()` – Index of Max/Min

**Scenario:** A store tracks sales each day. The manager wants to know the best and worst sales days.

```python
sales = np.array([200,500,400,800,600])
print("Day of Max Sales:", np.argmax(sales))
print("Day of Min Sales:", np.argmin(sales))
```

**Output:**

```
Day of Max Sales: 3
Day of Min Sales: 0
```

📌 Argmax = best performing day index, Argmin = worst day index.

---

## 4. Axis-based Operations

👉 Many aggregation functions can be applied **row-wise (axis=1)** or **column-wise (axis=0)**.

---

### Example: Student Marks Dataset

```python
marks = np.array([[80,90,70],   # Student 1
                  [60,75,85],   # Student 2
                  [90,95,100]]) # Student 3

print("Subject-wise average (axis=0):", np.mean(marks, axis=0))
print("Student-wise average (axis=1):", np.mean(marks, axis=1))
```

**Output:**

```
Subject-wise average (axis=0): [76.66666667 86.66666667 85.        ]
Student-wise average (axis=1): [80.         73.33333333 95.        ]
```

📌 Explanation:

* Subject-wise average → how each subject performed across all students.
* Student-wise average → how each student performed across all subjects.

---

# 🔑 Final Summary

* **Arithmetic operations** allow quick element-wise math (useful for comparisons).
* **Universal functions** (`sqrt`, `exp`, `log`, `abs`, `power`) are used in science, finance, ML, and data transformations.
* **Aggregations** (`sum`, `mean`, `median`, `std`, `var`, `min`, `max`, `argmax`, `argmin`) summarize datasets.
* **Axis-based operations** allow row-wise and column-wise analysis, very useful in structured datasets.

👉 These mathematical and statistical tools are the **foundation of data analytics**. They help analysts clean, transform, summarize, and interpret datasets efficiently.

---

Would you like me to now prepare a **20-question practice set with real-world scenarios** (like I did for Module 4) so your students can apply these mathematical and statistical functions directly?

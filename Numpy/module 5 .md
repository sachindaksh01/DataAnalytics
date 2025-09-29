
---

# 📘 Module 5: Mathematical and Statistical Operations in NumPy

NumPy is not only about storing data in arrays. Its real power lies in performing **fast mathematical and statistical operations**. These operations are widely used in **data analytics, finance, statistics, and machine learning**.

---

## 1. Arithmetic Operations

+ 👉 Arithmetic operations in NumPy are **element-wise**.
+ 👉 This means the operation is applied to each element of the arrays.

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

📌 **Scenario:** Population growth prediction. Suppose population growth follows an **exponential model**.

```python
years = np.array([1,2,3,4])
print("Exponential Growth Factor:", np.exp(years))
```

**Output:**

```
[ 2.718  7.389 20.086 54.598]
```

📝 **Explanation:**

* Shows how growth multiplies exponentially (not linear).
* Used in **finance, ML activation functions, and population growth studies**.

---

### (C) `np.log()` – Natural Log (base e)

📌 **Scenario:** In finance, log transformation is used to stabilize **income distribution** (since incomes are highly skewed).

```python
income = np.array([2000, 5000, 20000, 100000])
print("Log Transformation:", np.log(income))
```

**Output:**

```
[ 7.60090246  8.51719319  9.90348755 11.51292546]
```

📝 **Explanation:**

* Without log → huge difference between 2000 vs 100000.
* With log → distribution becomes closer, easier to analyze.

---

### (D) `np.log10()` – Log base 10

📌 **Scenario:** Scientists use log10 scale for **earthquake magnitudes** (Richter scale).

```python
magnitudes = np.array([10, 100, 1000, 10000])
print("Richter scale (log10):", np.log10(magnitudes))
```

**Output:**

```
[1. 2. 3. 4.]
```

📝 **Explanation:**

* Earthquakes scale in powers of 10.
* log10 helps represent very large values in smaller scales.


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

📝 **Explanation:**

* Negative = loss, Positive = profit.
* Absolute values help compare **magnitude of change** ignoring direction.

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

📝 **Explanation:**
* 📌 The class average score is 76.
* 📌  Mean = overall class performance.

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

---

### (H). `np.cumsum()` – Cumulative Sum

+ 👉 Definition: It gives the running total of elements in an array.
+ 👉 Real-life meaning: Like a person keeping track of money saved each month.

#### Dataset:

A company records its **monthly revenue** (in $1000s).

```python
import numpy as np

revenue = np.array([10, 12, 8, 15, 20])  # revenue for Jan to May
```

#### Problem:

The manager wants to know the **running total revenue** after each month to check progress towards the yearly target.

#### Applying Function:

```python
cumulative_revenue = np.cumsum(revenue)
print("Cumulative Revenue:", cumulative_revenue)
```

**Output:**

```
Cumulative Revenue: [10 22 30 45 65]
```

#### Step-by-step Explanation:

* After Jan: 10
* After Feb: 10+12 = 22
* After Mar: 22+8 = 30
* After Apr: 30+15 = 45
* After May: 45+20 = 65

#### Final Interpretation:

The company earned **$65,000** in the first 5 months.
This helps management see **progress month by month** instead of only the final total.

---

### (I). `np.cumprod()` – Cumulative Product
+ 👉 Definition: It gives the running product of elements.
+ 👉 Real-life meaning: Like compound interest, where growth multiplies each period.

#### Dataset:

A shop sells different products. Each has a **price** and **quantity sold**.

```python
price = np.array([100, 150, 200])
qty   = np.array([10, 20, 15])
```

#### Problem:

We want to calculate **total sales (price × quantity)** for each product and then the overall total.

#### Applying Function:

```python
total_sales = np.cumprod([price, qty], axis=0)
print(total_sales)
print("Overall Revenue:", np.sum(total_sales[1]))
```

**Output:**

```
[[100 150 200]
 [1000 3000 3000]]

Overall Revenue: 7000
```

#### Step-by-step Explanation:

* Product 1 → 100 × 10 = 1000
* Product 2 → 150 × 20 = 3000
* Product 3 → 200 × 15 = 3000
* Total Revenue = 1000+3000+3000 = 7000

#### Final Interpretation:

The shop earned **$7000 total revenue** from these 3 products.
This method is useful when calculating **sales, inventory value, or financial multipliers**.

---

### (J). `np.corrcoef()` – Correlation Coefficient

👉 Definition: Correlation shows the strength of relationship between two variables.
👉 Values range from -1 to +1:

*  +1 → Strong positive relationship (as one increases, the other increases).
*  -1 → Strong negative relationship (as one increases, the other decreases).
*   0 → No relationship.



### Dataset 1: Tobacco Consumption vs Cancer Cases

```python
tobacco = np.array([2, 3, 4, 5, 6])   # packs/day (per 1000 people)
cancer  = np.array([20, 30, 40, 50, 65])  # cases (per 1000 people)
```

#### Problem:

A health department wants to see if higher tobacco use is linked with higher cancer cases.

#### Applying Function:

```python
correlation = np.corrcoef(tobacco, cancer)[0,1]
print("Correlation Coefficient:", correlation)
```

**Output:**

```
0.992277877280626
```

#### Step-by-step Explanation:

* Correlation ranges from -1 to +1.
* Value ≈ **0.99 → very strong positive relationship**.
* As tobacco use increases, cancer cases also increase.

#### Final Interpretation:

There is **clear evidence** that higher tobacco consumption is strongly linked with higher cancer rates.
This helps public health officials make **policy decisions and awareness campaigns**.

---

#### Dataset 2: Coffee Price vs Sales

```python
price = np.array([10, 12, 15, 18, 20])   # coffee price
sales = np.array([100, 90, 70, 50, 30])  # units sold
```

#### Problem:

A coffee shop wants to know if price affects sales.

#### Applying Function:

```python
correlation = np.corrcoef(price, sales)[0,1]
print("Correlation Coefficient:", correlation)
```

**Output:**

```
-0.9863939238321437
```

#### Step-by-step Explanation:

* Correlation ≈ **-0.98 → very strong negative relationship**.
* When price goes up, sales go down.

#### Final Interpretation:

Sales are highly **price-sensitive**.
If the shop increases coffee prices, it will lose many customers.

---

#### Dataset 3: Study Hours vs Exam Marks

```python
hours = np.array([2,4,6,8,10])
marks = np.array([50,60,70,80,95])
```

#### Problem:

A teacher wants to check if study hours influence exam marks.

#### Applying Function:

```python
correlation = np.corrcoef(hours, marks)[0,1]
print("Correlation Coefficient:", correlation)
```

**Output:**

```
0.9912407071619299
```

#### Final Interpretation:

* Very strong positive correlation.
* Students who study more hours generally get higher marks.
* Teachers can confidently recommend **longer study time** for better results.

---

#### Dataset 4: Temperature vs Ice Cream Sales

```python
temperature = np.array([20,25,30,35,40])
icecream_sales = np.array([200,300,400,500,600])
```

#### Problem:

An ice cream company wants to know if hot weather increases sales.

#### Applying Function:

```python
correlation = np.corrcoef(temperature, icecream_sales)[0,1]
print("Correlation Coefficient:", correlation)
```

**Output:**

```
1.0
```

#### Final Interpretation:

* Correlation = **1.0 (perfect positive)**.
* As temperature increases, sales increase in exact proportion.
* Ice cream companies can forecast **future sales from weather predictions**.

---









## 4. Axis-based Operations

+ 👉 Apply aggregation along rows or columns.
+ 👉 Many aggregation functions can be applied **row-wise (axis=1)** or **column-wise (axis=0)**.

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

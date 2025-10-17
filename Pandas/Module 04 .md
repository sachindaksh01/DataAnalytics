---

# 🧩 **Module 4: Data Aggregation & Grouping**

---

## 🎯 **Learning Goals**

By the end of this module, students will be able to:

* Group data and calculate totals, averages, and counts.
* Create pivot tables.
* Analyze relationships between columns using `crosstab`.
* Perform rolling and cumulative (window-based) calculations.

---

## 🔹 **4.1 Grouping Data**

---

### 🧠 What is Grouping?

Grouping means **collecting similar data together** and then applying a calculation on it (like sum, average, count, etc.).

In real life —

> Think of a sales report where you want to know **total sales per city** or **average marks per subject**.

That’s what **`groupby()`** does in Pandas.

---

### 🧩 **Example Dataset**

```python
import pandas as pd

data = {
    'City': ['Delhi', 'Delhi', 'Mumbai', 'Mumbai', 'Kolkata', 'Kolkata'],
    'Salesperson': ['Amit', 'Priya', 'Ravi', 'Simran', 'John', 'Alex'],
    'Sales': [200, 250, 300, 350, 150, 180]
}

df = pd.DataFrame(data)
print(df)
```

**Output:**

| City    | Salesperson | Sales |
| ------- | ----------- | ----- |
| Delhi   | Amit        | 200   |
| Delhi   | Priya       | 250   |
| Mumbai  | Ravi        | 300   |
| Mumbai  | Simran      | 350   |
| Kolkata | John        | 150   |
| Kolkata | Alex        | 180   |

---

### ✅ **Basic Grouping**

Group by city:

```python
df.groupby('City')
```

This creates a grouped object — you need to apply a function like `sum()`, `mean()`, etc.

---

### ✅ **Sum of Sales per City**

```python
df.groupby('City')['Sales'].sum()
```

**Output:**

| City    | Sales |
| ------- | ----- |
| Delhi   | 450   |
| Kolkata | 330   |
| Mumbai  | 650   |

---

### ✅ **Average Sales per City**

```python
df.groupby('City')['Sales'].mean()
```

**Output:**

| City    | Sales |
| ------- | ----- |
| Delhi   | 225.0 |
| Kolkata | 165.0 |
| Mumbai  | 325.0 |

---

### ✅ **Count of Records per City**

```python
df.groupby('City')['Sales'].count()
```

**Output:**

| City    | Sales |
| ------- | ----- |
| Delhi   | 2     |
| Kolkata | 2     |
| Mumbai  | 2     |

---

### ✅ **Multiple Aggregations**

Use `.agg()` to apply multiple functions together:

```python
df.groupby('City')['Sales'].agg(['sum', 'mean', 'count'])
```

**Output:**

| City    | sum | mean  | count |
| ------- | --- | ----- | ----- |
| Delhi   | 450 | 225.0 | 2     |
| Kolkata | 330 | 165.0 | 2     |
| Mumbai  | 650 | 325.0 | 2     |

---

📘 **Real-Life Example:**
If you’re a sales manager, this helps you find:

* Total sales per city
* Average sales per salesperson
* Number of sales entries per region

All with one line of code!

---

## 🔹 **4.2 Pivot Table**

---

### 🧠 What is a Pivot Table?

A Pivot Table is a **summary table** that groups and calculates data — just like Excel’s pivot.

Syntax:

```python
df.pivot_table(values='column_to_calculate', index='group_by_column', aggfunc='function')
```

---

### ✅ **Example: Total Sales by City**

```python
df.pivot_table(values='Sales', index='City', aggfunc='sum')
```

**Output:**

| City    | Sales |
| ------- | ----- |
| Delhi   | 450   |
| Kolkata | 330   |
| Mumbai  | 650   |

---

### ✅ **Example: Average Sales by City**

```python
df.pivot_table(values='Sales', index='City', aggfunc='mean')
```

---

### ✅ **Pivot with Multiple Columns**

```python
df.pivot_table(values='Sales', index='City', columns='Salesperson', aggfunc='sum', fill_value=0)
```

This creates a table with cities as rows and salespeople as columns — great for multi-level analysis.

---

📘 **Real-Life Example:**
In a company, you can use pivot tables to see:

* Average sales per product category per city
* Total revenue per month
* Number of employees per department

---

## 🔹 **4.3 Crosstab**

---

### 🧠 What is Crosstab?

A **crosstab (cross-tabulation)** is used to **count relationships** between two categorical variables.

Example:
If you have Gender and City, you can see **how many males and females** are in each city.

---

### ✅ **Example Dataset**

```python
data = {
    'City': ['Delhi', 'Delhi', 'Mumbai', 'Mumbai', 'Kolkata', 'Kolkata'],
    'Gender': ['M', 'F', 'M', 'F', 'M', 'M']
}
df = pd.DataFrame(data)
```

---

### ✅ **Creating a Crosstab**

```python
pd.crosstab(df['City'], df['Gender'])
```

**Output:**

| Gender  | F | M |
| ------- | - | - |
| City    |   |   |
| Delhi   | 1 | 1 |
| Kolkata | 0 | 2 |
| Mumbai  | 1 | 1 |

---

📘 **Real-Life Example:**
You can use crosstab to find:

* Number of male/female customers in each city
* Number of students passed/failed by subject
* Number of employees in each department by gender

---

## 🔹 **4.4 Window Functions**

---

### 🧠 What are Window Functions?

Window functions help calculate **moving averages, cumulative sums, and trends** over a “window” (range) of rows.

Example: Daily sales — we can calculate **7-day average**, **cumulative total**, or **weighted mean**.

+ Learn more about [window Functions](https://github.com/sachindaksh01/DataAnalytics/blob/main/Pandas/other/Window_Function%20.md) 

---

### ✅ Example Dataset

```python
data = {'Day': [1,2,3,4,5,6,7],
        'Sales': [100, 120, 80, 150, 200, 180, 160]}
df = pd.DataFrame(data)
```

---

### 🔹 **Rolling Window**

`rolling()` creates a moving window.

```python
df['3_day_avg'] = df['Sales'].rolling(window=3).mean()
print(df)
```

**Output:**

| Day | Sales | 3_day_avg |
| --- | ----- | --------- |
| 1   | 100   | NaN       |
| 2   | 120   | NaN       |
| 3   | 80    | 100.0     |
| 4   | 150   | 116.6     |
| 5   | 200   | 143.3     |
| 6   | 180   | 176.6     |
| 7   | 160   | 180.0     |

🧠 Meaning: The 3-day average sales value is calculated using the current and previous 2 days.

---

### 🔹 **Expanding Window**
+ More about : [Expanding Window](https://github.com/sachindaksh01/DataAnalytics/blob/main/Pandas/other/Expanding_Window%20.md)

`expanding()` calculates **cumulative (till now)** results.

```python
df['Cumulative_Avg'] = df['Sales'].expanding().mean()
```

**Output:**

| Day | Sales | Cumulative_Avg |
| --- | ----- | -------------- |
| 1   | 100   | 100.0          |
| 2   | 120   | 110.0          |
| 3   | 80    | 100.0          |
| 4   | 150   | 112.5          |
| 5   | 200   | 130.0          |
| 6   | 180   | 138.3          |
| 7   | 160   | 141.4          |

---

### 🔹 **Exponentially Weighted Moving Average (EWMA)**

`ewm()` gives **more importance to recent data** — often used in stock market analysis.

```python
df['EWMA'] = df['Sales'].ewm(span=3, adjust=False).mean()
```

**Output (approximate):**

| Day | Sales | EWMA  |
| --- | ----- | ----- |
| 1   | 100   | 100.0 |
| 2   | 120   | 113.3 |
| 3   | 80    | 97.8  |
| 4   | 150   | 129.2 |
| 5   | 200   | 173.8 |
| 6   | 180   | 176.3 |
| 7   | 160   | 168.4 |

---

📘 **Real-Life Example:**
In a company:

* `rolling()` helps you track **weekly average sales**.
* `expanding()` helps calculate **total revenue till date**.
* `ewm()` helps track **recent performance trends**.

---

## 🧩 **Summary of Module 4**

| Concept                     | Description                                 | Example                                            |
| --------------------------- | ------------------------------------------- | -------------------------------------------------- |
| `df.groupby()`              | Group data by column                        | `df.groupby('City').sum()`                         |
| `.sum(), .mean(), .count()` | Common aggregation functions                | `df.groupby('City')['Sales'].mean()`               |
| `.agg()`                    | Apply multiple functions                    | `df.groupby('City')['Sales'].agg(['sum', 'mean'])` |
| `df.pivot_table()`          | Create Excel-like summary                   | `df.pivot_table(values='Sales', index='City')`     |
| `pd.crosstab()`             | Count relationship between categories       | `pd.crosstab(df['City'], df['Gender'])`            |
| `df.rolling()`              | Moving window calculations                  | `df['Sales'].rolling(3).mean()`                    |
| `df.expanding()`            | Cumulative calculations                     | `df['Sales'].expanding().mean()`                   |
| `df.ewm()`                  | Weighted average (recent data matters more) | `df['Sales'].ewm(span=3).mean()`                   |

---

## 💡 **Real-Life Analogy**

Imagine you’re managing a business:

* `groupby()` helps you check **sales per city or salesperson**.
* `pivot_table()` helps you summarize reports.
* `crosstab()` helps you compare **categories** (e.g., gender vs city).
* `rolling()` and `ewm()` help track **daily trends** in performance.

All this — in just a few lines of Python code! 🐍

---



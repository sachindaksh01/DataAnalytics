
---

# 🧩 **Module 5: Merging, Joining, and Concatenation (Intermediate Level)**

---

## 🎯 **Learning Goals**

After completing this module, students will be able to:

* Combine multiple DataFrames together using Pandas
* Merge and join tables like SQL joins or Excel lookups
* Handle missing and updated data using `combine_first()` and `update()`

---

## 🔹 **5.1 Concatenation**

---

### 🧠 What is Concatenation?

**Concatenation** means joining **DataFrames one after another** —
either vertically (row-wise) or horizontally (column-wise).

📘 Think of it like **stacking two Excel sheets** together (adding rows or columns).

---

### ✅ **Example 1: Row-wise Concatenation (default)**

```python
import pandas as pd

data1 = {
    'Name': ['Amit', 'Priya', 'Ravi'],
    'Marks': [85, 90, 78]
}
data2 = {
    'Name': ['Simran', 'John'],
    'Marks': [88, 92]
}

df1 = pd.DataFrame(data1)
df2 = pd.DataFrame(data2)

result = pd.concat([df1, df2])
print(result)
```

**Output:**

|   | Name   | Marks |
| - | ------ | ----- |
| 0 | Amit   | 85    |
| 1 | Priya  | 90    |
| 2 | Ravi   | 78    |
| 0 | Simran | 88    |
| 1 | John   | 92    |

🧠 Notice how the index repeated.
To fix it and make a clean sequence:

```python
pd.concat([df1, df2], ignore_index=True)
```

**Output:**

|   | Name   | Marks |
| - | ------ | ----- |
| 0 | Amit   | 85    |
| 1 | Priya  | 90    |
| 2 | Ravi   | 78    |
| 3 | Simran | 88    |
| 4 | John   | 92    |

---

### ✅ **Example 2: Column-wise Concatenation**

To join **side by side**, use `axis=1`.

```python
data3 = {
    'City': ['Delhi', 'Mumbai', 'Kolkata']
}
df3 = pd.DataFrame(data3)

result = pd.concat([df1, df3], axis=1)
print(result)
```

**Output:**

|   | Name  | Marks | City    |
| - | ----- | ----- | ------- |
| 0 | Amit  | 85    | Delhi   |
| 1 | Priya | 90    | Mumbai  |
| 2 | Ravi  | 78    | Kolkata |

---

📘 **Real-Life Example:**
You have two monthly sales files:

* `sales_january.csv`
* `sales_february.csv`

You can join them together using:

```python
all_sales = pd.concat([jan_sales, feb_sales], ignore_index=True)
```

---

## 🔹 **5.2 Merge / Join**

---

### 🧠 What is Merging?

Merging combines two DataFrames **based on a common column (called a key)** —
just like **SQL joins** or **Excel VLOOKUP**.

---

### ✅ Example DataFrames

```python
df1 = pd.DataFrame({
    'ID': [1, 2, 3, 4],
    'Name': ['Amit', 'Priya', 'Ravi', 'Simran']
})

df2 = pd.DataFrame({
    'ID': [3, 4, 5, 6],
    'City': ['Delhi', 'Mumbai', 'Kolkata', 'Chennai']
})
```

---

### ✅ **Inner Join** (default)

Keeps only **matching rows** from both DataFrames.

```python
pd.merge(df1, df2, how='inner', on='ID')
```

**Output:**

| ID | Name   | City    |
| -- | ------ | ------- |
| 3  | Ravi   | Kolkata |
| 4  | Simran | Mumbai  |

---

### ✅ **Left Join**

Keeps all rows from the **left** DataFrame (df1),
and matches data from the right (df2).
Missing data becomes NaN.

```python
pd.merge(df1, df2, how='left', on='ID')
```

**Output:**

| ID | Name   | City    |
| -- | ------ | ------- |
| 1  | Amit   | NaN     |
| 2  | Priya  | NaN     |
| 3  | Ravi   | Kolkata |
| 4  | Simran | Mumbai  |

---

### ✅ **Right Join**

Keeps all rows from the **right** DataFrame (df2).

```python
pd.merge(df1, df2, how='right', on='ID')
```

**Output:**

| ID | Name   | City    |
| -- | ------ | ------- |
| 3  | Ravi   | Kolkata |
| 4  | Simran | Mumbai  |
| 5  | NaN    | Kolkata |
| 6  | NaN    | Chennai |

---

### ✅ **Outer Join**

Keeps **all rows from both** DataFrames.
Where data doesn’t match, it fills with NaN.

```python
pd.merge(df1, df2, how='outer', on='ID')
```

**Output:**

| ID | Name   | City    |
| -- | ------ | ------- |
| 1  | Amit   | NaN     |
| 2  | Priya  | NaN     |
| 3  | Ravi   | Kolkata |
| 4  | Simran | Mumbai  |
| 5  | NaN    | Kolkata |
| 6  | NaN    | Chennai |

---

### ✅ **Merging on Different Column Names**

If the column names are different, use `left_on` and `right_on`:

```python
pd.merge(df1, df2, left_on='EmployeeID', right_on='ID', how='inner')
```

---

📘 **Real-Life Example:**
You have:

* `employee.csv` → Employee info (ID, Name, Department)
* `salary.csv` → Salary info (ID, Salary, Bonus)

You can merge both into one full report:

```python
report = pd.merge(employee, salary, on='ID', how='inner')
```

---

## 🔹 **5.3 Combine First / Update**

---

### 🧠 Why Use These?

When you have **two DataFrames with similar structure** but some missing data,
you can use them to **fill or update values** from one another.

---

### ✅ **df.combine_first()**

`combine_first()` fills missing values from another DataFrame.

```python
df1 = pd.DataFrame({
    'A': [1, None, 3, None],
    'B': [4, 5, None, 7]
})

df2 = pd.DataFrame({
    'A': [10, 20, 30, 40],
    'B': [50, 60, 70, 80]
})

result = df1.combine_first(df2)
print(result)
```

**Output:**

|   | A    | B    |
| - | ---- | ---- |
| 0 | 1.0  | 4.0  |
| 1 | 20.0 | 5.0  |
| 2 | 3.0  | 70.0 |
| 3 | 40.0 | 7.0  |

🧠 Missing values in df1 are replaced by df2.

---

### ✅ **df.update()**

`update()` updates existing data in one DataFrame using another (in-place).

```python
df1 = pd.DataFrame({
    'A': [1, 2, 3],
    'B': [4, 5, 6]
})

df2 = pd.DataFrame({
    'B': [40, None, 60]
})

df1.update(df2)
print(df1)
```

**Output:**

| A | B  |
| - | -- |
| 1 | 40 |
| 2 | 5  |
| 3 | 60 |

🧠 Only **non-null** values from df2 replace df1’s values.

---

📘 **Real-Life Example:**
You have an old student marks record (`df1`)
and a new file with some corrected marks (`df2`).
Use:

```python
df1.update(df2)
```

→ It will automatically update only changed marks.

---

## 🧩 **Summary of Module 5**

| Concept              | Description                                | Example                         |
| -------------------- | ------------------------------------------ | ------------------------------- |
| `pd.concat()`        | Combine DataFrames vertically/horizontally | `pd.concat([df1, df2], axis=0)` |
| `pd.merge()`         | Combine using keys like SQL join           | `pd.merge(df1, df2, on='ID')`   |
| `how='inner'`        | Keep matching rows only                    |                                 |
| `how='left'`         | All from left DataFrame                    |                                 |
| `how='right'`        | All from right DataFrame                   |                                 |
| `how='outer'`        | All rows from both                         |                                 |
| `df.combine_first()` | Fill NaN values using another DataFrame    | `df1.combine_first(df2)`        |
| `df.update()`        | Update data from another DataFrame         | `df1.update(df2)`               |

---

## 💡 **Real-Life Analogy**

Think of Pandas DataFrames as Excel sheets:

| Action            | What it’s like in Excel                  |
| ----------------- | ---------------------------------------- |
| `concat()`        | Copy-pasting sheets together             |
| `merge()`         | Using VLOOKUP or JOIN between sheets     |
| `combine_first()` | Filling blanks with backup data          |
| `update()`        | Replacing old data with corrected values |

---

## 🧠 Quick Recap Example

```python
# 1️⃣ Concatenate
pd.concat([df1, df2], ignore_index=True)

# 2️⃣ Merge
pd.merge(df1, df2, how='outer', on='ID')

# 3️⃣ Combine
df1.combine_first(df2)

# 4️⃣ Update
df1.update(df2)
```

---

Would you like me to now prepare a **Practice Set of 20 Questions + Mini Project (Data Merging and Sales Report)** for this Module 5 like we did for earlier modules?
It will include:

* Real dataset merging
* Different join types
* Concatenation tasks
* `combine_first` and `update` exercises

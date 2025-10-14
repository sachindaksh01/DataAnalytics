---

# 🧩 Module 2: Data Selection & Filtering 

---

## 🎯 **Learning Goals**

By the end of this module, students will be able to:

* Select specific rows and columns from DataFrames
* Use `loc[]` and `iloc[]`
* Filter data using conditions
* Sort data by values or index

---

## 🔹 **2.1 Indexing and Selecting Data**

---

### 📌 What is Indexing?

In Pandas, **indexing means selecting specific parts of the data** —
like choosing a few rows or columns from an Excel sheet.

If you have a DataFrame with 1000 rows, you rarely need all at once.
So, we “index” or “filter” the specific data we want.

---

### 🧠 Example Dataset

We’ll use this DataFrame in examples 👇

```python
import pandas as pd

data = {
    'Name': ['Amit', 'Priya', 'Ravi', 'Simran', 'John'],
    'Age': [21, 22, 20, 23, 25],
    'Marks': [85, 92, 78, 88, 90],
    'City': ['Delhi', 'Mumbai', 'Kolkata', 'Delhi', 'Chennai']
}

df = pd.DataFrame(data)
print(df)
```

**Output:**

|   | Name   | Age | Marks | City    |
| - | ------ | --- | ----- | ------- |
| 0 | Amit   | 21  | 85    | Delhi   |
| 1 | Priya  | 22  | 92    | Mumbai  |
| 2 | Ravi   | 20  | 78    | Kolkata |
| 3 | Simran | 23  | 88    | Delhi   |
| 4 | John   | 25  | 90    | Chennai |

---

## 🎯 Selecting Columns

There are multiple ways to select columns in Pandas.

---

### ✅ **Method 1: Single Column**

```python
df['Name']
```

or

```python
df.Name
```

Both give the same result — a **Series** of all names.

**Output:**

```
0     Amit
1     Priya
2     Ravi
3     Simran
4     John
Name: Name, dtype: object
```

📘 **Tip:**
Use `df['column']` (with square brackets) instead of `df.column` if your column name has spaces or special characters.

---

### ✅ **Method 2: Multiple Columns**

```python
df[['Name', 'Marks']]
```

**Output:**

| Name   | Marks |
| ------ | ----- |
| Amit   | 85    |
| Priya  | 92    |
| Ravi   | 78    |
| Simran | 88    |
| John   | 90    |

---

## 🎯 Selecting Rows

Now let’s move to **rows selection** — for that we use `.loc[]` and `.iloc[]`.

---

### 🧩 **df.loc[] → Label-based Selection**

* `loc[]` is used to select data **by labels (names)** — meaning row index name or column name.

#### Example 1:

```python
df.loc[0]
```

→ returns the row with **index label = 0**

#### Example 2:

Select multiple rows:

```python
df.loc[0:2]
```

**Output:**
Shows rows with index 0, 1, 2 (note: loc includes the last index).

---

#### Example 3:

Select rows and specific columns:

```python
df.loc[0:2, ['Name', 'City']]
```

**Output:**

| Name  | City    |
| ----- | ------- |
| Amit  | Delhi   |
| Priya | Mumbai  |
| Ravi  | Kolkata |

---

### 🧩 **df.iloc[] → Position-based Selection**

* `iloc[]` is used to select data **by position (numbers)** —
  It doesn’t care about labels, just counts from 0.

#### Example 1:

```python
df.iloc[0]
```

→ First row

#### Example 2:

```python
df.iloc[0:3]
```

→ Rows 0, 1, 2 (end excluded)

#### Example 3:

```python
df.iloc[0:3, 0:2]
```

→ First 3 rows and first 2 columns.

---

📊 **Difference between loc[] and iloc[]**

| Feature   | `loc[]`                | `iloc[]`                |
| --------- | ---------------------- | ----------------------- |
| Based on  | Label (name)           | Position (index number) |
| End index | Inclusive              | Exclusive               |
| Example   | `df.loc[0:2]` → 3 rows | `df.iloc[0:2]` → 2 rows |

---

## 🎯 Slicing Rows and Columns

You can slice rows and columns similar to Python lists.

```python
df[0:3]   # First 3 rows
```

**Output:** rows with index 0, 1, 2

You can also combine slicing with column selection:

```python
df.loc[1:3, 'Name']
```

**Output:**

```
1     Priya
2     Ravi
3     Simran
```

---

## 🎯 Conditional Filtering

This is one of the most powerful features in Pandas.
You can filter rows based on **conditions** — like in Excel filters.

---

### ✅ **Example 1: Filter rows where Marks > 85**

```python
df[df['Marks'] > 85]
```

**Output:**

| Name   | Age | Marks | City    |
| ------ | --- | ----- | ------- |
| Priya  | 22  | 92    | Mumbai  |
| Simran | 23  | 88    | Delhi   |
| John   | 25  | 90    | Chennai |

---

### ✅ **Example 2: Filter rows where Age > 21 and City == 'Delhi'**

```python
df[(df['Age'] > 21) & (df['City'] == 'Delhi')]
```

**Output:**

| Name   | Age | Marks | City  |
| ------ | --- | ----- | ----- |
| Simran | 23  | 88    | Delhi |

---

### ✅ **Example 3: Filter rows where City is not ‘Delhi’**

```python
df[df['City'] != 'Delhi']
```

---

### ✅ **Example 4: Filter rows where Marks between 80 and 90**

```python
df[(df['Marks'] >= 80) & (df['Marks'] <= 90)]
```

---

### ✅ **Example 5: Multiple OR condition**

```python
df[(df['City'] == 'Delhi') | (df['City'] == 'Mumbai')]
```

---

📘 **Real-Life Example:**
Imagine this DataFrame represents **sales records**:

| Product | Sales | Region |
| ------- | ----- | ------ |
| A       | 150   | North  |
| B       | 90    | South  |
| C       | 120   | North  |

You can easily find:

```python
df[df['Sales'] > 100]
```

→ Products that sold more than 100 units.

---

## 🔹 **2.2 Sorting**

Sorting means arranging data in a specific order — either by **column values** or by **index**.

---

### ✅ **Sorting by Column Values**

```python
df.sort_values(by='Marks')
```

→ Sorts by Marks in ascending order (default).

---

### ✅ **Descending Order**

```python
df.sort_values(by='Marks', ascending=False)
```

→ Highest marks first.

---

### ✅ **Sort by Multiple Columns**

```python
df.sort_values(by=['City', 'Marks'], ascending=[True, False])
```

→ Sorts by city alphabetically, and within city, by marks descending.

---

### ✅ **Sort by Index**

```python
df.sort_index()
```

→ Sorts DataFrame rows by their index labels.

---

### ✅ **Reset Index After Sorting**

When you sort data, the original index stays. To reset:

```python
df.sort_values(by='Marks', ascending=False).reset_index(drop=True)
```

---

## 🎯 **Real-Life Example: Sorting**

Let’s say you have an online store dataset:

| Product | Sales | Rating |
| ------- | ----- | ------ |
| A       | 200   | 4.5    |
| B       | 150   | 4.8    |
| C       | 180   | 4.2    |

If you want to see **highest sales first**:

```python
df.sort_values(by='Sales', ascending=False)
```

Or, to see **best rated products first**:

```python
df.sort_values(by='Rating', ascending=False)
```

---

## 🧩 **Summary of Module 2**

| Concept                | Description                  |
| ---------------------- | ---------------------------- |
| `df['col']`            | Select a single column       |
| `df[['col1', 'col2']]` | Select multiple columns      |
| `df.loc[]`             | Label-based selection        |
| `df.iloc[]`            | Position-based selection     |
| Conditional filtering  | Filter rows using conditions |
| `df.sort_values()`     | Sort by column values        |
| `df.sort_index()`      | Sort by index                |

---

## 🧠 Real-Life Analogy

Think of Pandas like **Google Sheets with superpowers**:

* You can instantly filter all Delhi students with marks > 90
* Sort them by age or city
* Pick only the “Name” and “Marks” columns

All that — with just one or two lines of Python code 💪

---


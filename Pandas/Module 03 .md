---

# 🧩 **Module 3: Data Cleaning & Preprocessing **

---

## 🎯 **Learning Goals**

By the end of this module, students will be able to:

* Detect and handle missing data
* Replace, fill, or remove unwanted values
* Apply transformations and custom functions
* Handle duplicate rows
* Clean text and string data

---

## 🔹 **3.1 Handling Missing Data**

---

### 🧠 What is Missing Data?

Missing data means that **some cells have no value** — for example, in an Excel sheet you might see blank cells.

In Pandas, missing data is represented as:

```python
NaN  (Not a Number)
```

Let’s see an example:

```python
import pandas as pd

data = {
    'Name': ['Amit', 'Priya', 'Ravi', 'Simran', 'John'],
    'Age': [21, None, 20, 23, None],
    'Score': [90, 97, None, 93, 95],
    'City': ['Kolkata ', 'kolkata', ' Mumbai', 'delhi', 'mumbai']
}

df = pd.DataFrame(data)
print(df)
```

**Output:**

| Name   | Age  | Marks |
| ------ | ---- | ----- |
| Amit   | 21.0 | 85.0  |
| Priya  | NaN  | 92.0  |
| Ravi   | 20.0 | NaN   |
| Simran | 23.0 | 88.0  |
| John   | NaN  | 90.0  |

---

### ✅ **Checking for Missing Values**

```python
df.isnull()
```

**Output:** (Shows True for missing cells)

| Name  | Age   | Marks |
| ----- | ----- | ----- |
| False | False | False |
| False | True  | False |
| False | False | True  |
| False | False | False |
| False | True  | False |

You can also count how many are missing:

```python
df.isnull().sum()
```

**Output:**

```
Name     0
Age      2
Marks    1
dtype: int64
```

---

### ✅ **Checking for Non-Missing Values**

```python
df.notnull()
```

This does the opposite of `isnull()` — it shows True where data **exists**.

---

### ✅ **Filling Missing Values**

If you don’t want to remove missing values, you can **fill** them with something.

```python
df.fillna(0)
```

→ Fills all NaN with 0.

---

#### Example 1: Fill with a constant value

```python
df['Age'].fillna(18)
```

→ Replaces missing ages with 18.

---

#### Example 2: Fill with column mean or median

```python
df['Marks'].fillna(df['Marks'].mean())
```

→ Replaces missing marks with the average mark.

---

### ✅ **Dropping Missing Values**

If you want to remove rows having missing data:

```python
df.dropna()
```

→ Drops all rows that contain **any** NaN value.

If you want to drop only those rows where **all** values are missing:

```python
df.dropna(how='all')
```

---

### ✅ **Replacing Specific Values**

You can also replace any specific value:

```python
df.replace(85, 100)
```

→ Replaces 85 with 100 wherever it appears.

Or replace NaN with text:

```python
df['Age'].replace(to_replace=None, value=0, inplace=True)
```

---

📘 **Real-Life Example:**
Suppose you have an employee record:

| Name | Salary | Bonus |
| ---- | ------ | ----- |
| A    | 50000  | 2000  |
| B    | NaN    | 3000  |
| C    | 60000  | NaN   |

You can:

* Fill missing salary with average salary
* Fill missing bonus with 0
* Drop rows with no salary at all

All using Pandas in a few lines!

---

## 🔹 **3.2 Data Transformation**

Transformation means **changing or modifying the data** to make it more useful for analysis.

---

### ✅ **Using `df.apply()`**

`apply()` is used to apply a **function** on each column or row.

Example:

```python
df['Marks'] = df['Marks'].apply(lambda x: x + 5)
```

→ Adds 5 bonus marks to everyone.

---

### ✅ **Using `df.map()`**

`map()` works like `apply()` but is used for **Series (single column)** only.

Example:

```python


# Clean and map properly
df['City'] = df['City'].str.strip().str.title()  # clean text
df['City'] = df['City'].map({'Delhi': 'DL', 'Mumbai': 'MB', 'Kolkata': 'KK'})


```

→ Converts full names into short codes.

---

### ✅ **Using `df.replace()`**

We can use `replace()` to substitute specific values.

Example:

```python
df['Marks'].replace(92, 100, inplace=True)
```

---

### ✅ **Renaming Columns**

You can rename columns easily with `rename()`.

```python
df.rename(columns={'Marks': 'Score'}, inplace=True)
```

**Before:**

| Name | Age | Marks |
| ---- | --- | ----- |

**After:**
| Name | Age | Score |

---

### ✅ **Handling Duplicates**

You can check if duplicate rows exist:

```python
df.duplicated()
```

→ Returns True/False for each row.

---

### ✅ **Removing Duplicate Rows**

```python
df.drop_duplicates(inplace=True)
```

→ Removes all rows that appear more than once.

---

📘 **Real-Life Example:**
You have customer data and one person is entered twice.
Use `df.drop_duplicates()` to clean up the list.

---

## 🔹 **3.3 String Functions**

Real-world datasets often have messy text — capital letters, spaces, spelling mistakes, etc.
Pandas provides **string functions** to clean them.

---

### ✅ Example Dataset

```python
data = {
    'Name': ['  AMIT  ', 'priya', 'RAVI ', 'SimRan', 'john'],
    'City': ['DELHI', 'Mumbai', ' kolkata', 'Delhi', 'CHENNAI']
}
df = pd.DataFrame(data)
```

**Output (Raw):**

| Name   | City    |
| ------ | ------- |
| AMIT   | DELHI   |
| priya  | Mumbai  |
| RAVI   | kolkata |
| SimRan | Delhi   |
| john   | CHENNAI |

---

### ✨ **Common String Cleaning Functions**

All string functions are used with `.str`

#### 🔹 Convert to lowercase

```python
df['Name'] = df['Name'].str.lower()
```

#### 🔹 Convert to uppercase

```python
df['Name'] = df['Name'].str.upper()
```

#### 🔹 Remove extra spaces

```python
df['Name'] = df['Name'].str.strip()
```

#### 🔹 Check if a column contains specific word

```python
df['City'].str.contains('Delhi')
```

→ Returns True/False.

#### 🔹 Replace text

```python
df['City'] = df['City'].str.replace('DELHI', 'New Delhi', case=False)
```

#### 🔹 String length

```python
df['Name'].str.len()
```

---

📘 **Real-Life Example:**
Suppose you got data from 3 different cities, but “Delhi” is written as:

* DELHI
* delhi
* Delhi (extra space)

You can clean it in one line:

```python
df['City'] = df['City'].str.strip().str.title()
```

**Output:**
All city names become clean → *Delhi, Mumbai, Kolkata, Chennai*

---

## 🧩 **Summary of Module 3**

| Concept                                                      | Description                |
| ------------------------------------------------------------ | -------------------------- |
| `df.isnull()` / `df.notnull()`                               | Detect missing values      |
| `df.fillna()`                                                | Fill missing values        |
| `df.dropna()`                                                | Remove missing rows        |
| `df.replace()`                                               | Replace specific values    |
| `df.apply()` / `df.map()`                                    | Apply functions to data    |
| `df.rename()`                                                | Rename columns             |
| `df.duplicated()`                                            | Find duplicate rows        |
| `df.drop_duplicates()`                                       | Remove duplicate rows      |
| String functions (`.str.lower()`, `.strip()`, `.contains()`) | Clean and format text data |

---

## 💡 **Real-Life Analogy**

Think of this module like “**data laundry**” 🧺
Before analysis, you must:

* Wash out missing values
* Iron (format) your strings
* Fold neatly (remove duplicates)

Then your data is clean, beautiful, and ready for use!

---


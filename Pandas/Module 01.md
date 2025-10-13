---

# 🎯 **Module 1: Getting Started with Pandas (Beginner Level)**

---

## 🔹 **1.1 Introduction to Pandas**

### 👉 What is Pandas?

**Pandas** is a Python library used for **data analysis and data manipulation**.
It helps us work with data in a **table format** (rows and columns) — just like an **Excel sheet**.

📘 **In simple words:**
Pandas = Python + Data + Analysis

It makes data handling super easy — you can clean, analyze, and visualize data efficiently.

### 🧠 **Why use Pandas?**

Without Pandas, data handling in Python is difficult and slow.
With Pandas, you can:

* Read and write data easily (CSV, Excel, SQL, etc.)
* Filter, sort, and summarize data
* Handle missing values
* Perform mathematical operations on columns
* Merge or join datasets

📍 **Real-Life Example:**
Suppose you have a file containing all your **students’ marks** or **sales records** in Excel.
Using Pandas, you can:

* Read the file easily in Python.
* Find the **average marks** or **total sales** in just one line.
* Filter only those students who scored above 90.

---

### ⚙️ **Installing Pandas**

If you don’t have Pandas installed, open your terminal or command prompt and type:

```bash
pip install pandas
```

If you are using Jupyter Notebook:

```python
!pip install pandas
```

---

### 📦 **Importing Pandas**

Once installed, you can import it in your Python file:

```python
import pandas as pd
```

We use `pd` as a **short name (alias)** — it’s a standard in the Python community.

---

## 🔹 **1.2 Data Structures in Pandas**

Pandas has two main data structures:

1. **Series**
2. **DataFrame**

---

### 🧩 **Series**

A **Series** is like a **single column** of data.

You can think of it like:

* A column in Excel
* A list with labels

#### Example:

```python
import pandas as pd

data = [10, 20, 30, 40]
s = pd.Series(data)
print(s)
```

**Output:**

```
0    10
1    20
2    30
3    40
dtype: int64
```

Here:

* The left side (0,1,2,3) is the **index**
* The right side (10,20,30,40) is the **data**

#### ✅ Real-Life Example:

Think of a **Series** as the “Marks of a single subject” for students.

| Index | Marks |
| ----- | ----- |
| 0     | 78    |
| 1     | 85    |
| 2     | 92    |

---

### 📊 **DataFrame**

A **DataFrame** is a **table** with rows and columns — like an Excel sheet.

#### Example:

```python
data = {
    'Name': ['Amit', 'Priya', 'Ravi'],
    'Marks': [85, 92, 78],
    'Subject': ['Math', 'Science', 'English']
}

df = pd.DataFrame(data)
print(df)
```

**Output:**

|   | Name  | Marks | Subject |
| - | ----- | ----- | ------- |
| 0 | Amit  | 85    | Math    |
| 1 | Priya | 92    | Science |
| 2 | Ravi  | 78    | English |

#### ✅ Real-Life Example:

A **DataFrame** can represent a **student report card**, **sales record**, **employee data**, etc.

---

## 🔹 **1.3 Creating Data**

You can create Pandas data from many sources.

---

### 🧾 **From Lists**

```python
data = [10, 20, 30]
s = pd.Series(data)
```

---

### 🧩 **From Dictionary**

```python
data = {'Name': ['Amit', 'Ravi'], 'Marks': [85, 90]}
df = pd.DataFrame(data)
```

---

### 📦 **From Numpy Arrays**

```python
import numpy as np
arr = np.array([[1, 2], [3, 4]])
df = pd.DataFrame(arr, columns=['A', 'B'])
```

---

### 📁 **Reading from CSV**

```python
df = pd.read_csv('data.csv')
```

**Example:** Reading a student marks file.

---

### 📘 **Reading from Excel**

```python
df = pd.read_excel('students.xlsx')
```

---

### 🌐 **Reading from JSON**

```python
df = pd.read_json('data.json')
```

---

### 🗄️ **Reading from SQL Database**

```python
import sqlite3
conn = sqlite3.connect('school.db')
df = pd.read_sql('SELECT * FROM students', conn)
```

---

## 🔹 **1.4 Basic Data Inspection**

Once data is loaded, we must inspect it — just like checking the first few rows of an Excel sheet.

---

### 👀 **View top and bottom rows**

```python
df.head()    # Shows first 5 rows
df.tail()    # Shows last 5 rows
```

---

### 📐 **Check shape (rows and columns)**

```python
df.shape
```

**Example Output:** `(10, 3)`
→ 10 rows, 3 columns

---

### 🏷️ **See columns and index**

```python
df.columns
df.index
```

---

### 🧾 **Info and Summary**

```python
df.info()       # Basic info (data type, null values)
df.describe()   # Statistical summary
```

---

### 🔡 **Check Data Types**

```python
df.dtypes
```

---

### 🔁 **Convert Data Type**

```python
df['Marks'] = df['Marks'].astype(float)
```

---

## ✅ **Real-Life Case Study Example**

**Situation:**
You are working in a school, and you have a file `students.csv` containing:

| Name  | Marks | Subject |
| ----- | ----- | ------- |
| Amit  | 85    | Math    |
| Priya | 92    | Science |
| Ravi  | 78    | English |

**Tasks using Pandas:**

```python
import pandas as pd

df = pd.read_csv('students.csv')

print(df.head())            # see first few rows
print(df.describe())        # summary of marks
print(df.dtypes)            # check column types
df['Marks'] = df['Marks'].astype(float)  # convert data type
```

Now you can:

* Find average marks
* Filter students who scored above 90
* Save results into a new CSV

All this in just a few lines!

---

## 🧩 **Summary of Module 1**

| Concept         | Description                         |
| --------------- | ----------------------------------- |
| Pandas          | Python library for data handling    |
| Series          | 1D labeled data                     |
| DataFrame       | 2D table with rows & columns        |
| Data creation   | From lists, dicts, CSV, Excel, etc. |
| Data Inspection | `.head()`, `.info()`, `.describe()` |
| Data Types      | `.dtypes`, `.astype()`              |

---


---

# ✅ **Module 7: Exporting Data in Pandas**

---

## 🎯 **Learning Goals**

After completing this module, students will learn:

* How to **save (export)** DataFrames into different file formats
* How to export to **CSV, Excel, JSON, and SQL databases**
* Real-life uses of exporting data in data analysis or reporting

---

## 🔹 **7.1 Why Export Data?**

When we work with Pandas, we usually import data from different sources (CSV, Excel, APIs, SQL, etc.),
clean and analyze it — and finally, we may want to **save our results**.

👉 Example situations:

* You cleaned messy data and want to save it back to a `.csv`
* You created a sales report and want to send it to your manager in `.xlsx`
* You want to store processed data in a **database (SQL)** for use in another system

Pandas makes exporting super easy — just **one line of code!**

---

## 🔸 **7.1 Exporting to CSV**

### 🧩 CSV (Comma Separated Values)

CSV files are the most common format — simple text with comma-separated data.

---

### ✅ **Example: Exporting DataFrame to CSV**

```python
import pandas as pd

data = {
    'Name': ['Amit', 'Priya', 'Ravi'],
    'Marks': [85, 90, 78],
    'City': ['Delhi', 'Mumbai', 'Kolkata']
}

df = pd.DataFrame(data)

# Exporting to CSV
df.to_csv('students.csv', index=False)
print("Data exported successfully to students.csv")
```

🧾 **Output (File Content):**

```
Name,Marks,City
Amit,85,Delhi
Priya,90,Mumbai
Ravi,78,Kolkata
```

💡 **`index=False`** removes the index column from being saved.

---

### 🧠 **Common Parameters:**

| Parameter  | Description                   | Example            |
| ---------- | ----------------------------- | ------------------ |
| `index`    | Whether to save index or not  | `index=False`      |
| `sep`      | Change separator              | `sep=';'`          |
| `header`   | Include column names          | `header=True`      |
| `encoding` | Handle languages (like Hindi) | `encoding='utf-8'` |

---

### 💡 Real-Life Use:

You can save your **cleaned sales data** or **customer list** as a `.csv` file to share with your team.

---

## 🔸 **7.2 Exporting to Excel**

### 🧩 Excel (.xlsx)

You can directly write your DataFrame to an Excel sheet using `to_excel()`.

---

### ✅ **Example:**

```python
# Exporting to Excel file
df.to_excel('students.xlsx', sheet_name='Sheet1', index=False)
print("Data exported successfully to students.xlsx")
```

💬 This will create an Excel file named **students.xlsx** with a sheet called “Sheet1”.

---

### 🧠 **Extra Tips:**

* You need to have **openpyxl** installed (`pip install openpyxl`)


---

### 💡 Real-Life Use:

When creating **reports**, **attendance sheets**, or **monthly performance summaries**,
Excel format is best since it’s widely used by non-programmers.

---

## 🔸 **7.3 Exporting to JSON**

### 🧩 JSON (JavaScript Object Notation)

JSON is a format used to exchange data between web applications and servers.

---

### ✅ **Example:**

```python
# Exporting DataFrame to JSON
df.to_json('students.json', orient='records', indent=2)
print("Data exported successfully to students.json")
```

🧾 **Output (File Content):**

```json
[
  {"Name": "Amit", "Marks": 85, "City": "Delhi"},
  {"Name": "Priya", "Marks": 90, "City": "Mumbai"},
  {"Name": "Ravi", "Marks": 78, "City": "Kolkata"}
]
```

💡 **`orient='records'`** creates a list of JSON objects.
**`indent=2`** makes it easy to read (pretty JSON).

---

### 💡 Real-Life Use:

* Web developers use JSON to share data between backend and frontend.
* You can export your analysis results as a JSON file for API integration.

---

## 🔸 **7.4 Exporting to SQL**

### 🧩 SQL Databases

Pandas can save data directly to SQL tables using **`to_sql()`**,
but it requires a connection — usually created via **SQLAlchemy**.

---

### ✅ **Example: Exporting Data to SQL**

```python
from sqlalchemy import create_engine
import pandas as pd

# Create an in-memory SQLite database
engine = create_engine('sqlite:///:memory:')

data = {'Name': ['Amit', 'Priya', 'Ravi'], 'Marks': [85, 90, 78]}
df = pd.DataFrame(data)

# Export to SQL table
df.to_sql('students_table', con=engine, index=False, if_exists='replace')

print("Data exported to SQL table successfully!")
```

💡 **Parameters:**

| Parameter   | Description                                              |
| ----------- | -------------------------------------------------------- |
| `con`       | Database connection                                      |
| `name`      | SQL table name                                           |
| `if_exists` | What to do if table exists (`replace`, `append`, `fail`) |
| `index`     | Whether to write index column or not                     |

---

### 💡 Real-Life Use:

* Storing cleaned data into **databases** (like MySQL, PostgreSQL, SQLite)
* Used by analysts to send results for use in **web dashboards** or **data warehouses**

---

## 🧾 **Summary Table**

| Format | Function        | Example                          | Library Needed |
| ------ | --------------- | -------------------------------- | -------------- |
| CSV    | `df.to_csv()`   | `df.to_csv('file.csv')`          | None           |
| Excel  | `df.to_excel()` | `df.to_excel('file.xlsx')`       | openpyxl       |
| JSON   | `df.to_json()`  | `df.to_json('file.json')`        | None           |
| SQL    | `df.to_sql()`   | `df.to_sql('table', con=engine)` | sqlalchemy     |

---


hamm
In **data analytics and ML**, working with **files** is essential because we often need to **read datasets from files (CSV, TXT)** and **save processed results back** for future use. NumPy provides powerful functions to handle this efficiently.

---

# 📘 Module 10: File I/O with NumPy

---

## 1. Why File I/O in NumPy?

* **Load Data:** Datasets are often stored in `.txt` or `.csv` files.
* **Save Results:** Processed arrays or models can be saved for reuse.
* **Efficiency:** NumPy I/O functions are faster than plain Python file handling for numerical data.

---

## 2. Reading Arrays

---

### (A) `np.loadtxt()`

👉 **Reads text files (like CSV, TXT) into NumPy arrays.**

**Scenario:** A company stores monthly sales in a file `sales.txt` as:

```
200 300 400
500 600 700
```

```python
import numpy as np

data = np.loadtxt("sales.txt")
print(data)
```

**Output:**

```
[[200. 300. 400.]
 [500. 600. 700.]]
```

📌 **Use:** Quick loading when data is clean and consistent.

---

### (B) `np.genfromtxt()`

👉 **Reads files with missing/dirty data** (can handle NaN).

**Scenario:** A survey data file `survey.csv`:

```
25, 30, NaN
40, NaN, 35
```

```python
data = np.genfromtxt("survey.csv", delimiter=",")
print(data)
```

**Output:**

```
[[25. 30. nan]
 [40. nan 35.]]
```

📌 **Use:** Handles missing values (NaN). Perfect for messy real-world datasets.

---

## 3. Writing Arrays

---

### (A) `np.savetxt()`

👉 **Saves arrays to a text or CSV file.**

**Scenario:** Save student marks to `marks.csv`.

```python
marks = np.array([[80, 90, 70],
                  [85, 95, 75]])

np.savetxt("marks.csv", marks, delimiter=",", fmt="%d")
```

✅ File `marks.csv` will contain:

```
80,90,70
85,95,75
```

📌 **Use:** Share processed data in CSV format.

---

### (B) `np.save()` and `np.load()`

👉 Save/load arrays in **NumPy’s binary format (.npy)** (faster and preserves array type, shape).

**Scenario:** Save and reload processed dataset.

```python
arr = np.array([10,20,30,40,50])

# Save as .npy file
np.save("data.npy", arr)

# Load back
loaded_arr = np.load("data.npy")
print("Loaded Array:", loaded_arr)
```

**Output:**

```
Loaded Array: [10 20 30 40 50]
```

📌 **Use:** Efficient when working on large arrays in ML pipelines.

---

# 🔑 Summary

* **Reading:**

  * `np.loadtxt()` → read clean text/CSV data.
  * `np.genfromtxt()` → read messy data with missing values.

* **Writing:**

  * `np.savetxt()` → save arrays as text/CSV.
  * `np.save()` / `np.load()` → save/load in NumPy’s `.npy` binary format.

👉 **Real-life application in analytics:**

* Load **datasets** (sales, survey, sensor data).
* Save **processed arrays** for reuse.
* Share **clean CSVs** with others.
* Store **large ML datasets** in `.npy` for speed.

---

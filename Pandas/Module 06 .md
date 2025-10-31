---
# ✅ **Module 6: Time Series Analysis in Pandas**

---

## 🎯 **Learning Goals**

* Work with **dates and times** in Pandas
* Perform **resampling** (daily → monthly, weekly → yearly)


---

## 🔹 **6.1 DateTime Handling**

### 🧩 What is Time Series Data?

👉 **Time Series data** means data recorded over time —
for example:

* Daily stock prices 📈
* Monthly sales 📊
* Hourly temperature 🌡️

Each record has a **date/time** linked to it.

---

### 🧠 Step 1: Converting Dates into DateTime Format

Pandas can easily understand dates if you convert them using:

```python
pd.to_datetime()
```

✅ **Example:**

```python
import pandas as pd

data = {'Date': ['2024-01-01', '2024-01-02', '2024-01-03'],
        'Sales': [250, 300, 280]}

df = pd.DataFrame(data)

df['Date'] = pd.to_datetime(df['Date'])
print(df)
```

🧾 **Output:**

```
        Date  Sales
0 2024-01-01    250
1 2024-01-02    300
2 2024-01-03    280
```

✅ Now `Date` column is recognized as a **datetime object**,
so we can extract details like year, month, and day.

---

### 🧩 Step 2: Extracting Parts of Date

Once the column is converted, we can access its parts using `.dt` accessor.

```python
df['Year'] = df['Date'].dt.year
df['Month'] = df['Date'].dt.month
df['Day'] = df['Date'].dt.day
print(df)
```

🧾 **Output:**

```
        Date  Sales  Year  Month  Day
0 2024-01-01    250  2024      1    1
1 2024-01-02    300  2024      1    2
2 2024-01-03    280  2024      1    3
```

---

### 💡 Real-Life Example

When working with sales data, this helps you find:

* Which **month** has the highest sales
* How performance changes **year by year**

---

## 🔹 **6.2 Resampling**

### 🧩 What is Resampling?

👉 **Resampling** means **changing the frequency** of time series data.
Example:

* Daily → Monthly
* Monthly → Yearly

We use it to summarize data over a period.

---

### ✅ **Example: Monthly Resampling**

```python
# Creating daily sales data
dates = pd.date_range('2024-01-01', '2024-01-10')
sales = [200, 220, 210, 250, 270, 260, 230, 240, 280, 300]

df = pd.DataFrame({'Date': dates, 'Sales': sales})
df.set_index('Date', inplace=True)

# Resampling data by month
monthly_sales = df.resample('M').sum()
print(monthly_sales)
```

🧾 **Output:**

```
            Sales
Date             
2024-01-31   2460
```

💬 It grouped all daily data in January and summed it.

---

### 🧩 Other Common Resampling Options

| Code | Meaning | Example            |
| ---- | ------- | ------------------ |
| 'D'  | Daily   | `df.resample('D')` |
| 'W'  | Weekly  | `df.resample('W')` |
| 'M'  | Monthly | `df.resample('M')` |
| 'Y'  | Yearly  | `df.resample('Y')` |

✅ You can also use:

* `.mean()` for average values
* `.count()` for counting entries

Example:

```python
df.resample('W').mean()
```

---

### 💡 Real-Life Example

In a company’s sales report:

* Daily data can be **resampled monthly** to see monthly revenue
* Hourly electricity usage can be **resampled weekly** for trends

---
---

### 🧠 Other Window Functions

| Function                   | Description                           |
| -------------------------- | ------------------------------------- |
| `.rolling(window=3).sum()` | Rolling sum                           |
| `.rolling(window=5).max()` | Rolling max                           |
| `.expanding().mean()`      | Expanding mean from start             |
| `.ewm(span=3).mean()`      | Exponentially weighted moving average |

---


---

## 🧾 **Summary Table**

| Concept                | Function               | Example                      |
| ---------------------- | ---------------------- | ---------------------------- |
| Convert to datetime    | `pd.to_datetime()`     | `pd.to_datetime(df['date'])` |
| Extract year/month/day | `.dt.year` etc.        | `df['date'].dt.month`        |
| Resampling             | `.resample('M').sum()` | Group monthly                |


---

---


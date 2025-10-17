
---

## 🧩 1. Expanding Window kya hoti hai?

### 🧠 Simple soch:

Rolling window me hum keval *last n rows* ka average nikalte the.
Expanding window me hum **starting se leke current row tak sab rows ka average** nikalte hain.

Matlab —

> “Ab tak ka total ya ab tak ka average”

---

### 📊 Example Data

| Day | Sales |
| --- | ----- |
| 1   | 100   |
| 2   | 120   |
| 3   | 80    |
| 4   | 150   |
| 5   | 200   |
| 6   | 180   |
| 7   | 160   |

---

### 🧮 Step by Step Calculation

| Day | Sales | Cumulative Average Calculation               | Result |
| --- | ----- | -------------------------------------------- | ------ |
| 1   | 100   | (100) / 1                                    | 100.0  |
| 2   | 120   | (100 + 120) / 2                              | 110.0  |
| 3   | 80    | (100 + 120 + 80) / 3                         | 100.0  |
| 4   | 150   | (100 + 120 + 80 + 150) / 4                   | 112.5  |
| 5   | 200   | (100 + 120 + 80 + 150 + 200) / 5             | 130.0  |
| 6   | 180   | (100 + 120 + 80 + 150 + 200 + 180) / 6       | 138.3  |
| 7   | 160   | (100 + 120 + 80 + 150 + 200 + 180 + 160) / 7 | 141.4  |

---

### ✅ Code Example:

```python
import pandas as pd

data = {'Day': [1,2,3,4,5,6,7],
        'Sales': [100, 120, 80, 150, 200, 180, 160]}
df = pd.DataFrame(data)

df['Cumulative_Avg'] = df['Sales'].expanding().mean()
print(df)
```

**Output:**

```
   Day  Sales  Cumulative_Avg
0    1    100     100.000000
1    2    120     110.000000
2    3     80     100.000000
3    4    150     112.500000
4    5    200     130.000000
5    6    180     138.333333
6    7    160     141.428571
```

---

## 🧮 2. EWMA (Exponentially Weighted Moving Average)

### 🧠 Simple Idea:

EWMA ka matlab hai —

> Recent (latest) data ko **zyada importance** dena
> Aur purane data ko **kam importance** dena.

Matlab rolling average me har point ka weight **equal** hota hai,
lekin EWMA me recent points ka **weight zyada** hota hai.

---

### 📊 Example Data:

| Day | Sales |
| --- | ----- |
| 1   | 100   |
| 2   | 120   |
| 3   | 80    |
| 4   | 150   |
| 5   | 200   |
| 6   | 180   |
| 7   | 160   |

---

### ⚙️ Formula ka simple sense:

```
New_EWMA = α * Current_Value + (1 - α) * Previous_EWMA
```

jaha `α` (alpha) hota hai **smoothing factor**
jo depend karta hai `span` par → `α = 2 / (span + 1)`

---

### ✅ Code Example

```python
df['EWMA'] = df['Sales'].ewm(span=3, adjust=False).mean()
print(df)
```

**Output (approx):**

```
   Day  Sales   EWMA
0    1    100  100.0
1    2    120  113.3
2    3     80   97.8
3    4    150  129.2
4    5    200  173.8
5    6    180  176.3
6    7    160  168.4
```

---

### 🔍 Compare Rolling vs Expanding vs EWMA

| Function             | Meaning                           | Example Use       |
| -------------------- | --------------------------------- | ----------------- |
| `rolling(3).mean()`  | Pichle 3 values ka moving average | Short-term trend  |
| `expanding().mean()` | Start se ab tak ka average        | Overall trend     |
| `ewm(span=3).mean()` | Recent values ko zyada weight     | Stock/price trend |

---

### 📘 Summary

| Concept       | Window Size          | Weight       | Result Type    |
| ------------- | -------------------- | ------------ | -------------- |
| **Rolling**   | Fixed (e.g., 3)      | Equal        | Moving         |
| **Expanding** | Expands each row tak | Equal        | Cumulative     |
| **EWMA**      | All rows             | Recent > Old | Smoothed Trend |

---


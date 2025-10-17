
---

## 🧠 **1. Window Function kya hota hai?**

Soch ke dekho — tumhare paas ek data hai jaise **daily sales**:

| Day | Sales |
| --- | ----- |
| 1   | 100   |
| 2   | 120   |
| 3   | 80    |
| 4   | 150   |
| 5   | 200   |
| 6   | 180   |
| 7   | 160   |

Ab agar tumhe **average sales** nikalni ho — to normally tum `df['Sales'].mean()` karoge.

👉 Lekin kya ho agar tumhe *har din ke liye pichle 3 din ki average* dekhni ho?

Usko bolte hain **moving average** (ya rolling average).
Aur isi tarah ke kaam ke liye Pandas me **window functions** hote hain.

---

## ⚙️ **2. Rolling Window kya karti hai?**

`rolling()` ek “window” (range) of rows banata hai.

Example:

```python
df['3_day_avg'] = df['Sales'].rolling(window=3).mean()
```

Matlab:

> Har row ke liye, us row ke peeche ke 3 rows ka **average** nikal do.

---

### 🧩 Step by Step Calculation:

| Day | Sales | 3-day average ka kaam        |
| --- | ----- | ---------------------------- |
| 1   | 100   | 3 din nahi hue → NaN         |
| 2   | 120   | 2 din hue → NaN              |
| 3   | 80    | (100 + 120 + 80)/3 = 100     |
| 4   | 150   | (120 + 80 + 150)/3 = 116.67  |
| 5   | 200   | (80 + 150 + 200)/3 = 143.33  |
| 6   | 180   | (150 + 200 + 180)/3 = 176.67 |
| 7   | 160   | (200 + 180 + 160)/3 = 180    |

---

### ✅ Final Output:

```python
import pandas as pd

data = {'Day': [1,2,3,4,5,6,7],
        'Sales': [100, 120, 80, 150, 200, 180, 160]}
df = pd.DataFrame(data)

df['3_day_avg'] = df['Sales'].rolling(window=3).mean()
print(df)
```

**Output:**

```
   Day  Sales   3_day_avg
0    1    100         NaN
1    2    120         NaN
2    3     80  100.000000
3    4    150  116.666667
4    5    200  143.333333
5    6    180  176.666667
6    7    160  180.000000
```

---

## 📘 **3. Window ka matlab simple me**

“Window” = har step pe kitne rows ko consider karna hai.

| Window Size | Matlab                                          |
| ----------- | ----------------------------------------------- |
| `window=2`  | 2 pichle rows ka average                        |
| `window=3`  | 3 pichle rows ka average                        |
| `window=7`  | 7 din ka moving average (useful in time series) |

---

## 📈 **4. Other Window Operations**

You can also use:

```python
.rolling(3).sum()     # moving total
.rolling(3).max()     # last 3 days ka max
.rolling(3).min()     # last 3 days ka min
.rolling(3).std()     # standard deviation
```

---

## 💡 In Short:

| Function            | Use                                    |
| ------------------- | -------------------------------------- |
| `rolling(window=n)` | Moving calculations over last `n` rows |
| `expanding()`       | From start till current row            |
| `cumsum()`          | Cumulative sum (total till now)        |

---

Agar chahe to mai ek **diagram** (chart) bna du jisme rolling window ka visual moving view dikhaye —
jaise sliding window step by step move ho rahi ho?

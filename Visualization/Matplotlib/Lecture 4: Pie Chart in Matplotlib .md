---

# 🎓 **Lecture 4: Pie Chart in Matplotlib**

---

## 📘 **1. What is a Pie Chart?**

A **Pie Chart** is a **circular graph** divided into slices that show how a **whole is divided into parts**.
Each slice’s size represents the **percentage** or **proportion** of that category.

💡 You can think of it like cutting a pizza — each slice shows its share of the total.

---

### 🧠 **When to Use a Pie Chart**

Use a **Pie Chart** when:

* You want to show **proportions or percentages**.
* The total represents **100% of something** (like budget, market share, or time spent).
* You have a small number of categories (3–7 is ideal).

---

## 🏢 **Real-Life Scenario: Company Expense Distribution**

Imagine a **startup company** wants to visualize how its **monthly budget** is spent across different departments:

* Marketing
* Operations
* Salaries
* Research & Development
* Miscellaneous

A **Pie Chart** is the perfect way to show this.

---

## 🧩 **2. Basic Pie Chart Example**

```python
import matplotlib.pyplot as plt

# Data
departments = ['Marketing', 'Operations', 'Salaries', 'R&D', 'Misc']
expenses = [20000, 15000, 30000, 10000, 5000]

# Create Pie Chart
plt.pie(expenses, labels=departments)

plt.title("Company Expense Distribution - October 2025")
plt.show()
```

✅ Output: A simple circular chart showing how much each department spends.

---

## 🎨 **3. Adding Percentages**

Use the **`autopct`** parameter to display percentage values.

```python
plt.pie(expenses, labels=departments, autopct='%1.1f%%')

plt.title("Company Expense Distribution (%)")
plt.show()
```

✅ Output: Each slice now shows the percentage of total expenses.

---

## ✳️ **4. Important Parameters in `plt.pie()`**

| Parameter      | Description                      | Example                            |
| -------------- | -------------------------------- | ---------------------------------- |
| `labels`       | Names of categories              | `labels=['A', 'B', 'C']`           |
| `colors`       | Custom slice colors              | `colors=['red', 'blue', 'green']`  |
| `autopct`      | Shows percentage format          | `autopct='%1.1f%%'`                |
| `startangle`   | Rotates the start of the chart   | `startangle=90`                    |
| `explode`      | Separates slices from the center | `explode=[0, 0.1, 0, 0, 0]`        |
| `shadow`       | Adds drop shadow effect          | `shadow=True`                      |
| `counterclock` | Draws slices clockwise or not    | `counterclock=False`               |
| `wedgeprops`   | Style properties for edges       | `wedgeprops={'edgecolor':'black'}` |

---

## 🌈 **5. Stylish Example with Customization**

```python
colors = ['#FF9999', '#66B3FF', '#99FF99', '#FFCC99', '#FFD700']
explode = [0.05, 0.05, 0.05, 0.05, 0.05]

plt.pie(expenses,
        labels=departments,
        autopct='%1.1f%%',
        startangle=90,
        explode=explode,
        colors=colors,
        shadow=True,
        wedgeprops={'edgecolor':'black', 'linewidth':1})

plt.title("Company Expense Breakdown - October 2025", fontsize=14, fontweight='bold')
plt.show()
```

✅ Output: A colorful, professional pie chart with exploded slices and percentage labels.

---

## 📊 **6. Highlighting a Specific Slice**

You can **“pull out”** one slice to highlight it — useful for emphasizing one category.

```python
explode = [0, 0, 0.1, 0, 0]  # Highlight the 'Salaries' slice

plt.pie(expenses, labels=departments, autopct='%1.1f%%',
        explode=explode, shadow=True, startangle=90, colors=colors)

plt.title("Highlighting Salaries in Company Expenses")
plt.show()
```

✅ Output: The "Salaries" slice pops out, drawing focus.

---

## 📈 **7. Adding Legends**

You can add a legend for better understanding.

```python
plt.pie(expenses, labels=departments, autopct='%1.1f%%', startangle=90, colors=colors)
plt.title("Company Expense Distribution")
plt.legend(title="Departments", loc="upper left", bbox_to_anchor=(1, 1))
plt.show()
```

✅ Output: A pie chart with a clean legend box on the side.

---

## ⚙️ **8. Creating a Donut Chart (Pie with Hole)**

A **donut chart** is just a pie chart with a circle in the middle.

```python
plt.pie(expenses, labels=departments, autopct='%1.1f%%', startangle=90, colors=colors, wedgeprops={'width':0.4})
plt.title("Company Expense Distribution - Donut Style")
plt.show()
```

✅ Output: A donut-style pie chart (modern and compact).

---

## 🧠 **9. Combine Multiple Pie Charts**

Compare **two months’ expenses** side-by-side.

```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(1, 2, figsize=(10,5))

departments = ['Marketing', 'Operations', 'Salaries', 'R&D', 'Misc']
sept_exp = [18000, 12000, 25000, 9000, 4000]
oct_exp = [20000, 15000, 30000, 10000, 5000]

colors = ['#FF9999', '#66B3FF', '#99FF99', '#FFCC99', '#FFD700']

ax[0].pie(sept_exp, labels=departments, autopct='%1.1f%%', startangle=90, colors=colors)
ax[0].set_title("September 2025")

ax[1].pie(oct_exp, labels=departments, autopct='%1.1f%%', startangle=90, colors=colors)
ax[1].set_title("October 2025")

plt.suptitle("Monthly Expense Comparison", fontsize=15, fontweight='bold')
plt.show()
```

✅ Output: Two pie charts comparing expenses for two different months.

---

## 🧮 **10. Real-Life Scenario #2: Smartphone Market Share**

Let’s visualize how smartphone brands share the market.

```python
brands = ['Apple', 'Samsung', 'Xiaomi', 'OnePlus', 'Others']
market_share = [30, 25, 20, 15, 10]

plt.figure(figsize=(7,7))
plt.pie(market_share, labels=brands, autopct='%1.1f%%', startangle=140, colors=plt.cm.Pastel1.colors, shadow=True)
plt.title("Global Smartphone Market Share - 2025", fontsize=14, fontweight='bold')
plt.show()
```

✅ Output: A pie chart showing percentage share of each smartphone brand.

---

## 🧾 **11. Summary Table**

| Concept         | Description                        |
| --------------- | ---------------------------------- |
| `plt.pie()`     | Creates a pie chart                |
| `autopct`       | Adds percentage labels             |
| `startangle`    | Rotates the starting angle         |
| `explode`       | Pulls out slices                   |
| `colors`        | Adds custom or gradient colors     |
| `shadow`        | Adds shadow effect                 |
| `wedgeprops`    | Customize edges or add donut style |
| `plt.legend()`  | Adds legend                        |
| `plt.cm.<name>` | Uses color maps for auto colors    |

---

## 💡 **12. When to Avoid Pie Charts**

❌ When you have too many categories (10+ slices).
❌ When differences between values are very small (bars show better comparison).
✅ Use **Bar Charts** for comparing exact values instead.

---

## 🧠 **13. Practice Task**

1. Create a pie chart showing **time spent in a day** — Sleep, Work, Exercise, Entertainment, Others.
2. Add percentages and a title.
3. Highlight your most time-consuming activity using **explode**.
4. Try converting it to a **Donut Chart** version.

---


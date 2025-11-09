
---

# 🎓 **Lecture 3: Bar Plot in Matplotlib**

---

## 📘 **1. What is a Bar Plot?**

A **Bar Plot (Bar Chart)** is used to compare **quantities of different categories**.
Each bar’s **height or length** shows the value of that category.

💡 Think of it as a visual way to **compare things side by side**.

---

### 🏪 **Real-Life Scenario: Supermarket Sales**

Imagine you manage a **supermarket**.
You want to analyze **which product category** (like Fruits, Snacks, Dairy, Beverages, etc.) earned the most sales last month.

A **bar chart** will instantly show you which category performed best.

---

## 🧩 **2. Basic Bar Plot Example**

```python
import matplotlib.pyplot as plt

# Data
categories = ['Fruits', 'Snacks', 'Dairy', 'Beverages', 'Bakery']
sales = [25000, 18000, 15000, 22000, 12000]

# Create Bar Plot
plt.bar(categories, sales)

# Labels and Title
plt.title("Supermarket Sales by Category - October 2025")
plt.xlabel("Product Category")
plt.ylabel("Sales (₹)")
plt.show()
```

✅ Output: Simple vertical bars showing sales for each product category.

---

## 🎨 **3. Customizing the Bar Plot**

You can customize the bar color, width, transparency, and border to make it more professional.

| Property    | Description          | Example             |
| ----------- | -------------------- | ------------------- |
| `color`     | Fill color of bars   | `color='orange'`    |
| `edgecolor` | Border color of bars | `edgecolor='black'` |
| `linewidth` | Border thickness     | `linewidth=2`       |
| `alpha`     | Transparency (0–1)   | `alpha=0.8`         |
| `width`     | Bar width            | `width=0.6`         |

---

### ✳️ **Example: Stylish Bar Chart**

```python
plt.bar(categories, sales, 
        color=['#FF7F50', '#FFD700', '#6A5ACD', '#00CED1', '#FF69B4'],
        edgecolor='black', linewidth=1.5, alpha=0.9)

plt.title("Supermarket Sales by Category", fontsize=14, fontweight='bold')
plt.xlabel("Category", fontsize=12)
plt.ylabel("Sales (in ₹)", fontsize=12)
plt.grid(axis='y', linestyle='--', alpha=0.5)

plt.show()
```

✅ Output: Colorful, visually appealing bar chart with light grid lines.

---

## 📈 **4. Adding Value Labels**

Let’s add the actual sales numbers on top of each bar.

```python
bars = plt.bar(categories, sales, color='lightgreen', edgecolor='black')

plt.title("Supermarket Sales by Category")
plt.xlabel("Category")
plt.ylabel("Sales (₹)")

# Adding value labels
for bar in bars:
    yval = bar.get_height()
    plt.text(bar.get_x() + bar.get_width()/2, yval + 500, f"₹{yval}", 
             ha='center', fontsize=10, color='black')

plt.grid(axis='y', linestyle=':')
plt.show()
```

✅ Output: Each bar has a label displaying its sales value.

---

## 🧮 **5. Horizontal Bar Plot**

When category names are long, a **horizontal bar chart** improves readability.

```python
plt.barh(categories, sales, color='skyblue', edgecolor='black')
plt.title("Supermarket Sales by Category (Horizontal View)")
plt.xlabel("Sales (₹)")
plt.ylabel("Category")
plt.grid(axis='x', linestyle='--', alpha=0.6)
plt.show()
```

✅ Output: Easy-to-read horizontal layout.

---

## 🧱 **6. Multiple Bar Charts (Comparison)**

Now you want to compare **sales of two months** — September vs October.

```python
import numpy as np

categories = ['Fruits', 'Snacks', 'Dairy', 'Beverages', 'Bakery']
sept_sales = [20000, 15000, 13000, 19000, 10000]
oct_sales = [25000, 18000, 15000, 22000, 12000]

x = np.arange(len(categories))
width = 0.35

plt.bar(x - width/2, sept_sales, width, label='September', color='lightcoral')
plt.bar(x + width/2, oct_sales, width, label='October', color='lightseagreen')

plt.title("Supermarket Sales Comparison: Sep vs Oct 2025", fontsize=14)
plt.xlabel("Category")
plt.ylabel("Sales (₹)")
plt.xticks(x, categories)
plt.legend()
plt.grid(axis='y', linestyle=':')
plt.show()
```

✅ Output: Two bars per category showing growth or decline.

---

## 🧠 **7. Highlighting the Highest Sales Category**

You can highlight or annotate specific bars for storytelling.

```python
plt.bar(categories, sales, color='cornflowerblue', edgecolor='black')

plt.title("Supermarket Sales by Category")
plt.xlabel("Category")
plt.ylabel("Sales (₹)")

# Highlight highest bar
max_val = max(sales)
max_cat = categories[sales.index(max_val)]

plt.annotate(f'Highest: ₹{max_val}',
             xy=(max_cat, max_val),
             xytext=('Dairy', max_val + 4000),
             arrowprops=dict(facecolor='red', shrink=0.05),
             fontsize=11, color='red')

plt.grid(axis='y', linestyle='--', alpha=0.6)
plt.show()
```

✅ Output: Arrow pointing at the top-performing product category.

---

## 🌈 **8. Using Colormaps (Automatic Color Gradient)**

Instead of choosing colors manually, you can use Matplotlib’s **colormaps** for gradients.

```python
import numpy as np

colors = plt.cm.viridis(np.linspace(0.2, 0.8, len(categories)))
plt.bar(categories, sales, color=colors, edgecolor='black')

plt.title("Supermarket Sales (Colormap Example)")
plt.xlabel("Category")
plt.ylabel("Sales (₹)")
plt.show()
```

✅ Output: A gradient-style color palette.

---

## ⚙️ **9. Figure Size and Layout**

```python
plt.figure(figsize=(9,6))
plt.bar(categories, sales, color='salmon')
plt.tight_layout()
plt.show()
```

✅ Ensures proper spacing and readable labels.

---

## 🧾 **10. Summary**

| Concept                   | Description                  |
| ------------------------- | ---------------------------- |
| `plt.bar()`               | Creates vertical bar chart   |
| `plt.barh()`              | Creates horizontal bar chart |
| `color`, `width`, `alpha` | Change appearance            |
| `plt.text()`              | Adds values on bars          |
| `plt.legend()`            | Adds comparison labels       |
| `plt.grid()`              | Adds gridlines               |
| `plt.annotate()`          | Highlights points            |
| `plt.cm.<colormap>`       | Adds color gradients         |

---

## 💼 **11. Real-Life Insight**

Bar plots are commonly used in:

* 📊 Sales and profit comparison
* 👩‍🏫 Student performance by subject
* 💰 Expense tracking by category
* 🌍 Population or employment distribution
* 🏢 Employee performance analysis

---

## 🧠 **12. Practice Task**

1. Create a bar chart showing **monthly electricity consumption (in kWh)** for your home.
2. Add value labels on bars.
3. Compare two months (like June vs July).
4. Highlight the month with **highest usage** using `plt.annotate()`.

---

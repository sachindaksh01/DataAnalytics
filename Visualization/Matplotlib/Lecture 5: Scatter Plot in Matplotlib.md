
---

# 🎓 **Lecture 5: Scatter Plot in Matplotlib**

---

## 📘 **1. What is a Scatter Plot?**

A **Scatter Plot** shows the **relationship between two numerical variables**.
Each point on the chart represents a pair of values — one on the X-axis and one on the Y-axis.

💡 Think of it as a “dot map” of data — showing how things move together (or not).

---

### 🧠 **When to Use a Scatter Plot**

✅ When you want to visualize **correlation** (relationship) between two variables.
✅ When you want to detect **patterns, clusters, or outliers** in data.
✅ Commonly used in **data analytics, marketing, sales, and science**.

---

## 💼 **Real-Life Scenario: Advertising vs Sales**

A **marketing manager** wants to know if **spending more on advertising** leads to **higher sales**.

The manager records the **amount spent on ads (in ₹)** and **monthly sales** for 8 months.

Let’s visualize it with a scatter plot.

---

## 🧩 **2. Basic Scatter Plot Example**

```python
import matplotlib.pyplot as plt

# Data
ad_spend = [10, 15, 20, 25, 30, 35, 40, 45]   # Advertising spend (in thousands)
sales = [25, 30, 35, 40, 48, 50, 60, 65]       # Sales (in thousands)

# Create Scatter Plot
plt.scatter(ad_spend, sales)

plt.title("Advertising Spend vs Sales (Scatter Plot)")
plt.xlabel("Advertising Spend (₹ in thousands)")
plt.ylabel("Sales (₹ in thousands)")
plt.show()
```

✅ Output: Each dot shows one month’s ad spend and sales.

---

## 🎯 **3. What Does It Show?**

You’ll notice:

* As **advertising spend increases**, **sales also increase**.
  ➡️ This indicates a **positive correlation**.

---

## 🎨 **4. Customizing Scatter Plots**

You can customize dots using several parameters.

| Parameter   | Description          | Example                           |
| ----------- | -------------------- | --------------------------------- |
| `color`     | Dot color            | `color='red'`                     |
| `s`         | Dot size             | `s=100`                           |
| `alpha`     | Transparency (0–1)   | `alpha=0.6`                       |
| `marker`    | Shape of dots        | `'o'`, `'^'`, `'s'`, `'x'`, `'p'` |
| `edgecolor` | Border color of dots | `edgecolor='black'`               |

---

### ✳️ **Example: Customized Scatter Plot**

```python
plt.scatter(ad_spend, sales, 
            color='orange', 
            s=120, 
            alpha=0.8, 
            edgecolor='black', 
            marker='o')

plt.title("Advertising Spend vs Sales", fontsize=14, fontweight='bold')
plt.xlabel("Ad Spend (₹ in thousands)", fontsize=12)
plt.ylabel("Sales (₹ in thousands)", fontsize=12)
plt.grid(True, linestyle='--', alpha=0.6)
plt.show()
```

✅ Output: A clean and colorful scatter plot with visible gridlines.

---

## 🧮 **5. Using Multiple Scatter Series**

Let’s say the company runs ads on **two different platforms** — **TV** and **Social Media** — and wants to compare their impact.

```python
tv_spend = [10, 15, 20, 25, 30]
tv_sales = [25, 28, 35, 40, 45]

social_spend = [10, 20, 30, 40, 50]
social_sales = [20, 30, 50, 65, 80]

plt.scatter(tv_spend, tv_sales, color='blue', label='TV Ads', s=100, alpha=0.8)
plt.scatter(social_spend, social_sales, color='green', label='Social Media Ads', s=100, alpha=0.8)

plt.title("TV vs Social Media Advertising Impact")
plt.xlabel("Ad Spend (₹ in thousands)")
plt.ylabel("Sales (₹ in thousands)")
plt.legend()
plt.grid(True)
plt.show()
```

✅ Output: Two sets of points showing two different advertising channels.

---

## 📈 **6. Adding Color Mapping (cmap)**

You can use a **color gradient** to represent a third variable (e.g., number of customers).

```python
import numpy as np

ad_spend = np.array([10, 15, 20, 25, 30, 35, 40])
sales = np.array([25, 30, 35, 45, 48, 55, 60])
customers = np.array([50, 60, 70, 90, 100, 120, 130])  # third variable

plt.scatter(ad_spend, sales, c=customers, cmap='viridis', s=150, alpha=0.9, edgecolor='black')
plt.colorbar(label='Number of Customers')
plt.title("Sales vs Ad Spend (Color = Customers)")
plt.xlabel("Ad Spend (₹ in thousands)")
plt.ylabel("Sales (₹ in thousands)")
plt.grid(True, linestyle='--', alpha=0.6)
plt.show()
```

✅ Output: A scatter plot with color intensity showing customer count.

---

## 🧠 **7. Detecting Correlations**

You can visually detect:

* **Positive correlation** → dots go upward (e.g., spend ↑ = sales ↑)
* **Negative correlation** → dots go downward
* **No correlation** → dots scattered randomly

👉 Scatter plots are very useful in **data analysis & regression modeling**.

---

## 🧩 **8. Adding Trend Line (Optional)**

To better see the trend, we can fit a **regression line** using `numpy.polyfit`.

```python
import numpy as np

x = np.array(ad_spend)
y = np.array(sales)

# Fit line (y = mx + c)
m, c = np.polyfit(x, y, 1)
plt.scatter(x, y, color='orange', s=100, edgecolor='black')
plt.plot(x, m*x + c, color='red', linewidth=2, label='Trend Line')

plt.title("Ad Spend vs Sales with Trend Line")
plt.xlabel("Ad Spend (₹ in thousands)")
plt.ylabel("Sales (₹ in thousands)")
plt.legend()
plt.grid(True)
plt.show()
```

✅ Output: Scatter points with a red line showing the trend — clear visual correlation.

---

## 📊 **9. Real-Life Scenario #2: Student Study Hours vs Exam Marks**

Let’s visualize how **study hours** affect **exam scores**.

```python
hours = [2, 3, 4, 5, 6, 7, 8]
marks = [40, 45, 55, 60, 65, 75, 85]

plt.scatter(hours, marks, color='purple', s=120, alpha=0.8, edgecolor='black')

plt.title("Study Hours vs Exam Marks")
plt.xlabel("Study Hours per Day")
plt.ylabel("Marks Scored (%)")
plt.grid(True, linestyle='--', alpha=0.6)
plt.show()
```

✅ Output: You’ll notice — as students study more hours, their scores go up.

---

## ⚙️ **10. Figure Settings**

```python
plt.figure(figsize=(8,5))
plt.scatter(ad_spend, sales, color='red', s=100, alpha=0.7)
plt.tight_layout()
plt.show()
```

✅ Makes sure chart fits well, even with long labels.

---

## 🧾 **11. Summary**

| Concept                  | Description                       |
| ------------------------ | --------------------------------- |
| `plt.scatter(x, y)`      | Creates a scatter plot            |
| `color`, `s`, `alpha`    | Customize appearance              |
| `cmap`                   | Adds color mapping (3rd variable) |
| `plt.legend()`           | Adds category labels              |
| `plt.grid()`             | Adds background grid              |
| `plt.colorbar()`         | Adds color scale                  |
| `np.polyfit()`           | Fits a trend/regression line      |
| `plt.figure(figsize=())` | Adjusts chart size                |

---

## 💡 **12. Real-World Uses**

Scatter plots are used in:

* 📈 Marketing: Ad spend vs sales
* 🎓 Education: Study hours vs performance
* 💰 Finance: Risk vs return
* 🧬 Science: Temperature vs growth rate
* 👨‍💻 Data science: Feature relationships

---

## 🧠 **13. Practice Task**

1. Create a scatter plot showing **age vs income** for 10 people.
2. Use different marker styles and colors.
3. Add a trend line.
4. Try a color gradient (`cmap`) based on **education level or experience**.

---

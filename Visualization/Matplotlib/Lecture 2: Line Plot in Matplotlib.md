
---

# 🎓 **Lecture 2: Line Plot in Matplotlib**

---

## 📘 **1. What is a Line Plot?**

A **line plot** is used to display **data trends over time** or **continuous data**.
It connects individual data points with a line — helping you visualize **patterns, growth, or decline**.

---

### 📊 **Example (Real-Life Scenario)**

Imagine you run an **online course platform** (like Dream Topper 🎯).
You record the **number of new student enrollments every month**.

You want to see **how enrollment changes month by month**.
A **line plot** is perfect for this.

---

## 🧩 **2. Basic Example**

```python
import matplotlib.pyplot as plt

# Data
months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun']
enrollments = [50, 70, 90, 120, 150, 200]

# Plot
plt.plot(months, enrollments)

# Labels and Title
plt.title("Monthly Student Enrollments - Dream Topper")
plt.xlabel("Month")
plt.ylabel("Number of Students")

plt.show()
```

✅ Output: A simple line showing how students increased from January to June.

---

## 🎨 **3. Customizing the Line Plot**

Matplotlib gives you full control over how your line looks — color, style, markers, etc.

---

### ✳️ **Line Customization Parameters**

| Property          | Description            | Example                                        |
| ----------------- | ---------------------- | ---------------------------------------------- |
| `color`           | Changes the line color | `color='red'` or `color='#00FF00'`             |
| `linestyle`       | Changes line style     | `'-'` (solid), `'--'` (dashed), `':'` (dotted) |
| `linewidth`       | Changes line thickness | `linewidth=2`                                  |
| `marker`          | Adds points on data    | `'o'`, `'s'`, `'^'` etc.                       |
| `markersize`      | Controls marker size   | `markersize=8`                                 |
| `markerfacecolor` | Fills marker color     | `markerfacecolor='blue'`                       |
| `markeredgecolor` | Marker border color    | `markeredgecolor='black'`                      |

---

### 🧠 **Example: Customized Line Plot**

```python
plt.plot(months, enrollments,
         color='green',
         linestyle='--',
         linewidth=3,
         marker='o',
         markersize=8,
         markerfacecolor='yellow',
         markeredgecolor='black')

plt.title("Dream Topper: Monthly Enrollments", fontsize=14, fontweight='bold')
plt.xlabel("Month", fontsize=12)
plt.ylabel("Students Enrolled", fontsize=12)
plt.grid(True, linestyle=':', alpha=0.6)
plt.show()
```

✅ Output: A stylish green dashed line with circle markers — looks professional and readable.

---

## 📈 **4. Adding Multiple Lines (Comparative Analysis)**

Let’s say Dream Topper runs **two centers** — Meerut and Modipuram.
We can compare both in one chart.

```python
months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun']
meerut = [50, 70, 90, 120, 150, 200]
modipuram = [40, 60, 80, 110, 130, 170]

plt.plot(months, meerut, color='blue', marker='o', label='Meerut Center')
plt.plot(months, modipuram, color='orange', marker='s', label='Modipuram Center')

plt.title("Monthly Enrollments Comparison")
plt.xlabel("Month")
plt.ylabel("Number of Students")
plt.legend()
plt.grid(True)
plt.show()
```

✅ Output: Two lines — one for each center — with a legend for clarity.

---

## 🧮 **5. Adding Annotations**

You can mark special points on the chart.

```python
plt.plot(months, enrollments, marker='o', color='teal')

plt.title("Monthly Student Enrollments")
plt.xlabel("Month")
plt.ylabel("Number of Students")

# Highlight max value
max_value = max(enrollments)
max_index = enrollments.index(max_value)
plt.annotate(f'Peak: {max_value}',
             xy=(months[max_index], max_value),
             xytext=(months[max_index], max_value+10),
             arrowprops=dict(facecolor='red', shrink=0.05),
             fontsize=10, color='red')

plt.grid(True)
plt.show()
```

✅ Output: Adds an arrow showing the month with the highest enrollment.

---

## 🎚️ **6. Figure Size and Layout**

You can control the overall figure size and layout spacing.

```python
plt.figure(figsize=(8,5))
plt.plot(months, enrollments, color='purple', marker='o')
plt.title("Enrollment Trend", fontsize=14)
plt.tight_layout()
plt.show()
```

---

## 🌈 **7. Line Styles and Markers List**

```python
# Line styles: '-', '--', '-.', ':'
# Markers: 'o', 's', '^', 'D', '*', 'p', 'h', 'x'
```

You can even use short notation:

```python
plt.plot(x, y, 'r--o')   # red dashed line with circle markers
```

Here:

* `r` → red
* `--` → dashed line
* `o` → circle marker

---

## 💼 **8. Real-Life Scenario: Sales Growth Tracking**

Let’s visualize a **small business** tracking monthly sales.

```python
months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul']
sales = [12000, 15000, 18000, 22000, 21000, 25000, 30000]

plt.figure(figsize=(9,5))
plt.plot(months, sales, color='blue', marker='^', linestyle='-', linewidth=2)

plt.title("Dream Topper - Monthly Sales Trend (₹)", fontsize=14, fontweight='bold')
plt.xlabel("Month")
plt.ylabel("Sales (in ₹)")
plt.grid(True, linestyle='--', alpha=0.7)

# Highlight growth
plt.annotate('Festival Season Boost',
             xy=('May', 21000), xytext=('Mar', 26000),
             arrowprops=dict(facecolor='green', shrink=0.05),
             fontsize=11, color='darkgreen')

plt.show()
```

✅ Output: A beautiful, storytelling chart showing sales growth with annotation.

---

## 🧾 **9. Summary**

| Concept                        | Description                 |
| ------------------------------ | --------------------------- |
| `plt.plot()`                   | Creates a line plot         |
| `color`, `linestyle`, `marker` | Customize look              |
| `plt.legend()`                 | Adds label box              |
| `plt.grid()`                   | Adds background grid        |
| `plt.figure(figsize=())`       | Adjusts figure size         |
| `plt.annotate()`               | Highlights important points |
| `plt.show()`                   | Displays the plot           |

---

## 🧠 **10. Practice Task**

1. Create a line plot showing **your center’s monthly revenue**.
2. Use custom colors, markers, and grid.
3. Highlight the month with **maximum revenue** using `plt.annotate()`.

---

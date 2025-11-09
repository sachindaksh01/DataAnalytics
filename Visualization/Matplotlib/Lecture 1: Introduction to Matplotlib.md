---

# 🎓 **Lecture 1: Introduction to Matplotlib**

---

## 📘 **1. What is Matplotlib?**

**Matplotlib** is a **Python library** used to create **data visualizations** — like graphs, charts, and plots — so that we can easily understand data patterns.

It’s one of the most powerful and widely used visualization tools in Python.

💡 Think of it like a “painting tool” for data — it helps you **see** your numbers.

---

### ✨ **Why We Use Matplotlib**

✅ Easy to use and beginner-friendly
✅ Works well with **NumPy** and **Pandas**
✅ Supports 2D and 3D plotting
✅ Fully customizable — you can change color, size, labels, etc.
✅ Used in **Data Analytics, Machine Learning, and Reports**

---

## 🎯 **2. Static vs Interactive Plots**

Matplotlib can generate **two types of plots**:

| Type                 | Description                                                                | Example                               |
| -------------------- | -------------------------------------------------------------------------- | ------------------------------------- |
| **Static Plot**      | A simple image that doesn’t change. Common in reports or PDFs.             | `plt.savefig('chart.png')`            |
| **Interactive Plot** | Allows zooming, panning, hovering, etc. Usually seen in notebooks or apps. | Jupyter Notebook / Matplotlib widgets |

📌 Example:
In **Jupyter Notebook**, you can make your plots interactive by adding this magic command:

```python
%matplotlib inline
```

or for full interaction:

```python
%matplotlib notebook
```

---

## 🐍 **3. Importing Matplotlib**

Before you can use it, you must **import the library**.

```python
import matplotlib.pyplot as plt
```

Here:

* `matplotlib` → is the main library
* `pyplot` → is a module that helps you make plots easily
* `plt` → is a short name (alias) used for convenience

---

## 🧩 **4. Basic Example**

Let’s make our first line chart 👇

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [10, 20, 25, 30, 40]

plt.plot(x, y)
plt.xlabel("X-Axis")
plt.ylabel("Y-Axis")
plt.title("My First Line Plot")
plt.show()
```

✅ Output: A simple line graph with labels and a title.

---

## 🎨 **5. Structure of a Matplotlib Plot**

Every Matplotlib plot has these parts:

| Part                | Description                                      |
| ------------------- | ------------------------------------------------ |
| **Figure**          | The entire window or page where the plot appears |
| **Axes**            | The area where data is plotted                   |
| **X-axis & Y-axis** | The horizontal and vertical lines                |
| **Labels**          | Text that describes axes                         |
| **Title**           | The heading of the plot                          |

Example:

```python
plt.figure(figsize=(6,4))  # Controls overall size
plt.plot(x, y, color='red', linestyle='--', marker='o')
plt.xlabel("Days")
plt.ylabel("Sales")
plt.title("Sales Growth Over Days")
plt.grid(True)
plt.show()
```

---

## ⚙️ **6. Saving Your Plot**

You can also save the plot to a file:

```python
plt.savefig("myplot.png")
```

You can save in formats like `.png`, `.jpg`, `.pdf`, etc.

---

## 🧠 **7. Summary**

| Concept              | Description                                       |
| -------------------- | ------------------------------------------------- |
| Matplotlib           | Python library for data visualization             |
| pyplot               | Module that provides plotting functions           |
| plt                  | Common alias for pyplot                           |
| Static plot          | Simple non-interactive graph                      |
| Interactive plot     | Allows zoom, hover, etc.                          |
| `%matplotlib inline` | Used in Jupyter to show plots inside the notebook |

---

## ✅ **Practice Task**

Create a line plot showing the number of students enrolled per month:

```python
months = ['Jan', 'Feb', 'Mar', 'Apr', 'May']
students = [30, 45, 60, 80, 100]

plt.plot(months, students, color='green', marker='s')
plt.title("Student Enrollment Growth")
plt.xlabel("Month")
plt.ylabel("Number of Students")
plt.show()
```

---

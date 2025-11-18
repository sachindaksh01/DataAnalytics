
# 🎓 Lecture: Matplotlib — Customization, Multiple Plots, Save & Export

This lecture teaches how to **make publication-ready Matplotlib figures**: titles, labels, legends, gridlines, ticks, colors, markers, linestyles, figure size & DPI, arranging multiple plots with `plt.subplot()` and `plt.subplots()`, and saving/exporting to files (PNG/JPG/PDF) with good quality.

---

## 1️⃣ Overview & real-life scenario

**Scenario:** You are a data analyst at a retail chain. You need to produce a presentation slide that shows:

* Monthly sales (line plot),
* Category-wise revenue (bar plot),
* Distribution of order values (histogram).

You must put these three plots on one slide (clean, readable), annotate important points, and export a high-resolution PNG and a PDF for print.

We’ll build that step-by-step.

---

## 2️⃣ Customization (titles, labels, legends, gridlines, ticks, colors, markers, linestyle, figsize, dpi)

### Titles & labels

* `plt.title("Title", fontsize=14, fontweight='bold')`
* `plt.xlabel("X label", fontsize=12)`
* `plt.ylabel("Y label", fontsize=12)`

**Tip:** Use `fontsize` and `fontweight` for slide-friendly readability.

### Legends

* Add `label=` for plot calls and `plt.legend()` to show them.
* Control location: `plt.legend(loc='upper left')` or `loc='best'`.
* Use `bbox_to_anchor` for precise placement.

### Gridlines

* `plt.grid(True)` toggles a grid.
* Style: `plt.grid(axis='y', linestyle='--', alpha=0.6)`

### Ticks

* Set tick positions: `plt.xticks([0,1,2], ['Jan','Feb','Mar'])`
* Rotate labels: `plt.xticks(rotation=45)`
* Format large numbers: use `matplotlib.ticker` (example below)

```python
from matplotlib.ticker import FuncFormatter
ax.yaxis.set_major_formatter(FuncFormatter(lambda x, pos: f"₹{int(x/1000)}k"))
```

### Colors, markers, linestyle

* Colors: name (`'blue'`), hex (`'#FF5733'`), or colormaps (`plt.cm.viridis`).
* Markers: `'o', 's', '^', 'x'`
* Linestyles: `'-', '--', '-.', ':'`
* Combined short form: `'r--o'` → red dashed line with circle markers.

### Figure size & DPI

* `plt.figure(figsize=(8,5), dpi=150)` — larger figsize & dpi for high-res export.
* `fig, ax = plt.subplots(figsize=(10,6), dpi=200)` — recommended for precise control.

---

## 3️⃣ Multiple plots — `plt.subplot()` vs `plt.subplots()`

### `plt.subplot()` (stateful)

* Useful for quick small plots.

```python
plt.figure(figsize=(10,4))
plt.subplot(1,3,1)   # rows, cols, index
plt.plot(...)
plt.title("A")
plt.subplot(1,3,2)
plt.bar(...)
plt.title("B")
plt.subplot(1,3,3)
plt.hist(...)
plt.title("C")
plt.tight_layout()
plt.show()
```

**Works**, but can get messy when customizing each axis heavily.

### `plt.subplots()` (recommended)

* Returns `(fig, axes)` — easy to iterate, more pythonic & clearer.

```python
fig, axes = plt.subplots(1, 3, figsize=(15,5), dpi=150)

# Line plot on axes[0]
axes[0].plot(months, sales, color='tab:blue', marker='o', linestyle='-',
             linewidth=2, markersize=6, label='Sales')
axes[0].set_title("Monthly Sales", fontsize=12)
axes[0].set_xlabel("Month")
axes[0].set_ylabel("Sales (₹)")
axes[0].legend()
axes[0].grid(axis='y', linestyle='--', alpha=0.5)

# Bar plot on axes[1]
axes[1].bar(categories, revenue, color='tab:orange', edgecolor='black')
axes[1].set_title("Category Revenue")
axes[1].tick_params(axis='x', rotation=30)
axes[1].grid(axis='y', linestyle='--', alpha=0.5)

# Histogram on axes[2]
axes[2].hist(order_values, bins=30, color='tab:green', edgecolor='black', alpha=0.7)
axes[2].set_title("Order Value Distribution")
axes[2].set_xlabel("Order value (₹)")
axes[2].grid(axis='y', linestyle=':', alpha=0.5)

plt.tight_layout()
plt.show()
```

**Advantages of `subplots()`**

* Control each axes independently (`axes[i]`).
* Easier to set shared axes (`sharex=True`, `sharey=True`).
* Better integration with `fig` for annotations, suptitle, and saving.

---

## 4️⃣ Advanced formatting examples & goodies

### Formatting y-axis as currency (thousands)

```python
import matplotlib.ticker as mtick
ax.yaxis.set_major_formatter(mtick.StrMethodFormatter('₹{x:,.0f}'))
```

### Adding annotations & arrows

```python
ax.annotate("Peak sales",
            xy=(peak_month_index, peak_value),
            xytext=(peak_month_index-1, peak_value*1.15),
            arrowprops=dict(facecolor='black', arrowstyle='->'),
            fontsize=10)
```

### Marking subplots’ shared title

```python
fig.suptitle("Retail Dashboard — October 2025", fontsize=16, fontweight='bold')
```

### Custom legend outside plot

```python
axes[0].legend(loc='upper left', bbox_to_anchor=(1.02, 1), borderaxespad=0)
plt.subplots_adjust(right=0.8)  # leave space for legend
```

---

## 5️⃣ Save & Export (`plt.savefig` and file options)

### Basic saving

```python
plt.savefig("dashboard.png")
```

### Recommended saving parameters for publication/print

* `dpi` — higher value gives better resolution (150–300).
* `bbox_inches='tight'` — crops white margins.
* `transparent=True` — useful for overlays.
* `facecolor` — set if not transparent.

```python
plt.savefig("dashboard.png", dpi=300, bbox_inches='tight')
plt.savefig("dashboard.pdf", dpi=300, bbox_inches='tight')  # vector-friendly (PDF)
```

### File types & when to use

* **PNG/JPG** — raster images; PNG preserves transparency and sharp lines (use for presentations and web).
* **PDF / SVG / EPS** — vector formats; best for print and scaling without loss (use for reports or slides where resizing might happen).
* **JPG** — lossy, avoid for plots with text or where clarity matters.

### Save an entire `fig` from `subplots()` style

```python
fig.savefig("retail_dashboard.png", dpi=300, bbox_inches='tight')
fig.savefig("retail_dashboard.pdf", bbox_inches='tight')  # PDF vector
```

**Important:** call `savefig` *before* `plt.show()` in some backends to avoid blank outputs.

---

## 6️⃣ Full worked example (complete pipeline — simulate data, style, subplot, save)

```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.ticker as mtick

# Simulated data (retail example)
months = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct']
sales = np.array([120000, 135000, 128000, 140000, 150500, 160000, 155000, 170000, 165000, 180000])
categories = ['Grocery','Electronics','Clothing','Home','Beauty']
revenue = np.array([500000, 300000, 250000, 180000, 90000])
order_values = np.random.gamma(shape=2.0, scale=50, size=2000) * 100  # skewed order value

fig, axes = plt.subplots(1, 3, figsize=(18,5), dpi=150)

# Line plot: Monthly sales
axes[0].plot(months, sales, color='#1f77b4', marker='o', linestyle='-', linewidth=2, markersize=7, label='Sales')
axes[0].set_title("Monthly Sales", fontsize=12, fontweight='bold')
axes[0].set_xlabel("Month")
axes[0].set_ylabel("Sales (₹)")
axes[0].yaxis.set_major_formatter(mtick.StrMethodFormatter('₹{x:,.0f}'))
axes[0].grid(axis='y', linestyle='--', alpha=0.5)
axes[0].legend(loc='upper left')

# Bar plot: category revenue
bars = axes[1].bar(categories, revenue, color=plt.cm.Pastel1(np.linspace(0,1,len(categories))),
                   edgecolor='black')
axes[1].set_title("Revenue by Category")
axes[1].set_ylabel("Revenue (₹)")
axes[1].yaxis.set_major_formatter(mtick.StrMethodFormatter('₹{x:,.0f}'))
axes[1].tick_params(axis='x', rotation=25)
# Add value labels
for bar in bars:
    h = bar.get_height()
    axes[1].text(bar.get_x() + bar.get_width()/2, h + 5000, f"₹{int(h/1000)}k", ha='center', fontsize=9)

axes[1].grid(axis='y', linestyle=':', alpha=0.4)

# Histogram: order values
axes[2].hist(order_values, bins=40, color='#2ca02c', edgecolor='black', alpha=0.8)
axes[2].set_title("Order Value Distribution")
axes[2].set_xlabel("Order value (₹)")
axes[2].set_ylabel("Count")
axes[2].grid(axis='y', linestyle=':', alpha=0.4)

fig.suptitle("Retail Overview — Q3 2025", fontsize=16, fontweight='bold')
plt.tight_layout(rect=[0, 0.03, 1, 0.95])  # leave space for suptitle

# Save high-resolution PNG and vector PDF
fig.savefig("retail_overview.png", dpi=300, bbox_inches='tight')
fig.savefig("retail_overview.pdf", bbox_inches='tight')

plt.show()
```

**What this does**

* Creates a 3-panel dashboard with readable fonts, formatted currency ticks, gridlines, legend, rotated xticks, bar labels, and saves both PNG (300 dpi) and PDF.

---

## 7️⃣ Best practices & checklist before saving figures

* Choose `figsize` and `dpi` appropriate for medium (web) vs print. (e.g., `dpi=150` web, `dpi=300` print).
* Use `bbox_inches='tight'` to avoid cut-off labels.
* Use vector format (PDF/SVG) for line art and slides that may be scaled.
* Ensure fonts are large enough for slides (title ≥14, labels ≥10–12).
* Export with `facecolor='white'` unless you need transparent.
* Keep color palette accessible (check contrast for projection).

---

## 8️⃣ Practice tasks

1. Create a 2×2 grid of plots (sales, revenue, histogram, scatter) using `plt.subplots(2,2, figsize=(12,8))`. Use `sharex` or `sharey` where appropriate.
2. Export one figure as `dashboard.png` (300 dpi) and `dashboard.pdf`. Verify text is crisp in the PDF.
3. Make a plot where the legend is outside the axes using `bbox_to_anchor`. Ensure `tight_layout()` or `plt.subplots_adjust()` avoids overlap.
4. Format y-axis to display thousands (`₹120k`) using `Matplotlib.ticker`.
5. Create a publication-ready figure: choose colors, markers, add annotation, and save with `dpi=600` (if required for journal).

---

## 9️⃣ Quick reference snippet

```python
fig, ax = plt.subplots(figsize=(10,6), dpi=200)
ax.plot(x, y, label='Line', color='C0', marker='o', linestyle='--')
ax.set_title("Title", fontsize=14)
ax.set_xlabel("X-label")
ax.set_ylabel("Y-label")
ax.grid(True, linestyle=':', alpha=0.6)
ax.legend(loc='best')
fig.savefig("figure.png", dpi=300, bbox_inches='tight')
```

---

Would you like me to:

* Convert this **entire lecture** into a runnable **Jupyter Notebook (.ipynb)** (with the simulated data used above), **or**
* Generate the **PNG + PDF example files** from the exact code above and provide download links?

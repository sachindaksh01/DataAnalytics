---

# 📘 Module 6: Working with Random Data

---

## 1. Why Random Data is Important?

* **Data Simulation:** Sometimes we don’t have real datasets, so we generate artificial data.
* **Sampling:** Random selection is used in surveys, research, and experiments.
* **Machine Learning:** Models are trained on randomly shuffled or split data.
* **Statistics:** Random numbers are used in probability experiments and Monte Carlo simulations.

---

## 2. Generating Random Numbers

NumPy provides a module `np.random` to generate random numbers.

---

### (A) `np.random.rand()` – Random numbers (Uniform distribution 0 to 1)

**Scenario:** A company wants to simulate **customer satisfaction scores** between 0 and 1.

```python
import numpy as np

scores = np.random.rand(5)  # 5 random values between 0 and 1
print("Random Satisfaction Scores:", scores)
```

**Possible Output:**

```
Random Satisfaction Scores: [0.62 0.13 0.87 0.44 0.91]
```

📌 **Interpretation:**
These values represent **probability-like data**. For example, 0.91 = 91% satisfied.

---

### (B) `np.random.randn()` – Random numbers (Normal distribution, mean=0, std=1)

**Scenario:** A school wants to simulate **student test score deviations** from the mean.

```python
scores = np.random.randn(10)  # 10 values from normal distribution
print("Random Test Score Deviations:", scores)
```

**Possible Output:**

```
[-0.45  1.20 -0.33  0.87 -1.10  0.52 -0.12  0.90 -0.60  1.45]
```

📌 **Interpretation:**

* Negative = below average, Positive = above average.
* Useful when simulating **real-world naturally distributed data** (like heights, IQ, marks).

---

### (C) `np.random.randint()` – Random Integers

**Scenario:** A store wants to randomly generate **invoice numbers** or **lottery tickets**.

```python
lottery = np.random.randint(1000, 9999, size=5)  # 5 random integers between 1000–9999
print("Lottery Numbers:", lottery)
```

**Possible Output:**

```
Lottery Numbers: [4821 9345 1283 7701 5610]
```

📌 **Interpretation:**
Random integers are useful for **IDs, sampling customers, assigning random groups**.

---

## 3. Setting Random Seed – `np.random.seed()`

👉 **Problem:** By default, random numbers change every time we run code.
👉 **Solution:** Fix results using a seed.

**Scenario:** A researcher needs the **same random sample each time** for testing reproducibility.

```python
np.random.seed(42)  # fix the randomness
print(np.random.rand(5))  # will always give same result
```

**Output (always same):**

```
[0.37454012 0.95071431 0.73199394 0.59865848 0.15601864]
```

📌 **Interpretation:**
Setting a seed ensures **reproducibility** — same “random” numbers across multiple runs.

---

## 4. Shuffling and Permutations

---

### (A) `np.random.shuffle()` – Shuffles array in place

**Scenario:** A teacher wants to **randomize student roll numbers** before an activity.

```python
students = np.array([1,2,3,4,5,6,7,8,9,10])
np.random.shuffle(students)
print("Shuffled Student Order:", students)
```

**Output (changes every run):**

```
Shuffled Student Order: [ 7  2  9  6  4  1 10  5  8  3]
```

📌 **Interpretation:**
Shuffle rearranges the data randomly, useful in **random sampling and ML training splits**.

---

### (B) `np.random.permutation()` – Returns a new shuffled array

**Scenario:** A company wants to test **random order of product promotions**.

```python
products = np.array(["Tea", "Coffee", "Juice", "Soda"])
random_order = np.random.permutation(products)
print("Random Promotion Order:", random_order)
```

**Output (example):**

```
Random Promotion Order: ['Juice' 'Tea' 'Soda' 'Coffee']
```

📌 **Interpretation:**
Unlike shuffle, this does **not change the original array**. It creates a **new shuffled copy**.

---

# 🔑 Summary

* **rand()** → uniform random numbers between 0–1 (customer satisfaction, probabilities).
* **randn()** → normal distribution (student marks, heights, IQ).
* **randint()** → random integers (lottery, IDs, random sampling).
* **seed()** → fix random results (reproducibility in research and ML).
* **shuffle()** → randomizes data in-place (student order, dataset shuffling).
* **permutation()** → random shuffled copy (product testing order, experiment variations).

👉 These tools are **essential in analytics and ML** for sampling, simulations, shuffling datasets, and reproducible experiments.

---

Perfect 👍
Here’s a **20-question practice set** for **Module 6: Working with Random Data in NumPy**.
Each question is **scenario-based**, so students learn not just syntax, but also **real-life applications**.

---

# 📝 Practice Set – Random Data in NumPy

---

## **Part A – Generating Random Numbers**

1. Use `np.random.rand()` to simulate **probability of winning a cricket match** for 10 teams.

2. Generate **random customer satisfaction scores** (between 0 and 1) for 5 customers using `np.random.rand()`.

3. Use `np.random.randn()` to generate 20 values representing **student score deviations** from the class average.

4. A company wants to simulate **employee performance deviations** (normal distribution). Generate 15 random values with `np.random.randn()`.

5. Generate 10 random integers between **1000 and 5000** to represent **invoice numbers** using `np.random.randint()`.

6. Create a simulation of **daily sales units** for 7 days, with random integers between 50 and 200.

---

## **Part B – Setting Random Seed**

7. Use `np.random.seed(10)` and generate 5 random numbers with `np.random.rand()`. Run the code twice — are the results the same?

8. Set seed = 99 and generate 10 random integers between 1 and 100. Verify that results remain the same when rerun.

---

## **Part C – Shuffling and Permutations**

9. Shuffle a list of student roll numbers `[1,2,3,4,5,6,7,8,9,10]` using `np.random.shuffle()`.

10. Create an array of product names: `["Tea","Coffee","Juice","Soda"]`. Use `np.random.permutation()` to create a random promotion order.

11. Shuffle a dataset of exam scores `[60,70,80,90,100]` and print the result.

12. Use `np.random.permutation()` to shuffle employee IDs `[101,102,103,104,105]` without changing the original array.

---

## **Part D – Applied Random Data Scenarios**

13. Generate 30 random numbers between 0 and 1 to represent **probabilities of customers buying a product**. Find how many are greater than 0.5.

14. Use `np.random.randn(100)` to generate a dataset of **100 student score deviations**. Calculate mean and standard deviation of this dataset.

15. Generate a **random 5x5 matrix** of integers between 1 and 50 to simulate a **lottery ticket grid**.

16. Simulate **10 coin tosses** using `np.random.randint(0,2,10)` where 0 = Tail, 1 = Head. Count how many Heads and Tails appear.

17. Generate random ages of 20 people between 18 and 60. Calculate mean age.

18. Use `np.random.shuffle()` on `[“Math”,“Science”,“English”,“History”]` to create a random **exam schedule**.

19. Generate random sales quantities for 12 months (between 100–500). Find cumulative sales using `np.cumsum()`.

20. Simulate **daily temperature deviations** for 30 days using `np.random.randn(30)`. Identify the day with the maximum deviation using `np.argmax()`.

---






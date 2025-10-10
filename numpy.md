# Extra Exercises: NumPy

Credits: Akara Supratak (email: [akara.sup@mahidol.ac.th](mailto:akara.sup@mahidol.ac.th), github: [@akaraspt](https://github.com/akaraspt))

## What is NumPy?

### **Why do we use NumPy arrays instead of pure Python lists for numeric computing?**

Select the **best** answer.

* [ ] A. Because NumPy forbids loops entirely.
* [ ] B. Because NumPy arrays are stored contiguously with a fixed `dtype`, enabling vectorized operations that are faster and memory-efficient.
* [ ] C. Because Python lists cannot hold integers.
* [ ] D. Because NumPy automatically parallelizes every operation.
* [ ] E. Because NumPy makes code always shorter, regardless of logic.

## Array Creation & Shapes

### **Fill in the blanks: create arrays with the correct shape/dtype**

Create an integer array of 5 zeros.

```python
import numpy as np
a = np.zeros(_____, dtype=_____)   # expect: shape (5,), integer
```

Create a 2×3 array of zeros with `float` dtype.

```python
b = np.______(_____, dtype=_____)    # expect: shape (2,3), float
```

Create evenly spaced integers `[0, 2, 4, 6, 8]`.

```python
c = np.arange(_____)               # fill proper arguments
```

### **Multiple choice: shapes**

Given:

```python
x = np.arange(12).reshape(3,4)
```

What is `x.shape`?

* [ ] A. `(12,)`
* [ ] B. `(4,3)`
* [ ] C. `(3,4)`
* [ ] D. `(2,6)`
* [ ] E. `None`

## Indexing, Slicing, Boolean Masks

### **Complete the slices**

Given:

```python
x = np.array([[10, 20, 30],
              [40, 50, 60],
              [70, 80, 90]])
```

Select the **second column** (as a 1D view):

```python
col2 = x[:, _____]   # expect: [20 50 80]
```

Select the **first two rows and last two columns**:

```python
block = x[_____, _____]   # expect: [[20,30],
                          #         [50,60]]
```

Select elements **greater than or equal to 50** (boolean filter giving a 1D result):

```python
ge50 = x[_____]   # expect: [50 60 70 80 90]
```

### **Which lines correctly build a boolean mask?**

Select **all that apply** (assume `x` is a NumPy array):

* [ ] A. `mask = x > 0`
* [ ] B. `mask = (x % 2 == 0) & (x < 50)`
* [ ] C. `mask = x and (x < 10)`
* [ ] D. `mask = (x == 3) | (x == 7)`
* [ ] E. `mask = ~(x > 100)`

## Element-wise Operations vs Aggregation

### **Complete the code: element-wise operations**

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

s = np.__________(a, b)     # addition → [5 7 9]
d = np.__________(a, b)     # subtraction → [-3 -3 -3]
m = np.__________(a, b)     # multiply → [ 4 10 18]
q = np.__________(b, a)     # divide → [4.  2.5 2. ]
```

**True/False**
Mark **True** if `axis` can be passed to the function.

* [ ] `np.add(..., axis=1)`
* [ ] `np.sum(..., axis=1)`
* [ ] `np.mean(..., axis=0)`
* [ ] `np.multiply(..., axis=0)`

> Reminder: `axis` applies to **aggregation** (e.g., `sum`, `mean`, `min`, `max`, `std`), not to element-wise arithmetic (`add/subtract/multiply/divide`).

## Aggregation with `axis`

Given:

```python
y = np.array([[1,  2,  3],
              [10, 20, 30]])
```

### **Fill in the blanks**

Row sums (shape `(2,)`):

```python
row_sums = np.sum(y, axis=_____)   # expect: [ 6 60 ]
```

Column means (shape `(3,)`):

```python
col_means = np.mean(y, axis=_____) # expect: [5.5 11.  16.5]
```

Global min and max:

```python
gmin   = np.________(y)     # expect: 1
gmax   = np.________(y)     # expect: 30
```

Row maxs (shape `(2,)`):

```python
row_max = np.________(y, axis=_____)  # expect: [ 3 30 ]
```

Column standard deviations (shape `(3,)`):

```python
col_std = np.________(y, axis=_____)  # expect: [ 4.5  9.  13.5]
```

## Unique & Counting

### **Use `np.unique`**

Given:

```python
z = np.array([3, 1, 2, 3, 2, 1, 3])
```

Get the sorted unique values:

```python
u = np.__________  # expect: [1 2 3]
```

Get unique values **and** their counts:

```python
vals, cnts = __________
# expect: vals=[1 2 3], cnts=[2 2 3]
```

## Short Coding Tasks

### Compute basic statistics

Read a 2D array and print:

* Sum of all elements
* Mean of all elements
* Row-wise maximum values
* Column-wise standard deviation

**Input:**

```text
2 3
1 2 3
10 20 30
```

**Expected Output:**

```text
sum=66
mean=11.0
row_max=[ 3 30]
col_std=[4.5 9. 13.5]
```

---

### Count labels using `np.unique(..., return_counts=True)`

**Input:**

```text
n
l1 l2 ... ln
```

**Goal**
Print unique labels, their counts, and the most frequent label.

**Input:**

```text
10
1 2 1 3 2 2 3 3 3 1
```

**Expected Output:**

```text
unique=[1 2 3]
counts=[3 3 4]
most_frequent=3
```

---

### Selecting specific rows and columns

Given:

```python
import numpy as np
A = np.array([[10, 20, 30],
              [40, 50, 60],
              [70, 80, 90]])
```

**1. Select the first row**

```python
row1 = A[_____]       # expect: [10 20 30]
```

**2. Select the last column**

```python
last_col = A[:, _____]   # expect: [30 60 90]
```

**3. Select the middle element (row=1, col=1)**

```python
mid = A[_____, _____]    # expect: 50
```

**4. Select the top-left 2×2 block**

```python
block = A[_____, _____]  # expect: [[10 20],
                         #          [40 50]]
```

---

### Selecting multiple rows or columns

Given:

```python
B = np.array([[ 1,  2,  3,  4],
              [ 5,  6,  7,  8],
              [ 9, 10, 11, 12]])
```

**1. Select rows 0 and 2**

```python
rows_0_2 = B[[_____, _____], :]
# expect: [[ 1  2  3  4]
#          [ 9 10 11 12]]
```

**2. Select columns 1 and 3**

```python
cols_1_3 = B[:, [_____, _____]]
# expect: [[ 2  4]
#          [ 6  8]
#          [10 12]]
```

---

### Selecting rows with conditions

Given:

```python
C = np.array([[10, 15, 20],
              [25, 30, 35],
              [40, 45, 50]])
```

**1. Select rows where the first column ≥ 20**

```python
cond = C[:, 0] >= _____
filtered = C[cond]
# expect: [[25 30 35]
#          [40 45 50]]
```

**2. Select rows where the last column < 40**

```python
cond = C[:, -1] < _____
filtered = C[cond]
# expect: [[10 15 20]
#          [25 30 35]]
```

---

### Combine Selection and Summation

Given:

```python
G = np.array([[10, 20, 30],
              [40, 50, 60],
              [70, 80, 90]])
```

Select only the **rows where the first column > 20**,
then **print each row together with its row sum**.

Expected output:

```text
Row: [40 50 60] → sum = 150
Row: [70 80 90] → sum = 240
```

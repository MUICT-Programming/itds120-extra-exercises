# Extra Exercises: pandas

Credits: Akara Supratak (email: [akara.sup@mahidol.ac.th](mailto:akara.sup@mahidol.ac.th), github: [@akaraspt](https://github.com/akaraspt))

Assume `import pandas as pd` and `df` is a DataFrame loaded from `data.csv` [[download](https://raw.githubusercontent.com/MUICT-Programming/itds120-extra-exercises/refs/heads/main/data.csv)].

Typical columns you may see in the tasks below: `['Name','Sex','Age','Pclass','Fare','Embarked']`. Adjust if your file differs.

## What is pandas?

### Why do we use a pandas DataFrame for tabular data?

Select the best answer.

* [ ] A. Because pandas automatically fixes all missing data without any effort.
* [ ] B. Because DataFrames provide labeled columns, fast vectorized operations, and rich filtering/sorting/grouping APIs for tabular data.
* [ ] C. Because CSV files can only be read by pandas.
* [ ] D. Because DataFrames are always smaller in memory than NumPy arrays.
* [ ] E. Because pandas replaces the need to understand Python.

## Selecting Columns and Rows

### Fill in the blanks: select specific columns

Select only columns `Name`, `Age`, and `Fare`.

```python
subset = df[___________]
```

Select the first 5 rows of those columns.

```python
head5 = subset.___________
```

### Select rows by position with `iloc`

Given `df` with at least 120 rows, select rows 100–109 (10 rows) and only show columns `Name` and `Age`.

```python
part = df.iloc[___________][[___________]]
```

Select the very first row as a Series.

```python
row0 = df.iloc[___________]
```

Select rows 0, 2, and 4, and only columns `Pclass` and `Fare`.

```python
pick = df.iloc[[___________]][[___________]]
```

## Conditional Filtering (`&`, `|`, `~`)

### Complete the conditions

Select passengers with `Age >= 18` and `Fare > 100`.

```python
adults_rich = df[___________]
```

Select rows where `Embarked` is not `'S'` (use `~` with a condition).

```python
not_S = df[___________]
```

Select passengers who are either in `Pclass` 1 or have `Fare >= 200`.

```python
vip = df[___________]
```

Note: Always wrap each condition in parentheses when using `&`, `|`, or `~`.

## String Matching with `.str.contains`

### Case-insensitive name search

Select rows where `Name` contains `"john"` (case-insensitive), then show `['Name','Age','Embarked']` for the first 10 results.

```python
mask = df['Name'].str.contains('john', case=______, na=______)
out  = df[mask][___________].head(______)
```

Hint:

* Case-insensitive means `case=False` and case-sensitive means `case=True`.
* Use `na=False` to treat missing values as non-matching, so they won't appear in the output.

## Membership with `.isin`

### Filter by a set of values

Keep rows where `Embarked` is in `{'S','C'}` and then show the first 8 rows of `['Embarked','Pclass','Fare']`.

```python
subset = df[df['Embarked'].isin(___________)][[___________]].head(___________)
```

## Frequency with `value_counts()` and `unique()`

### Count categories

Show counts of each value in `Sex` (from most to least common).

```python
counts = df['Sex'].___________
```

List unique values (in order of appearance) in `Embarked`.

```python
uniq = df['Embarked'].___________
```

## Sorting with `sort_values()`

### Single-key and multi-key sort

Sort by `Fare` descending and show `['Name','Fare']` for the first 5 rows.

```python
top_fare = df.sort_values(___________)[___________].head(___________)
```

Sort by `Embarked` ascending, then by `Fare` descending, and show the last 5 rows of `['Embarked','Fare','Name']`.

```python
tail5 = df.sort_values(___________)[___________].tail(___________)
```

## Short Coding Tasks

The `data.csv` file can be downloaded from here [[download](https://raw.githubusercontent.com/MUICT-Programming/itds120-extra-exercises/refs/heads/main/data.csv)].

### Basic column selection and preview

Read `data.csv`, select columns `['Pclass','Sex','Age','Fare','Embarked']`, and print the first 5 rows.

---

### Row and column slicing with `iloc`

Print rows 50–59 (10 rows) showing only `['Name','Age','Pclass']` in the original order.

---

### Combined conditions

Print `['Name','Age','Fare','Embarked']` for passengers who:

* `Age >= 18`
* `Fare` between 50 and 150 (inclusive of lower bound, exclusive of upper bound)
* `Embarked` is not `'UNK'`

---

### String matching

Print the first 12 rows of `['Name','Pclass','Embarked']` where `Name` contains `"anna"` (case-insensitive).

Hint:

* `.str.contains` is used for substring matching.
* You can specify whether the match is case-sensitive or not using the `case` parameter.
  * case-sensitive: `case=True`
  * case-insensitive: `case=False`
* Use `na=False` to treat missing values as non-matching, so they won't appear in the output.

---

### Membership filtering with `.isin`

Keep rows where `Embarked` in `{'S','Q'}` and print the first 10 rows of `['Embarked','Pclass','Fare']` sorted by `Pclass` ascending and `Fare` descending.

---

### Value counts and unique values

Print counts of each value in `Embarked` (from most to least common) and list unique values (in order of appearance).

---

### Multi-key sorting with a condition

Select rows where `Age` is not null and `Age >= 16`, then sort by `Embarked` ascending and `Fare` descending. Print `['Name','Embarked','Fare','Age']` for the top 15.

---

### Two ways to get “top N by frequency”

Show the top 3 most common `Embarked` values and their counts.

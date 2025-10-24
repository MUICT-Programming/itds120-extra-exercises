# Extra Exercises: String Manipulation

Credits: Akara Supratak (email: akara.sup@mahidol.ac.th, github: [@akaraspt](https://github.com/akaraspt))

## What is a String?

### Which statement about Python strings is TRUE?

Select the **best** answer.

* [ ] A. Strings are mutable; you can assign to `s[0] = 'H'`.
* [ ] B. Strings are sequences of characters and **immutable**.
* [ ] C. Strings must be declared with a fixed length.
* [ ] D. Strings cannot contain spaces.

### Which statement create an empty string?

Select the **best** answer.

* [ ] A. `s = ''`
* [ ] B. `s = ""`
* [ ] C. `s = str()`
* [ ] D. `s = None`
* [ ] E. `s = 0`

## Indexing & Slicing

Given:

```python
s = "Hello, world!"
```

### Fill in the blanks

First character:

```python
first = s[___]           # expect: 'H'
```

Last character:

```python
last = s[___]            # expect: '!'
```

Slice `"Hello"`:

```python
hello = s[___]       # expect: 'Hello'
```

Slice `"world"` (no comma, no space):

```python
world = s[___]       # expect: 'world'
```

Slice `"world!"` using negative indices:

```python
world_excl = s[___]  # expect: 'world!'
```

Reverse the string:

```python
reversed_s = s[___]  # expect: '!dlrow ,olleH'
```

## Core String Methods

### Multiple choice (select **all** that apply)

Which lines correctly transform `t = "  Data Science  "` to `"data science"`?

* [ ] A. `t.strip().lower()`
* [ ] B. `t.lower().strip()`
* [ ] C. `t.replace("  ", "").lower()`
* [ ] D. `t.upper().strip()`

### Fill in the blanks

Convert to uppercase:

```python
"mah-idol".____()        # expect: 'MAH-IDOL'
```

Remove leading/trailing spaces:

```python
"  hello  ".___()        # expect: 'hello'
```

Replace `"cat"` with `"dog"`:

```python
"catapult"._____("cat", "dog")   # expect: 'dogapult'
```

Find index of substring `"lo"` in `"Hello"`:

```python
"Hello".____("lo")       # expect: 3
```

## Splitting & Joining

Given:

```python
line = "Alice,Bob,Charlie"
```

### Fill in the blanks

Split by comma to a list:

```python
names = line.____(",")     # expect: ['Alice', 'Bob', 'Charlie']
```

Join names with a space:

```python
joined = " ".___([ "Alice", "Bob", "Charlie" ])  # expect: 'Alice Bob Charlie'
```

Split `"  one   two  three    "` by any whitespace:

```python
s = "  one   two  three    "
# YOUR CODE HERE
# expect: ['one','two','three']
# Hint: see the result after calling split to understand what to do next.
```

## Short Coding Tasks

### Normalize Names

Read one line, which contains names separated by commas.
Print names in lowercase, stripped, and joined by a single space.

**Input:**

```text
 Alice , BOB,   charlie
```

**Expected Output:**

```text
alice bob charlie
```

**Starter `main.py`**

```python
s = input()
# TODO: strip input, split by ',', strip each, lower each, join with one space, print
```

---

### Count Vowels and Consonants

Given a single lowercase string `s` (letters only), print counts of vowels and consonants.

**Input:**

```text
datascience
```

**Expected Output:**

```text
vowels=6
consonants=6
```

**Starter `main.py`**

```python
s = input().strip()
vowels = set("aeiou")
# TODO: compute counts (no loops required if you prefer: sum(c in vowels for c in s))
```

---

### Palindrome Check (ignore spaces and case)

Print `"palindrome"` if the input line is a palindrome when spaces and case are ignored; otherwise print `"not palindrome"`.

**Input:**

```text
Never odd or even
```

**Expected Output:**

```text
palindrome
```

---

### Extract Numbers and Sum

Given a line that may contain words and numbers, extract all integer substrings and print their sum.

**Input:**

```text
id=10 code42 and 8 apples
```

**Expected Output:**

```text
60
```

Explanation: 60 = 10 + 42 + 8

---

### Remove word that contain symbols

Given a line of text, remove words that contain any non-alphabetic characters (i.e., symbols, digits). Print the cleaned line.

**Input:**

```text
is fun, but c0ding is #awesome!
```

**Expected Output:**

```text
is but is
```

Explanation: after you split the line into words, only `"is"`, `"but"`, and `"is"` remain. `"fun,"`, `"c0ding"`, and `"#awesome!"` are removed.

---

### Convert from string money to float

Write a program that reads a string representing money in either USD or JPY currency (e.g., `"1,234.56 USD"` or `"87.5 JPY"`) and converts it to a float number representing the amount only in THB (e.g., `1234.56` or `87.5`).

The following exchange rates apply:

* 1 USD = 30.0 THB
* 1 JPY = 0.25 THB

**Input in USD:**

```text
1,234.56 USD
```

**Expected Output:**

```text
37036.8
```

**Input in JPY:**

```text
87.5 JPY
```

**Expected Output:**

```text
21.875
```

**Starter `main.py`**

```python
s = input().strip()
convert2THB = {
    "USD": 30.0,
    "JPY": 0.25
}
# YOUR CODE HERE
```

---

### Encode/Decode a Message

Write a program that reads a string message and an integer key, then either encodes or decodes the message using a Caesar cipher based on user choice. The program should read three lines: the first line is the message, the second line is the integer key (shift), and the third line is either `"encode"` or `"decode"`.

The encoding shifts each letter forward by the key, while decoding shifts each letter backward by the key. Non-alphabetic characters should remain unchanged. The case of the letters should be preserved. Ignore the characters that are not letters.

**Input:**

```text
Hello, World!
3
encode
```

**Expected Output:**

```text
Khoor, Zruog!
```

**Input:**

```text
Khoor, Zruog!
3
decode
```

**Expected Output:**

```text
Hello, World!
```

**Starter `main.py`**

```python
text = input()
key = int(input())
# YOUR CODE HERE
```

# Extra Exercises: File Input/Output

Credits: Akara Supratak (email: akara.sup@mahidol.ac.th, github: [@akaraspt](https://github.com/akaraspt))

## File Basics

### Which statement about file modes is TRUE?

Select the **best** answer.

* [ ] A. `'r'` creates a new file and truncates existing contents.
* [ ] B. `'w'` opens a file for writing only, creating it if it doesn't exist. It truncates existing contents.
* [ ] C. `'a'` opens a file for reading only.
* [ ] D. `'r+'` is invalid in Python.
* [ ] E. Files must always be closed manually; `with ... as f:` cannot manage closing.

## Open & Read

IMPORTANT: It is recommended to specify encoding (e.g., `encoding="utf-8"`) when dealing with text files to avoid platform-dependent issues.

Given the following file:

**input.txt**

```text
I love coding in Python!
Python is great for data science.
Hello, world!

123 abc 45 def 6gh 7890
The quick brown fox jumps over the lazy dog.
Python3 Is fun, but c0ding iS #awesome!
A man a plan a canal Panama
Madam In Eden I'm Adam
Was it a car or a cat I saw?
No 'x' in Nixon

```

### Fill in the blanks

Read entire contents:

```python
with open("input.txt", ____, encoding="utf-8") as f:
    data = f.____()          # expect: full string
```

Read one line:

```python
with open("input.txt", ____, encoding="utf-8") as f:
    line = f.________()      # expect: line including trailing '\n' if present
```

Read all lines into a list:

```python
with open("input.txt", ____, encoding="utf-8") as f:
    lines = f.________()     # expect: list of lines
```

Iterate safely over lines (preferred pattern):

```python
with open("input.txt", ____, encoding="utf-8") as f:
    for line in f:
        # process line
        pass
```

## Write & Append

### Multiple choice

Which lines **correctly** write text to a file?

* [ ] A. `with open("out.txt","r") as f: f.write("hi")`
* [ ] B. `with open("out.txt","w",encoding="utf-8") as f: f.write("hi\n")`
* [ ] C. `with open("out.txt","a",encoding="utf-8") as f: f.write("next\n")`
* [ ] D. `f = open("out.txt","w"); f.write("x")` (and never close)

### Fill in the blanks

Write a single line:

```python
with open("out.txt", "w", encoding="utf-8") as f:
    f.____("Hello, World!\n")
```

Write multiple lines using a loop:

```python
lines = ["A", "B", "C"]
with open("out.txt", "w", encoding="utf-8") as f:
    for line in lines:
        f.____(line)
        f.____("\n")
```

Write multiple lines at once:

```python
lines = ["A\n", "B\n", "C\n"]
with open("out.txt", "w", encoding="utf-8") as f:
    f.________(lines)
```

### Debugging Writing One Word Per Line

The goal is to write each word from a list to a new line in `words.txt`, but the code is buggy.

```python
words = ["apple", "banana", "cherry"]
with open("words.txt","w") as f:
    for w in words:
        f.write(w)
```

**Fix** the code so that each word appears on its own line in `words.txt`.

**Expected `words.txt`:**

```text
apple
banana
cherry
```

### Debugging File I/O

The goal is to append a line `"DONE\n"` to `log.txt`, but the code is buggy.

```python
# Create a log file, `log.txt` with some initial content
with open("log.txt","w") as f:
    f.write("Starting log...\n")
    f.write("Processing data...\n")
    f.write("Finished processing.\n")

# Buggy code
f = open("log.txt","w")
f.append("DONE\n")
```

**Fix** the code so it appends correctly and closes the file safely.

**Expected**: the line `DONE` appears at the end of `log.txt`.

## Short Coding Tasks

### Count Lines, Words, Characters

Read a text file, `input.txt`, and print counts:

```text
lines=<num_lines>
words=<num_words>
chars=<num_chars>
```

Rules:

* Words are tokens from `split()` (whitespace-delimited).
* Characters include all characters (including `\n` if read via `read()`).

**input.txt**

```text
I love coding in Python!
Python is great for data science.
Hello, world!

123 abc 45 def 6gh 7890
The quick brown fox jumps over the lazy dog.
Python3 Is fun, but c0ding iS #awesome!
A man a plan a canal Panama
Madam In Eden I'm Adam
Was it a car or a cat I saw?
No 'x' in Nixon
```

**Starter main.py**

```python
with open("input.txt", "r", encoding="utf-8") as f:
    data = f.read()
# TODO: compute lines, words, chars and print as specified
```

---

### Filter Lines Containing a Keyword

Read `input.txt`, print only lines that contain the substring from user input (case-insensitive). Do **not** modify the file.

**input.txt**

```text
<>
Python is great for data science.
Python3 Is fun, but c0ding iS #awesome!

This is the third line.
We love file I/O.
Text processing is fun.

&!5 12 -098

```

**Input:**

```text
IS
```

**Expected Output:**

```text
Python is great for data science.
Python3 Is fun, but c0ding iS #awesome!
This is the third line.
Text processing is fun.
```

---

### Copy File (Text Mode)

Copy contents of `input.txt` to `dest.txt`. If `dest.txt` exists, overwrite it.

**input.txt**

```text
<>
Python is great for data science.
Python3 Is fun, but c0ding iS #awesome!

This is the third line.
We love file I/O.
Text processing is fun.

&!5 12 -098

```

---

### Sum Integers from File

Each line of `nums.txt` may contain integers separated by spaces. Sum **all** integers and print the total.

**nums.txt**

```text
10 20 -5
abc 15 xyz
-30 25
42
no numbers here
-10 -20 5
```

**Starter main.py**

```python
total = 0
with open("nums.txt", "r", encoding="utf-8") as f:
    # YOUR CODE HERE

print(total)
```

**Expected Output:**

```text
52
```

---

### Write Results to a New File

Read `input.txt`, convert every line to lowercase and strip trailing spaces, then write to `clean.txt`.

**input.txt**

```text
  Hello World!
Python is GREAT.  
   File I/O is FUN!   
```

**Expected `clean.txt`**

```text
hello world!
python is great.
file i/o is fun!
```

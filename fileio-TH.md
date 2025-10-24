# แบบฝึกหัดเพิ่มเติม: การอ่านและเขียนไฟล์ (File Input/Output)

เครดิต: Akara Supratak (email: [akara.sup@mahidol.ac.th](mailto:akara.sup@mahidol.ac.th), github: [@akaraspt](https://github.com/akaraspt))

## พื้นฐานของไฟล์ (File Basics)

### ข้อใดต่อไปนี้เกี่ยวกับโหมดการเปิดไฟล์เป็นจริง

เลือกคำตอบที่ **ถูกต้องที่สุด**

* [ ] A. `'r'` จะสร้างไฟล์ใหม่และลบเนื้อหาเก่าออกทั้งหมด
* [ ] B. `'w'` เปิดไฟล์สำหรับเขียนเท่านั้น สร้างไฟล์ใหม่ถ้าไม่มีอยู่ และลบเนื้อหาเก่าออก
* [ ] C. `'a'` เปิดไฟล์เพื่ออ่านเท่านั้น
* [ ] D. `'r+'` เป็นโหมดที่ใช้ไม่ได้ใน Python
* [ ] E. ทุกไฟล์ต้องปิดด้วยตนเองเสมอ; `with ... as f:` ไม่สามารถปิดไฟล์อัตโนมัติได้

## การเปิดและอ่านไฟล์ (Open & Read)

**สำคัญ:** แนะนำให้ระบุ encoding (เช่น `encoding="utf-8"`) เมื่อจัดการไฟล์ข้อความ เพื่อหลีกเลี่ยงปัญหาที่ขึ้นอยู่กับแพลตฟอร์ม

กำหนดไฟล์ต่อไปนี้:

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

### เติมคำในช่องว่าง

อ่านเนื้อหาทั้งหมด:

```python
with open("input.txt", ____, encoding="utf-8") as f:
    data = f.____()          # คาดหวังผลลัพธ์: สตริงเต็มทั้งไฟล์
```

อ่านบรรทัดเดียว:

```python
with open("input.txt", ____, encoding="utf-8") as f:
    line = f.________()      # คาดหวังผลลัพธ์: หนึ่งบรรทัด (รวม '\n' ถ้ามี)
```

อ่านทุกบรรทัดเป็นรายการ (list):

```python
with open("input.txt", ____, encoding="utf-8") as f:
    lines = f.________()     # คาดหวังผลลัพธ์: รายการของบรรทัดทั้งหมด
```

วนซ้ำอ่านไฟล์อย่างปลอดภัย (รูปแบบที่แนะนำ):

```python
with open("input.txt", ____, encoding="utf-8") as f:
    for line in f:
        # ประมวลผลแต่ละบรรทัด
        pass
```

## การเขียนและเพิ่มข้อมูล (Write & Append)

### คำถามแบบหลายตัวเลือก

บรรทัดใดต่อไปนี้เขียนข้อมูลลงไฟล์ได้ **ถูกต้อง**

* [ ] A. `with open("out.txt","r") as f: f.write("hi")`
* [ ] B. `with open("out.txt","w",encoding="utf-8") as f: f.write("hi\n")`
* [ ] C. `with open("out.txt","a",encoding="utf-8") as f: f.write("next\n")`
* [ ] D. `f = open("out.txt","w"); f.write("x")` (แล้วไม่ปิดไฟล์)

### เติมคำในช่องว่าง

เขียนข้อความหนึ่งบรรทัด:

```python
with open("out.txt", "w", encoding="utf-8") as f:
    f.____("Hello, World!\n")
```

เขียนหลายบรรทัดด้วยลูป:

```python
lines = ["A", "B", "C"]
with open("out.txt", "w", encoding="utf-8") as f:
    for line in lines:
        f.____(line)
        f.____("\n")
```

เขียนหลายบรรทัดพร้อมกัน:

```python
lines = ["A\n", "B\n", "C\n"]
with open("out.txt", "w", encoding="utf-8") as f:
    f.________(lines)
```

### แก้โค้ดที่บันทึกคำหนึ่งต่อบรรทัด (Debugging Writing One Word Per Line)

เป้าหมาย: เขียนแต่ละคำจากลิสต์ลงไฟล์ `words.txt` บรรทัดละคำ แต่โค้ดยังผิดอยู่

```python
words = ["apple", "banana", "cherry"]
with open("words.txt","w") as f:
    for w in words:
        f.write(w)
```

**แก้ไข** โค้ดเพื่อให้แต่ละคำอยู่คนละบรรทัดใน `words.txt`

**ผลลัพธ์ที่คาดหวัง (`words.txt`):**

```text
apple
banana
cherry
```

### แก้โค้ดการเขียนไฟล์ (Debugging File I/O)

เป้าหมาย: เพิ่มบรรทัด `"DONE\n"` ต่อท้ายไฟล์ `log.txt` แต่โค้ดยังผิดอยู่

```python
# สร้าง log.txt พร้อมเนื้อหาตั้งต้น
with open("log.txt","w") as f:
    f.write("Starting log...\n")
    f.write("Processing data...\n")
    f.write("Finished processing.\n")

# โค้ดที่มีบั๊ก
f = open("log.txt","w")
f.append("DONE\n")
```

**แก้ไข** โค้ดให้เพิ่มเนื้อหาอย่างถูกต้องและปิดไฟล์อย่างปลอดภัย

**ผลลัพธ์ที่คาดหวัง:**
บรรทัด `DONE` จะปรากฏท้ายไฟล์ `log.txt`

## แบบฝึกหัดเขียนโค้ดสั้น (Short Coding Tasks)

### นับจำนวนบรรทัด คำ และตัวอักษร (Count Lines, Words, Characters)

อ่านไฟล์ `input.txt` แล้วพิมพ์จำนวน:

```text
lines=<num_lines>
words=<num_words>
chars=<num_chars>
```

**กฎ:**

* คำ (words) คือตัวแยกด้วย `split()` (ช่องว่าง)
* ตัวอักษร (chars) รวมทุกตัว รวมถึง `\n` ถ้าอ่านด้วย `read()`

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
# TODO: คำนวณจำนวนบรรทัด คำ ตัวอักษร และพิมพ์ตามรูปแบบที่กำหนด
```

---

### กรองบรรทัดที่มีคำค้น (Filter Lines Containing a Keyword)

อ่าน `input.txt` แล้วพิมพ์เฉพาะบรรทัดที่มีคำย่อยจากอินพุตของผู้ใช้ (ไม่สนใจตัวพิมพ์ใหญ่/เล็ก)
**ห้ามแก้ไขไฟล์ต้นฉบับ**

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

**อินพุต:**

```text
IS
```

**ผลลัพธ์ที่คาดหวัง:**

```text
Python is great for data science.
Python3 Is fun, but c0ding iS #awesome!
This is the third line.
Text processing is fun.
```

---

### คัดลอกไฟล์ (Copy File, Text Mode)

คัดลอกเนื้อหาจาก `input.txt` ไปยัง `dest.txt`
ถ้า `dest.txt` มีอยู่แล้วให้เขียนทับ

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

### หาผลรวมของจำนวนเต็มในไฟล์ (Sum Integers from File)

แต่ละบรรทัดใน `nums.txt` อาจมีจำนวนเต็มคั่นด้วยช่องว่าง
ให้หาผลรวมของจำนวนเต็มทั้งหมดและพิมพ์ผลรวม

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

**ผลลัพธ์ที่คาดหวัง:**

```text
52
```

---

### เขียนผลลัพธ์ลงไฟล์ใหม่ (Write Results to a New File)

อ่าน `input.txt` แปลงทุกบรรทัดให้เป็นตัวพิมพ์เล็กและลบช่องว่างท้ายบรรทัด
จากนั้นเขียนผลลัพธ์ลงไฟล์ `clean.txt`

**input.txt**

```text
  Hello World!
Python is GREAT.  
   File I/O is FUN!   
```

**ผลลัพธ์ที่คาดหวัง (`clean.txt`):**

```text
hello world!
python is great.
file i/o is fun!
```

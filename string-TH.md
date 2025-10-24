# แบบฝึกหัดเพิ่มเติม: การจัดการสตริง (String Manipulation)

เครดิต: Akara Supratak (email: [akara.sup@mahidol.ac.th](mailto:akara.sup@mahidol.ac.th), github: [@akaraspt](https://github.com/akaraspt))

## สตริงคืออะไร (What is a String?)

### ข้อใดต่อไปนี้เกี่ยวกับสตริงของ Python เป็นจริง

เลือกคำตอบที่ **ถูกต้องที่สุด**

* [ ] A. สตริงเป็นชนิดข้อมูลที่เปลี่ยนค่าได้ (mutable); สามารถกำหนดค่าเช่น `s[0] = 'H'` ได้
* [ ] B. สตริงเป็นลำดับของตัวอักษร (sequence of characters) และเป็นชนิดข้อมูลที่ **ไม่สามารถเปลี่ยนค่าได้ (immutable)**
* [ ] C. สตริงต้องถูกประกาศด้วยความยาวที่แน่นอน
* [ ] D. สตริงไม่สามารถมีช่องว่างได้

### ข้อใดต่อไปนี้สร้างสตริงว่างเปล่าได้

เลือกคำตอบที่ **ถูกต้องที่สุด**

* [ ] A. `s = ''`
* [ ] B. `s = ""`
* [ ] C. `s = str()`
* [ ] D. `s = None`
* [ ] E. `s = 0`

## การเข้าถึงตำแหน่งและการตัดส่วนของสตริง (Indexing & Slicing)

กำหนดให้:

```python
s = "Hello, world!"
```

### เติมคำในช่องว่าง

อักขระตัวแรก:

```python
first = s[___]           # คาดหวังผลลัพธ์: 'H'
```

อักขระตัวสุดท้าย:

```python
last = s[___]            # คาดหวังผลลัพธ์: '!'
```

ตัดคำ `"Hello"`:

```python
hello = s[___]       # คาดหวังผลลัพธ์: 'Hello'
```

ตัดคำ `"world"` (ไม่เอาเครื่องหมายจุลภาคและช่องว่าง):

```python
world = s[___]       # คาดหวังผลลัพธ์: 'world'
```

ตัด `"world!"` โดยใช้อินเด็กซ์เชิงลบ:

```python
world_excl = s[___]  # คาดหวังผลลัพธ์: 'world!'
```

กลับสตริง:

```python
reversed_s = s[___]  # คาดหวังผลลัพธ์: '!dlrow ,olleH'
```

## เมธอดหลักของสตริง (Core String Methods)

### คำถามแบบหลายตัวเลือก (เลือกได้มากกว่า 1 ข้อ)

บรรทัดใดต่อไปนี้แปลง `t = "  Data Science  "` ให้เป็น `"data science"` ได้ถูกต้อง

* [ ] A. `t.strip().lower()`
* [ ] B. `t.lower().strip()`
* [ ] C. `t.replace("  ", "").lower()`
* [ ] D. `t.upper().strip()`

### เติมคำในช่องว่าง

แปลงเป็นตัวพิมพ์ใหญ่:

```python
"mah-idol".____()        # คาดหวังผลลัพธ์: 'MAH-IDOL'
```

ลบช่องว่างข้างหน้าและข้างหลัง:

```python
"  hello  ".___()        # คาดหวังผลลัพธ์: 'hello'
```

แทนที่ `"cat"` ด้วย `"dog"`:

```python
"catapult"._____("cat", "dog")   # คาดหวังผลลัพธ์: 'dogapult'
```

หาตำแหน่งของคำย่อย `"lo"` ใน `"Hello"`:

```python
"Hello".____("lo")       # คาดหวังผลลัพธ์: 3
```

## การแบ่งและรวมสตริง (Splitting & Joining)

กำหนดให้:

```python
line = "Alice,Bob,Charlie"
```

### เติมคำในช่องว่าง

แยกด้วยเครื่องหมายจุลภาคให้ได้ลิสต์:

```python
names = line.____(",")     # คาดหวังผลลัพธ์: ['Alice', 'Bob', 'Charlie']
```

รวมชื่อทั้งหมดโดยมีช่องว่างขั้น:

```python
joined = " ".___([ "Alice", "Bob", "Charlie" ])  # คาดหวังผลลัพธ์: 'Alice Bob Charlie'
```

แยก `"  one   two  three    "` ด้วยช่องว่างใด ๆ:

```python
s = "  one   two  three    "
# YOUR CODE HERE
# คาดหวังผลลัพธ์: ['one','two','three']
# Hint: ดูผลลัพธ์ของ split เพื่อเข้าใจสิ่งที่ต้องทำต่อ
```

## แบบฝึกหัดเขียนโค้ดสั้น (Short Coding Tasks)

### ปรับรูปแบบชื่อ (Normalize Names)

อ่าน 1 บรรทัดที่มีชื่อคั่นด้วยเครื่องหมายจุลภาค
พิมพ์ชื่อทั้งหมดเป็นตัวพิมพ์เล็ก ลบช่องว่าง และเชื่อมด้วยช่องว่างเดียว

**อินพุต:**

```text
 Alice , BOB,   charlie
```

**ผลลัพธ์ที่คาดหวัง:**

```text
alice bob charlie
```

**Starter `main.py`**

```python
s = input()
# TODO: strip input, split by ',', strip each, lower each, join with one space, print
```

---

### นับสระและพยัญชนะ (Count Vowels and Consonants)

ให้สตริงตัวพิมพ์เล็ก `s` (มีแต่ตัวอักษร) ให้พิมพ์จำนวนสระและพยัญชนะ

**อินพุต:**

```text
datascience
```

**ผลลัพธ์ที่คาดหวัง:**

```text
vowels=6
consonants=6
```

**Starter `main.py`**

```python
s = input().strip()
vowels = set("aeiou")
# TODO: compute counts (ไม่จำเป็นต้องใช้ลูปถ้าใช้ sum(c in vowels for c in s))
```

---

### ตรวจสอบคำกลับ (Palindrome Check) (ไม่สนใจช่องว่างและตัวพิมพ์)

พิมพ์ `"palindrome"` ถ้าข้อความเป็นคำกลับเมื่อไม่สนใจช่องว่างและตัวพิมพ์
มิฉะนั้นพิมพ์ `"not palindrome"`

**อินพุต:**

```text
Never odd or even
```

**ผลลัพธ์ที่คาดหวัง:**

```text
palindrome
```

---

### ดึงตัวเลขและหาผลรวม (Extract Numbers and Sum)

ให้บรรทัดที่มีทั้งคำและตัวเลข
ให้ดึงเฉพาะตัวเลขจำนวนเต็มออกมาและหาผลรวม

**อินพุต:**

```text
id=10 code42 and 8 apples
```

**ผลลัพธ์ที่คาดหวัง:**

```text
60
```

คำอธิบาย: 60 = 10 + 42 + 8

---

### ลบคำที่มีสัญลักษณ์ (Remove word that contain symbols)

ให้บรรทัดข้อความ ลบคำที่มีอักขระที่ไม่ใช่ตัวอักษร (เช่น สัญลักษณ์หรือตัวเลข) แล้วพิมพ์ผลลัพธ์

**อินพุต:**

```text
is fun, but c0ding is #awesome!
```

**ผลลัพธ์ที่คาดหวัง:**

```text
is but is
```

คำอธิบาย: หลังจากแยกคำ `"fun,"`, `"c0ding"`, และ `"#awesome!"` จะถูกลบออก เหลือ `"is"`, `"but"`, `"is"`

---

### แปลงจากข้อความเงินเป็นตัวเลข (Convert from string money to float)

เขียนโปรแกรมอ่านสตริงแสดงจำนวนเงินในสกุล USD หรือ JPY
เช่น `"1,234.56 USD"` หรือ `"87.5 JPY"` แล้วแปลงเป็นจำนวนทศนิยม (float) หน่วยบาท (THB)

อัตราแลกเปลี่ยน:

* 1 USD = 30.0 THB
* 1 JPY = 0.25 THB

**อินพุต (USD):**

```text
1,234.56 USD
```

**ผลลัพธ์ที่คาดหวัง:**

```text
37036.8
```

**อินพุต (JPY):**

```text
87.5 JPY
```

**ผลลัพธ์ที่คาดหวัง:**

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

### เข้ารหัส/ถอดรหัสข้อความ (Encode/Decode a Message)

เขียนโปรแกรมที่อ่านข้อความและจำนวนเต็ม (key) จากนั้นเข้ารหัสหรือถอดรหัสด้วย Caesar cipher
โปรแกรมอ่าน 3 บรรทัด:

* บรรทัดที่ 1 = ข้อความ
* บรรทัดที่ 2 = จำนวนเต็ม key (จำนวนการเลื่อน)
* บรรทัดที่ 3 = `"encode"` หรือ `"decode"`

การเข้ารหัส: เลื่อนตัวอักษรไปข้างหน้าตาม key
การถอดรหัส: เลื่อนตัวอักษรกลับตาม key
ตัวอักษรที่ไม่ใช่ตัวอักษรไม่เปลี่ยนแปลง และรักษาตัวพิมพ์ใหญ่/เล็ก

**อินพุต:**

```text
Hello, World!
3
encode
```

**ผลลัพธ์ที่คาดหวัง:**

```text
Khoor, Zruog!
```

**อินพุต:**

```text
Khoor, Zruog!
3
decode
```

**ผลลัพธ์ที่คาดหวัง:**

```text
Hello, World!
```

**Starter `main.py`**

```python
text = input()
key = int(input())
# YOUR CODE HERE
```

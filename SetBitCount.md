# 🔢 Sort Array by Set Bit Count

## 📌 Problem Statement
Given an array `arr[]` of integers, sort the array in **descending order based on the number of set bits (1s)** in their binary representation.

### ⚠️ Note:
- If two numbers have the **same number of set bits**, maintain their **original order** (**stable sort**).

---

## 🧠 Concept

- Convert each number to binary
- Count the number of `1`s (set bits)
- Sort based on:
  1. **Higher set bits first**
  2. Maintain **original order if equal** (stable sort)

---

## ✨ Example

### Input
```

arr = [5, 2, 3, 9, 4, 6, 7, 15, 32]

```

### Binary Representation
```

15 → 1111  (4 bits)
7  → 0111  (3 bits)
5  → 0101  (2 bits)
3  → 0011  (2 bits)
9  → 1001  (2 bits)
6  → 0110  (2 bits)
2  → 0010  (1 bit)
4  → 0100  (1 bit)
32 → 10000 (1 bit)

```

### Output
```

[15, 7, 5, 3, 9, 6, 2, 4, 32]

````

---

## 🐍 Python Solution

### ✅ Using Built-in `bit_count()` (Recommended)
```python
class Solution:
    def sortBySetBitCount(self, arr):
        arr.sort(key=lambda x: x.bit_count(), reverse=True)
        return arr
````

---

### ⚡ Alternative (Using `bin()`)

```python
class Solution:
    def sortBySetBitCount(self, arr):
        arr.sort(key=lambda x: bin(x).count('1'), reverse=True)
        return arr
```

---

---

## ⏱️ Complexity Analysis

| Approach    | Time Complexity | Space Complexity |
| ----------- | --------------- | ---------------- |
| Sorting     | O(n log n)      | O(n)             |
| Bucket Sort | O(n)            | O(n)             |


## Given an integer n, determine position of the only set bit (1) in its binary representation. The position is counted starting from 1 at the least significant bit (LSB).

## 💻 `Solution.java`

```java
public class Solution {

    // Function to find position of only set bit
    public static int findPosition(int n) {

        // If n is 0 or has more than one set bit
        if (n == 0 || (n & (n - 1)) != 0) {
            return -1;
        }

        int position = 1;

        // Find position of set bit
        while (n > 1) {
            n = n >> 1;
            position++;
        }

        return position;
    }

    // Main method for testing
    public static void main(String[] args) {
        int[] testCases = {2, 5, 4, 8, 0};

        for (int n : testCases) {
            System.out.println("Input: " + n + " → Output: " + findPosition(n));
        }
    }
}
```

---

# 📄 `README.md`

```md
# 🔍 Find Position of Only Set Bit

## 📌 Problem Statement

Given an integer `n`, determine the position of the only set bit (1) in its binary representation.

- Position starts from **1 (LSB)**
- If exactly one set bit exists → return its position
- Otherwise → return `-1`

---

## 🧠 Approach

A number has only one set bit **if and only if** it is a power of 2.

### ✔ Key Property
```

n & (n - 1) == 0   → only one set bit

````

---

## ⚙️ Algorithm

1. If `n == 0` → return `-1`
2. If `(n & (n - 1)) != 0` → return `-1`
3. Count position using right shift

---

## 💻 Code

```java
if (n == 0 || (n & (n - 1)) != 0) return -1;

int pos = 1;
while (n > 1) {
    n >>= 1;
    pos++;
}
return pos;
````

---

## 📊 Examples

| Input | Binary | Output |
| ----- | ------ | ------ |
| 2     | 10     | 2      |
| 4     | 100    | 3      |
| 5     | 101    | -1     |
| 0     | 0      | -1     |

---

## ⏱️ Complexity

* Time: `O(log n)`
* Space: `O(1)`

---

# 🌇 Buildings Receiving Sunlight

## 📌 Problem Statement

Given an array `arr[]` representing the heights of buildings arranged in a line, sunlight falls from the **left side**.

A building can receive sunlight if **all buildings to its left are shorter**.

👉 Find the **total number of buildings** that receive sunlight.

---

## 🧠 Approach

* Traverse the array from **left to right**
* Keep track of the **maximum height seen so far**
* A building gets sunlight if:

  ```text
  current height > max height so far
  ```

---

## ⚙️ Algorithm

1. Initialize:

   * `count = 0`
   * `maxHeight = 0`
2. Traverse the array:

   * If `arr[i] > maxHeight`:

     * Increment `count`
     * Update `maxHeight = arr[i]`
3. Return `count`

---

## 💻 Java Implementation

```java
class Solution {
    public int visibleBuildings(int arr[]) {
        int count = 0;
        int maxHeight = Integer.MIN_VALUE;

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] >= maxHeight) { 
                count++;
                maxHeight = arr[i];
            }
        }

        return count;
    }
}

```

---

## 🧪 Examples

### Example 1

```id="f1o2k7"
Input: arr = [2, 3, 4, 5]
Output: 4

Explanation:
All buildings are taller than previous ones → all get sunlight
```

---

### Example 2

```id="9w2mrl"
Input: arr = [4, 2, 3, 1]
Output: 1

Explanation:
Only the first building gets sunlight
```

---

### Example 3

```id="1o0zy9"
Input: arr = [1, 2, 1, 3, 4]
Output: 4
```

---

## ⚡ Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)










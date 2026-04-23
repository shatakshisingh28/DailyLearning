# 🔀 Split Array into Two Equal Sum Subarrays

## 📌 Problem Statement

Given an array of integers `arr[]`, determine whether it is possible to split it into **two contiguous subarrays** (without reordering) such that the **sum of both parts is equal**.

Return:

* `true` → if such a split exists
* `false` → otherwise

---

## 🧠 Approach

1. Calculate the **total sum** of the array
2. If the total sum is **odd**, return `false` (cannot split equally)
3. Find a point where the **prefix sum = total / 2**
4. If such a point exists → return `true`

---

## ⚙️ Algorithm

* Traverse the array once to calculate total sum
* Traverse again to find a prefix sum equal to half of total

---

## 💻 Java Implementation

```java
class Solution {
    public boolean canSplit(int[] arr) {
        
        int total = 0;

        // Step 1: Calculate total sum
        for (int i = 0; i < arr.length; i++) {
            total = total + arr[i];
        }

        // Step 2: If total is odd, cannot split
        if (total % 2 != 0) {
            return false;
        }

        int half = total / 2;
        int sum = 0;

        // Step 3: Find prefix sum equal to half
        for (int i = 0; i < arr.length; i++) {
            sum = sum + arr[i];

            if (sum == half) {
                return true;
            }
        }

        return false;
    }
}
```

---

## 🧪 Examples

### Example 1

```
Input: arr = [1, 2, 3, 4, 5, 5]
Output: true

Explanation:
Total = 20 → Half = 10  
[1,2,3,4] = 10  
[5,5] = 10
```

---

### Example 2

```
Input: arr = [4, 3, 2, 1]
Output: false

Explanation:
No split gives equal sum
```

---

## ⚡ Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)



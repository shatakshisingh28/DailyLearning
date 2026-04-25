

# ⚔️ Array Reduction with Opposite Signs

## 📌 Problem Statement

Given an integer array `arr[]`, repeatedly apply the following operation **from left to right** until no more valid operations can be performed:

### 🔁 Operation Rules

If two **adjacent elements have opposite signs**:

* If their **absolute values are different**:

  * Remove both elements
  * Insert the one with the **greater absolute value** (keep its sign)
* If their **absolute values are equal**:

  * Remove both elements
  * Do **not** insert anything

---

## 🎯 Goal

Return the **final array** after applying all possible operations.

---

## 🧠 Approach (Stack-Based)

👉 This behaves like a **collision problem** (similar to asteroid collision)

* Traverse the array from left to right
* Use a **stack** to keep track of elements
* For each element:

  * Compare with the top of stack
  * If signs are opposite → apply rules
  * Continue until no more collisions possible

---

## ⚙️ Algorithm

1. Initialize an empty stack
2. Iterate through array:

   * Push element if no conflict
   * If conflict (opposite signs):

     * Compare absolute values
     * Remove/replace accordingly
     * Repeat until stable
3. Convert stack to array and return

---

## 💻 Java Implementation

```java


import java.util.*;

class Solution {
    public ArrayList<Integer> reducePairs(int[] arr) {
        Stack<Integer> stack = new Stack<>();

        for (int num : arr) {
            
            while (!stack.isEmpty() && stack.peek() * num < 0) {
                int top = stack.peek();

                if (Math.abs(top) > Math.abs(num)) {
                    num = top; // keep bigger
                } else if (Math.abs(top) == Math.abs(num)) {
                    num = 0; // both removed
                }

                stack.pop(); // remove top

                if (num == 0) break;
            }

            if (num != 0) {
                stack.push(num);
            }
        }

        return new ArrayList<>(stack);
    }
}
```

---

## 🧪 Examples

### Example 1

```
Input: arr = [5, -3]
Output: [5]

Explanation:
|5| > |3| → keep 5
```

---

### Example 2

```
Input: arr = [4, -4]
Output: []

Explanation:
|4| = |4| → both removed
```

---

### Example 3

```
Input: arr = [3, 2, -5]
Output: [-5]

Explanation:
2 vs -5 → remove 2  
3 vs -5 → remove 3  
Remaining → [-5]
```

---

## ⚡ Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(n) (stack)

---

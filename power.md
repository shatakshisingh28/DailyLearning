# 🔢 Check if y is a Power of x
## 📌 Problem Statement

Given two positive integers x and y, determine whether y is a power of x.

Return:

true → if y = x^k for some integer k ≥ 0

false → otherwise
## 🧠 Approach

We repeatedly divide y by x:

If at any step y is not divisible by x, it is not a power.

If we eventually reach 1, then y is a power of x.

## ⚙️ Algorithm

Handle edge cases:

If y == 1 → return true

If x == 1 → return y == 1

While y % x == 0:

Divide y by x

If final value of y == 1 → return true

Else → return false

## 💻 Java Implementation
``` java
class Solution {
    public boolean isPower(int x, int y) {
        if (y == 1) return true;
        if (x == 1) return y == 1;

        while (y % x == 0) {
            y = y / x;
        }

        return y == 1;
    }
}
```
## 🧪 Examples
Example 1
Input: x = 2, y = 8
Output: true
Explanation: 8 = 2^3
Example 2
Input: x = 3, y = 12
Output: false
Explanation: 12 is not a power of 3
Example 3
Input: x = 5, y = 1
Output: true
Explanation: 1 = 5^0
## ⚡ Time Complexity
O(logₓ y)
## 🗂️ Space Complexity
O(1)

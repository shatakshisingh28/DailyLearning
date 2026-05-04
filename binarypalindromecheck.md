# Binary Palindrome Check

## 🧩 Problem Statement
Given an integer `n`, determine whether its binary representation forms a palindrome.

A binary representation is considered a palindrome if it reads the same forward and backward.

---

## 📌 Examples

### Example 1
**Input:**  
n = 17  

**Binary:**  
10001  

**Output:**  
true  

---

### Example 2
**Input:**  
n = 16  

**Binary:**  
10000  

**Output:**  
false  

---

## 🚀 Approach

1. Convert the integer into its binary representation using:
```

Integer.toBinaryString(n)

```
2. Use two pointers:
- One at the start
- One at the end
3. Compare characters:
- If mismatch → not a palindrome
- If all match → palindrome

---
# 📄 `Solution.java`

```java
class Solution {
    public boolean isBinaryPalindrome(int n) {
        // Convert number to binary string
        String binary = Integer.toBinaryString(n);

        int left = 0, right = binary.length() - 1;

        // Check if palindrome
        while (left < right) {
            if (binary.charAt(left) != binary.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }

        return true;
    }
}
```
## 💡 Code Explanation

- We convert the number into a binary string.
- Then we check if the string is a palindrome using two pointers.

## ⏱️ Complexity

| Type        | Complexity |
|------------|-----------|
| Time       | O(log n)  |
| Space      | O(log n)  |



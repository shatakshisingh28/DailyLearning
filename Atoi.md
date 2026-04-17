# 🔢 String to Integer (atoi) – Java

## 📌 Problem

Implement a function that converts a string to a **32-bit signed integer** (like `atoi`) without using built-in conversion methods.

---

## 📜 Rules

1. **Ignore Leading Whitespaces**
2. **Check Sign**

   * `'+'` → positive
   * `'-'` → negative
3. **Read Digits**

   * Stop at first non-digit character
   * If no digits found → return `0`
4. **Handle Overflow**

   * If value > `2147483647` → return `2147483647`
   * If value < `-2147483648` → return `-2147483648`

---

## 💡 Approach

* Traverse the string
* Skip spaces
* Detect sign
* Build number digit by digit
* Check overflow **before updating result**

---

## ✅ Java Implementation

```java id="9v7s0j"
class Solution {
    public int myAtoi(String s) {
        int i = 0, n = s.length();
        
        // 1. Skip leading spaces
        while (i < n && s.charAt(i) == ' ') {
            i++;
        }
        
        // 2. Check sign
        int sign = 1;
        if (i < n && (s.charAt(i) == '+' || s.charAt(i) == '-')) {
            sign = (s.charAt(i) == '-') ? -1 : 1;
            i++;
        }
        
        // 3. Convert digits
        int result = 0;
        
        while (i < n && Character.isDigit(s.charAt(i))) {
            int digit = s.charAt(i) - '0';
            
            // 4. Handle overflow
            if (result > (Integer.MAX_VALUE - digit) / 10) {
                return (sign == 1) ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }
            
            result = result * 10 + digit;
            i++;
        }
        
        return result * sign;
    }
}
```

---

## ⚡ Complexity

* Time Complexity: **O(n)**
* Space Complexity: **O(1)**

---


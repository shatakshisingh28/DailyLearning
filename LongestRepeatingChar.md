# 🔠 Longest Repeating Character Replacement

## 📌 Problem Statement

Given a string `s` consisting of uppercase English letters and an integer `k`, you can perform at most `k` operations.

In one operation, you can change any character to any other uppercase letter.

Return the **length of the longest substring** that can be converted into a string with all identical characters using at most `k` operations.

---

## 🧾 Examples

### Example 1

```text
Input: s = "ABBA", k = 2
Output: 4
```

**Explanation:**
Change both `'A'` → `'B'` → `"BBBB"` → length = 4

---

### Example 2

```text
Input: s = "ADBD", k = 1
Output: 3
```

**Explanation:**
Change `'B'` → `'D'` → `"ADDD"` → substring `"DDD"` → length = 3

---

## 🚀 Approach (Sliding Window + Frequency Count)

### 💡 Key Idea

To make all characters in a substring the same:

* We only need to replace the **non-most-frequent characters**

👉 So, for a window:

```
changes needed = window size - max frequency character
```

If:

```
(window size - maxFreq) <= k
```

✅ Valid window
❌ Otherwise shrink the window

---

## 🧠 Algorithm Steps

1. Use a frequency array of size 26
2. Maintain:

   * `left` pointer
   * `maxFreq` → frequency of most common character in window
3. Expand window using `right`
4. If window becomes invalid:

   * shrink from left
5. Track maximum window size

---

## 💻 Java Implementation

```java
class Solution {
    public int characterReplacement(String s, int k) {
        int[] freq = new int[26];
        int left = 0, maxFreq = 0, maxLen = 0;

        for (int right = 0; right < s.length(); right++) {
            int idx = s.charAt(right) - 'A';
            freq[idx]++;
            
            // Track max frequency in current window
            maxFreq = Math.max(maxFreq, freq[idx]);

            // If more than k replacements needed → shrink window
            while ((right - left + 1) - maxFreq > k) {
                freq[s.charAt(left) - 'A']--;
                left++;
            }

            maxLen = Math.max(maxLen, right - left + 1);
        }

        return maxLen;
    }
}
```

---

## 🔍 Example Walkthrough

### Input: `"ADBD"`, k = 1

| Window | MaxFreq | Changes Needed | Valid |
| ------ | ------- | -------------- | ----- |
| ADB    | 1       | 2              | ❌     |
| DBD    | 2       | 1              | ✅     |

Max length = **3**

---

## ⏱️ Complexity Analysis

| Type  | Complexity |
| ----- | ---------- |
| Time  | O(n)       |
| Space | O(1)       |


# 🔍 Smallest Substring Containing '0', '1', and '2'

## 📌 Problem Statement

Given a string `s` consisting only of characters `'0'`, `'1'`, and `'2'`, find the **length of the smallest substring** that contains all three characters at least once.

If no such substring exists, return `-1`.

---

## 🧾 Examples

### Example 1

```
Input: s = "10212"
Output: 3
```

**Explanation:**
The substring `"102"` contains all three characters `'0'`, `'1'`, and `'2'`, and is the shortest such substring.

---

### Example 2

```
Input: s = "12121"
Output: -1
```

**Explanation:**
Character `'0'` is missing, so no valid substring exists.

---

## 🚀 Approach (Sliding Window)

We use the **Sliding Window Technique**:

* Maintain two pointers: `left` and `right`
* Expand the window using `right`
* Track frequency of `'0'`, `'1'`, `'2'`
* When all 3 are present:

  * Update minimum length
  * Shrink window from `left`

---

## 🧠 Algorithm Steps

1. Initialize:

   * `freq[3]` → frequency array
   * `count` → number of unique characters present
   * `minLen` → store minimum length

2. Traverse string using `right` pointer:

   * Add current character to window
   * Update `count` if new character appears

3. When `count == 3`:

   * Update `minLen`
   * Remove characters from `left` to shrink window

4. Return:

   * `minLen` if found
   * Otherwise `-1`

---

## 💻 Java Implementation

```java
class Solution {
    public int smallestSubstring(String s) {
        int n = s.length();
        int[] freq = new int[3];
        int left = 0, count = 0, minLen = Integer.MAX_VALUE;

        for (int right = 0; right < n; right++) {
            int idx = s.charAt(right) - '0';

            if (freq[idx] == 0) {
                count++;
            }
            freq[idx]++;

            while (count == 3) {
                minLen = Math.min(minLen, right - left + 1);

                int leftIdx = s.charAt(left) - '0';
                freq[leftIdx]--;

                if (freq[leftIdx] == 0) {
                    count--;
                }
                left++;
            }
        }

        return minLen == Integer.MAX_VALUE ? -1 : minLen;
    }
}
```

---

## ⏱️ Complexity Analysis

| Type  | Complexity |
| ----- | ---------- |
| Time  | O(n)       |
| Space | O(1)       |

---

## 🎯 Key Concepts

* Sliding Window
* Two Pointer Technique
* Frequency Counting

---

## ✨ Summary

* Efficient way to solve substring problems
* Avoids brute force (O(n²))
* Works in linear time

---

## 📚 Tags

`Sliding Window` `Two Pointers` `Strings` `Hashing`

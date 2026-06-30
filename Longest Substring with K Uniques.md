# Longest Substring with Exactly K Distinct Characters (Sliding Window + HashMap)

## Problem Statement

Given a string `s` consisting of lowercase alphabets and an integer `k`, find the length of the **longest substring** that contains **exactly `k` distinct characters**.

If no such substring exists, return **-1**.

### Example

**Input**

```text
s = "aabacbebebe"
k = 3
```

**Output**

```text
7
```

**Explanation**

The longest substring having exactly **3 distinct characters** is:

```text
cbebebe
```

It contains the characters:

```text
c, b, e
```

Length = **7**

---

# Approach

This problem is solved using the **Sliding Window** technique.

We maintain a window using two pointers:

* `left` → Start of the window
* `right` → End of the window

A **HashMap** stores the frequency of characters inside the current window.

### Steps

1. Expand the window by moving `right`.
2. Add the current character to the HashMap.
3. If the number of distinct characters becomes greater than `k`, shrink the window from the left.
4. When the window has exactly `k` distinct characters, update the maximum length.
5. Continue until the end of the string.

---

# Java Code

```java
import java.util.*;

class Solution {

    public static int longestKSubstr(String s, int k) {

        int left = 0;
        int maxLen = -1;

        HashMap<Character, Integer> map = new HashMap<>();

        for (int right = 0; right < s.length(); right++) {

            char ch = s.charAt(right);

            map.put(ch, map.getOrDefault(ch, 0) + 1);

            while (map.size() > k) {

                char leftChar = s.charAt(left);

                map.put(leftChar, map.get(leftChar) - 1);

                if (map.get(leftChar) == 0) {
                    map.remove(leftChar);
                }

                left++;
            }

            if (map.size() == k) {
                maxLen = Math.max(maxLen, right - left + 1);
            }
        }

        return maxLen;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the string: ");
        String s = sc.next();

        System.out.print("Enter k: ");
        int k = sc.nextInt();

        int ans = longestKSubstr(s, k);

        System.out.println("Longest Length = " + ans);

        sc.close();
    }
}
```

---

# Dry Run

### Input

```text
s = "aabacbebebe"
k = 3
```

| Left | Right | Current Window | Distinct Characters | Maximum Length |
| ---- | ----- | -------------- | ------------------- | -------------: |
| 0    | 0     | a              | 1                   |             -1 |
| 0    | 1     | aa             | 1                   |             -1 |
| 0    | 2     | aab            | 2                   |             -1 |
| 0    | 3     | aaba           | 2                   |             -1 |
| 0    | 4     | aabac          | 3                   |              5 |
| 2    | 5     | bacb           | 3                   |              5 |
| 2    | 6     | bacbe          | 4 → Shrink          |              5 |
| 4    | 6     | cbe            | 3                   |              5 |
| 4    | 7     | cbeb           | 3                   |              5 |
| 4    | 8     | cbebe          | 3                   |              5 |
| 4    | 9     | cbebeb         | 3                   |              6 |
| 4    | 10    | cbebebe        | 3                   |          **7** |

Final Answer:

```text
7
```

---

# Code Explanation

## Step 1: Initialize Variables

```java
int left = 0;
int maxLen = -1;
```

* `left` represents the start of the sliding window.
* `maxLen` stores the maximum valid substring length.

---

## Step 2: Create a HashMap

```java
HashMap<Character, Integer> map = new HashMap<>();
```

The HashMap stores the frequency of characters inside the current window.

Example:

```text
Window = aabac

Map

a → 3
b → 1
c → 1
```

---

## Step 3: Expand the Window

```java
for (int right = 0; right < s.length(); right++)
```

Move the `right` pointer one step at a time.

---

## Step 4: Add the Current Character

```java
char ch = s.charAt(right);

map.put(ch, map.getOrDefault(ch, 0) + 1);
```

Example:

```text
Window = aab

Map

a → 2
b → 1
```

---

## Step 5: Shrink the Window if Needed

```java
while (map.size() > k)
```

If the number of distinct characters becomes greater than `k`, move the `left` pointer until only `k` distinct characters remain.

---

## Step 6: Decrease Frequency

```java
char leftChar = s.charAt(left);

map.put(leftChar, map.get(leftChar) - 1);
```

Decrease the frequency of the leftmost character.

---

## Step 7: Remove Character if Frequency Becomes Zero

```java
if (map.get(leftChar) == 0) {
    map.remove(leftChar);
}
```

If a character is no longer present in the window, remove it from the HashMap.

---

## Step 8: Move the Left Pointer

```java
left++;
```

Shrink the window from the left.

---

## Step 9: Update the Answer

```java
if (map.size() == k) {
    maxLen = Math.max(maxLen, right - left + 1);
}
```

If the window contains exactly `k` distinct characters, calculate its length and update the answer.

Window Length:

```text
right - left + 1
```

---

## Step 10: Return the Result

```java
return maxLen;
```

If no substring with exactly `k` distinct characters exists, `maxLen` remains `-1`.

---

# Example

Input

```text
Enter the string: aabacbebebe
Enter k: 3
```

Output

```text
Longest Length = 7
```

---

# Time Complexity

Each character enters and leaves the sliding window at most once.

```text
O(n)
```

where `n` is the length of the string.

---

# Space Complexity

The HashMap stores at most `k` distinct characters (or at most 26 lowercase letters).

```text
O(k)
```

For lowercase English letters, this is effectively:

```text
O(1)
```

---

# Key Takeaways

* Use **Sliding Window** to maintain a valid substring.
* Use a **HashMap** to count character frequencies.
* Expand the window using the `right` pointer.
* Shrink the window using the `left` pointer when distinct characters exceed `k`.
* Update the answer only when the window contains **exactly `k` distinct characters**.

## One-Line Summary

> **Maintain a sliding window with exactly `k` distinct characters using a HashMap, and keep track of the maximum window length.**

# Minimum String Value After Removing K Characters

## Problem Statement

Given a string `s` consisting of lowercase alphabets and an integer `k`, remove exactly `k` characters such that the value of the string is minimized.

The value of a string is defined as:

```text
Sum of squares of frequencies of all distinct characters
```

### Example 1

**Input:**

```text
s = "abccc"
k = 1
```

**Output:**

```text
6
```

**Explanation:**

Initial frequencies:

```text
a → 1
b → 1
c → 3
```

Remove one `'c'`:

```text
a → 1
b → 1
c → 2
```

Value:

```text
1² + 1² + 2²
= 1 + 1 + 4
= 6
```

---

### Example 2

**Input:**

```text
s = "aaab"
k = 2
```

**Output:**

```text
2
```

**Explanation:**

Initial frequencies:

```text
a → 3
b → 1
```

Remove two `'a'` characters:

```text
a → 1
b → 1
```

Value:

```text
1² + 1²
= 2
```

---

## Approach

### Key Observation

To minimize the final value, we should always remove a character from the character having the **highest frequency**.

Why?

Because decreasing a larger frequency gives a greater reduction in the square value.

Example:

```text
5² = 25
4² = 16
Reduction = 9
```

while

```text
2² = 4
1² = 1
Reduction = 3
```

Therefore, repeatedly reducing the maximum frequency leads to the minimum possible value.

---

## Algorithm

### Step 1

Count the frequency of each character using a `HashMap`.

### Step 2

Repeat `k` times:

* Find the character with maximum frequency.
* Decrease its frequency by 1.

### Step 3

Calculate:

```text
Σ(freq × freq)
```

for all remaining frequencies.

---

## Java Solution

```java
class Solution {
    int minValue(String s, int k) {

        HashMap<Character, Integer> map = new HashMap<>();

        for(int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            map.put(c, map.getOrDefault(c, 0) + 1);
        }

        while(k > 0) {

            char maxChar = ' ';
            int maxFreq = -1;

            for(Map.Entry<Character, Integer> entry : map.entrySet()) {

                if(entry.getValue() > maxFreq) {
                    maxFreq = entry.getValue();
                    maxChar = entry.getKey();
                }
            }

            if(maxFreq <= 0)
                break;

            map.put(maxChar, maxFreq - 1);

            k--;
        }

        int ans = 0;

        for(int freq : map.values()) {
            ans += freq * freq;
        }

        return ans;
    }
}
```

---

## Dry Run

### Input

```text
s = "abccc"
k = 1
```

### Frequency Map

```text
a → 1
b → 1
c → 3
```

### Iteration 1

Maximum frequency:

```text
c → 3
```

Reduce by 1:

```text
c → 2
```

Updated map:

```text
a → 1
b → 1
c → 2
```

### Calculate Answer

```text
1² + 1² + 2²
= 1 + 1 + 4
= 6
```

### Output

```text
6
```

---

## Time Complexity

Let:

```text
n = length of string
```

### Frequency Counting

```text
O(n)
```

### Finding Maximum Frequency

For every removal:

```text
O(26)
```

Since only lowercase English letters exist.

Repeated `k` times:

```text
O(26 × k)
```

Which simplifies to:

```text
O(k)
```

### Overall

```text
O(n + k)
```

---

## Space Complexity

HashMap stores frequencies of characters.

```text
O(26)
```

or

```text
O(1)
```

for lowercase English alphabets.

---

## Key Concepts Used

* HashMap
* Greedy Strategy
* Frequency Counting
* String Traversal
* Mathematical Optimization

---

## Why the Greedy Approach Works

At every step, removing one occurrence from the highest-frequency character produces the largest decrease in the total value.

Therefore:

```text
Always decrease the maximum frequency first.
```

This guarantees the minimum possible string value after removing `k` characters.


# Count Binary Substrings Starting and Ending with 1

## Problem Statement

Given a binary string `s` consisting of only `0`s and `1`s, count the number of substrings that start and end with `1`.

### Example

**Input:**

```text
s = "1111"
```

**Output:**

```text
6
```

**Explanation:**

The positions of `1`s are:

```text
1 1 1 1
```

Choosing any two `1`s forms a valid substring that starts and ends with `1`.

Possible pairs:

```text
(1,2)
(1,3)
(1,4)
(2,3)
(2,4)
(3,4)
```

Total = 6 substrings.

---

## Approach

### Key Observation

If there are `n` occurrences of `1` in the string, then every valid substring can be formed by choosing any two positions containing `1`.

The number of ways to choose 2 positions from `n` positions is:

```text
nC2 = n × (n - 1) / 2
```

Thus:

1. Count the number of `1`s in the string.
2. Apply the formula:

```java
ones * (ones - 1) / 2
```

3. Return the result.

---

## Java Solution

```java
class Solution {
    public int binarySubstring(String s) {
        
        int ones = 0;
        
        for(char c : s.toCharArray()) {
            if(c == '1')
                ones++;
        }
        
        return ones * (ones - 1) / 2;
    }
}
```

---

## Dry Run

### Input

```text
s = "10101"
```

### Count Ones

```text
1 0 1 0 1
↑   ↑   ↑

ones = 3
```

### Apply Formula

```text
3 × (3 - 1) / 2
= 3 × 2 / 2
= 3
```

### Output

```text
3
```

---

## Time Complexity

Counting `1`s requires one traversal of the string.

```text
O(n)
```

where `n` is the length of the string.

---

## Space Complexity

Only one variable is used.

```text
O(1)
```

---

## Key Concepts

* String Traversal
* Character Counting
* Combinations (nC2)
* Mathematical Optimization


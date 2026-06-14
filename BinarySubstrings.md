# Count Binary Substrings Starting and Ending with 1

## Problem Statement

Given a binary string `s` consisting of only `'0'` and `'1'`, count the number of substrings that start and end with `'1'`.

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

Possible substrings starting and ending with `1`:

```text
(1,2)
(1,3)
(1,4)
(2,3)
(2,4)
(3,4)
```

Total = **6**

---

## Key Observation

If a string contains `n` occurrences of `'1'`, then every valid substring can be formed by choosing any **two positions containing '1'**.

This becomes a simple combination problem:

```text
Number of ways = nC2
```

Formula:

```text
nC2 = n × (n - 1) / 2
```

where `n` is the count of `'1'` characters.

---

## Approach

### Step 1

Count the number of `'1'`s in the string.

### Step 2

Apply the combination formula:

```text
ones × (ones - 1) / 2
```

### Step 3

Return the result.

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

Valid substrings:

```text
101
10101
101
```

---

## Another Example

### Input

```text
s = "1111"
```

### Count Ones

```text
ones = 4
```

### Calculate

```text
4 × 3 / 2
= 6
```

### Output

```text
6
```

---

## Time Complexity

The string is traversed once.

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

## Why This Works

Every valid substring must:

* Start with `'1'`
* End with `'1'`

So instead of generating all substrings, we simply count how many pairs of `'1'` positions exist.

If there are:

```text
n = 4 ones
```

Possible pairs:

```text
(1,2)
(1,3)
(1,4)
(2,3)
(2,4)
(3,4)
```

Which equals:

```text
4C2 = 6
```

---

## Key Concepts Used

* String Traversal
* Character Counting
* Combinatorics (nC2)
* Mathematical Optimization

---

## Advantages

✅ Optimal Time Complexity

✅ Constant Extra Space

✅ No Need to Generate Substrings

✅ Simple and Elegant Solution




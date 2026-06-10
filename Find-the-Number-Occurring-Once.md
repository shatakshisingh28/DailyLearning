# Find the Number Occurring Once

## Problem Statement

Given an unsorted array `arr[]` of positive integers where every element appears exactly twice except for one element that appears only once, find the element that occurs only once.

---

## Example

### Input

```text
arr[] = [1, 2, 1, 5, 5]
```

### Output

```text
2
```

### Explanation

* `1` occurs twice.
* `5` occurs twice.
* `2` occurs only once.

Therefore, the answer is:

```text
2
```

---

## Approach

We can efficiently solve this problem using the **XOR (^) operator**.

### XOR Properties

```text
a ^ a = 0
a ^ 0 = a
```

Since every number except one appears twice:

```text
1 ^ 2 ^ 1 ^ 5 ^ 5
```

Rearranging:

```text
(1 ^ 1) ^ (5 ^ 5) ^ 2
```

```text
0 ^ 0 ^ 2
```

```text
2
```

The duplicate numbers cancel out, leaving only the unique number.

---

## Algorithm

1. Initialize `xor = 0`.
2. Traverse the array.
3. XOR each element with `xor`.
4. Return the final value of `xor`.

---

## Java Solution

```java
class Solution {
    public int findUnique(int[] arr) {

        int xor = 0;

        for (int num : arr) {
            xor ^= num;
        }

        return xor;
    }
}
```

---

## Dry Run

### Input

```text
arr = [1, 2, 1, 5, 5]
```

### Execution

```text
xor = 0

xor = 0 ^ 1 = 1
xor = 1 ^ 2 = 3
xor = 3 ^ 1 = 2
xor = 2 ^ 5 = 7
xor = 7 ^ 5 = 2
```

### Result

```text
2
```

---

## Complexity Analysis

### Time Complexity

```text
O(n)
```

We traverse the array once.

### Space Complexity

```text
O(1)
```

Only one extra variable is used.

---

## Key Insight

Using XOR allows duplicate elements to cancel each other out automatically, leaving only the element that appears once.

```text
Duplicate ^ Duplicate = 0
```

Hence, XOR is the most optimal solution for this problem.

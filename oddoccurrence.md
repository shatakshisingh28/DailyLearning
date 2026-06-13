# Find the Number with Odd Occurrence

## Problem Statement

Given an array of positive integers where every element occurs an even number of times except one element, which occurs an odd number of times, find and return that element.

### Example

**Input:**

```text
arr[] = [1, 2, 3, 2, 3, 1, 3]
```

**Output:**

```text
3
```

**Explanation:**

* 1 occurs 2 times (even)
* 2 occurs 2 times (even)
* 3 occurs 3 times (odd)

Therefore, the answer is:

```text
3
```

---

## Approach

This problem can be solved efficiently using the **XOR (^) operator**.

### XOR Properties

```text
a ^ a = 0
```

A number XORed with itself becomes 0.

```text
a ^ 0 = a
```

A number XORed with 0 remains unchanged.

Because all numbers except one appear an even number of times, all paired numbers cancel each other out when XORed together.

The remaining value is the number with odd occurrence.

---

## Java Solution

```java
class Solution {
    // Method to find the element with odd occurrence in given array
    int getOddOccurrence(int[] arr) {

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
[1, 2, 3, 2, 3, 1, 3]
```

### XOR Operations

Initial:

```text
xor = 0
```

Step 1:

```text
xor = 0 ^ 1 = 1
```

Step 2:

```text
xor = 1 ^ 2 = 3
```

Step 3:

```text
xor = 3 ^ 3 = 0
```

Step 4:

```text
xor = 0 ^ 2 = 2
```

Step 5:

```text
xor = 2 ^ 3 = 1
```

Step 6:

```text
xor = 1 ^ 1 = 0
```

Step 7:

```text
xor = 0 ^ 3 = 3
```

Final:

```text
xor = 3
```

### Output

```text
3
```

---

## Why XOR Works

Consider:

```text
1 ^ 1 = 0
2 ^ 2 = 0
3 ^ 3 = 0
```

All numbers occurring an even number of times cancel out.

Only the number with odd occurrence remains.

```text
1 ^ 2 ^ 3 ^ 2 ^ 3 ^ 1 ^ 3
= 3
```

---

## Time Complexity

The array is traversed once.

```text
O(n)
```

where `n` is the size of the array.

---

## Space Complexity

Only one variable (`xor`) is used.

```text
O(1)
```

---

## Advantages of This Approach

✅ Single traversal of the array

✅ Constant extra space

✅ No HashMap required

✅ Optimal solution

---

## Key Concepts Used

* Bit Manipulation
* XOR Operator (`^`)
* Array Traversal
* Space Optimization



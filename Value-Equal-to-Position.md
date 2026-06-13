# Value Equal to Position

## Problem Statement

Given an array of integers, find all elements whose value is equal to their **1-based position (index)** in the array.

Return all such elements in an `ArrayList`.

### Example

**Input:**

```text
arr[] = [15, 2, 45, 4, 7]
```

**Output:**

```text
[2, 4]
```

**Explanation:**

| Position (1-based) | Value |
| ------------------ | ----- |
| 1                  | 15    |
| 2                  | 2 ✅   |
| 3                  | 45    |
| 4                  | 4 ✅   |
| 5                  | 7     |

Since the values at positions 2 and 4 are equal to their positions, the answer is:

```text
[2, 4]
```

---

## Approach

The array uses **0-based indexing**, but the problem asks us to compare values with their **1-based positions**.

Therefore:

* Position 1 corresponds to `arr[0]`
* Position 2 corresponds to `arr[1]`
* Position 3 corresponds to `arr[2]`
* and so on...

Traverse the array and check:

```text
Position == Value
```

If true, add the value to the result list.

---

## Java Solution

```java
class Solution {
    public static ArrayList<Integer> valEqualToPos(int[] arr) {

        ArrayList<Integer> result = new ArrayList<>();

        for (int i = 1; i <= arr.length; i++) {

            if (i == arr[i - 1]) {
                result.add(i);
            }
        }

        return result;
    }
}
```

---

## Dry Run

### Input

```text
arr[] = [15, 2, 45, 4, 7]
```

### Iteration 1

```text
Position = 1
Value = 15

1 == 15 ❌
```

Result:

```text
[]
```

---

### Iteration 2

```text
Position = 2
Value = 2

2 == 2 ✅
```

Result:

```text
[2]
```

---

### Iteration 3

```text
Position = 3
Value = 45

3 == 45 ❌
```

Result:

```text
[2]
```

---

### Iteration 4

```text
Position = 4
Value = 4

4 == 4 ✅
```

Result:

```text
[2, 4]
```

---

### Iteration 5

```text
Position = 5
Value = 7

5 == 7 ❌
```

Final Result:

```text
[2, 4]
```

---

## Time Complexity

The array is traversed exactly once.

```text
O(n)
```

where `n` is the size of the array.

---

## Space Complexity

The extra space used is for storing the answer.

```text
O(k)
```

where `k` is the number of matching elements.

In the worst case:

```text
O(n)
```

---

## Key Concepts Used

* Arrays
* Array Traversal
* 0-Based Indexing
* 1-Based Position Comparison
* ArrayList

---

## Edge Cases

### No Matching Elements

**Input:**

```text
[10, 20, 30]
```

**Output:**

```text
[]
```

---

### All Matching Elements

**Input:**

```text
[1, 2, 3, 4, 5]
```

**Output:**

```text
[1, 2, 3, 4, 5]
```



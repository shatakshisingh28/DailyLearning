
# Minimum Product of k Elements

## Problem Statement
Given an array `arr[]` of positive integers and an integer `k`, find the minimum possible product of any `k` elements from the array.

Since the product can be very large, return the answer modulo **10^9 + 7**.

---

## Example 1

### Input
```text
arr[] = [1, 2, 3, 4, 5]
k = 2
```

### Output
```text
2
```

### Explanation
The minimum product is obtained by multiplying the two smallest elements:

```text
1 × 2 = 2
```

---

## Example 2

### Input
```text
arr[] = [9, 10, 8]
k = 3
```

### Output
```text
720
```

### Explanation
Since `k = 3`, all elements must be selected.

```text
9 × 10 × 8 = 720
```

---

## Approach

Since all elements are positive integers:

- The minimum product is obtained by choosing the `k` smallest elements.
- Sort the array in ascending order.
- Multiply the first `k` elements.
- Take modulo `10^9 + 7` after every multiplication.

---

## Algorithm

1. Sort the array.
2. Initialize `product = 1`.
3. Traverse the first `k` elements.
4. Multiply them with `product`.
5. Return `product % (10^9 + 7)`.

---

## Java Solution

```java
import java.util.Arrays;

class Solution {

    int minProduct(int arr[], int k) {
        // code here
        Arrays.sort(arr);

        long mod = (int)1e9 + 7;
        if (k > arr.length) {
            k = arr.length; 
        }
        long product = 1;

        for (int i = 0; i < k; i++) {
            product = (product * arr[i]) % mod;
        }

        return (int) product;
    }
}
```

---

## Dry Run

### Input
```text
arr[] = [5, 1, 4, 2, 3]
k = 3
```

### Step 1: Sort Array

```text
[1, 2, 3, 4, 5]
```

### Step 2: Multiply First k Elements

```text
product = 1

product = 1 × 1 = 1
product = 1 × 2 = 2
product = 2 × 3 = 6
```

### Final Answer

```text
6
```

---

## Complexity Analysis

### Time Complexity
```text
O(n log n)
```

(Sorting the array)

### Auxiliary Space
```text
O(1)
```

(Excluding sorting space used internally)

---
````

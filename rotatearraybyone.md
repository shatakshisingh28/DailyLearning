
# Rotate Array by One

## Problem Statement
Given an array `arr[]`, rotate the array by one position in clockwise direction.

This means:

- The last element moves to the first position.

- All other elements shift one position to the right.

---

## Example 1

### Input
```text
arr[] = [1, 2, 3, 4, 5]
````

### Output

```text
[5, 1, 2, 3, 4]
```

### Explanation

* `5` moves to the front.
* Remaining elements shift right by one position.

---

## Example 2

### Input

```text
arr[] = [9, 8, 7, 6, 4, 2, 1, 3]
```

### Output

```text
[3, 9, 8, 7, 6, 4, 2, 1]
```

---

# Approach

1. Store the last element of the array.
2. Shift all elements one position to the right.
3. Place the stored last element at index `0`.

---

# Time Complexity

* **O(n)**

# Auxiliary Space

* **O(1)**

---

# Java Solution

```java
class Solution {
    public void rotate(int[] arr) {
        int n = arr.length;

        // Store last element
        int last = arr[n - 1];

        // Shift elements to the right
        for (int i = n - 1; i > 0; i--) {
            arr[i] = arr[i - 1];
        }

        // Place last element at first position
        arr[0] = last;
    }
}
```

---

# Dry Run

### Input

```text
arr[] = [1, 2, 3, 4, 5]
```

### Step 1

Store last element:

```text
last = 5
```

### Step 2

Shift elements right:

```text
[1, 1, 2, 3, 4]
```

### Step 3

Place last at front:

```text
[5, 1, 2, 3, 4]
```

### Final Output

```text
[5, 1, 2, 3, 4]
```

---

```
```

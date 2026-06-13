# Segregate Even and Odd Numbers in an Array

## Problem Statement

Given an array of integers, rearrange the elements such that all **even numbers** appear first, followed by all **odd numbers**.

### Example

**Input:**

```text
[1, 2, 3, 4, 5, 6]
```

**Output:**

```text
[2, 4, 6, 1, 3, 5]
```

---

## Approach

### Step 1: Sort the Array

First, sort the array in ascending order using `Arrays.sort()`.

### Step 2: Separate Even and Odd Numbers

Traverse the sorted array:

* If the number is even, store it in the `even` list.
* If the number is odd, store it in the `odd` list.

### Step 3: Rebuild the Array

Copy all elements from the `even` list into the original array, followed by all elements from the `odd` list.

---

## Java Solution

```java
class Solution {
    void segregateEvenOdd(int arr[]) {
        Arrays.sort(arr);

        ArrayList<Integer> odd = new ArrayList<>();
        ArrayList<Integer> even = new ArrayList<>();

        for (int i : arr) {
            if (i % 2 == 0) {
                even.add(i);
            } else {
                odd.add(i);
            }
        }

        int j = 0;

        for (int i : even) {
            arr[j++] = i;
        }

        for (int i : odd) {
            arr[j++] = i;
        }
    }
}
```

---

## Dry Run

### Input

```text
[5, 2, 8, 1, 7, 4]
```

### After Sorting

```text
[1, 2, 4, 5, 7, 8]
```

### Separate Elements

**Even List:**

```text
[2, 4, 8]
```

**Odd List:**

```text
[1, 5, 7]
```

### Rebuild Array

```text
[2, 4, 8, 1, 5, 7]
```

### Final Output

```text
[2, 4, 8, 1, 5, 7]
```

---

## Time Complexity

### Sorting

```text
O(n log n)
```

### Traversing Array

```text
O(n)
```

### Copying Elements Back

```text
O(n)
```

### Overall Time Complexity

```text
O(n log n)
```

---

## Space Complexity

Two additional ArrayLists are used:

```text
O(n)
```

---

## Key Concepts Used

* Arrays Sorting (`Arrays.sort`)
* ArrayList
* Enhanced For Loop
* Even/Odd Checking using Modulus Operator (`%`)
* Array Manipulation

---

## Notes

* The solution ensures all even numbers come before odd numbers.
* Numbers within each group remain in sorted order because the array is sorted before segregation.
* Extra space is used to store even and odd elements separately.

```
```

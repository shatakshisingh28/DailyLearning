# Why is Melody so chocolaty - Solution

## Problem Statement
Given an array `arr[]`, each element represents the happiness Chunky gets by eating a melody.  
Find the maximum happiness Chunky can get by eating **two adjacent melodies**.

---

## Approach
- Traverse the array.
- For every adjacent pair, calculate their sum.
- Keep track of the maximum sum found.

### Time Complexity
- **O(n)**

### Auxiliary Space
- **O(1)**

---

## Java Solution

```java
class Solution {
    public int maxAdjacent(int[] arr) {
        int maxSum = Integer.MIN_VALUE;

        for (int i = 0; i < arr.length - 1; i++) {
            maxSum = Math.max(maxSum, arr[i] + arr[i + 1]);
        }

        return maxSum;
    }
}

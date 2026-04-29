# Minimum Swaps to Group All 1s Together

## 🧩 Problem Statement
You are given a binary array `arr[]` consisting only of `0`s and `1`s.  
Your task is to determine the **minimum number of swaps** required to group all the `1`s together in a contiguous subarray.

A swap operation allows you to swap any two elements in the array.

If the array contains no `1`s, return `-1`.

---

## 💡 Approach (Sliding Window)

### Key Idea:
- Count total number of `1`s → let it be `k`
- We need a window of size `k` where all `1`s can fit
- In each window, count how many `0`s are present
- Minimum number of `0`s in any window = minimum swaps required

---

## 🚀 Algorithm Steps
1. Count total number of `1`s (`k`)
2. If `k == 0`, return `-1`
3. Create a sliding window of size `k`
4. Count number of `0`s in the first window
5. Slide the window across the array:
   - Remove left element
   - Add right element
   - Update zero count
6. Return the minimum zero count found

---

## ✅ Java Implementation

```java
class Solution {
    public int minSwaps(int[] arr) {
        int n = arr.length;

        // Step 1: Count total 1s
        int k = 0;
        for (int num : arr) {
            if (num == 1) k++;
        }

        // If no 1s exist
        if (k == 0) return -1;

        // Step 2: Count zeros in first window
        int zeros = 0;
        for (int i = 0; i < k; i++) {
            if (arr[i] == 0) zeros++;
        }

        int minSwaps = zeros;

        // Step 3: Sliding window
        for (int i = k; i < n; i++) {
            if (arr[i - k] == 0) zeros--; // remove left
            if (arr[i] == 0) zeros++;     // add right

            minSwaps = Math.min(minSwaps, zeros);
        }

        return minSwaps;
    }
}

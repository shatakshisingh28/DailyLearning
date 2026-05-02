# 💡 Explanation of the Approach
Problem Summary:
Each candle burns for a given number of days (units). Every day, the candle’s height reduces by 1 unit.
We are asked to find the maximum number of days until any candle is still burning — that simply means finding the candle with the longest burn time, or the largest number in the given array.

## 🧠 Idea / Logic
The problem boils down to finding the maximum element in an unsorted array.

We start by assuming the first element is the largest.

Then, we traverse the entire array:

For each element, compare it with the current largest.

If a greater element is found, update largest.

After the loop ends, largest holds the maximum value — i.e., the candle that will burn the longest.

## ⚙️ Approach (Step-by-Step)
Initialize a variable largest with the first element arr[0].

Loop through the array starting from index 1.

In each iteration, compare arr[i] with largest.

If arr[i] > largest, update largest = arr[i].

After the loop completes, return largest.

## 🧩 Why We Use long Instead of int
Even though all array elements are integers, it’s safer to use a long variable because:

The input constraints may contain values that exceed int range (±2,147,483,647).

Using long prevents integer overflow and makes the function robust for larger data.

long can handle up to ±9,223,372,036,854,775,807 — about 4 billion times larger than int.

## ⏱️ Time Complexity
We traverse all n elements exactly once → O(n)

This is the minimum possible time complexity for this problem since we must check every element at least once.

## 💾 Space Complexity
We use only one variable (largest) → O(1) auxiliary space.

## ✅ Conclusion
This is the most efficient and optimal solution.
No sorting or extra space is needed.
Even for very large arrays (like size 10⁶), it runs extremely fast because of its linear nature.

## 🧰 Code:
``` java
class Solution {
    long maxDays(int arr[]) {
        long largest = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > largest) {
                largest = arr[i];
            }
        }
        return largest;
    }
}
```
## ✨ In short:

Problem = Find longest-burning candle = Find largest number in array

Method = Simple linear scan

Complexity = O(n) time, O(1) space

Type = Use long to stay safe from overflow

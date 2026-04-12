# 🔍 Two Sum Problem

## 📌 Problem Statement
Given an array of integers `arr[]` and an integer `target`, determine whether there exist **two elements** in the array such that their sum is equal to the target.

---

## 🐢 Approach 1: Brute Force

### 💡 Idea
Check every possible pair using two nested loops.

### 🔧 Implementation
```java
class Solution {
    boolean twoSum(int arr[], int target) {
        for(int i = 0; i < arr.length; i++){
            for(int j = i + 1; j < arr.length; j++){
                if(arr[i] + arr[j] == target){
                    return true;
                }
            }
        }
        return false;
    }
}
```
### ⏱ Complexity
Time Complexity: O(n²)

Space Complexity: O(1)

### ❌ Drawback

Not efficient for large inputs due to repeated comparisons

## ⚡ Approach 2: Optimized using HashSet
### 💡 Idea

Traverse the array once

Store elements in a HashSet

Check if the complement (target - num) exists

### 🔧 Implementation
```java
import java.util.HashSet;

class Solution {
    boolean twoSum(int arr[], int target) {
        HashSet<Integer> set = new HashSet<>();
        
        for(int num : arr){
            if(set.contains(target - num)){
                return true;
            }
            set.add(num);
        }
        return false;
    }
}
```

}
### 🧠 Key Insight

At each step:

Check if the required number to reach the target has already been seen.

### ⏱ Complexity
Time Complexity: O(n)

Space Complexity: O(n)

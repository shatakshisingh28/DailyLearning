# Minimum Insertions to Make Array Co-Prime (Adjacent Pair-wise)

## 🧩 Problem Statement
Given an array of integers, find the **minimum number of insertions** required so that every adjacent pair of elements becomes **co-prime** (i.e., GCD = 1).

---

## 📌 Examples

### Example 1
Input:
arr = [2, 7, 28]

Output:
1

Explanation:
- gcd(2,7) = 1 ✅
- gcd(7,28) = 7 ❌ → insert 1 element

---

### Example 2
Input:
arr = [5, 10, 20]

Output:
2

Explanation:
- gcd(5,10) ≠ 1 ❌
- gcd(10,20) ≠ 1 ❌
→ Need 2 insertions

---

## 💡 Approach

- Traverse the array
- For each adjacent pair `(arr[i], arr[i+1])`:
  - If `gcd(arr[i], arr[i+1]) != 1`, increment count

### 🔑 Key Insight
Only **one insertion** is needed per non-coprime pair  
(because we can always insert `1`, which is co-prime with any number)

---

## ⚙️ Algorithm
1. Initialize `count = 0`
2. Loop from `i = 0` to `n-2`
3. Check:
```

if gcd(arr[i], arr[i+1]) != 1:
count++

````
4. Return `count`

---

## ⏱️ Complexity
- Time Complexity: `O(n log(max))`
- Space Complexity: `O(1)`

---

## 🧪 Sample Test

```java
Input: [2, 7, 28]
Output: 1

Input: [5, 10, 20]
Output: 2
```


---

# 📄 `Solution.java`
```java id="n9cxfv"
class Solution {
    
    private int gcd(int a, int b) {
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }

    public int countCoPrime(int[] arr) {
        int count = 0;
        
        for (int i = 0; i < arr.length - 1; i++) {
            if (gcd(arr[i], arr[i + 1]) != 1) {
                count++;
            }
        }
        
        return count;
    }
}
````

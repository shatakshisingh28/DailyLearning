# To check whether a given array represents a **valid max heap (level-order traversal)**, you just need to verify one condition:

👉 **For every parent node, its value must be greater than or equal to its children.**

---

### 🧠 Key Idea

For an array `arr` of size `n`:

* Parent index = `i`
* Left child index = `2*i + 1`
* Right child index = `2*i + 2`

You only need to check this for all **non-leaf nodes** (i.e., indices from `0` to `(n/2 - 1)`).

---

### ✅ Algorithm Steps

1. Loop through each parent node.
2. Compare:

   * `arr[i] >= arr[2*i + 1]` (left child)
   * `arr[i] >= arr[2*i + 2]` (right child, if exists)
3. If any condition fails → return `false`
4. If all pass → return `true`

---

### 💻 Java Code

```java
class Solution {
    public boolean isMaxHeap(int[] arr) {
        int n = arr.length;
        
        // Check all non-leaf nodes
        for (int i = 0; i <= (n / 2) - 1; i++) {
            
            // Left child
            int left = 2 * i + 1;
            if (arr[i] < arr[left]) {
                return false;
            }
            
            // Right child
            int right = 2 * i + 2;
            if (right < n && arr[i] < arr[right]) {
                return false;
            }
        }
        
        return true;
    }
}
```

---

### 🔍 Example Walkthrough

Input:
`[90, 15, 10, 7, 12, 2]`

Check:

* 90 ≥ 15, 10 ✅
* 15 ≥ 7, 12 ✅
* 10 ≥ 2 ✅

✔ All conditions satisfied → **Valid Max Heap**

---

### ⏱️ Complexity

* Time: **O(n)**
* Space: **O(1)**

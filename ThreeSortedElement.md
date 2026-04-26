# 🔗 Common Elements in Three Sorted Arrays

## 📌 Problem Statement

Given three **sorted arrays** in non-decreasing order, return all **common elements** present in all three arrays.

👉 If no such elements exist, return an **empty array**
👉 **Ignore duplicates** — include each common element only once

---

## 🧠 Approach (Three Pointers)

Since arrays are already sorted, we can efficiently solve this using **three pointers**:

* Use three indices `i`, `j`, `k` for arrays `arr1`, `arr2`, `arr3`
* Compare elements at these indices:

  * If all are equal → add to result
  * Otherwise, move the pointer pointing to the **smallest value**

---

## ⚙️ Algorithm

1. Initialize `i = 0, j = 0, k = 0`
2. While all pointers are within bounds:

   * If `arr1[i] == arr2[j] == arr3[k]`:

     * Add to result (avoid duplicates)
     * Increment all pointers
   * Else:

     * Increment the pointer with the smallest value
3. Return the result

---

## 💻 Java Implementation

```java id="i0rt0y"
import java.util.*;

class Solution {
    public ArrayList<Integer> commonElements(int[] arr1, int[] arr2, int[] arr3) {
        int i = 0, j = 0, k = 0;
        ArrayList<Integer> result = new ArrayList<>();

        while (i < arr1.length && j < arr2.length && k < arr3.length) {
            
            if (arr1[i] == arr2[j] && arr2[j] == arr3[k]) {
                
                // Avoid duplicates
                if (result.isEmpty() || result.get(result.size() - 1) != arr1[i]) {
                    result.add(arr1[i]);
                }
                
                i++;
                j++;
                k++;
            } 
            else {
                int min = Math.min(arr1[i], Math.min(arr2[j], arr3[k]));
                
                if (arr1[i] == min) i++;
                else if (arr2[j] == min) j++;
                else k++;
            }
        }

        return result;
    }
}
```

---

## 🧪 Examples

### Example 1

```id="k0fjx8"
Input:
arr1 = [1, 5, 10, 20, 40, 80]
arr2 = [6, 7, 20, 80, 100]
arr3 = [3, 4, 15, 20, 30, 70, 80, 120]

Output:
[20, 80]
```

---

### Example 2

```id="5a9y0s"
Input:
arr1 = [1, 2, 3]
arr2 = [4, 5, 6]
arr3 = [7, 8, 9]

Output:
[]
```

---

## ⚡ Complexity

* **Time Complexity:** O(n1 + n2 + n3)
* **Space Complexity:** O(1) (excluding output)



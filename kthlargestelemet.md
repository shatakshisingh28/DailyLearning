# 📊 Kth Largest Element in a Stream

## 🧩 Problem Statement
Given a stream of integers, find the **Kth largest element after each insertion**.

If the Kth largest element does not exist, return `-1`.

---

## 📥 Example

**Input:**

arr = [1, 2, 3, 4, 5, 6]
k = 4


**Output:**

[-1, -1, -1, 1, 2, 3]


---

## 🧠 Approach: Min Heap (Priority Queue)

We use a **Min Heap of size k** to efficiently track the k largest elements.

### 💡 Key Idea
- Keep only **k largest elements** in the heap
- The **top (root)** of the heap = **Kth largest element**

---

## ⚙️ Algorithm

For each element in stream:
1. Add element to heap  
2. If heap size > k → remove smallest element  
3. If heap size < k → answer = -1  
4. Else → answer = heap.peek()  

---

## 📊 Visual Diagram (Step-by-Step)

### 👉 k = 4


Step 1: Add 1
Heap: [1]
Output: -1

Step 2: Add 2
Heap: [1, 2]
Output: -1

Step 3: Add 3
Heap: [1, 2, 3]
Output: -1

Step 4: Add 4
Heap: [1, 2, 3, 4]
Output: 1 ← 4th largest

Step 5: Add 5
Heap before removal: [1, 2, 3, 4, 5]
Remove smallest (1)

Heap after: [2, 3, 4, 5]
Output: 2

Step 6: Add 6
Heap before removal: [2, 3, 4, 5, 6]
Remove smallest (2)

Heap after: [3, 4, 5, 6]
Output: 3


---

## 🧱 Heap Structure Visualization


Min Heap (k = 4)

    2
   / \
  3   4
 /
5

Top = 2 → 4th largest element


---

## ✅ Code (Java)

```java
import java.util.*;

public class KthLargestInStream {

    public static List<Integer> kthLargest(int[] arr, int k) {
        List<Integer> result = new ArrayList<>();
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();

        for (int num : arr) {
            minHeap.offer(num);

            if (minHeap.size() > k) {
                minHeap.poll();
            }

            if (minHeap.size() < k) {
                result.add(-1);
            } else {
                result.add(minHeap.peek());
            }
        }

        return result;
    }
}

Complexity Analysis

Type	Complexity

Time	O(n log k)

Space	O(k)



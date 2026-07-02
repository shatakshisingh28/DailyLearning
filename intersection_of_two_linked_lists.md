# Intersection of Two Linked Lists (Unsorted) | HashSet Approach

## Problem Statement

Given two linked lists `head1` and `head2`, find their intersection.

* Each linked list contains **distinct node values**.
* The intersection list should contain only the common elements.
* The order of nodes in the result should be the **same as they appear in `head1`**.
* If there is no common element, return `null`.

---

## Example

### Input

```text
head1 : 9 → 6 → 4 → 2 → 3 → 8

head2 : 1 → 2 → 8 → 6
```

### Output

```text
6 → 2 → 8
```

### Explanation

The common elements are:

```text
2, 6, 8
```

But the output is:

```text
6 → 2 → 8
```

because these elements appear in this order in **head1**.

---

# Approach

Since the linked lists are **not sorted**, we cannot use the two-pointer technique.

Instead:

1. Store all elements of **head2** in a `HashSet`.
2. Traverse **head1**.
3. If a node's value exists in the `HashSet`, add it to the answer list.
4. Return the newly created linked list.

Using a `HashSet` allows us to check whether a value exists in **O(1)** average time.

---
# Code
```java
import java.util.HashSet;

class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class Solution {

    public static Node findIntersection(Node head1, Node head2) {

        // Store all elements of second linked list
        HashSet<Integer> set = new HashSet<>();

        Node temp = head2;

        while (temp != null) {
            set.add(temp.data);
            temp = temp.next;
        }

        // Dummy node for the answer list
        Node dummy = new Node(-1);
        Node tail = dummy;

        // Traverse first linked list
        temp = head1;

        while (temp != null) {

            // If element exists in second list
            if (set.contains(temp.data)) {

                // Add it to answer
                tail.next = new Node(temp.data);
                tail = tail.next;
            }

            temp = temp.next;
        }

        return dummy.next;
    }
}
```
# Code Explanation

## Step 1: Create a HashSet

```java
HashSet<Integer> set = new HashSet<>();
```

The HashSet stores all values of the second linked list.

Example:

```text
head2

1 → 2 → 8 → 6

↓

HashSet

{1, 2, 8, 6}
```

---

## Step 2: Traverse the Second Linked List

```java
Node temp = head2;

while (temp != null) {
    set.add(temp.data);
    temp = temp.next;
}
```

Store every node value of `head2` inside the HashSet.

---

## Step 3: Create a Dummy Node

```java
Node dummy = new Node(-1);
Node tail = dummy;
```

A dummy node helps us build the new linked list easily.

`tail` always points to the last node of the answer list.

---

## Step 4: Traverse the First Linked List

```java
temp = head1;
```

Start traversing `head1`.

---

## Step 5: Check if the Current Node Exists in the HashSet

```java
if (set.contains(temp.data))
```

If the value is found in the HashSet, then it is common to both linked lists.

---

## Step 6: Add the Common Node

```java
tail.next = new Node(temp.data);
tail = tail.next;
```

Create a new node and add it to the answer list.

Move the `tail` pointer forward.

---

## Step 7: Move to the Next Node

```java
temp = temp.next;
```

Continue checking the remaining nodes.

---

## Step 8: Return the Result

```java
return dummy.next;
```

`dummy.next` points to the first node of the newly created intersection list.

---

# Dry Run

### Input

```text
head1

9 → 6 → 4 → 2 → 3 → 8

head2

1 → 2 → 8 → 6
```

### Step 1

Store `head2` in the HashSet.

```text
{1, 2, 8, 6}
```

---

### Step 2

Traverse `head1`.

| Current Node | Present in HashSet? | Result    |
| ------------ | ------------------- | --------- |
| 9            | ❌                   |           |
| 6            | ✅                   | 6         |
| 4            | ❌                   | 6         |
| 2            | ✅                   | 6 → 2     |
| 3            | ❌                   | 6 → 2     |
| 8            | ✅                   | 6 → 2 → 8 |

---

## Final Output

```text
6 → 2 → 8
```

---

# Why Do We Store `head2`?

The problem states that the output should follow the order of **head1**.

Therefore:

* Store all values of **head2** in a `HashSet`.
* Traverse **head1**.
* Whenever a value is found in the HashSet, add it to the answer.

This preserves the required order.

---

# Time Complexity

Building the HashSet:

```text
O(m)
```

Traversing the first linked list:

```text
O(n)
```

Overall:

```text
O(n + m)
```

where:

* `n` = Number of nodes in `head1`
* `m` = Number of nodes in `head2`

---

# Space Complexity

The HashSet stores all values of `head2`.

```text
O(m)
```

---

# Key Takeaways

* The linked lists are **not sorted**, so the two-pointer approach cannot be used.
* Use a **HashSet** for fast lookup.
* Store all values of `head2` in the HashSet.
* Traverse `head1` to maintain the required output order.
* Create a new linked list for the common elements.

## One-Line Summary

> **Store all nodes of the second linked list in a HashSet, then traverse the first linked list and add every common node to a new linked list while preserving the order of `head1`.**

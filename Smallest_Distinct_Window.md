# Smallest Distinct Window in a String

> **Platform:** GeeksforGeeks
> **Topic:** Sliding Window, HashMap
> **Difficulty:** Medium
> **Language:** Java

---

# Problem Statement

Given a string `str`, find the length of the **smallest substring** that contains **all the distinct characters** present in the original string.

---

## Example

### Input

```text
str = "aabcbcdbca"
```

### Output

```text
4
```

### Explanation

The distinct characters in the string are:

```text
a, b, c, d
```

The smallest substring containing all of them is:

```text
dbca
```

Length = **4**

---

# Intuition

Whenever a problem contains words like:

* Smallest Substring
* Longest Substring
* Continuous Characters

the **Sliding Window** technique should immediately come to mind.

Instead of checking every possible substring (which takes **O(n²)** time), we maintain a window that expands and shrinks while tracking the frequency of characters inside it.

The goal is to find the smallest valid window.

---

# Approach

### Step 1: Store All Distinct Characters

Traverse the string once and store every distinct character in a HashMap with frequency `0`.

Example:

```text
String = aabcbcdbca

HashMap

a → 0
b → 0
c → 0
d → 0
```

This tells us which characters every valid window must contain.

---

### Step 2: Expand the Window

Move the `right` pointer one step at a time.

Increase the frequency of the current character.

Example:

```text
Window = aabc

Map

a → 2
b → 1
c → 1
d → 0
```

The window is not valid because `d` is missing.

Continue expanding.

---

### Step 3: Check if the Window is Valid

A window is valid if every distinct character has a frequency greater than zero.

The helper function

```java
allAvailable(map)
```

checks this condition.

---

### Step 4: Shrink the Window

Once the window becomes valid, remove unnecessary characters from the left.

For example,

```text
Window = aabcbcd

Map

a → 2
b → 2
c → 2
d → 1
```

The leftmost character (`a`) appears twice.

Removing one occurrence still keeps another `a` inside the window.

So we shrink the window.

Stop shrinking when removing another character would make the window invalid.

---

### Step 5: Update the Answer

Whenever the window is valid,

calculate

```text
right - left + 1
```

and update the minimum length.

---

# Dry Run

String

```text
aabc
```

Distinct Characters

```text
a b c
```

### Initial State

```text
a = 0
b = 0
c = 0
```

---

### Right = 0

Window

```text
a
```

Map

```text
a = 1
b = 0
c = 0
```

Not valid.

---

### Right = 1

Window

```text
aa
```

Map

```text
a = 2
b = 0
c = 0
```

Not valid.

---

### Right = 2

Window

```text
aab
```

Map

```text
a = 2
b = 1
c = 0
```

Not valid.

---

### Right = 3

Window

```text
aabc
```

Map

```text
a = 2
b = 1
c = 1
```

Now the window is valid.

Shrink:

Remove one `a`

Window

```text
abc
```

Map

```text
a = 1
b = 1
c = 1
```

Still valid.

Cannot remove another `a`.

Minimum answer becomes **3**.

---

# Java Solution

```java
import java.util.HashMap;

class Solution {

    public int findSubString(String str) {

        int left = 0;
        int right = 0;
        int min = str.length();

        HashMap<Character, Integer> map = new HashMap<>();

        // Store all distinct characters
        for (char ch : str.toCharArray()) {
            map.put(ch, 0);
        }

        while (right < str.length()) {

            // Include current character in the window
            map.put(str.charAt(right),
                    map.get(str.charAt(right)) + 1);

            // Remove duplicate characters from the left
            while (map.get(str.charAt(left)) > 1) {

                map.put(str.charAt(left),
                        map.get(str.charAt(left)) - 1);

                left++;
            }

            // If all distinct characters are present,
            // update the minimum length
            if (allAvailable(map)) {
                min = Math.min(min, right - left + 1);
            }

            right++;
        }

        return min;
    }

    boolean allAvailable(HashMap<Character, Integer> map) {

        for (int frequency : map.values()) {

            if (frequency < 1) {
                return false;
            }
        }

        return true;
    }
}
```

---

# Time Complexity

Building the HashMap:

```text
O(n)
```

Sliding Window traversal:

```text
O(n)
```

Checking whether all characters are present:

```text
O(k)
```

where `k` is the number of distinct characters.

Overall:

```text
O(n × k)
```

For English alphabets, `k` is small, making the solution practically **O(n)**.

---

# Space Complexity

The HashMap stores only distinct characters.

```text
O(k)
```

where `k` is the number of distinct characters.

---

# Key Takeaways

* Substring problems often suggest the **Sliding Window** technique.
* Expand the window until it satisfies the condition.
* Shrink the window to remove unnecessary characters.
* Keep updating the minimum valid window.
* Use a **HashMap** to efficiently maintain character frequencies.

This **Expand → Validate → Shrink → Update** pattern is widely used in sliding window problems and is an important interview concept.

# Uncommon Characters Between Two Strings

## Problem Statement

Given two strings `s1` and `s2`, find all characters that are present in one string but not in the other.

The resulting characters should:

* Appear only once.
* Be sorted in alphabetical order.
* Return the final string containing all uncommon characters.

### Example

**Input:**

```text
s1 = "geeksforgeeks"
s2 = "geeksquiz"
```

**Output:**

```text
fioqruz
```

**Explanation:**

Characters present only in one string are:

```text
f, i, o, q, r, u, z
```

After sorting:

```text
fioqruz
```

---

## Approach

### Step 1: Store Unique Characters

Use two `HashSet<Character>` objects:

* `set1` stores unique characters from `s1`
* `set2` stores unique characters from `s2`

This automatically removes duplicate characters.

### Step 2: Find Uncommon Characters

Traverse:

* All characters in `set1`

  * If a character is not present in `set2`, add it to the result list.

* All characters in `set2`

  * If a character is not present in `set1`, add it to the result list.

### Step 3: Sort the Result

Use:

```java
Collections.sort(arr);
```

to arrange characters in ascending alphabetical order.

### Step 4: Convert to String

Use `StringBuilder` to build the final answer.

---

## Java Solution

```java
class Solution {
    String uncommonChars(String s1, String s2) {

        HashSet<Character> set1 = new HashSet<>();
        HashSet<Character> set2 = new HashSet<>();

        for(char c1 : s1.toCharArray()) {
            set1.add(c1);
        }

        for(char c2 : s2.toCharArray()) {
            set2.add(c2);
        }

        ArrayList<Character> arr = new ArrayList<>();

        for(char c1 : set1) {
            if(!set2.contains(c1)) {
                arr.add(c1);
            }
        }

        for(char c2 : set2) {
            if(!set1.contains(c2)) {
                arr.add(c2);
            }
        }

        Collections.sort(arr);

        StringBuilder sb = new StringBuilder();

        for(char c : arr) {
            sb.append(c);
        }

        return sb.toString();
    }
}
```

---

## Dry Run

### Input

```text
s1 = "abc"
s2 = "bcd"
```

### Create Sets

```text
set1 = {a, b, c}
set2 = {b, c, d}
```

### Traverse set1

```text
a → not in set2 → add
b → present in set2 → skip
c → present in set2 → skip
```

Result:

```text
[a]
```

### Traverse set2

```text
b → present in set1 → skip
c → present in set1 → skip
d → not in set1 → add
```

Result:

```text
[a, d]
```

### Sort

```text
[a, d]
```

### Convert to String

```text
"ad"
```

### Output

```text
ad
```

---

## Time Complexity

Let:

```text
n = length of s1
m = length of s2
```

### Building HashSets

```text
O(n + m)
```

### Finding Uncommon Characters

```text
O(n + m)
```

### Sorting

At most 26 lowercase English characters:

```text
O(26 log 26)
```

which is effectively constant.

### Overall Complexity

```text
O(n + m)
```

---

## Space Complexity

Two HashSets and one ArrayList are used.

```text
O(n + m)
```

In practice, for lowercase alphabets:

```text
O(26)
```

---

## Key Concepts Used

* HashSet
* ArrayList
* Character Comparison
* Set Operations
* Sorting
* StringBuilder

---

## Edge Cases

### No Uncommon Characters

**Input:**

```text
s1 = "abc"
s2 = "abc"
```

**Output:**

```text
""
```

---

### Completely Different Strings

**Input:**

```text
s1 = "abc"
s2 = "xyz"
```

**Output:**

```text
abcxyz
```

---

## Advantages of Using HashSet

✅ Removes duplicates automatically

✅ Fast lookup operation `O(1)`

✅ Cleaner implementation

✅ Efficient for large strings



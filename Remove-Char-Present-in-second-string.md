# Remove Characters Present in Second String

## Problem Statement

Given two strings `str1` and `str2`, remove from `str1` all characters that are present in `str2`.

Return the resulting string after removing all matching characters.

---

## Example 1

### Input

```text
str1 = "computer"
str2 = "cat"
```

### Output

```text
ompuer
```

### Explanation

Characters present in `str2`:

```text
c, a, t
```

Removing these from `str1`:

```text
computer
↓      ↓
c      t
```

Result:

```text
ompuer
```

---

## Example 2

### Input

```text
str1 = "occurrence"
str2 = "car"
```

### Output

```text
ouene
```

---

## Approach

### Idea

For every character in `str1`:

1. Check whether it exists in `str2`.
2. If it exists, skip it.
3. Otherwise, add it to the answer.

A `StringBuffer` is used to efficiently build the final string.

---

## Java Solution

```java
class Solution {
    static String removeChars(String str1, String str2) {

        boolean val;
        StringBuffer str = new StringBuffer();

        for(int i = 0; i < str1.length(); i++) {

            val = false;

            for(int j = 0; j < str2.length(); j++) {

                if(str1.charAt(i) == str2.charAt(j)) {
                    val = true;
                }
            }

            if(!val)
                str.append(str1.charAt(i));
        }

        return str.toString();
    }
}
```

---

## Dry Run

### Input

```text
str1 = "computer"
str2 = "cat"
```

### Iteration 1

```text
Character = c
```

Found in:

```text
cat
```

Skip it.

Result:

```text
""
```

---

### Iteration 2

```text
Character = o
```

Not found in `str2`.

Add to result:

```text
"o"
```

---

### Iteration 3

```text
Character = m
```

Not found.

Result:

```text
"om"
```

---

### Continue

```text
p → add
u → add
t → skip
e → add
r → add
```

Final result:

```text
ompuer
```

---

## Time Complexity

Let:

```text
n = length of str1
m = length of str2
```

For every character of `str1`, we scan the entire `str2`.

```text
O(n × m)
```

---

## Space Complexity

The result string may contain all characters of `str1`.

```text
O(n)
```

---

## Key Concepts Used

* Nested Loops
* String Traversal
* Character Comparison
* StringBuffer
* Brute Force Searching

---

## Optimization

A faster solution uses a `HashSet<Character>`.

### Why?

Checking:

```java
set.contains(ch)
```

takes:

```text
O(1)
```

instead of scanning the whole second string.

This reduces complexity from:

```text
O(n × m)
```

to:

```text
O(n + m)
```
### Pattern

```text
Store characters of second string in HashSet
→ Traverse first string
→ Keep only characters not present in HashSet
```

This is a common string + hashing interview pattern.

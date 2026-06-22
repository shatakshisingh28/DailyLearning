# Remove Duplicate Characters from String

## Problem Statement

Given a string `s` which may contain lowercase and uppercase characters, remove all duplicate characters from the string while preserving the order of their first occurrence.

The resultant string should contain only the first occurrence of each character, and the order of characters should remain the same as in the original string.

### Example

**Input**

```text
geEksforGEeks
```

**Output**

```text
geEksforG
```

**Explanation**

The characters `E`, `e`, `k`, and `s` appear more than once in the string. Their duplicate occurrences are removed while keeping their first occurrence.

Result: `geEksforG`

---

## Approach

We use a boolean array of size 256 to keep track of characters that have already been encountered.

### Steps

1. Create a boolean array `seen` of size 256.
2. Traverse the string character by character.
3. If the current character has not been seen before:

   * Mark it as seen.
   * Append it to the result string.
4. Ignore characters that have already been seen.
5. Return the resultant string.

This approach preserves the order of first occurrence and efficiently removes duplicates.

---

## Java Solution

```java
class Solution {
    String removeDuplicates(String s) {
        boolean[] seen = new boolean[256];
        StringBuilder ans = new StringBuilder();

        for (char ch : s.toCharArray()) {
            if (!seen[ch]) {
                seen[ch] = true;
                ans.append(ch);
            }
        }

        return ans.toString();
    }
}
```

---

## Dry Run

Input:

```text
geEksforGEeks
```

Processing:

| Character | Seen Before? | Result    |
| --------- | ------------ | --------- |
| g         | No           | g         |
| e         | No           | ge        |
| E         | No           | geE       |
| k         | No           | geEk      |
| s         | No           | geEks     |
| f         | No           | geEksf    |
| o         | No           | geEksfo   |
| r         | No           | geEksfor  |
| G         | No           | geEksforG |
| E         | Yes          | Skip      |
| e         | Yes          | Skip      |
| k         | Yes          | Skip      |
| s         | Yes          | Skip      |

Final Output:

```text
geEksforG
```

---

## Complexity Analysis

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)

Where `n` is the length of the string.

The boolean array has a fixed size of 256, so the extra space used is constant.

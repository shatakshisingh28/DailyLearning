# Good or Bad String

## Problem Statement

Given a string `S` consisting of lowercase alphabets and the character `'?'`, determine whether the string is **Good** or **Bad**.

A string is considered **Bad** if:

* It contains more than **5 consecutive vowels**, or
* It contains more than **3 consecutive consonants**.

The character `'?'` can represent either a vowel or a consonant.

Return:

* `1` if the string is **Good**
* `0` if the string is **Bad**

---

## Example 1

### Input

```text
S = "aeioup"
```

### Output

```text
0
```

### Explanation

The string contains:

```text
a e i o u
```

which forms more than 5 consecutive vowels.

Therefore, the string is **Bad**.

---

## Example 2

### Input

```text
S = "abc"
```

### Output

```text
1
```

### Explanation

The string does not contain:

* More than 5 consecutive vowels
* More than 3 consecutive consonants

Therefore, the string is **Good**.

---

## Approach

### Step 1

Maintain two counters:

* `vowel` → consecutive vowels count
* `consonant` → consecutive consonants count

### Step 2

Traverse the string character by character.

* If the character is a vowel:

  * Increment `vowel`
  * Reset `consonant`

* If the character is a consonant:

  * Increment `consonant`
  * Reset `vowel`

* If the character is `'?'`:

  * Increment both counters since it can act as either a vowel or a consonant.

### Step 3

At any point:

```text
vowel > 5
```

or

```text
consonant > 3
```

the string becomes **Bad**, so return `0`.

### Step 4

If traversal completes successfully, return `1`.

---

## Java Solution

```java
class Solution {
    static int isGoodorBad(String S) {

        int vowel = 0;
        int consonant = 0;

        for (int i = 0; i < S.length(); i++) {

            char ch = S.charAt(i);

            if (ch == '?') {

                vowel++;
                consonant++;

            } else if (isVowel(ch)) {

                vowel++;
                consonant = 0;

            } else {

                consonant++;
                vowel = 0;
            }

            if (vowel > 5 || consonant > 3) {
                return 0;
            }
        }

        return 1;
    }

    static boolean isVowel(char ch) {
        return ch == 'a' || ch == 'e' || ch == 'i'
            || ch == 'o' || ch == 'u';
    }
}
```

---

## Dry Run

### Input

```text
S = "aeiou?"
```

### Traversal

| Character | Vowel Count | Consonant Count |
| --------- | ----------- | --------------- |
| a         | 1           | 0               |
| e         | 2           | 0               |
| i         | 3           | 0               |
| o         | 4           | 0               |
| u         | 5           | 0               |
| ?         | 6           | 1               |

Since:

```text
vowel = 6
```

which is greater than 5,

Return:

```text
0
```

---

## Time Complexity

The string is traversed once.

```text
O(n)
```

where `n` is the length of the string.

---

## Space Complexity

Only a few variables are used.

```text
O(1)
```

---

## Key Concepts Used

* String Traversal
* Character Classification
* Vowel Checking
* Consecutive Count Tracking
* Conditional Logic


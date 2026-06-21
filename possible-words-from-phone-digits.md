# Possible Words From Phone Digits

## 🧠 Intuition

This problem is based on the traditional mobile phone keypad.

Each digit from **2 to 9** represents a set of characters:

| Digit | Characters |
| ----- | ---------- |
| 2     | abc        |
| 3     | def        |
| 4     | ghi        |
| 5     | jkl        |
| 6     | mno        |
| 7     | pqrs       |
| 8     | tuv        |
| 9     | wxyz       |

The goal is to generate all possible words that can be formed by choosing one character from each digit.

For example:

```text
Input: [2, 3]

2 → abc
3 → def

Output:
ad ae af bd be bf cd ce cf
```

The solution builds combinations level by level.

---

## 🔄 Approach

### Step 1: Create Keypad Mapping

Store all possible characters corresponding to each digit.

```java
String[] chr = {
    "", "", "abc", "def", "ghi",
    "jkl", "mno", "pqrs", "tuv", "wxyz"
};
```

---

### Step 2: Process Each Digit

For every digit in the input array:

* Ignore digits `0` and `1` because they do not contain letters.
* For the first valid digit:

  * Add all its characters directly into the result list.
* For subsequent digits:

  * Create new combinations by appending every character of the current digit to every existing string.

---

### Step 3: Update Result List

After processing a digit:

* Store newly formed combinations in a temporary list.
* Replace the old list with the new one.

---

### Step 4: Return All Combinations

Once all digits are processed, return the final list.

---

## 💻 Java Code

```java
class Solution {
    public ArrayList<String> possibleWords(int[] arr) {

        String[] chr = {
            "", "", "abc", "def", "ghi",
            "jkl", "mno", "pqrs", "tuv", "wxyz"
        };

        ArrayList<String> list = new ArrayList<>();
        int flag = 0;

        for(int i : arr) {

            if(i == 0 || i == 1) {
                continue;
            }

            ArrayList<String> l1 = new ArrayList<>();

            for(int j = 0; j < chr[i].length(); j++) {

                String st = String.valueOf(chr[i].charAt(j));

                if(flag == 0) {
                    list.add(st);
                    continue;
                }

                for(String st1 : list) {
                    String st2 = st1.concat(st);
                    l1.add(st2);
                }
            }

            if(flag == 1) {
                list.clear();
                list.addAll(l1);
            }

            flag = 1;
        }

        return list;
    }
}
```

---

## 📝 Dry Run

### Input

```text
arr = [2, 3]
```

### Iteration 1 (Digit = 2)

Characters:

```text
a b c
```

List becomes:

```text
[a, b, c]
```

---

### Iteration 2 (Digit = 3)

Characters:

```text
d e f
```

Generate combinations:

```text
a + d = ad
b + d = bd
c + d = cd

a + e = ae
b + e = be
c + e = ce

a + f = af
b + f = bf
c + f = cf
```

Final List:

```text
[ad, bd, cd, ae, be, ce, af, bf, cf]
```

---

## 🎯 Example

### Input

```text
[4, 5]
```

### Mapping

```text
4 → ghi
5 → jkl
```

### Output

```text
gj gk gl
hj hk hl
ij ik il
```

---

## ⚙️ Complexity Analysis

Let:

* n = number of digits
* k = maximum letters mapped to a digit (4 for digit 7 and 9)

### Time Complexity

```text
O(k^n)
```

Reason:

* Every digit multiplies the number of combinations.
* In the worst case, each digit contributes 4 characters.

Example:

```text
Input = [7,7,7]

Total combinations = 4 × 4 × 4 = 64
```

---

### Space Complexity

```text
O(k^n)
```

Reason:

* All generated combinations are stored in the result list.

---

## ✅ Key Takeaways

* Uses an iterative approach to build combinations.
* Similar to generating Cartesian products.
* Avoids recursion by constructing combinations level-by-level.
* Efficient for keypad combination problems.
* Commonly asked in coding interviews and competitive programming.

### Pattern Used

```text
Existing Words + Current Character
          ↓
      New Words
```

This technique is useful for generating all possible combinations from multiple groups of characters.

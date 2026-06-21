# Valid Parentheses / Balanced Brackets

## 🧠 Intuition

The idea is to use a **Stack** data structure to keep track of opening brackets.

* Whenever we encounter an opening bracket `(`, `{`, or `[`, we push it onto the stack.
* Whenever we encounter a closing bracket `)`, `}`, or `]`, we check whether it matches the most recent opening bracket stored at the top of the stack.
* If the brackets do not match, or if the stack is empty when a closing bracket appears, the string is invalid.
* At the end, if the stack is empty, all brackets have been matched correctly.

---

## 🔄 Approach

### Step 1: Traverse the String

For every character in the string:

* If it is an opening bracket (`(`, `{`, `[`):

  * Push it onto the stack.
* If it is a closing bracket (`)`, `}`, `]`):

  * Check whether the stack is empty.
  * If empty, return `false`.
  * Otherwise, compare it with the top element of the stack.
  * If they do not form a valid pair, return `false`.
  * If they match, remove the opening bracket from the stack.

### Step 2: Final Validation

After processing all characters:

* If the stack is empty, all brackets are balanced.
* Otherwise, some opening brackets remain unmatched.

---

## ☕ Java Code

```java
class Solution {
    public boolean ispar(String s) {

        if(s.length() <= 1) {
            return false;
        }

        Stack<Character> stack = new Stack<>();

        for(int i = 0; i < s.length(); i++) {

            if(s.charAt(i) == '[' ||
               s.charAt(i) == '{' ||
               s.charAt(i) == '(') {

                stack.push(s.charAt(i));
            }

            else if(stack.empty()) {
                return false;
            }

            else {

                if(s.charAt(i) == ')') {
                    if(stack.pop() != '(') {
                        return false;
                    }
                }

                if(s.charAt(i) == '}') {
                    if(stack.pop() != '{') {
                        return false;
                    }
                }

                if(s.charAt(i) == ']') {
                    if(stack.pop() != '[') {
                        return false;
                    }
                }
            }
        }

        return stack.empty();
    }
}
```

---

## 📝 Dry Run

### Input

```text
{[()]}
```

### Execution

| Character | Operation     | Stack   |
| --------- | ------------- | ------- |
| `{`       | Push          | `{`     |
| `[`       | Push          | `{ [`   |
| `(`       | Push          | `{ [ (` |
| `)`       | Match and Pop | `{ [`   |
| `]`       | Match and Pop | `{`     |
| `}`       | Match and Pop | Empty   |

### Result

```text
true
```

All brackets are properly matched.

---

## ⚙️ Complexity Analysis

### Time Complexity

**O(n)**

* Each character is processed exactly once.
* Every push and pop operation takes **O(1)** time.

### Space Complexity

**O(n)**

* In the worst case, all characters are opening brackets.
* The stack may store all `n` characters.

---

## ✅ Key Takeaways

* Stack follows **LIFO (Last In, First Out)**.
* The most recent opening bracket must be closed first.
* Balanced brackets require:

  * Correct ordering
  * Correct pairing
  * No unmatched brackets remaining

This makes Stack the perfect data structure for solving the Balanced Parentheses problem.
